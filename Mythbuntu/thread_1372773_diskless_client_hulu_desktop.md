---
title: "diskless client hulu desktop"
date: 2010-01-04
forum: Mythbuntu
---

### Post by jimp180 on 2010-01-04
Has anyone gotten hulu desktop to work on a diskless client frontend? I can't seem to put the libflashplayer.so file in a place that hulu desktop is happy with

---

### Post by matt06 on 2010-01-05
I'm not using a diskless client, but maybe this will help you.

In my /home/username/.huludesktop file I have:

> mythuser@mythtv-cf:~$ cat /home/mythuser/.huludesktop | grep flash
[flash]
flash_location = /usr/lib/flashplugin-installer/libflashplayer.so

location of my libflashplayer.so file(s):

> mythuser@mythtv-cf:~$ locate libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/libflashplayer.so

The locations may vary on your system though from what I've read.  Is this a Hulu or Flash issue with diskless client only?  I remember having problems at one point or another getting Hulu working with Flash.

---

### Post by jimp180 on 2010-01-05
Thanks for the reply, I was having problems with Hulu finding the flash player, I tried all of the places that different people posted on different sites and forums including your setup but none of it seemed to work. I did get it fixed though, I realized that I didn't have firefox installed on this front-end so I installed it and then put the libflashplayer.so file in /usr/lib/mozilla/plugins and changed my .huludesktop file to reflect this location and it works now

I didn't think that firefox was a prerequisite to hulu or flash but that seemed to be the fix for me!

---

### Post by matt06 on 2010-01-05
Nice catch.  Will have to remember that if I ever go to remove unnecessary packages from my frontend.

---

