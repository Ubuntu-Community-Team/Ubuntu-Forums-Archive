---
title: "Anyone getting corrupted videos, recording with ogv? Read this!"
date: 2010-06-28
forum: Multimedia Software
---

### Post by Half-Left on 2010-06-28
About a week ago I decided to do a screencast but found that when I uploaded the OGV to YouTube or imported it into a video editor, it would look corrupted. It seems like some Theora codec issue in Ubuntu Lucid(not sure if it affects other distros). 

Just to let you know, thankfully there is a way to make your corrupted video perfect again.

Install Devede and pick DivX / MPEG-4 from the option at the start, then add your video via the Add button. Click (None) at the top and pick your video. Now select any advanced options you need, like resolution and ratio(pick something near to the resolution you recorded it in. Click OK click forward.

Just enter the name of your video and where to export it to and then click OK. Now your video should show just fine in your video editor or YouTube. 

Hope this helps.

---

### Post by crouchdash on 2010-06-28
Great! This was really bugging me for a while. I'll try it later!

---

### Post by lovinglinux on 2010-06-28
I convert them to avi with mencoder. Works for me.

---

### Post by Half-Left on 2010-06-28
> **lovinglinux said:**
> I convert them to avi with mencoder. Works for me.

Yeah, any app will do. I just found Devede to do the job and a has a decent UI.

---

### Post by lovinglinux on 2010-06-28
> **Half-Left said:**
> Yeah, any app will do. I just found Devede to do the job and a has a decent UI.

I wonder when they will fix this. My videos are totally messed without the conversion and sometimes has several extra minutes with a static desktop image.

---

### Post by ron999 on 2010-06-28
Hi
There's a solution using mencoder discussed on this thread here:-[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1501566]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1501566")

---

### Post by Half-Left on 2010-06-28
> **lovinglinux said:**
> I wonder when they will fix this. My videos are totally messed without the conversion and sometimes has several extra minutes with a static desktop image.

Yep, no idea who how this bug got through, I mean it's one of the most standard codecs FOSS uses. I've not tried it on any other distro so I don't know if it's Ubuntu specific.

No doubt Canonical will wait for an upstream fix as usual.

---

