---
title: "MP3 ID3 Tag Re-writing Itself"
date: 2009-10-03
forum: Multimedia Software
---

### Post by urlacher3292 on 2009-10-03
When editing one particular mp3 (Summer, Highland Falls by Billy Joel in case you were wondering) the metadata decides to rewrite itself. I was trying to orgnaize my library by Album since a few songs had the wrong info. Every time I edit the album of this file, and only this file, after about a two second wait it revert sto the original, wrong album title. It's frustrating and extremely odd. I have tried using both Rythmbox and Easytag.

---

### Post by RedRat on 2009-10-03
> **urlacher3292 said:**
> When editing one particular mp3 (Summer, Highland Falls by Billy Joel in case you were wondering) the metadata decides to rewrite itself. I was trying to orgnaize my library by Album since a few songs had the wrong info. Every time I edit the album of this file, and only this file, after about a two second wait it revert sto the original, wrong album title. It's frustrating and extremely odd. I have tried using both Rythmbox and Easytag.

This may or may not work for you but try using Thunar, its a file management program much like Nautilus but you can go in and change the ID3 tags. Since it is only one mp3, it should not hard. Thunar is in Synaptic, at least for Hardy which I use. 

Another program to try is Amarok, which I also use. Make sure that you have read-write permission for this file. It sounds as if you might have only read permission for the file.

---

### Post by vinutux on 2009-10-03
Try **Ex Falso**

---

### Post by vinmar on 2010-01-12
Probably this bug, need to somehow strip the APEv2 tags from the file.

[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/235945]("https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/235945")

---

