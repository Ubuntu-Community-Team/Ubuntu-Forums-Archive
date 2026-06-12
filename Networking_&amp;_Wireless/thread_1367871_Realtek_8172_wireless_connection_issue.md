---
title: "Realtek 8172 wireless connection issue"
date: 2009-12-30
forum: Networking &amp; Wireless
---

### Post by derekmbarnes on 2009-12-30
If you're having trouble connecting your wi-fi in Karmic, and your network controller is a Realtek 8172, chances are the driver is missing. Fortunately, a solution was found; I came across this link in a thread for Lucid and thought I'd post it here. This link contains all the downloads and instructions necessary to get your wi-fi working again:

[http://forum.novatech.co.uk/showthread.php?p=197789](http://forum.novatech.co.uk/showthread.php?p=197789)

A few tips on the instructions:

-Users with 9.10 can skip step 3; as stated at the bottom of the original post, this version comes with the needed kernel.
-Step 5: you can download from the installer disk (this page explains how: [link]("https://help.ubuntu.com/community/WifiDocs/SolvingWireless#Ndiswrapper")).
-Step 6: Tarball won't paste into usr; just put it in your Downloads folder.
-Step 10: "sudo su -" will take you out of the directory. Repeat steps 7 and 9, and only then proceed with "make; make install." Otherwise Ubuntu won't see the makefile for the driver.

Hope this helped!

---

### Post by Glyn Hughes on 2010-02-06
Thank you for that, but I'm afraid it simply didn't do anything at all.

---

### Post by attercop on 2010-02-06
I used a similar how-to to this to get my 8172 Rev10 wireless working, and it does but now it disconnects after a while and won't reconnect until reboot.

Does anyone have a solution to this?

---

### Post by attercop on 2010-02-10
There are lots of how-to guides for getting the driver installed for RTL8192 which for some reason is in 9.04 and 10.04 but not 9.10. It's also not hard to download the linux driver from Realtek, compile and install it. However for the few of us with the dropping connection issue there are very few posts covering it. I believe that on the launchpad bug thread someone suggested a solution which has worked for me. In the four Makefile files in the drivers folder simple find all lines with DENABLE_LPS in and remove them. Then recompile and reinstall and it no longer drops connection.

---

### Post by phil_hood on 2010-03-03
The module resulting from the article referenced in post #1 crashes my kernel when put under load.  Use with caution.

---

### Post by phil_hood on 2010-03-05
I strongly recommend getting the rtl8192se_linux_2.6.0014.0115.2010.tar.gz (or later) from the realtek site.  It is much more reliable than the older one referenced above.  Try [http://www.realtek.com.tw/](http://www.realtek.com.tw/) and go to downloads and follow the link under Communications Network ICs/Wireless LAN ICs/WLAN NIC/IEEE 802.11b/g/n single chip/Software.

---

### Post by c.pfarher on 2010-03-11
the solution is here:
[http://kikipblog.blogspot.com/2010/03/realtek-8172-de-toshiba-a505-s69803-en.html]("http://kikipblog.blogspot.com/2010/03/realtek-8172-de-toshiba-a505-s69803-en.html")
good luck!

---

### Post by c.pfarher on 2010-03-11
I posted a solution here:
[http://kikipblog.blogspot.com/2010/03/realtek-8172-de-toshiba-a505-s69803-en.html]("http://kikipblog.blogspot.com/2010/03/realtek-8172-de-toshiba-a505-s69803-en.html")
good luck!

---

