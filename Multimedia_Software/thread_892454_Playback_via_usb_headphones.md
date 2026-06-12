---
title: "Playback via usb headphones"
date: 2008-08-17
forum: Multimedia Software
---

### Post by Mattt on 2008-08-17
Hi all,

I've been trying to get my usb headphone working for a few days now, I'm going around in circles.

I can play music in Amarok, via my speakers, it sounds great.  Better than it did in Vista, great.
I want to be able to listen via my Logitech USB headphones too.
When I connect the headphones I hear the Ubuntu startup sound, and that sounds fine.

In Amarok, Settings, Configure Amarok;

```

Sound system is 'xine engine'
Xine config is : Alsa
Mono:Default
Stereo:Default
4 Channels:plug:surround40:0
6 Channels:plug:surround51:0
Speaker Arrangement: 5.1

```
I double click the volume control on the top panel of the desktop.
File, Change Device, three options:
0 HDA Intel (alsa mixer)
1 Logitech USB Headphones (alsa mixer)
2 Realtek ALC888 (OSS mixer)

Device 0 is selected.

If I select Device 1, the headphones, I can see it's not muted.
and as I mentioned, I hear the startup sound when I plug them in.

So how do I get music to the headphones?

Thanks

Matt

---

### Post by benbelly on 2008-08-22
I have the same problem.  Are there any suggestions?

---

### Post by spegru on 2008-09-27
I also have this problem.
I used the autodetect settings in Amarok. In fact if I try Alsa or Pulse I get a warning that xine engine cannot initialise drivers, so I think the autodetect is using OSS.

I can't see any way to select my USB headphones and actually i dont understand why neither pulse nor Alsa works with amarok

by the way the usb headphones are listed under volume control and do work ok with skype

I am on kubuntu 8.04

help please
spegru

---

### Post by markbuntu on 2008-09-27
For one thing, Kubuntu does not come with pulseaudio so you have to get it yourself. Do you have the amarok engines?
They are a separate package that contains the amarok plugins for alsa and pulseaudio.

You should be able to select your headphones in the volume control. If you have pulseaudio, you should be able to select your usb headphones in the PA Volume Control.

---

### Post by spegru on 2008-09-29
I do have pulse audio, because as I should have mentioned, my system is actually Ubuntu with the Kubuntu-desktop installed on top.

However I cannot get Amarok to work with pulse because it complains that xine could not initialise any drivers.

any Ideas?

spegru

---

### Post by markbuntu on 2008-09-29
You are probably missing the xine plugins:

libxine-all-plugins

or

libxine-misc-plugins

You probably have this already but it doesn't hurt to check

amarok-xine

I am running amarok with the xine engine and the pulseaudio plugin and it works great for me so don't give up yet.

You may also be missing these:
libasound2
libasound2-plugins
gstreamer0.10-pulseaudio (may not be relevant)
pulseaudio-esound-compat

You can also look through my 100,000 page guide here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by philetus on 2008-11-16
I've tried everything posted and nothing works.Maybe someone can figure it out.

$ cat /proc/bus/input/devices

I: Bus=0003 Vendor=0d8c Product=000c Version=0100
N: Name="C-Media USB Headphone Set  "
P: Phys=usb-0000:00:02.0-7/input3
S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb1/1-7/1-7:1.3/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=13
B: KEY=e0000 0 0 0
B: MSC=10

asoundconf list

Names of available sound cards:
CK804
default

$ asoundconf set-default-card Headphone Set
You have omitted a necessary parameter.  Please see the output from `asoundconf list`, and use one of those sound card(s) as the parameter.

 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [C-Media USB Headphone Set  ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by markbuntu on 2008-11-16
In the Pulseaudio Volume Control (pavucontrol) you should be able to change the playing stream to the usb headphones by right clicking on it and choosing move stream. 

In the Pulse Audio Preferences (papref) you can check the box in Simultaneous Output and then choose the Simultaneous output.....virtual device in pavucontrol for both speaker and usb headset output.

You should set pulse as the default in asound.conf. You can do this easily with asoundconf-gtk which will appear as Default Sound Card in the Preferences menu.

---

### Post by philetus on 2008-11-17
I did this:
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

This:
 sudo apt-get install linux-sound-base alsa-base alsa-utils

This:
 sudo apt-get install gdm ubuntu-desktop

and rebooted.My headphones work.

I had to turn the speakers off, but that is not a hardship. When I want speakers, I'll turn them back on.

---

### Post by psyke83 on 2008-11-17
> **Mattt said:**
> Hi all,

I've been trying to get my usb headphone working for a few days now, I'm going around in circles.

If you're actually running **U**buntu (i.e. the GNOME version) with Amarok installed, then you should use PulseAudio (and its configuration utilities) to choose different audio devices.

If you're using GNOME as I suspect (when you plug in a headset and hear the startup sound, that's usually caused by PulseAudio's hotplug detection), look at the FAQ of the [PulseAudio Fixes]("http://ubuntuforums.org/showthread.php?t=789578") thread - it explains how you can choose a different playback device per-application, and also change between audio devices on-the-fly.

You should not configure Amarok explicitly - instead, leave the configuration at its defaults so that it will use PulseAudio.

---

### Post by erikthedrink on 2009-09-08
Since your USB headphones are listed as device 1, use this in a Terminal Window

[FONT=Georgia][SIZE=4]asoundconf set-default-card 1[/SIZE][/FONT]

Then close and re-open your browser (Mozilla Firefox) or restart your system.
:KS
Note, if you unplug your usb headphones, your laptop speakers will take over.  In order to re-establish contact with the usb headphones, you will need to (plug them back in) restart the system.

---

