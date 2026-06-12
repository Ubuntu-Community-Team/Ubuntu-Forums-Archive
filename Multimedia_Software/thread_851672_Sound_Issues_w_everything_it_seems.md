---
title: "Sound Issues w/ everything it seems"
date: 2008-07-06
forum: Multimedia Software
---

### Post by v0idnull on 2008-07-06
I'm having issues trying to get sound working in Ubuntu. I've tried everything I can think of but to no avail.

Sound Card: M Audio Audiophile 2496 (ice1712 sound module)

When trying to test sound with Alsa I get:
v0idnull@statika:~$ gnome-sound-properties 
sound-properties-Message: Error running pipeline 'audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink': Could not open audio device for playback. [gstalsasink.c(697): gst_alsasink_open (): /bin0/alsasink0:
Playback open error on device 'default': No such file or directory]

Everything in the drop down menu in the sound properties window produces no sound and/or that error, EXCEPT when I select ICE1712 Multi. This creates the irritating sine wave. When options like OSS don't produce an error, they claim they are testing, but there is no sound.

Here is some output from a debugging script I took from Alsa's website:
[http://www.psikon.com/~v0idnull/alsa-info.txt](http://www.psikon.com/~v0idnull/alsa-info.txt)

This is a fresh install of Ubuntu with all the latest updates. On a previous install of Ubuntu 8, I followed all the steps in the Comprehensive sound guide on this forum, but to no avail either. The sound card works 100% under Windows so I'm certain this is not a hardware problem. This problem exists both on the SPDIF output of the card and the analog rca outs as well.

Any ideas folks?

edit: I rebooted to enable the Nvidia drivers for my video card, when prompted for the password, I heard the little drum rap sound. However, after logging in, the above issues still apply.

---

### Post by Sevy on 2008-07-22
I too am having the same problem with Alsa using the m-audio 2496 soundcard.
I would particually like to use alsa in the media players(xmms,audacious etc)but can only use oss.
My latest error in sound preferences is:
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Internal data flow error.
I can open volume control under the speaker icon which says M audio audiophile 2496 (Alsa mixer),so the card is being recognised.
Does anyone have there 2496 working??

---

### Post by oskar2000 on 2008-10-13
Bump once more.
This still hasn't been resolved in 8.04, and 8.10 is only a couple of weeks away.

I got a cheap behringer soundcard that works with pulseaudio but otherwise it totally sucks, so I'm not going to promote it here.

Here's the bug report
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442)

None of the workarounds have worked. For some time I got it working by telling it to just use "ALSA" but not anymore for some reason.

I guess that the root of the problem lies in the alsa driver for the chipset. It thinks it's a 10 channel soundcard, and the controlls are not named correctly. - gnome volume control never worked with this card. But I don't know enough about this to file a sensible bug report.

In addition to that the realtime kernel crashes randomly, so I can't do any audio processing anyway. I'm going to fall back once again to PCLOS.

---

