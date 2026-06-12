---
title: "Connection to multiple networks and sharing internet"
date: 2009-08-10
forum: Networking &amp; Wireless
---

### Post by geear on 2009-08-10
Hello!

I've had a couple network problems and tried to solve them myself, but I'm afraid I've just made it worse!

I have a desktop computer running Kubuntu 9.04. I have a wireless USB adapter that just worked when I hooked it up, no trouble there and I've been using it for several months without problem.

Now I have a couple additional computers that don't have wifi, these 3 computers are connected through a wired connection.

First problem: I can't get my desktop computer to connect to both networks at the same time. I tried running this pppoe config command that was suggested to someone else, but that caused my desktop machine to stop getting an IP address automatically from wifi hub (this is still broken and I had to input an IP address manually to get back online). So if I connect to the wired connection my wifi drops and if I connect to the wifi my wired connection drops. Before doing the PPPOE config thing I could connect to both, but my internet wouldn't work when both were connected.

Second problem: I'd like to share my internet to these other computers once I'm able to connect to both networks.

Sorry about the complex mess which I probably made worse.

And thanks a ton for the help!!

Also, I have WICD installed.

---

### Post by Iowan on 2009-08-10
Where did you configure PPPOE? Coming from a Gnome background (that should serve as a warning), NM only manages one connection at a time, so "the other" connection should be set up in */etc/network/interfaces*. Your (Kubuntu) mileage may vary.

---

