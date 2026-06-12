---
title: "Updates are messing up my wireless."
date: 2009-03-20
forum: Networking &amp; Wireless
---

### Post by bapy on 2009-03-20
Hey, actually got my wireless working. But i got all the updates for my system and after that it stopped working, so i ended up taking ubuntu off and then re-installing it and then used the solution i found again to get my wireless working. So Now its working but i wonder if i should update my system or not. Also i think its just certain updates that might have messed up my wireless. The ubuntu version i'm using is 8.10 and its 64bit.

The laptop and the wireless chipset i'm using are : VGN-NR220E and the wireless card its using is a Atheros AR242x 802.11

The site where i got my wireless solution from was : [http://www.ubuntu-inside.me/2009/02/how-to-get-your-atheros-ar242x-working_25.html]("http://www.ubuntu-inside.me/2009/02/how-to-get-your-atheros-ar242x-working_25.html")

So if anyone can tell me exactly which updates are the ones that messed up my wireless that would be great. also i was wondering if it is possible to pin point which updates are causing the problems then will i be able to just get the updates that wont mess up my wireless. Thank you.

---

### Post by ugm6hr on 2009-03-20
That How-to recommends manually compiling the ath5k driver.

Hence, every kernel update (generally named linux-image-2.6.xx-x) will remove the driver.

You can just repeat steps 5 & 6 to reinstall.

PS:  I would like to say that I am personally recommending using the pre-compiled ath5 driver, which does not need any manual re-compilation with updates.

If you are interested, see this (although the "fix" you have already applied may interefere with this):
[http://ubuntuforums.org/showthread.php?p=6895635#post6895635](http://ubuntuforums.org/showthread.php?p=6895635#post6895635)

---

