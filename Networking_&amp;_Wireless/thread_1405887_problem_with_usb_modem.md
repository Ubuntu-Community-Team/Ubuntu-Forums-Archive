---
title: "problem with usb modem"
date: 2010-02-13
forum: Networking &amp; Wireless
---

### Post by kareempharmacist on 2010-02-13
I have a usb modem : huawei e220
I am using ubuntu 9.10 . I can't access the internet using it . I made a connection form the mobile broadband tab but every time it disconnects .
Ubuntu identifies the modem but every time i try to make a connection it fails...please help me

---

### Post by pradeepthundiyil on 2010-02-13
> **kareempharmacist said:**
> I have a usb modem : huawei e220
I am using ubuntu 9.10 . I can't access the internet using it . I made a connection form the mobile broadband tab but every time it disconnects .
Ubuntu identifies the modem but every time i try to make a connection it fails...please help me



hello,

Do this to connect to internet.

Download Gnome-ppp, (search in google)
Boot in Ubuntu, install it.
Open it, click settings, click detect modem.
Give username and password..

And you will be connected.. I had the same problem.. Good luck..

---

### Post by kareempharmacist on 2010-02-14
it didn't work . the program asked for the the phone number...I live in egypt ,I use vodafone network so it may be *99#. I  tried it but it didn't work . I am desperate!!!!!!!!!
I love Linux But...............!!!!!!!!!!!!!!!!!!

---

### Post by Plumtreed on 2010-02-15
Have you had it working in Windows?

Can you describe what happens when you try to connect in Ubuntu 9.10?

---

### Post by GeorgeVita on 2010-02-15
Hi to all above!

Using 9.10 & E220 you must check also:

1. possible firmware update as at:
[http://ubuntuforums.org/showpost.php?p=8499795&postcount=9](http://ubuntuforums.org/showpost.php?p=8499795&postcount=9)

2. kernel update of Ubuntu 9.10 (using wifi or ethernet) due to bug# [446146]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146")

3. proper APN and DNS settings: right click network manager icon, edit connections, mobile broadband, click on your provider, check APN/user/pass (ASK your provider), click IPv4 settings tab and check DNS (usually 'automatic ppp' is OK)

Regards,
George

---

### Post by kareempharmacist on 2011-02-25
I downloaded vodafone-mobile-connect package from [https://forge.betavine.net/frs/?group_id=12](https://forge.betavine.net/frs/?group_id=12)
and installed it and it worked
By the I installed also usbmodeswitch package for my another usb modem but i don't know wether it is needed or not but it helped for my heuwai e153 on karmic 
thanks for everyone who helped me
now my problem is with my barcode printer .......there is no hope for it to work.....
but this is a good start:P:P

---

