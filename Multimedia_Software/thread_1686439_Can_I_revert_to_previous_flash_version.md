---
title: "Can I revert to previous flash version?"
date: 2011-02-12
forum: Multimedia Software
---

### Post by flammenwurfer on 2011-02-12
I have ubuntu 10.10 installed and running boxee.  When flash updated to 10.2 the other day flash videos stopped working correctly.  Is there somewhere I can get the previous version of flashplugin-installer and replace the 10.2 version?

---

### Post by Swagman on 2011-02-12
assuming your using a nVidia card

Copying from the post [**HERE**](http://ubuntuforums.org/showpost.php?p=10450353&postcount=123) .... Do the following

press left alt F2

enter gksu nautilus and navigate to filesystem /etc

make a new folder (dir) called adobe and then right click in that folder and create document (empty)

then click on that document and copy & paste this in...

```
EnableLinuxHWVideoDecode=1
```

save and then reboot.

Voila

---

### Post by flammenwurfer on 2011-02-12
That doesn't solve my problem.  I want to revert to the previous version of flash, not enable hardware decoding.

---

### Post by Swagman on 2011-02-12
My apologies.

I actually asked the same question in a thread I created [**HERE**](http://ubuntuforums.org/showthread.php?t=1685844)

But no-one answered that bit !!

I played around in flashes settings though and discovered if I allowed it 10mb instead of 150k then it played ok again. <-- I dunno if that will help you ?

I agree the update was terrible. Flash was regularly crashing and doing a chromakeying effect when it did play.

I know this post doesn't answer your OP but it does keep it bumped to the top !!

---

### Post by james_xxx on 2011-02-12
Same problem here.

Flash 10.2 is crashing all the time. Browser has to be restarted to get things going again.

I tried reducing from 100k to 10k. It might be helping, but does not fix the problem.

I also want 10.1 back as quickly as possible.

---

### Post by flammenwurfer on 2011-02-13
I was able to downgrade back to flash 10.1.  Download the archived version of flash from [this]("http://kb2.adobe.com/cps/142/tn_14266.html") link .  Replace "libflashplayer.so" in /usr/lib/flashplugin-installer with the one for 10.1 that you downloaded from that link.

Swagman:  Are you saying that you were able to get 10.2 working by changing the cache size in the flash settings?

---

### Post by gino.c on 2011-02-13
you can revert to a previeous flash version with synaptic!

1) open synaptic package manager.
2) search for flashplugin-installer and select it
4) goto menu Package -> force version
5) select the previous version and apply
6) done!!:P

make sure you right click flashplugin after and unmark it (synaptic reinstalls the latest again otherwise)!

---

### Post by Swagman on 2011-02-13
> **flammenwurfer said:**
> I was able to downgrade back to flash 10.1.  Download the archived version of flash from [this]("http://kb2.adobe.com/cps/142/tn_14266.html") link .  Replace "libflashplayer.so" in /usr/lib/flashplugin-installer with the one for 10.1 that you downloaded from that link.

Swagman:  Are you saying that you were able to get 10.2 working by changing the cache size in the flash settings?

I *had* thought so but it appears that different youtube clips affect in different ways.

eg: Even though I now have hardware acceleration enabled, on some clips I still get that weird chromakey effect. I took a screeny but when viewed Black = colour zero (sees everything behind it).

I'll do a test upload of that grab.

[img]http://localhostr.com/file/E8RH59V/Ubuntu158.jpeg[/img]

No.. that's appearing ok now but the black edges each side were colour zero and had lots of "sparklies/blocks" in them.

---

### Post by flammenwurfer on 2011-02-13
Interesting.  Hopefully there will be an update soon instead of having to mess with all this to get it working.  I'm just staying with 10.1 for now until I hear that 10.2 is working correctly.

---

### Post by gcranston on 2011-02-18
> **flammenwurfer said:**
> I was able to downgrade back to flash 10.1.  Download the archived version of flash from [this]("http://kb2.adobe.com/cps/142/tn_14266.html") link .  Replace "libflashplayer.so" in /usr/lib/flashplugin-installer with the one for 10.1 that you downloaded from that link.

Reverted to 10.1.102.64. Works like a charm. Now I can capture all my flash "movies" again.

Thanks.

---

