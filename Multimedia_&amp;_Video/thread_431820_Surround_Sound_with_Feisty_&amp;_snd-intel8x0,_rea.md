---
title: "Surround Sound with Feisty &amp; snd-intel8x0, realtek ac97,"
date: 2007-05-03
forum: Multimedia &amp; Video
---

### Post by wgaprotest on 2007-05-03
This is a very stubborn problem, and I think I've read just about everything, as well as enjoyed some excellent attempts at supporting me from the #alsa irc channel, but I still **can't get any sound from my rear speakers**. They do work in winblows, so it's not the hardware or connections.

I can get good sound from speakers FL, FR, Centre, and LFE, and the trick for this onboard realtek chip on this Asus A8N32-SLI Deluxe mobo (nvidia nForce4 chipset) is to select the "independent' option in the surround jack switch -- not the 'shared'. This change got me sound from Centre and LFE, whereas the 'shared' option only allows for FL and FR speaker output.

Has anyone tried the NFORCE-Linux-x86-1.21 package from nvidia's site? The one post that really made sense said you had to use nvmixer from them, instead of alsamixer, and it does make logical sense because of how proprietary nvidia is. I would have tried it last night, except the post was rather old (breezy user) and looking inside the zip package with ark didn't show any files that could be remotely appropriate for sound...just rpm's for the network and other settings - not sound. And nvidia only seems to give info/support for its linux drivers related to graphics cards...their nvnews forum is almost useless because it states that the package named above has been deprecated and you can't even register to post (no matter what you type in, you get the message that your email address has been banned by the site administrator, even if you've never registered with them before). Realtek's site gives gibberish/unreadable results.

Please help if you can, as I've already tried sooo many .asoundrc files, lots of ac97_quirk options...nothing helps with rear speakers -- or side speakers for that matter. Yes, I actually have 7.1 capability, but I'd be happy with 5.1 at this rate. And yes, at every change I try, I do the "speaker-test -c6 -Dplug:surround51 -twav" test, and variations thereof. Even wishie has been trying to help...

Using alsa 1.0.13, kernel 2.6.20-15 generic. (latest alsa.org driver is 1.0.14, but almost all recommend lower, more stable versions than the one I have).

Thanks in advance,
wgaprotest aka dennister

---

