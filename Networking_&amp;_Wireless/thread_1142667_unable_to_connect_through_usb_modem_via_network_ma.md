---
title: "unable to connect through usb modem via network manager [Debian Lenny]"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by ekalavyan on 2009-04-29
Hi

I am having trouble trying to configure my huawei E180 usb modem to connect using Network Manager ( ver 0.6.6). I get the option to 'Connect to ppp0 via modem' but that does nothing. 'network-admin' will let me add the ppp connection, but it automatically unticks itself the moment i apply changes.

I can connect without any issues using wvdial however. Please advice. Thanks

Using the following;
Debian Lenny running 2.6.26-1-686.

Output of dmesg:
[ 1955.677643] usb 6-1: GSM modem (1-port) converter now attached to ttyUSB0
[ 1955.720264] usb 6-1: GSM modem (1-port) converter now attached to ttyUSB1
[ 1959.720260] scsi13 : SCSI emulation for USB Mass Storage devices
[ 1963.729236] scsi14 : SCSI emulation for USB Mass Storage devices

wvdial.conf:

[Dialer Defaults]
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = 1
Modem Type = Analog Modem
ISDN = 0
Phone = *99#
Modem = /dev/ttyUSB0
Username = user
Dial Command = ATDT
Password = pass
Baud = 9600

---

