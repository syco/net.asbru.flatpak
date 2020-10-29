## asbru

### Here follows some commands I use to test and prefer to keep together with the repo for quick copy and paste:
```bash
sudo zypper install flatpak flatpak-builder
sudo flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
sudo flatpak -y --system install flathub org.gnome.Platform//3.36 org.gnome.Sdk//3.36

# BUILD
flatpak-builder --force-clean --repo=test-repo-asbru build-dir net.asbru.flatpak.json

# TEST
sudo flatpak remote-add --no-gpg-verify test-repo-asbru test-repo-asbru
flatpak -y remove net.asbru.flatpak
flatpak -y --system install test-repo-asbru net.asbru.flatpak
flatpak run net.asbru.flatpak
flatpak run --command=/bin/bash net.asbru.flatpak
/app/asbru-cm/asbru-cm

# EXPORT
flatpak build-bundle test-repo-asbru asbru-6.2.1.flatpak net.asbru.flatpak

# IMPORT
sudo flatpak -y install asbru-6.2.1.flatpak
sudo flatpak -y remove net.asbru.flatpak

```

`PERL_MM_USE_DEFAULT=true perl -MCPAN`
