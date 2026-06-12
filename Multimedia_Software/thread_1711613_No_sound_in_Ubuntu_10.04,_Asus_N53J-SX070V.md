---
title: "No sound in Ubuntu 10.04, Asus N53J-SX070V"
date: 2011-03-21
forum: Multimedia Software
---

### Post by Keeepcool on 2011-03-21
Hello, after searching a lot and trying to re-install Alsa and pulse-audio, trying the older kernell, editing the alsa-config files and a lot of reboots I cant get any sound out of my new laptop.
It worked 2 or 3 times, and if I leaved Windows with audio disabled it would never work in Ubuntu, but now I cant ever get any sound from my speaker, do any one can help me?
The laptop is pretty new/recent, and it as an Bang&Olufsen ICEpower speaker with a gorgeous quality that I never expected from a laptop.
I use Ubuntu in a lot of my programming classes and at home to to study and also to program micro-controllers and to play a bit with open-cv to do some image processing.
So having sound is almost a must, programming hours and hours with no sound is driving me crazy :/

The laptop an a Core i7 64 bits processor but I'm using a 32 bits Ubuntu 10.04 because I'm also part of the robotic soccer team of my university and they can run code compiled in 64 bits machines so I just opted from the 32 bits distro to remain compatible, everything is working fine now, the graphics card as also given some fight, but its now running perfectly.

So, this is the output of some commands that might be usefull for anyone willing to help me:
```
tiago@tiago-laptop:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC269

tiago@tiago-laptop:~$ uname -r
2.6.32-30-generic


tiago@tiago-laptop:~$ lspci -v -v
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device 1113
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 22
    Region 0: Memory at d9600000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

```

But if I use lspic -v or only lspci it says this:
```
01:00.1 Audio device: nVidia Corporation Device 0bea (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device 1522
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at d3080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>

```

Dont understand why one says its Realtek and the other says Nvidia..
If anyone as ideas just shoot them off!
Thanks in advance.

---

### Post by lidex on 2011-03-21
So, if you are in windows and boot into ubuntu, audio works? Unless it's disabled there? Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Keeepcool on 2011-03-22
No, I tough that the problem was that, but its not, I think I'm being hit by the new kernel problem, because after I made the update I lost all my sound.
The problem was that the keyboard as dedicated buttons to control the sound and I didn't notice that they weren't working, using the usual fn+f12 gave me the supposed lost sound, but this was before the kernel update, now its silent.
I will try that, thanks for the help.

Here is the link that the script generated:
[http://www.alsa-project.org/db/?f=9f01c9bf03edcd56ddd3aae79471b2f384197be4](http://www.alsa-project.org/db/?f=9f01c9bf03edcd56ddd3aae79471b2f384197be4)

---

### Post by lidex on 2011-03-22
What do you get for this:
```
dpkg -l | grep "alsa"
```

---

### Post by Keeepcool on 2011-03-23
Sorry for the delay in the responde, here is the output:
> [QUOTE]tiago@tiago-laptop:~$ dpkg -l | grep "alsa"
ii  alsa-base                                 1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-oss                                  1.0.17-3                                        ALSA wrapper for OSS applications
ii  alsa-utils                                1.0.22-0ubuntu5                                 ALSA utilities
ii  alsamixergui                              0.9.0rc2-1-9                                    graphical soundcard mixer for ALSA soundcard
ii  bluez-alsa                                4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                        0.10.28-1                                       GStreamer plugin for ALSA
[/QUOTE]

---

### Post by lidex on 2011-03-23
OK, I'll need you to purge and re-install alsa.
Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```

---

### Post by Keeepcool on 2011-03-24
It works!!!!!!!!!
Thank you a LOT for helping me to solve this problem mr. Lidex.

---

### Post by Vektor67 on 2011-03-24
> **lidex said:**
> OK, I'll need you to purge and re-install alsa.
Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```

God I hope this works for me, This is the first cogent advice I've found after an entire evening of searching. Asus p5Q Deluxe here. wish me luck

---

### Post by Vektor67 on 2011-03-24
Nothing,I'll start my own thread we'll leave this one on a positive note.

---

