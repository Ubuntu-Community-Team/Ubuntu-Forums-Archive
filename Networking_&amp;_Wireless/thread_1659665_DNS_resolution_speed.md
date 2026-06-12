---
title: "DNS resolution speed"
date: 2011-01-04
forum: Networking &amp; Wireless
---

### Post by msknight on 2011-01-04
Hi Folks,

Ubuntu 10.04 64 bit.

DNS lookups seem to be taking between 4 to 5 seconds at certain parts of the day. My ISP has asked me to clear my DNS cache so the least I can do is attempt to comply.

The usual commands...
sudo /etc/init.d/nscd restart
sudo /etc/init.d/dnsmasq restart
...aren't found so I'm concluding that I've got no DNS caching enabled on the client and that every time the machine needs a look up, it is going to the outside world to get it.

Am I correct in this?

---

### Post by PatchesTheCaveman on 2011-01-04
Hi msknight.  Happy New Year!

Your computer does not maintain a DNS cache unless you purposely download one of those packages.

If you want to increase your DNS performance, you can use the free/open-source NameBench tool from Google.  That will test the speed of hundreds of DNS servrs and report which one is fastest on your connection.

For more information and to download this tool, visit [http://code.google.com/p/namebench/](http://code.google.com/p/namebench/)

---

### Post by Boondoklife on 2011-01-04
I totally second this as ISP name servers blow! If you don't wanna run the app, then you could always just use googles:

DNS1: 8.8.8.8
DNS2: 8.8.4.4

---

### Post by PatchesTheCaveman on 2011-01-04
Yes, Google's Public DNS servers generally work very well.  For more info on those including how to set them up in almost every operating system, visit [http://code.google.com/speed/public-dns/](http://code.google.com/speed/public-dns/)

---

### Post by msknight on 2011-01-05
Many thanks folks - cool information. Much appreciated!

---

