---
title: "Getting Started"
date: 2005-12-26
forum: Networking &amp; Wireless
---

### Post by jbmalone on 2005-12-26
I live in a two story house and up to this point my using the cable modem has never been a problem.  There are two computers downstairs that use AOL, and neither person really cared that they were on dial-up.  Until now.  I want to set up a network for the house so that everyone can use the cable, with a basic betwork for files and such.  

I have done some basic networking on Windows before, but have never really touched it with Linux.  I would like to make my computer the access point, and I want it to be as fast as possible with the largest range.  

The only types of routers I really know are Linksys.  I have looked at the 802.11fg with SRX, SRX 200 and 400.  This is a wireless network, btw.

I know that the computers downstairs will need wireless cards too, and I have looked at the USB 2.0 cards that max at 54mbps.  I would like the cards to be just as fast as the router.  The SRX 400 can do up to 240mbps, so it would be nice to have cards that match, for instance.  

Any help on this, or a website that would send me in the right direction involving the wireless routers and the cards?  I know this has to be possible.  

Just to let you know, both computers downstairs are running XP Home, and I am running Ubuntu 5.10.

Thanks.

---

### Post by Lambert on 2005-12-26
I'll give you my basic knowledge here.

The two windows computers should be fine with just about anything you buy as there will be drivers that support anything on the market.

What ever router you buy you'll have to make sure the signal/technology and throughput matches the cards you buy for the pcs. With the speeds and srx you're talking about I believe you're looking at the 802.11(pre-n) protocol which is known as mimo technology. (pre-n because the standard is not completed yet, when it is it will be known as 802.11n)

Now as for linux, you're looking at a problem. We are just now getting drivers to their "stable" release for the 802.11g protocol. I do not currently know of a project that's working on a driver for the .11n protocol so none of those routers and matching cards will work for you on the linux box. You need to go with 802.11(a)(b)(g) technology.

There are differences with these, g offers the best throughput at 54M and is kind of the best of a and b protocols. You can actually find routers such as the d-link di-624 routers with superg cards that can raise the max throughput to 108m. What happens is it creates two separate 54 channels and transmits data on both channels where the mimo technology above is an advancement in throughput on a singal channel.

Now you say you want your box to be the acces point? Do you want to run your pc as an acces point or a firewall inbetween your house and the internet? And will it be wired into the network or wireless also? I've based my comments on all boxes being wireless. You could set it so it goes like this modem>linux>router>wireless signal with no problems. The problems comes in if you want modem>router>wireless-all pcs

So I hope I summarized this so it can be understood. Here are some links for more reading. There are endless links in all these that coule keep you busy for a while.

[http://computer.howstuffworks.com/wireless-network8.htm](http://computer.howstuffworks.com/wireless-network8.htm)
[http://www.tutorial-reports.com/wireless/wlanwifi/standards.php](http://www.tutorial-reports.com/wireless/wlanwifi/standards.php)
[http://en.wikipedia.org/wiki/IEEE_802.11](http://en.wikipedia.org/wiki/IEEE_802.11)
[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)

If you have more questions or want any clarification send me a pm or if you have im I use icq and msn you can contact me at. (links in my user profile)

---

### Post by Gooks on 2005-12-26
How do i do this?? [http://forums.gstutor.com/showpost.php?p=519&postcount=12](http://forums.gstutor.com/showpost.php?p=519&postcount=12)

---

### Post by jbmalone on 2005-12-27
I would like to just run the router off of my Linux box, so I guess in essence that one would be wired and then the other two would be wireless.  Thanks for the tip on the MiMO not being supported in Linux because I was really clueless on the whole issue.  I am going to take a look at some of the routers you mentioned.  How complicated is this going to be?  Like you said, I am not really worried about it from the Windows end, just the Linux.  Also, on the 54mbps network, how much speed lose am I going to see on my computer and the other two?  I know that sharing the signal with lower the speeds, but how much am I looking at?

---

### Post by Lambert on 2005-12-27
It all depends on the network activity that's happening to how much you could possibly lose. If both windows pcs are streaming music/video you could see a slow down. If normal web surfing/e-mail checking is done there won't be a noticeable difference.

There are apps that can limit and give rules to how the bandwidth is used so it's balanced in the network.

As far as setting up linux so it routes, I don't believe it's too hard but I've not done it.You need two nics, turn on ip forwarding, and set up routing tables. there are others in the forum that have done this and there are tutorials out there somewhere on how to set it up.

Something I would recommend is getting a good router/ap and instead of running all traffic through the linux box it can just be modem>router a wire going to linux and the wireless signal for the windows boxes.

I use a [d-link di-624]("http://www.dlink.com/products/?pid=6") which I haven't had any problems with and have been happy with. I also have friends who talk highly of netgear products.

running through the linux box though you have more flexibility though with firewalling, bandwith monitoring, bandwidth control, etc...

One more good link

[www.linuxhomenetworking.com](www.linuxhomenetworking.com)

---

### Post by jbmalone on 2005-12-27
Yeah, that would be a pretty good setup.  I guess now I am going to look at routers and wireless cards and post them up to see if they are good.  Thanks for all of your help.  I greatly appreciate it.

---

### Post by jbmalone on 2005-12-27
I went to Circuit City and saw these two options:
Router:
[http://www.circuitcity.com/ssm/Linksys-Wireless-Router-v-2-1-WRT54G-/sem/rpsm/oid/69086/rpem/ccd/productDetail.do](http://www.circuitcity.com/ssm/Linksys-Wireless-Router-v-2-1-WRT54G-/sem/rpsm/oid/69086/rpem/ccd/productDetail.do)
Card:
[http://www.circuitcity.com/rpsm/oid/80674/rpem/ccd/productDetail.do](http://www.circuitcity.com/rpsm/oid/80674/rpem/ccd/productDetail.do)
or [http://www.circuitcity.com/rpsm/oid/86339/rpem/ccd/productDetail.do](http://www.circuitcity.com/rpsm/oid/86339/rpem/ccd/productDetail.do)

or

Router:
[http://www.circuitcity.com/ssm/Netgear-Wireless-Router-WGT624-/sem/rpsm/oid/86260/catOid/-12980/rpem/ccd/productDetail.do](http://www.circuitcity.com/ssm/Netgear-Wireless-Router-WGT624-/sem/rpsm/oid/86260/catOid/-12980/rpem/ccd/productDetail.do)
Card:
[http://www.circuitcity.com/ssm/Netgear-Wireless-Desktop-Adapter-WG311TNA-/sem/rpsm/oid/97244/catOid/-12980/rpem/ccd/productDetail.do](http://www.circuitcity.com/ssm/Netgear-Wireless-Desktop-Adapter-WG311TNA-/sem/rpsm/oid/97244/catOid/-12980/rpem/ccd/productDetail.do)

The Linksys setup here is a lot cheaper than the Netgear option.  Will the double speed really be needed?  Will the speed itself affect the Internet speed on the two wireless computers, OR will it just affect how fast I can transfer files between the two computers?

---

### Post by mips on 2005-12-28
[QUOTE=jbmalone]....Will the double speed really be needed?  Will the speed itself affect the Internet speed on the two wireless computers, OR will it just affect how fast I can transfer files between the two computers?[/QUOTE]

The only thing the speed will affect is between the 2 computers or computer & router. It will not affect your internet speed as that is already the lowest common denominator here.

---

### Post by jbmalone on 2005-12-28
Well if that is the case, do you think the range on the Linksys will be good enough?  They don't really need the extra speed, and plus with rebates, I can get the Linksys for under 100.  I'll try to get a close estimate on the footage that it will need to go.

---

### Post by Lambert on 2005-12-28
That should be a good router for you. signal strenth has so many factors it's hard to tell but if this fits in your budget go for it.

If not circiut city has a good policy about returning and exchanging if you have any problems. (at least my experiences)

---

### Post by jbmalone on 2005-12-28
Yeah, if the speed only depends on computer to computer speeds, then 54mbps is fine.  I don't need the 108.  Now, when I buy it, what are my first steps under Linux.  Will Linux be fine since it will be wired to the router, and then I configure the wireless parts on the XP computers?

---

### Post by Lambert on 2005-12-28
there will be instructions that come with the device on how to set it up.

usually it's just plug in a pc in to a wired port, open up a browser and type the routers ip address in the address bar (something like 192.168.1.1 instructions will tell you what it is) you then administer the router through a web interface.

linksys has a real good support system with online chat style help if you need it. Just go to the linksy website and click on support.

---

### Post by jbmalone on 2005-12-28
All right.  Thanks for all your help.  I'm probably going to get the hardward tonight.  So, I hope that it isn't too painful. 

I'll try to follow up later to tell of my adventures, or if I have any questions.

---

### Post by jbmalone on 2005-12-28
I got the hardware and now I am kind of lost on how to set it up.  I can't use the Setup Wizard CD, so I went to the online setup and have no clue what to put in.  I guess I am going to have to figure it out.

---

### Post by jbmalone on 2005-12-28
Here is how it panned out:

I got everything out and plugged in and ran into trouble with the router giving me Internet.  Eventually, Lambert and I deduced it down to a DNS problem.  However, I remembered that everytime I unplugged my ethernet cable, my modem needed to be reset.  So, when I was going to try and access the dns stuff manually, I reset the modem before turning on the computer.  It worked.  Everything was fine and running perfectly.
As for the USB cards, I plugged them in ran the software and they were working in maybe 15 seconds.  It is only about 20 minutes old, but I hope that it works out and I did everything correctly.

I want to say thanks for everyone that helped me, you really gave me the knowledge to get this running- especially Lambert.  

Thanks again,
Jacob

---

