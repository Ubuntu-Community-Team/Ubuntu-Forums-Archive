---
title: "Soundblaster 5.1 vx, microphone does not work"
date: 2014-05-24
forum: Multimedia Software
---

### Post by Bill Cosby on 2014-05-24
Hello there,

I have a Soundblaster 5.1 vx, it works perfectly under Winows 7 (dual boot setup), on Linux I can hear sound, but I can't get the microphone to work.
Alsamixer shows me no volume levels in the capture section (see figure below)
[IMG]http://media.cdn.ubuntu-de.org/forum/attachments/37/17/6602672-alsam.png[/IMG]

As you can see, it's using the ca0106 chip/kernel driver, any ideas of what is wrong?

Pulseaudio gives me volume levels, but it doesn't show any level response when I speak into the mic.

[BTW] I am using Xubuntu 14.04

Any ideas? 

Regards, 
Bill

---

### Post by dannyboy79 on 2014-05-24
does pressing "m" when on the analog source do anything? can you press the up arrow and have the Mic meter bars go up?

---

### Post by Bill Cosby on 2014-05-25
> **dannyboy79 said:**
> does pressing "m" when on the analog source do anything?
Sadly, no.

> **dannyboy79 said:**
> can you press the up arrow and have the Mic meter bars go up?
No again, if I press up (or down) I can only change the source (Phone/Mic/Aux/Line-In), and sadly, neither works.

I suspect it could be an option I am missing for the module loading, but I couldn't find anything on the internet, does no one have the same soundcard under Linux here?

---

### Post by Yellow Pasque on 2014-05-25
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Bill Cosby on 2014-05-25
[http://www.alsa-project.org/db/?f=19c6e67b0592ad647d3c25df7299f03215f75344](http://www.alsa-project.org/db/?f=19c6e67b0592ad647d3c25df7299f03215f75344)

---

### Post by Yellow Pasque on 2014-05-25
The code says capture was not tested:
> /* Sound Blaster 5.1vx
+	 * Tested: Playback on front, rear, center/lfe speakers
+	 *** Not-Tested: Capture**
-- [https://github.com/torvalds/linux/commit/23156e8faed5df60364976bffea0711a4f38d88a](https://github.com/torvalds/linux/commit/23156e8faed5df60364976bffea0711a4f38d88a)

I would suggest filing a bug on kernel bugzilla (reference the commit and your alsa info link).

---

### Post by Bill Cosby on 2014-05-26
So capture is simply not supported by the current Alsa driver, am I getting this right?

Thank you very much, so far!

---

### Post by Yellow Pasque on 2014-05-26
Correct. Interestingly, the original patch had the line "i2c_adc=1;", and the author said it worked, but apparently didn't propose the patch for inclusion. A couple years later, a different author made the current patch, but with "i2c_adc=0;"
> With i2c_adc=1, the driver adds some capture volume controls, phone,
mic, line-in and aux.  Check whether these controls really work.
-- [http://www.alsa-project.org/pipermail/alsa-devel/2008-October/011312.html](http://www.alsa-project.org/pipermail/alsa-devel/2008-October/011312.html)

---

