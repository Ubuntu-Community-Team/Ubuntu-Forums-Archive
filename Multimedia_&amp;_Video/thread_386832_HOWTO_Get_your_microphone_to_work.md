---
title: "HOWTO: Get your microphone to work"
date: 2007-03-17
forum: Multimedia &amp; Video
---

### Post by Cappy on 2007-03-17
Moved: [http://www.ubuntuforums.org/showthread.php?p=2306168](http://www.ubuntuforums.org/showthread.php?p=2306168)

---

### Post by Titi on 2007-03-20
> **Cappy said:**
> 

Now, click on the **Capture** tab ...

i wish i could do that, but i don't have a capture tab! how can i get it there? thanks

---

### Post by Cappy on 2007-03-20
You checked all the **Check Boxes** in preferences and you still didn't have a Capture Tab? You could try the tip at the bottom about using
```
alsamixer
```
instead.

---

### Post by Titi on 2007-03-20
ok, but my alsamixer seems to differ from yours. also, i can't adjust the volume for the Mic. i don't know what's wrong...
screenshot in attachment.

---

### Post by Cappy on 2007-03-20
You don't control the volume there. Hit **F4** which will bring you to the **Capture Tab** (you hit F5). Hit your **SPACE** on the _CAPTURE_ control. Raise the _CAPTURE_ control's volume - this is where your mic volume is. Now test your mic and see if it works. If not, then hit **SPACE** on that _AC97_ control (to turn capture off) and then hit space on that _Mic/Line in Capture_ control (to turn capture on). If  that doesn't work .. you could try activating the capture on both .. or maybe there is another control with _"Mic" or "Capture" or "Mix"_ that I can't see in your screenshot (that you can find). 
You can't really break anything so don't worry about doing something wrong or experimenting.

---

### Post by Titi on 2007-03-21
unbelievable! suddenly it worked! alsamixer just looked totally different. i don't know what i did. now your suggestions do work. thanks a lot.
i'm really happy man :) (or woman)

---

### Post by nolox on 2007-03-24
Hi guys! I've read this post so interested because I've a similar problem with mi hell micro. I've sound in my laptop but I can't record sound

I've a hp laptop dv2141eu. Webcam and Micro are integrated in laptop. I get  my webcam runnig but can't run micro.

I've tried to follow the instructions of this post but my alsamixer is so different. I only have "master" "pcm" and "capture" (put at level 100) I haven't a field to activate micro.

something strange is that seems to be I have two dispositives:

0 HDA Nvidia (alsa mixer)
1 Generic 14f1 ID 5045 (OSS mixer)

In this last dispositive I only have controls for "In-gain" and "Volume"

I've tried so many configuration but neither run...

Could you help me please? I need have micro running for my job.

---

### Post by jrz on 2007-04-02
We've been trying for months now to get the microphone to work on a new compaq Presario V3000 notebook, following FAQ's, hints, IRC help, and any info we could possibly find with zero success. Our alsamixer shows all controls set to 100, and identifies our Card: HDA Nvidia, and Chip: Generic 14f1 ID 5045. We have just recently reinstalled the OS, Ubuntu 6.06 from scratch and applied all recommended updates in order to eliminate any problems that may have been introduced through so many installs directed by advise by numerous persons. If anyone has a similar system and could provide us with some insight as to where to begin to repair this problem we would be very appreciative. Obviously we have no idea where to begin and are at the mercy of those who are kind enough to provide help. Thanks.

---

