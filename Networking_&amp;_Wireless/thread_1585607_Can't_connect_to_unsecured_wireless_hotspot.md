---
title: "Can't connect to unsecured wireless hotspot"
date: 2010-09-30
forum: Networking &amp; Wireless
---

### Post by Bucky Ball on 2010-09-30
Hi all,

I'm looking but not finding an answer so wondering if anyone has ideas?

I am attempting to connect to an unsecured wireless network; I helped set it up for my local club with a local ISP. Once things were up and running I took my wife's laptop running Ubuntu 8.04.3 and Wicd. Can see the unsecured network no problem, good signal, hit connect, whirs away for awhile, then: 'Unable to obtain IP address.' Strange. I am about to give up and report back to the ISP when I think I might try one of the old Windows boxes in the computer room. Spots the network, hit connect, online, no problem.

So Windows connects fine, Ubuntu box can't get an IP though no doubt the router is trying to serve it one. Has anyone got any ideas about this? Cheers in advance.

---

### Post by gordintoronto on 2010-09-30
Did you boot at the location of the unsecured network? I have heard of problems trying to resume from Suspend or Hibernate.

---

### Post by Bucky Ball on 2010-10-01
Yep, booted the computer right there. As I say, can see the network, good signal, just won't take the IP the router is no doubt attempting to serve it (obvious as it is serving all the Windows boxes in the place).

---

### Post by mrhhug on 2010-10-01
where you boot the box shouldn't matter, networking resources can easily be restarted ... what program are you using to manage your wireless networks ?

have you tryed wifi-radar?

---

### Post by Bucky Ball on 2010-10-01
Using Wicd and it sees the network fine. I don't think that would be the issue unless there is a setting in Wicd I haven't found (and I've looked pretty hard). 

Once more: Laptop sees unsecured network, excellent signal strength, click 'Connect', unsecured router tries to serve me an IP, short time later this error "Unable to obtain IP." Router's giving but laptop's not taking.

---

### Post by mrhhug on 2010-10-01
does this access point have mac address filtering? - textbook mac filtering

cept you said it connects in wondows....

did you previously spoof your ip in linux for some reason!?1

---

### Post by mrhhug on 2010-10-01
wait you said you setup this wifi network??? > I helped set it up for my local club with a local ISP

.. more details on the access point please! - model and version numbers give us no excuse;)

---

### Post by 0x656b694d on 2010-12-10
Hey,

Have the same no doubt **CRITICAL** issue with my asus eeepc1015 PED.

I cannot connect to **some** unsecured wifi networks.
Using network manager and wicd.

Wicd says 'Not connected' after trying to get an IP.
This happened in Scandic hotel in Helsinki, Finland, in several other places in Saint-Petersburg, Russia.

lspci says i have:
Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY

It does work with my home ad-hoc network, with my office WEP network, with some other networks. Not sure what is the difference for other networks i cannot connect.

I don't see any errors in the logs. Just it fails to get an IP.
I tried default and pump DHCP clients.

Any suggestions would be highly appreciated.

-Mike

---

### Post by joehillen on 2010-12-10
I think there was a regression in a recent 10.10 kernel update because I haven't been able to connect my laptop to my network since the update. I noticed that it said something about wireless in the summary. 

My router is running DD-WRT which I cannot connect to. I just tried connecting to my neighbor's unprotected wireless and it worked. 

I'm using the iwl3945 driver.

---

### Post by 0x656b694d on 2010-12-11
I filed a bug for my problem. Please check if it matches yours:
[bug 689007](https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/689007)

---

### Post by Bucky Ball on 2010-12-28
Problem persists.

---

### Post by henriquemaia on 2011-03-26
I too have this problem. I had to boot on Windows to post this (I'm on a FON hotspot and I couldn't connect with Ubuntu).

---

### Post by mrhhug on 2011-03-26
hmmmmm... where did you all get your wifi cards? American companies? found this [http://en.wikipedia.org/wiki/List_of_WLAN_channels](http://en.wikipedia.org/wiki/List_of_WLAN_channels) N America doesn't use all the channels that the rest of the world uses for public wifi. possibly everyone could report in the channels that they can consistently connect to and the channels they can't consistently connect to. and research if your chipset supports the non American channels.

used this site as a reference:
[http://www.mydellmini.com/forum/dell-mini-10v-mac-os-x-discussion/22762-mini-10v-wifi-adapter-does-not-work-channel-13-a.html](http://www.mydellmini.com/forum/dell-mini-10v-mac-os-x-discussion/22762-mini-10v-wifi-adapter-does-not-work-channel-13-a.html)


```
iwlist wlan0 scanning | egrep 'Channel|Address|ESSID'
```
copy and pasted from : [http://adaywithtape.blogspot.com/2009_09_01_archive.html](http://adaywithtape.blogspot.com/2009_09_01_archive.html)

---

### Post by wilshere on 2011-03-28
Same problem :(

---

