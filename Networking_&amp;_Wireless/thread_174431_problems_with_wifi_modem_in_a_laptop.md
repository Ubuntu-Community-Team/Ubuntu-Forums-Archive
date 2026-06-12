---
title: "problems with wifi modem in a laptop"
date: 2006-05-11
forum: Networking &amp; Wireless
---

### Post by Richard Roy on 2006-05-11
Hello,
I have a thinkpad X60s laptop, and a wifi modem ipw3945. I can't get it work, and I don't know what to do next. The module seems to be loaded. Here is the output of several commands.
Thanks.

$ lsmod | grep ipw
ipw3945               131452  0
ieee80211_1_1_13       40008  1 ipw3945
$ modprobe -l ipw3945
/lib/modules/2.6.15-22-686/kernel/drivers/net/wireless/ipw3945/ipw3945.ko 

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:D3:21:52:71
          inet addr:192.168.0.207  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fe21:5271/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4942 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2829 errors:0 dropped:0 overruns:0 carrier:0
          collisions:92 txqueuelen:10
          RX bytes:5015258 (4.7 MiB)  TX bytes:316461 (309.0 KiB)
          Base address:0x2000 Memory:ee000000-ee020000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

sit0      no wireless extensions.

---

### Post by khightower on 2006-05-11
I just recieved a DELL inspiron 1200, I had to go with a D-Link Wireless PC card because the one that came with the dell did something similer to what you describe.

After I installed the dlink all was good in wireless land.

---

### Post by Richard Roy on 2006-05-11
[QUOTE=khightower]I just recieved a DELL inspiron 1200, I had to go with a D-Link Wireless PC card because the one that came with the dell did something similer to what you describe.

After I installed the dlink all was good in wireless land.[/QUOTE]


But it works fine on Windows, so the card is ok.
What can I do with it ? (should I work on Windows :confused:  ?)

---

### Post by Richard Roy on 2006-05-11
Please help me...

---

