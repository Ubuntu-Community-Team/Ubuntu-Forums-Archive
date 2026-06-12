---
title: "Mobile Internet Timeouts"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by neamtua on 2009-04-30
Hello,

I've been having a rather annoying problem with my mobile internet 3g modem. It's an Option Icon 225 and the internet is provided by Orange. Ubuntu recognized the modem just fine and it connects to the internet.

The problem is that sometimes when I browse the internet some images don't load or load incompletely. Sometimes some pages fail to load at all giving me a Content Encoding error.
I have specified in the Firefox settings that I do not want to use a proxy but I still see while loading websites, an ip address in the form of 1.1.1.x which I reckon is from the usb device since I've seen this on windows too. ( on windows it works just fine )

The problem is not only limited to firefox or other browsers. I get timeouts and errors when using aptitude in the console.

EDIT: I forgot to mention that pinging any website does not show packet loss.

Here is the ifconfig for the connection:

```
hso0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.80.0.170  P-t-P:10.80.0.170  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1486  Metric:1
          RX packets:5803 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5696 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:10 
          RX bytes:4765018 (4.7 MB)  TX bytes:919987 (919.9 KB)
```Any suggestions?

---

### Post by conorturton on 2009-04-30
Welcome to the wonderful world of mobile broadband. 3UK is the same for me as well whether on Windows or Linux. I changed the DNS server addresses to those for OpenDNS and it solved a lot of the problems.

---

