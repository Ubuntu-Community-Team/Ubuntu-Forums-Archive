---
title: "wired network problem"
date: 2011-02-16
forum: Networking &amp; Wireless
---

### Post by wilho on 2011-02-16
Hi,

I'm having mysterious wired network problem with my Karmic/9.10 machine. It hasn't been in network a while, but now I finally got the cabling done. 

I can't get the IP from dhcp server (TW-EA510), and static settings doesn't work either. Fresh cabling showed OK 1Gb connection on tester, and win7 laptop works fine. I even tried with long cable though the rooms, but it doesn't help, so it definately isn't the new cabling.

Log from the router after issuing #"dhclient":
Feb 16 23:01:43 DHCP SERVER: DHCPDISCOVER from 00:01:29:fb:c5:d1 via br0
Feb 16 23:01:43 DHCP SERVER: DHCP offer to 00:01:29:fb:c5:d1
Feb 16 23:01:49 DHCP SERVER: DHCP request from 00:1b:ea:c8:a0:ba
Feb 16 23:01:49 DHCP SERVER: DHCP ack to 00:1b:ea:c8:a0:ba
Feb 16 23:01:54 DHCP SERVER: DHCPDISCOVER from 00:01:29:fb:c5:d1 via br0
Feb 16 23:01:54 DHCP SERVER: DHCP offer to 00:01:29:fb:c5:d1
Feb 16 23:02:03 DHCP SERVER: DHCPDISCOVER from 00:01:29:fb:c5:d1 via br0
Feb 16 23:02:03 DHCP SERVER: DHCP offer to 00:01:29:fb:c5:d1
.
.
.
00:01:29:fb:c5:d1 is the MAC of the Ubuntu machine, so at least the request is getting to the router, but ACK never gets sent. In the ubuntu machine end it just says "No DHCPOFFERS received".

Motherboard is some old Lanparty with two ethernet ports, NVidia CK804 and Marvell 88E800 rev 13 Gigabit netwok adapters, neither of them works. At least another of them has been worked earlier when I last got it wired. It's been a while, so I'm not sure which one of them and with different router if that matters.

What might be the problem?

---

### Post by wilho on 2011-02-17
Thought I should add; "#lshw -C network" sees only the Marvell adapter for some reason, but network manager sees them both, and I'm able to get both to send the DHCPDISCOVER requests even simultaneously with two cables. Both of them works as poorly though.

---

### Post by wilho on 2011-02-17
I solved this. Router had vlan configured, which prevented linux from working. Don't know why, but after disabling vlan-tagging it started to work.

---

### Post by tsucol11 on 2011-02-17
> **wilho said:**
> I solved this. Router had vlan configured, which prevented linux from working. Don't know why, but after disabling vlan-tagging it started to work.


Thanks for posting your results.

Brian

---

