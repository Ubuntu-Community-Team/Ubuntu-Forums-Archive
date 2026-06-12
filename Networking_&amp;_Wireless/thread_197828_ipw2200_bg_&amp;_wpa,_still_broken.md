---
title: "ipw2200 bg &amp; wpa, still broken"
date: 2006-06-16
forum: Networking &amp; Wireless
---

### Post by flan on 2006-06-16
I really don't know what else I can do to fix this...

I've followed [this]("http://ubuntuforums.org/showthread.php?t=125150")  and [this]("http://www.ubuntuforums.org/showthread.php?t=26623&highlight=ipw2200+wpa") how-to's but it doesn't help me so much... I have to keep my wireless lan unprotected because if wpa is enabled my acer 1652 laptop (centrino) simply won't connect to the access point/router...

is there something else to know to fix this?

my wireless card works and i can connect to the internet trough the router and to the router web interface but i can't use wpa protection.
here the result of some commands:

```

~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:D3:2C:15
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:169

eth1      Link encap:Ethernet  HWaddr 00:13:CE:3C:DF:A0
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4079 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3450 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3794926 (3.6 MiB)  TX bytes:405702 (396.1 KiB)
          Interrupt:177 Base address:0xe000 Memory:c820b000-c820bfff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:360 (360.0 b)  TX bytes:360 (360.0 b)

~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11g  ESSID:"XXXXX"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:2B:01:D1:17
          Bit Rate:48 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=84/100  Signal level=-46 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:2

eth0      no wireless extensions.

```

---

### Post by flan on 2006-06-17
I have re-installed dapper on my laptop acer 1652 wlmi because my network was messed up
after re-installing I created this file /etc/wpa_supplicant.conf with these lines in:

```
ctrl_interface=/var/run/wpa_supplicant

network={
       ssid="XXXX"
       scan_ssid=1
       proto=WPA
       key_mgmt=WPA-PSK
       psk="YYYY"
}
```

where XXXX is the ssid of my router/access point and YYYY is my wpa key.
now i can connect to my wpa wireless network but every time i have to open a terminal and do:

```
sudo wpa_supplicant -B -w -ieth1 -Dwext -c /etc/wpa_supplicant.conf -d

```

it is possible to start this command at boot? I just want my wireless card to connect to te ap as soon it is detected, just like it goes in windows...

---

### Post by spier on 2006-06-17
I think you don`t need to mess with wpasupplicant.conf and such to get a working wireless in dapper.

Have a look at this:
[HOWTO: NetworkManager with WPA 1&2 Support on Dapper]("http://www.ubuntuforums.org/showthread.php?t=125150")

Specially for the **Further Clarification** note.

---

