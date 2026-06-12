---
title: "Unable writing by DVD writer"
date: 2021-09-14
forum: MINT
---

### Post by pascal111 on 2021-09-14
My Linux is Mint 19 Mate. I tried "brasero" and "xfburn" to burn ISO image of Mint 20 and had  error messages. I checked my DVD driver by some commands form the WEB  like this:

```

pascal@pascal-Lenovo-ideapad-330-15AST:~$ inxi -d
Drives:
  Local Storage: total: 931.51 GiB used: 152.34 GiB (16.4%) 
  ID-1: /dev/sda vendor: Western Digital model: WD10SPZX-24Z10T0 
  size: 931.51 GiB 
  Optical-1: /dev/sr0 vendor: HL-DT-ST model: DVDRAM GUE0N 
  dev-links: cdrom,cdrw,dvd,dvdrw 
  Features: speed: 24 multisession: yes audio: yes dvd: yes 
  rw: cd-r,cd-rw,dvd-r,dvd-ram 
  Optical-2: /dev/sr1 vendor: CDEmu model: CD-ROM dev-links: N/A 
  Features: speed: 48 multisession: yes audio: yes dvd: yes 
  rw: cd-r,cd-rw,dvd-r,dvd-ram 

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
  ID-1: BAT0 charge: 13.5 Wh condition: 14.9/30.6 Wh (49%) 
  model: CPT-COS L16C2PB2 status: Charging 
CPU:
  Topology: Dual Core model: AMD E2-9000 RADEON R2 4 COMPUTE CORES 2C+2G 
  bits: 64 type: MCP arch: Excavator L2 cache: 1024 KiB 
  flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm 
  bogomips: 7199 
  Speed: 1398 MHz min/max: 1200/1800 MHz Core speeds (MHz): 1: 1473 2: 1423 
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
  Local Storage: total: 931.51 GiB used: 152.34 GiB (16.4%) 
  ID-1: /dev/sda vendor: Western Digital model: WD10SPZX-24Z10T0 
  size: 931.51 GiB 
  Optical-1: /dev/sr0 vendor: HL-DT-ST model: DVDRAM GUE0N rev: T.02 
  dev-links: cdrom,cdrw,dvd,dvdrw 
  Features: speed: 24 multisession: yes audio: yes dvd: yes 
  rw: cd-r,cd-rw,dvd-r,dvd-ram state: running 
  Optical-2: /dev/sr1 vendor: CDEmu model: CD-ROM rev: 1.0  dev-links: N/A 
  Features: speed: 48 multisession: yes audio: yes dvd: yes 
  rw: cd-r,cd-rw,dvd-r,dvd-ram state: running 
Partition:
  ID-1: / size: 91.17 GiB used: 57.60 GiB (63.2%) fs: ext4 dev: /dev/sda6 
  ID-2: /home size: 182.34 GiB used: 94.57 GiB (51.9%) fs: ext4 
  dev: /dev/sda8 
  ID-3: swap-1 size: 5.59 GiB used: 170.5 MiB (3.0%) fs: swap dev: /dev/sda7 
Sensors:
  System Temperatures: cpu: 46.2 C mobo: N/A 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 215 Uptime: 2h 24m Memory: 3.38 GiB used: 1.86 GiB (55.0%) 
  Init: systemd runlevel: 5 Compilers: gcc: 7.5.0 clang: 6.0.0-1ubuntu2 
  Shell: bash v: 4.4.20 inxi: 3.0.32 

```

---

### Post by jeremy31 on 2021-09-14
Moved to Mint

---

### Post by guiverc on 2021-09-14
Maybe the drive itself is faulty.

3 of my last 5 writes have required me to replace the DVD writers in boxes. Most DVD burners (*I see anyway*) are getting rather old now, are no longer regularly used, so failures seem rather common.

Where it's a desktop system, replacing the drive is usually pretty easy, though if you don't have a replacement drive, or it's an unusual shape/model, needing to go to a recycler to pick up a second-hand replacement can still be annoying.

I can't/won't help with Mint, but I'd try a burn using *live* media and see if it fails there. If it's *live* media you know works you have a pretty good indication is hardware related & I'd suspect a faulty drive (*to confirm that if you're unsure; use the live media on another box with dvd-burner writing the same project*).

Note:  my current view is very much *colored* by a series of DVD-RW failures; at least one of the writers would still read (*just couldn't burn **except to waste media*); other two easier to detect as faulty/failing drives.

---

### Post by pascal111 on 2021-09-14
My computer is a relative new one, I didn't use its DVD much, it's not corrupted.

---

### Post by ajgreeny on 2021-09-14
Have you checked the mint.iso file you used against the published hashes to make sure it's a good download, or did you download it using a torrent client which checks it as its arrives?

I also wonder why use a DVD?  Booting to USB is generally much a better way to run the live OS and then install it.

---

### Post by pascal111 on 2021-09-17
I installed Ubuntu now and removed Mint, and have the same problem, I'm continuing solving the problem now in the "Hardware" forum.

---

### Post by T6&amp;sfpER35% on 2021-09-18
how did you write the ubuntu ISO to disk to install ubuntu? i mean if the dvd drive doesn't work?

---

