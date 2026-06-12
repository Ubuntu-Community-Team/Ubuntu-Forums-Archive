---
title: "How to enable surround sound?"
date: 2008-10-27
forum: Multimedia Software
---

### Post by GmAz on 2008-10-27
I have the Logitech 5300 speakers, 5.1, and a Creative Audigy 2 ZS sound card.  Where is a sound control panel that I can enable surround 5.1 in Ubuntu?  I can't find it anywhere.  Is it an addon from the repos?  I know my speakers work, as does my sound card.  But I am only getting stereo sound.

---

### Post by grantbuntu on 2008-10-28
I explain how I solved the same problem for a Creative Audigy Value card (Intrepid) in: [http://p-s.co.nz/wordpress/?p=105]("http://p-s.co.nz/wordpress/?p=105")
> 
Initially had a problem getting the surround sound working with the Creative Audigy Value card. Lots of advice involved .asoundrc, ALSA, OSS etc. All were wrong ;-). The correct answer was at [http://ubuntuforums.org/showthread.php?t=795525](http://ubuntuforums.org/showthread.php?t=795525).

sudo gedit /etc/pulse/daemon.conf
then uncomment the line:
; default-sample-channels = 2
and set it to 6 (for 5.1)
i.e.
default-sample-channels = 6
Now reboot
sudo reboot

Then System > Preferences > Sound and set all the values to PulseAudio Sound Server.

Finally, double click on the speaker icon to get the volume control. For CA0106 (Alsa mixer) I set Preferences to show Analog Center/LFE, Analog Front, and Analog Rear. For Playback: ALSA PCM on surround51:0 (CA0106) (PulseAudio Mixer) it was Master that was needed. The only thing I had to adjust was to make Analog Center/LFE slightly less powerful than Front and Rear to prevent boominess from the front centre.

Does this help?

----

For reference, my settings are:

aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


lspci -v

01:01.0 Multimedia audio controller: Creative Labs SB Audigy LS
	Subsystem: Creative Labs Device 100a
	Flags: bus master, medium devsel, latency 64, IRQ 21
	I/O ports at b800 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: CA0106
	Kernel modules: snd-ca0106

---

### Post by markbuntu on 2008-10-28
[http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/](http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/)

---

### Post by GmAz on 2008-10-29
I will be testing this as soon as I get home.  I am connected remotely right now, but obviously can't hear it.  Many thanks!

---

### Post by somudrog on 2008-11-03
I followed these instructions and surround seems to work, but my master volume control no longer does (the one I control with my keyboard).  Any idea how to fix?  Also, when I do the speaker test sound comes from all speakers but not the subwoofer.

Thanks!

---

### Post by markbuntu on 2008-11-04
Here are a few more links about surround sound that may be of help:

[http://ubuntuforums.org/showthread.php?t=795525](http://ubuntuforums.org/showthread.php?t=795525)

[http://ubuntuforums.org/showthread.php?t=899139](http://ubuntuforums.org/showthread.php?t=899139)

---

