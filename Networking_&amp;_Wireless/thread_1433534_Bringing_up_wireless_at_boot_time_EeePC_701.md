---
title: "Bringing up wireless at boot time: EeePC 701"
date: 2010-03-19
forum: Networking &amp; Wireless
---

### Post by tipichris on 2010-03-19
I'm trying to configure an Asus EeePC 701 with Ubuntun Netbook Remix karmic on to start up a specific wireless network at boot time, rather than rely on NetworkManager and waiting for a user to log in. The machine is to stay put on one shelf so I have no need for NetworkManager, but I do have a need for the network to start up as early as possible.

Wireless networking works fine with NetworkManager.

I've disabled NM and added the following to /etc/network/interfaces, an approach which has worked on an old Dell laptop with Xubuntu 9.10

auto wlan0
iface wlan0 inet dhcp
wireless-essid <myssid>
wireless-key <secrethexkey>
wireless-mode managed
wireless-channel 11

This didn't work. The obvious problem is that it refuses to set the frequency, but man iwconfig suggests this is not unexpected with mode managed, and that excluding the channel command is fine. So I remmed that out. But still nothing.

The card is a Realtek RTL8187SE

iwconfig reports the correct essid, but gives the AP as 'not associated'.

iwlist wlan0 scan reports the required network and several of my neighbours.

Can anyone suggest what it is that NM does to get the network up that I'm missing?

---

### Post by jdmoylan on 2010-04-11
i also am running ubuntu 9.10, on an asus eeepc 1005ha, as well as on several panasonic cf50 toughbooks, and have the same problem.  so far as i can tell, NetworkManager completely superceeds any info in /etc/network/interfaces, which is completely ignored.  this is very frustrating, as
whenever anyone does a switch-usere, the connection is dumped and a new connection made according to the parameters set in that users NetworkManager, which dumps any remote logins in the process. i can't imagine whoever thought this was a good design.

---

### Post by tipichris on 2010-04-11
What I found out digging into this a bit more is that the behaviour you describe for NM is by design, and not without good reason. Wireless connections are treated as user preferences, on the basis that one user my not be allowed to access another users' wireless networks. It is possible to set a connection available to all users, but this is still not held open when no user is logged in. 

If you always want to use the same wireless network, you can disable or uninstall NM, and configure the network in /etc/network/interfaces. But if you need NM's functionality, you will have to put up with connections being dropped when a user logs out. 

In my case I don't need NM, but the card that ships with the 701 has limited support. Somehow NM manages to get it working, but it doesn't work well otherwise. My solution in the end was to buy a Zyxel USB wireless adapter, which works fine.

---

### Post by chili555 on 2010-04-11
> NetworkManager completely superceeds any info in /etc/network/interfaces, which is completely ignored.If it is running, that is, not disabled on boot, that is correct. If you want to use /etc/network/interfaces, remove NM.

However, you might right-click the NM icon, select Edit Connections, select the Wireless tab, highlight your network and click Edit. Make sure Available to All Users is checked. See attached.

It is not checked in my example; the relevant computer only has one user.

---

