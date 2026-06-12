---
title: "How to set up wireless repeater in Ubuntu 9.04?"
date: 2009-06-17
forum: Networking &amp; Wireless
---

### Post by otakuj462 on 2009-06-17
Hi all,

I have an old laptop which I would like to set up as a wireless repeater. The configuration is simple: I have one Wireless NIC that connects to a wireless router, and I have another wireless NIC that I would like to re-broadcast the signal. I've done this before with brutils, as well as various front-ends that help set up masquerade, but I used all of these techniques in the days before Network Manager 0.7. Network Manager 0.7 seems to have subsumed some of these responsibilities on Ubuntu 9.04, and I so I was wondering how best I should set this up with respect to the technology shipping in Ubuntu 9.04. To start, it seems like I have two main options:

1. Disable Network Manager and use the old tools (editing /etc/network/interfaces, and/or setting up masquerade). If I do this, could anyone tell me how to disable Network Manager?

2. User Network Manager to set up the machine to act as a repeater. It's not clear how I would do this, though, as it does not appear as though Network Manager allows you to configure a wireless profile specific to a particular NIC. If there were a way to set up a profile for a particular NIC, that would probably do the trick, as it appears as though Network Manager offers the ability to create a new wireless network, thus sharing an existing internet connection.

I'd appreciate any advice anyone can offer on the best way to set this up in Ubuntu 9.04.

Thanks,

Jake

Update: I see now that when you have two wireless NIC's, the NM dialog gives you the option to select one NIC on which to create the network. So, there's no issue there.

I currently have this setup almost working perfectly. I have the connection shared between my two NIC's. The only problem is that DNS masquerade does not seem to be working correctly, as I can connect to my repeater and navigate to [http://72.14.205.104/](http://72.14.205.104/) in Mozilla, but the same thing does not work when I attempt to navigate to [http://www.google.com](http://www.google.com). To confirm this, I edited /etc/resolv.conf and set the contents to be the same as the resolv.conf file on my repeater. After that, all hostnames resolved correctly on the computer behind the repeater. This is all on Ubuntu 9.04. Could anyone tell me what I need to do to troubleshoot this?

I'd greatly appreciate any guidance anyone can offer. Thanks,

Jake

---

### Post by Zorael on 2009-06-25
Do you have a guide on how to set up the other solutions you mention? I'm in a similar situation; I have a machine with two wireless cards and I want it to act as a wlan repeater.

---

### Post by otakuj462 on 2009-06-25
I ended up ditching NetworkManager and using the following guide:

[http://ubuntuforums.org/showthread.php?t=335465]("http://ubuntuforums.org/showthread.php?t=335465")

There were a few other quirky things I had to do to make it work. Here's the full story:

The above instructions worked well at first, but stopped working on reboot, and I could never reproduce my success. I think the reason for this was that one of the NIC's was an [EUB-362]("http://www.keenansystems.com/nub362_eub362_linux_ndiswrapper_driver_howto.htm") which I was using under NDISWrapper, and one of the quirks to using it was that in order for it to work, it had to be hotplugged and couldn't be coldplugged. I think this was confusing the dhcp server (it wasn't able to find the device on boot), so I decided to switch the roles of the NICs: the EUB-362 would connect to the network, and the other card, a prism-based PCMCIA card, would share internet and act as dhcp server. 

Unfortunately, the p54 drivers didn't work well with my card in ad-hoc mode (I couldn't assign it a static IP address when it was in ad-hoc mode, see this [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/389545")), so I rolled back to the older prism54 driver, which, among other improvements, allowed me to put the card in Master mode, as well as assign it a static IP address.

After that, for some reason my iptables configuration was a bit confused, and I couldn't figure out how to permanently reset it (flushing iptables didn't persist through the next reboot), so I ended up using Firestarter iptables front-end to set up simple internet connection sharing. This worked fine, and has continued to work fine, except for the fact that the firewall is very restrictive, and has blocked ssh access to the box, which is somewhat annoying as it is currently headless (I don't have an external monitor for it). 

Good luck,

Jake

---

### Post by mikilion on 2010-04-01
Hi all,
I would like to install Ubuntu on a desktop PC and plug in a 802.11N wireless PCI network card in repeater mode to extend the wireless range of my router/modem.
I have a router/ADSL modem with Broadcom BCM4318e wireless module, what's the best PCI wireless card suited for my purpose?

---

### Post by mikilion on 2010-04-02
Bump

---

### Post by mikilion on 2010-04-12
Bump

---

