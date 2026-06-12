---
title: "Why is my wireless so slow?"
date: 2005-12-27
forum: Networking &amp; Wireless
---

### Post by axcairns on 2005-12-27
Hey all,

I have been running Breezy since it came out on my Sony Vaio PCG-FX301 with a Cisco Aironet 350 802.11b wireless card connecting to a Aironet 340 base station. I had some fun getting the card to work (for some reason it created two wireless connections) and connecting on startup but got those sorted. 

I thought the network was a bit slow but I didn't realise just how slow until my wife got a new laptop with built-in 802.11g running Win XP Home. As the two machines use the same 802.11b base station they should (in theory) run roughly the same speed connection. This is not the case.

To verify my impressions I tried ftp'ing a file from my home server. The results are below.

Ubuntu/Vaio/Aironet 350 - 

```
ftp> get Joanne.rar
local: Joanne.rar remote: Joanne.rar
200 PORT command successful
150 Opening BINARY mode data connection for Joanne.rar (154024 bytes)
226 Transfer complete.
154024 bytes received in 34.85 secs (4.3 kB/s)
```

Win XP/Travelmate/Built-in 802.11g - 
```
ftp> get Joanne.rar
200 PORT command successful
150 Opening ASCII mode data connection for Joanne.rar (154024 bytes)
226 Transfer complete.
ftp:154024 bytes received in 0.63Seconds 247.37Kbytes/sec.
```

Ouch! Any ideas?

Thanks,

Allan

---

### Post by axcairns on 2005-12-29
*bump*

Anyone? I really like Ubuntu (I've handed out about 40 cd sets so far) but this network issue is making it almost unusable.

Thanks,

Allan

---

### Post by shin on 2005-12-29
Type dmesg and check if there are any errors according to your wireless. Also - turn off ipv6 (/etc/modprobe.d/aliases -> 'alias net-pf-10 ipv6' to 'alias net-pf-10 off').

Check iwconfig if there is a power managment turned off.

If it won't provide anything useful - consider upgrading drivers etc.

Here is a little help:
[http://modzer0.cs.uaf.edu/~wanderlust/wireless.htm](http://modzer0.cs.uaf.edu/~wanderlust/wireless.htm)
but be careful as this is a howto for debian and for kernel 2.4

---

### Post by axcairns on 2006-01-28
Sorry for the delay in responding - been away on holidays.

I ended up installing Dapper alpha 3. After a bit of confusion over whether to use wifi0 or eth1 (eth0 is wired), dapper now zips along.

Thanks for your help,

Allan

---

