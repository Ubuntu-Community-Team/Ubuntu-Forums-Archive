---
title: "How to improve internet connection?"
date: 2013-07-13
forum: Networking &amp; Wireless
---

### Post by Nate Hofmann on 2013-07-13
I have a Trendnet Tew-664UB v2 wireless usb adapter for internet on my computer. Though recently the internet has had horrible connection with games like Minecraft and ver slow internet on Foxfire. Any solutions to help spped it up or improve the connection?

Btw I might purchase a new wireless usb adapter, any good ones for 30-100 dollars that are good for online gaming and Ubuntu supports?

---

### Post by TheFu on 2013-07-13
There are 100+ suggestions - too many for put into a forum.  Without facts and data, it is hard to recommend anything for any specific purpose.  Some of the suggestions below won't help you at all - YOUR specific situation determines what can be done to help.

Use wired ethernet.  Wired **always** beats wifi.  Wifi is not as stable, though it appears that way for light web surfing. When it comes to stable throughput, wired ALWAYS beats wifi. No peaks and valleys.

Perform a wireless survey of your area, find where the signal is strongest and sit there.

Make certain the router/AP is using the least-used wifi channel that doesn't overlap other channels. [http://blog.jdpfu.com/2010/11/22/recheck-wifi-channel-every-year](http://blog.jdpfu.com/2010/11/22/recheck-wifi-channel-every-year)  In the USA, for wifi-G - that means using channels 1, 6, and 11 and none of the others.

Limit the number of devices connecting to the wifi network - each added device approximately halves the throughput. Even just a connection sucks bandwidth.

Use a PCI network/wifi adapter, not USB. USB bandwidth is limited and less than some networks support. CAT5 plugs connect well, USB connections seem to fail.

Buy a faster internet connection.

Buy a better wifi access point and/or antenna suited for the specific environment you are trying to work in.  I like the Ubiquity line but that is almost always overkill for a home setting unless there is a compound or longer than usual distances involved.

Buy a faster router.  The router makes a huge difference in network performance. You didn't say what sort of router was being used. This is probably the most important bottleneck on the network.  A new wifi adapter for the PC won't help at all if a slow router with wifi-B is used.

Wired connections are **always** better than wifi. ALWAYS, if convenience isn't a consideration.

---

### Post by anspectrum on 2013-07-14
TheFu has described it eloquently. If you want to play online games specially FPS, go for wired connection (Ethernet / Fiber). Many online games work pretty good if you have got 512kbps BW. Higher is better though. Alot also depends where the gaming server is located i.e., delays and jitters between your ISP and the Server hosting ISP. You can use trace facility (tracert for MS and traceroute for ubuntu) to see where are the maximum delays between your router and the destination server etc etc.

Also you have not mentioned if you are a Ubuntu user or not. :) . MS can have its own lacunae.

Cheers.

---

### Post by praseodym on 2013-07-14
What kind of stick is it? Please show the terminal outputs of:
```

lsusb
lsmod
iwconfig
ifconfig -a
iwlist chan
sudo iwlist scan
```

---

### Post by TheFu on 2013-07-14
None of this matters until we know the router or wifi-access point capabilities.  That equipment and the up/down bandwidth are probably much more important overall.

---

### Post by Nate Hofmann on 2013-07-14
First off I am sorry that I havn't been very clear. 

The type of router I use is a Belkin F5D8233-4v3 Wirless Router. 

Though I know wired beats wireless beats wifi. I plan to get my own modem now, could anyone recommend a good $25-75 modem that meets requirments for online gaming?

---

### Post by TheFu on 2013-07-15
What sort of modem?
* Cable,
* DSL,
* Wireless (cellular network would be good to know too),
* Old-style POTS?

Specifics can help someone provide answers.  

My home connection is through a cable modem that the cable company provides. I cannot provide one myself, since it isn't a residential connection.  Policy of the cable company is that they provide the equipment and manage it for business connections.  For about a decade, I had my own cable modems and managed them - not that there is much to manage.  The distance that the coax runs from the street to your home matters greatly.  I've had 4 different cables run at this house. There is a shorter way, under the driveway and a longer way all the way around the house to the demarcation point. With brand new very thick RJ54 coax, the signal-to-noise ratio is much better going the short way. Going the long way, sometimes we had data loss.  There is signal loss for every foot of the cable.  I always have some other router behind the cable modem/router that I manage - TP-link, Buffalo, Linksys which was the 1st line of security for the network here.

I've never had DSL due to the distance.  Typical DSL connections here are 6/1Mbps and most people never see either, whereas typical cable connections are 22/5Mbps with those being the usual speeds even during peaks. Both offers cost about the same - so the DSL is about 4x more expensive for a slower connection.  

Wireless (i.e. cellular) connections can be around the DSL speeds now, but only if you are in the upgraded areas.  Any radio-based connection will always have ups and downs - it isn't s laminar flow of data, it is more like going over a series of waterfalls with very high speeds occasionally, and a few trickles elsewhere.  For casual web surfing and email, that is fine. For running a server or gaming it is terrible - even worse than wifi.

In some countries, internet is provided via WiFi .... this is strange to people in the USA.  The telco puts wifi antennas on poles in densely populated cities and 200 people share it concurrently.  I guess if you have a smartphone and electricity isn't always available at your home (4 hrs on, 6 hrs off around the clock), then some wifi provided externally is better than nothing.  When I was in Kathmandu a few months ago, the compound where I stayed had battery backups for the wifi and fibre connection into the ISP. The internet always was up.  BTW, I was there upgrading their network.  It is hard to get used to rolling power outages as a way of life and non-potable water everywhere.  Warm water available only in the afternoon on sunny days - solar heated.  Every time I get hot drinking water from a tap here, I'm amazed.  Sorry to digress.

Anyway, if you can provide more details about the setup, it helps us make better recommendations. It is hard when you are new to this stuff to know what to provide - more data is better than less, but starting with the specific service plan from the ISP, all distances and boxes used helps.  If things are on a different floor and going through walls - what are the walls made from?  How close are your neighbors?  What wifi do they have running? Which channels do they use?  Is there a microwave between the computer and wifi router?  Any house wireless phones used?  Anything else running over 2.4Ghz radio nearby?  What is the total number of devices connecting with the wifi router you use? Are any old, as in supporting wifi-B or wifi-G only?  Is the area really humid or very dry?  All these things matter.

---

