---
title: "3G 60KB Download Limit - Please Help"
date: 2010-07-15
forum: Networking &amp; Wireless
---

### Post by Turkuaz on 2010-07-15
I am new to Linux and have recently dropped Windows 7 (and windows all together for that matter) for Ubuntu 10.04.
  
I love the look and feel of Linux and enjoy using it more over Windows.  Despite this I am experiencing a serious problem which may cause me to revert back to Windows 7.

I have a USB 3G modem: ZTE MF622 on the KKTCELL network.
I have got this modem to work with wvdial and Gnome PPP, however i cannot get speeds over 60kb, Windows gives me well over 200kb.  

I have tried a number of things but nothing has worked, it seems that no-one has posted a solution to this annoying conundrum.
Does anybody have any advice?  Any feedback is much appreciated.

---

### Post by TechnikAlsace on 2010-07-15
It seems that you get only a EDGE connection instead of 3G...

Why don't you use the network-manager applet in the gnome-panel? This allows you to configure your 3G+ connexion in a graphical interface. With this and my Icon 515m I get a UMTS download rate of >5.8Mb/s (Orange France)

If this will not give satisfying results for you, you should make sure that you have the latest kernel module drivers for your USB modem. I also had difficulties in connecting first, but with the updated driver modules from HSO there is no more worry.

---

### Post by viralmeme on 2010-07-15
> **Turkuaz said:**
> i cannot get speeds over 60kb, Windows gives me well over 200kb

Fortunately that's been reported in bugs.launchpad.net .. [3G download speed is very slow]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/525049")

---

### Post by Turkuaz on 2010-07-15
> You should make sure that you have the latest kernel module drivers for your USB modem

I am new to Linux, how would I do that, is there a guide or something?

---

### Post by Turkuaz on 2010-07-25
This is why many new users from Windows to Linux leave the Linux scene, because things just do not work out the why they are supposed to.

---

### Post by Turkuaz on 2010-09-09
Please guys, is there anyone who can tell me how i can reach my 3G's modem maximum download speed.  I have rinsed Google and cannot get a fix.

Someone please help!

---

### Post by Turkuaz on 2010-09-12
bump

---

### Post by kammmo on 2010-12-23
try to check your proxy server settings..:smile: >>System>Preferences>Network Proxy :smile: if your connection use proxy you must set it

---

