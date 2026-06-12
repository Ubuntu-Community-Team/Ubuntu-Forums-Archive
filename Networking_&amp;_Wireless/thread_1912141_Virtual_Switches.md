---
title: "Virtual Switches"
date: 2012-01-20
forum: Networking &amp; Wireless
---

### Post by guitou91 on 2012-01-20
Hello,

I would like to do 3 switches with one switch.
I explain:  I have a big switch: 10 port
I want to create 3 switches of 3 ports with this switch.
see the attached pictures
[ATTACH]211156[/ATTACH]

My switch has the RSTP mode.
It's to avoid to buy several switchs.

Can we create virtual switches in a switch?
each Virtual switches are totally independent ?

Thank a lot.

---

### Post by guitou91 on 2012-01-20
sorry, the picture is bad.
[ATTACH]211157[/ATTACH]

---

### Post by guitou91 on 2012-01-20
an other test.

is it possible to delete my last post?
[attach]211158[/attach]

---

### Post by qubits4all on 2012-10-23
I would suggest seeing whether your switch supports the use of VLANs (Virtual LANs). (See the Wikipedia [article]("http://en.wikipedia.org/wiki/VLAN") for an overview.) If your hardware supports it, they're generally a good way to isolate traffic on an Ethernet switch. Pretty much any managed switch supports this functionality, although lower priced (i.e., "unmanaged") switches generally do not. If you have this capability, a different VLAN can be assigned to each of 3 sets of 3 ports, which would give you the 3 essentially "virtual switches" within the one physical switch, you ask about. VLANs effectively segregate Ethernet traffic, which would otherwise be able to traverse any of the switch's 10 ports.

The tenth port could be reserved for switch management, or if the need arises it could be used to provide a VLAN Trunk port. (See the IEEE [802.1Q]("http://en.wikipedia.org/wiki/IEEE_802.1Q") standard). However the additional functionality provided by such VLAN Trunking, namely the ability to pass traffic for multiple VLANs over one port, is not required.

---

