---
title: "enabling direct rendering"
date: 2006-09-08
forum: Multimedia &amp; Video
---

### Post by nbpetts on 2006-09-08
I have recently been having problems with running Doom 3.  I have worked out that the problem involves the fact that direct rendering was disabled when i installed xgl.  I followed the instructions from this HOW-TO [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)
following method 1.  However, glxinfo | grep direct render still returns that direct render is disabled.  Any suggestions on how to get this working again?


athalon 2200
gforce 6600
512 ddr 3200
ubuntu dapper 6.06
k7 kernal

---

### Post by dannyboy79 on 2006-09-08
you can't have direct rendering and xgl! I would suggest that if you're a gamer that you install xgl and compiz as another session so that when you want to login you have a choice between xgl session and normal gnome session. If you want to run xgl and still have good video performance check this out at [http://www.compiz.net/topic-1623-howto-opengl-acceleration-with-session-still](http://www.compiz.net/topic-1623-howto-opengl-acceleration-with-session-still), I did it but I am not sure if it's working or not because I moved onto trying to get mythtv working and set aside my compiz and xgl trials. I do have compiz working as a different session but what I am saying is that I am not sure whether or not following all these instructions worked for me since I didn't try to watch any videos when compiz and xgl was loaded

---

### Post by nbpetts on 2006-09-08
I have disabled xgl, and replaced my xorg.conf file, so i dont think that xgl is still the culprit

---

### Post by dannyboy79 on 2006-09-08
well, if you have put your computer back the way it was prior to xgl and compiz than you should be fine. If you replaced your xorg.conf file with the old one, are you sure that the driver still says, "nvidia"? If it still says nvidia and you are still having a problem with direct rendering being enabled why don't you try and uninstall your nvidia driver per the link you provided and then reinstall it? Maybe that would work. I am just a newbie so I wish I could of more help!

---

### Post by nbpetts on 2006-09-11
ok, i got it working.  For some reason byond me, the second time I installed the nvidia driver, it just worked.  thanks for all the help.

nbpetts

---

