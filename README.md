# smx-stage-udev-rule

Installs a udev rule that grants read/write access to [StepManiaX Stage](https://www.stepmaniax.com/) devices in linux, allowing applications like [SMX Web Config](https://smx.tools/) to communicate with the pad.

## Installation

Download the appropriate package for your distro from the [Releases](../../releases) page.

**Debian / Ubuntu / Mint**

```sh
sudo dpkg -i smx-stage-udev-rule_1.0.0_all.deb
```

**Fedora / RHEL / openSUSE**

```sh
sudo rpm -i smx-stage-udev-rule-1.0.0-1.noarch.rpm
```

**Arch Linux**

Available on the [AUR](https://aur.archlinux.org/packages/smx-stage-udev-rule) — install with your AUR helper:

```sh
yay -S smx-stage-udev-rule
# or
paru -S smx-stage-udev-rule
```

Or install the `.pkg.tar.zst` from the Releases page directly:

```sh
sudo pacman -U smx-stage-udev-rule-1.0.0-1-any.pkg.tar.zst
```

The package runs `udevadm control --reload-rules && udevadm trigger --subsystem-match=hidraw` on install. Replug your stage after installing if it was already connected.

## Manual installation

If you'd prefer not to use a package manager:

```sh
sudo cp 95-smx-stage.rules /usr/lib/udev/rules.d/
sudo udevadm control --reload-rules
sudo udevadm trigger --subsystem-match=hidraw
```

To remove:

```sh
sudo rm /usr/lib/udev/rules.d/95-smx-stage.rules
sudo udevadm control --reload-rules
```

## Building from source

Requires [nFPM](https://nfpm.goreleaser.com/).

```sh
mkdir dist
nfpm package --packager deb --target dist/
nfpm package --packager rpm --target dist/
nfpm package --packager archlinux --target dist/
```

## License

0BSD
