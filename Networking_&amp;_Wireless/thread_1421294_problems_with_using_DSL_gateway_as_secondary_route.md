---
title: "problems with using DSL gateway as secondary router"
date: 2010-03-04
forum: Networking &amp; Wireless
---

### Post by knurledflanges on 2010-03-04
Hi everyone,
So, this is a little convoluted and I don't think the problems I'm having are really related to Ubuntu, but I'm on Ubuntu for any local settings I need to change, and this forum is kinda where I take my tech issues these days :).

I live on a property with 3 other units and we all share a cable connection. There's a modem connected to a wireless router (I'll call it the "main" router), which until recently I connected to with an 80' or so long ethernet cable because I don't get a good signal, and all I've got is a desktop anyway. When plugged directly into the main router, I can get very fast download speeds - the fastest I've seen over bittorrent, for example, is about 2.2 Mb/s, and it's over 1 Mb/s most of the time for popular torrents or sites with good bandwidth.

A friend with a laptop is staying with me for a month, so I wanted to set up a wireless router in my home, and my desktop needed to be moved to a location where running a wire is kind of awkward, so I planned on using the wireless too. I don't have a spare proper router with an uplink port laying around, but I did have a spare DSL modem/wireless router combo (which I'll call the "secondary" router) that I used to use at a former residence, and I thought I'd try to use it here. I plugged it into my computer, configured its security settings how I wanted (64-bit WEP) and looked through for settings that seemed like they might pertain to using it in this capacity. I didn't really find any except for something that seemed to turn off its DHCP, which I did. Then I unplugged my computer and plugged in the ethernet cable that runs to the main router (which is a normal ethernet cable, not crossover). I found that this setup does "just work" for the most part - our computers see the signal and can log in and access the internet through the main router's cable connection. However:
1. I can't figure out how to access the secondary router's settings once it's been plugged into the main one, even if I unplug it from the main one. What happens is that as soon as I connect the two routers together, it's almost like the secondary ceases to exist independently until it's settings are purged via the reset button.  I plug it's IP address into a browser like usual, and nothing happens (it's an Actiontec whose stock one is 192.168.0.1 and the main router is a Netgear with an IP of 192.168.1.1).  I can log into the main one like normal through a wireless connection to the secondary, though. If I look at "attached devices" in the main router's config, it lists all the client computers in the network, but there's no IP that could be for the router (I'm sure of this). Each computer connected through my secondary router gets assigned its own IP like normal, and port forwarding works without a hitch. Again, this persists until the secondary is reset - after the two routers are connected but until the secondary is reset, there doesn't to be a way into the secondary's config. The security settings are acting as they should, though (ie, you need the secondary's WEP key to log on).
2. Internet download speeds when connected to the secondary over wireless are extremely slow compared to what the connection is capable of (can't seem to top 90 Kb/s) but for some reason the max attainable internet upload speed seems to be about the same as normal (around 200 Kb/s). This is puzzling to me. Back when I was using the secondary router for it's intended purpose as a DSL gateway under XP, I downloaded at around 300 Kb/s all the time with it using the same wireless card I am now, so I know the hardware I have is capable of it. Now both of our wireless cards are getting the same mediocre speeds (seemingly bottlenecked at around 90 Kb/s), even with a full signal (ie, the computer right next to the router). If we connect to the secondary router with a cable rather than wireless, there's no problem and downloads are really fast (note again though that the max upload speed doesn't seem affected whether wired or wireless, as determined by running internet speed tests in both configurations). Ping times over wireless are also extremely high - ie, 800ms+ even when pinging the main router at 192.168.1.1. It almost seems like there's something inferior or bottlenecked about the wireless signal the secondary router puts out, but I don't know what that could be or how to change it. (I also don't really understand anything about the setup I created here though, other than that I plugged it in and crossed my fingers and it works for basic, non-bandwidth-intense tasks).

So basically I'm curious whether there's a way to have normal access to the secondary router's settings in this setup, and whether there's a way to make the bandwidth over wireless less mediocre. Thanks!

---

### Post by knurledflanges on 2010-03-06
Alright, so it seems that the secondary router just configures itself automatically to act as a switch when set up in this configuration. I haven't been able to find any other explanation. 

It turns out that the speed and ping problems were only with my computer, and it seems that Ubuntu's default driver for my wireless card (RaLink RT2500) was faulty. I'm currently using the windows driver with ndiswrapper and it works at full blast.

---

### Post by Charly85551 on 2010-03-08
Sounds like a real challenge!
Your primary router IP = 192.168.1.1 - right? So your subnet behind is 192.168.1.0/24. If there is a fixed IP range - say from 192.168.1.2 till 192.168.1.20 then we will use for your purpose.
Your secondary router works in this subnet, therefore its address for the WAN-interface is to be set as static IP (fixed IP) to 192.168.1.10 as an example (hope nobody else is on this address!).
Your local network is then serviced by this 2nd router under a different subnet like 192.168.0.0/24 with the router acting on 192.168.0.1 and the rest of your PC's will be serviced with DHCP from this router. If you need you can tell your PC's the gateway- or DNS-address as being 192.168.1.1. If port forwarding is needed it needs to be activated and addressed from primary router to secondary router using 192.168.1.10 and additionally in secondary router to your local machine preferably with DHCP-reservation (= linked to MAC-address of your machine). This should work equally with wireless set-ups.
Hope I made it clear for you. Good luck!
cheers
Charly85551

---

### Post by knurledflanges on 2010-03-16
just in case anyone finds this with similar issues, i finally found buried in an FAQ page on actiontec's site that the dsl gateway i'm using as a router has a feature where it acts as a hub/switch when a cable modem is plugged into one of its ethernet ports, which i assume is what's also happening in my case, where i have it plugged into a router (which is getting its connection from a cable modem). the model is actiontec GT704WG.

---

