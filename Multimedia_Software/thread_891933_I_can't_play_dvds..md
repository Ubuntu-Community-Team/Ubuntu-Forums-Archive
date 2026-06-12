---
title: "I can't play dvds."
date: 2008-08-16
forum: Multimedia Software
---

### Post by MinderBinderNW on 2008-08-16
I can't get my dvd to play in any of the media players I have.

When I use totem it says cannot read from resource.
when I use gxine is opens then says "Error Segmentation Fault"
When I use vlc it doesn't do much of anything.

I tried the dvd playback starter guide and the thread titled starter guide not sufficient.  But I still can't get it to work.  Any suggestions would be much appreciated.

Thanks

---

### Post by jualin on 2008-08-16
Can you run VLC using the terminal and post the outputs? Go to the terminal and write > vlc

---

### Post by clueless on 2008-08-16
Have you tried installing the restricted package:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

and the medibuntu repo?
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by MinderBinderNW on 2008-08-16
When I start it in the terminal the player comes up with no error readings.

However I noticed that when I installed libdvdcss2 it said that the package is broken.

[HTML]ryan@ryan-laptop:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libdvdcss2: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is to be installed
E: Broken packages[/HTML]

---

### Post by jualin on 2008-08-16
Try running > sudo apt-get install libc6

---

### Post by lisati on 2008-08-16
Try this:
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```
It should work without the need to mess around with the repositories.

---

### Post by MinderBinderNW on 2008-08-16
jualin.

[HTML]ryan@ryan-laptop:~$ sudo apt-get install libc6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libc6 is already the newest version.
The following packages were automatically installed and are no longer required:
  libgtk-jni libcairo-java libglib-java libswt3.2-gtk-jni
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[/HTML]

---

### Post by jualin on 2008-08-16
Follow lisati suggestion since it may be easier than changing the repositories. Good luck!

---

### Post by MinderBinderNW on 2008-08-16
Ive done everything posted so far, but I still get a segmentation error with gxine and nothing at all with vlc.  I am running feisty fawn, is there a difference with the codecs?

---

### Post by MinderBinderNW on 2008-08-16
Also, I now have ogle.  When I try to open disc with that it flashes a screen and then instantaneously closes.

---

