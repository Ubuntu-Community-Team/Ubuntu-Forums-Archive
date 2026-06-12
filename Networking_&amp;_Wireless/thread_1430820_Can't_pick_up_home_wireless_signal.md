---
title: "Can't pick up home wireless signal"
date: 2010-03-15
forum: Networking &amp; Wireless
---

### Post by eldonkr on 2010-03-15
For the past few months I've been using Ultimate Edition 2.3 on my laptop. Various problems I encountered convinced me to switch. I installed Ubuntu 9.10 today and after the install I can't pick up my wireless router on the list of available networks. I'm able to pick up every other one on my block, just not my own. My server and my roommates laptop can pick it up and are connected to it, the problem seems to be exclusive to this laptop with the fresh install on it.

I tried the 'connect to hidden network' option and it doesn't connect, it just keeps asking for the psk.

However, I can still hard line to the router and pick up internet just fine.

---

### Post by eldonkr on 2010-03-16
Is there anyone out there who can help me? After some googling I've come to the conclusion that my Netgear WNR1000v2 wireless router doesn't like linux.

It can't be the Airlink 101 150N adapter, it's picking up the signals from the neighbors.

---

### Post by oldefoxx on 2010-03-16
I'm sorry, I went down the same road a few months back, and finally got it to work, but there are several tricks involved, and I would have to find the thread and read through it to get a handle on it again.

What I can tell you is this:  It is do-able, but every wireless modem belongs to a family of chips, and you need the right drivers for that chipset.  That for a start.

There are a number of commands suggested for identifying where your wireless is situated in the laptop, meaning what port and all.
Things like lshw which lists your hardware, lsusb if the modem is USB configured on the laptop side, lspci if it is seen as a PCI device instead, ifconfig, and another wifeless manager that many find better, which is wicp.  You may need to ensure that the wireless is turned on by software, that the antenna is connected (there may be a switch setting for this), that power to the wireless adapter is on (another switch setting sometimes(, and eventually you get it all together.

The best thing it to not think of this as a Ubuntu thing, but as a Linux thing, and search by what you know about the wireless adapter (if you are not sure, check the OEM or vendor's sites(.

SourceForge has some surprisingly good tips, but finding them is not so easy.  I suggest using Ubuntu OR Linux in the searches, just in case someone else with Ubuntu has the same model laptop (or has the same wireless adapter in another model).

I can say that it can be done, but will likely take a small sequence of steps to get working the first time.  After that, it should pretty well work all the time.  So that is the good news.

The bad news it took me weeks to get mine up and running.  Lots of ideas out there, but getting the right combination in the right order can take a bit of work.  On the other hand, some claim that it wasn't that much time and effort involved.  I guess they just got lucky.

---

### Post by c0nfusedami on 2010-03-16
You tried connecting to a hidden network is your network set up to be hidden.

---

### Post by eldonkr on 2010-03-16
The problem does not lie in the usb adapter. If I was having a problem was with the adapter I wouldn't be able to pick up any of the neighbors signals. I can pick up every other signal on the block, just not my own.

My wireless is not set up to be hidden. 

When I try to connect to a hidden network and type in the information for my router it doesn't connect it just keeps asking me for my WPA/WPA2 over and over again, and I'm absolutely 100% sure beyond the shadow of any doubt whatsoever that I'm typing that in correctly.

---

### Post by Terzi on 2010-03-17
My desktop sometimes does the same if I have it set up to connect automatically. I found that if I deselect "connect automatically" and then turn the wireless off and on it will pick up the signal.

---

