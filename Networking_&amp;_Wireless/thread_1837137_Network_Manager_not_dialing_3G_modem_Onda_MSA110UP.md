---
title: "Network Manager not dialing 3G modem Onda MSA110UP"
date: 2011-09-01
forum: Networking &amp; Wireless
---

### Post by cirobr on 2011-09-01
Hello.

I have a 3G modem (Onda MSA110UP) running on a Ubuntu Lucid system for the past six months. Network Manager has always been able to dial up to operator. Recently, this software tries on and on without any success (both manually and automatically. Have checked and confirmed that lsusb shows the modem correctly identified. Have also been able to immediately dial up with wvdial. Output as follows:

> test@note3:~$ sudo wvdial 3g
[sudo] password for test: 
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2
ATQ0 V1 E1 S0=0 &C1 &D2
OK
--> Sending: AT+CGDCONT=1,"IP","zap.vivo.com.br"
AT+CGDCONT=1,"IP","zap.vivo.com.br"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT 7200000
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Thu Sep  1 06:52:20 2011
--> Pid of pppd: 2167
--> Using interface ppp0
--> pppd: 0
--> pppd: 0
--> pppd: 0
--> pppd: 0
--> pppd: 0
--> pppd: 0
--> pppd: 0
--> pppd: 0
--> local  IP address 189.0.102.71
--> pppd: 0
--> remote IP address 10.64.64.64
--> pppd: 0
--> primary   DNS address 200.220.227.57
--> pppd: 0
--> secondary DNS address 200.142.132.32
--> pppd: 0


Would appreciate if anyone could check what's wrong with Network manager.

---

### Post by praseodym on 2011-09-01
Hi,

you may have a look at this checklist:

[http://ubuntuforums.org/showthread.php?t=1831649&highlight=checklist+umts](http://ubuntuforums.org/showthread.php?t=1831649&highlight=checklist+umts)

---

### Post by cirobr on 2011-09-01
Hi,

Have checked and carried out some adjustments (authorization for "modem" word mostly). Network manager still fails, and wvdial works out.

---

### Post by praseodym on 2011-09-01
In Lubuntu the package **modemmanager** is missing by default. Installed?

---

### Post by cirobr on 2011-09-01
Installed and reinstalled. Still fails.

---

### Post by cirobr on 2011-09-01
Some command outputs follow.

> test@note3:~$ lsusb
Bus 007 Device 003: ID 056a:0093 Wacom Co., Ltd 
Bus 007 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 064e:a104 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 013: ID 19d2:0037 ONDA Communication S.p.A. 
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


> test@note3:~$ usb-devices

T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#= 13 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=0037 Rev=00.00
S:  Manufacturer=ONDA COMMUNICATION
S:  Product=ONDA Configuration
S:  SerialNumber=P671A2ODVD010000
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option


Output of lsmod has not shown any visible output related to modem, 3G or USB.

---

### Post by praseodym on 2011-09-01
Hmmm, in our german forum I only find one thread about this ONDA device. The solution was to use kppp as tool.

[http://forum.ubuntuusers.de/topic/t-mobile-zte-637-komme-nicht-ins-netz/?highlight=19d2%3A0037#post-2394528](http://forum.ubuntuusers.de/topic/t-mobile-zte-637-komme-nicht-ins-netz/?highlight=19d2%3A0037#post-2394528)

---

### Post by cirobr on 2011-09-02
Thanks. For the time being I will keep using wvdial. I am opening a case at Launchpad.

---

