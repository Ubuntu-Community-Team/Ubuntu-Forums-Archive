---
title: "Access Point: Not associated"
date: 2006-06-30
forum: Networking &amp; Wireless
---

### Post by busgeek on 2006-06-30
I'm having difficulty getting my wifi working on Dapper.

I have a Broadcom 4306 PCI card running with Ndiswrapper.
The driver and hardware are both recognised correctly.
I have no strange messages in dmesg.

$ sudo iwconfig eth1 gives:

Mode: Managed   (I've tried Ad-hoc as well)
ESSID:  off/any
Acess Point: Not associated.
Freq: 2.472  (= channel 13, correct for my wlan)

I've tried running - but it gives no results...
$ sudo iwlist eth1 scan 
eth1     No scan results

What should I try next.  
(The wifi works fine with XP - but I'm trying to escape from that OS!)

---

### Post by busgeek on 2006-07-01
Ok.  Here's the actual output of iwconfig (etc...)

howard@Mesh:~$ sudo iwconfig eth1
eth1      IEEE 802.11b  ESSID:off/any
          Mode:Managed  Frequency:2.472 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:14 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

howard@Mesh:~$ sudo iwlist eth1 scan
eth1      No scan results

howard@Mesh:~$ sudo invoke-rc.d networking restart
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:30:bd:93:1a:a4
Sending on   LPF/eth1/00:30:bd:93:1a:a4
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:30:bd:93:1a:a4
Sending on   LPF/eth1/00:30:bd:93:1a:a4
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


All the parameters seem ok - it just doesn't seem to be "on"!?
Any ideas anyone?

---

### Post by busgeek on 2006-07-02
Also I notice that I get the message

eth1: no IPv6 routers present

Is it possible to get it to run just IPv4 (& will this fix my problem?)

---

### Post by thedarksavant on 2006-07-02
[QUOTE=busgeek]Also I notice that I get the message

eth1: no IPv6 routers present

Is it possible to get it to run just IPv4 (& will this fix my problem?)[/QUOTE]

Please see if [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) can help you. Dapper has Broadcom drivers that sometimes conflict with ndiswrapper.

---

### Post by busgeek on 2006-07-03
No luck yet.  I still get no scan results.

I still get IPv6 messages in dmesg too:

[INDENT][4295583.742000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[4295583.839000] ndiswrapper: driver bcmwl5 (Broadcom,12/29/2002, 3.10.36.0) loaded
[4295583.840000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 18 (level, low) -> IRQ 209
[4295583.927000] ndiswrapper: using irq 209
[4295584.936000] wlan0: vendor: ''
[4295584.936000] wlan0: ndiswrapper ethernet device 00:30:bd:93:1a:a4 using driver bcmwl5, 14E4:4320.5.conf
[4295584.936000] ndiswrapper (set_auth_mode:686): setting auth mode to 3 failed (C0010015)
[4295584.936000] wlan0: encryption modes supported: none
[4295595.568000] eth1: no IPv6 routers present
[4295710.904000] ndiswrapper (iw_set_bitrate:520): setting bit rate failed (C00000BB)[/INDENT]

Also, I wonder that that 'setting auth mode to 3 failed' message means???

---

### Post by moa3333 on 2006-07-21
Solution:

[http://www.fedoraforum.org/forum/showthread.php?t=90409](http://www.fedoraforum.org/forum/showthread.php?t=90409)


Run:

iwpriv wlan0 network_type g
iwconfig wlan0 essid "any"
ifconfig wlan0 up
iwlist wlan0 scan

or 
iwpriv eth1 network_type g
iwconfig eth1 essid "any"
ifconfig eth1 up
iwlist eth1 scan

---

