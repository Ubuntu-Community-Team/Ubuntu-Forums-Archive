---
title: "Sound doesn't work for some media files"
date: 2007-11-08
forum: Multimedia &amp; Video
---

### Post by Cerebrum on 2007-11-08
My soundproblems:
 
My system:
My computer has the motherboard: PCCHIPS A13G+
[http://www.pcchips.com.tw/PCCWebSite/Products/ProductsDetail.aspx?DetailID=392&CategoryID=1&DetailName=Feature&MenuID=44&LanID=0](http://www.pcchips.com.tw/PCCWebSite/Products/ProductsDetail.aspx?DetailID=392&CategoryID=1&DetailName=Feature&MenuID=44&LanID=0)

I'm using Ubuntu 7.10 - the Gutsy Gibbon, I was using Feisty before and had the same problems.

The sound hardware of my Mobo is in the NVIDIA MCP61S Single chipset. This chipset consists of: GeForce® 6100 GPU and MCP nForce® 405

What works:

The login and logout sound works fine.
If I go to the "Examples" folder that is installed by default I can play "Experience ubuntu.ogg" and "ubuntu Sax.ogg" just fine using the Totem player. But if I play "fables_01_01_aesop.spx" the sound is very very low, almost inaudible.

Pidgin/Gaim messaging sounds also work fine.

What doesn't work:

Now if I use the same Totem player to play an .avi file the sound is very low and distorted. And it depends on the avi file. There are some files where I can hear the sound, although it is still low and distorted, others are inaudible.

Summing it up: 

The sound is working, but it seems to be a problem of some file formats(CODECS?) not working properly.

Below are some more technical details:

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

With the command "lspci -v" I get the following information:

00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)


Suggestions anyone?

PS: Yes, I installed mplayer and I have the same problems with it. Even worse, with mplayer the video doesn't work!

---

### Post by Cerebrum on 2007-11-08
Anyone?

---

### Post by Cerebrum on 2007-11-09
?

---

### Post by Cerebrum on 2007-11-12
?

---

### Post by Cerebrum on 2007-11-16
?

---

### Post by Yellow Pasque on 2007-11-17
When I have ALSA problems (and I usually do) I use OSS (see my sig for details)

---

### Post by Cerebrum on 2007-12-04
> **Temüjin said:**
> When I have ALSA problems (and I usually do) I use OSS (see my sig for details)

Thanks for the tip Temujin. I installed OSS but I'm having problems with it as well. I posted about it on the OSS forums:

[http://www.4front-tech.com/forum/viewtopic.php?p=6912#6912](http://www.4front-tech.com/forum/viewtopic.php?p=6912#6912)

---

### Post by Cerebrum on 2008-03-31
Solution: repartition the HD and install Windows XP!!! I'm happy again.

Lesson learned: if you are not 100% sure go for a double-boot. You only need a few Gb more and can share the data between Windows and Linux anyway, so no big deal.

---

### Post by zanoman on 2008-04-05
I'm thinking of getting a bundle with A13G+ for my ubuntu and found your post.
I had trouble with ubuntu in the past with my K8-VM (nvidia everywhere).

After months, I found that Totem was just crap depending on codecs, I switched to VLC (videolan.org) and OSS. Firefox working in backgournd (with youtube or other flash for instance) also removed the sound in another player (didn't share audio channels). I also installed "ugly", and "bad" codecs (don't remember which repo). It's their real names.
Now it works fine with Gutsy, except suspend and hibernate.

I switched from XP to Ubuntu, the day I wanted to change more than 6 parts in my computer (basically, I kept the disk and installed a new bundle around it, so audio, video, MB, CPU, ... changed), because of the flags stuff I couldn't start Windows.

Today I'll do the same, but at least, I know that it will work. Just a matter of package to install :)

---

