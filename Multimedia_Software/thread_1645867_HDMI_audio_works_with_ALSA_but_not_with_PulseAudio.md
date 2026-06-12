---
title: "HDMI audio works with ALSA but not with PulseAudio"
date: 2010-12-15
forum: Multimedia Software
---

### Post by go4linux on 2010-12-15
I spent a few days trying to make audio work on my TV connected via HDMI to a PC. The speaker test used by the sound preferences was dead, as was MPlayer. I managed to find a solution for MPlayer, giving the option "-ao alsa:device=hdmi", as specified in this article:

[http://footils.org/2010/06/8/hdmi-output-alsa-and-intel/](http://footils.org/2010/06/8/hdmi-output-alsa-and-intel/)

So, basically ALSA can see all my devices. This is the output of aplay -l:
> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
PulseAudio, on the other hand, can't. If I go on the sound preferences output I only see one, and that's not the HDMI one. In fact, audio works if I connect my earphones.

What I really don't understand is why it works on ALSA but not on PulseAudio. I always thought that PulseAudio was a superset of ALSA, and therefore it could do anything ALSA could do. Besides, now that I know that my Linux installation can correctly see my HDMI audio, how can I configure it to have it fully working?

---

### Post by scar1 on 2010-12-15
Hi,

I had similar issues and managed to resolve. To resolve check your pulseaudio log.

pulseaudio -vv

You may need edit your pusleaudio default.pa file.

/etc/pulse

now edit the default.pa file with text editor of your choice I use nano.
etc/pulse$ nano default.pa

In this file locate this line

load-module module-alsa-sink device=hw:**0,1**

now the 0, and 1 need to machine what you aplay -l has displayed for your HDMI card. It is the same as mine 0 & 3.

load-module module-alsa-sink device=hw:[B]0,3

[/B]Save the file and reboot. Now run pulseaudio -vv again check for errors. If says it is already running you should now be able to select your HDMI sound card in audio preferences.

I hope this help...
Cheers
Scar1

---

### Post by efflandt on 2010-12-15
Pulseaudio is a front end for alsa, but sometimes you have to give pulse a clue which one(s) actually work in alsa, or initially unmute devices with alsamixer before they work.

It sounds like scar1 is on track about how to let pulse know the alsa card, device.  I don't have any ATI or Intel HDMI video, but I have to do the same thing in /etc/pulse/default.pa for nvidia HDMI (except that the one that works with aplay -D is plughw:1,9 so I use "load-module module-alsa-sink device=hw:1,9" in /etc/pulse/default.pa

The speaker test in Sound Preferences may still not work, but I test it by playing internet radio in Rythmbox and test by switching Output in Sound Preferences (should switch on the fly).

---

### Post by go4linux on 2010-12-16
and indeed that helped, thank you very much. How this thing works is still a bit unclear, and I will have to look at it a bit more. I am actually starting to think that Ubuntu uses both ALSA and PulseAudio independently. Not sure this makes sense.
Anyway, I guess I have some more research to do to understand this. In the meanwhile I can watch some movies :)

Thanks again

---

