---
title: "Network Manager"
date: 2011-08-02
forum: Networking &amp; Wireless
---

### Post by bob steele on 2011-08-02
Hi All,

        Ubuntu 11.04 using Gnome Desktop instead of Unity.  All patches and stuff installed.

We recently added a second QNap TS-210 to our network and Network Manager doesn't see it.  The 210 is set to DHCP.  Our old TS-210 is just fine as are all 6 PC and 1 laptop.  We can all browse the network and the internet.  It seems that Network manager has decided that we have enough on our network.  How do I tell Network Manager to add the new NAS??  Is there a way to tell it to explore the network or reset or something??  Or maybe clear it's current connections??  I really don't want to have to wipe it or re-install!!

Our little network:

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

---

### Post by Beacon11 on 2011-08-03
Unfortunately I don't have a solution to your problem, but I wanted to say that your email address will be scraped just leaving it here. I would recommend not posting it.

---

### Post by bob steele on 2011-08-03
G'day Beacon,

> **Beacon11 said:**
> Unfortunately I don't have a solution to your problem, but I wanted to say that your email address will be scraped just leaving it here. I would recommend not posting it.

OK, I'll edit my sig.  Thanks.

I don't suppose you know how to stop, clear and re-start Network Manager by any chance??  Or perhaps were I might find such information?


Yours Sincerely

bob Steele

---

