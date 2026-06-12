---
title: "Free Alt+mouse button"
date: 2020-04-02
forum: MINT
---

### Post by pascal111 on 2020-04-02
I want to free Alt+left mouse button.
My system info.:

```

pascal@pascal-Lenovo-ideapad-330-15AST:~$ inxi -Fxzd 
System:
  Host: pascal-Lenovo-ideapad-330-15AST Kernel: 5.0.0-32-generic x86_64 
  bits: 64 compiler: gcc v: 7.4.0 Desktop: MATE 1.22.2 
  Distro: Linux Mint 19.3 Tricia base: Ubuntu 18.04 bionic 
Machine:
  Type: Laptop System: LENOVO product: 81D6 v: Lenovo ideapad 330-15AST 
  serial: <filter> 
  Mobo: LENOVO model: LNVNB161216 v: No DPK serial: <filter> 
  UEFI [Legacy]: LENOVO v: 8UCN06WW date: 04/10/2018 
Battery:
  ID-1: BAT0 charge: 10.2 Wh condition: 24.4/30.6 Wh (80%) 
  model: CPT-COS L16C2PB2 status: Charging 
CPU:
  Topology: Dual Core model: AMD E2-9000 RADEON R2 4 COMPUTE CORES 2C+2G 
  bits: 64 type: MCP arch: Excavator L2 cache: 1024 KiB 
  flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm 
  bogomips: 7199 
  Speed: 1199 MHz min/max: 1200/1800 MHz Core speeds (MHz): 1: 1202 2: 1213 
Graphics:
  Device-1: AMD Stoney [Radeon R2/R3/R4/R5 Graphics] vendor: Lenovo 
  driver: amdgpu v: kernel bus ID: 00:01.0 
  Display: x11 server: X.Org 1.19.6 driver: amdgpu,ati 
  unloaded: fbdev,modesetting,radeon,vesa resolution: 1366x768~60Hz 
  OpenGL: renderer: AMD STONEY (DRM 3.27.0 5.0.0-32-generic LLVM 9.0.0) 
  v: 4.5 Mesa 19.2.8 direct render: Yes 
Audio:
  Device-1: AMD vendor: Lenovo driver: snd_hda_intel v: kernel 
  bus ID: 00:01.1 
  Device-2: AMD Family 15h Audio vendor: Lenovo driver: snd_hda_intel 
  v: kernel bus ID: 00:09.2 
  Sound Server: ALSA v: k5.0.0-32-generic 
Network:
  Device-1: Realtek RTL8821CE 802.11ac PCIe Wireless Network Adapter 
  vendor: Lenovo driver: rtl8821ce v: v5.2.5.2.1_xxxx.20181112_beta 
  port: 2000 bus ID: 01:00.0 
  IF: wlp1s0 state: up mac: <filter> 
  Device-2: Realtek RTL810xE PCI Express Fast Ethernet vendor: Lenovo 
  driver: r8169 v: kernel port: 1000 bus ID: 02:00.0 
  IF: enp2s0 state: down mac: <filter> 
  IF-ID-1: elfr3on state: up speed: N/A duplex: N/A mac: <filter> 
Drives:
  Local Storage: total: 931.51 GiB used: 64.16 GiB (6.9%) 
  ID-1: /dev/sda vendor: Western Digital model: WD10SPZX-24Z10T0 
  size: 931.51 GiB 
  Optical-1: /dev/sr0 vendor: HL-DT-ST model: DVDRAM GUE0N rev: T.02 
  dev-links: cdrom,cdrw,dvd,dvdrw 
  Features: speed: 24 multisession: yes audio: yes dvd: yes 
  rw: cd-r,cd-rw,dvd-r,dvd-ram state: running 
Partition:
  ID-1: / size: 91.17 GiB used: 40.56 GiB (44.5%) fs: ext4 dev: /dev/sda6 
  ID-2: /home size: 182.34 GiB used: 23.60 GiB (12.9%) fs: ext4 
  dev: /dev/sda8 
  ID-3: swap-1 size: 5.59 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/sda7 
Sensors:
  System Temperatures: cpu: 45.2 C mobo: N/A gpu: amdgpu temp: 45 C 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 173 Uptime: 27m Memory: 3.45 GiB used: 1.20 GiB (34.8%) 
  Init: systemd runlevel: 5 Compilers: gcc: 7.4.0 Shell: bash v: 4.4.20 
  inxi: 3.0.32 
pascal@pascal-Lenovo-ideapad-330-15AST:~$ 

```

---

### Post by CelticWarrior on 2020-04-03
What exactly do you mean by "free Alt+left mouse button"?

---

### Post by pascal111 on 2020-04-03
I have an application that uses Alt+left mouse button to make a function, Mint uses the same keys shortcut to move windows, I want remove that from Mint to make the application able to function.

---

