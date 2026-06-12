---
title: "connecting to internet problems"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by Bad Wolf on 2009-10-31
Hi, again, I'm back. So far I've successfully installed 9.04 on a new pc with a new hdd. The only problem seems to be that I cant connect to the internet. Its like my pc doesnt see my cable modem. Old pc sees it fine. Checked bios - networking is enabled. Do I need extra drivers? Any help would be appreciated, btw its a dell optiplex circa 2003, p4 ht processor clocked at 300, 512 ram (have more, up to a gig), NOTHING ON THE HDD BUT UBUNTU 9.04. If you can think of any useful links, please post them. Thanks in advance.

---

### Post by gordintoronto on 2009-10-31
It's all about your Ethernet device.  If you click on Accessories/Terminal, then type lspci, it should display information about your ethernet device.

---

### Post by Bad Wolf on 2009-10-31
It says:

ethernet controller: intel 82540 EM (rev 02)

---

### Post by faical117 on 2009-10-31
your modem port is USB OR ETHERNET ?

---

### Post by faical117 on 2009-10-31
See this [http://ubuntuforums.org/showthread.php?t=1308311](http://ubuntuforums.org/showthread.php?t=1308311)  :KS

---

### Post by Iowan on 2009-10-31
Just in case it's not the PPPOE crisis, check **ifconfig -a** to see if the machine gets an IP address.

---

