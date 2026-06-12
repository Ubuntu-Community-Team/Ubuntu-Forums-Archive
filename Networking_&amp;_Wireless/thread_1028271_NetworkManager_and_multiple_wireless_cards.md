---
title: "NetworkManager and multiple wireless cards"
date: 2009-01-02
forum: Networking &amp; Wireless
---

### Post by grimmeissen on 2009-01-02
I am using Xubuntu 8.10 which comes with the network-manager-gnome applet.  I have been googling and searching for a while and I can't seem to find a solution to this problem.

I'm using a Dell laptop that has an internal wireless card installed, but that card is an old 802.11b and is too slow for some things I need to do with it.  I have a separate wireless card installed in my PCMCIA slot that uses the atheros drivers.

When I was running Kubuntu, I could configure the ath0 device to start by default instead of eth1 (the internal card), but under Xubuntu the network manager does not seem to be so sophisticated.

When I create a wifi device in network manager, it does not ask me to choose a device to associate with the connection.  It just creates a generic wireless connection setting.  So when my computer boots up and wireless kicks in, I get a connection on both cards.  They both compete with each other and I get really shotty performance.

What I want to be able to do is disable the internal wifi card or at least just tell Network Manager to connect to the ath0 device by default if it exists and not connect to the other one.

Any help would be greatly appreciated.

---

### Post by grimmeissen on 2009-01-02
Well, I did get my problem solved, but I'm not sure if this is the best way.

Anyway, since I'm runing Xubuntu I didn't have the gnome-network-admin tool.  So I installed that to give me a graphical interface for managing network devices.  I turned off roaming mode on the eth1 device and this caused Network Manager to no longer be able to manage it.

It accomplishes what I need.  Network Manager establishes the wireless connection on ath0 and no longer does anything with the internal card.

If I am ever somewhere where I don't have the PCMCIA card plugged in, I'll have to setup networking manually to re-enable the internal card.

---

### Post by superprash2003 on 2009-01-02
if problem is solved.. mark thread as SOLVED

---

