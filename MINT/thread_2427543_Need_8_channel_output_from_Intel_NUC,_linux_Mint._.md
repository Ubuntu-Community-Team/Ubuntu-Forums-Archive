---
title: "Need 8 channel output from Intel NUC, linux Mint. Please help."
date: 2019-09-23
forum: MINT
---

### Post by scottmayo1 on 2019-09-23
[SIZE=4][FONT=arial][SIZE=3]*Extremely frustrated* [/SIZE][/FONT][/SIZE]describes my situation. I've been banging on this problem for days. Let me describe the goal, because at this point I think I just took the wrong approach. 

I have an Intel NUC running Tessa Linux Mint. My goal is to have independent control of 8 channels of audio. I'm fine if it's 4 sets of stereo channels. I have software that spawns off (and kills) aplay commands in parallel as needed, with -D arguments to select the channel pair in question. It's my own software and it's networked, so at the end of the day my solution might be buy 4 raspberry pis and have them each talk to a USB stereo DAC, and call it done. But I'd *like* to do this with the NUC over HDMI, because I have a SKSL HDMI Digital Audio Converter which claims it will give me the outputs I need, and I'd *like* to avoid buying more hardware. 


My previous attempt involved plugging 4 USB DACs into the NUC, and I got sound out, but I've discovered the cheap USB DACs don't have serial numbers, so which DAC goes to which channel changes on every reboot. I need a solution that's set up once, never touched again, and works predictably every time. So the point of using HDMI is that channels won't wander on reboot.


Note I'm not attempting 7.1 surround music, movies, etc. (Those might be nice). The goal is to synchronize lighting with sound; when lightning flashes on the left side of the room, the left side speakers need to thunder, etc. If I can spawn off handfuls of aplay instances and they predictably play to the speakers I expect, I'm set. And while I'd like to get the HDMI solution working, at the end of the day what I don't have is endless time to "just try" solutions. I've done that for days and I'm fed up. So if after I've posted all the relevant data dumps, I'm really hoping for someone to come along and say "Aha! I can definitively tell you you need to type these three commands..." or likewise, someone to say "oh - no one ever wrote a driver for that hardware that did 8 channel, give up on HDMI." I know I'm being demanding but good mercy why is this even hard?


One thing I cannot risk is bricking the hardware. It runs a lot of other software that family and friends depends on and I don't know enough Linux to undo damage. So if it's rebuilding kernels or making other changes that are fragile or would evaporate on updates, I'll settle for a handful of raspberry pi's.


Anyway, the data that seems to be asked for in these threads - sorry for the length:


```
wget -O alsa-info.sh [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) && chmod +x ./alsa-info.sh && ./alsa-info.sh
[http://alsa-project.org/db/?f=9a8a1a8f97c09f05356c327bc8a1d071064900d5](http://alsa-project.org/db/?f=9a8a1a8f97c09f05356c327bc8a1d071064900d5)



```

```
uname -r
4.15.0-64-generic
```


#I'm guessing this is what should work, but doesn't:
speaker-test -D surround71:CARD=PCH,DEV=0 -c 8




```
speaker-test 1.1.3




Playback device is surround71:CARD=PCH,DEV=0
Stream parameters are 48000Hz, S16_LE, 8 channels
Using 16 octaves of pink noise
Channels count (8) not available for playbacks: Invalid argument
Setting of hwparams failed: Invalid argument


But trying
speaker-test -D surround71:CARD=PCH,DEV=0 -c 2
doesn't return errors, but gives silence (even with the SKSL converter set to stereo)


pavucontrol 
Unable to init server: Could not connect: Connection refused
(But do I need it?)


alsamixer shows Auto-Mute Disabled, Loopback Enabled.
Master, Headphones, Speaker and PCM all have columns in the white (but a green 00 at the bottom). There's no line, front, center, side, rear, etc. There are 5 S/PDIF columns, all blank and showing 00, and I can't get them to change (but presumably I don't care.)


inxi -Fxz
System: Host: lachesis Kernel: 4.15.0-64-generic x86_64 bits: 64 compiler: gcc v: 7.4.0 Console: tty 0 
Distro: Linux Mint 19.1 Tessa base: Ubuntu 18.04 bionic 
Machine: Type: Desktop System: Azulle product: Inspire v: N/A serial: <filter> 
Mobo: INTEL model: SKYBAY serial: <filter> UEFI: American Megatrends v: 5.12 date: 10/10/2017 
CPU: Topology: Dual Core model: Intel Core i5-7200U bits: 64 type: MT MCP arch: Kaby Lake rev: 9 L2 cache: 3072 KiB 
flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 21696 
Speed: 619 MHz min/max: 400/3100 MHz Core speeds (MHz): 1: 600 2: 600 3: 601 4: 600 
Graphics: Device-1: Intel HD Graphics 620 driver: i915 v: kernel bus ID: 00:02.0 
Display: server: X.org 1.19.6 driver: modesetting unloaded: fbdev,vesa tty: 154x34 
Message: Advanced graphics data unavailable in console. Try -G --display 
Audio: Device-1: Intel Sunrise Point-LP HD Audio driver: snd_hda_intel v: kernel bus ID: 00:1f.3 
Device-2: C-Media type: USB driver: hid-generic,snd-usb-audio,usbhid bus ID: 1-7.3:10 
Device-3: C-Media type: USB driver: hid-generic,snd-usb-audio,usbhid 
Sound Server: ALSA v: k4.15.0-64-generic 
Network: Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet driver: r8169 v: 2.3LK-NAPI port: e000 
bus ID: 01:00.0 
IF: enp1s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
Device-2: Intel Wireless 3165 driver: iwlwifi v: kernel port: e000 bus ID: 02:00.0 
IF: wlp2s0 state: up mac: <filter> 
Drives: Local Storage: total: 960.82 GiB used: 187.73 GiB (19.5%) 
ID-1: /dev/sda vendor: Samsung model: SSD 860 EVO M.2 500GB size: 465.76 GiB 
ID-2: /dev/sdb type: USB vendor: Samsung model: Portable SSD T5 size: 465.76 GiB 
ID-3: /dev/sdc type: USB model: SMI USB size: 29.30 GiB 
Partition: ID-1: / size: 456.96 GiB used: 102.94 GiB (22.5%) fs: ext4 dev: /dev/sda2 
Sensors: System Temperatures: cpu: 48.0 C mobo: 29.8 C 
Fan Speeds (RPM): N/A 
Info: Processes: 208 Uptime: 17m Memory: 15.59 GiB used: 828.9 MiB (5.2%) Init: systemd runlevel: 5 Compilers: gcc: 7.4.0 
Shell: bash v: 4.4.20 inxi: 3.0.27 








cat /proc/asound/car*/co* | grep Codec
Codec: Realtek ALC269VC
Codec: Intel Kabylake HDMI


```
lspci -nn
```
00:00.0 Host bridge [0600]: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers [8086:5904] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation HD Graphics 620 [8086:5916] (rev 02)
00:08.0 System peripheral [0880]: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th Gen Core Processor Gaussian Mixture Model [8086:1911]
00:14.0 USB controller [0c03]: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller [8086:9d2f] (rev 21)
00:14.2 Signal processing controller [1180]: Intel Corporation Sunrise Point-LP Thermal subsystem [8086:9d31] (rev 21)
00:16.0 Communication controller [0780]: Intel Corporation Sunrise Point-LP CSME HECI #1 [8086:9d3a] (rev 21)
00:17.0 SATA controller [0106]: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] [8086:9d03] (rev 21)
00:1c.0 PCI bridge [0604]: Intel Corporation Device [8086:9d13] (rev f1)
00:1c.4 PCI bridge [0604]: Intel Corporation Sunrise Point-LP PCI Express Root Port #5 [8086:9d14] (rev f1)
00:1f.0 ISA bridge [0601]: Intel Corporation Sunrise Point-LP LPC Controller [8086:9d58] (rev 21)
00:1f.2 Memory controller [0580]: Intel Corporation Sunrise Point-LP PMC [8086:9d21] (rev 21)
00:1f.3 Audio device [0403]: Intel Corporation Sunrise Point-LP HD Audio [8086:9d71] (rev 21)
00:1f.4 SMBus [0c05]: Intel Corporation Sunrise Point-LP SMBus [8086:9d23] (rev 21)
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
02:00.0 Network controller [0280]: Intel Corporation Wireless 3165 [8086:3165] (rev 81)




```






I'm not sure what else is needed, but I'll happily gather information as directed.


If someone can get this permanently working for me, I'll contribute $40 to a disaster relief charity of mutual agreement: OXFAM, American Red Cross, Doctors without borders, mission groups working in Haiti, etc, It's cheaper than buying several raspberry pis. 


(By the way, why does selecting text and typing not replace the selected text, when typing into this window?).

---

### Post by Frogs Hair on 2019-09-23
*Moved to **Mint.***

---

### Post by scottmayo1 on 2019-09-25
Nada? Is what I'm trying really unusual?

---

### Post by uRock on 2019-09-25
Have you tried Mint's forums? I am not sure if there are any forums for the NUCs, but that may be a place to try as well. I haven't used Mint for years and my sound system is a $20 pair of computer speakers from Target, so I can't be much help on the subject.

---

