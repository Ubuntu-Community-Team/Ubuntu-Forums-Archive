---
title: "Internet stopped working after forced reboot"
date: 2009-06-17
forum: Networking &amp; Wireless
---

### Post by corwinspyre on 2009-06-17
Hiya!

I was cleaning my laptop (i.e. the outside), looked up, and saw somehow a ton of firefox windows opened, enough that my computer wouldn't respond.  I tried hitting the switch on my laptop to turn wireless off, as well as other things, but it wouldn't respond, so I held the power button to shut it off.  When I started it again, it connected to my wireless router as usual, but I don't have Internet access.  

Ifconfig shows I have a local ip address. It shows a bunch of error packets on the TX packets line.

Other computers are using wireless fine, so it's definitely local to the computer.  

I'm on an HP Pavilion tx2500z, which lspci reports uses for a wireless card BCM4312 rev 1 using the wl driver, and I'm using Jaunty/9.04.

Anyone have an idea on how to fix this?  Thank you very much, as I am very confused (and frustrated) as to why I can't access the Internet.

edit:  One more thing.  When I try to ping my wired router (which is the first thing after my modem) via "ping -c 1 192.168.1.1" or with sudo at the beginning, I get the error: "ping: sendmsg: Operation not permitted".  Also, although network-manager comes up with the message saying it's connected to my wireless router, iwconfig says it isn't associated with an access point.

---

### Post by corwinspyre on 2009-06-17
I'vebeen playing around some more and noticed a few more things.  The ip address on my wireless is the one it was before the problems, so I'm not sure it's being assigned it.

When I run iwlist scan, it says for my wireless card 'Interface doesn't support scanning'.

In dmesg, I notice unlike my wired connection that says 'eth0: link down', my wireless interface says 'eth1: no IPv6 routers present'.  Could that be the problem?  Adding to the confusion, I have had ipv6 blacklisted since before upgrading to Jaunty.

---

### Post by corwinspyre on 2009-06-18
One more update: it's not specifically the wireless.  I plugged a network cord in, and it said it was connected and even assigned a local ip, but I can't get Internet, ping my lan, etc., from the wired connection.

---

### Post by sickofthesea on 2009-06-21
I have a E160G mobile broadband dongle and I am running jaunty. After an update my internet just stopped working. The modem apparently connects in network manager and the lights on the modem show that it is connected but I can't get any web pages or e-mail at all.

The update included a kernel update and I've tried going back to the previous kernel and it's still the same. So I'm assuming it is not a kernel issue but something else. I am writing this only by installing Windows on a spare bit of drive and connecting. The modem works perfectly under Windows.

I am away from home at the moment, but 5 days ago just before I left, my other laptop lost internet connection showing these same symptoms, also running jaunty, also after an update but that was a wireless connection to my router, not a mobile broadband stick.

So I am completely lost on this one. It's a real pain. Something has a bug in it somewhere and I haven't a clue where to begin to look.

Martin

---

### Post by sickofthesea on 2009-07-08
It was just too much of a show stopper. I've abandoned ubuntu :-(

---

