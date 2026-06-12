---
title: "Can't mount DVD"
date: 2021-09-14
forum: MINT
---

### Post by pascal111 on 2021-09-14
I tried to amount my DVD and found this error message:

```

pascal@pascal-Lenovo-ideapad-330-15AST:~$ sudo mount -t auto /dev/cdrom /media/cdrom
mount: /media/cdrom: can't read superblock on /dev/sr0.

```

My computer infos. are like this:

```

pascal@pascal-Lenovo-ideapad-330-15AST:~$ inxi -Fxzd 
System:
  Host: pascal-Lenovo-ideapad-330-15AST Kernel: 5.4.0-84-generic x86_64 
  bits: 64 compiler: gcc v: 7.5.0 Desktop: MATE 1.22.2 
  Distro: Linux Mint 19.3 Tricia base: Ubuntu 18.04 bionic 
Machine:
  Type: Laptop System: LENOVO product: 81D6 v: Lenovo ideapad 330-15AST 
  serial: <filter> 
  Mobo: LENOVO model: LNVNB161216 v: No DPK serial: <filter> 
  UEFI [Legacy]: LENOVO v: 8UCN06WW date: 04/10/2018 
Battery:
  ID-1: BAT0 charge: 6.2 Wh condition: 15.2/30.6 Wh (50%) 
  model: CPT-COS L16C2PB2 status: Discharging 
CPU:
  Topology: Dual Core model: AMD E2-9000 RADEON R2 4 COMPUTE CORES 2C+2G 
  bits: 64 type: MCP arch: Excavator L2 cache: 1024 KiB 
  flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm 
  bogomips: 7200 
  Speed: 1399 MHz min/max: 1200/1800 MHz Core speeds (MHz): 1: 1456 2: 1479 
Graphics:
  Device-1: AMD Stoney [Radeon R2/R3/R4/R5 Graphics] vendor: Lenovo 
  driver: amdgpu v: kernel bus ID: 00:01.0 
  Display: x11 server: X.Org 1.19.6 driver: amdgpu,ati 
  unloaded: fbdev,modesetting,radeon,vesa resolution: 1366x768~60Hz 
  OpenGL: renderer: AMD STONEY (DRM 3.35.0 5.4.0-84-generic LLVM 10.0.0) 
  v: 4.5 Mesa 20.0.8 direct render: Yes 
Audio:
  Device-1: AMD vendor: Lenovo driver: snd_hda_intel v: kernel 
  bus ID: 00:01.1 
  Device-2: AMD Family 15h Audio vendor: Lenovo driver: snd_hda_intel 
  v: kernel bus ID: 00:09.2 
  Sound Server: ALSA v: k5.4.0-84-generic 
Network:
  Device-1: Realtek RTL8821CE 802.11ac PCIe Wireless Network Adapter 
  vendor: Lenovo driver: rtl8821ce v: N/A port: 2000 bus ID: 01:00.0 
  IF: wlp1s0 state: up mac: <filter> 
  Device-2: Realtek RTL810xE PCI Express Fast Ethernet vendor: Lenovo 
  driver: r8169 v: kernel port: 1000 bus ID: 02:00.0 
  IF: enp2s0 state: down mac: <filter> 
Drives:
  Local Storage: total: 931.51 GiB used: 152.23 GiB (16.3%) 
  ID-1: /dev/sda vendor: Western Digital model: WD10SPZX-24Z10T0 
  size: 931.51 GiB temp: 39 C 
  Optical-1: /dev/sr0 vendor: HL-DT-ST model: DVDRAM GUE0N rev: T.02 
  dev-links: cdrom,cdrw,dvd,dvdrw 
  Features: speed: 24 multisession: yes audio: yes dvd: yes 
  rw: cd-r,cd-rw,dvd-r,dvd-ram state: running 
Partition:
  ID-1: / size: 91.17 GiB used: 57.65 GiB (63.2%) fs: ext4 dev: /dev/sda6 
  ID-2: /home size: 182.34 GiB used: 94.57 GiB (51.9%) fs: ext4 
  dev: /dev/sda8 
  ID-3: swap-1 size: 5.59 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/sda7 
Sensors:
  System Temperatures: cpu: 48.6 C mobo: N/A 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 193 Uptime: 32m Memory: 3.38 GiB used: 1.44 GiB (42.6%) 
  Init: systemd runlevel: 5 Compilers: gcc: 7.5.0 clang: 6.0.0-1ubuntu2 
  Shell: bash v: 4.4.20 inxi: 3.0.32 


```

---

### Post by TheFu on 2021-09-15
Some commercial DVDs have DRM and cannot be mounted.

---

