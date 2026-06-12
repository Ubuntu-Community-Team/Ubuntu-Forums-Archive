---
title: "Mythbuntu 16.04 Ethernet"
date: 2016-04-28
forum: Mythbuntu
---

### Post by clueo8 on 2016-04-28
I installed the latest Mythbuntu 16.04 (MythTV 0.28) from the ISO and noticed that my Ethernet (Wired) was not working after the install.  I had to manually go into /etc/NetworkManager/NetworkManager.conf and change managed to true (it was set to false):

```
[ifupdown]
managed=true

```

And then restart the network-manager service and it worked by configuring the wired connection using the network icon near the top right (clock area).  I noticed that my Wireless connection was okay, but just the Wired required this additional step.  Did anyone else run into this issue?

I've installed this on two different machines and experienced the same with both, I have filed a bug report: [https://bugs.launchpad.net/mythbuntu/+bug/1576668]("https://bugs.launchpad.net/mythbuntu/+bug/1576668")

---

