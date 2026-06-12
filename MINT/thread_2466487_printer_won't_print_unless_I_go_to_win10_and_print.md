---
title: "printer won't print unless I go to win10 and print something there, and then back to"
date: 2021-08-29
forum: MINT
---

### Post by Kris_M on 2021-08-29
Mint 20.2 Sorry but hoping you know the answer.
This one is a HP P1102w. It will recognize it, sometimes, or I can add it manually via cups, but I either get a 5012 communication error or it says it has printed and it hasen't.

Getting very frustrated with this. I have 2 HP laser printers. It would be awfully nice if I could get them to work when I ask them to rather than having to boot to win10, which I keep trying to leave...

Any help?
Thanks.

```
kris@kris-ThinkPad-T570:~$ inxi -Fxxxrz
System:
  Kernel: 5.4.0-81-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 
  Desktop: Cinnamon 5.0.5 wm: muffin 5.0.1 dm: LightDM 1.30.0 
  Distro: Linux Mint 20.2 Uma base: Ubuntu 20.04 focal 
Machine:
  Type: Laptop System: LENOVO product: 20HAS02P00 v: ThinkPad T570 
  serial: <filter> Chassis: type: 10 serial: <filter> 
  Mobo: LENOVO model: 20HAS02P00 v: SDK0J40697 WIN serial: <filter> 
  UEFI: LENOVO v: N1VET56W (1.46 ) date: 05/17/2021 
Battery:
  ID-1: BAT0 charge: 28.3 Wh condition: 28.6/32.0 Wh (89%) volts: 15.3/15.3 
  model: SMP 00UR891 type: Li-poly serial: <filter> status: Unknown 
  cycles: 29 
  ID-2: BAT1 charge: 32.5 Wh condition: 33.1/47.5 Wh (70%) volts: 12.3/10.8 
  model: SANYO 01AV425 type: Li-ion serial: <filter> status: Unknown 
  cycles: 212 
  Device-1: hidpp_battery_0 model: Logitech Wireless Mouse M510 
  serial: <filter> charge: 55% (should be ignored) rechargeable: yes 
  status: Discharging 
CPU:
  Topology: Dual Core model: Intel Core i7-7600U bits: 64 type: MT MCP 
  arch: Amber Lake rev: 9 L2 cache: 4096 KiB 
  flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx 
  bogomips: 23199 
  Speed: 1000 MHz min/max: 400/3900 MHz Core speeds (MHz): 1: 937 2: 953 
  3: 931 4: 935 
Graphics:
  Device-1: Intel HD Graphics 620 vendor: Lenovo driver: i915 v: kernel 
  bus ID: 00:02.0 chip ID: 8086:5916 
  Display: x11 server: X.Org 1.20.11 driver: modesetting 
  unloaded: fbdev,vesa resolution: 1920x1080~60Hz 
  OpenGL: renderer: Mesa Intel HD Graphics 620 (KBL GT2) v: 4.6 Mesa 21.0.3 
  direct render: Yes 
Audio:
  Device-1: Intel Sunrise Point-LP HD Audio vendor: Lenovo 
  driver: snd_hda_intel v: kernel bus ID: 00:1f.3 chip ID: 8086:9d71 
  Sound Server: ALSA v: k5.4.0-81-generic 
Network:
  Device-1: Intel Ethernet I219-LM vendor: Lenovo driver: e1000e v: 3.2.6-k 
  port: efa0 bus ID: 00:1f.6 chip ID: 8086:15d7 
  IF: enp0s31f6 state: up speed: 1000 Mbps duplex: full mac: <filter> 
  Device-2: Intel Wireless 8265 / 8275 driver: iwlwifi v: kernel port: efa0 
  bus ID: 04:00.0 chip ID: 8086:24fd 
  IF: wlp4s0 state: down mac: <filter> 
  IF-ID-1: vmnet1 state: unknown speed: N/A duplex: N/A mac: <filter> 
  IF-ID-2: vmnet8 state: unknown speed: N/A duplex: N/A mac: <filter> 
Drives:
  Local Storage: total: 1.15 TiB used: 559.83 GiB (47.5%) 
  ID-1: /dev/nvme0n1 vendor: Samsung model: MZVLW256HEHP-000L7 
  size: 238.47 GiB speed: 31.6 Gb/s lanes: 4 serial: <filter> rev: 4L7QCXB7 
  scheme: GPT 
  ID-2: /dev/sdb type: USB model: N/A size: 7.38 GiB serial: <filter> 
  rev: PMAP scheme: MBR 
  ID-3: /dev/sdc type: USB vendor: Samsung model: SSD 870 EVO 1TB 
  size: 931.51 GiB serial: <filter> scheme: GPT 
Partition:
  ID-1: / size: 72.83 GiB used: 44.55 GiB (61.2%) fs: ext4 
  dev: /dev/nvme0n1p8 
Sensors:
  System Temperatures: cpu: 65.0 C mobo: N/A 
  Fan Speeds (RPM): cpu: 3110 
Repos:
  No active apt repos in: /etc/apt/sources.list 
  Active apt repos in: /etc/apt/sources.list.d/google-earth-pro.list 
  1: deb [arch=amd64] http://dl.google.com/linux/earth/deb/ stable main
  Active apt repos in: /etc/apt/sources.list.d/official-package-repositories.list 
  1: deb http://packages.linuxmint.com uma main upstream import backport #id:linuxmint_main
  2: deb http://archive.ubuntu.com/ubuntu focal main restricted universe multiverse
  3: deb http://archive.ubuntu.com/ubuntu focal-updates main restricted universe multiverse
  4: deb http://archive.ubuntu.com/ubuntu focal-backports main restricted universe multiverse
  5: deb http://security.ubuntu.com/ubuntu/ focal-security main restricted universe multiverse
  6: deb http://archive.canonical.com/ubuntu/ focal partner
  Active apt repos in: /etc/apt/sources.list.d/skype-stable.list 
  1: deb [arch=amd64] https://repo.skype.com/deb stable main
  Active apt repos in: /etc/apt/sources.list.d/steam.list 
  1: deb [arch=amd64,i386] https://repo.steampowered.com/steam/ stable steam
  2: deb-src [arch=amd64,i386] https://repo.steampowered.com/steam/ stable steam
Info:
  Processes: 242 Uptime: 54m Memory: 15.49 GiB used: 2.45 GiB (15.8%) 
  Init: systemd v: 245 runlevel: 5 Compilers: gcc: 9.3.0 alt: 9 Shell: bash 
  v: 5.0.17 running in: gnome-terminal inxi: 3.0.38 
kris@kris-ThinkPad-T570:~$ 


```

---

### Post by Irihapeti on 2021-08-29
*Thread moved to **MINT** for a better fit.*

---

### Post by bcschmerker on 2021-08-31
**Checking the Hewlett-Packard Developers Portal page on [printers and all-in-ones supporting LinUX Imaging and Printing](https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index), the LaserJet Professional p1102w Printer requires Release 3.10.4 or newer,** which should be in the ubuntu Repositories for all of Trusty (3.14.0-0ubuntu3.4), Xenial (3.16.3+repack0-1), Bionic (3.17.10+repack0-5), Focal (3.20.3+dfsg0-2), Groovy (3.20.5+dfsg0-3build1, n/l/s), Hirsute (3.21.2+dfsg1-2), and Impish (3.21.4+dfsg0-1, devel).  From [the package Page at Launchpad](https://launchpad.net/ubuntu/+source/hplip), the total driver suite includes:

hpijs-ppds: HP Linux Printing and Imaging - HPIJS PPD files
hplip: HP Linux Printing and Imaging System (HPLIP)
hplip-data: HP Linux Printing and Imaging - data files
hplip-dbgsym: debug symbols for hplip
hplip-doc: HP Linux Printing and Imaging - documentation
hplip-gui: HP Linux Printing and Imaging - GUI utilities (Qt-based)
libhpmud-dev: HP Multi-Point Transport Driver (hpmud) development libraries
libhpmud0: HP Multi-Point Transport Driver (hpmud) run-time libraries
libhpmud0-dbgsym: debug symbols for libhpmud0
libsane-hpaio: HP SANE backend for multi-function peripherals
libsane-hpaio-dbgsym: debug symbols for libsane-hpaio
printer-driver-hpcups: HP Linux Printing and Imaging - CUPS Raster driver (hpcups)
printer-driver-hpcups-dbgsym: debug symbols for printer-driver-hpcups
printer-driver-hpijs: HP Linux Printing and Imaging - printer driver (hpijs)
printer-driver-hpijs-dbgsym: debug symbols for printer-driver-hpijs
printer-driver-postscript-hp: HP Printers PostScript Descriptions
printer-driver-postscript-hp-dbgsym: debug symbols for printer-driver-postscript-hp

In GNOME Terminal, KDE Konsole, or equivalent, ```
sudo apt install hplip
``` should select any missing Depends for co-installation.

---

