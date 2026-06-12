---
title: "Skype crash if ATI/AMD active - no sound on tv via HDMI if ATI/AMD inactive"
date: 2012-11-06
forum: Multimedia Software
---

### Post by gruiiik on 2012-11-06
Hello!

Sorry for my english that hurts eyes. ;) And I must precise that I'm not a geek.

I searched in the archives of the forum, but it seems that my problem (or a similar) has not yet been processed.

I'm on Ubuntu 12.04 (desktop). Previously I was on Ubuntu 10.04. This problem occurred before, on 10.04, in fact since the skype's update (-> version 4), but "randomnly". 
More precisely the characteristics of my computer are (version):

```
-Version-
Kernel		: Linux 3.2.0-32-generic-pae (i686)
Compiled		: #51-Ubuntu SMP Wed Sep 26 21:54:23 UTC 2012
C Library		: Unknown
Default C Compiler		: GNU C Compiler version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) 
Distribution		: Ubuntu 12.04.1 LTS
Processor	2x Intel(R) Core(TM)2 Duo CPU E7200 @ 2.53GHz
```

and (for media):

```
Multimedia
Audio Adapter	HDA-Intel - HDA Intel
Audio Adapter	USB-Audio - USB Device 0x46d
Audio Adapter	HDA-Intel - HDA ATI HDMI
```

I installed Skype 4.0.0.8 (32 bits) that works perfectly until I don't activate the drivers:

[IMG]http://img401.imageshack.us/img401/2664/driveratiamd.png[/IMG]

If the driver is active, Skype crashes whenever somebody call me (but it is relatively stable when I call). But if the driver is inactive, I have obviously no sound from my computer on my TV (via HDMI).

My question: how to get Skype stable and in the same time sound on my tv via HDMI?

Some hints to solve my problem?

Thanks!

Bye.

N.B.: I can't throw off Skype because almost all my contacts (private and professional) are on Skype.

---

### Post by gruiiik on 2012-11-22
Hello,

Problem solved by trial and error. I hope that the situation will remain stable for a very long time.

Here's how I did it (if it can help someone else in a similar situation or somewhat similar) : 

[LIST]**upgrade Skype** (done today) : the current version is 4.0.1.20;[/LIST]
[LIST]**activation** of driver **ATI/AMD**;[/LIST]
[LIST]**cancel** *<account-skype>* directory in the directory **.Skype**;[/LIST]
[LIST]**enter** in **Skype**;[/LIST]
[LIST]in **Options -> Notifications** of Skype, **mute** all **sounds**;[/LIST]
[LIST]in **Options -> video devices** of Skype, **uncheck** (if checked) the **automatic start** of the **video**.[/LIST]

Why does it work ? It's a mystery (for me).

Bye.

---

### Post by gruiiik on 2012-11-22
I forgot to add the tag [SOLVED] to the title. I think I can't add it now that I have answered. Sorry.

Bye.

---

