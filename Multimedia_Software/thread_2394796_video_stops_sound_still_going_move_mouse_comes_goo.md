---
title: "video stops sound still going move mouse comes good again"
date: 2018-06-21
forum: Multimedia Software
---

### Post by graham70 on 2018-06-21
Gday 
I will be playing a video from the internet eg netflix, youtube  or from a memory card the video will play but randomly stop with the sound still going until i move the mouse any help will be great running ubuntu 18.04

---

### Post by ajgreeny on 2018-06-21
Give us full details of your hardware.

A good place to start is with command **inxi -F** and then copy back here the terminal output.

Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by graham70 on 2018-06-21
thanks ajgreeny for your quick response here is the inxi -f output 

```
System:
  Host: tvlaptop Kernel: 4.15.0-23-generic x86_64 bits: 64 
  Desktop: Gnome 3.28.1 Distro: Ubuntu 18.04 LTS 
Machine:
  Type: Laptop System: ASUSTeK product: X555UA v: 1.0 
  serial: G4N0CV16B829175 
  Mobo: ASUSTeK model: X555UA v: 1.0 serial: BSN12345678901234567 
  UEFI: American Megatrends v: X555UA.206 date: 01/23/2016 
Battery:
  ID-1: BAT0 charge: 33.3 Wh condition: 34.0/37.3 Wh (91%) 
CPU:
  Topology: Dual Core model: Intel Core i7-6500U bits: 64 type: MT MCP 
  L2 cache: 4096 KiB 
  Speed: 500 MHz min/max: 400/3100 MHz Core speeds (MHz): 1: 500 2: 500 
  3: 500 4: 500 
Graphics:
  Card-1: Intel HD Graphics 520 driver: i915 v: kernel 
  Display: server: X.Org 1.19.6 driver: modesetting unloaded: fbdev,vesa 
  resolution: 4096x2160~24Hz 
  OpenGL: renderer: Mesa DRI Intel HD Graphics 520 (Skylake GT2) 
  v: 4.5 Mesa 18.0.0-rc5 
Audio:
  Card-1: Intel Sunrise Point-LP HD Audio driver: snd_hda_intel 
  Sound Server: ALSA v: k4.15.0-23-generic 
Network:
  Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  driver: r8169 
  IF: enp2s0 state: up speed: 1000 Mbps duplex: full mac: 34:97:f6:b7:89:d8 
  Card-2: Qualcomm Atheros AR9485 Wireless Network Adapter driver: ath9k 
  IF: wlp3s0 state: down mac: 74:c6:3b:2f:f7:15 
Drives:
  HDD Total Size: 931.51 GiB used: 13.36 GiB (1.4%) 
  ID-1: /dev/sda vendor: Seagate model: ST1000LM024 HN-M101MBB 
  size: 931.51 GiB 
Partition:
  ID-1: / size: 264.42 GiB used: 13.33 GiB (5.0%) fs: ext4 dev: /dev/sda6 
  ID-2: swap-1 size: 11.90 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/sda7 
Sensors:
  System Temperatures: cpu: 54.0 C mobo: N/A 
  Fan Speeds (RPM): cpu: 3500 
Info:
  Processes: 322 Uptime: 18m Memory: 11.63 GiB used: 2.07 GiB (17.8%) 
  Shell: bash inxi: 3.0.12 

```
I hope this helps you or someone else to help me thanks

---

### Post by #&amp;thj^% on 2018-06-21
Not really as your Specs I can see no obvious reasons for the random stops.
Gnome is a bit heavier as far as a DE gose, and just wondering if you have tried a lighter DE like Lubuntu (LXDE) or Xubuntu (XFCE) or Mate (Forked from Gnome2)?
Also with Xubuntu watching video's from any player with firefox opened with multiple tabs has shown me some very small glitch's
My Specs should be able to run these very nicely.and do for other OS's I have installed.
```
sudo inxi -xxxm
[sudo] password for me: 
Memory:
  RAM: total: 11.64 GiB used: 1.33 GiB (11.4%) 
  Array-1: capacity: 32 GiB slots: 2 EC: None max module size: 16 GiB 
  note: est. 
  Device-1: XMM1 size: 4 GiB speed: 2133 MT/s type: DDR4 detail: synchronous 
  bus width: 64 bits total: 64 bits manufacturer: Samsung 
  part-no: M378A5143EB1-CPB serial: 334983A7 
  Device-2: XMM3 size: 8 GiB speed: 2400 MT/s type: DDR4 detail: synchronous 
  bus width: 64 bits total: 64 bits manufacturer: Kingston 
  part-no: HP24D4U7S8MBP-8 serial: 06105D16 
```

Graphics:
```
inxi -G
Graphics:
  Card-1: Intel HD Graphics 530 driver: i915 v: kernel 
  Card-2: NVIDIA GF114 [GeForce GTX 560 Ti] driver: nvidia v: 390.67 
  Display: x11 server: X.Org 1.20.0 driver: intel,nvidia 
  resolution: 1920x1080~60Hz 
  OpenGL: renderer: GeForce GTX 560 Ti/PCIe/SSE2 v: 4.6.0 NVIDIA 390.67 


```
When I use a swap it never shows any usage. So I'm wondering either some bad software from a PPA (If you have any in use) or possible hardware problems, but your specs should run a lot better than you are seeing now.
BTW your CPU seems to be running a bit on the Hot side, have you clean your lappy lately with some Air?
```
inxi -xxxC
CPU:
  Topology: Quad Core model: Intel Core i5-6400 bits: 64 type: MCP 
  arch: Skylake-S rev: 3 L2 cache: 6144 KiB 
  flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 21704 
  Speed: 2502 MHz min/max: 800/3300 MHz Core speeds (MHz): 1: 900 2: 900 
  3: 900 4: 900 

```
Mine Seldom run higher than 32C unless I'm maxing out with Video editing then I will see Temps rise to what you are now seeing @50C
After running 7 tabs on firefox and playing a game "Asylum" and having a Video opened VLC my Temp is:
```
printf '%d°\n' $(sensors | grep 'id 0:' | awk '{ print $4 }') 2>/dev/null
43°

```
With outside Temp @ (88 F) Conditions: Clear.

---

### Post by ajgreeny on 2018-06-21
I don't really know, but I wonder if your 4K resolution monitor is part of the problem you're seeing with a relatively low resource graphics system.

Wait for other answers before you accept this as likely to be the cause as I may be completely wrong about this.

---

### Post by mjsrsc on 2018-06-22
I've the same problem. All browsers based on Chromium have problems. The only one that work is FireFox.

---

### Post by graham70 on 2018-06-23
Gday
Thanks to ajgreeny 1fallen and mjsrsc for your help I down loaded the kubuntu desktop all working now. Just one question my video will stop and only movement of the the mouse will it play again why . One other thing the running at higher then normal temp could be due to the lap top screen is turned off and closed. Should I mark this solved or not as it will still not working under ubuntu. Thanks again

---

### Post by kazakore on 2018-06-23
Is it definitely random and not after a fixed time? Sound like the symptoms from a badly configured screensaver to me.....

---

### Post by mjsrsc on 2018-06-23
@kazakores, It's random between 5 and 15 seconds

---

### Post by graham70 on 2018-06-29
there were no screen savers install gone to kde full install all good . I don't think it was totally random it depends on the video some were very bad some one or two time the whole movie don't know if it was video quality related.

---

### Post by Antoon Stessels on 2018-07-08
> **graham70 said:**
> Gday 
I will be playing a video from the internet eg netflix, youtube or from a memory card the video will play but randomly stop with the sound still going until i move the mouse any help will be great running ubuntu 18.04

I have been having the same issue, and agree with others: it is a Chrome issue, that has recently cropped up in GNOME. In Firefox, everything works fine.

I don't know how to solve this. Anyone?

---

### Post by rikial on 2018-12-20
I found a fix without any throwbacks!

It's sufficient to start chromium with the flag --disable-gpu-vsync and the problem completely goes away.

It's possible to make chromium start with this flag by default, just execute this command in the terminal, restart chrome and the issue will be gone forever:

```
sudo sh -c 'echo "CHROMIUM_FLAGS=--disable-gpu-vsync" > /etc/chromium-browser/customizations/10-gpufix'
```

---

