---
title: "How to build a router"
date: 2009-07-11
forum: Networking &amp; Wireless
---

### Post by blazemore on 2009-07-11
I'm not sure if this is the right section; mods, please move this thread if it's not.


I want to build a PC to be used as a home server (NAS, media centre, torrent box etc) But I also want it to be a wireless router. is this possible?
Basically, the PC would connect to the Internet (ADSL) and then share the connection with other PCs wirelessly. Ideally it would support features such as port forwarding *and a web interface*.

I don't know much about ADSL connections as all I've ever had is cable (The router connects to the modem, which connects to the wall). I don't know much about ADSL so I don't know if this will be possible.

Can anyone point me in the right kind of direction for a project like this? Specifically hardware and software to use?

Thanks!

---

### Post by blazemore on 2009-07-12
12 hr bump (sorry)

---

### Post by bernied on 2009-07-12
> **blazemore said:**
> I'm not sure if this is the right section; mods, please move this thread if it's not.


I want to build a PC to be used as a home server (NAS, media centre, torrent box etc) But I also want it to be a wireless router. is this possible?
Basically, the PC would connect to the Internet (ADSL) and then share the connection with other PCs wirelessly. Ideally it would support features such as port forwarding *and a web interface*.

I don't know much about ADSL connections as all I've ever had is cable (The router connects to the modem, which connects to the wall). I don't know much about ADSL so I don't know if this will be possible.

Can anyone point me in the right kind of direction for a project like this? Specifically hardware and software to use?

Thanks!
This is all possible. Here's someone else with similar ideas:
[http://ubuntuforums.org/showthread.php?t=376283](http://ubuntuforums.org/showthread.php?t=376283)

That person used a very old PC, so you don't need much in the way of hardware. Your torrent software will be the most demanding of all the things you mention, unless you have lots of people accessing the webserver. The fileserver (samba?) doesn't use much resource. If in doubt, you can run all the software on another machine before you start, to see how much resource it might need.

I'd suggest you build it next to your existing setup, don't try to make it all work at once. And use two wired network interfaces to test your routing, so you're not trying to get the routing and the wireless stuff right at the same time. You can get a spare wired NIC for pennies.

---

### Post by blazemore on 2009-07-14
Right, thanks for this. I'll have a look at it when I get some time, as it looks like my most ambitious project yet.

---

