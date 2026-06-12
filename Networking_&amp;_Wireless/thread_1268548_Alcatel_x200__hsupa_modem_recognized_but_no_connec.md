---
title: "Alcatel x200  hsupa modem recognized but no connection"
date: 2009-09-17
forum: Networking &amp; Wireless
---

### Post by garzona on 2009-09-17
hi im using ubuntu 9.04 and i followed a thread on how to make an alcatel x200 usb modem to be recognized, apparently it worked when i start wvdial (sudo wvdial) says the following: 
> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","wap.tigo.sv"
AT+CGDCONT=1,"IP","wap.tigo.sv"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Thu Sep 17 02:14:26 2009
--> Pid of pppd: 9865
--> Using interface ppp0
--> pppd: &#65533;&#65533;
--> pppd: &#65533;&#65533;
--> pppd: &#65533;&#65533;
--> pppd: &#65533;&#65533;
--> pppd: &#65533;&#65533;
--> pppd: &#65533;&#65533;
--> pppd: &#65533;&#65533;
--> local  IP address 1xxx.xxx.xxx.
--> pppd: &#65533;&#65533;
--> remote IP address 1xxx.xx.xx.
--> pppd: &#65533;&#65533;
--> primary   DNS address 200.85.0.104
--> pppd: &#65533;&#65533;
--> secondary DNS address 200.85.0.107
--> pppd: &#65533;&#65533;

i want to know what do i do to connect now; since, im opening firefox and no connection , thanks in advanced.

---

### Post by louigi600 on 2009-09-17
After vwdial did what you wrote what do you get if you type in a terminal the following commands:
tail -20 /var/log messages
dmesg |tail -20
ifconfig
route -n

---

### Post by GeorgeVita on 2009-09-17
Hi **garzona**,
using **wvdial** firefox starts in offline mode.

Check and 'untick' offline mode with: **ALT-F W** into firefox

Reegards,
George

---

### Post by GeorgeVita on 2009-09-17
sorry double post!

---

### Post by garzona on 2009-09-18
thank you. 
> **louigi600 said:**
> After vwdial did what you wrote what do you get if you type in a terminal the following commands:
tail -20 /var/log messages
dmesg |tail -20
ifconfig
route -n

garzona@garzona-laptop:~$ tail -20 /var/log messages
tail: option used in invalid context -- 2

garzona@garzona-laptop:~$ dmesg |tail -20
[  900.446485] usb 1-1: USB disconnect, address 4
[  900.808101] usb 1-1: new high speed USB device using ehci_hcd and address 5
[  900.953345] usb 1-1: configuration #1 chosen from 1 choice
[  900.957692] usbserial_generic 1-1:1.0: generic converter detected
[  900.957801] usb 1-1: generic converter now attached to ttyUSB0
[  900.958047] usbserial_generic 1-1:1.1: generic converter detected
[  900.958248] usb 1-1: generic converter now attached to ttyUSB1
[  900.959441] scsi4 : SCSI emulation for USB Mass Storage devices
[  900.959899] usbserial_generic 1-1:1.3: generic converter detected
[  900.959986] usb 1-1: generic converter now attached to ttyUSB2
[  900.962273] usb-storage: device found at 5
[  900.962278] usb-storage: waiting for device to settle before scanning
[  905.961479] usb-storage: device scan complete
[  905.963808] scsi 4:0:0:0: Direct-Access     USBModem MMC Storage      2.31 PQ: 0 ANSI: 2
[  905.970812] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[  905.970933] sd 4:0:0:0: Attached scsi generic sg2 type 0
[  949.691022] PPP BSD Compression module registered
[  949.708504] PPP Deflate Compression module registered
[ 1291.326175] eth2: no IPv6 routers present
[ 2224.509040] eth2: no IPv6 routers present


garzona@garzona-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:a8:ac:5a  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth2      Link encap:Ethernet  HWaddr 00:16:cf:1a:34:ef  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:cfff:fe1a:34ef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2590 errors:0 dropped:0 overruns:0 frame:964
          TX packets:2653 errors:16 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2647925 (2.6 MB)  TX bytes:495195 (495.1 KB)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.245.138.253  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:146 (146.0 B)  TX bytes:3973 (3.9 KB)

im with my wifi on this
garzona@garzona-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.64.64.64     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 eth2
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth2
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth2

with usb modem connected only im getting 

garzona@garzona-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.64.64.64     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0

---

### Post by garzona on 2009-09-18
> **GeorgeVita said:**
> Hi **garzona**,
using **wvdial** firefox starts in offline mode.

Check and 'untick' offline mode with: **ALT-F W** into firefox

Reegards,
George

thanks george,tried that  but it did not work.

---

### Post by GeorgeVita on 2009-09-18
Hi **garzona**, in case your DNS are not correct (or using eth as gateway and not the real modem) check file: **/etc/ppp/peers/wvdial**

Possible parameters (from **man pppd**): ```
name wvdial
noauth
usepeerdns
defaultroute
replacedefaultroute
```

> **usepeerdns** Ask the peer for up to 2 DNS server addresses...
**defaultroute** Add a default route to the system routing tables...
**replacedefaultroute** ... replaces an existing default route with the new default route.

Regards,
George

---

### Post by garzona on 2009-09-18
hey George, i checked file and this is what i got:

noauth
usepeerdns
defaultroute

---

### Post by GeorgeVita on 2009-09-18
Hi **garzona**, looking at recent network-manager data, shows:
APN for tigo = internet.tigo.sv (and not wap.tigo.sv)

I am not sure which is the right one and I propose to ASK THEM, because if your account is not 'internet' but 'wap' it may cost you a lot choosing the wrong one!

If your provider confirm the APN, change it (**/etc/wvdial.conf**) and retry.
Otherwise add **replacedefaultroute** and/or **noipv6** at **/etc/ppp/peers/wvdial** file.

G

---

### Post by garzona on 2009-09-18
Mr. George Vita, thank you very much im using my Alcatel x200 usb modem as i write this, so thank you very much, and yes, they wap address was the problem, i called them and they confirmed the one you gave me, so thanks again for solving my problem.
Regards!

---

### Post by louigi600 on 2009-09-20
You connection looks fine .... if you've no firewalling configured on the box you should be fine.
Firefox caches content of /etc/resolv.conf ...you might want to restart firefox after you make the wireless broadbend connection.

---

### Post by louigi600 on 2009-09-20
Where's your default gw gone after you make the ppp connection ?

---

