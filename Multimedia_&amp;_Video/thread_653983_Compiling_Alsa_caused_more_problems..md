---
title: "Compiling Alsa caused more problems."
date: 2007-12-30
forum: Multimedia &amp; Video
---

### Post by blue4paper on 2007-12-30
Like the title reads after i compiled alsa it just caused more problems. Now my sound card (HDA-intel) isn't recognized any more. I followed every step. Everything worked great. I think it was even a tutorial from ubuntuforums i'm not too sure. Anyways here are some pictures of what it says when i try opening alsamixer or doing the speaker test.



[[IMG]http://img81.imageshack.us/img81/3276/screenshot1ul6.th.png[/IMG]](http://img81.imageshack.us/my.php?image=screenshot1ul6.png)

[[IMG]http://img81.imageshack.us/img81/2896/screenshotyz5.th.png[/IMG]](http://img81.imageshack.us/my.php?image=screenshotyz5.png)

---

### Post by blue4paper on 2007-12-30
hm i found a new compiling alsa guide "https://help.ubuntu.com/community/HdaIntelSoundHowto" and everything in there is exactly what i did except for one thing. Where it says "sudo mkdir -p /usr/src/alsa" i did "sudo mkdir -p /usr/alsa/" could this be causing my audio issues?

Edit : Also when i type in the command "cat /proc/asound/card0/codec#* | grep Codec" i get "no such file or directory"

---

### Post by Yellow Pasque on 2007-12-30
You can try OSSv4 and ditch ALSA if it doesn't work. The instructions are linked in my sig.

---

### Post by blue4paper on 2007-12-30
Yeah actually its funny, i was looking around ubuntuforums i saw one of your post, looked down saw your sig. Thats the one that fixed it lol. Except now, i'm left with alsa. 

So i got 2 small problems. How can i uninstall alsa. aka alsa drivers, alsa utils, alsa firware and alsa libs.

2nd the only configuration for OSSv4 is that jackinput or whatever its called. And only sound comes out of 2 of my speakers. On my windows my surround sound works wonders but i dont get how to configure it on ubuntu. Any other OSS configurations?

---

### Post by blue4paper on 2007-12-31
Now i got 3 speakers to work. Only 1 rear 1 front speaker and my center speaker work. I'm not sure why but the OSSmixer doesn't recognize the green jack input to be for both (2) speakers in the front or the black/grey input to be for 2 rear speakers and not just. Anyway to tell the program that there are 2?

---

### Post by Yellow Pasque on 2007-12-31
Do a:
```
sudo gedit /usr/lib/oss/conf/vmix.conf
```
and remove the '#' in front of the vmix_multich_enable=1  line

---

### Post by blue4paper on 2008-01-01
tried that, made my sound much worse. Now after listening to my sound, its all distorted cracking then after about 5 seconds it stops and my ubuntu freezes ^^.''

---

### Post by Yellow Pasque on 2008-01-03
Didn't mean to leave you hanging. Let's look at ossinfo -v and see what that tells us.

---

