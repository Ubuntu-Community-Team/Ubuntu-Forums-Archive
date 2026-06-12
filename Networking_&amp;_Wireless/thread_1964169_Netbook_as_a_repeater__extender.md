---
title: "Netbook as a repeater / extender"
date: 2012-04-23
forum: Networking &amp; Wireless
---

### Post by nukinfuts29 on 2012-04-23
I have a netbook that we no longer use running on Ubuntu. It is an asus eee....something. Anyway is it possible to use this to extend the range of a connection? I want to log it onto my home network in the basement and then broadcast a signal for my other laptop to grab onto.

I cannot plug it in via cable because my routers ethernet ports dont work. I'm too cheap to replace it.

---

### Post by |{urse on 2012-04-23
You'd need 2 wireless adaptors on that laptop in AP promiscuous mode, unless you have a old usb wireless adaptor (prism-based preferrably, probably impossible to find) you'll need to buy one (sicne you're 'too cheap' to buy a new router) I'll not continue this tutorial lol.

---

### Post by jonobr on 2012-04-23
Hello


Run a few Ethernet cables and get a small switch.
a 4 port switch on ebay will cost south of $50
[Saw this one for less then $10]("http://www.ebay.com/itm/Netgear-Model-FS608-8-Port-10-100Mbps-Fast-Ethernet-Network-Switch-w-WARRANTY-/380425189972?pt=COMP_EN_Hubs&hash=item58931bba54")
Not recommending you use this seller or site, but there are cheap options out there

---

### Post by |{urse on 2012-04-23
Much better idea ^_-

---

### Post by nukinfuts29 on 2012-04-24
If I was going to spend $50 I could just go to walmart and spend $30 on a range extender.

Can i connect the netbook to the router via wireless, and then connect my laptop to the netbook via ethernet?

---

### Post by jonobr on 2012-04-24
> I could just go to walmart and spend $30 on a range extender.

Thats a viable solution also, but working wireless to these device could be problematic


> 
Can i connect the netbook to the router via wireless, and then connect my laptop to the netbook via ethernet? 

Can you connect to your router via wireless from your basement in the first place?

If so then try using [ICS]("https://help.ubuntu.com/community/Internet/ConnectionSharing") to share the connection to the Ethernet interface

---

### Post by nukinfuts29 on 2012-04-25
Yes, the spot under the stairs has great signal from the wifi, I just need it on the other side of the basement. So maybe I can connect the netbook under the stairs and run a cable to the laptop from it.

---

### Post by jonobr on 2012-04-25
Yes

Try the ICS link I sent you.

Internet connection sharing works in windows pretty well, but takes a bit of effort in *nix.
You will see they talk about different interfaces,
pick the one right for you

---

