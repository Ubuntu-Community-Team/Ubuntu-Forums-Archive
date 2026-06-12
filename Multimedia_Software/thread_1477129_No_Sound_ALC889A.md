---
title: "No Sound: ALC889A"
date: 2010-05-08
forum: Multimedia Software
---

### Post by fysicsandpholds on 2010-05-08
I am a complete linux beginner you'll have to be patient
I have tried every tutorial and troubleshooting guide that I could follow
I installed the Realtek driver for linux from their site
I followed it step by step

I am running Ubuntu 10.04 on an iMac
nothing is muted
and my system has been restarted
yet there is no sound
any help is greatly appreciated

when I type $ aplay -l
I get:
[INDENT]**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

[/INDENT]when I type $ cat /proc/asound/card0/codec#* | grep Codec
I get:
[INDENT]Codec: Realtek ALC889A
[/INDENT]when i type $ lshw -c multimedia
I get:
[INDENT]  *-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:30 memory:50700000-50703fff
[/INDENT]

---

### Post by lidex on 2010-05-08
OK. Update your kernel:
```
sudo apt-get update
sudo apt-get upgrade
```
Now reboot so we can work with the latest kernel.
Install alsa backports:
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
``` Reboot again.
Check your levels in alsamixer:
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

---

### Post by fysicsandpholds on 2010-05-09
hmmm
the sound still doesnt work
and if I boot in the .22 version (the updated one), the networks card that I worked so hard to get running is not functional again, and nothing but the lowest graphical setting will function

---

### Post by rubenvazquez on 2010-08-30
If its a new install then you have to specify what your using as the output.

When you click on the speaker/volume control icon you can set the preferences.   You can specify digital or analog outputs.  Mess with that a little and see what works.

---

### Post by Marcus209 on 2010-09-12
Hey guys, 

I have an iMac 20' running Ubuntu 10.04 with ALC889A as a sound card, however ubuntu does not recognize this, it used to but after i followed the instructions on this page it disappeared, I used to be able to get sound on my headphones, but not anymore, anyone have any tips? Please help!    [IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

---

