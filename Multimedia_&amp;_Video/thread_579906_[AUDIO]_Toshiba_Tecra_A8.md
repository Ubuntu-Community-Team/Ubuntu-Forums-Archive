---
title: "[AUDIO] Toshiba Tecra A8"
date: 2007-10-18
forum: Multimedia &amp; Video
---

### Post by Korsakoff on 2007-10-18
Ok ok... it's the well-known problem for the Toshiba's notebooks. I'm tired of that. Why ubuntu audio team didn't solve it with gutsy? I've just installed and the audio come out only from frontal jack and I have to amplify to hear something....

I tried [**this**]("http://ubuntuforums.org/showthread.php?t=539595&highlight=toshiba+sound") (both 1.0.14 - 1.0.15 alsa) [**and this**]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#High%20Definition%20Audio%20Codecs") but without success.

I tried to add in alsa-base:

options snd-card-0 enable=1 index=0 model=basic
options snd-hda-intel enable=1 index=0 model=basic 

and other stuff like that.

Now I want to know from Tecra A8 owners, did you manage to solve it? And if yes, can u explain in details howto?

And last question: what is doing ubuntu audio team about that? Every ubuntu version my audio works for few days and after it stops. I always keep my version up to date.

Thanks @ all,
a stressed user.

---

### Post by floke on 2007-10-29
Nope.

I have to use external speakers plugged in to the headphone socket to get sound.
I filed a bug on this ages ago - they reckoned it was a jack sense bug. Then they claimed it was fixed. It wasn't. I posted a new bug report. They retracted the fixed claim. But nothing since.

I won't hold my breath.

But its not just Ubuntu - this is the same on every distro I've tried. Only BSD pulls it off.

---

### Post by JediEagle on 2007-11-03
I have the same problem. Could you please tell me how did you manage to get the sound working with the headphones? I plug in the headphones, but there is still no sound. Thank you in advance.

Yeah, I'm new at this :)

---

### Post by floke on 2007-11-04
> **JediEagle said:**
> I have the same problem. Could you please tell me how did you manage to get the sound working with the headphones? I plug in the headphones, but there is still no sound. Thank you in advance.

Yeah, I'm new at this :)

In the dreaded terminal, type

alsamixer

this will pull up all your settings - make sure the headphones are not muted and that the headphone sound channel is turned up.

---

### Post by fmorales on 2007-12-23
I resolved this issue by adding the following line to /etc/modprobe.d/alsa-base

options snd-hda-intel enable=1 index=0 model=basic

---

### Post by raideen on 2008-02-29
I've posted the solution that I figured out over in this thread: [http://ubuntuforums.org/showthread.php?p=4423596]("http://ubuntuforums.org/showthread.php?p=4423596"). Hopefully, it works for someone besides me. :)

My solution will probably work for those who have sound either through the speakers or the headphones but is not working from both (or works from both but the jack sense doesn't work). It's a pretty general solution (i.e. requires you to do some work) that should work for multiple configurations. For those with no sound, upgrading the ALSA drivers will probably be the best bet although I don't think that it will hurt to try my instructions first.

---

