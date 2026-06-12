---
title: "[SOLVED] video all scrambled"
date: 2008-11-09
forum: Multimedia Software
---

### Post by cybergalvez on 2008-11-09
Hi all, when I play some DVD's the video is all scrambled (see attachment).  I've read all links I can find in this forum and nothing works, including adding restricted-codecs. and running install-css.sh from libdbvdread3

I'm runnign 8.10 amd64 currently fully patched

Any and all help would be much appreciated

Jose

---

### Post by cybergalvez on 2008-11-10
Bump, does anyone have any suggestions?

---

### Post by mc4man on 2008-11-10
Either go here and add medibuntu as a source (use Intrepid line and the add key line
Then go in terminal ```
sudo apt-get install libdvdcss2
```

or do a direct download and install from here (choose the amd64 version

[http://packages.medibuntu.org/intrepid/libdvdcss2.html](http://packages.medibuntu.org/intrepid/libdvdcss2.html)

Then try again

---

### Post by lavinog on 2008-11-11
What movie is it?
Sony has been making non-compliant DVDs to deter copying.
These DVDs don't seem to work with current DVD decrypting software/players.

Some hardware DVD players also can't play these DVDs. There are lawyers looking for people with these players for a class action suit against Sony.

---

### Post by cybergalvez on 2008-11-11
> **mc4man said:**
> Either go here and add medibuntu as a source (use Intrepid line and the add key line
Then go in terminal ```
sudo apt-get install libdvdcss2
```

or do a direct download and install from here (choose the amd64 version

[http://packages.medibuntu.org/intrepid/libdvdcss2.html](http://packages.medibuntu.org/intrepid/libdvdcss2.html)

Then try again

Thanks I already had libdvdcss2 installed and I even rebuilt it using the command /usr/share/doc/libdvdread3/install-css.sh as suggested in the media sticky, however things didn't get fixed unill I deleted everything in my .dvdcss folder.  Once I deleted everything in that folder the DVD started to play correctly.

---

