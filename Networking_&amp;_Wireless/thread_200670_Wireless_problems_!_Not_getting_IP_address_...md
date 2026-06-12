---
title: "Wireless problems ! Not getting IP address .."
date: 2006-06-20
forum: Networking &amp; Wireless
---

### Post by joaocorreia on 2006-06-20
Hello,

After upgrading from Breezy to Dapper wireless stop working ... it enables the card but doesn't get an IP ...

joaocorreia@atlantis:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:02:A5:6E:8A:44
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:3 Base address:0xd100

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3437 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3437 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:874693 (854.1 KiB)  TX bytes:874693 (854.1 KiB)

joaocorreia@atlantis:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"ns"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:0C:76:AC:23:C7
          Bit Rate:2 Mb/s   Sensitivity:1/3
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=24/92  Signal level=-73 dBm  Noise level=-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

joaocorreia@atlantis:~$

Any tips ?

Regards
Joao Correia

---

### Post by noname101 on 2006-06-20
Try giving it a static ip address. Also you could try to reboot your router.

---

### Post by joaocorreia on 2006-06-22
It was working before ! Its Dapper's fault not the router. I have other equipments that work fine. 

After the upgrade wireless just stopped working !

Regards
Joao Correia

---

### Post by adagio on 2006-06-22
Looked up a DHCP howto, found that 'dhcpcd' is not installed by default, not sure if this is anything to do with it.

---

### Post by adagio on 2006-06-22
Could be down to the default IP assigned to the network interface...

[http://www.ubuntuforums.org/showthread.php?t=201959](http://www.ubuntuforums.org/showthread.php?t=201959)

Ref. post #3

---

