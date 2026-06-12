---
title: "Radeon X1600"
date: 2006-08-21
forum: Multimedia &amp; Video
---

### Post by nazgulord on 2006-08-21
Hey guys,

I recently installed Dapper on my new Acer TravelMate 8200 (Mobility Radeon X1600 for graphics). It booted up fine the first time, and told me there were updates available, which I installed. It then told me a system restart was required, and when I rebooted, X refused to start up, claiming that no screens were found. I tried changing vesa to ati in xorg.conf, and then installed xorg-driver-fglrx and changed it to fglrx, but I'm still getting the "No screens found" error, even though fglrx supposedly supports the card.

Any help would be welcome.

Thanks,

nazgulord.

---

### Post by Eversmann on 2006-08-21
Maybe current shipped driver for radeon doesn't support x1600 very well. Ati have to make much better drivers for linux.

Try this: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide) and download latests one (8.28.8) and install it by hand. 

hope helps.

---

### Post by ischg on 2006-08-21
nazgulord, just to give you a heads up: I installed dapper on my brand-new notebook (ATI radeon mobility x1400).
Everything worked initially (i.e. I installed yesterday and had it working for a day), but today I updated the xserver and ended up sitting here with the same error:
(EE) No devices detected
I tried dpkg-reconfigure xserver-xorg, but to no avail ](*,) . The only difference between the working configuration and the broken configuration is the xserver update. Frustrating ...

---

### Post by JYoda on 2006-08-21
The same thing happened to me on a Radeon X800! Couldn't fix it so I re-installed Ubuntu. Let's see how long I can go before accidentally re-applying the broken update.

Any help here would be appreciated.

---

### Post by ischg on 2006-08-22
good news. The xserver-xorg-core update broke our xorg.conf's: [see here]("http://www.ubuntuforums.org/showthread.php?p=1407304#post1407304")

---

### Post by nazgulord on 2006-08-22
Thanks guys! I'll try that tomorrow (it's pretty late here).

nazgulord.

---

