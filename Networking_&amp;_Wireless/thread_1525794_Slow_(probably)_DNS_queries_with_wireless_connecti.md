---
title: "Slow (probably) DNS queries with wireless connection"
date: 2010-07-07
forum: Networking &amp; Wireless
---

### Post by saifulwebid on 2010-07-07
I have read many threads about this, but it doesn't solve my problem. I'm sorry for my duplicate post, but I'm going crazy because of this.

All of my networking-related programs in my Ubuntu 10.04 Lucid Lynx 32-bit are running slowly with the DNS queries. Okay, (probably) DNS, because I noticed that there is about 10-15 seconds delay in resolving hostname.

For example, when I browsed [http://www.google.com/](http://www.google.com/) with my Firefox, it's displaying "Looking up www.google.com..." so long and I noticed that the progress of web loading after that phase is very fast. I have 512kbps Internet connection and this is running smoothly in my Windows 7 Home Premium.

It must not be the IPv6. I have turned off my IPv6, both in my laptop or my router. But it still have slowly DNS queries.

Few months ago I read a thread about this, following the steps and finally my DNS queries running smoothly. The problem is I just formatted my entire harddisk and now I can't remember the thread, even the title of the thread. I only remember that the problem-solver is arranging the way Ubuntu sends DNS queries (and I remembered that I delete some entries from a file).

Could you help me with this problem?

---

### Post by Brandon Williams on 2010-07-07
What does your /etc/nsswitch.conf file look like, especially the "hosts:" line? Mine simply says "files dns". If your hosts line lists any other resolution methods, then one of the extras could be the source of your problem. For example, [some people report](http://ubuntuforums.org/showthread.php?t=1496488&highlight=nsswitch.conf) having trouble with the wins method.

---

### Post by jonobr on 2010-07-07
You could just try pinging google.com in a terminal window, 
that should show how quick dns responds with the ip address,

I would also, try different urls to avoid cache showing a faster response.

Also, putting the IP address in the browser instead of the dns name might show if this is definately (or not ) dns realted.
You could also trying using a public DNS server to rule out issue ywith your ISPs DNS

---

### Post by saifulwebid on 2010-07-08
Okay. After finding in several sources, I did this steps already:

First, I remove the **libnss-mdns** package with running this on terminal:
```
sudo apt-get remove libnss-mdns
```
Then editing **/etc/nsswitch.conf** with gedit with running this on terminal:
```
sudo gedit /etc/nsswitch.conf
```
and make sure the **hosts** line is containing this:
```
hosts: files dns
```

Then I reboot the machine and the problem is didn't solved.

---

Second, after rebooting the machine I opened **/etc/sysctl.conf** file and adding this into the end of the file:
```
#disable IPv6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.default.all.disable_ipv6 = 1
net.ipv6.lo.all.disable_ipv6 = 1
```

Then I reboot the machine, and browsing with Firefox is still slow. However, I didn't check other programs.

---

Third, finally I tried to change IPv6 setting in Firefox by opening **about:config** and set **network.dns.disableIPv6** to **true**. Then I tried to browse several sites and the problem is solved.

Being fun, I tried to use any network-related programs and the connection is going normal. I didn't know what step(s) did I do to solve the problem, but I say thank you for the solid Ubuntu community to help me solve my problem.

And thank you for **Brandon Williams** and **jonobr** that trying to help me solve my problem.

Sorry for my bad English.

---

### Post by Sarteck on 2010-07-23
> **saifulwebid said:**
> 
Third, finally I tried to change IPv6 setting in Firefox by opening **about:config** and set **network.dns.disableIPv6** to **true**. Then I tried to browse several sites and the problem is solved.


Hah, I've been going through the same problem, but never even gave a thought to it being a setting in FireFox.  :)

I changed this setting, and BAM!  My google searches finally load almost instantaneously, I don't have to wait half a minute for my forums to load.



Sank you, OP, for having this problem and posting the solution.

---

