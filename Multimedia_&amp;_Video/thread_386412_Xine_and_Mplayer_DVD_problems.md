---
title: "Xine and Mplayer DVD problems"
date: 2007-03-17
forum: Multimedia &amp; Video
---

### Post by koulanji on 2007-03-17
When I try to run a dvd in xine media player I get the following error messages

There is no input plugin to handle dvd
Maybe MRL syntax is wrong or file/stream source does not exist

The source cannot be read; maybe you do not have enough rights for this or source does not contain data

For Mplayer I get this 
 Failed to open dvd://1

Any solutions; everything was working fine when I last played a dvd

---

### Post by ssavelan on 2007-03-17
Do you have libxine-extracodecs?

---

### Post by koulanji on 2007-03-17
Yes I do have libxine-extra codecs sir

---

### Post by ssavelan on 2007-03-17
Have you attempted to load the material in other media players like totem/gxine/kaffeine/etc?

Have you attempted other DVDs?

** usually my little 'get libxine-extracodecs' advice works.... uh oh **

---

### Post by koulanji on 2007-03-17
Yup the dvds work fine elsewhere. They work in SUSE on my lappy and gentoo on my amd, just no here lol :)

---

### Post by hilde on 2007-03-22
I had the same error output from kaffeine, but Mplayer opened the DVD successfully and started complaining about an Encrypted VOB file, so I could solve my problem with
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```
which I found in another forum thread.
In Gentoo I had no problems with this DVD.

Do you have this problem with any DVD or just one?

---

### Post by thewump on 2007-03-22
Hey Hilde - thanks, that solved my issues.

---

### Post by Temis on 2007-05-11
> **hilde said:**
> I had the same error output from kaffeine, but Mplayer opened the DVD successfully and started complaining about an Encrypted VOB file, so I could solve my problem with
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```
which I found in another forum thread.
In Gentoo I had no problems with this DVD.

Do you have this problem with any DVD or just one?

Great I can now play dvds with Mplayer, but it only works for one user (with admin privileges) the other users get this error message: Error opening/initializing the selected video_out (-vo) device.
Any solution for this?

---

### Post by Temis on 2007-05-13
I am giving up on Mplayer until it becomes as reliable  as Totem.
After I did this code  ( sudo /usr/share/doc/libdvdread3/install-css.sh )                                                                         it worked one day now it says again: Failed to open dvd://1

---

