---
title: "no sound with intel card notebook eeepc asus 1018P"
date: 2011-04-24
forum: Multimedia Software
---

### Post by phattch on 2011-04-24
Hi guys,

I have installed a Ubuntu Server 10.10 with fluxbox as X.
Everything works fine except the sound. Either speakers or with headsets, it does not work at ALL.
This is some informations that could help you. i will appreciate your help as when I work, I need to listen music :-)

1) LSPCI result
************************
root@polo-server-linux:/tmp# lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)
*******************************

2) APLAY result
***********************
root@polo-server-linux:/tmp# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC259 Analog [ALC259 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
***********************

3) 
root@polo-server-linux:/tmp# cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.23.

4)[FONT=monospace]
[/FONT]root@polo-server-linux:/tmp# head -n 1 /proc/asound/card0/codec#0 [FONT=monospace]
[/FONT]Codec: Realtek ALC259

5)
I have installed : 
alsa-oss
alsa-tools
alsamixergui
alsa-utils

6)
root@polo-server-linux:/tmp# uname -a
Linux polo-server-linux 2.6.35-28-generic-pae #49-Ubuntu SMP Tue Mar 1 14:58:06 UTC 2011 i686 GNU/Linux

7) /etc/modprobe.d/alsa-base.conf
options snd-hda-intel probe_mask=1 model=auto


Please help me out at least, I would like at least having the headset working :-)

Let me know which logs/informations could help you to troubleshoot the issue.

Much appreciated

Paul

---

### Post by mwl128340 on 2011-04-24
have you looked in alsamixer. i have learned that for some reason default in alsamixer is mute so you may have to unmute your device.
```
alsamixer
```if there is MM then the line is muted. if it is muted then using the M button will unmute.

---

### Post by KegHead on 2011-04-24
Hi!

Have you tried:

system...preferences...sound

uncheck mute.

KegHead

---

### Post by phattch on 2011-04-24
Its not mute, I have checked it out, there is no "M" in alsamixer. 
Any others suggestions ??? I found on google they might be some bugs with ALC259 Analog, dont know if it has been fixed by a new kernel or something else ...

Thanks in advance
Paul

---

### Post by KegHead on 2011-04-24
Hi!

Update your kernel;

sudo apt-get update

sudo apt-get install linux-image -f

Restart

Advise.

KegHead

---

### Post by phattch on 2011-04-24
Hi,
I tried the two commands and get no difference (even after reboot)
If I run pulseaudio command I got this : 

************************
root@polo-server-linux:~# pulseaudio 
W: main.c: This program is not intended to be run as root (unless --system is specified).
E: alsa-util.c: snd_pcm_avail_delay() returned strange values: delay 8 is less than avail 656.
E: alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
************************

What exactly is pulseaudio ? Do you think the problem could be this ?

Thanks in advance for your help

Paul

---

### Post by KegHead on 2011-04-24
[http://en.wikipedia.org/wiki/PulseAudio](http://en.wikipedia.org/wiki/PulseAudio)

---

### Post by KegHead on 2011-04-24
system...admin...synaptic..pulseaudio

install if needed

KegHead

---

### Post by phattch on 2011-04-24
pulseaudio seems already installed ...don't know where it could come from !!!!

---

### Post by mwl128340 on 2011-04-24
pulseaudio should have come pre installed with ubuntu i believe. there is a way to manually check which device works audio. 
```
aplay -D plughw:0,0 /usr/share/sounds/alsa/Front_Center.wav
```from your aplay output this should work and you should hear a front, center voiced audio test. if you do then you may have to tweak pulse audio a lil bit.

---

### Post by phattch on 2011-04-26
I tried to run the command you gave me and got this : 

polo@polo-server-linux:/home/polo $aplay -D plughw:0,0 /usr/share/sounds/alsa/Front_Center.wav
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
aplay: main:654: audio open error: No such file or directory

Then I tried as root and got the sound working.

So I run my firefox as root and not as user and the sound seems working fine.

Do you know why its not working if I run my Firefox as simple user. Should I change some right ?

Thanks in advance
Paul

---

### Post by lidex on 2011-04-27
Go to 'System > Administration > Users and Groups' and make sure your user is in the audio group.

---

