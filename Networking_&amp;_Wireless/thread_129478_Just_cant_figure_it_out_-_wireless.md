---
title: "Just cant figure it out - wireless"
date: 2006-02-13
forum: Networking &amp; Wireless
---

### Post by theProf on 2006-02-13
Hey folks.  I've been able to use these forums to solve just about every problem I've encounterd with Ubuntu, but I've got a wifi problem that has me totally perplexed.

I'm using a D-Link DWL-650+ on a Dell C600 laptop.  I dual book Win2K and Ubuntu.  I have the same wireless settingson the AP in my classroom at school (Netgear MR814V2) and the one in my living room at home (Linksys WRT54G).

Here's the problem.  At home I can connect wirelessly through Windows or Ubuntu.  At school, without changing any configuration, I can connect to the internet through Windows, but not through Ubuntu.  I get a siganl strength, but no IP, and even if I force an IP, I still cannot connect.

So windows works both places, but ubuntu only works at home.  I doesn't make sense to me.  I'd like to go ubuntu full-time if possible, but this is keeping me from doing so.

Any help you can provide is appreciated.  Thanks.
Marc

---

### Post by gruepig on 2006-02-13
What's the output of 'iwconfig -a' when you are at school?

---

### Post by theProf on 2006-02-14
I didn't see the -a option in iwconfig.  I wasn't sure if you wanted to see 'ifconfig -a' or 'iwconfig', so here are both.  Let me know if I mistakenly missed an option in iwconfig.

Thanks for your help.

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+  ESSID:"XXXX" ##ESSID is assigned and confirmed to be the same on both APs##   Nickname:"acx100 v0.2.0pre8"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:09:5B:6F:4C:6A
          Bit Rate=22 Mb/s   Tx-Power=18 dBm   Sensitivity=187/255
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality=87/100  Signal level=82/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

ifconfig -a:
```
eth0      Link encap:Ethernet  HWaddr 00:04:76:49:48:8F
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xd400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:344 errors:0 dropped:0 overruns:0 frame:0
          TX packets:344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:92752 (90.5 KiB)  TX bytes:92752 (90.5 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:40:05:B3:A6:17
          inet6 addr: fe80::240:5ff:feb3:a617/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3184 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:278977 (272.4 KiB)  TX bytes:2220 (2.1 KiB)
          Interrupt:11 Base address:0x4800
```

---

### Post by theProf on 2006-02-26
I was away last week on vacation.  Has anyone taken a look at the posted logs?  Any ideas about how to get my wifi working at school (as far as I can tell, the AP is configured the same as at home).

Thanks
Marc

---

