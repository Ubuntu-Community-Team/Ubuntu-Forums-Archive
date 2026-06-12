---
title: "No sound via headphones"
date: 2020-03-02
forum: Multimedia Software
---

### Post by arisdel on 2020-03-02
No sound via headphones. the speakers work well.
Sys info:
```
aris@aris-laptop:~$ inxi -F
System:
Host: aris-laptop Kernel: 5.3.0-40-generic x86_64 bits: 64
Desktop: Xfce 4.14.1 Distro: Ubuntu 19.10 (Eoan Ermine)
Machine:
Type: Laptop System: Hewlett-Packard product: N/A v: Rev 1
serial: <root required>
Mobo: Quanta model: 306A v: 21.10 serial: <root required>
BIOS: Hewlett-Packard v: F.08 date: 07/16/2009
Battery:
ID-1: BAT0 charge: 100% condition: N/A/47.5 Wh
CPU:
Topology: Dual Core model: Pentium T4200 bits: 64 type: MCP
L2 cache: 1024 KiB
Speed: 1197 MHz min/max: 1200/2000 MHz Core speeds (MHz): 1: 1197 2: 1197
Graphics:
Device-1: NVIDIA G98M [GeForce G 103M] driver: nvidia v: 340.107
Display: x11 server: X.Org 1.20.5 driver: nvidia
unloaded: fbdev,modesetting,nouveau,vesa resolution: 1366x768~60Hz
OpenGL: renderer: GeForce G 103M/PCIe/SSE2 v: 3.3.0 NVIDIA 340.107
Audio:
Device-1: Intel 82801I HD Audio driver: snd_hda_intel
Sound Server: ALSA v: k5.3.0-40-generic
Network:
Device-1: Qualcomm Atheros AR9285 Wireless Network Adapter driver: ath9k
IF: wlp2s0 state: up mac: 00:26:5e:50:36:2f
Device-2: Realtek RTL810xE PCI Express Fast Ethernet driver: r8169
IF: enp3s0 state: down mac: da:2a:fe:d9:99:63
Drives:
Local Storage: total: 232.89 GiB used: 9.09 GiB (3.9%)
ID-1: /dev/sda vendor: Seagate model: ST9250315AS size: 232.89 GiB
Partition:
ID-1: / size: 228.23 GiB used: 9.09 GiB (4.0%) fs: ext4 dev: /dev/sda1
Sensors:
System Temperatures: cpu: 47.0 C mobo: N/A gpu: nvidia temp: 49 C
Fan Speeds (RPM): N/A
Info:
Processes: 194 Uptime: 11m Memory: 3.81 GiB used: 1.35 GiB (35.5%)
Shell: bash inxi: 3.0.36
```
I can't find solution

---

### Post by Autodave on 2020-03-02
Until someone else comes along with way more smarts than myself, try this: I get well over 1/2 of mine working:

Power off machine completely.  Plug headphones in.  Power up and see if they work.

---

### Post by ajgreeny on 2020-03-02
Make sure you have the **pavucontrol** package installed; this is the **pulseaudio volume control** which you open from clicking the volume icon in the panel, clicking on Audio Mixer from that.

Go to the **Output devices** tab and in that you will see that headphones and speakers are controlled separately (see my screenshot) and you may find that headphones are muted.

---

### Post by Yellow Pasque on 2020-03-04
If you tell us what laptop you have (all inxi tells us is some kind of HP laptop), maybe there is a fix for it in the upstream kernel.
Maybe this could shed some light too: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

