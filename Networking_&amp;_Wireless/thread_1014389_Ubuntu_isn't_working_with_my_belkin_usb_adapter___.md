---
title: "Ubuntu isn't working with my belkin usb adapter     help please!!!"
date: 2008-12-17
forum: Networking &amp; Wireless
---

### Post by lagginwagon on 2008-12-17
I recently installed ubuntu 8.04 and i have a belkin F5D8053 
wireless usb adapter. I have downloaded the driver and added it with ndiswrapper. It added the driver fine with no problems. There's still no wireless in the network manager though, but i think that it just doesn't recognize the actual usb device. 


Also i tried installing the Belkin Software(the thing with setup and utility and all that stuff) with wine and it will start installing but near the end of installing it will post this 

Warning- ERROR number : 0x80040707
Description- DLL function call crashed: Install Enumerate Device
Setup will new terminate.

I have been working at this for a couple of days now and it seems like i have tried everything.I am at the almost at the point of just quitting and going back to xp, so help getting this to work would be great.  I am also very new to linux, so easy to follow directions would be great also. 
Thanks

---

### Post by ieee488 on 2008-12-17
There are a couple of threads in this forum about your network adapter. Search on 'F5D8053'.

---

### Post by cdtech on 2008-12-17
Could you list your USB devices with it plugged in?:
```
lsusb
```

---

### Post by lagginwagon on 2008-12-18
Alright, here it is
travis@travis-desktop:~$ lsusb
Bus 005 Device 004: ID 050d:815c Belkin Components 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

I'm just kinda confused because it says Belkin Components, but there's no wireless option in the network manager.

---

### Post by 1993cb7 on 2008-12-18
> **1993cb7 said:**
> I installed Ndiswrapper, loaded the XP 64 driver and followed this write up

[http://blog.delgurth.com/tag/ubuntu/](http://blog.delgurth.com/tag/ubuntu/)

Some of the steps didn't work but i kept going untill i reached the end and restarted and clicked on the network i wanted to connect too, it loaded and was fast as all hell. 

It works fine but leaving it on overnight it was disconnected this morning and to get it to be recognized i had to shut down and restart. For me this won't be a problem as any overnight downloading ill do in Vista but i want to be able to login to Ubuntu and use it and to do that i need internet so im content now. 


When i find a solution to it disconnecting overnight and it not loading automatically ill post it here for those who actually need the help.

This was from the thread i made about this same problem.

---

### Post by cdtech on 2008-12-19
I've been away. here is a post with the same belkin:
[http://ubuntuforums.org/showthread.php?t=919044&page=3](http://ubuntuforums.org/showthread.php?t=919044&page=3)

---

