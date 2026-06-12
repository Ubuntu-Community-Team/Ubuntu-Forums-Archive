---
title: "Internet YAY - but no network"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by zootoxin on 2009-05-21
Hello all,

I am a brand new ubuntu user and I have been working through all the tons of information and guides on this site.

I am really enjoying my ubuntu experience.

Sorry if this is a re-post but I didnt know how to phrase the search.

So here is my problem 

I bought this wireless adapter from amazon [http://www.amazon.co.uk/Lm-Technologies-802-11g-Wireless-Network/dp/B000CC3ZFS/ref=sr_1_1?ie=UTF8&s=electronics&qid=1242940697&sr=8-1](http://www.amazon.co.uk/Lm-Technologies-802-11g-Wireless-Network/dp/B000CC3ZFS/ref=sr_1_1?ie=UTF8&s=electronics&qid=1242940697&sr=8-1)

and it work an absolute treat plugged in configured wireless options and I am on the internet no problem.

BUT................ 

I can't access my network. I have a PC on Win7 A laptop on Xp when I have my ubuntu pc attached via rj45 cable I access internet and network fine.
With the wireless dongle I can access Internet but not the network files, external NetHD or Printer...

Please can someone explain where I am going wrong. 

I am using 8.04

Thanks and Hello 

Zoot :)

---

### Post by Iowan on 2009-05-21
I suspect you're gonna need [Samba]("https://help.ubuntu.com/community/SettingUpSamba") to work between Ubuntu and Windows.

---

### Post by superprash2003 on 2009-05-22
post output of ifconfig from the terminal , there could be a firewall blocking.. or you could try bringing down the wired interface when connected via wireless

---

