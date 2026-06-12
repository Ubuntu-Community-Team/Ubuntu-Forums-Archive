---
title: "stupid question but...."
date: 2006-01-12
forum: Networking &amp; Wireless
---

### Post by amitab09 on 2006-01-12
Hi,

I have a Belkin wireless card running on an RT2500 chipset. Ubuntu found and installed the driver successfully and i have connected to my home wireless network... 

But I havent been able to do anything useful such as browse the web. I am new to linux and am unsure if there is anything else i need to do. How can i use my wireless card, (eg so i can browse the web) or ping to other computers on the network? Do I need to download any wifi managers such as kwifi or wifi-radar to b able to browse the web?

Thanks

---

### Post by odin on 2006-01-12
no question is stupid (I can make worst ones).Said this I have another question:

how do you know your network card is working correctly if you can do nothing??

If you can connect to your Access Point then the problem could be in the access point  not in your PC,just guessing...post here the output of **ifconfig** and **iwconfig** for your wireless card.

[B]sudo ifconfig your_network_card
sudo iwconfig your_network_card[/B]

---

### Post by amitab09 on 2006-01-12
I read on some forum post to try typing sudo dhclient ra0 so i tried that, but it didnt work

[B]
ifconfig gets me the following:[/B]

kuk@kuks:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:164071 errors:0 dropped:0 overruns:0 frame:0
          TX packets:164071 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:14904091 (14.2 MiB)  TX bytes:14904091 (14.2 MiB)

ra0       Link encap:Ethernet  HWaddr 00:11:50:90:0E:37
          inet6 addr: fe80::211:50ff:fe90:e37/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16808 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4905 errors:20 dropped:20 overruns:0 carrier:0
          collisions:550 txqueuelen:1000
          RX bytes:1418931 (1.3 MiB)  TX bytes:497373 (485.7 KiB)
          Interrupt:17

**iwconfig gives me the following:**

kuk@kuks:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:"ADAM IS GAY"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:12:17:07:70:9D
          Bit Rate:54 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=76/100  Signal level=-25 dBm  Noise level:-192 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



**When i type sudo dhclient ra0 i get the following:**

There is already a pid file /var/run/dhclient.pid with pid 12200
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/ra0/00:11:50:90:0e:37
Sending on LPF/ra0/00:11:50:90:0e:37
Sending on Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Please could you help me. Thanks

---

### Post by az on 2006-01-12
Are you using WEP?


Your card can see your router (it is outing Adam...), but what do you mean by it can connect to your wireless network?

---

### Post by amitab09 on 2006-01-13
Oh. I thought the following meant i was connected to the router adam...

ra0 RT2500 Wireless ESSID:"ADAM IS GAY"
Mode:Managed Frequency=2.462 GHz Access Point: 00:12:17:07:70:9D
Bit Rate:54 Mb/s
RTS thrff Fragment thrff
Link Quality=76/100 Signal level=-25 dBm Noise level:-192 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

Does that mean I am not connected to it? It does use WEP encryption. How do i connect to it?

---

### Post by odin on 2006-01-13
[QUOTE=amitab09]Oh. I thought the following meant i was connected to the router adam...

ra0 RT2500 Wireless ESSID:"ADAM IS GAY"
Mode:Managed Frequency=2.462 GHz Access Point: 00:12:17:07:70:9D
Bit Rate:54 Mb/s
RTS thrff Fragment thrff
Link Quality=76/100 Signal level=-25 dBm Noise level:-192 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

Does that mean I am not connected to it? It does use WEP encryption. How do i connect to it?[/QUOTE]

ok.This is the process I would follow:

[B]ifconfig ra0 up
iwconfig ra0 essid "ADAM IS GAY" key  your_wep_key
dhclient ra0[/B]


hope this helps

---

