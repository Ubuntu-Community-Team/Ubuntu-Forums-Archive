---
title: "Help finding windows drivers"
date: 2010-05-11
forum: Networking &amp; Wireless
---

### Post by Aidan09 on 2010-05-11
I'm really rather stuck here, and need some help. I installed Ubuntu 10.04 yesterday, but my wireless card (BCM4312) is not recognised by the system. I've spent the best part of 36 hours trying to find the appropriate Windows drivers and relevant .inf file but couldn't, so if anyone has a working link to the drivers I need, it would be much appreciated. Already have ndisgtk ready, all I need is the driver.

thanks

---

### Post by ronnielsen1 on 2010-05-11
Try this first
> sudo apt-get install bcmwl-kernel-source

[http://ubuntuforums.org/showthread.php?t=1480056](http://ubuntuforums.org/showthread.php?t=1480056)

>  I've spent the best part of 36 hours trying to find the appropriate Windows drivers and relevant .inf file but couldn't,

Are you using Bing?

[http://www.bioticaindia.com/bcm4312.html](http://www.bioticaindia.com/bcm4312.html)
[http://www.filestube.com/b/bcm4312+xp+driver](http://www.filestube.com/b/bcm4312+xp+driver)

---

### Post by Aidan09 on 2010-05-11
No, I was using Google. That Terminal command didn't work, I have no access to the internet on my Ubuntu system at all.

---

### Post by chili555 on 2010-05-11
I believe it's on the install CD. Please do:```
sudo apt-cdrom add
```You will be prompted to drop the CD in the tray. Now do:```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source 
```

---

### Post by Aidan09 on 2010-05-11
Ended up just getting this; 

[FONT=monospace]E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Aaahhh, this is so frustrating ):
[/FONT]

---

### Post by ronnielsen1 on 2010-05-11
> [FONT=monospace]E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/FONT]

Close synaptic before using this command

---

