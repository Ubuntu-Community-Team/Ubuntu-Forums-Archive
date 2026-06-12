---
title: "how i use medibuntu to install all codec"
date: 2011-07-03
forum: Multimedia Software
---

### Post by MMALLOW on 2011-07-03
hi

how i use medibuntu to install all codec

free AND NONE FREE

---

### Post by MartyBuntu on 2011-07-03
Add the Medibuntu repository...

Read this:

[http://medibuntu.org/repository.php](http://medibuntu.org/repository.php)

---

### Post by wolfen69 on 2011-07-03
After installing the medibuntu repos, do:
```
sudo apt-get install non-free-codecs
```
and it will give you all the codecs you will need.

---

### Post by MMALLOW on 2011-07-04
thanks for all

  MY FRIEND GIVE ME THIS CODEC 

THIS CODEC ENOUGH TO PLAY ALL 

UDIO AND VEDIO OR I NEED MORE 

  ubuntu-restricted-extras
   
  gstreamer0.10-plugins-ugly
  gstreamer0.10-plugins-ugly-multiverse
  gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-bad-multiverse
  gstreamer0.10-ffmpeg

---

### Post by nomko on 2011-07-04
Also installed the following codecs:
 
- w32codecs (for 32-bit) or w64codecs (for 64-bit)
- libdvdcss2
- non-free-codecs
 
When you installd the package libdvdcss2 do the following:
 
- open a terminal
- type the following command:
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```
- press enter
- type in your password and press enter

---

### Post by MMALLOW on 2011-07-04
> **nomko said:**
> Also installed the following codecs:
 
- w32codecs (for 32-bit) or w64codecs (for 64-bit)
- libdvdcss2
- non-free-codecs
 
When you installd the package libdvdcss2 do the following:
 
- open a terminal
- type the following command:
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```- press enter
- type in your password and press enter


THANKS FOR YOU TO MUCH

BUT WHY UBUNTU DON'T MAKE ONE SIMPLE LIST LIKE THIS INCLUDING ALL CODEC

[B]
  ubuntu-restricted-extras
  gstreamer0.10-plugins-ugly
  gstreamer0.10-plugins-ugly-multiverse
  gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-bad-multiverse
  gstreamer0.10-ffmpeg
w32codecs (for 32-bit) or w64codecs (for 64-bit)
libdvdcss2
non-free-codecs[/B]

LIKE THIS LIST ITS SIMPLE  AND EASY TO ARRIVE

SPEACHIALY TO PEOPLE DONT HAV INTERNET

OR PEOPLE WANT ORIGINAL UBUNTU AND CODEC ONLY

NOT LIKE MINT CHANGE SOME PROGRAM

THANKS

---

### Post by nomko on 2011-07-04
Most of those codecs the usage of them are restricted by licenses. So, Canonical cannot add those codecs just like that. To avoid any legal issues it is decided that those codecs are not supplied standard in (K)Ubuntu.

---

### Post by MMALLOW on 2011-07-04
I UNDERSTAND NOW

IM SORRY I MAKE HEAVY FOR YOU BUT I WANT SOME THING MORE

CAN YOU GIVE ME ONE SCRIPT FOR ALL THIS CODEC 

[B]ubuntu-restricted-extras
  gstreamer0.10-plugins-ugly
  gstreamer0.10-plugins-ugly-multiverse
  gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-bad-multiverse
  gstreamer0.10-ffmpeg
w32codecs (for 32-bit) or w64codecs (for 64-bit)
libdvdcss2
non-free-codecs[/B]

TO MAKE IT FAST

THANKS

---

