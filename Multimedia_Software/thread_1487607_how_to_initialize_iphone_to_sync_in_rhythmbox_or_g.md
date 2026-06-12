---
title: "how to initialize iphone to sync in rhythmbox or gtkpod?"
date: 2010-05-19
forum: Multimedia Software
---

### Post by lucey24 on 2010-05-19
ive spent days figuring out how to sync my iphone 3gs firmware 3.1.3 in ubuntu 10.04. my laptop can detect my iphone, i can actually browse its folder. (i can see photos and music from my phone, i tried to paste some photos in a certain folder and went well, just in ONE folder). 

i tried almost all instructions i can find on net, but nothing is working well. i even freshly installed my ubuntu, thinking that i did something wrong in my first attempt. still cant sync music and photos.

i transferred songs already to my phone using itunes in windows (on another laptop). they said that doing this can initialize my iphone, but it didnt work.

what do i do? please help! thanks!

---

### Post by lucey24 on 2010-05-19
or do i really need to initialize it? my main problem is that rhythmbox or gtkpod can not detect my phone.

---

### Post by dumblebee100 on 2010-05-19
check this site [http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux/]("http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux/")

---

### Post by rdunnion on 2010-07-01
I was having trouble syncing my iPhone 3g running 4.0 software on lucid w/ rhythymbox. I saw the diagram in the above link and started at the top I installed libgpod-dev and everything is working hunkey dorey.
Here was my error message:
Error transferring track Error while getting peer-to-peer dbus connection: The name :1.80 was not provided by any .service files

---

### Post by MR NIX on 2010-07-02
dude this is the same problem i have and have found no answer!!!

Quote:
 Here was my error message:
Error transferring track Error while getting peer-to-peer dbus  connection: The name :1.80 was not provided by any .service files

---

### Post by keith.burgoyne on 2010-07-14
I have precisely the same issue, and haven't been able to find an answer!

---

### Post by gregtheCdn on 2010-07-15
Same here...getting error:

Error while getting peer-to-peer dbus connection:

My Iphone 3GS has been working fine **until today** using Ubuntu 10.04 and Rythmbox :-(

GtC

---

### Post by gregtheCdn on 2010-07-15
> **gregtheCdn said:**
> Same here...getting error:

Error while getting peer-to-peer dbus connection:

My Iphone 3GS has been working fine **until today** using Ubuntu 10.04 and Rythmbox :-(

GtC

Forget it...restart of Rythmbox seems to be the fix - D'oh!

GtC

---

### Post by keith.burgoyne on 2010-07-15
I restarted Rhythmbox and it seemed to work for a while. I tried synching over about 350 songs and, after it had worked for maybe 100, Rhythmbox froze and seemed to freeze X entirely. I was able to ssh into my computer and restart X, so at least it hadn't killed my entire computer.

Any thoughts on what could cause this?

---

### Post by charding on 2010-09-29
I can't see my iphone4 listed in the left column of rhythmbox, but I just happened to open the 'Open Folder' and my iphone was listed in the quick links of my file browser. Wierd. 

I selected the iphone and then it asked me to initialize it, which I did. It still doesn't list itself in the column where my ipod 3g does...

---

### Post by mr_luksom on 2010-10-27
Try syncing with gtkpod instead:

[http://ubuntuforums.org/showthread.php?t=1567271](http://ubuntuforums.org/showthread.php?t=1567271)

It is the only way I can sync my iOS 4.1 iPhone.

---

### Post by Solaar on 2011-10-01
Quote:
 Here was my error message:
Error transferring track Error while getting peer-to-peer dbus   connection: The name :1.80 was not provided by any .service files

I got this message too when trying to drag and drop tracks to the device in rhythmbox.. Turns out my jailbroken iPhone 3GS (4.3.3) had gone into ITsafeMode when it was connected to my laptop (located on top of the screen of the phone, between signal and battery) From what i read this i a crash caused by Cydia. Fixed this by tapping the ITsafeMode message, restarting the phone and now its all fresh!
Still no autosync tho but atleast u get music to your iPhone ;)

---

