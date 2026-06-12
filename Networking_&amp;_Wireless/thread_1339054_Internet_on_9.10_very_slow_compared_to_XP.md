---
title: "Internet on 9.10 very slow compared to XP"
date: 2009-11-27
forum: Networking &amp; Wireless
---

### Post by karlhm76 on 2009-11-27
Hi all,

My girlfriend accidentally poured water all over my DLink ADSL2+ modem/router (don't ask!) so I had to buy another in a hurry. When I got home from work I bought a cheap Belkin 300 N modem/router.

My problems started from that point onwards.

The internet is super fast in XP, faster than ever - I can get sustained D/L rates of about 1MB/s from 300K with the DLink.

But on ubuntu I get about 20KB/s maximum, usually much less.

I went to the speed test site for my ISP, both computers wirelessly connected at the same time and ran the test on both computers one after the other. I got about 2500 on the XP laptop, and 256 on Ubuntu.

What gives?
I'll try some testing whilst wired but I doubt it will make a lot of difference.

It does this on both gutsy and (freshly installed) karmic.

DNS on both XP and Ubuntu seems to be set up identically and both are using 192.168.2.1 as the gateway. So where do I start looking for the problem, and how can I fix this?

BTW I don't want to replace the router because it works so well in XP.

---

### Post by prshah on 2009-11-27
> **karlhm76 said:**
> 
The internet is super fast in XP,

But on ubuntu I get about 20KB/s maximum, usually much less.


Please see this thread [ [SOLVED] Firefox/Epiphany/Lynx not loading certain websites]("http://ubuntuforums.org/showthread.php?t=718709") for a possible solution. I would advise going through all the posts (it wont take more than a few mins) but if you are impatient, you can jump to the solution near the end of the second page.

---

### Post by karlhm76 on 2009-11-27
Wow, certainly did the trick.

MTU was set to 1454 by default and had a big warning next to the setting not to change it, after changed to 1492 the difference was incredible.

Thanks again!

Karl.

---

### Post by smarcellus on 2009-11-28
I was having slow internet problems with Ubuntu 9.10 where some times it would error out. I tried to speed up firefox and also tried some other fixes but the only one that worked was disabling Ipv6 with this and it worked on all 3 different browsers I use: 

DISABLE IPV6 IN UBUNTU 9.10 
IN A TERMINAL RUN 
gksu gedit /etc/default/grub 

CHANGE THIS LINE:
GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash” 

TO
GRUB_CMDLINE_LINUX_DEFAULT=”ipv6.disable=1 quiet splash” 

CLOSE AND SAVE

THEN UPDATE GRUB:
sudo update-grub

TO TEST WITH TERMINAL:
ip a | grep inet6
IF THIS RETURNS NOTHING THEN IT IS DISABLED

---

### Post by prshah on 2009-11-28
> **smarcellus said:**
> DISABLE IPV6 IN UBUNTU 9.10 

There is an easier way to do this; edit the /etc/modprobe.d/blacklist.conf file```
gedit /etc/modprobe.d/blacklist.conf
``` and add this line to the end of it```
blacklist ipv6
```

Changes will take effect after a reboot.

As an aside, if IPv6 is causing slow browsing / Internet problems, it is more likely to be a problem with the (substandard) router than with Ubuntu.

---

### Post by enviromook on 2009-11-29
Did you throw your DLink router away?  If you still have it you might be able to save it!  I once spilled a full cup of water over my keyboard of my laptop.  Needless to say I thought it was dead after, and it sat in my closet for two years.  I learned of a trick to bring it back to life using rubbing alcohol.  Usually devices stop working from water spills because the water dries but leaves behind minerals that make cross contacts on the boards.  I took the motherboard out of the laptop and completely submerged it in a shallow pan filled with two bottles of rubbing alcohol (the higher % the better).  I shook it around a little so the alcohol will remove the minerals left behind from the dried water.  I let it dry for a few hours put it all back together and hit the power button, and got a perfect boot up, no joke.  If you think your router is already dead, no harm in trying.

---

### Post by smarcellus on 2009-11-29
> **prshah said:**
> There is an easier way to do this; edit the /etc/modprobe.d/blacklist.conf file```
gedit /etc/modprobe.d/blacklist.conf
``` and add this line to the end of it```
blacklist ipv6
```

Changes will take effect after a reboot.

As an aside, if IPv6 is causing slow browsing / Internet problems, it is more likely to be a problem with the (substandard) router than with Ubuntu.
I tried this with Ubuntu 9.10 and it did not work for me. It did show disabled in System > Administration > Network Tools but did not seem to make a difference and when I ran "ip a | grep inet6" it showed that Ipv6 was still there. Now Network Tools shows Ipv6 as Unknown and ip a | grep inet6 returns nothing and I have no more problems.

---

### Post by Paul Dietrich on 2010-01-09
When I enter:
sudo update-grub

I get this:
/etc/default/grub: 10: quiet: not found

Any idea what to do with that?

...so I went back to the way it was, tried again, and got:

/etc/default/grub: 9: splash&#8221;: not found

I haven't changed anything else in this file, and it's pretty much an unmodified clean install.  Help.  Thanks.

---

### Post by leorolla on 2010-03-16
> **Paul Dietrich said:**
> When I enter:
sudo update-grub

I get this:
/etc/default/grub: 10: quiet: not found

Any idea what to do with that?

...so I went back to the way it was, tried again, and got:

/etc/default/grub: 9: splash”: not found

I haven't changed anything else in this file, and it's pretty much an unmodified clean install.  Help.  Thanks.

See [http://ubuntuforums.org/showthread.php?t=1430322](http://ubuntuforums.org/showthread.php?t=1430322)

---

