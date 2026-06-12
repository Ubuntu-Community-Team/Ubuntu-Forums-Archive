---
title: "Wireless no longer connecting, and repeatedly asking for WEP Key."
date: 2010-07-28
forum: Networking &amp; Wireless
---

### Post by WombleKiller on 2010-07-28
Hey. I downloaded the latest version of Ubuntu yesterday (10.04 LTS) for the first time and it worked like a treat, with the Internet conencting immediately without any problems.
 
However, this morning I turned on my laptop and despite seemingly connecting to the network, Ubuntu won't conenct to the Internet. It is also repeatedly asking for me to re-input the WEP Key despite it being correct and always automatically inputted.
 
**Machine:**
> Advent 8117
Intel Core Duo T2080 1.73GHZ
1GB RAM
 
RaLink RT7
 
I've been looking around for hours on the Internet to try and find a solution but to no avail, even though people do seem to experience similar problems. Also bare in mind I am a complete Linux newbie!

---

### Post by quixote on 2010-07-30
Yeah, there are some kind of issues (read: Issues) between Lucid and wireless.  A bug of some kind that causes it to drop wireless connections, especially if your system uses the iwlagn driver.  This is the bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/548992?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/548992?comments=all)

I use iwlagn and I'm having the problem after coming out of suspend, and it is very annoying.  I tried the ipv.6 fix suggested on launchpad, but it doesn't work either.

What has worked (so far, knock on wood) is to manually reassociate the Access Point when the connection is lost.  To find your AP, open a terminal (Applications > Accessories > terminal) and type```
iwconfig
```and copy the Access Point down exactly.  That stays the same for a given router and computer.  Also note the system's wireless designation, eg wlan0.  Then, to manually re-associate the AP type```
sudo iwconfig wlan[COLOR="Blue"]0[/COLOR] ap [COLOR="Blue"]00:80:4D:99:D7:10[/COLOR]
```Substitute your own values for the bits in blue.

To repeat the command, hit the up arrow, the command will reappear, and hit return.  Sometimes I've had to repeat five or six times before it successfully reconnects.

A neat trick when you need the command again hours or days later: open the terminal and hit ctrl-r. That prepares it to do a reverse search.  Then just type in a couple of letters from your previous command, such as ap, and it'll fill in the whole command.  Hit return.  Saves having type the whole thing in all the time.

---

