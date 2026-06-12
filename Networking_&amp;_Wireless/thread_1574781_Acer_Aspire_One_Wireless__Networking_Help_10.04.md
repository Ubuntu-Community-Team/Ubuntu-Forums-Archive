---
title: "Acer Aspire One Wireless  Networking Help 10.04"
date: 2010-09-14
forum: Networking &amp; Wireless
---

### Post by penguinmaster on 2010-09-14
So I am having issues as the topic title suggests with the wireless on my home network.  

It's a bit of story so bear with me, but hopefully all the information helps solve the problem.

About a month ago the computers on my wireless network started having trouble with disconnecting from our wireless router.  One computer was on Win XP and the other Ubuntu 10.04. I figured since it was happening to multiple computers and was fixed for a day or so with a router reboot it was probably my 6 year old WRT54g.  

So I bought a new router, a wrt160nl.  Now with this router, the XP laptop is perfectly fine, doesn't drop the signal.  As well I dual boot the ubuntu machine and the Windows 7 OS is fine.  But once I use ubuntu it still continues to drop the signal.  To get more weird, whenever my ubuntu machine loses signal, it knocks my wii offline as well, but not the xp machine.

To confuse the situation even more, when I'm using my ubuntu machine at my workplace, it's also on wireless, but there it never drops the signal.  

Both my workplace and home are on WPA encryption, home being personal, work being an enterprise variant.

Any help with this conundrum would be greatly appreciated, as I'm running out of ideas!

Any help would be greatly appreciated.

Edited to add both routers were and running dd-wrt firmware.

---

### Post by blakep2 on 2010-09-15
How far away are the devices from the access point.

---

### Post by penguinmaster on 2010-09-15
The devices are at most 30 feet away?  The router is in the office and all three devices are in the family room.  So one wall to get through.

-Tom

---

### Post by blakep2 on 2010-09-16
Make sure ubuntu's wireless settings are setup for a dhcp router assuming that is what you use.  In other words make sure its not setup for static ip's.  But if this is the problem it should not effect any other devices.  What is the client lease time set on for the router.

---

### Post by penguinmaster on 2010-09-21
> **blakep2 said:**
> Make sure ubuntu's wireless settings are setup for a dhcp router assuming that is what you use.  In other words make sure its not setup for static ip's.  But if this is the problem it should not effect any other devices.  What is the client lease time set on for the router.

Sorry for the delay in response.  I checked, my wireless settings are for a dhcp router (which I do use).  My client lease time is 1440 minutes.

---

### Post by blakep2 on 2010-09-23
Ok what is the range of dhcp addresses.  Also  where does it start.  What is the ip address of the router. Also type ifconfig in the terminal in linux or type ipconfig in windows cmd prompt.  paste results here

---

