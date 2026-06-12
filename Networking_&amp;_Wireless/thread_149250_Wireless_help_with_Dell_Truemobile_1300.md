---
title: "Wireless help with Dell Truemobile 1300"
date: 2006-03-23
forum: Networking &amp; Wireless
---

### Post by umdzig on 2006-03-23
I had my wireless card working under ubuntu 5.04. I just reformatted my HD and installed 5.10, and followed the instruction at [How To: Configure wireless card with broadcom chipsets]("http://www.ubuntuforums.org/showthread.php?t=25683") and I cant get the wireless to work for anything. 

I have typed```
 ~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present

```

However i can not get the wlan0 to show up in networking. This tutorial mentioned above has helped me get the wireless card working in the past. I dont know why it is not working now.

Thanks for your help!

---

### Post by obiwan on 2006-03-23
what errors do you get? when you type ifconfig your wireless card appears on the list?

---

### Post by umdzig on 2006-03-23
obiwan,

when i type ifconfig i dont get any errors. It just gives the info about eth0.

---

### Post by CompShrink on 2006-03-31
I have a truemobile 1300 in a dell inspiron 5100. I couldn't get wlan0 to show up either with the official driver from dell currently on their download site, but I downloaded one of the ones from the ndiswrapper wiki;

[http://ankhcraft.com/drivers/bcmwl5.zip](http://ankhcraft.com/drivers/bcmwl5.zip)

and now it finally shows up! I'm not where the wireless is, so not sure if it will work, but at least the interface shows up now.

---

### Post by cntrlf8 on 2006-05-01
Thank you!  That driver did the trick for me!

---

