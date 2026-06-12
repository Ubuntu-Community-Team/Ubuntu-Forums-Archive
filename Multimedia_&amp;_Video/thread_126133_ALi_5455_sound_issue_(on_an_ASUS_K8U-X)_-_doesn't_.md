---
title: "ALi 5455 sound issue (on an ASUS K8U-X) - doesn't work the way it should"
date: 2006-02-05
forum: Multimedia &amp; Video
---

### Post by _Luiz_ on 2006-02-05
My onboard sound doesn't work the way it was meant to.
 It is working this way right now:
 -Sound is possible only when speakers are plugged into the microphone jack input. (Yes, a bit strange)
 -On KMix, the devices are marked as "Unknown".
 -Just works after the loading of the module "ali5455", which isn't modprobe'd after the installation process. 
 -Only works with OSS. ALSA doesn't detect it.

The strange fact is that it worked great on Hoary, right out-of-the-box.

Any help is (greatly) appreciated. :-D

---

### Post by felmatos on 2006-02-25
Hi 
I have the same problem!
I'm using SLAMD64, and after 2 weeks i have made the sound work. But its in the microphone jack!! Its very problematic because i use windows too. and i have to change every time i boot windows.
Some one have the solution?

---

### Post by ekalin on 2006-03-12
I've found a solution to make that card work with ALSA. Pass the buggy_semaphore=1 option to the snd_intel8x0 module:

modproble snd_intel8x0 buggy_semaphore=1

or add that option to your modules configuration file. It worked for me.

---

### Post by marciovinicius on 2006-05-25
[quote=ekalin]I've found a solution to make that card work with ALSA. Pass the buggy_semaphore=1 option to the snd_intel8x0 module:

modproble snd_intel8x0 buggy_semaphore=1

or add that option to your modules configuration file. It worked for me.[/quote]

How may I do it? (Sorry I'm new in Linux and Ubuntu)

---

### Post by postadelmaga on 2006-08-10
I still have sound problem ... also after editing alsa-base ... (i all copy the stuff posted by rambo ...
All that is very strange : i have dapper 6.06 and at the first install all go well  but after installing new kernel then i had no sound so i tried re-install everything (all Dapper) but nothing: no way to get it work.

Please help me no more use winzoz and give sound to my xgl
Thanks ...

---

### Post by abreups on 2006-08-20
This is how I managed to use the buggy_semaphore option:
1- go to the /etc/modprobe.d directory (cd /etc/modprobe.d)
2- edit file alsa-base (sudo vi alsa-base)
3- find the line which says something like this:
options snd-intel8x0m index=-2
4- put buggy_semaphore=1 at the end of the line:
options snd-intel8x0m index=-2 buggy_semaphore=1
5- save the file (:wq)
6- reboot your system

It worked for me. Hope it works for you all.
Good luck.

Paulo Abreu

---

### Post by abreups on 2006-08-22
Bad news.
The buggy_semaphore option seamed to work, but turning on the machine next day showed me the problem of no sound persists...
Still looking for a solution.

Paulo Abreu

---

### Post by abreups on 2006-08-24
A new light at the end of the tunnel:

[http://www.ubuntuforums.org/showpost.php?p=884808&postcount=3](http://www.ubuntuforums.org/showpost.php?p=884808&postcount=3)

Worked first time. Who knows if it will continue to work after a few reboots.
Time will tell.
Thanks for Carlos Junior for the hint!

Paulo Abreu

---

### Post by etcetc on 2006-11-23
My sound card worked after I made the following edits to /etc/modprobe.d/alsa-base

#Comment out the following line
#options snd-intel8x0m index=-2
# Added the next line
options snd-intel8x0 buggy_semaphore=1

Then rebooted the system.

Note, I'm using snd-intel8x0 instead of snd-intel8x0m, removed index=-2, and added buggy_semaphore=1

This was with Dapper on a 32 bit system.

---

### Post by postadelmaga on 2007-01-15
Thks ,this is finaly a good solution but it generate another problem for me ](*,) :
... now the playback is ok, also sorround, but the capture is out of controll .
I can use microphone by setting mic2 but i can't avoid to mix the playback with it ( during conversation with voip programs it makes very hard comunicating) people speaking with me hear their voice.

Any Idea ??? (i hope you can understand the problem by my bad english, sorry...) :-#    

P.s. i'm on edgy.

---

