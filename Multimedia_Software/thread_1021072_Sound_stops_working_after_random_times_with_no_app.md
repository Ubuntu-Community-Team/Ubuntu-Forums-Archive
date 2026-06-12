---
title: "Sound stops working after random times with no apparent cause"
date: 2008-12-24
forum: Multimedia Software
---

### Post by jharris0221 on 2008-12-24
To preface, I have spent over 10 hours working on my audio and have not been able to fix the problem. I've read and followed advice at:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
as well as several other posts, to no avail... I don't know where else to look.

My problem is not that sound isn't working, but rather that it stops working. The only way I can get it reworking is to restart. I think this may have something to do with suspend, but I am not sure. I seem to remember a time or two where it just stopped working... Programs I commonly use that use sound include songbird, pidgin, skype, firefox.

When it stops, it seems to be the pulseaudio module crashing because zero sound is played from any program. Also, both songbird and amarok lock up when I try to play sound. However, I am not sure how to check this so I cannot verify that this is the exact issue. Also- can anyone tell me how to kill/restart the module? I have tried several different ways (killall pulseaudio and pulseaudio -k to no avail)

I am running a custom built computer with an ASUS P5K-SE/EPU motherboard and onboard 5.1 sound and two harman/kardon speakers plugged in. See below for the output of lspci -v and some various other info:

```
$ lspci -v
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 829f
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ pulseaudio
W: ltdl-bind-now.c: Failed to find original dlopen loader.
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.

```

Any help would be more than appreciated. Let me know what additional information is needed and I will post as soon as I can (although with Christmas here, it may be hard for a few days...) I also added a screenshot of $ alsamixer because I have heard posts say that it should have several channels.

---

### Post by jharris0221 on 2008-12-30
Come on, *no one* can tell me at least where I can start looking?

---

### Post by Cracauer on 2008-12-31
It's probably in one of the threads you linked to, but anyway. Most of the time you fix this by unloading the driver kernel modules for your soundcard and reloading them. That does both, it resets the hardware and it gets a new software copy of the driver and usually works.

Which module in specific you have to re-load needs to be found out in try and error.

---

### Post by jharris0221 on 2009-01-01
Followed the instructions [in this post]("http://ubuntuforums.org/showthread.php?t=205449") to reinstall the driver fresh:
> A faster way, is to just remove the problematic packages and reinstall them cleanly.

(1) Remove these packages
Code:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils


(2) Reinstall those same packages
Code:

sudo apt-get install linux-sound-base alsa-base alsa-utils

[list][*]
VERY IMPORTANT NOTE: Ubuntu (GNOME) users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following
Code:

sudo apt-get install gdm ubuntu-desktop


(3) Reboot

Sound works great, I suspend, come back a day later, and no sound... :-/

---

### Post by jharris0221 on 2009-01-02
FIXED-

Turned out to be a suspend bug. See [here]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/222428") or [here]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/292129"). After looking around for some more information, I [found a post]("https://help.ubuntu.com/community/AspireOne") regarding specifying your hardware in /etc/modprobe.d/options [or]("http://ubuntuforums.org/archive/index.php/t-771207.html") /etc/modprobe.d/alsa-base. 

You can [look up your hardware here]("http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt#770"). Look under ```
aplay -l
``` to find the ALC###, mine was ALC883. Then look under the linked webpage above to find the correct ALC and hardware. Finally, I added > options snd-hda-intel model=6stack-digto /etc/modprobe.d/options (for ASUS P5K SE/EPU with built in 8 channel sound)
 
Hope this helps someone.

**EDIT:**

This doesn't completely work. If any sound streams are present when suspending (can check pulseaudio applet > volume control > playback to see if anything is playing), the pulseaudio server crashes. Note that songbird still keeps an audio stream registered even when paused. 

This shows up in /var/log/messages on resume when the above conditions are met:

 kernel: [  375.676041] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22

pulseaudio[5891]: module-alsa-sink.c: Got POLLERR from ALSA
last message repeated 3 times
kernel: [  382.356029] usb 1-6: reset high speed USB device using ehci_hcd and address 4
pulseaudio[5891]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
[B]
EDIT: [/B]Update on 1/04/09 completely fixed suspend problem.

---

### Post by sickenmcsluggets on 2009-01-18
My eyes are going buggy from researching this, sounds like my problem as well. Thanks for the links to the bug reports.

---

### Post by s57nev on 2009-03-11
Well if you are searching info on this motherboard... I think I had to solve my microphone problem with adding another line in: 

options snd-hda-intel model=6stack-dig

Anyone else with simmilar experience on this ?

---

### Post by Mike001977 on 2009-09-30
I got the same problem guys.

i run side by side xp and ubuntu i use only xp for gaming COD5 :)

But my sound lost on ubuntu 9.04 i have perfect sound in windows so i assume
that sound-card and speakers are ok.

I had perfect sound when i install ubuntu after few week i lost it,

now i did all and nothing.

 few info below to help you.

ASUS P5K-PE 

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 829f
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

so if you can advise before i format it again >.<

thanks 

Regards Mike

---

