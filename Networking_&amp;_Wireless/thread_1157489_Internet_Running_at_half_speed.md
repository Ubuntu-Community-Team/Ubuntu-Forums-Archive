---
title: "Internet Running at half speed?"
date: 2009-05-12
forum: Networking &amp; Wireless
---

### Post by BlackRat90 on 2009-05-12
I switched to ubuntu 9.04 about 2 weeks ago and ever sense then my internet has been runnning at half the speed it should be. i just ran test at speedtest.net to make sure...
it came back half of what it should be.

it has done this before with my router but then it usually effect my dads desktop computer as while, which it hasnt, that leads me to believe that it is something wrong here. also it takes a VERY long time to connect if it does at all.
is there a setting i need to change? i read around here that ipv6 could be the problem but i really dont know how to fix it.

---

### Post by BlackRat90 on 2009-05-12
The lack help on these forums is disconsirning...
Everyone else who post here seems to get there help, but alias....

---

### Post by Iendicis on 2009-05-12
1. Spell stuff correctly. Coherence is key.

2. More info. What you've posted now is cryptic. Network hardware (card, router, modem), anything else pertinent to the topic, etc.

3. You posted about a half an hour ago. Maybe, just maybe, there simply hasn't been anyone that knows the answer yet. Just because the forums here are very popular doesn't entitle you to instant gratification.

---

### Post by BlackRat90 on 2009-05-12
1. very sorry
2. no
3. it should :P

anyway nothing has been change except i put ubuntu on my laptop.

---

### Post by orlcam2002 on 2009-07-07
I have the same issue.  I'm connected via Verizon Fios at 20/5.  My download speed is around 10 upload is 5. 
  
Ubuntu 9.04.
Kernel 2.6.28-13
gnome 2.26.1
AMD phenom II x4 955
4gb memory

All my other computers (2 ubuntu, 2 windows) are at 20/5 and only one is at 1/2 the speed.  I've already changed the IPv6 stuff on it but I didn't expect to see a jump on this as my other Ubuntu machine (9.04) didn't have any modifications on this. 

I've tested in firefox and opera.  I've even tried firefox in wine.  

Could any software cause this?

---

### Post by jonobr on 2009-07-08
This is a funny thread

orlcam2002  if your getting 10 meg down and 5 meg up thats pretty good so IM not sure what your issue is, and if you expect higher speeds then what your seeing.

On the IPV6 front, heres what I dont get,
You obviously researched this , you undoubtedly saw that it helped other peeple achieve faster speeds,
however, becuase it didnt help you in your situtation, you dont even feel inclined to pass on the information of your findings to someone else.
As they say in the united states, thats fubar.


BlackRat90 2 points.

[HERE]("http://www.clububuntu.com/2009/01/how-to-disable-ipv6-in-ubuntu-810.html")is info on disabling ipv6 

There are other examples, such as [HERE]("http://www.ubuntugeek.com/speed-up-firefox-web-browser.html") which help you speed up the firefox browser also, may be worth a try

2- You should try downloading a file using the browser against using command line.
You can do this by using something like ftp in the terminal and ftp to a location with a file you can download. Compare that against using the browser for the same download.
If you controlled the remote server that would even be better.

---

### Post by orlcam2002 on 2009-07-08
Dude,

As for that comment on not inclined to pass on the information.....I just did buy saying it didn't help me.  What more do you want?  Should I post something every 5 minutes on what I'm doing?  I don't get that response.  Please don't respond if you plan on continuing to attack me.  This ain't Mafia Wars.

My rated speed is 20/5,  but I'm getting 10/5 on just one machine.  So, my download time is cut in 1/2.   I've tested the same line on a different computer and that computer is at 20/5.  So, it's not the line coming in.  

I've did some more research to find out if the settings for the lan connection on the mb matches the specs on the mb and it does:
[COLOR=DarkRed]orlando@orlando-desktop:~$ sudo ethtool eth0
Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
    Link detected: yes[/COLOR]

So I can rule that out also.  It leave's me with something running that's preventing a full 20/5.  I'm really puzzled on this.  I don't have the firewall on but I tried to a few weeks ago and had issue so I turned it off.  I'm wondering if there's some setting that didn't get turned off when I turned off the firewall.  Not sure what to check.

---

