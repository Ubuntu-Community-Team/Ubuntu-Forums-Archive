---
title: "slow wireless connection"
date: 2006-04-29
forum: Networking &amp; Wireless
---

### Post by mentus on 2006-04-29
hi all

i managed to install the driver for my wifi (using ndiswrapper) and establish a wireless connection. however it is quite slow. when i connect to the same network in windows it is much quicker.
could somebody help me to properly set up my wireless connection or to find out where the problem is?

thanks a lot

---

### Post by Gannin on 2006-04-29
In what way is it slow?  As in, once connected to a large file, does it download the file at regular speed?  Or, does it just take a really long time to look up a hostname, so for instance in Firefox, you see in the status bar at the bottom of the screen, &#8220;Looking up whatever web site...&#8221; for a long time?

---

### Post by mentus on 2006-04-30
[QUOTE=Gannin]In what way is it slow?  As in, once connected to a large file, does it download the file at regular speed?  Or, does it just take a really long time to look up a hostname, so for instance in Firefox, you see in the status bar at the bottom of the screen, &#8220;Looking up whatever web site...&#8221; for a long time?[/QUOTE]
Thank You for Your quick response.

Yes, exactly... It seems to take really long time to look up the hostname of whatever website while browsing. The download speed is ok.

mentus

---

### Post by Gannin on 2006-04-30
It sounds like you're probably having a DNS problem then.  You should find out if your ISP has any other DNS servers available in addition to the ones you're already using, and then try those.  I don't know how to do this in Ubuntu off the top of my head, but I can look into it and get back to you if you'd like.

---

### Post by mentus on 2006-05-01
Well, i don't know who my IPS and i don't know what DNS server i am using. I just found out some unencrypted wireless network in my flat, which i don't know who does it belong to and which i can connect to. As already mentioned, using the same network in windows works very quickly. So i wonder, what is the difference in establishing a wireless internet connection between linux (ubuntu) and windows, as there is so big difference in the connection speed while connecting to the same network. Probably it has something to do with the configuration, which i have to set up more properly,or even maybe my wireless interface, which seems to be ok though... i don't know...

thanks for Your help

---

### Post by tribaal on 2006-05-01
Something that helped a lot with my own firefox was [this thread]("http://www.ubuntuforums.org/showthread.php?t=166562&highlight=firefox+speed")... you need to restart firefox for it to take effect, though.

Hope it helps.

- trib'

---

### Post by Gannin on 2006-05-01
Have you ever used your Linux system with a regular Internet connection?  If so, how well did it work then?

---

### Post by mentus on 2006-05-01
The problem has been resolved. Now is the browsing much quicker.

I dissabled the IPv6 following instructions on:
[https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4?highlight=%28ipv6%29](https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4?highlight=%28ipv6%29)

Thanks both of You.

Ubuntu is cool

---

