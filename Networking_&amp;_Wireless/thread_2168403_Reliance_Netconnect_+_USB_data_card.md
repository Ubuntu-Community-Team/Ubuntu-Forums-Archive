---
title: "Reliance Netconnect + USB data card"
date: 2013-08-17
forum: Networking &amp; Wireless
---

### Post by igodspeed on 2013-08-17
Hi,

I am usiing this data card by this company called Reliance, which is probebly not important. Anyway i tried to follow the mobile broadband wizard but that does not seem to work. The usb data card mounts as both a CD and a USB which makes the kernal confused as to what should be mounted. So after a lot of searching on the net i found this article which requires me to follow the following steps.

Go to disks and unmount the CD part of the datacard which then mounts again as a USB disk.

go to terminal and type lsusb which spits out:
```
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 1bcf:2c18 Sunplus Innovation Technology Inc. 
**Bus 002 Device 006: ID 19d2:ffe9 ZTE WCDMA Technologies MSM <-- Data card**
Bus 002 Device 007: ID 0fca:8004 Research In Motion, Ltd. Blackberry Handheld
Bus 002 Device 004: ID 046d:c05a Logitech, Inc. Optical Mouse M90
```

then type:
```
sudo modprobe usbserial vendor=0x19d2 product=0xffed
```

then type:

sudo wvdialconf which gives

```
 
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   S4   S5   S6   S7   
Modem Port Scan<*1>: S8   S9   S10  S11  S12  S13  S14  S15  
Modem Port Scan<*1>: S16  S17  S18  S19  S20  S21  S22  S23  
Modem Port Scan<*1>: S24  S25  S26  S27  S28  S29  S30  S31  
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB0<*1>: Modem Identifier: ATI -- Model: 119
ttyUSB0<*1>: Speed 9600: AT -- OK
ttyUSB0<*1>: Max speed is 9600; that should be safe.
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
WvModem<*1>: Cannot get information for serial port.
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot get information for serial port.
ttyUSB2<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB2<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB2<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot get information for serial port.
ttyUSB3<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB3<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB3<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot get information for serial port.
ttyUSB4<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB4<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB4<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.

Found a modem on /dev/ttyUSB0.
Modem configuration written to /etc/wvdial.conf.
ttyUSB0<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
```

Then type: 
sudo wvdial which gives:
```
--> WvDial: Internet dialer version 1.61
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT 3100000
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sun Aug 18 01:23:49 2013
--> Pid of pppd: 2857
--> Using interface ppp0
--> pppd: 0Xz 0az 
--> pppd: 0Xz 0az 
--> pppd: 0Xz 0az 
--> local  IP address 101.63.3.120
--> pppd: 0Xz 0az 
--> remote IP address 220.224.141.129
--> pppd: 0Xz 0az 
--> primary   DNS address 220.226.100.40
--> pppd: 0Xz 0az 
--> secondary DNS address 220.226.6.104
--> pppd: 0Xz 0az **<---- Connected to the net**
^CCaught signal 2:  Attempting to exit gracefully...
--> Terminating on signal 15
--> pppd: 0Xz 0az 
--> Connect time 0.5 minutes.
--> pppd: 0Xz 0az 
--> pppd: 0Xz 0az 
```
 
And that is where i am able to connect to the internet. I am sure there has to be an esier way to connect to the net with this data card as this method takes an extremly long time. I had another data card which worked fine as soon as plugged it in after the mobile broadband wizard. Kindly please let me know if there is an easier way to do this!!!!

Another question i had is if there is a way to make the kernal permanently remember the PID and VID of the data card. Also if you could tell me how i can use usbmodes command to make sure it always loads the dongle part only and not the data storage part as a cd drive.

I am very grateful for any help you can provide.

---

