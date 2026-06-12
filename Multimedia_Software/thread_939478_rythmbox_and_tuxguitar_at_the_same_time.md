---
title: "rythmbox and tuxguitar at the same time"
date: 2008-10-06
forum: Multimedia Software
---

### Post by hecato on 2008-10-06
So I now can listen to flash inside firefox and dont need to close rythmbox before do it.


But now, Im also using tuxguitar, and it seem that they exclude each other (ryhtmbox and tusguitar), I will be happy if you know how I can use both of them at the same time (ie, no need to close the other while using one of them).

---

### Post by minky311 on 2008-10-06
Well it is working fine for me.
Are you using pulseaudio or alsa?
I'm using pulseaudio and everything works seamlessly.
I used this guide to set it up and you should give it a try too.
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)
Start Where it says packages and install them all.
Then follow the rest of the guide.

---

### Post by hecato on 2008-10-07
Is there a command that I can use from cmd line for see which one Im using?

(I think I have almost all packages listed there, thought I will see).




------------

By the way, the error I get when I hit tab is databank not available.

---

### Post by minky311 on 2008-10-07
Is this the error you get? [http://www.tuxguitar.com.ar/tgwiki/doku.php?id=doc:error_soundbank](http://www.tuxguitar.com.ar/tgwiki/doku.php?id=doc:error_soundbank)
Forget what I said about it working using pulseaudio. I thought it did but now it doesn't. It does work with both programs open if I am using ALSA.
You can check in system->preferences->sound to see if you are using ALSA.

---

### Post by kurotenshi on 2008-10-08
I have a similar problem.

start Tuxguitar, play a bit then start rythmbox and it says that the resource needed to play is occupied. Shutdown TG and then RB plays ok but if i start TG again it says "MIDI system unavailable"

---

