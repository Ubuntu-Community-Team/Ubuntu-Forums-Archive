---
title: "System freezes and crashes."
date: 2021-03-20
forum: MINT
---

### Post by Quirky747 on 2021-03-20
Hi, having occasional freezes and crashes, no obvious (to me) reasons or times when it happens. This is a newly built machine, and I am an amateur, so looking for something I may have done wrong. System info is - 
```
System:    Kernel: 5.4.0-67-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 Desktop: Cinnamon 4.8.6 
           wm: muffin dm: LightDM Distro: Linux Mint 20.1 Ulyssa base: Ubuntu 20.04 focal 
Machine:   Type: Desktop Mobo: ASRock model: A320M-DVS R4.0 serial: <filter> 
           UEFI: American Megatrends v: P4.00 date: 07/16/2020 
CPU:       Topology: Quad Core model: AMD Ryzen 5 1400 bits: 64 type: MT MCP arch: Zen rev: 1 
           L2 cache: 2048 KiB 
           flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm bogomips: 51096 
           Speed: 1412 MHz min/max: 1550/3200 MHz Core speeds (MHz): 1: 1375 2: 1375 3: 1375 
           4: 1375 5: 1375 6: 1375 7: 1423 8: 1375 
Graphics:  Device-1: NVIDIA GK208B [GeForce GT 710] vendor: Micro-Star MSI driver: nvidia 
           v: 460.39 bus ID: 06:00.0 chip ID: 10de:128b 
           Display: x11 server: X.Org 1.20.9 driver: nvidia 
           unloaded: fbdev,modesetting,nouveau,vesa resolution: 1366x768~60Hz 
           OpenGL: renderer: GeForce GT 710/PCIe/SSE2 v: 4.6.0 NVIDIA 460.39 direct render: Yes 
Audio:     Device-1: NVIDIA GK208 HDMI/DP Audio vendor: Micro-Star MSI driver: snd_hda_intel 
           v: kernel bus ID: 06:00.1 chip ID: 10de:0e0f 
           Device-2: AMD Family 17h HD Audio vendor: ASRock driver: snd_hda_intel v: kernel 
           bus ID: 08:00.3 chip ID: 1022:1457 
           Sound Server: ALSA v: k5.4.0-67-generic 
Network:   Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet vendor: ASRock 
           driver: r8169 v: kernel port: f000 bus ID: 05:00.0 chip ID: 10ec:8168 
           IF: enp5s0 state: down mac: <filter> 
           Device-2: Realtek 802.11ac WLAN Adapter type: USB driver: rtl88XXau bus ID: 3-4:2 
           chip ID: 0bda:0811 
           IF: wlxe84e06570618 state: up mac: <filter> 
Drives:    Local Storage: total: 931.52 GiB used: 140.19 GiB (15.0%) 
           ID-1: /dev/sda vendor: Western Digital model: WD5000AAKX-001CA0 size: 465.76 GiB 
           speed: 6.0 Gb/s serial: <filter> 
           ID-2: /dev/sdb vendor: Seagate model: ST3500312CS size: 465.76 GiB speed: 1.5 Gb/s 
           serial: <filter> 
Partition: ID-1: / size: 456.96 GiB used: 70.09 GiB (15.3%) fs: ext4 dev: /dev/sda2 
Sensors:   System Temperatures: cpu: 20.0 C mobo: N/A gpu: nvidia temp: 27 C 
           Fan Speeds (RPM): N/A gpu: nvidia fan: 50% 
Repos:     No active apt repos in: /etc/apt/sources.list 
           Active apt repos in: /etc/apt/sources.list.d/gezakovacs-ppa-focal.list 
           1: deb http: //ppa.launchpad.net/gezakovacs/ppa/ubuntu focal main
           Active apt repos in: /etc/apt/sources.list.d/official-package-repositories.list 
           1: deb http: //www.mirrorservice.org/sites/packages.linuxmint.com/packages ulyssa main upstream import backport
           2: deb http: //archive.ubuntu.com/ubuntu focal main restricted universe multiverse
           3: deb http: //archive.ubuntu.com/ubuntu focal-updates main restricted universe multiverse
           4: deb http: //archive.ubuntu.com/ubuntu focal-backports main restricted universe multiverse
           5: deb http: //security.ubuntu.com/ubuntu/ focal-security main restricted universe multiverse
           6: deb http: //archive.canonical.com/ubuntu/ focal partner
           Active apt repos in: /etc/apt/sources.list.d/opera-stable.list 
           1: deb https: //deb.opera.com/opera-stable/ stable non-free #Opera Browser (final releases)
           Active apt repos in: /etc/apt/sources.list.d/spotify.list 
           1: deb http: //repository.spotify.com stable non-free
Info:      Processes: 254 Uptime: 24m Memory: 15.57 GiB used: 1.48 GiB (9.5%) Init: systemd v: 245 
           runlevel: 5 Compilers: gcc: 9.3.0 alt: 9 Client: Unknown python3.8 client inxi: 3.0.38 
```
And this is a log of my most recent crash - 
```
08:23:16 pulseaudio: GetManagedObjects() failed: org.freedesktop.DBus.Error.TimedOut: Failed to activate service 'org.bluez': timed out (service_start_timeout=25000ms)
08:23:01 lightdm: gkr-pam: unable to locate daemon control file
08:22:42 wpa_supplicant: bgscan simple: Failed to enable signal strength monitoring
08:22:23 kernel: Failed to find module '8192eu'
08:22:19 kernel: mce: [Hardware Error]: PROCESSOR 2:800f11 TIME 1616228521 SOCKET 0 APIC 2 microcode 8001138
08:22:19 kernel: mce: [Hardware Error]: PROCESSOR 2:800f11 TIME 1616228521 SOCKET 0 APIC 2 microcode 8001138
08:22:19 kernel: mce: [Hardware Error]: TSC 0 ADDR 1ffff98edc72e MISC d012000100000000 SYND 4d000000 IPID 500b000000000 
08:22:19 kernel: mce: [Hardware Error]: CPU 1: Machine Check: 0 Bank 5: bea0000000000108
```
Anyone point me to a simple solution, or point out if I did something wrong? This was a fresh install on a new system and everything seemed to go well.

---

