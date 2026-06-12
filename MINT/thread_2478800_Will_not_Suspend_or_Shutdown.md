---
title: "Will not Suspend or Shutdown"
date: 2022-09-05
forum: MINT
---

### Post by lenny54linux on 2022-09-05
I have searched for a solution to no avail, Dell laptop with fresh new install, Mint 20.2 Cinnamon

[COLOR=#333333][FONT=&amp]Here is the ISSUE:[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]~Computer will not suspend. (Doesn't matter if by menu, power button, terminal)[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]~Computer will not shut down. (Doesn't matter if by menu, power button, terminal) Shut down always results in reboot.

With the new installation, the hard drive wiped, this was done in an attempt to resolve this issue, but it has not.
I've combed the bios and cannot see any issues there.

Timeshift is not an option, brand new install.

Thank you in advance for any suggestions on this one.

[/FONT][/COLOR]```
System:    Kernel: 5.4.0-125-generic x86_64 bits: 64 compiler: gcc v: 9.4.0 
           Desktop: Cinnamon 5.0.7 wm: muffin dm: LightDM Distro: Linux Mint 20.2 Uma 
           base: Ubuntu 20.04 focal 
Machine:   Type: Laptop System: Dell product: Inspiron 3583 v: N/A serial: <filter> Chassis: 
           type: 10 serial: <filter> 
           Mobo: Dell model: 0RPPCD v: A02 serial: <filter> UEFI: Dell v: 1.20.0 date: 07/05/2022 
Battery:   ID-1: BAT0 charge: 7.7 Wh condition: 23.1/42.0 Wh (55%) volts: 11.1/11.4 
           model: LGC-LGC3.65 DELL FDRHM0B serial: <filter> status: Discharging 
CPU:       Topology: Dual Core model: Intel Celeron 4205U bits: 64 type: MCP arch: Kaby Lake 
           rev: C L2 cache: 2048 KiB 
           flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 7200 
           Speed: 1800 MHz min/max: 400/1800 MHz Core speeds (MHz): 1: 1800 2: 1800 
Graphics:  Device-1: Intel vendor: Dell driver: i915 v: kernel bus ID: 00:02.0 chip ID: 8086:3ea1 
           Display: x11 server: X.Org 1.20.13 driver: modesetting unloaded: fbdev,vesa 
           resolution: 1366x768~60Hz 
           OpenGL: renderer: Mesa Intel UHD Graphics 610 (WHL GT1) v: 4.6 Mesa 21.2.6 
           direct render: Yes 
Audio:     Device-1: Intel Cannon Point-LP High Definition Audio vendor: Dell 
           driver: snd_hda_intel v: kernel bus ID: 00:1f.3 chip ID: 8086:9dc8 
           Sound Server: ALSA v: k5.4.0-125-generic 
Network:   Device-1: Realtek RTL810xE PCI Express Fast Ethernet vendor: Dell driver: r8169 
           v: kernel port: 3000 bus ID: 01:00.0 chip ID: 10ec:8136 
           IF: enp1s0 state: up speed: 100 Mbps duplex: full mac: <filter> 
           Device-2: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter vendor: Dell 
           driver: ath10k_pci v: kernel port: 3000 bus ID: 02:00.0 chip ID: 168c:0042 
           IF: wlp2s0 state: down mac: <filter> 
Drives:    Local Storage: total: 1.38 TiB used: 669.84 GiB (47.6%) 
           ID-1: /dev/nvme0n1 vendor: A-Data model: SX8200PNP size: 476.94 GiB speed: 31.6 Gb/s 
           lanes: 4 serial: <filter> 
           ID-2: /dev/sda vendor: Seagate model: ST1000LM035-1RK172 size: 931.51 GiB 
           speed: 6.0 Gb/s serial: <filter> 
Partition: ID-1: / size: 467.89 GiB used: 134.03 GiB (28.6%) fs: ext4 dev: /dev/nvme0n1p2 
USB:       Hub: 1-0:1 info: Full speed (or root) Hub ports: 12 rev: 2.0 chip ID: 1d6b:0002 
           Device-1: 1-6:2 info: Sunplus Innovation Integrated_Webcam_HD type: Video 
           driver: uvcvideo rev: 2.0 chip ID: 1bcf:2b98 
           Hub: 2-0:1 info: Full speed (or root) Hub ports: 4 rev: 3.1 chip ID: 1d6b:0003 
Sensors:   System Temperatures: cpu: 54.0 C mobo: N/A 
           Fan Speeds (RPM): cpu: 2758 
Repos:     No active apt repos in: /etc/apt/sources.list 
           Active apt repos in: /etc/apt/sources.list.d/brave-browser-release.list 
           1: deb [signed-by=/usr/share/keyrings/brave-browser-archive-keyring.gpg arch=amd64] https: //brave-browser-apt-release.s3.brave.com/ stable main
           Active apt repos in: /etc/apt/sources.list.d/official-package-repositories.list 
           1: deb http: //packages.linuxmint.com uma main upstream import backport #id:linuxmint_main
           2: deb http: //archive.ubuntu.com/ubuntu focal main restricted universe multiverse
           3: deb http: //archive.ubuntu.com/ubuntu focal-updates main restricted universe multiverse
           4: deb http: //archive.ubuntu.com/ubuntu focal-backports main restricted universe multiverse
           5: deb http: //security.ubuntu.com/ubuntu/ focal-security main restricted universe multiverse
           6: deb http: //archive.canonical.com/ubuntu/ focal partner
Info:      Processes: 237 Uptime: 1h 20m Memory: 15.39 GiB used: 8.39 GiB (54.5%) Init: systemd 
           v: 245 runlevel: 5 target: graphical.target Compilers: gcc: 9.4.0 alt: 8/9 
           Client: Unknown python3.8 client inxi: 3.0.38 

```

---

### Post by QIII on 2022-09-05
Moved to MINT as a more appropriate sub-forum.

---

### Post by lenny54linux on 2022-09-06
Updated to 5.14 kernel, did not fix

---

### Post by lenny54linux on 2022-09-09
complete hard drive wipe, new install, did NOT fix

---

### Post by lenny54linux on 2022-10-25
The latest kernal update made the issue go away.

---

