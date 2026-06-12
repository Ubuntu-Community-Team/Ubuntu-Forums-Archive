---
title: "Can barely play any DVDs"
date: 2006-12-22
forum: Multimedia &amp; Video
---

### Post by PatrickMay16 on 2006-12-22
Hello.

I have a collection of DVDs. I recently got a laptop which has a DVD drive, so I thought I'd try watching some DVDs.

I've tried about 6 different DVDs... only one of them worked! All the others gave this error in totem: "could not open location; you may not have permission to open the file" or something similar.

Is there any way I can get more DVDs to play? Or am I stuck watching nothing other than "super size me"?

---

### Post by taurus on 2006-12-22
What media player are you using to play those DVDs?

---

### Post by PatrickMay16 on 2006-12-23
totem-gstreamer, and ogle.

---

### Post by taurus on 2006-12-23
Have you tried vlc?  It's in the repos...

---

### Post by blackmh on 2006-12-23
Check if DMA is turned on. 
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_speed_up_CD.2FDVD-ROM](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_speed_up_CD.2FDVD-ROM)

---

### Post by PatrickMay16 on 2006-12-23
> **taurus said:**
> Have you tried vlc?  It's in the repos...

I haven't tried vlc. I will give it a go now.

Also, to blackmh; Yeah, I checked it before and DMA was on.

---

### Post by chele on 2007-07-02
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/10550](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/10550) [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				> **PatrickMay16 said:**
> ... 6 different DVDs... only one of them worked! All the others gave this error in totem: "could not open location; you may not have permission to open the file" ...Put "gksudo"  in front of the totem command  in System Preferences...

The problem is that the DVD's are being monuted with funky file permissions, allowing only the root user to view them.

---

