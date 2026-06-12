---
title: "Sporadical sound from HTPC-pulseaudio server"
date: 2010-10-28
forum: Multimedia Software
---

### Post by PureW on 2010-10-28
Hello

My HTPC with Ubuntu Server 10.04 has caused me so much trouble now. I actually got the sound working yesterday and I could even stream music over the network from my laptop to the pulseaudio-server in the htpc.

Then the strange things happened. Suddenly sounds played from the htpc (XBMC and aplay through ssh) were heard from my laptop(!!!!) and not from the htpc.

After that I disabled the network in the laptop's default.pa because I certainly didn't want the sound from the htpc streamed to the laptop! After this, I can't get any sound from the htpc anymore. 

It is very strange because I can see in pavucontrol (over ssh with X-forwarding) that the sound-meter is moving when playing a file with aplay over ssh:
[IMG]http://i54.tinypic.com/27z99o7.png[/IMG]

So why is no sound heard?

Output of "pulseaudio -v" when playing a wav-file. [http://pastebin.com/m4RD360x](http://pastebin.com/m4RD360x)

---

### Post by PureW on 2010-10-28
I've checked that the sound isn't muted in alsamixer, but since it really seems muted, are there any more places I can unmute the sound?

---

### Post by PureW on 2010-10-29
Can no one tell me what to do?

---

