---
title: "Making Firestarter interface-specific"
date: 2009-03-03
forum: Networking &amp; Wireless
---

### Post by alnilamski on 2009-03-03
Hey all,

I have two NICs (eth0 and eth1), and I am running firewall program Firestarter. I want it to ONLY pay attention to eth0, which is the one connecting to my LAN, and the internet thereafter.
eth1 communes directly with an isolated board, and to avoid complications I want firestarter to completely ignore eth1.

In Preferences, under Network Settings, I have the "Internet Connected Device" and "Local Network connected device" both set as eth0. However, when Firestarter is running, I still run into problems doing stuff over eth1, and these problems go away when I turn Firestarter off. This tells me Firestarter is still trying to butt into eth1! Anyway to make it forget eth1 exists?

---

### Post by alnilamski on 2009-03-04
I've noticed something else kind of strange (also this is sort of a bump I guess, hope that's okay).

In Firestarter's settings, I tell it to "filter ICMP traffic" and allow both pings and pongs.

**When Firestarter is on**:
[LIST]
[*]Pinging google.com (which would go through eth0) works fine.
[*]Pinging the IP of the board that eth1 is hard-wired to does NOT work, nor does pinging the eth1 IP *from* that board.
[/LIST]

When Firestarter is OFF, though, I *can* ping the board.

So not only is Firestarter affecting eth1, which I don't want it to, but it's dis-allowing pings/pongs on eth1 while it allows them on eth0.

I'm a little confused?

---

