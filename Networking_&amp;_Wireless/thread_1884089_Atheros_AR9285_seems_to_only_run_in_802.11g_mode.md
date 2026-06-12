---
title: "Atheros AR9285 seems to only run in 802.11g mode?"
date: 2011-11-20
forum: Networking &amp; Wireless
---

### Post by Leaena on 2011-11-20
I'm sorry if this issue has been posted before, but I couldn't find anything in a quick search. 

I have an HP DV4-2014nr laptop running Ubuntu 10.10 with an Atheros AR9285 Wireless Network Card. The last few weeks I've been troubleshooting an issue with our router (which is a Linksys WRT310 802.11n), and last night I came across an interesting anomaly.

All the computers in the house were having connection/throughput issues, so I had spent most of the day diagnosing signal strength and finally logged into the router. There are several 802.11g devices on our network, so I knew the router had dropped to running at the G Standard rates, and decided to disable Mixed Mode to see what sort of difference it would make.

As soon as I turned off G Transmissions, my laptop lost it's connection to the internet, and I was only able to reconnect after hardwiring into the router and changing it back to Mixed Mode. Yet the AR9285 is a 802.11b/g/n card? It seems like, for one reason or another, my wireless card is running in 802.11g mode, and I can't figure out why or how to diagnose the issue?

Could this be a driver issue, or something along those lines? I can't seem to find a way to check the wireless card's settings (and I honestly have no idea how to do that in Ubuntu), so any help I could get would be greatly appreciated. 

I was hoping to upgrade the network hardware in the next few months and install additional Access Points, but there's no real point in spending the money if I'm not going to get N Transmission Rates.

Anyone?

Edit: (I believe my driver for this card is the ath9k?)

---

### Post by Leaena on 2011-11-20
After doing a bit more research, I haven't found anything that actually suggests Ubuntu *supports *802.11n. Is this the case, and might that be why I am unable to connect to my router when it's not set to Mixed Mode? 

Can anyone confirm this?


After scouring the Internet for more information on 802.11n support in Linux/Ubuntu, it would seem that there has been support integrated for Atheros cards in ath9k. I'd still like someone to confirm this, but if this is the case, then why would I not be able to get an 802.11n connection? 

If my interpretation is correct, and there has been support for N-Transmissions in the ath9k driver, then this leads me to wonder if the driver itself (which I know is present on my system, and supposedly being used, but I don't know how to tell for sure) is configured properly and actually being used.

---

### Post by Leaena on 2011-11-20
Sorry for the multitude of posts, I'm just trying to provide as much detail as possible.

When I run the command ```
 sudo lshw
```This is what it gives me:


 ```
*-network
                description: Wireless interface
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: wlan0
                version: 01
                serial: 90:4c:e5:2c:fe:f5
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=2.6.35-30-generic firmware=N/A ip=192.168.1.100 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn

```

---

### Post by Leaena on 2011-11-20
Hey everyone, just a short update:

After quite a bit of work, I managed to dig up countless references to an issue with the ath9k driver connecting to 802.11n networks and it would seem to be a very common one across multiple distributions, and spanning the course of several years now. 

There was even a bug report about the issue on launchpad, which seems to have been promptly ignored. 

I'm highly disappointed that this hasn't been resolved, and virtually every post I found in this forum in particular had absolutely no reply or the only replies were by others with the exact same issue. This is obviously a recurring issue with the ath9k driver which is *supposed* to support 802.11n. 

If anyone can suggest a workaround in the meantime, I'd be greatly appreciative.

---

