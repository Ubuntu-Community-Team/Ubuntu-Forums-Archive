---
title: "VLC not playing shoot 'em up"
date: 2008-09-05
forum: Multimedia Software
---

### Post by Tower43 on 2008-09-05
sorry, maybe It's already answered, but i am completely confused and i need a step-by-step, point and click instructions on how to watch the movie ... anyone could help me please? =[[

---

### Post by mc4man on 2008-09-05
that's due to a structure protection.
A couple of ways to fix
One way is to go here and follow instructions
basically adding a repo and then installing a patched dvdnav (don't remove current, installs along side

[http://tobias.rautenkranz.ch/debian/](http://tobias.rautenkranz.ch/debian/)

The other way is to install the new libdvdnav4

Just d. click on the download link and let gdebi install
(again don't uninstall current libdvdnav4 - gbebi will handle for you (most likely the i386 ver.

[http://packages.debian.org/lenny/libdvdnav4](http://packages.debian.org/lenny/libdvdnav4)

I'm using the new one now instead of the patched ver. - no problems (**hardy**

For mplayer you need to patch libdvdread in the source and build

patch
[http://tobias.rautenkranz.ch/code/libdvdread_udf.patch](http://tobias.rautenkranz.ch/code/libdvdread_udf.patch)

( at least with revision of a couple of months ago or older


edit;
> i need a step-by-step, point and click instruction

for the **new ver**. -> use the packages link, pick the i386 dl. link (for 32 bit ubuntu - what you probably have- for 64 bit ubuntu pick amd64
Click on it and from mirror page click on one (first one is fine

You'll get a pop up as in screenshoot 1 - choose open with as in screen
Click Ok and that's all you need to do

for the **patched** one

Go system -> administration ->  open software sources (screen 2
Click add

Paste in this line (as in screen 3
```
deb [http://tobias.rautenkranz.ch/debian](http://tobias.rautenkranz.ch/debian) stable/
```

Click add source , then close with a reload

Then run this in the terminal

```
wget -qO - http://tobias.rautenkranz.ch/tobias.rautenkranz.asc | sudo apt-key add -
```

followed by
```
sudo apt-get update
```

and finally 
```
sudo apt-get install libdvdnav-ifo4
```

 The  first one (new dvdnav) is much easier, only use the 2nd way if for some reason the new one won't install (unlikely on hardy

---

### Post by Tower43 on 2008-09-06
how do i open it with the "GDebi Package Installer (default)"?

---

### Post by Tower43 on 2008-09-06
mine just comes up with DEB file, instead of screenshot's software package

---

### Post by mc4man on 2008-09-06
Then just download the .deb ( to desktop probably) and d. click on it and let it be installed

Edit: right click on the downloaded .deb and choose GDebi Package Installer if available

what Os are you using?

---

### Post by Tower43 on 2008-09-06
it poped up and said 
"window cannot open this file," i need to select a program to open it?

---

### Post by Tower43 on 2008-09-06
vista,

---

### Post by Tower43 on 2008-09-06
with new version of vlc

---

### Post by mc4man on 2008-09-06
> vista,
Then use a licensed player like powerdvd or find a **windows** forum

---

### Post by Tower43 on 2008-09-06
ok then ill try my best tky for the help =]

---

### Post by Tower43 on 2008-09-06
i wonder if u could also post me a video/windows link on here as well? just to make life easier ? please?

---

### Post by mc4man on 2008-09-06
I really don't know if a win. ver. of vlc can play the x-protect disks (mainly some new line cinema titles in region1.

I'd go here and search or join and post a question (based on x-protect
[http://forum.videolan.org/viewforum.php?f=14](http://forum.videolan.org/viewforum.php?f=14)

otherwise search and use the free dvdfabhddecrypter and rip to hdd
[http://www.dvdfab.com/free.htm](http://www.dvdfab.com/free.htm)

or search and use free trial of anydvd
[http://www.slysoft.com/en/anydvd.html](http://www.slysoft.com/en/anydvd.html)

---

### Post by Tower43 on 2008-09-06
tky sooo mcuh

---

