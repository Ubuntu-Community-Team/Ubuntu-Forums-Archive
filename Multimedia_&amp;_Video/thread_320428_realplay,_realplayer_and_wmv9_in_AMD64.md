---
title: "realplay, realplayer and wmv9 in AMD64"
date: 2006-12-17
forum: Multimedia &amp; Video
---

### Post by pickarooney on 2006-12-17
Using automatix, I installed RealPlayer 10, but it won't play the video or sound in any .RM files. 
apt-get doesn't find any packages called realplay which should be version 8 I believe?
I also can't playback any WMV or WMA files.
Is there any way of installing codecs for playing these types of files on AMD64?

---

### Post by pay on 2006-12-17
Yes, but you need to download and install a 32bit player and then the 32bit codecs because windows media codecs are only 32bit. Just download the debs but install them with ```
sudo dpkg --force-architecture my.deb
```

---

### Post by pickarooney on 2006-12-17
OK, got the codecs installed. So I need a 32-bit version of Xine to play back RM and WMV files, I guess?

---

### Post by flygin on 2006-12-17
you can install chroot environment for 32 bit programs.
I did that for firefox and realplayer. You can also compile applications that only work in 32 bit (somehow better than the complie option).
there is a lot of help on the forums for installing a 32bit chroot environment.

---

### Post by pay on 2006-12-17
A chroot is overkill. Just install the 32bit Xine.

---

### Post by pickarooney on 2006-12-18
> **pay said:**
> A chroot is overkill. Just install the 32bit Xine.

ah so this *is* possible? All the threads I searched on it mentioned installing chroot.

---

### Post by pickarooney on 2006-12-19
Ehm, where can I get a 32-bit xine deb?
Do I need to uninstall the 64-bit one and all its dependencies or can I overwite it, or do they two coexist and use different names for the executable binary?

---

### Post by jkwarras on 2006-12-19
> **pickarooney said:**
> Ehm, where can I get a 32-bit xine deb?
Do I need to uninstall the 64-bit one and all its dependencies or can I overwite it, or do they two coexist and use different names for the executable binary?

You can get the 32bits version from the packages.ubuntu.com site. AFAIK, both packages will use the same name, so uninstall 64 bits version to avoid problems.

---

### Post by pickarooney on 2006-12-21
I have a 32-bit realplayer installed now, but it doesn't playback RM files properly. I get a bit of an image, then a break, a bit of sound, etc. I'm probably missing some later-version codecs?

---

### Post by pickarooney on 2006-12-24
OK, I'm still not getting this. Simply, how do I play RM files in Kubuntu 64?

---

### Post by tseliot on 2006-12-24
have a look at this thread:
[http://ubuntuforums.org/showthread.php?t=191205](http://ubuntuforums.org/showthread.php?t=191205)

but I guess that installing vlc would do the trick as well

---

