---
title: "youtube not working?"
date: 2009-02-25
forum: Multimedia Software
---

### Post by tombom62 on 2009-02-25
hey, I just found  out that youtube vids won't play....... well... sort of.  They can play with the plugin  in totem, but not in browser. (firefox) other flash items do work, so I do not k now what is happening.  anyone know?:guitar:

---

### Post by gandaran on 2009-02-25
do you have adobe flash installed or gnash or swfdec flash?
for it to work properly you must only have adobe flash installed.

---

### Post by sailsandwaves on 2009-02-25
> **tombom62 said:**
> hey, I just found  out that youtube vids won't play....... well... sort of.  They can play with the plugin  in totem, but not in browser. (firefox) other flash items do work, so I do not k now what is happening.  anyone know?:guitar:


HI I have found the source of the problem I think:
I have the latest version of Ubuntu with all updates:
Pentium 4 w/:2.8ghz processor and 2x228 RAM +(new)2x556 RAM
I have been having problems with flash but most of all Firefox(closing/crashing) so I got extra RAM, and this is how I found the origin of the problem:
It is Ubuntu its self that is problematic it seems:
By typing :KS Free in a terminal:KS I get the Ram usage of my computer:
This is meant to vary up and down with use: but :KS in Ubuntu it keeps going up and up :KS ! When I close programs only a portion of the Ram is freed again and I believe this is the reason for the firefox problems
as well as other problems in Ubuntu.:popcorn:
sails.

---

### Post by tombom62 on 2009-02-25
@gandaran: i have adabe flash, yes.
@sailsandwaves: i have got 1 gb of ram, a 2.4 ghz chip, and a 160gb hdd.  I also have xubuntu, not ubuntu, and I have tried opmimizing it for speed,I don't think memory usage is my problem.

---

### Post by tombom62 on 2009-02-26
bump.
no luck.

---

### Post by lukjad on 2009-02-26
Well, if you want to see youtube videos, try installing youtube-dl (sudo apt-get install youtube-dl). It downloads youtube videos to your computer.

---

### Post by tombom62 on 2009-02-27
ok, i did that, but i would stil like to have browser vids.  any other help?

---

### Post by BrandonBan6 on 2009-03-24
> **tombom62 said:**
> ok, i did that, but i would stil like to have browser vids.  any other help?

Tombom,

I've got the same problem!! :( 

I have tried gnash, the nonfree plugin, I've installed the .deb package from adobe. I have tried extracting the .so file into my /usr/share/mozilla/plugins/ folder and have gotten no where. So, I put the .so file in /home/<username>/.mozilla/plugins/ and still nothing. I've uninstalled firefox and it's dependencies, and then re-installed it. I have tried opera and firefox.  I'm pulling my hair out here in frustration. I too am running xubuntu 8.10.

---

### Post by BrandonBan6 on 2009-03-24
> **BrandonBan6 said:**
> Tombom,

I've got the same problem!! :( 

I have tried gnash, the nonfree plugin, I've installed the .deb package from adobe. I have tried extracting the .so file into my /usr/share/mozilla/plugins/ folder and have gotten no where. So, I put the .so file in /home/<username>/.mozilla/plugins/ and still nothing. I've uninstalled firefox and it's dependencies, and then re-installed it. I have tried opera and firefox.  I'm pulling my hair out here in frustration. I too am running xubuntu 8.10.

Okay, so I have it working in Opera now. I downloaded the .tar.gz file from adobe. I then extracted the file and ran "sh <filepath>/flash-installer". When prompted, I installed the file in /usr/lib/opera. 

I then launched Opera, in the content section in the preferences menu, I selected /usr/lib/opera for both the swf and spl MIME types. 

still trying with firefox.

---

### Post by leonardo_neo on 2009-03-25
Well firefox is giving trouble for a while in streaming videos.

I got help from this link. Hope this helps you too. :)

> [http://ubuntuforums.org/showthread.php?t=1101074](http://ubuntuforums.org/showthread.php?t=1101074)

---

### Post by BrandonBan6 on 2009-03-25
thanks! I actually ended up getting it late last night. 

Under the firefox tools menu, there is a manage plugins option. I went to that and changed adobe flash player MIME type to use Adobe flashplayer and not the other one it had selected, and presto it worked!

---

