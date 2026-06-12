---
title: "Udev update and Alsa Problem in Maverick?"
date: 2010-12-24
forum: Multimedia Software
---

### Post by cknoettg on 2010-12-24
Ever since I installed the update for udev on 12-22-2010, my user.log has been littered with the following several times:

pulseaudio[1584]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
pulseaudio[1584]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_intel8x0'. Please report this issue to the ALSA developers.
pulseaudio[1584]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
pulseaudio[1584]: ratelimit.c: 13 events suppressed

This is a strange "bug" report, since my primary "symptom" is that my right speaker is now working, whereas it always failed the sound test before. Therefore, it is a low-priority "problem."

My hardware is: Intel 82801EB/FR (ICH5/R) AC'97 Audio Controller (rev02)

I started to follow the "Comprehensive Sound Card..." sticky and my aplay -l results were:
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Since aplay had a return, and lspci returned:
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

...I figured that it wasn't a "driver" issue per se, in the sense that it was detecting my device. I did notice, however, that running the modprobe cmd in the Gnome terminal for snd- led to an error in which - was converted to _ : FATAL: Module snd_ not found. Which leads me to another Q that I will try to find in another thread.

So finally to my question: since the only update I performed just prior to the error log filling with Alsa errors was the udev update, is it possible that the udev update led to my problem?  Or is it just coincidence?

I hope I am not overloading one thread, but a question that fits into the same category: Should I follow the "Comprehensive sound..." sticky instructions to reload the Alsa drivers, or the driver-specific Alsa instructions at: [http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0](http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0) ? It would seem like a no-brainer, except that the Comprehensive Sound instructions seem more up-to-date. Does this seem like reasonable troubleshooting? Is it even worth it, since my main symptom is just a busy error log? Do you need anymore relevant info to help diagnose this issue?

(also, I reported the bug to ALSA - others have it, but they are also having sound problems - not me).

---

