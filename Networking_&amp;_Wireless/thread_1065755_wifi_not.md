---
title: "wifi not"
date: 2009-02-10
forum: Networking &amp; Wireless
---

### Post by ussndmac on 2009-02-10
I'm finally getting back to looking at the wifi on my dell xps1530 w/
Intel 3945. I have Unbuntu Studio Hardy amd64 installed.

Here is the result after bringing down eth0 and wlan0 up:

lsmod | grep 3945
iwl3945               100848  0 
iwlwifi_mac80211      253284  1 iwl3945


lspci |grep Network
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG
Network Connection (rev 02)


iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"macwap"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point:
00:0C:41:68:E7:99   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xx (I hid the real key, it is correct though)
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

dmesg | grep 3945
[   88.757156] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network
Connection driver for Linux, 1.2.0
[   88.757160] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   88.757810] iwl3945: Detected Intel PRO/Wireless 3945ABG Network
Connection
[   89.719885] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a
channels
[   89.724457] wmaster0: Selected rate control algorithm 'iwl-3945-rs'

But I don't get connected.

I also noticed an message in dmesg about association rejected.

Any pointers appreciated.

---

### Post by superprash2003 on 2009-02-10
please post your **ifconfig** output.. you may not be getting an ip address.. also type **sudo dhclient wlan0** to try to get an ip from your wifi router.

---

### Post by ussndmac on 2009-02-10
> **superprash2003 said:**
> please post your **ifconfig** output.. you may not be getting an ip address.. also type **sudo dhclient wlan0** to try to get an ip from your wifi router.

my net is not using dhcp, so ip is entered manually.

Will get output of ifconfig later, I'm not near the machine in question at the moment.

---

### Post by ussndmac on 2009-02-11
I have also noticed that having messed with Network Manager last night, when I boot, I don't get wired or wireless, without going into terminal and issuing a /etc/init.d/networking restart. A simple ifup eth0 doesn't do it. What the heck did Net Mangler do to me now?

Output of ifconfig:

```
root@macstudio:/home/ubmac# ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1428 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1428 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:71476 (69.8 KB)  TX bytes:71476 (69.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:c0:ab:f1  
          inet addr:192.168.53.13  Bcast:192.168.53.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-C0-AB-F1-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

---

### Post by superprash2003 on 2009-02-12
well you are getting an ip.. type **ping google.com** and post output

---

### Post by ussndmac on 2009-02-12
Since I'm not using dhcp, the ip is static, spec'd by me.

ping fails to anything intranet or internet.

The wap shows no sing of this laptop in it's log.

---

### Post by ussndmac on 2009-02-13
Ok, so I loaded wicd.

It could see the wap but not connect.

So, I disabled all the security on the wap. Then wicd could see it and claimed to connected.

But still no ping to intranet or internet.
:confused:

---

