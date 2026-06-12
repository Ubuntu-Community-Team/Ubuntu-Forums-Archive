---
title: "No audio whatsoever"
date: 2008-10-30
forum: Multimedia Software
---

### Post by skotoseme on 2008-10-30
I've been running a copy of ubuntu live on an old PC for a while. Everything works great; internet access, flash video, all apps run fine, but I've not heard a peep of audio from anything but the internal PC speaker since I installed it.

Here's what I've already concluded. (Please forgive the detail, but I figure it will save everyone's time if I list what I've already checked!):

* I'm using the correct jack; my speakers are still plugged in from when the machine was running Windows. (I did try the others just for fun.)
* The soundcard is not fried; I tried it on my new machine and it functions fine.

More conclusions, with the help of the troubleshooter that is "stickied" in this section:

* Nothing is muted, nothing is turned all the way down (I checked all levels through both the Volume Control frond-end *and* alsamixer through the shell; additionally, Volume Monitor responds visually when I play audio files, so there are definitely audio signals "trying" to get out)
* I cycled through four listed sound devices.
* Ubuntu appears to recognize my sound card; When I type aplay -l, as recommended in the troubleshooter, I get, among other things:

card 0: Audigy [Audigy 1 [Unknown]], device 3: emu10k1 [Multichannel Playback]

When I type lspci -v I see:

0000:00:08.0 Multimedia audio controller: Creative Labs SB Audigy (rev 05)
        Subsystem: Creative Labs: Unknown device 2005
        Flags: bus master, medium devsel, latency 32, IRQ 16
        I/O ports at dc00 [size=64]
        Capabilities: <available only to root>

This was encouraging. I looked up the corresponding "chipset." Now listed at [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs) are chipsets for various Sound Blaster cards with the name "Audigy" in them. Problem is, I have no idea how to install them.
emu10k1 is the device already associated with Audigy and I "activated" it.  (sudo modprobe snd-emu10k1) This was successful in the sense that there was no error message (as with sudo modprobe snd-randomgarble), but there's no audio either. All the other chipsets I tried "activating" returned error messages.
I may have hit my Linux wall of comprehension here. I really want to continue using Ubuntu but it's strange how lifeless a computer can be without a little musical accompaniment so I absolutely must solve this...with your help! Many thanks in advance :)

Chase

---

### Post by skotoseme on 2008-10-31
I hope my excruciating detail didn't turn anyone off :) The gyst of it is the audio doesn't work and I think I need help with installing a different driver/chipset!

---

