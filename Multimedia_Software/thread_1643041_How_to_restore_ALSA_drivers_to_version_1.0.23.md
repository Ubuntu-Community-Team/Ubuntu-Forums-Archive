---
title: "How to restore ALSA drivers to version 1.0.23?"
date: 2010-12-11
forum: Multimedia Software
---

### Post by fteo on 2010-12-11
Hi all, I am a noob at Linux & Ubuntu. I've followed [some instructions]("http://forums.m-audio.com/showthread.php?714-Not-a-problem.-FastTrack-on-linux&p=91557#post91557") to patch, compile & install the ALSA git repository in order to make my M-Audio Fast Track Ultra to work properly. After installing and rebooting there is no sound and in fact, in the hardware tab in Sound Preferences there's no device shown. The problem exists only when I boot using the 2.6.35-23-generic kernel. When I boot using the 2.6.35-22-generic kernel there's no problem at all and I can still use my on board sound card (listed as Internal Audio in h/w tab), which was what I was using before installing the patched drivers.

Is there a way to restore the original 1.0.23 ALSA Driver? I tried compiling from source but I get compile errors. Also I've taken a backup of the /etc/ directory -among others- before installing, if that's any use.

if that's any use to you:
in 2.6.35-23
```
$ aplay -l
aplay: device_list:235: no soundcards found...

``````
$ sudo lshw -c sound
  *-multimedia UNCLAIMED  
       description: Multimedia audio controller
       product: CK804 AC'97 Audio Controller
       vendor: nVidia Corporation
       physical id: f
       bus info: pci@0000:00:04.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0 maxlatency=5 mingnt=2
       resources: ioport:f000(size=256) ioport:ec00(size=256) memory:febfd000-febfdfff

``````
$ cat /proc/asound/cards
cat: /proc/asound/cards: No such file or directory

``````
$ cat /proc/asound/devices 
cat: /proc/asound/devices: No such file or directory

``````
$ cat /proc/asound/version
cat: /proc/asound/version: No such file or directory

```
in 2.6.35-22
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Ultra [Fast Track Ultra], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


``````
$ sudo lshw -c sound
    *-multimedia            
       description: Multimedia audio controller
       product: CK804 AC'97 Audio Controller
       vendor: nVidia Corporation
       physical id: f
       bus info: pci@0000:00:04.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2
       resources: irq:22 ioport:f000(size=256) ioport:ec00(size=256) memory:febfd000-febfdfff

``````
$ cat /proc/asound/cards
  0 [Ultra          ]: USB-Audio - Fast Track Ultra
                      M-Audio Fast Track Ultra at usb-0000:00:02.1-10, high speed
 1 [U0x46d0x9a1    ]: USB-Audio - USB Device 0x46d:0x9a1
                      USB Device 0x46d:0x9a1 at usb-0000:00:02.1-5, high speed
 2 [CK804          ]: NFORCE - NVidia CK804
                      NVidia CK804 with ALC850 at irq 22

``````
$ cat /proc/asound/devices 
  2:        : timer
  3:        : sequencer
  4: [ 1- 0]: digital audio capture
  5: [ 1]   : control
  6: [ 0- 0]: digital audio playback
  7: [ 0- 0]: digital audio capture
  8: [ 0]   : control
  9: [ 2- 2]: digital audio playback
 10: [ 2- 1]: digital audio capture
 11: [ 2- 0]: digital audio playback
 12: [ 2- 0]: digital audio capture
 13: [ 2]   : control

``````
$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.

```

---

### Post by fteo on 2010-12-12
I've tried following the "**[Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449")**" sticky topic and didn't have any results. The "Getting the ALSA drivers from a *fresh* kernel" step didn't give me any results and when I tried compiling from source I got compile error.

I have even tried reinstalling the 2.6.35-23-generic kernel from synaptic, but it seems the configuration for that kernel in alsa remains the same even after removing it completely.

Is there any way to copy the configuration I'm using in 2.6.35-22 to 2.6.35-23?

Any help would be greatly appreciated!

---

### Post by lidex on 2010-12-12
Boot into the .23 kernel and try this:
Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**Reboot.**
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**

---

### Post by fteo on 2010-12-12
Well that was mentioned on the guide I posted above, and I tried again with no results. I still get the same results with aplay -l etc. (and obviously no sound). Any ideas?

---

### Post by Yellow Pasque on 2010-12-12
I would completely remove/purge the problematic kernel and reinstall it.

---

### Post by fteo on 2010-12-12
I tried removing it completely via synaptic but I got no results. How can I purge it using the terminal?

---

### Post by fteo on 2010-12-14
Ok I managed to solve the problem. I post the solution here for future reference. I removed the problematic kernel using:
```
sudo apt-get remove --purge linux-headers-2.6.35-23 linux-headers-2.6.35-23-generic linux-image-2.6.35-23-generic
```
I figured out that there were some files left in /lib/modules/2.6.35-23/
So I removed that folder:
```
sudo rm -rf /lib/modules/2.6.35-23-generic/
```
And then reinstalled the kernel packages via synaptic, or by:
```
sudo apt-get install linux-headers-2.6.35-23 linux-headers-2.6.35-23-generic linux-image-2.6.35-23-generic
```
I booted into 2.6.35-23 generic, and that was it. Sound configuration was just like in 2.6.35-22.

Thanks everyone for the help.

---

### Post by efflandt on 2010-12-15
Neither the alsa nor kernel purge/reinstall seems to restore my Maverick sound before X starts.  So I get no login prompt or X startup sound.  And if I go to console from login gui before logging in **aplay -l** just hangs.  Although, strangely alsamixer appears to properly show the sound devices.  After X starts, aplay -l works properly and audio works fine analog or HDMI.

I had used ubuntu-audio-dev/ppa during the -22 kernel to get HDMI sound working for nvidia GT 430 (a new model).  I no longer needed the ppa for 2.6.35-23 which supports HDMI audio for my card (with just a one-liner in /etc/pulse/default.pa).  But apparently I did not get everything removed from the ppa when I uninstalled and unchecked the ppa in Synaptic.  Login prompt and gnome startup sound work fine in Maverick with all updates booted from USB hard drive on that same computer, so it is not a hardware issue.

Any other ideas what might be lingering from the ppa?

---

