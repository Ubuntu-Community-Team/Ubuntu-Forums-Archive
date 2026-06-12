---
title: "OpenVPN Server with nm-managed wifi uplink?"
date: 2011-02-07
forum: Networking &amp; Wireless
---

### Post by snotplop on 2011-02-07
Hello all!

I'm attempting to set up a VPN server on my box using the nifty HowTo posted here: [https://help.ubuntu.com/10.10/serverguide/C/openvpn.html](https://help.ubuntu.com/10.10/serverguide/C/openvpn.html).

My setup is as follows:[INDENT]wifi0 --> Internet; managed entirely via nm-applet (NetworkManager)
[/INDENT]Where I'm running into trouble is in the creation of a bridge interface (br0) to bridge future VPN clients to my local network. 

The guide(s) say that I need to screw around in /etc/network/interfaces to setup br0 and [eth0/wifi0] accordingly. The problem is that when I specify a configuration of any sort for wifi0 (my only choice for a network uplink), it disables nm and I am unable to configure my wifi in any sort of sane way after reboot...

Any tips?

Further info: this "server" doesn't move, and always always connects to the same wifi hotspot that is also nailed in place.


Tx Ubuntu community!

---

### Post by snotplop on 2011-02-07
Has there really been nobody out there that's set up a VPN server with a wifi uplink?:confused:

---

