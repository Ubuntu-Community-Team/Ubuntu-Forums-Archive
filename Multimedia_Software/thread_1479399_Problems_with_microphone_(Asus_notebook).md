---
title: "Problems with microphone (Asus notebook)"
date: 2010-05-10
forum: Multimedia Software
---

### Post by zbyszek26104 on 2010-05-10
Hi,

I'm working on Asus G50Vt and my microphone catches no sound after installing Ubuntu 10.04. I was working before on Karmic 9.10 and everything was fine. 

I've checked all options in alsamixer and the only and everything seems to be ok. When I turn i-Mic on I can hear myself from my norebook ;) The only thing I noticed is that only Pulseaudio can't catch my voice (I need it for example in Skype...). What can I do with it?

Zbyszek

---

### Post by xc3RnbFO8P on 2010-05-11
Try **gnome-alsamixer**, and move the balance slider all the way to the left (capture, mic,?)
remember to unmute.

---

### Post by zbyszek26104 on 2010-05-11
Nothing changed..

Any idea?

---

### Post by Froobloops on 2010-06-16
i am having the exact same problem, let me know if you figure it out - otherwise i'll keep looking into it

---

### Post by lidex on 2010-06-19
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by robbinhood on 2010-06-19
At the beginning I can't hear sound from headset nor use micro.So I created a file in /etc/modprobe.d named snd-hda-intel.conf.where I put this line This options gives the better results.

---

### Post by mbi0 on 2010-06-27
> **lidex said:**
> Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)


I got the same computer with the same problem hope this can help solve the problem


```
mbi0@mbi0-pc:~$ uname -a
Linux mbi0-pc 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux
mbi0@mbi0-pc:~$ ^C
mbi0@mbi0-pc:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC663 Digital [ALC663 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
mbi0@mbi0-pc:~$ dpkg -l | grep "alsa"
ii  alsa-base                                  1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                 1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                 4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                         0.10.28-1                                       GStreamer plugin for ALSA
ii  libesd-alsa0                               0.2.41-6ubuntu1                                 Enlightened Sound Daemon (ALSA) - transition
rc  libsdl1.2debian-alsa                       1.2.13-4ubuntu4                                 Simple DirectMedia Layer (with X11 and ALSA 
mbi0@mbi0-pc:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC663

==> /proc/asound/card0/codec#2 <==
Codec: Nvidia MCP78 HDMI

```

---

### Post by flamefury on 2010-09-30
My machine is similar / possibly identical and I have the same problem. An answer to this would be most excellent.

---

### Post by lidex on 2010-09-30
This is wholly dependent on codec and make/model. For Asus ALC663 try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=asus-mode3 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by flamefury on 2010-09-30
You are awesome! The changes you made didn't compromise my headphone functionality (I had previously been using 'model=m51va' in order to have my speakers and headphone work correctly. asus-mode3 works just as well).

Thanks so much for your solution.

---

### Post by yax51 on 2011-01-12
WOOT WOOT!! thanks! for the solution!! it works great!!

:KS:KS:KS:KS:KS:KS:KS

---

