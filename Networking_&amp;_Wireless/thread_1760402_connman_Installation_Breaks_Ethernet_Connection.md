---
title: "connman Installation Breaks Ethernet Connection"
date: 2011-05-16
forum: Networking &amp; Wireless
---

### Post by andymandias on 2011-05-16
I was browsing the available packages to install the weather indicator and noticed that a network indicator was available. apt-get said that it needed to install 'connman' and remove 'network-manager' and 'network-manager-gnome' in order to install the network indicator.  I foolishly assumed it knew what it was doing so I went ahead and performed the installation/removal and restarted the computer.

Now I cannot connect to the internet.  I only have an ethernet card for connection to the internet, no wireless or otherwise.  The configuration I use is not DHCP, but a manual settings of address/subnet/gateway and name servers

When I try to set the network values through the network indicator some of them do not stay set.   The gateway value appears to be set, but then after closing down the indicator window completely it comes up with the value 'Modified'.   The DNS servers is the only other value that does not stay set, but it only changes to be blank.  The connection never works.

So, I downloaded 'network-manager' and 'network-manager-gnome' on another computer, transferred the packages by USB, and reinstalled them (uninstalling connman and the network indicator).  But the network connection remains broken.  At least with 'network-manager-gnome' the values I set stay set, they just don't work anymore.  I've tried editing /etc/network/interfaces to previously working values directly, but they do not seem to have any effect either.  The connection no longer works.

I really do not care if I use the network indicator or not at this point, I simply want the network connection to work properly.  Please, any help would be greatly appreciated.

Edit:  I realize I forgot to say that I'm using Ubuntu 11.04 (upgraded from 10.10).  The network card is the "Integrated Broadcom® 57780 Gigabit Ethernet controller".

---

### Post by andymandias on 2011-05-17
Turns out connman overwrites /etc/resolv.conf as well with garbage, removing my DNS server list.  So, after removing connman and reinstalling network-manager and network-manager-gnome, I had to fix this file as well as /etc/network/interfaces.

Why the Network Connections preference window/manager setting for DNS servers does not actually work I do not know.  And how the connman network settings can actually be set is a mystery as well.  Hopefully I won't have to find out too soon.

---

### Post by zeddock on 2011-05-23
Seems I am not as savvy as you and need help getting things back to normal...

This whole upgrade to 11 has been a disaster!

I only went the way of connman because I had no indicator to change wireless AP's.  It disappeared from my notification tray shortly after ubuntu 11 install.

Any help appreciated!

zeddock

---

