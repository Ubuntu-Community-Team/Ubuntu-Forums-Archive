---
title: "Problem with Broadcom BCM4311 in 10.04"
date: 2010-06-07
forum: Networking &amp; Wireless
---

### Post by notthisyear on 2010-06-07
Hi!

I can't connect to my wireless network. I have no problems with discovering it, but when I input the password, it just tries to connect for a minute, then asks me again. This procedure is repeated until I give in and use the wired network instead. 

I've installed the proprietary driver provided by System -> Administration -> Hardware Drivers (Broadcom STA wireless driver), tried installing the bcmwl-kernel-source manually (through apt-get install bcmwl-kernel-source) and too tried the b43-fwcutter. 

When I run the "sudo ifconfig wlan0 up"-command, it says that there is no such device.

Yes, in the world of Linux, I'm a noob.
Please help me.

/notthisyear

---

### Post by IBUA on 2010-06-07
Hey i've been having exactly the same problem (just fixed it now)

On the GRUB menu, try selecting the linux.generic.[...].21 instead of .22 and see if that helps.

---

### Post by notthisyear on 2010-06-08
Thanks for the reply, but it didn't work. When in .21, I had to reinstall all the drivers, but still no luck. 

Gah, how do get this stupid wireless working? :mad: 

/notthisyear

---

### Post by IBUA on 2010-06-08
> **notthisyear said:**
> Thanks for the reply, but it didn't work. When in .21, I had to reinstall all the drivers, but still no luck. 

Gah, how do get this stupid wireless working? :mad: 

/notthisyear

Yeah, it died for me too :(

For some reason, on .22 I remove the b43-fwcutter, and add the STA, the STA doesn't work and the b43-fwcutter disappears.

If I go to .21, both appear, the b43-fwcutter works for about a minute and dies.

The STA just doesn't work at all.

---

### Post by IBUA on 2010-06-08
I've just installed the 32-bit Ubuntu. Is working fine with the STA now :S

---

### Post by twent4 on 2010-11-16
> **notthisyear said:**
> Hi!

I can't connect to my wireless network. I have no problems with discovering it, but when I input the password, it just tries to connect for a minute, then asks me again. This procedure is repeated until I give in and use the wired network instead. 

I've installed the proprietary driver provided by System -> Administration -> Hardware Drivers (Broadcom STA wireless driver), tried installing the bcmwl-kernel-source manually (through apt-get install bcmwl-kernel-source) and too tried the b43-fwcutter. 

When I run the "sudo ifconfig wlan0 up"-command, it says that there is no such device.

Yes, in the world of Linux, I'm a noob.
Please help me.

/notthisyear

Hey guys, i know I'm necroing a bit but have the exact same issue with Mint 10. No luck with STA, and a bit weary of trying ndiswrapper due to possible conflicts.

---

### Post by bluewaves on 2011-01-20
> **notthisyear said:**
> Hi!

I can't connect to my wireless network. I have no problems with discovering it, but when I input the password, it just tries to connect for a minute, then asks me again. This procedure is repeated until I give in and use the wired network instead. 

I've installed the proprietary driver provided by System -> Administration -> Hardware Drivers (Broadcom STA wireless driver), tried installing the bcmwl-kernel-source manually (through apt-get install bcmwl-kernel-source) and too tried the b43-fwcutter. 

When I run the "sudo ifconfig wlan0 up"-command, it says that there is no such device.

Yes, in the world of Linux, I'm a noob.
Please help me.

/notthisyear

my first post here, so thanks for the ospitality and for anyone who will help :)

sorry for resuming this old post, but finally I found someone who has got my very same problem. 
Around the web there is plenty of people whose Broadcom Wireless Card does not work, mine works (i see it under eth01) and it can scan for wireless networks but, as notthisyear said, I simply cannot connect to any wireless network. I am running Ubuntu 10.04 and my card is Broadcom 4311 rev.01. I am using Broadcom STA driver. The message returned is "incorrect password", but it is not really a password problem; I tried to turn off authentication and still got the same problem (now the message returned was "unable to contact access point". 

If anyone out there could help fixing this.. it would be very helpful :) i have been viewing and trying tons of guides but nothing works :(

---

