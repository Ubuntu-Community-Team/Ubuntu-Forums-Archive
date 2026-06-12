---
title: "[SOLVED] Wired network problem"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by earthwarrior on 2008-12-06
I have a Linksys BEFSR41 router connected to my computer with a cat5e ethernet cable. But the port indicator light on the router doesn't light up and ubuntu says no network device is available. I am running 8.10 on a dell desktop and the cable is connected to the built in ehternet port.

---

### Post by mhh91 on 2008-12-06
maybe there's something with the wiring,specially that the light in the router isn't on

---

### Post by earthwarrior on 2008-12-06
> **mhh91 said:**
> maybe there's something with the wiring,specially that the light in the router isn't on
 
The cable is plugged in to both the router and computer and I tested ithe cable with another computer.  I think the problem could be that ubuntu is somehow not detedticing the ethernet port it says unable to detect any network device.

---

### Post by theozzlives on 2008-12-06
> **earthwarrior said:**
> The cable is plugged in to both the router and computer and I tested ithe cable with another computer.  I think the problem could be that ubuntu is somehow not detedticing the ethernet port it says unable to detect any network device.

Do you have a cable tester? I think it's a bad cable.

---

### Post by earthwarrior on 2008-12-06
> **theozzlives said:**
> Do you have a cable tester? I think it's a bad cable.
 
I tested the cable with another computer and it workedfine , its a new cat5e etherenet cable.

---

### Post by theozzlives on 2008-12-06
> **earthwarrior said:**
> I tested the cable with another computer and it workedfine , its a new cat5e etherenet cable.


Then a bad NIC

---

### Post by iwc5893 on 2008-12-06
Or a bad port on the router....provided that the ethernet interface on the computer is actually enabled.

---

### Post by nolewatcher on 2008-12-06
Might be none of those things.....might be the driver for your NIC. I have had problems ever since I went to UBUNTU 8.10, it installs the wrong driver for my RTL8101 NIC. I have been going in circles trying to get it configured where it will even see the 'network device'.

---

### Post by adaptr on 2008-12-06
> **nolewatcher said:**
> Might be none of those things.....might be the driver for your NIC. 
Nope.
A functioning NIC will always light at least one LED when a functioning cable is connected to another functioning device.
OS or driver have nothing to do with this, it is hardware.
So if the LED is not lit, that means it's definitely a hardware issue.

---

### Post by earthwarrior on 2008-12-06
So its probably a hardware issue and I still have warranty but I would have to reinstall XP to get warranty service.  Is there a howto on installing windows without wiping out ubuntu?

---

### Post by 1OldDog2 on 2008-12-07
> **earthwarrior said:**
> I have a Linksys BEFSR41 router connected to my computer with a cat5e ethernet cable. But the port indicator light on the router doesn't light up and ubuntu says no network device is available. I am running 8.10 on a dell desktop and the cable is connected to the built in ehternet port.
I think you will find the default ip address is the same on the network card and the linksys befsr41. In windows you have to change the address of the router to 192.168.2.1 instead of the default 192.168.1.1. to get the system to work with this cabel/dsl router. Then the ip address of the computer has to be released and renewed. Linksys has a q&a on this procedure for windows I was looking here to see if anyone had done it for Linux. Reboot after you change it and everything should work fine. I have this same box and I was looking here to find the procedure for doing just this when I stumbled over your post.

---

### Post by earthwarrior on 2008-12-09
the problem was that the integrated NIC was disabled in the BIOS setup.

---

