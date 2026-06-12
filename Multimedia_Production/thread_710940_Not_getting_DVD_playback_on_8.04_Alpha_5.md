---
title: "Not getting DVD playback on 8.04 Alpha 5"
date: 2008-02-29
forum: Multimedia Production
---

### Post by Elotero on 2008-02-29
Followed many tutorials but none have helped. Installed VLC. No DVD is detected. Getting this error:

No stream found to handle url dvd://1

Anyone else run into this??

---

### Post by Lester_Burnham on 2008-04-13
Hi,

I found some where else to run this to link DVD1 to just DVD

sudo ln -s /dev/dvd1 /dev/dvd

It worked for me in mplayer.

Lester

---

### Post by thorgal on 2008-04-13
it often has to do with the default device apps are trying to use. Not every linux system has a /dev/dvd linked to the real device. Depending on whether you have a SATA or IDE  DVD drive, the real device node might be /dev/scd0 or /dev/hdx, x being b, c or d depending on how many other IDE devices you have. I have a USB case with an IDE DVD drive in it. Because it is USB, it shows up as /dev/scd0. You can create a udev rule for it (udev is the system utility that creates device nodes in a plug'n'play fashion). 

OK, that's a bit geekish if you don't know much about the linux guts. But I am sure VLC and other apps allow you to change the name of the device node in their setup. So if /dev/dvd is not working, it's just that there's no symbolic link to the real node being /dev/scd0 for example. YMMV :)

---

