---
title: "ndispwrapper and fastethernet problem"
date: 2006-07-07
forum: Networking &amp; Wireless
---

### Post by sles on 2006-07-07
Hello!

I just installed ubunty 6.06.
I have bcm4318 based card and I can't get it works with bcm43xx driver, but it works with ndiswrapper.

I also need fastethernet interface, so I installed realtek-based card.
Here is what I see in dmesg:

[4294693.327000] 8139too Fast Ethernet driver 0.9.27
[4294693.327000] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294693.342000] eth0: RealTek RTL8139 at 0xe088c000, 00:e0:4d:08:b2:af, IRQ 11
[4294693.342000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[4294693.371000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)

[skip]

[4294699.169000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[4294699.236000] ndiswrapper: driver bcmwl5a (ASUS,10/14/2004, 3.90.7.0) loaded
[4294699.236000] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNKF] -> GSI 10 (level, low) -> IRQ 10
[4294699.249000] ndiswrapper: using irq 10
[4294700.455000] wlan0: vendor: ''
[4294700.455000] wlan0: ndiswrapper ethernet device 00:17:31:1f:7a:bd using driver bcmwl5a, 14E4:4318:1043:100F.5.conf
[4294700.455000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK


but wlan0 doesn't work.
wlan0     Link encap:Ethernet  HWaddr 00:17:31:1F:7A:BD
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fe1f:7abd/64 &#1044;&#1080;&#1072;&#1087;&#1072;&#1079;&#1086;&#1085;:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Memory:e7040000-e7042000

it is up, but no pings:

root@dm-desktop:~# ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

--- 192.168.0.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 1998ms

And I can't get eth0 up:

root@dm-desktop:~# ifup eth0
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
eth0: ERROR while getting interface flags: No such device
Failed to bring up eth0.

but:
root@dm-desktop:~# cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0


Looks like wlan0 and eth0 conflict.
If I have only wifi or only fastethernet card installed all is OK?
What can I do to have wifi and fastethernet cars works at the same time?

Thank you!

---

### Post by sles on 2006-07-07
I tried to set wifi card as eth1.
If I write options ndiswrapper if_name=eth%d then wifi is eth0 and previosly loaded realtek driver is eth0 too, certanly nothing works.

I tried
options ndiswrapper if_name=eth1
ndiswrapper module crashes....

---

### Post by sles on 2006-07-11
I solved my problem with dirty hack.

I blacklisted ndiswrapper and 8139too modules and load it from rc.local with 
/sbin/modprobe ndiswrapper
/sbin/modprobe 8139too

all works OK.

Sorry, I'm Ubuntu newbie, may be there is more correct method.
And looks like there is bug in Ubuntu init scripts.

---

### Post by sles on 2006-07-19
Well, this strange method didn't solve problem ;-)
After several days and reboots I got the same problem.
So I downloaded sources for latest ndiswrapper (1.21), compiled it and looks all is OK now even without blacklisting modules(hmm, may be for several days? ;-) ).

---

