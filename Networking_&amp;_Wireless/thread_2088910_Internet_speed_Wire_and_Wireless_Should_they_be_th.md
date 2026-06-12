---
title: "Internet speed: Wire and Wireless? Should they be the same?"
date: 2012-11-27
forum: Networking &amp; Wireless
---

### Post by irv on 2012-11-27
I am paying for 40 Mbps but I can't get it on the wireless. My question is should I get the same speed on wire and wireless?
[ATTACH]227847[/ATTACH]  [ATTACH]227848[/ATTACH]

---

### Post by CharlesA on 2012-11-27
The speed you get on wireless depends on your wireless signal, if there is interference, objects in the path and a bunch of other things.

It will not reach the same speed as a wired connection. Wireless G topped out at 54Mbps, but in normal operation you probably won't get very close to that unless you are in the area that is free of interference.

In other words, in theory, they should be the same speed, but in practice it isn't likely.

---

### Post by ahallubuntu on 2012-11-27
If you have a wireless N router and a wireless N card in your laptop, your chances of getting closer to 40Mbps improve.  It's probably not a good idea to read too much into advertised wireless router specs like "54Mbps" or "300Mbps."  Real-life wireless sustained wireless connection rates are nothing close to those.

Even if your supposedly have a 300Mbps wireless connection on 802.11n, in practice it will be much less than that - and worse depending on how far you are from the router, how much local interference there is, how good a router it is, how good a wireless card it is, etc.  Wireless connection quality fluctuates constantly.

The starting point should be checking your wired connection speed to the same point your wireless is coming from.

---

### Post by irv on 2012-11-27
I have a tech from my ISP coming in a couple of days to run some test on my Internet speeds, wire and wireless.
To day I check it on three different devices. Nook tablet, a Chromebook and my Laptop. They are were in the range of 22 to 25 Mbps. My desktop is about 35 Mbps because I am going through a router and then a switch. If I plug my Laptop in from a port off my router I can get the 40 Mbps.
I had my wireless router in a seperate room but I moved it into the room where I use most of my computers. It is very close to my Laptop most of the time so I get a good single. 4 to 5 bars.
[ATTACH]227861[/ATTACH]
EDIT: My Active Network Connections says 54 Mb/s
[ATTACH]227862[/ATTACH]

---

### Post by CharlesA on 2012-11-27
Hrm, the desktop should be getting 40Mbps even if the traffic needs to go thru the router and a switch. Mine is set up a similar way - one connection from the router to the switch, and everything is running off the switch.

Hopefully the tech can find an answer as to why your wireless is so bad.

---

### Post by irv on 2012-11-28
At first I thought it was my network card in my laptop, but I am getting the same speed with my Nook Tablet and my wife's Chromebook. I also have a Asus Transformer but it has Android 4.1 on it, so I can't get Flash to work to check the Internet speed. Yes, I hope the tech can find something.

---

### Post by kurt18947 on 2012-11-28
A simple thing to try would be to change channels on the wireless router/wireless access point.  One problem with wiFi is that most use 2.4 ghz. which is also used by a number of different devices such as cordless phones, baby monitors etc.  Even microwave ovens operate on the 2.4 ghz. bandwidth and have been shown to impact wireless network performance.   Sometimes changing channels will help.

You could also look at the wireless 'page' on your router. In my case I have an Actiontec that Verizon uses for their FiOS service.  I can choose 'compatibility' or 'performance'.  The difference being that 'compatibility' supports b, g, and draft n speeds.  'Performance' supports only draft n but I do find that in spite of only having 25 Mb./sec down internet,  'performance' feels faster than running in 'compatibility' mode.  Just some simple things to check.

---

### Post by chili555 on 2012-11-28
Some routers permit adjustment of the transmission rate. Make sure it is set to Auto and not some lower rate, for example, 24 Mbps. Please see attached.

---

### Post by SeijiSensei on 2012-11-28
One thing I learned recently is that wifi is a "half-duplex" service.  That means it cannot sustain traffic in both directions like full-duplex wired connections can.  Instead wifi has to "reverse the line" to send and reverse it again to receive.  This limits its speed in comparison to wired connections.

Other good suggestions have already been made like finding less crowded radio channels.  If you run 

```
sudo iwlist wlan0 scanning | grep Channel
```

you'll see the information for all the wifi nodes in your vicinity.  Pick a channel no one else is using.

---

### Post by irv on 2012-11-28
> **SeijiSensei said:**
> One thing I learned recently is that wifi is a "half-duplex" service.  That means it cannot sustain traffic in both directions like full-duplex wired connections can.  Instead wifi has to "reverse the line" to send and reverse it again to receive.  This limits its speed in comparison to wired connections.

Other good suggestions have already been made like finding less crowded radio channels.  If you run 

```
sudo iwlist wlan0 scanning | grep Channel
```

you'll see the information for all the wifi nodes in your vicinity.  Pick a channel no one else is using.

Here are all the wifi nodes in my vicinity:
> Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
Also here are my Advanced wireless setting.
[ATTACH]227878[/ATTACH]

---

### Post by irv on 2012-11-28
Just for the record I saw this at [http://en.wikipedia.org/wiki/IEEE_802.11#Protocols]("http://en.wikipedia.org/wiki/IEEE_802.11#Protocols")
> 802.11g
Main article: IEEE 802.11g-2003

In June 2003, a third modulation standard was ratified: 802.11g. This works in the 2.4 GHz band (like 802.11b), but uses the same OFDM based transmission scheme as 802.11a. It operates at a maximum physical layer bit rate of 54 Mbit/s exclusive of forward error correction codes, or [COLOR="Red"]about 22 Mbit/s average throughput.[/COLOR][12] 802.11g hardware is fully backward compatible with 802.11b hardware and therefore is encumbered with legacy issues that reduce throughput when compared to 802.11a by ~21%
Notice the red text. I am wondering if this is what I am seeing.

---

### Post by CharlesA on 2012-11-28
Could be. Basically for any transmission medium, you will have some overhead - my Wireless N router says it can transfer at 130Mbps, but I usually get around 65Mbps if I am lucky - usually less depending on if I am transferring a ton of small files or one large one. If I am doing file transfers, I use the wired connection. ;)

Internet browsing isn't affected, but that may be because I rarely use my laptop at home and my internet speed is only around 15Mbps.

---

### Post by ahallubuntu on 2012-11-28
FYI, you can probably upgrade the internal wireless card in your Dell laptop to an 802.11n card.  That will only help if your router is also 802.11n.  For about $10 on eBay you can get an Intel 5100 card.  Just verify that the existing card is not an 802.11n card first.

---

### Post by CharlesA on 2012-11-28
That would have to get a different router since their current one is a wireless G model.

---

### Post by irv on 2012-11-29
> **CharlesA said:**
> That would have to get a different router since their current one is a wireless G model.

I think I am going to look into a different router today. I been reading about routers at [http://en.wikipedia.org/wiki/IEEE_802.11#Protocols]("http://en.wikipedia.org/wiki/IEEE_802.11#Protocols") and I see the differences between the G and N routers. I have other devices on the wireless so if I upgrade my router I can see if it boost my speed. If this works I will look at changing my wifi card in my laptop.

---

### Post by pqwoerituytrueiwoq on 2012-11-29
you can try this [http://www.freeantennas.com/projects/template2/index.html](http://www.freeantennas.com/projects/template2/index.html)
if you are using a wireless desktop try making a cantenna for it
using encryption like WEP slows it down for me

---

### Post by irv on 2012-11-29
Been looking at this beauty. 
[ATTACH]227932[/ATTACH]
[http://reviews.cnet.com/routers/asus-rt-ac66u-802/4505-3319_7-35406080.html]("http://reviews.cnet.com/routers/asus-rt-ac66u-802/4505-3319_7-35406080.html")
A lot of good reviews at Amazon.
[http://www.amazon.com/RT-AC66U-Dual-Band-Wireless-AC1750-Gigabit-Router/dp/B008ABOJKS/ref=sr_1_1?ie=UTF8&qid=1354243788&sr=8-1&keywords=asus+rt-ac66u+router]("http://www.amazon.com/RT-AC66U-Dual-Band-Wireless-AC1750-Gigabit-Router/dp/B008ABOJKS/ref=sr_1_1?ie=UTF8&qid=1354243788&sr=8-1&keywords=asus+rt-ac66u+router")
It's hard to put out almost $200 for a router.

---

