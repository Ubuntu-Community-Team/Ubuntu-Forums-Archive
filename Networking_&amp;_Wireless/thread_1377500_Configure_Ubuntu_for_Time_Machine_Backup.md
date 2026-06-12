---
title: "Configure Ubuntu for Time Machine Backup"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by rodreegez on 2010-01-10
Hello. 

I have a machine running Karmic sat in the corner of my office. I scp stuff from my mac to it quite a lot over my local wireless network.  At the moment, it holds a .sparsebundle backup of my mac created by SuperDuper! (mac backup application) that I periodically transfer over. I'd like to make this system a  little more sophisticated and use Apple's Time Machine to automatically backup to my Ubuntu box if possible.

Anyone have any experience of this? I'm kinda hoping for something a bit more straight forward than this: [http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/)

Any pointers gratefully received. 

Cheers, 

Ad.

---

### Post by rodreegez on 2010-01-13
so, I ended up creating a new user on my ubuntu machine, granted the almighty power of sudo and following this guide: [http://www.pronetworks.org/forums/configuring-ubuntu-to-store-time-machine-backups-t109371.html](http://www.pronetworks.org/forums/configuring-ubuntu-to-store-time-machine-backups-t109371.html)

(admittedly not the simple solution I was looking for)

I think everything worked. No errors were reported at any point. However my machine is not showing up on my Mac. I'm wondering if this is because my Ubuntu machine is connected to my router via ethernet, and my mac is connected to my router via wifi?

TimeMachine is looking for a wifi drive, which obviously the Ubuntu machine is not. I wonder if this is happening because the drive is not visible in the Finder?

Any hints?

---

