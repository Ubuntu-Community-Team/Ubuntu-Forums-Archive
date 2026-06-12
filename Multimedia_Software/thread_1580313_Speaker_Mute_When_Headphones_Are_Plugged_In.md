---
title: "Speaker Mute When Headphones Are Plugged In"
date: 2010-09-23
forum: Multimedia Software
---

### Post by mastermindg on 2010-09-23
I'm just installed 10.04 on a new Gateway DX4300. The integrated sound card is a Realtek AC1200. Sound works great, however, I'd like the rear input to mute when I plugin my headphones in the front input. 

Where can I configure this?

Here's some basic information:
```

!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Thu Sep 23 10:54:00 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.04.1 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"


!!DMI Information
!!---------------

Manufacturer:      Gateway
Product Name:      DX4300


!!Kernel Information
!!------------------

Kernel release:    2.6.32-24-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.21
Library version:    1.0.22
Utilities version:  1.0.22


!!Loaded ALSA modules
!!-------------------

snd_hda_intel
snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe6f4000 irq 16
 1 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfe9bc000 irq 19


!!PCI Soundcards installed in the system
!!--------------------------------------

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
02:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 500
```0 Series]

---

### Post by lkjoel on 2010-09-24
Are you sure your sound card is working correctly?

---

### Post by lidex on 2010-09-25
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel probe_mask=1 
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

### Post by Sorinux on 2010-10-04
lidex, your advice worked for me... kind of!
The rear output will be muted when i use the front output, but when I want to adjust the volume from keyboard (Logitech Internet 350) also the rear output will be activated and the front. To mute again rear, I must unplug and then plug again the headset.
If I adjust the volume from the applet it will change the volume only for the headset, without activating also the rear.
Is this some conflict with my keyboard?
You have any suggestions about this?
My sound-card is VIA VT1708S on ASRock A770DE+.
Thank you for patience

---

### Post by NightwishFan on 2010-10-04
> VIA VT1708S
This card is evil! :D

I ended up having to remove pulseaudio to use it. It works fine with just Alsa on Maverick and Alsa Backports on Lucid.

---

### Post by Sorinux on 2010-10-04
Why evil?
Before I had Gigabyte MA78GM-S2HP with ALC889A. I got tiered after 4 or 5 times asking to fix the board and I went for the ASRock. 
The Realtek ALC889A had the same problem with the rear and front output working in the same time.
The thing is that my laptop, an old Aspire 4520 (don't remember the codec, but also Realtek), does not have this problem.
When I exchange the motherboard, I did not made a new install and the sound on VIA worked without problems.

---

### Post by NightwishFan on 2010-10-04
The card is very problematic with a different issue as it goes on. With old alsa it was not supported. At first once it was, sound was way too low. Then it was both too quiet and the volume would not work with pulse. Now, the card will not let me use external speakers. Etc.. Pulse seems to be a bit picky with this device. So I just remove it.

---

### Post by lidex on 2010-10-05
> **NightwishFan said:**
> The card is very problematic with a different issue as it goes on. With old alsa it was not supported. At first once it was, sound was way too low. Then it was both too quiet and the volume would not work with pulse. Now, the card will not let me use external speakers. Etc.. Pulse seems to be a bit picky with this device. So I just remove it.

NWF:
Your sound working now with alsa then? Did you try pulse audio manager for the volume issue?
We need to get ubuntu-pulse devs to fix this.

---

### Post by NightwishFan on 2010-10-05
I agree. The card works under alsa but has issues no matter what I do with pulse.

---

### Post by lidex on 2010-10-05
> **NightwishFan said:**
> I agree. The card works under alsa but has issues no matter what I do with pulse.

Sounds 'fishy' to me, but i see you hit 3500 ;-)

---

### Post by NightwishFan on 2010-10-05
Quite so my good fellow. I enjoyed the pun. :)

---

