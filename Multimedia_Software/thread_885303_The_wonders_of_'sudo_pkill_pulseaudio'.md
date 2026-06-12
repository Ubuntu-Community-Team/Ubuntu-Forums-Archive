---
title: "The wonders of 'sudo pkill pulseaudio'"
date: 2008-08-10
forum: Multimedia Software
---

### Post by T_W on 2008-08-10
So I was sitting at my Ubuntu desktop yesterday and suddenly rhythmbox, flash, pitivi, and skype were all coexisting.  Gstreamer audio and youtube content mixed together... seamlessly... without any hangs... it was a miracle!  Attributing this to a recent update, I was like "Hallelujah.... they finally fixed Pulse Audio".

Then I noticed that somehow my pulseaudio process had crashed.  The fix was not provided by a system update, the fix was to remove Pulse Audio from the picture.  Since then, 'sudo pkill pulseaudio' has become a staple of stable multimedia usage.

I've been hanging on, hoping for a fix (even trying the lock-up prone flash 10 beta), but now I have to ask, is there any reason to keep Pulse Audio installed?  In its current form it only serves to propel Linux multimedia back into the stone age before software mixing.

So should I pull the trigger and 'apt-get remove' it?  Has anyone got anything resembling acceptable multimedia performance out of it?

---

### Post by eye208 on 2008-08-10
> **T_W said:**
> I have to ask, is there any reason to keep Pulse Audio installed?
It depends on who you ask. I would say no.

---

### Post by markbuntu on 2008-08-10
I would say yes. You can go here to get it all working:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by rainwalker on 2008-08-10
+1 "yes" vote from me.

---

### Post by Yellow Pasque on 2008-08-10
PulseAudio was a novel hack for ALSA's inept coding. You have to give them credit for trying against the high latencies.
Of course, you could just completely remove both of them and use OSS4/vmix, and I really hope the Linux kernel devs will one day use OSS and let ALSA die a slow, painful death.

---

### Post by markbuntu on 2008-08-11
What we need is drivers, low level bare bones fast as hell drivers for the hardware that applications can adress with a minimum of interference from the sound server. 

We need a sound server that will let an application use all available sound hardware simultaneously and invisibly.

Will OSS4 hook jack up to all the dacs and inputs outputs on my multiple sound cards?

---

### Post by T_W on 2008-08-17
So quick update:

I swapped my system entirely over to ALSA (see attachment), and the system is behaving much better.  

Flash, Skype, and GStreamer all cooperate again.

Some of the threads tell you to remove pulseaudio entirely using apt-get or synaptic, but for me at least this was not necessary.

---

### Post by tuxxy on 2008-08-18
I have always used ALSA, did you have a reason to use pulseaudio in the sound config

---

### Post by markbuntu on 2008-08-18
Well I did, I have 2 sound cards and was looking to use them simultaneously. Pulseaudio does that for me. I can have any application that goes through pulse play through either one or both. Also, I can use jack through one card and listen to youtubes through the other without having to change my jack setup.

---

### Post by T_W on 2008-08-18
> **tuxxy said:**
> I have always used ALSA, did you have a reason to use pulseaudio in the sound config

I believe the upgrade process switched everything over to pulseaudio automagically.

---

### Post by markbuntu on 2008-08-18
Yes, upgrading to hardy automagically put pulse in control of your sound system in an incredibly inept fashion. Important packages and much information critical to successful migration were just left out. Default sound driver settings and a large accumulation of audio driver fixes were not migrated. Many serious bugs in PulseAudio were ignored and the release went forward.

It is really a shame and I do not expect that Intrepid will fix it.

---

### Post by eye208 on 2008-08-19
> **Temüjin said:**
> PulseAudio was a novel hack for ALSA's inept coding. You have to give them credit for trying against the high latencies.
Of course, you could just completely remove both of them and use OSS4/vmix, and I really hope the Linux kernel devs will one day use OSS and let ALSA die a slow, painful death.
Don't blame ALSA for PulseAudio's latency issues. ALSA/JACK introduced low-latency audio to Linux in the first place. If you think OSS4 or even PulseAudio on top of it will ever give you 1.3ms latency the way ALSA/JACK did since 2003, you must be smoking too much weed. Get real.

PulseAudio's prime achievement so far is the deterioration of Ubuntu. I cannot seriously advocate this system in its current state as a substitute for Windows. And that's a shame because Ubuntu 7.10 came really close to being ready for the average user's desktop.

The fact that people can get rid of the PulseAudio mess with just a few clicks doesn't help here. If things don't work by default, they're not ready.

---

### Post by markbuntu on 2008-08-19
Actually, Pulseaudio iteself has very low latency. The latency problem comes from the applications like players that have huge buffers and so, high latency. There are some instances, like resampling, where there is some added latency, but any resampler will do that. If you insist on playing back 44.1k audio tracks at 48k, you will get a little to a lot of resampling latency no matter what you use for a sound server or application, and worse audio quality instead of better.

You can go to pulseaudio.org and read what lennart has to say about latency in pulseaudio if you are really interested in this issue.

---

### Post by Yellow Pasque on 2008-08-19
> **eye208 said:**
> Don't blame ALSA for PulseAudio's latency issues. I'm not. I'm giving PulseAudio a backhanded compliment for fixing ALSA's inept mixing, but introducing a lot of latency.

> If you think OSS4 or even PulseAudio on top of it...
Huh? OSS4 on top of ALSA? Apparently, you don't know what OSS4 is.

---

### Post by eye208 on 2008-08-20
> **Temüjin said:**
> Huh? OSS4 on top of ALSA?
No, PulseAudio on top of OSS4.

You seem to think that replacing ALSA with OSS4 will make PulseAudio go away. Keep in mind these guys are advertising their sound server for Linux, Solaris, FreeBSD, Windows 2000 and Windows XP. That means they want to see it running on top of everything: ALSA, OSS, DirectSound, ASIO, whatever.

---

