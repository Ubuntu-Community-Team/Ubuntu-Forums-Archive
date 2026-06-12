---
title: "Network Manager - all users by default"
date: 2012-03-20
forum: Networking &amp; Wireless
---

### Post by ajarmoniuk on 2012-03-20
Hi,

Somehow whenever I want to setup a new wireless connection or when I want to connect to a new wifi network, network manager assumes that I want to allow the network for all users (available to all users is checked by default) and it asks me for my password first (before even displaying the settings window).

It didn't use to be like that when I first installed Ubuntu and I wonder if it's possible to change back to the default behaviour.

I don't like to be asked for my password each time I want to connect to a new network (I still remember that Linus rant, I have the same now).

---

### Post by uteck on 2012-07-13
Nope, it seems that for some stupid reason the network manager folks have decided that you have to have sudo rights to connect to a wireless access point.  They want to store all wifi settings in /etc/NetworkManager/system-connections/ and share them by default with all users on the system.

I am looking into Wicd as a replacement for NM.  Or I need to set sudo for network-manager so anyone can run it.  Not that safe, but better then putting everyone in the sudo group like the NM devs recommend.

---

### Post by hovrashko on 2012-07-13
That is a good point, is there they way to get rid of that security window?

---

