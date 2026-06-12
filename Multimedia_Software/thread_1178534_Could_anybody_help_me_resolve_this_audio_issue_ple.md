---
title: "Could anybody help me resolve this audio issue please?"
date: 2009-06-04
forum: Multimedia Software
---

### Post by gasto40 on 2009-06-04
Hi everybody....

I recently switched from Windows XP to Ubuntu's latest version. Everything went OK during installation and post update...but, there's one issue I still can't resolve, which is audio..

I have a Gigabyte P35C-DS3R motherboard, which uses the ALC889A HD audio codec. The thing is I do not hear sounds from my rear speakers, nor my subwoofer (the latter one not being that important anyway). I have not touched anything from the preferences menu yet. I've only tried to download realtek drivers for linux (2.4 version), but haven't suceed when compiling, because there's a message saying I don't have alsa-control, or something like that...

Could someone please enlighten me, or tell me what to do? It's only this, and I'll have a 100% working Ubuntu system on my PC :)

Thank you in advance

---

### Post by theozzlives on 2009-06-04
Maybe you should go to preferences and make sure the proper channels aren't muted, or turned down.

---

### Post by gasto40 on 2009-06-04
Yes. That was the first thing I did.... I checked every single channel with alsamixer....front, surround, pcm, master, surround, etc. They are all unmuted, 100% volume.

Then I executed "speaker-test -Dplug:surround40 -c5 -l1 -twav " in terminal, and got no sound in rear speakers...

---

### Post by jjross on 2009-06-04
Have you looked at the Pulse Audio settings?
Go to Applications/ Sound & Video/Pulse Audio Volume control
Open it and start something that will play the audio that you want.
It will show the active device working, right click on that device and see if there are other streams to choose from and try them.
Basically everything is routed thru pulse audio.
Hope this helps

---

### Post by gasto40 on 2009-06-04
Yes. Already tried that, but still no luck. Thanks anyway!

---

### Post by penguinehax on 2009-06-04
I assume that you are using ubuntu 9.04 then
I found a fix for it that is fairly simple(worked great for me)
follow this guide
[http://moderngeek.com/node/10](http://moderngeek.com/node/10)

---

### Post by g1pete on 2009-06-04
Look her, Pulse audio defaults to 2 channels
**HOWTO: Surround sound in pulseaudio**
[http://ubuntuforums.org/showthread.php?t=795525](http://ubuntuforums.org/showthread.php?t=795525)

maybe that will get you going.


Pete

---

### Post by gasto40 on 2009-06-04
Thank you Pete, but that didn't work. I will check the link [penguinehax]("http://ubuntuforums.org/member.php?u=849520") provided and see if it works

---

### Post by spy king on 2009-06-05
Hello, I have a similar problem, but my audio chip is the altek883..

---

### Post by gasto40 on 2009-06-05
Well, nothing seems to work :(
I still can't get sound from rear speakers...

---

### Post by spy king on 2009-06-05
Hmm thats sad.. I really like Ubuntu but for this one problem..
Have you tried installing the drivers from the realtek Website? I downloaded it, but don't know how to compile it.. :( 
used to double clicking and clicking next > next.. :p

---

### Post by penguinehax on 2009-06-05
I'm supprised Because I just used my solution on my machine, and again on my neighbors machine...they both had this issue.

---

