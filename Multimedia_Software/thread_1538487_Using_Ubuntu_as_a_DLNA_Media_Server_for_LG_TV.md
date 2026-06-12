---
title: "Using Ubuntu as a DLNA Media Server for LG TV"
date: 2010-07-25
forum: Multimedia Software
---

### Post by fgomesbarros on 2010-07-25
I just have bought a LG 32LD650 LCD television set to which I wanted to feed audio and video files from my computer which is running Ubuntu 10.04. This LG TV have included an Ethernet port and the ability to connect to a DLNA server for quite a long time.

I installed MediaTomb, which is a UPnP (DLNA) server, but it didn't work as it was installed. 

I also tried to do as was described in other forum thread ([http://ubuntuforums.org/showthread.php?t=1198689&highlight=dlna](http://ubuntuforums.org/showthread.php?t=1198689&highlight=dlna)), but it don't work. :(

Can someone help me?

---

### Post by BridgeLife on 2010-08-03
I'd like to know also, any Linux DLNA Server or AllShare Server That would work on Ubuntu 10.04 Lucid Lynx......

Thanks in Advance

---

### Post by jpseixas on 2010-11-17
I have a LG TV (model 32LD650), and I manage to make it work by the following way:

Run Media Tomb forcing it to use port 54444. To do so, use the option:

"mediatomb -p 54444"

I use the -d option too, just to be able to close or keep using the terminal after running Media Tomb.

---

