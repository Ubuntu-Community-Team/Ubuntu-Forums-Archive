---
title: "Huawei E122 mobile broadband dongle problems"
date: 2010-02-06
forum: Networking &amp; Wireless
---

### Post by georgie on 2010-02-06
Hi all

I just picked up a mobile broadband (3G) dongle and am having trouble getting it working in Karmic x86.

It's a Huawei E122, and came from UK mobile provider 3. It came with a SIM specifically for data access.

It worked - once -  but hasn't since. So I *know* it can work, but despite making no changes, it stopped working. I tested in on a friend's Mac laptop and it worked fine. I've tried it both with and without a PIN.

lsusb says > Bus 001 Device 011: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem and dmesg says > usb 1-3: GSM modem (1-port) converter now attached to ttyUSB0
[ 2787.411302] option 1-3:1.1: GSM modem (1-port) converter detected
[ 2787.411453] usb 1-3: GSM modem (1-port) converter now attached to ttyUSB1
[ 2787.412079] option 1-3:1.2: GSM modem (1-port) converter detected
[ 2787.412224] usb 1-3: GSM modem (1-port) converter now attached to ttyUSB2


Might the problem be that it's misreporting its ID (it really is an E122!)

I've tried network manager, wvdial, gnome-ppp and wader.

NM (with the correct information entered, using the preselected info for '3' (changing the APN to 'three.co.uk' (as it's PAYG)) whirs, then says "GSM network disconnected"
Wvdial says:

> Feb  6 22:30:59 solar pppd[6176]: CHAP authentication succeeded: Welcome!!
Feb  6 22:30:59 solar pppd[6176]: CHAP authentication succeeded
Feb  6 22:30:59 solar kernel: [ 2111.801908] PPP BSD Compression module registered
Feb  6 22:30:59 solar kernel: [ 2111.822530] PPP Deflate Compression module registered
Feb  6 22:30:59 solar pppd[6176]: Modem hangup

tailing syslog says

> Feb  6 22:43:05 solar NetworkManager: <info>  (ttyUSB0): device state change: 7 -> 9 (reason 13)
Feb  6 22:43:05 solar NetworkManager: <info>  Marking connection '3 connection' invalid.
Feb  6 22:43:05 solar NetworkManager: <info>  Activation (ttyUSB0) failed.
Feb  6 22:43:05 solar NetworkManager: <info>  (ttyUSB0): device state change: 9 -> 3 (reason 0)
Feb  6 22:43:05 solar NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 0).
Feb  6 22:43:05 solar modem-manager: (ttyUSB0) closing serial device...
Feb  6 22:43:05 solar modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (connected -> disconnecting)
Feb  6 22:43:05 solar modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (disconnecting -> connected)
Feb  6 22:43:05 solar NetworkManager: <info>  (eth1): writing resolv.conf to /sbin/resolvconf
Feb  6 22:43:05 solar NetworkManager: <info>  Policy set 'Auto eth1' (eth1) as default for routing and DNS.
Feb  6 22:43:05 solar NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Feb  6 22:43:06 solar modem-manager: (ttyUSB1): re-checking support...
Feb  6 22:43:06 solar modem-manager: (Huawei): (ttyUSB1) deferring support check
Feb  6 22:43:06 solar modem-manager: (ttyUSB2): re-checking support...
Feb  6 22:43:06 solar modem-manager: (Huawei): (ttyUSB2) deferring support check
Feb  6 22:43:06 solar pppd[7571]: Exit.
Feb  6 22:43:08 solar NetworkManager: <debug> [1265496188.001179] ensure_killed(): waiting for ppp pid 7571 to exit
Feb  6 22:43:08 solar NetworkManager: <debug> [1265496188.001403] ensure_killed(): ppp pid 7571 cleaned up


Has anyone got any clues? I can give more logs if necessary.

Ta

georgie

---

### Post by TwilightKnight on 2010-05-30
I got it working with WVdial. 
I threw my settings in wvdial and do it manually.. less than ideal. 

> [Dialer huawei_e620]

Phone = *99***#
Username = vodafone
Password = password
Stupid Mode = 1
Dial Command = ATDT

Init1= ATZ
Modem = /dev/ttyUSB0
Baud = 460800
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem

Init5 = AT+CGDCONT=1,"IP","vfinternet.au"

setting for Australian Vodafone.

---

