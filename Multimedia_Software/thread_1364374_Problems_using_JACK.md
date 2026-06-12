---
title: "Problems using JACK"
date: 2009-12-25
forum: Multimedia Software
---

### Post by The Funkbomb on 2009-12-25
Let me tell you all the information I have...

I have a fresh install of Ubuntu 9.10 x64.  My sound is ALC888.  I have been using the standard notification applet for playback and settings.  I don't know if I'm using ALSA or PulseAudio or what.  Unfortunately, this did not play well with gtk-recordmydesktop.

I installed qjackctl and that shows up on my screen.  I go into setup and it's very confusing.  I have no idea how to set this up.

I tried to follow some other sites with no love.  I get errors like:

```
Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```

Could anyone help me out?

---

### Post by RaumTrug on 2009-12-25
don't forget to browse the official ubuntu help stuff on help.ubuntu.com, expecially the community contributed stuff...

read here: [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation) , under "real time support", doesn't need the ...-rt kernel, btw, works fine with genereic...

for setting up jackd via qjackctl look here: [https://help.ubuntu.com/community/HowToJACKConfiguration ]("https://help.ubuntu.com/community/HowToJACKConfiguration")

still questions then...? just ask!

btw...pulse runs ontop of alsa, and jack itself kills/suspends pulse to get alsa all by itself...that's the way it works...

---

### Post by The Funkbomb on 2009-12-25
Thanks for the reply.  I have read those pages but no luck.  I don't know how else to do it.

I was able to sort of getting it working via CLI with:

```
jackd -d alsa
```

It now shows jacks in gtk-recordmydesktop but none of them work as far as I can tell.

---

### Post by RaumTrug on 2009-12-25
qjackctl has a button for messages below the start button...fire it up, and post what it sais there (the whole text, not just the single line!!)

as for setting up, you'd normally not want to change other stuff that "Frames/period" "sampling rate" and "periods", and maybe "interface" to select the sound card.

ah, and the "realtime" checkbox should be set for jack to be of any use...but on standard ubuntu it will only work, if you modified your limits.conf, like in the link I posted above, and have logged out and in again (or just rebooted your pc).

---

