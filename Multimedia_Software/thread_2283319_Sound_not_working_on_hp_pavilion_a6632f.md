---
title: "Sound not working on hp pavilion a6632f"
date: 2015-06-21
forum: Multimedia Software
---

### Post by jesse_h._goode_jr. on 2015-06-21
hello... i'm new to Ubuntu. just installed 15.04 on my HP Pavilion a6632f. wireless is good, but having trouble getting my sound to work. following some troubleshooting tips i've found, i've done the following. (see below)

* ubuntu see's the soundcard
* sound modules appear to be installed.
* installed dpkg, and got the latest alsa package / driver
* made sure bios enabled for audio

I do see an access denied below.  

Does anyone have some thoughts on helping rectify this? Thanks :)

jesse h. goode jr.
[email]jessehgoodejr@gmail.com[/email]

jesse@linny:~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

jesse@linny:~$ lspci -v | grep -A7 -i "audio"
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
        Subsystem: Hewlett-Packard Company Asus IPIBL-LB Motherboard
        Flags: bus master, fast devsel, latency 0, IRQ 30
        Memory at fe9f4000 (64-bit, non-prefetchable) [size=16K]
        **Capabilities: <access denied>**
        Kernel driver in use: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])

this listed a ton of sound modules installed...
find /lib/modules/`uname -r` | grep snd

This didn't work. either as my user, or as root...
sudo aplay /usr/share/sounds/alsa/Front_Center.wav

installed dpkg
got the latest (06/20/2015) alsa drivers package and installed it. reboot. tested and no sound.
got into bios. verified that onboard audio is "enabled"

---

### Post by Bucky Ball on 2015-06-21
Welcome. You *could* be making things more complicated that they need to be. Please use code tags for terminal output, BTW. See the last link in my signature. Thanks. ;)

Firstly, have you got Pulse Audio Volume Control installed? If not, install it and launch it. Open the 'Playback' tab. Open a music player and get an audio stream going (play a tune). Does the stream show in the 'Playback' tab? If so, there is nothing wrong with sound, just the set up. 

Go to the Output tab and see which device you are outputting to in the drop-down list at the right above the sliders. Check Playback and see where you are routing the stream. Is it to headphones or HDMI? Analogue or digital? Where are you wanting it to come from?

Bottom line, experiment with PAVContol. Tweak about and see what you come up with. Unless you are using an exotic outboard audio device you haven't mentioned, sound will generally work 'out of the box'. Unlike Windows, there are a ton of drivers in the Ubuntu kernel already (which is why wireless works OOTB) so you generally don't need to go looking around for sound drivers. What am I saying. More like never, unless, as I say, you have an exotic, unsupported outboard device. 

Good luck and let us know how you go. :)

PS: This is not to say that something you've tweaked or installed hasn't now become your problem. Cross that bridge when you get back with how you went with PAVControl. Just get an audio stream going and look for it in the 'Playback' tab of PAVC.

---

