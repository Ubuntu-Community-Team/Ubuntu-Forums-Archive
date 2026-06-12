---
title: "Rhythm box plays music through headphones and monitor"
date: 2010-07-24
forum: Multimedia Software
---

### Post by spliceroverlord on 2010-07-24
Hi, I recently installed ubuntu Luci Lynx, and, I like to listen to music whilst browsing the net. When I fired up rhythm box, I wanted to listen to music through my headphones. I started a song up, and as soon as it started playing, audio was transferring through both the monitor and my headphones. Help would be greatly appreciated :)

Thanks.

P.S. I would prefer a fix that didn't involve just having to remember to turn the volume down on my monitor every time I intend to use headphones

---

### Post by lidex on 2010-07-26
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

### Post by luctor on 2010-07-26
Had the same issue with my PC.
I have a hda-intel soundchip and followed the guide on the wiki:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
That solved it ..

---

### Post by typal on 2010-07-26
Is it only when you play music through Rhythmbox? Or system-wide sounds? If the latter, check under System > Preferences > Sound & check the output tab. There should be a drop down menu to select where audio is played from. Select an option similar to "analog headphones."

---

### Post by spliceroverlord on 2010-07-27
Hi,
the terminal command outputs are as follows:
```
uname -a
Linux oliver-desktop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

```
```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
```
dpkg -l | grep "alsa"
ii  alsa-base                              1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                             1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                             4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                     0.10.28-1                                       GStreamer plugin for ALSA

```
```
head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC1200
```

My system is a compaq presario SR5120AN, I recently converted from windows vista, I hope this info helps.
Thanks

---

### Post by spliceroverlord on 2010-07-27
Also, I forget to mention in my last post, the sound issue is system wide, and I tried typal&#347; solution, but that just seems to cut off sound from the headphones entirely.
Thanks

---

### Post by typal on 2010-07-27
> **spliceroverlord said:**
> Also, I forget to mention in my last post, the sound issue is system wide, and I tried typal&#347; solution, but that just seems to cut off sound from the headphones entirely.
Thanks

What other options are in that drop down menu? What is selected when sounds are going through both (headphones/monitor)? What's listed under "Devices?"

Right now, I'm picturing your monitor connected to the jack at the back of your machine, while your headphones are connected to the front. When the headphones are plugged in, you want the output from the back of the computer to stop. Is that correct?

---

### Post by lidex on 2010-07-27
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel probe_mask=1 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

After all that port this output please:
```
dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
```

---

### Post by spliceroverlord on 2010-07-28
Hi again,
the terminal output is as follows:
```
dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
[   10.519002] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 21
[   10.519010] HDA Intel 0000:00:05.0: PCI INT B -> Link[AAZA] -> GSI 21 (level, low) -> IRQ 21
[   10.519015] hda_intel: Disable MSI for Nvidia chipset
[   10.519040] HDA Intel 0000:00:05.0: setting latency timer to 64
[   10.522231] vga16fb: initializing
--
[   11.084476] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   11.112121] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:05.0/input/input5
[   11.182840] [drm] nouveau 0000:00:0d.0: Allocating FIFO number 1

```
thanks for the help.

---

### Post by lidex on 2010-07-28
OK. Did the alsa-base.conf edit help?

---

### Post by spliceroverlord on 2010-07-28
Nope, music still plays through monitor and headphones :/

---

### Post by lidex on 2010-07-28
Try gnome-alsamixer.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

---

### Post by spliceroverlord on 2010-07-28
Hi, I ran into a problem whilst trying to install the alsamixer,
when I tried to run it, it couldn't find it, so I tried the install command, and it returned this output:
```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```
Help?

**EDIT** just closed all of my programs, it's working fine now

---

### Post by spliceroverlord on 2010-07-28
What am I looking for in the alsamixer?

---

### Post by lidex on 2010-07-30
> **spliceroverlord said:**
> What am I looking for in the alsamixer?

Winning lottery numbers.
Sorry, couldn't resist. You want to make sure all options are enabled such as jack-sense or other headphone options that would govern automute of mains when HP plugged in.

---

