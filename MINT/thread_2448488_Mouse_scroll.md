---
title: "Mouse scroll"
date: 2020-08-08
forum: MINT
---

### Post by Kevin McCready on 2020-08-08
The scrolling function of the mouse is not recognised by my system. Here is the output of 
```
inxi -Fxz

System:    Host: j-Swift-SF514-51 Kernel: 4.8.0-53-generic i686 (32 bit gcc: 5.4.0)
           Desktop: Xfce 4.12.3 (Gtk 2.24.28) Distro: Linux Mint 18.2 Sonya
Machine:   Mobo: Acer model: MiniOne_SK v: V1.11 Bios: Insyde v: V1.11 date: 01/18/2017
CPU:       Dual core Intel Core i5-7200U (-HT-MCP-) cache: 3072 KB
           flags: (lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 10800
           clock speeds: max: 3100 MHz 1: 660 MHz 2: 699 MHz 3: 691 MHz 4: 655 MHz
Graphics:  Card: Intel HD Graphics 620 bus-ID: 00:02.0
           Display Server: X.Org 1.18.4 drivers: intel (unloaded: fbdev,vesa) Resolution: 1920x1080@60.05hz
           GLX Renderer: Mesa DRI Intel HD Graphics 620 (Kaby Lake GT2) x86/MMX/SSE2
           GLX Version: 3.0 Mesa 18.0.5 Direct Rendering: Yes
Audio:     Card Intel Sunrise Point-LP HD Audio driver: snd_hda_intel bus-ID: 00:1f.3
           Sound: Advanced Linux Sound Architecture v: k4.8.0-53-generic
Network:   Card: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter driver: ath10k_pci bus-ID: 02:00.0
           IF: wlp2s0 state: up mac: <filter>
Drives:    HDD Total Size: NA (-) ID-1: /dev/nvme0n1 model: N/A size: 256.1GB
Partition: ID-1: / size: 227G used: 65G (30%) fs: ext4 dev: /dev/nvme0n1p1
           ID-2: swap-1 size: 8.45GB used: 0.00GB (0%) fs: swap dev: /dev/nvme0n1p5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 29.8C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 219 Uptime: 7:31 Memory: 2424.6/7960.2MB Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.481) inxi: 2.2.35

```

---

### Post by jeremy31 on 2020-08-09
Moved to Mint

---

### Post by T6&amp;sfpER35% on 2020-08-09
silly question ...have you tried another mouse?

---

### Post by Kevin McCready on 2020-08-09
It's a great question. The other mouse scrolls down a bit and then reverses direction!!

---

### Post by Kevin McCready on 2020-08-18
Answer. I've now tried four different mice. The answer is that Mint doesn't seem to handle them well. I've finally got one to work which is a simple scrolling mouse from China. It seems that the other mice require special drivers that Mint cannot bypass.

---

