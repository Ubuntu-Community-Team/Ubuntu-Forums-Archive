---
title: "Can't see second QNap TS-210"
date: 2011-08-01
forum: Networking &amp; Wireless
---

### Post by bob steele on 2011-08-01
Hi All,

        I recently added a second QNap TS-210 to our small home network.  The only way I could access it to set it up was by plugging it directly into a windows XP PC.  After setting it up, I plugged the windows XP PC and the NAS back into the network, rebooted everything, still can't see the second NAS.  It's really starting to get painful   So far no-one at QNap Support or Forums has been able to shed any light on the issue.

So, a small description of our little home network. Please note that no-one and nothing is using a fixed IP, they all get it automatically when they start.

    Netgear ADSL2+ DG834 Modem Router - firmware version v5.01.16 [up to date]
        only needed to connect to the internet from the little gateway
        IP 192.168.10.1
    HP small form factor P4 PC acting as a gateway
        2 x NIC with ICS enabled running Ubuntu 11.04 Classic Desktop
        connected to a Netgear 10/100 24port un-managed switch
        eth1 IP 192.168.10.2 [connects back to the Netgear ADSL2+ DG834 Modem Router]
        subnet 255.255.255.0
        eth0 IP 10.42.43.1 [DNS Server] connects to the LAN via the Netgear switch
        subnet 255.255.255.0

    From the switch;
        My wife's Ubuntu 11.04 Classic Desktop
            IP 10.42.43.80
        Penny's XP Laptop
        Kimmo's XP Desktop
            IP 10.42.43.50
            also a net-book running Ubuntu 11.04 Unity [doing Astrophysics at Curtain Uni so she needed a real OS ]
        Paddy's XP Desktop
            IP 10.42.43.73
        Tommi's XP Desktop or Ubuntu 11.04 Unity [depends on what he wants at the time]
            IP 10.42.43.69
        Samsung CLX3175FN
            IP 10.42.43.27
        QNap TS-210 [the old one] that works just fine and hunky dory
            IP 10.42.43.60
        QNap TS-210 [the new one] can't been seen on the network from any PC
            Supposed to be IP 10.42.43.61 but can't see it unless I plug it directly into an XP PC

Is it Ubuntu on the gateway that is preventing the new NAS from joining our little network?

---

