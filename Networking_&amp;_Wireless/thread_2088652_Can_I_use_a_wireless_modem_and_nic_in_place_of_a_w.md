---
title: "Can I use a wireless modem and nic in place of a wireless pci card ?"
date: 2012-11-27
forum: Networking &amp; Wireless
---

### Post by robert shearer on 2012-11-27
Complete novice about wireless setup/use.

I need a yes/no answer as to if what I want to do will work and if yes then what is the term for the setup so I can search for some information. 

I have a desktop pc connected by ethernet cable to a Modem/router/switch that came bundled with our connection. It has 802.11 b,g, and n capability but wireless is currently switched off.

I want to set up a pc in an outbuilding (20 metres, line of sight) and have another spare modem/router/switch (802.11 b,g) The pc has an ethernet card.

Can I connect the second modem to the second pc and use this to access the first modem wirelessly to get access to the internet ... ?

(otherwise I may have to dig a trench and do some cabling for wired access :-(   )

---

### Post by Statia on 2012-11-27
What you want is a wireless bridge, so your connection will look like this:

Internet
  |
your primary router - - - wireless bridge---- your 2nd PC
                        |
                   1st PC

(where | and --- is wired connection, - - - wireless)

I have a set-up like that here. (Except the wireless bridge is no longer in use, as I decided to install cat6 cable to take full advantage of an upgrade in speed by my ISP)
Most wireless routers don't have wireless bridging functionality, usually that is reserved for more expensive models. However, if your router can be flashed with dd-wrt, you can set up a wireless bridge. Google your (second) router model and dd-wrt to see if it will work, instructions for the setup of the bridge can be found on the dd-wrt wiki.

This is a cheap solution, that only costs time.
If your time is more valuable than your money, another option is to buy a wireless USB dongle. I have good experiences with a D-Link DWA-125, they can be had for under $15 on Ebay.

---

### Post by chili555 on 2012-11-27
You can also buy a wireless ethernet bridge. For many years, I used a similar device quite successfully.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833124338](http://www.newegg.com/Product/Product.aspx?Item=N82E16833124338)

---

### Post by robert shearer on 2012-11-27
Thank you both for your replies.
Now I know what it is I need to search for. Most helpful.

I have a box of older modems from a thrift store so will check them on the dd-wrt site.

Otherwise your recommendations for dongles are appreciated.
It helps immensely to know those products work with Ubuntu/linux.

---

### Post by robert shearer on 2012-11-28
> (otherwise I may have to dig a trench and do some cabling for wired access )
'Heigh Ho!, Heigh Ho! its off to work we go,
With a shovel and a pick and a ........
Heigh Ho!, Heigh Ho!, Heigh Ho!."

(With apologies to Walt)
[http://www.youtube.com/watch?v=fCJjJJRHA48](http://www.youtube.com/watch?v=fCJjJJRHA48)
1min 18 seconds.

---

### Post by Statia on 2012-11-28
> **robert shearer said:**
> 'Heigh Ho!, Heigh Ho! its off to work we go,
With a shovel and a pick and a ........
Heigh Ho!, Heigh Ho!, Heigh Ho!."


Well, a cabled connection is faster, safer and more stable and reliable than a wireless connection. That's why I drilled a hole in the ceiling to pass some cat6 through. Good thing I live in a house from the 1700's: not much concrete around :-)

---

### Post by coldraven on 2012-11-28
if your shed has AC power you could use powerline adapters. But I have heard that the speed can be lower than advertised due to your particular wiring setup.
[http://www.pcadvisor.co.uk/buying-advice/network-wifi/3370997/homeplug-powerline-networking-adaptors-buying-advice/](http://www.pcadvisor.co.uk/buying-advice/network-wifi/3370997/homeplug-powerline-networking-adaptors-buying-advice/)

---

### Post by irv on 2012-11-28
> **Statia said:**
> I have a set-up like that here. (Except the wireless bridge is no longer in use, as I decided to install cat6 cable to take full advantage of an upgrade in speed by my ISP)
I have a quick question about this statement. I just upgraded my Internet speed from 25 Mbps to 40 Mbps and checking my speeds the other day, I found my cat6 is giving me the full 40 Mbps, but my wireless is only 25 Mbps. I checked three devices on the wireless and it is about the same on all of them. My question is, is the wireless run that much slower then the wired?

---

### Post by Statia on 2012-11-28
> **irv said:**
> I have a quick question about this statement. I just upgraded my Internet speed from 25 Mbps to 40 Mbps and checking my speeds the other day, I found my cat6 is giving me the full 40 Mbps, but my wireless is only 25 Mbps. I checked three devices on the wireless and it is about the same on all of them. My question is, is the wireless run that much slower then the wired?

It depends on the wireless hardware you have, both sending (router) and receiving (laptop, smartphone) speed is determined by the slowest link.
Have a look at this table:

[http://en.wikipedia.org/wiki/IEEE_802.11#Protocols](http://en.wikipedia.org/wiki/IEEE_802.11#Protocols)

If you have Gigabit Ethernet hardware and cat5e or cat6 cable, your theoretical maximum is 1000 Mbps.

In my case, when my Internet speed was still 20/2, that matched the maximum speed my wireless bridge could deliver. When I got a free upgrade to 40/4, actual speed did not go up at my PC, because the bridge couldn't deliver and I switched to wired to get full Internet speed (and faster transfers to and from NAS).

---

### Post by irv on 2012-11-28
My Linksys 802.11G is rated at 6, 9, 12, 18, 24, 36, 48, 54 Mbps and I have my router set to auto which give me either 48 to 54 Mbps at any given time when I check it, but I still can't get more then 25 Mbps on wireless. My wire connetion is running at 40+ Mbps. Even my ISP can't figur out why I can't get up to 40 Mbps. They are going to come in next Friday to do some testing.

---

### Post by irv on 2012-11-28
Just for the record I saw this at [http://en.wikipedia.org/wiki/IEEE_802.11#Protocols]("http://en.wikipedia.org/wiki/IEEE_802.11#Protocols")
> 802.11g
Main article: IEEE 802.11g-2003

In June 2003, a third modulation standard was ratified: 802.11g. This works in the 2.4 GHz band (like 802.11b), but uses the same OFDM based transmission scheme as 802.11a. It operates at a maximum physical layer bit rate of 54 Mbit/s exclusive of forward error correction codes, or [COLOR="Red"]about 22 Mbit/s average throughput.[/COLOR][12] 802.11g hardware is fully backward compatible with 802.11b hardware and therefore is encumbered with legacy issues that reduce throughput when compared to 802.11a by ~21%
Notice the red text. I am wondering if this is what I am seeing.

---

### Post by Statia on 2012-11-29
> **irv said:**
> Just for the record I saw this at [http://en.wikipedia.org/wiki/IEEE_802.11#Protocols](http://en.wikipedia.org/wiki/IEEE_802.11#Protocols)

Notice the red text. I am wondering if this is what I am seeing.

That is quite possible. Remember that all those speeds are theoretical maxima and real world speeds are always (substantially) lower.

---

