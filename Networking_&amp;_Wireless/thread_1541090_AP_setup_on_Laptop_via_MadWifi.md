---
title: "AP setup on Laptop via MadWifi"
date: 2010-07-28
forum: Networking &amp; Wireless
---

### Post by ThiKa on 2010-07-28
I have successfully created an access point on my Laptop via Madwifi drivers. A second laptop can successfully associate with the created AP. But ping is not possible from both sides.

AP on the first Laptop:
ifconfig ath0 10.0.0.1 netmask 255.255.255.0 broadcast 10.0.0.255 up

Second Laptop:
ifconfig ath1 10.0.0.50 netmask 255.255.255.0 up
route add default gw 10.0.0.1

Association works, but ping command is not possible from both sides:
ping 10.0.0.50
ping 10.0.0.1

What could be the problem?

---

### Post by Iowan on 2010-07-28
> **ThiKa said:**
>  A second laptop can successfully associate with the created AP. But ping is not possible from [COLOR="Red"]both[/COLOR] sides
....
Association works, but ping command is not possible from [COLOR="Red"]both[/COLOR] sides:
ping 10.0.0.50
ping 10.0.0.1


:confused: I'm not sure that just because two machines have IP's in the same subnet, that they're "associating". **ping** would suggest that they are not... Will [COLOR="Red"]either [/COLOR]successfully ping the other?

---

### Post by ThiKa on 2010-07-29
(1)------------------------------------------------
I see the successfull association in the Logs of hostapd.
This is the Output of hostapd:

l2_packet_receive - recvfrom: Network is down
Wireless event: cmd=0x8b19 len=8
Wireless event: cmd=0x8c03 len=20
ath0: STA 00:XX:XX:XX:XX:XX IEEE 802.11: associated
  New STA
madwifi_sta_clear_stats: addr=00:XX:XX:XX:XX:XX
Wireless event: cmd=0x8b19 len=8

If I connect with my Palm TX I see the successfull association by the notification "successfull connection" at the bottom.

(2)--------------------------------------------------------
The output of the command  "route -n" is as follows:

Ziel            Router          Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 ath0

(3)--------------------------------------------------
"ping" is not possible in neither direction.

---

### Post by ThiKa on 2010-08-28
I have tried lot of settings during the last weeks - and could not find a working solution within Ubuntu. However if you want to do networking only and do not like/are not able to configure too much things, give a try to Zeroshell, programmed by Fulvio Riccardi. This Linux distribution worked like a charm right from the beginning.

Nevertheless I like Ubuntu Linux, and for all other work I use UBUNTU of course;-)

---

