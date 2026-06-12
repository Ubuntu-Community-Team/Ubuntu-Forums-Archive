---
title: "Wireless connection to internet &amp; wired connection to NAS"
date: 2010-02-22
forum: Networking &amp; Wireless
---

### Post by mykurtaccount on 2010-02-22
Hello,

My computer if no where near where my router is so I connect wirelessly. I also have a NAS directly connected by cable to my computer using eth0.

With the network manager installed by default I had got this working i.e. having both a wireless and a static wired connection both up and working at the same time...

.....but I was having the same problems as a lot of other people in that my wireless connection repeatedly disconnected. The answer seemed to be to install WICD network manager. This I did (and in the process uninstalled the default nettwork manager). This has solved my random wireless disconnects...

....but WICD doesn't seem to allow two network connections connected at the same time. I fill in my static info. for the "Wired Network", press connect and it promptly disconnect my wireless connection.

Any help would be appreciated.

---

### Post by Iowan on 2010-02-22
I've never used WICD, so I don't know how it reacts to interfaces configured via */etc/network/interfaces* Otherwise, try setting up the wired connection there.

---

