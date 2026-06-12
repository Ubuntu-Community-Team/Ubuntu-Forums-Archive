---
title: "Throttled Download Speeds"
date: 2011-04-19
forum: Networking &amp; Wireless
---

### Post by MuerteBlack on 2011-04-19
I have had a fairly perplexing problem with my Lubuntu Maverick installation on my laptop for the past few weeks.

My laptop is connected to a DSL-based LAN via 100mbps Ethernet - pretty typical. Usually, the download speed from most websites tends to be around 340-350kb/s. However, its Ethernet connection seems to be having some strange hiccups.  The speed starts out at normal ranges, but after about 5-10 minutes of internet use through any means (be it loading normal web pages, streaming video, downloading a file via a browser, or even other uses such as downloading a torrent using Transmission, or even a command line application such as apt, aptitude or wget, etc), the speed suddenly drops to around 40kb/s and will not raise again.  Once this happens, the drop is seen across the board.  Again, once it happens, the speed of everything that accesses the internet is affected.  Web pages load slowly, all downloads will only operate at a maximum of 40kb/s, whether it is from any browser, or wget in a terminal.  The speed stayed slow until I restarted, which would give me another 5-10 minutes.  My troubleshooting attempts yielded some very strange results, which I will relate here:

First, I assumed it was either my ISP throttling speeds, or a router problem.  But even during the slowdowns, the  other computer on my LAN operated at full speed.  Also, I discovered that merely restarting X would cause the connection speed to instantly jump back to full again (for another 5-10 minutes).  I tried disabling ipv6 system-wide by editing /etc/sysctl.conf and adding the lines

```
#disable ipv6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
```

and verified with 

```
muerte@thing2:~$ cat /proc/sys/net/ipv6/conf/all/disable_ipv6
1
```

which did nothing to solve the problem.  I then did another test that surprised me.  I discovered that if I killed X/the GUI with "sudo service LXDM stop" the problem disappeared.  I could run downloads with wget all day long with no slowdowns.  However, if I started X again and ran wget from a terminal in the GUI, I would get the slowdown again.

So I knew there was something that was fiddling with the speeds in the GUI that didn't exist when X was stopped.  I started comparing processes, and saw that one called modem-manager was not running when X was stopped.  I then tested downloading again and waited until I got the slowdown, then killed the modem-manager process.  The process restarted automatically, but as soon as I killed it and it restarted, the download speed instantly jumped back to full again.  I thought I had found the offending service right there.  So I disabled it (since that service shouldn't even have anything to do with an ethernet connection anyway), and tested again.  To my astonishment, the problem persisted.  

So this process wasn't causing the slowdown, and the slowdowns happened even without it, yet if it DID happen to be running when the slowdowns occurred, killing it temporarily fixed the problem for another 5-10 minutes.  That did not, and still does not, make a lick of sense to me.

I know that modem-manager is part of the NetworkManager service, so I tried completely removing the network-manager, modemmanager and network-manager-gnome packages and configured my ethernet connection with the "networking" service via /etc/network/interfaces.  The slowdowns kept happening.  So I went ahead and reinstalled NetworkManager & friends.

And so this is where I'm at today.  To sum things up, I know the following:

1. My connection will only run at full speed for 5-10 minutes before it gets throttled to ~40kb/s.

2. This problem only happens while running in the GUI, and does not occur if X is not running.

3. The modem-manager process is not causing the slowdowns, and apparently neither is NetworkManager, because the problem persists even if both are uninstalled, yet if it happens to be running, I can kill modem-manager which restores the speed for another 5-10 minutes.

This is one of the strangest issues I have encountered, and it really has me pulling my hair out over it.  Does anyone know what else could possibly be causing this strangeness?  If it helps, here are my laptop's specs

Dell Inspiron 5000
700mhz Pentium III
512mb RAM
Xircom CardBus ethernet card.  (Wireless is currently disabled since I never use it.)

Please let me know if there are any other additional details I can provide, such as logfiles, etc.  I'm not sure what all to provide, since I am a bit of a newbie at networking in general.  Thank you everyone in advance!

---

