---
title: "Jackd with both outboard and onboard sound interface"
date: 2008-12-31
forum: Multimedia Software
---

### Post by ussndmac on 2008-12-31
When I start jack with my FP10, jack no longer shows the onboard inputs and outputs, only the 10 in & out channels of the FP10.

I'm not sure what to ask about here.

I think the onboard sound is being managed by alsa. When I start Audacious it's output is being sent to PCM device of the ALSA system. I can direct it's outs to Jack and Jack sees two inputs from Audaciuos.

How do I tell ALSA (?) to point the onboard I/O's to Jack. Or do I tell Jack to find the ALSA I/O's onboard? (if so how?)

Regards,
Mac

---

### Post by markbuntu on 2008-12-31
So, you want to use both devices in jack is that it?
I do not know that you can use multiple devices with jack by itself but you can connect more than one device to jack with pulseaudio. Audacious can then use your on-board and you can connect audacious to jack and still have the FP10 connected to jack.

Look in the **Ubuntu Studio and jack** section of the guide here.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

