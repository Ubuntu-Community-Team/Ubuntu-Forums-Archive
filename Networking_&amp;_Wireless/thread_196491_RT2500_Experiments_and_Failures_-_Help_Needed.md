---
title: "RT2500 Experiments and Failures - Help Needed"
date: 2006-06-14
forum: Networking &amp; Wireless
---

### Post by cholly on 2006-06-14
**Short**
Any suggestions on how to 'restore' my wireless configuration to how it would have been after the upgrade from 5.10 to 6.06 would be appreciated, then I can just try the suggestsions in the more current threads regarding /etc/networking/interfaces file and see if I can get that working.

**EDIT:** Once I got home I tried a few more things, nothing major just checking to see that I driver was installed and some basic iw* troubleshooting and was able to get it to work by basically reconfiguring it *agan* using wifi-radar. I'd tried this once before to no avail, so I don't know what changed. 

The driver is listed as rt2500 and I can set up a managed DHCP WEP connection with wifi-radar and it persists through reboot. The Gnome network panel doesn't seem to work. this is a known issue I think.

cheers

**Long**

I was experiencing difficulty with my wireless connection (RT2500 - RaLink) since my update to 6.06. I was getting similar "No DHCPOFFERS" errors as discussed here, however I did not find that thread in time, I found others though and with the limited knowledge I found there I think I have only managed to make matters worse. Here is how things have gone: 

First
----
I searched for infomation on the web but was in a bit of a rush and didn't find  what I was looking for so I searched the package db via Synaptic for 'rt2500' and got a couple of hits. 

```
rt2500, rt2500 source
```

A config tool for the rt2500 chipset and the source for said drivers, respectivly.

So I installed them allong with a recommneded pkg:
```
module-assistant
```

Recommeded to use to fetch the kernel headers and source files to build that (or other) module(s).

Second
-------

I ran module-assistant and it appeared to do everything needed so I ran the rt2500 config tool too but it claimed to not have the neccessary files needed to run (sorry I do not have the output). Basically it could not find the driver.

So figuring that perhaps it was just in the wrong place (inspired by: [http://doc.gwos.org/index.php/Rt2x00drivers](http://doc.gwos.org/index.php/Rt2x00drivers)) i looked for the driver and only got confused b/c the locations recommended by that link were not helpful either.

So I planned to install the driver manullly. I 'removed completely' via Synaptic the three packages I installd in my first step.

Third
-----

I downloaded driver from sourceforge (rt2x00-2.0.0-b3.tar.gz) and untarred it and did a
```
make install
```

with very little output and tried to see if the steps outlined in the link in my second step would work, but they did not. The driver does not seem to be where it is suggested to be by the howto or the driver README.

Fourth
------
I have found the threads regarding editing the 'interfaces' file etc and the several threads on the original problem (remember the original problem?) and would like to try those steps, but I don't think I have my drivers installed anymore or if I do, if they are in the right place or loaded correctly, because now I don't even have a signal meter reading, whereas at the beginning of this free-form jazz oddessy I did.

So...

Any suggestions on how to 'restore' my wireless configuration to how it would have been after the upgrade from 5.10 to 6.06 would be appreciated, then I can just run the suggestsions in the more current threads regarding /etc/networking/interfaces file and see if I can get that working.

Sorry for the long post, but I figured I should get it all out in the initial post.

---

