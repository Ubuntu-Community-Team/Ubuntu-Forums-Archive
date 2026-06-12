---
title: "Dell Inspiron 6000 Wireless card detected but not working"
date: 2006-07-09
forum: Networking &amp; Wireless
---

### Post by sunilsattiraju on 2006-07-09
Guys,
Please guide me, i installed Dapper 6.06.. everything is perfect expect with wireless.. it dosent active here is what it says

dmesg 

 bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.


iwconfig 

eth1      IEEE 802.11b/g  ESSID:"tryme"  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lspci

0000:03:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)

--------------------------------------------------------------

is it as simple as getting the fw installed into /lib/firmware/2.6.15-23-386/ ?????????????? or do i have to do anything else...

Please give me detailed instruction on how to do it..i am fairly new to linux..any help greatly appreciated...

if you guys want any other logs..i can post..

---

### Post by tonyr on 2006-07-09
This can apparently be solved using **ndiswrapper**.  There are several
threads about it.  Here is one:
[http://www.ubuntuforums.org/showthread.php?t=201902](http://www.ubuntuforums.org/showthread.php?t=201902)

You can find more with the search keys **broadcom** and **4306**
in the Search window at the top of this page.

EDIT:  There is a wiki page about **ndiswrapper** at
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by sunilsattiraju on 2006-07-09
i did exactly as said in [http://www.ubuntuforums.org/showthread.php?t=201902](http://www.ubuntuforums.org/showthread.php?t=201902)
now i cant see my wireless card in the network manager..

Please help...

---

### Post by sunilsattiraju on 2006-07-09
Guys,
Thanks to everyone in the forum..
My wireless card is now working and what i did is just removed all the previous ndiswrapper suggested on and re- installed ndiswrapper,rebooted and it worked...
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu)
and it's working like charm.....

---

