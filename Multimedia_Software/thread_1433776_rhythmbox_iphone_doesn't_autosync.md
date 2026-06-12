---
title: "rhythmbox iphone doesn't autosync"
date: 2010-03-19
forum: Multimedia Software
---

### Post by serlex on 2010-03-19
Hi,

I've rhythmbox and iphone 3gs running on ubuntu 9.10.

I can get rhythmbox to recognize my iphone and transfer music to it. However when I disconnect my iphone, nothing shows up in 'ipod' app. 

If I mount the iphone back, I can see the music files are transferred, but iphone interface doesn't show it. I've tried to restart iphone...

Any ideas?

---

### Post by vipseixas on 2010-03-29
Same thing here, but with Lucid beta. It seems that rhythmbox does not updates the iPod library, just transfer the files, which is useless.

> **serlex said:**
> Hi,

I've rhythmbox and iphone 3gs running on ubuntu 9.10.

I can get rhythmbox to recognize my iphone and transfer music to it. However when I disconnect my iphone, nothing shows up in 'ipod' app. 

If I mount the iphone back, I can see the music files are transferred, but iphone interface doesn't show it. I've tried to restart iphone...

Any ideas?

---

### Post by vipseixas on 2010-03-29
I resolved the issue following steps 3/5/6/7 of this page:

[http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux-part-2/](http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux-part-2/)

In a few lines:
1 - I installed ifuse and gtkpod (sudo apt-get install ...)
2 - Mounted iphone using ifuse (mkdir iphone; ifuse ./iphone/)
3 - Created the "Device" dir (mkdir iphone/iTunes_Control/Device)
4 - Found out iPhone serial (lsusb -v | grep -i iSerial)
5 - Ran the command ipod-read-sysinfo-extended xxxxx iphone/ (xxxxx is the big serial number found at step 4)
6 - I ran gtkpod, it asked for iPhone model 
7 - I added some music and clicked save - now iphone syncs!
8 - Umounted the iPhone (sudo umount iphone) 

After that I can sync through rhythmbox normally. Rhythmbox does not have a save ou sync button like gtkpod, so if you add a lot of songs it will sync a lot of times, not just once, it sucks a little. 

Since I am running Lucid you might not have all the packages I have installed, but it might not be hard to figure out...

---

### Post by FunkyM on 2010-04-01
> **serlex said:**
> Hi,
I can get rhythmbox to recognize my iphone and transfer music to it. However when I disconnect my iphone, nothing shows up in 'ipod' app.

Your issue is related to one a lot of people seem to have.

You have to wait for Rhythmbox to actually sync the music database onto your device!

This happens by showing the "Sync in Progress..." screen on your device. If you unplug the device before that step, nothing will change on your device.

Since Rhythmbox appears to do that sync step rather "sporadically" people do not understand they must wait for it.

This is being worked on for future releases to directly sync after all tracks are copied like iTunes does.

---

### Post by yipidee on 2011-01-22
> **vipseixas said:**
> I resolved the issue following steps 3/5/6/7 of this page:

[http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux-part-2/](http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux-part-2/)

In a few lines:
1 - I installed ifuse and gtkpod (sudo apt-get install ...)
2 - Mounted iphone using ifuse (mkdir iphone; ifuse ./iphone/)
3 - Created the "Device" dir (mkdir iphone/iTunes_Control/Device)
4 - Found out iPhone serial (lsusb -v | grep -i iSerial)
5 - Ran the command ipod-read-sysinfo-extended xxxxx iphone/ (xxxxx is the big serial number found at step 4)
6 - I ran gtkpod, it asked for iPhone model 
7 - I added some music and clicked save - now iphone syncs!
8 - Umounted the iPhone (sudo umount iphone) 

After that I can sync through rhythmbox normally. Rhythmbox does not have a save ou sync button like gtkpod, so if you add a lot of songs it will sync a lot of times, not just once, it sucks a little. 

Since I am running Lucid you might not have all the packages I have installed, but it might not be hard to figure out...

Thanks very much man, this fixed my problems!

Upgraded to os4.2 through iTunes in VirtualBox, was able to restore all contacts, apps, mail etc using iTunes then reloaded my music with Rhythmbox. Definitely reccommend keeping a playlist of the tracks on your iPhone...

---

