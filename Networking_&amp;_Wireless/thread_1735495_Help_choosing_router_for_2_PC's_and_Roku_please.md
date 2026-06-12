---
title: "Help choosing router for 2 PC's and Roku please"
date: 2011-04-21
forum: Networking &amp; Wireless
---

### Post by kansasnoob on 2011-04-21
I've been planning for some time to add a Roku box so I can get Hulu plus on my TV (and possibly Netflix later on), plus I do quite a bit of iso/upgrade testing during Ubuntu development (nearly three years now), and it would be very convenient to be able to connect both of my computers at the same time :)

So I need a router. I currently just have an AT&T DSL modem, but I have super fast DSL (about 7,000 kbps down and 1500 kbps up), and it costs me about 60% of comparable cable service :) Anyway just a desktop switch won't help until I get a router set up.

No doubt the easiest way to go would be AT&T's own router for $100 US:

[http://www.att.com/equipment/accessory-details/?wtSlotClick=1-005GWU-0-1&WT.svl=calltoaction&q_categoryid=cat2020062&q_sku=sku5140238&q_manufacturer=&q_model=](http://www.att.com/equipment/accessory-details/?wtSlotClick=1-005GWU-0-1&WT.svl=calltoaction&q_categoryid=cat2020062&q_sku=sku5140238&q_manufacturer=&q_model=)

I still have Win XP on one box (although it's nearly never used) and their "stuff" comes with an auto-setup disc that usually just works, but I've dealt with their "tech help" several times down through the years and as soon as you mention Linux they become almost mute :(

OTOH I've been looking at less expensive alternatives:

[http://www.trendnet.com/products/proddetail.asp?status=view&prod=145_TW100-S4W1CA&cat=11](http://www.trendnet.com/products/proddetail.asp?status=view&prod=145_TW100-S4W1CA&cat=11)

[http://www.netgear.com/home/products/wired-routers-and-modems/wired-routers/RP614.aspx](http://www.netgear.com/home/products/wired-routers-and-modems/wired-routers/RP614.aspx)

The Trendnet runs about $35 US and the Netgear runs about $42 US. As far as I can see both would just connect to my modem with a Cat5 ethernet cable and then to each device with additional Cat5 cables.

But this really is a first for me :(

Any suggestions at all will be appreciated :)

I've found this community to always be quite helpful, and "if in doubt" I find it best to ask before jumping into something. Thanks in advance.

Oops, I left out one thing. This from Netgear really impressed me:

> Open Source for Linux developers
NETGEAR&#8217;s Web Safe Router is the perfect solution for sharing one broadband connection for all computers or Ethernet devices on your home network. The router also features double firewallprotection that helps shield the network with two security methods&#8212;Network Address Translation (NAT) and Stateful Packet Inspection (SPI). Ultra-fast LAN ports distribute high-quality digital movies, photos, and MP3s at speeds up to 200 Mbps**. Installation is a snap, thanks to a unique setup CD that automatically detects and configures all necessary settings.

---

### Post by kansasnoob on 2011-04-23
Bump :)

---

### Post by kansasnoob on 2011-05-28
Thought I'd give this another bump.

I'm going to stick my neck out and go for it in just the next week or so :D

---

### Post by chili555 on 2011-05-28
Before you consider AT&Ts router, you might read this: [http://linuxlock.blogspot.com/2010/12/at-blocks-linux-configuration.html](http://linuxlock.blogspot.com/2010/12/at-blocks-linux-configuration.html)> Starting about two months ago, we noticed that when we accessed the modem page at 192.168.something.or_another, as soon as we focused the cursor in the first field, we got a popup that asked us to install software to guide us through the configuration.

Of course, the requirements were a Windows Operating System and a Microsoft Explorer browser.  Big surprise...an ActiveX control.
He is referring to the combination modem and router device.

A lot of people might reply that they have a Windows computer around so it's no problem. However, do you really want to give a premium price to a vendor that actively and knowingly participates in what many of us here consider anti-competitive practices? In other words, if I spend $100, I must use Windows but if I spend $42 I can use anything I want.

DISCLAIMER: This is my opinion only. I am not on the staff of the forum or Ubuntu and my opinion is only my own.

I have used a variety of routers and never had the slightest problem with Ubuntu. I suggest you research  reliability and choose any commercially available router you want.

Are you certain that you won't want wireless in the future? I'd consider a router with wireless capability. As well, I'd look for gigabit speeds for streaming as well as N speed capability for wireless. For a few dollars more, you future-proof yourself, in my opinion.

Finally, I'd suggest you set up the DSL username and password in the router, not the computers.

---

### Post by kansasnoob on 2011-05-28
Oddly even my old AT&T provided modem is like that.

If for any reason I have to totally reset the modem then I MUST use Windows to get it up and running again :(

And as soon as you mention Linux to the AT&T support folks they get tongue-tied. But I do have good service at a decent price, better than cable here.

But I've read a lot of nightmare stories about PS2 and Xbox with their 2-wire routers, and I'm thinking a Roku box has to be similar - barely for sure - so I think it's just more money for no better support.

I'll look at some wireless-N routers and try to find out how much I don't know :D

Many, many thanks :)

---

### Post by kansasnoob on 2011-05-28
Just thought to add, the Windows requirement is obviously NOT a security related issue with AT&T because I have an old PII puter that can run Win ME which I still have on a spare hard drive and I can even use it to set up the modem.

It's obviously just an AT&T laziness issue, like their revenue won't allow them to invest in better support :lolflag:

---

### Post by kansasnoob on 2011-05-28
I can see already that this was very good advice. I'm finding many more options, including devices with USB support to share a printer :D

Much, much reading to do but thanks again. This is the best part of the Ubuntu community - sharing knowledge.

---

### Post by chili555 on 2011-05-28
I'm not sure it's unwillingness to hire Linux-friendly tech support; I think it's arrogance. I can go on to my bank's site and pay out $3000 in bills and they don't know or care what operating system I use. The same with my investments. The same with my taxes. But AT&T believes that they only need to write Windows-centric software. A tiny bit of me supposes that Microsoft offers to write the router/modem software free so they can lock out Linux and, I'd guess, Mac O/S. I'm probably wrong, but maybe...

In any and every router that you and I can buy at Newegg, Amazon, Best Buy, et al, I have been able to plug in an ethernet cable, type in 192.168.1.1 (or whatever the default IP address is) in a browser and I'm configuring easily. In fact, my neighbor asked me to set up wireless on her system. I don't even know what her system is! I walked my ancient IBM Thinkpad running Ubuntu 10.04 LTS over there and I tried 192.168.1.1 and got no joy. 192.168.0.1 got me in. I played with usernames and passwords (admin? pass? user? blank?) and got in and set up wireless, a WPA2 password and then connected wirelessly with her and my computer! I helped her change the password to one I couldn't see. 

I suppose you could get one that wouldn't yield to Linux, but I strongly doubt it. There are inquiries on this forum about all manner of stuff, some that I've never heard of!

PS- Kansas? I grew up in Shawnee Mission!

---

