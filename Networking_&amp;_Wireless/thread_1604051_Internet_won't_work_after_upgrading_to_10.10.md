---
title: "Internet won't work after upgrading to 10.10"
date: 2010-10-23
forum: Networking &amp; Wireless
---

### Post by Apostolique on 2010-10-23
I have installed Ubuntu on an other computer using a Ubuntu 9.10 cd and I can connect to the internet perfectly. Now that I upgraded to Ubuntu 10.10, the internet won't work. I can see the connection but doesn't seem to be able to connect to it. 

I remember having a similar problem with Ubuntu 9.10 on an different computer but I never found a fix to it. I tried searching for fixes to similar problems but none of them seemed to work.

---

### Post by PokerJoker on 2010-10-23
> **Apostolique said:**
> I have installed Ubuntu on an other computer using a Ubuntu 9.10 cd and I can connect to the internet perfectly. Now that I upgraded to Ubuntu 10.10, the internet won't work. I can see the connection but doesn't seem to be able to connect to it....

Ah...i've just posted on another thread but this seems to be the proper channel. I have the same problem, but you may need to give some more info....maybe you can describe it in some more detail?
Can you ping? can you open webpage of your router? 

Here's my findings (as posted earlier):

I've just upgraded to 10.10 from 10.04 by means of Live-CD (Beta) as i couldn't get the network connection (internet only, local network just fine) to work in 10.04.

Here's my problem.
Dualboot system has perfect internetconnection when running Windoze..
On 10.04/10.10, i get a DHCP ip, can access router webpage with FF no problem, can even ping ubuntuforums.org (40ms avg)... so i do have a decent internet connection....
I'm using wired only...

**But:** webpages won't load, also package-manager won't load repositories, traceroute to ubuntuforums.org times-out.....

My first guess would be DNS problems, but tried static ip with valid DNS entries with same results....

Many many problems found, with different causes but not a solution yet to this problem. 
A last remark, my Andriod phone won't work either (wireless) on my home network unless i use static ip. iPhone has no problem on DHCP....

Edit: Just ran the Live-CD on other machine (Dell Latitude notbook) over wireless connection (to same ADSL ISP router) with same result, can ping, can't traceroute/open webpage. Neither with DHCP or static ip/dns

---

### Post by musicthebee on 2010-10-23
I have the same issue with wired and wireless connections with 10.10 release. This happened on two systems (one is a laptop and and the other is a desktop).

I can ping the web sites fine but however I cannot telnet to port 80. The firefox will eventually give up loading the websites. 

Can somebody help? I have tried disabling ipv6 alltogether but that doesnt help either.

Thanks
M

I t

---

### Post by PokerJoker on 2010-10-24
Ok, i seem to have solved this weird problem for me anyway.
As both my desktop and my laptop, wired and wireless weren't working in Linux mode but ok in Windows mode it had to be software related.
As i previously had an Ubu server running for a few years behind this same modem, checked the adsl/router's (Thomson TG787v) settings again, portforwarding for 80 was still set. Removed this without result, restarted modem and FINALY webpages load like a charm. 

Not sure if this is the same problem that threadstarter Apostolique has... :(

I would like to know what more tools there are to check network connectivity besides ping and traceroute. Trace route clearly showed a problem, just not where....

---

### Post by Apostolique on 2010-11-08
Sorry for not coming back earlier to respond to anything but...

I made a mistake in my op. Here is my system:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"

When I updated from the update manager, it says "The new version "10.04 LTS" is disponible." It means that I was updating to version 10.04 LTS. Since 10.04 LTS is the long term version, I'm pretty sure I want to have the 10.10 instead.

Could that be the problem? Do I have anything wrong?

---

### Post by grahammechanical on 2010-11-08
Apostolique

The correct way to upgrade from 9.10 would be to download 10.4 and then 10.10 as a progression from one to the other. Unless you download an install CD or DVD image and burn it to disc and then do a new installation writing over the previous installation. Update manager was doing things correctly. There must be a different reason why you cannot connect to the Internet.

How do you know that the connection is there? You say you can see it. How do you know that you cannot access the Internet? What have you tried? Tell us what kind of modem you are using, what type of computer. ARe you trying to connect by wireless or by wire (ethernet)? You do not give us enough information even to make a guess. I would not want it to be my last. Oh. it is wishes that will be my last. Sorry. Misread your signature.

Regards

---

