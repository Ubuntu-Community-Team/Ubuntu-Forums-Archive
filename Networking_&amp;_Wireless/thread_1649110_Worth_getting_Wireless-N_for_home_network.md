---
title: "Worth getting Wireless-N for home network?"
date: 2010-12-19
forum: Networking &amp; Wireless
---

### Post by mmad on 2010-12-19
My Media Centre Box/File server runs Ubuntu 10.10 and is connected via Ethernet to my router. I've also got 2 laptops, one which has a wireless n card, and the other which doesn't, but has a wireless n dongle if necessary. Currently I stream media from my file server to my laptop and I get approximately 1.8Mbps, which seems fine usually, but occasionally I get a little bit of stuttering when there's a lot of wireless stuff going on.

I was wondering if anyone thought that upgrading my router to wireless N was a good idea (since routers aren't that expensive) and approximately how much of a transfer speed increase I could get. This could potentially make it easier to sync files from my laptop to the main server, but if its only a small change then its not worth it.

Thanks in advance for your input on this.

---

### Post by walt.smith1960 on 2010-12-19
For me it was worth the upgrade.  I upgraded my broadband service to 30 Mb/sec.  My Wireless N devices would show that on a speed test, my G devices maxed out at 18 Mb./sec.  Neither G nor N devices will run at their theoretical maximums.  I'm running a mixed environment because i have Wireless G devices that can't be upgraded but for me Wireless N was worth it. An added bonus is that Wireless N devices seem to use MIMO which help with signal strength.  Even the mini USB adapters have very good signal strength.

---

### Post by mmad on 2010-12-20
Signal strength isn't a major concern for me at home, it all seems just fine. I'm more about transfer speeds. For example connected via ethernet, I can internally transfer to the server at around 12MB/sec, but wirelessly I get just 1.8MB/sec. By using wireless N, will that 1.8MB/sec increase to a speed which makes an upgrade worthwhile? Theres a lot of conflicting information out there, and thats why I'm trying to look for personal opinions rather than just google for the answer.

Regards,

---

### Post by Boondoklife on 2010-12-20
I noticed no one asked you the speed of the current routers ethernet ports. If you router is only 10/100 capable and your media server is connected to it via a 1000mb nic then a new router would give you a nice increase.

Not only would your wireless get an upgrade, but so would any wired devices.

---

### Post by walt.smith1960 on 2010-12-21
1.8MB is slow for a G device.  I wonder if you're getting interference from another device.  Cordless phones & microwave ovens among other devices  can radiate at around 2.4 Ghz, same as WiFi G & 150 N.  Devices capable of N300 use dual frequencies, 2.4 Ghz & 5 Ghz. Would it be possible or worthwhile to disconnect possible offenders and recheck your wireless throughput?

---

### Post by Eaglebird on 2010-12-21
If all of your wireless devices support 802.11G, change your access point to G only if it's in mixed b/g, and see if you get any better throughput.

Further, if you're analyzing bandwidth throughout your network, you need to look at bottlenecks in/on the machines themselves, not just the network, a few that come to mind being:
-The PCI bus tops out right below 1Gbps (33MHz * 32bits)
-IDE drives tend to run at either 100 or 133 MB/s or 0.8 to 1.03 Gbps. A channel occupied with a master and slave will effectively halve this (~400Mbps).
-Anything attached to the PCI bus will run less than 1Gbps, SATA included. Boards that have SATA capability but no PCI Express (e.g. serial) capability simply have SATA controllers attached to the PCI bus.
-A lot of systems tend to be conservative with bandwidth and headroom.

The choice to upgrade should be based on a few things;
1) Do you have the money? (this should be pretty obvious to anyone)
2) Will it make a difference? (Are you seeing things top out at x Mbps because there's no more bandwidth available or because something is imposing a limit that you can change, on it?)
3) Will something else become a bottleneck? (Do you have another device somewhere that will inhibit the machine from actually getting to N speeds? (Maybe that Wireless N dongle?))
4) Do you think it's worth it? (Is dropping $XYZ on a new piece of hardware worth the possibility that you'll get better performance?)


In my opinion, though, I would say you should get one, or possibly wait until Christmas passes and see if you can grab one for cheap. If something else ends up being a problem, you ca take it on as it comes up.

---

### Post by Boondoklife on 2010-12-21
Just watch ebay, I just picked up a WRT320n for $22 and free shipping. I get about 1.2 - 1.7MBps on my g network too. This is not too bad considering it is 802.11g we are talking about.

Take a look [[here]("http://www.passmark.com/support/wireless_bandwidth_testing.html")], they get about the same.

---

### Post by mmad on 2010-12-28
Sorry for the late reply guys, Christmas and all that :p

> **walt.smith1960 said:**
> 1.8MB is slow for a G device.  I wonder if you're getting interference from another device.  Cordless phones & microwave ovens among other devices  can radiate at around 2.4 Ghz, same as WiFi G & 150 N.  Devices capable of N300 use dual frequencies, 2.4 Ghz & 5 Ghz. Would it be possible or worthwhile to disconnect possible offenders and recheck your wireless throughput?

There are a LOT of wireless access points in my area. I think that it is unlikely that there is inteference within my own home, and its more likely that its the result of the other routers in range.  

> **Eaglebird said:**
> If all of your wireless devices support 802.11G, change your access point to G only if it's in mixed b/g, and see if you get any better throughput.

Further, if you're analyzing bandwidth throughout your network, you need to look at bottlenecks in/on the machines themselves, not just the network, a few that come to mind being:
-The PCI bus tops out right below 1Gbps (33MHz * 32bits)
-IDE drives tend to run at either 100 or 133 MB/s or 0.8 to 1.03 Gbps. A channel occupied with a master and slave will effectively halve this (~400Mbps).
-Anything attached to the PCI bus will run less than 1Gbps, SATA included. Boards that have SATA capability but no PCI Express (e.g. serial) capability simply have SATA controllers attached to the PCI bus.
-A lot of systems tend to be conservative with bandwidth and headroom.

The choice to upgrade should be based on a few things;
1) Do you have the money? (this should be pretty obvious to anyone)
2) Will it make a difference? (Are you seeing things top out at x Mbps because there's no more bandwidth available or because something is imposing a limit that you can change, on it?)
3) Will something else become a bottleneck? (Do you have another device somewhere that will inhibit the machine from actually getting to N speeds? (Maybe that Wireless N dongle?))
4) Do you think it's worth it? (Is dropping $XYZ on a new piece of hardware worth the possibility that you'll get better performance?)

In my opinion, though, I would say you should get one, or possibly wait until Christmas passes and see if you can grab one for cheap. If something else ends up being a problem, you ca take it on as it comes up.

The hard drives are SATA, and all my pcs support a 1000Mbps ethernet speed. I think I'm going to upgrade because I think any speed increase will be worth it & also quite frankly my current router is a piece of garbage.

---

### Post by Boondoklife on 2010-12-28
What protocol do you use to stream your media? FTP, SMB, HTTP, etc. 

Also have you tried other channels? I get crap for signal on 1, 6, and 11 but excellent on 3! Try to do a wireless scan to see who is around you and what channels they are on and then pick a channel that is between two weak signals.

Here is a great site for bandwidth number and what not.
[http://web.forret.com/tools/bandwidth.asp?speed=24.7&unit=Mbps](http://web.forret.com/tools/bandwidth.asp?speed=24.7&unit=Mbps)

What router do you have?

---

### Post by mmad on 2010-12-28
> **Boondoklife said:**
> What protocol do you use to stream your media? FTP, SMB, HTTP, etc. 

Also have you tried other channels? I get crap for signal on 1, 6, and 11 but excellent on 3! Try to do a wireless scan to see who is around you and what channels they are on and then pick a channel that is between two weak signals.

Here is a great site for bandwidth number and what not.
[http://web.forret.com/tools/bandwidth.asp?speed=24.7&unit=Mbps](http://web.forret.com/tools/bandwidth.asp?speed=24.7&unit=Mbps)

What router do you have?

Um http? I just browse the samba shares in the file explorer and play them like that. My router is an O2 Wireless Box II - its the one my ISP gave me when I joined. Perhaps you're right though, some trial and error could improve connectivity.

---

### Post by Boondoklife on 2010-12-28
ok you are using samba then, your rate of 1.8MB/s is spot on for 802.11g. If you upgrade to N you should see a very nice boost in speed, just make sure the wired ports are all 1Gbit connections.

---

### Post by mmad on 2011-02-15
Hi guys, sorry its been so long but I've been so busy with uni work that I haven't had time to attend to this network stuff. Now that I have a little bit of free time, I'd like to go ahead and do the upgrade asap.

I've been looking for routers and stuff, but I cant seem to find a good one - it seems to be a hit or miss on any one piece of hardware.

So to reiterate, I've got a server and desktop machine connected via ethernet. They both have gigabit interfaces but my router can only do fast ethernet at max. I also have 2 laptops, one that has wireless b/g/n capability and the other that's wireless b/g.

I want a router to be a cheap as possible but still support a gigabit interface and be a modem/router in one.

These are the two I am looking at, at the moment:
[http://www.amazon.co.uk/D-Link-DIR-655-Wireless-Gigabit-Firewall/dp/tech-data/B000PLSAII/ref=de_a_smtd](http://www.amazon.co.uk/D-Link-DIR-655-Wireless-Gigabit-Firewall/dp/tech-data/B000PLSAII/ref=de_a_smtd)

[http://www.it247.com/product/1/BELNT208/F5D8232UK4-Belkin-N1-Vision-wireless-router-802-11b-g-n-draft-desktop.html?mc=FR-P-NetworkStorageComms-F5D8232UK4](http://www.it247.com/product/1/BELNT208/F5D8232UK4-Belkin-N1-Vision-wireless-router-802-11b-g-n-draft-desktop.html?mc=FR-P-NetworkStorageComms-F5D8232UK4)

I've read many reviews online, but I thought I'd ask for your opinion before I bite the bullet and buy one. I am steering towards the IT247 one at present.

---

### Post by Boondoklife on 2011-02-15
A linksys N130 flashed with ddwrt runs my network. it does gigabit and b/g/n wireless.

I got one on ebay for about 30 dollars not to long ago.

---

### Post by mmad on 2011-02-16
> **Boondoklife said:**
> A linksys N130 flashed with ddwrt runs my network. it does gigabit and b/g/n wireless.

I got one on ebay for about 30 dollars not to long ago.

I googled this model, but it doesn't seem to exist :S.

---

### Post by Boondoklife on 2011-02-16
Sorry, my dyslexia kicked in, it is 130N; WRT130N to be exact.

---

