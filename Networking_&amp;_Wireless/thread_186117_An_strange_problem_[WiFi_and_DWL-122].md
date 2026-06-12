---
title: "An strange problem [WiFi and DWL-122]"
date: 2006-06-01
forum: Networking &amp; Wireless
---

### Post by Davidios on 2006-06-01
Hi! I have installed Dapper Drake and I have been trying to configure the f*****g WiFi...

First I installed wlan-ng-drivers... But it didn't work.

Then I installed ndiswrapper and the Windows drivers. Ok, the WiFi appeared in the administration. I configure it, but... 

> davids@ubuntu-linux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11-b  ESSID:"ADSL-WIRELESS"  Nickname:"ADSL-WIRELESS"
          Mode:Ad-Hoc  Frequency:2.437 GHz  Cell: 00:A0:C5:DC:1C:38
          Bit Rate:11 Mb/s   Tx-Power:18 dBm
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Link Quality=48/92  Signal level=-44 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


and...

> davids@ubuntu-linux:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.20 icmp_seq=2 Destination Host Unreachable
From 192.168.1.20 icmp_seq=3 Destination Host Unreachable
From 192.168.1.20 icmp_seq=4 Destination Host Unreachable
From 192.168.1.20 icmp_seq=5 Destination Host Unreachable
From 192.168.1.20 icmp_seq=6 Destination Host Unreachable
From 192.168.1.20 icmp_seq=7 Destination Host Unreachable
...
From 192.168.1.26 icmp_seq=600 Destination Host Unreachable
From 192.168.1.26 icmp_seq=601 Destination Host Unreachable
From 192.168.1.26 icmp_seq=602 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
605 packets transmitted, 16 received, +398 errors, 97% packet loss, time 605725ms
rtt min/avg/max/mdev = 0.677/0.927/2.317/0.524 ms, pipe 4


What can I do?
PS: sorry, my English is too bad.

---

### Post by az on 2006-06-01
It's in the linux-wlan-ng documentation.

Linux wlan-ng and the prism2 speak a different language that the standard wireless tools.

You need to edit /etc/network/interfaces by hand like this:

auto wlan0

iface wlan0 inet dhcp
 wireless_mode managed
 wireless_enc on
 wlan_ng_key0 aa:11:bb:22:ff
 wireless-essid MYessid

Also, ndiswrapper will not work because the prims2_usb module is being loaded.  You either use the linux-wlan-ng stuff (very stable) or blacklist the prims2_usb module and use ndiswrapper (good luck)

---

### Post by Davidios on 2006-06-02
Thanks for your help, azz.

I've uninstalled ndiswrapper. Then, I have edited /etc/network/interfaces but DHCP didn't work, so I tried with:

> auto wlan0

iface wlan0 inet static
wireless_mode managed
wireless_enc on
wlan_ng_key0 aa:11:bb:22:ff
wireless-essid ADSL-WIRELESS
wireless-key *************************
address 192.168.1.27
netmask 255.255.255.0
gateway 192.168.1.1


... it still doesn't work:( 

> davids@ubuntu-linux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11-b  ESSID:"ADSL-WIRELESS"  Nickname:"ADSL-WIRELESS"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:A0:C5:DC:1C:38
          Bit Rate:11 Mb/s   Tx-Power:18 dBm
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Link Quality=50/92  Signal level=-42 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Can anybody find me any solution?

Later I will try to connect without WEP, now I'm leaving. I'll tell you how it works.

---

