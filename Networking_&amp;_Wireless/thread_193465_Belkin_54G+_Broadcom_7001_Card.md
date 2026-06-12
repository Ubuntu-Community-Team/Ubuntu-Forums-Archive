---
title: "Belkin 54G+ Broadcom 7001 Card"
date: 2006-06-10
forum: Networking &amp; Wireless
---

### Post by deja2004 on 2006-06-10
I've managed to set up a computer with this card using ndiswrapper. It took a little doing, and some help from this thread:

[http://www.ubuntuforums.org/showthread.php?t=190177&highlight=BCM4318](http://www.ubuntuforums.org/showthread.php?t=190177&highlight=BCM4318)

But I got it working. However, once I turned WEP on, my card would see the AP, but not connect to it. I spent a couple of hours before giving up for the evening. If anyone has a suggestion, I'm all ears! :confused:

---

### Post by spd106 on 2006-06-10
Does it associate with the AP? ie does **sudo iwconfig** show the AP's hardware address. 

If so you might only need to do **sudo dhclient eth0**. 

If not then double check the encryption key, making sure you select the right kind in n-m (ascii, hex etc).

---

### Post by deja2004 on 2006-06-10
Thanks for the tip. I won't have access to the machine until Monday. I'll give it a try then and let you know what happens. Thanks so much.

---

### Post by DarkElf109 on 2006-06-12
You might want to try using the Dell drivers. I've seen lots of good support from those.

[http://ftp.us.dell.com/network/R115321.EXE](http://ftp.us.dell.com/network/R115321.EXE)

Use the bcmwl5.inf and bcmwl5.sys under "driver" folder.

I found that on the Ndiswrapper wiki, so it should be good. Lemme know if it works.

---

### Post by deja2004 on 2006-06-20
In the midst of trying to get ndiswrapper to work, the new kernel (2.6.17) came out so I decided to update my system with it. My card now works like a charm (with encryption even!). Thanks for the help/suggestions!

---

