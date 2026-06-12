---
title: "Audio CD's won't mount In Ubuntu"
date: 2009-11-07
forum: Multimedia Software
---

### Post by nfgrachanin3 on 2009-11-07
I have a Dell XPS A2420 "all in one". The DVD/CD drive will not mount audio CD's and let them play in the music player. It will flash on the screen for a second and then go through the cycle again. I tried in 9.04 and now 9.10 with the same results. Data software loads with no problem and movie DVD's will load but will not get past the initial clips on the movies using all the players in Synaptic. The Audio CD's mount and DVD's run fine in Xubuntu and Kubuntu. It seems the culprit is Nautilus. Any ideas? 
The fstab shows UUID=ea2812db-3e4e-4e7e-a993-cd93d4813f86 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by sc30317 on 2009-11-07
Can you mount the CD's manually?

---

### Post by nfgrachanin3 on 2009-11-08
No they will not manually mount. The Cd will mount for a second then disappear with the messsage DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus). The audio CD's mount just fine on all of the other Dell computers we have here and mount fine in Kubuntu and Xubuntu but will not mount in Fedora 11 just like 9.04 and 9.10. I just found a post  Re: Known Jaunty Jackalope bugs with workarounds
Grip can't eject CD and also rips slow

Grip eject code no longer works so it thinks that a new CD has been inserted and remains in a loop continually ripping the one CD unless manually terminated. Also CD ripping is very slow unless following code is used.

Bug: [https://bugs.launchpad.net/ubuntu/+s...ip/+bug/382013](https://bugs.launchpad.net/ubuntu/+s...ip/+bug/382013)

Workaround:

Code:

sudo hal-disable-polling --device /dev/sr0

this allows VLC to play the audio CD's

---

