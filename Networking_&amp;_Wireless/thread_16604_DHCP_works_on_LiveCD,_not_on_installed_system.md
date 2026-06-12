---
title: "DHCP works on LiveCD, not on installed system"
date: 2005-02-22
forum: Networking &amp; Wireless
---

### Post by anterok on 2005-02-22
I have a HomePNA card that works with the Ubuntu LiveCD, the connection is configured automatically. But I can't connect using the installed system. The installer program couldn't connect either.

When I try ifup on the installed system, it says it's sending some DHCP requests but doesn't get an answer. Strangely, ifup on the LiveCD says:
```
Ignoring unknown interface eth0=eth0.
```

[FONT=Fixedsys]ifconfig eth0[/FONT] on the LiveCD gives me this:
```
eth0      Link encap:Ethernet  HWaddr 00:05:6E:00:0A:EA
          inet addr:192.168.1.37  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::205:6eff:fe00:aea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1321 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1456 errors:0 dropped:0 overruns:0 carrier:0
          collisions:253 txqueuelen:1000
          RX bytes:755489 (737.7 KiB)  TX bytes:209635 (204.7 KiB)
          Interrupt:19 Base address:0x9000

```

The card is apparently recognized on the installed system as well:
```
eth0      Link encap:Ethernet  HWaddr 00:05:6E:00:0A:EA
          inet6 addr: fe80::205:6eff:fe00:aea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:11 dropped:0 overruns:0 carrier:11
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:2430 (2.3 KiB)
          Interrupt:169 Base address:0x9000

```

Are there some kernel parameters that might have an effect here? I had to install GRUB manually, so I'm not sure I'm using all the necessary parameters.

---

### Post by Ufo on 2005-02-23
Hi

 I had same kind of problem when I installed Ubuntu (Warty).
I managed to solve the problem by adding following line to /etc/modules:

pcnet32 homepna=1

Maybe this would help for you too?

---

### Post by anterok on 2005-02-23
That worked!  :grin: Thanks a lot!

---

