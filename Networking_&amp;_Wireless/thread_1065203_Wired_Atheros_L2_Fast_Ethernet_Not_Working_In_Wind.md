---
title: "Wired Atheros L2 Fast Ethernet Not Working In Windows XP Dual Boot With Ubuntu"
date: 2009-02-09
forum: Networking &amp; Wireless
---

### Post by SVN7 on 2009-02-09
Hi,

Firstly I am new to Ubuntu and have try to recently install the current version 8.10 to an Asus X50R laptop. I have two of these and am trying to set them both up with the same configuration, Dual Boot Ubuntu 8.10 & Windows XP Professional. I have suceeded in installing both operating systems and both work well. However, I seem to have an issue with both machines. The wired LAN card seems to be working fine when using in Ubuntu, but when in Windows it reports the Network cable as unplugged. I have the same issue on both machines and have tried serveral network cables and ports on the switch to resolve the problem. The network cards worked for a while during the install process and reinstalling the drivers doesn't seem t help. Any suggestions would be great, thank you.

---

### Post by Tyllar on 2009-02-12
I work on an Asus F5R, in a Windows domain network, everything was OK, until I installed an Ubuntu. Now, in Ubuntu, there is no problem with LAN, but in XP, it says the same "Network cable is unplugged".
Because I work with AutoCAD, I need my XP, and also have to access the domain. 
Wireless access is not a long term option.

---

### Post by Tyllar on 2009-02-12
After two hours intense googleing, finally I found the solution.

First, I edited the GRUB's list that it will load XP after countdown, to avoid accidentally boot to Ubuntu. ('Cause after a first try I forgot that damn bootloader, so it booted to Linux)

Then booted to XP, restored my fix IP, WINS, etc. settings, then shuted down the notebook.

Unplugged the network cable, the DC cable, then the accumulator!
Waited some time, then plugged first the network cable, then accu, and finally the DC. 

And voila! everything OK.

So I will not boot to Ubuntu, just when somebody put a gun to my head!  

Anyway, some idea what caused this problem?

---

### Post by dinoc on 2009-03-01
Guys , I'm having the same issue here ! With Atheros L2 network card ( on board network adapter, Asus motherbord) , the wired network works fine under Ubuntu , but it doesn't work anymore in Windows XP, where it tells me that "Network cable is unplugged" .
I've reinstalled the drives in XP for this card but no success ... 

Any ideea what could be wrong ????

---

### Post by CptMatty on 2009-03-11
Hi, i had same problem as you but with dual boot ubuntu-vista. I fixed it installing atheros driver-	Atheros L2 Driver V2.5.7.9 ([http://support.asus.com/download/download_item.aspx?model=P5GC-MX/1333&product=1&type=drivers&SLanguage=en-us]("http://support.asus.com/download/download_item.aspx?model=P5GC-MX/1333&product=1&type=drivers&SLanguage=en-us")), hope it will help;)

---

### Post by CptMatty on 2009-03-11
I have ASUS F5R

---

