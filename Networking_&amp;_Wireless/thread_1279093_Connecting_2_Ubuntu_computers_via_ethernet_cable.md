---
title: "Connecting 2 Ubuntu computers via ethernet cable?"
date: 2009-09-30
forum: Networking &amp; Wireless
---

### Post by Gogeden on 2009-09-30
How do I connect a desktop pc with Ubuntu Jaunty on it to my laptop  which also has Ubuntu Jaunty on it so that I can use my laptop as a sort  of wireless router so I can get updates on my desktop? Thanks! ^_^

I have 2 straight through cables and a switch


Also, do I have to give either computer a manual IP?


Please help with detail! ^_^ Thanks again! :lolflag:

---

### Post by doas777 on 2009-09-30
> **Gogeden said:**
> How do I connect a desktop pc with Ubuntu Jaunty on it to my laptop  which also has Ubuntu Jaunty on it so that I can use my laptop as a sort  of wireless router so I can get updates on my desktop? Thanks! ^_^

I have 2 straight through cables and a switch


Also, do I have to give either computer a manual IP?


Please help with detail! ^_^ Thanks again! :lolflag:

you have to configure IP on both PCs.

I would suggest these settings:
PC1:
address: 192.168.1.1
mask: 255.255.255.0

PC2:
address 192.168.1.2
mask: 255.255.255.0

if you are required to use a gateway, just use the local ip. 
that should do ya for network connectivity.

now, what do you want to do with these networked computers? IP will get you ping, but not much else, unless you install and configure network services.

---

### Post by Gogeden on 2009-09-30
Thanks for the info


I want to connect the desktop to my laptop and then use my laptop as a wireless router so that data will go from my ACTUAL wireless router, through my laptop, and into the desktop. I'm working on a buddy's computer and I want to get all the updates and codecs for it ^_^

---

### Post by Iowan on 2009-09-30
[Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is a help page for connection sharing - near the end is [this]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless") link to a wireless sharing page.

---

### Post by MadeTheSwitch on 2009-09-30
And you should be using a "cross" cable - otherwise both computers will have their send and transmit wires on the same side, making the connection fail.

The easiest way to know if a cable is "straight" or "cross" is by holding both ends of it next to each other. If the wires are arranged in the same pattern left-to-right, then it's a straight. If 2 or 4 of them are switched, it's a cross. You need the latter.

---

### Post by Iowan on 2009-09-30
> **Gogeden said:**
> I have 2 straight through cables and a switchThat should work, too.

---

