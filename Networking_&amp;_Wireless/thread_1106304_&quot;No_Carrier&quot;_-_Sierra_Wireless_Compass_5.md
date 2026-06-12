---
title: "&quot;No Carrier&quot; - Sierra Wireless Compass 597"
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by wblogan on 2009-03-25
**1)** Dell XPS M1530
==============================
**2)** "Bus 004 Device 003: ID 1199:0023 Sierra Wireless, Inc."; Compass 597
==============================
**3)** ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:23:ae:11:63:03  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1748 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1748 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:87400 (85.3 KB)  TX bytes:87400 (85.3 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:192.168.65.1  Bcast:192.168.65.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.59.1  Bcast:192.168.59.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:369 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:d2:77:76  
          inet addr:192.168.2.103  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fed2:7776/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46928 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9335 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:64484810 (61.4 MB)  TX bytes:1630383 (1.5 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-D2-77-76-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
========================================
iwconfig: "no wireless extensions"
========================================
iwconfig wlan0:
wlan0     IEEE 802.11g  ESSID:"haha"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1B:2F:E5:40:BA   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=93/100  Signal level=-34 dBm  Noise level=-69 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
========================================
**4)** lsmod:
Module                  Size  Used by
ppp_generic            29588  0 
slhc                    7040  1 ppp_generic
usb_storage            73664  0 
libusual               19108  1 usb_storage
sierra                 13192  0 
usbserial              35816  1 sierra
usbcore               146028  10 usb_storage,libusual,sierra,usbserial,hci_usb,uvcvideo,usbhid,ehci_hcd,uhci_hcd
========================================[B]
5)[/B] dmesg: too much to post
========================================[B]
6)[/B] lshw -C networks: PCI (sysfs)
========================================
**7) **network scan: "interface doesn't support scanning"
========================================
**8)** Ubuntu 8.04
========================================[B]
9)[/B] 2.6.24-16-generic i686
========================================
**10)**  /etc/init.d/networking restart
 * Reconfiguring network interfaces...
/usr/bin/poff: No pppd is running.  None stopped.
ppp0: ERROR while getting interface flags: No such device
========================================

I'm trying to get the Sprint Sierra Wireless Compass 597 USB card to work on my Dell XPS M1530 running Ubuntu 8.04 (Hardy Herron) 2.6.24-16-generic.

I followed the instructions in the manual I obtained from Sprint ([http://www.nextel.com/en/software_downloads/mobile_broadband/sierra_ac_597e.shtml](http://www.nextel.com/en/software_downloads/mobile_broadband/sierra_ac_597e.shtml) and [http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf](http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf)) precisely and succesfully. However, when I execute 'wvdial' I get the following:
========================================
bill@dell-desktop:~$ wvdial 
--> WvDial: Internet dialer version 1.60 
--> Cannot get information for serial port. 
--> Initializing modem. 
--> Sending: ATZ 
ATZ OK 
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 OK 
--> Modem initialized. 
--> Sending: ATDT#777 
--> Waiting for carrier. 
Caught signal 2: Attempting to exit gracefully... 
ATDT#777 
NO CARRIER 
--> No Carrier! Trying again. 
--> Disconnecting at Wed Mar 25 00:26:34 2009
=========================================

I downloaded and installed the updated driver and the ppp scripts from the Sierra site. When I executed pppd call cdma and ifup ppp0 I get the same result: "no carrier".

dell-desktop kernel: [ 6178.159651] usb 4-1: Sierra USB modem converter now attached to ttyUSB0
dell-desktop kernel: [ 6178.159761] usb 4-1: Sierra USB modem converter now attached to ttyUSB1
dell-desktop kernel: [ 6178.159861] usb 4-1: Sierra USB modem converter now attached to ttyUSB2
dell-desktop kernel: [ 6178.192307] scsi6 : SCSI emulation for USB Mass Storage devices
dell-desktop kernel: [ 6179.753052] scsi 6:0:0:0: Direct-Access Sierra Wireless Storage 2.31 PQ: 0 ANSI: 2
dell-desktop kernel: [ 6179.759329] sd 6:0:0:0: [sdb] Attached SCSI removable disk
dell-desktop kernel: [ 6179.759367] sd 6:0:0:0: Attached scsi generic sg2 type 0
dell-desktop kernel: [ 6282.445040] PPP generic driver version 2.4.2
dell-desktop pppd[18618]: pppd 2.4.4 started by bill, uid 1001
dell-desktop chat[18630]: abort on (NO DIAL TONE)
dell-desktop chat[18630]: abort on (NO ANSWER)
dell-desktop chat[18630]: abort on (NO CARRIER)
dell-desktop chat[18630]: abort on (DELAYED)
dell-desktop chat[18630]: send (AT^M)
dell-desktop chat[18630]: expect (OK)
dell-desktop chat[18630]: AT^M^M
dell-desktop chat[18630]: OK
dell-desktop chat[18630]:  -- got it 
dell-desktop chat[18630]: send (ATZ^M)
dell-desktop chat[18630]: expect (OK)
dell-desktop chat[18630]: ^M
dell-desktop chat[18630]: ATZ^M^M
dell-desktop chat[18630]: OK
dell-desktop chat[18630]:  -- got it 
dell-desktop chat[18630]: send (ATDT#777^M)
dell-desktop chat[18630]: expect (CONNECT)
dell-desktop chat[18630]: ^M
dell-desktop chat[18630]: ATDT#777^M^M
dell-desktop chat[18630]: NO CARRIER
dell-desktop chat[18630]:  -- failed
dell-desktop chat[18630]: Failed (NO CARRIER)
dell-desktop pppd[18618]: Exit.

I spent an hour on the phone with Sprint's "super techs" to be sure that the card was properly activated. I've also searched the web (including these forums) for assistance and have tried several things which I learned from my research.

Before returning the Compass 597 and trying something else I thought maybe someone could see something I'm missing or has worked around this issue.

BTW, following is my /etc/wvdial.conf file:
========================================
[Dialer Defaults]
Modem = /dev/ttyUSB0
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = USB Modem
Phone = #777
Username = ''
Password = ''
Carrier Check = no
Stupid Mode = yes
========================================

TIA for your help.

Regards,
Bill****

---

### Post by wblogan on 2009-03-26
**Resolved.**

Having concluded that my problem was the card I took the Sierra Wireless Compass 597 back to exchange it for another. The store had nothing else but one Sierra Wireless 597. Plugged it in, ran "pppd call cdma" and was connected in seconds. Anyone's guess as to whether the card was bad or Ubuntu had issues with it. All I care is that the 598 works!

---

