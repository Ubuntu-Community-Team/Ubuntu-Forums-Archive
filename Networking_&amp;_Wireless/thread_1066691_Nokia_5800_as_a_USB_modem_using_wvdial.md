---
title: "Nokia 5800 as a USB modem using wvdial"
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by m3topaz on 2009-02-11
1) Log watch
$ tail -f /var/log/messages | grep USB

2) Plug Nokia USB cable into PC. Log says:

Feb 11 10:55:33 my-laptop kernel: [ 6810.396124] usb 5-1: new high speed USB device using ehci_hcd and address 5
Feb 11 10:55:34 my-laptop kernel: [ 6810.875276] cdc_acm 5-1:1.1: ttyACM0: USB ACM device
Feb 11 10:55:34 my-laptop kernel: [ 6810.876088] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters

That tells me the modem is on ttyACM0

3) Set up wvdial.conf
I was using Vodafone UK, with a pre-pay SIM. If you're in the UK you'll probably find T Mobile cheaper, set up Init3, username & password accordingly

$ sudo gedit /etc/wvdial.conf

[Dialer 5800]
New PPPD = yes
Modem Type = USB Modem
Modem = /dev/ttyACM0
ISDN = 0
Stupid Mode = 1
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","pp.vodafone.co.uk"
Phone = *99#
Username = "web"
Password = "web"
Baud = 921600

4) Dial from a Terminal
$ sudo wvdial 5800

5) Check it works
Open a new Terminal
$ ping live.vodafone.com
PING live.vodafone.com (80.84.1.14) 56(84) bytes of data.

That means the DNS is working, and the connection probably is too. At this point my Skype lit up, so I knew it was OK.

6) Hang up
In the connection Terminal (your first one) use Ctrl + C to end the connection. Here is an example of the last few lines:

--> pppd: [08]&#65533;*[08]
^CCaught signal 2:  Attempting to exit gracefully...
--> Terminating on signal 15
--> pppd: [08]&#65533;*[08]
--> Connect time 0.5 minutes.
--> pppd: [08]&#65533;*[08]
--> pppd: [08]&#65533;*[08]
--> pppd: [08]&#65533;*[08]
--> Disconnecting at Wed Feb 11 11:01:09 2009

*IF* anyone can make the 5800 work with Bluetooth, I'd love to know how. I have an unbranded variant with the latest firmware V 11.0.009. Please post Bluetooth successes, if you have any!

Thank you

---

### Post by bbldox on 2009-02-11
You can update the HAL settings to get this working in another way:

cd /usr/share/hal/fdi/information/10freedesktop
backup 10-modem.fdi
edit 10-modem.fdi
find <match key="@info.parent:usb.vendor_id" int="0x421">
and inside it there is:
<match key="@info.parent:usb.product_id" int_outof="0x4f9;0x64;0x2f;0xab;0x418;0x4f0;0x4ce; 0x43a;0x44d;0x070;0x3a;0x71;0x72;0xb0;0x01;0x419;0 x420;0x425;0x00e;0x432;0x42f;0x445;0x475;0x481;0x4 86;0x48e;0x4c4;0x4c9;0x4df;0x04e6;0x508;0x078">
add ";0x156" into list of codes.

reboot / restart dbus

the next time you plug the device in (in the PC Suite mode) you'll be able to create a connection via 5800.
I found my local operator in the list of available (o.m.g settings are correct!) and just that's all.

---

### Post by m3topaz on 2009-02-11
With Bluetooth, the 5800 is touchy about the order of events in wvdial.conf. I was using an old and fairly well worn conf file, with settings for loads of Nokia, Sony Ericsson and other devices. I messed around with a copy of my N95 modem section and that just didn't work - I now realise that the layout of the section is important.

1) Switch Bluetooth on and visible on the 5800. Find where it is:
$ hcitool scan
Scanning ...
	00:24:3A:AE:46:C7	5800

2) Work out which Bluetooth channel the 5800 is on.

$ sdptool search --bdaddr 00:24:3A:AE:46:C7 dun
Searching for dun on 00:24:3A:AE:46:C7 ...
Service Name: Dial-Up Networking
Service RecHandle: 0x10003
Service Class ID List:
  "Dialup Networking" (0x1103)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 2
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Dialup Networking" (0x1103)
    Version: 0x0100

This happens to be Channel 2.

3) Bind an rfcomm to the channel, I used rfcomm0:
$  sudo rfcomm bind 0 00:24:3A:AE:46:C7 2

4) Edit wvdial.conf and add another dialer. This is the bit I couldn't get right before, however I now realise it's not a lot different to my USB attempt (please don't flame me for my blatant idiocy!)
$ sudo gedit /etc/wvdial.conf

[Dialer 5800b]
New PPPD = yes
Modem = /dev/rfcomm0
Stupid Mode = 1
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","pp.vodafone.co.uk"
Phone = *99#
Username = "web"
Password = "web"
Baud = 460800

5) Dial
$ sudo wvdial 5800b

This connected as for the USB before and worked just fine.

---

### Post by ArchieK on 2009-05-09
While trying to get the 5800 working as a modem on my Dell mini 9 I used Gnome-ppp to configure it but found that although this configuration worked perfectly on an Inspiron 510 with Ubuntu 8.04 the mini 9 with remix 8.04 didn't. Same phone same dialler, I later ......found that in /var/logs/kern.log the port it said the modem was on was different to the one that Gnome-ppp discovered it to be on.

May  9 16:40:43 user kernel: [16585.005216] usb 5-3: new high speed USB device using ehci_hcd and address 8
May  9 16:40:43 user kernel: [16585.136217] usb 5-3: configuration #1 chosen from 1 choice
May  9 16:40:43 user kernel: [16585.139502] cdc_acm 5-3:1.1: ttyACM3: USB ACM device


Gnome-ppp said ttyACM1 (The Inspiron said ttyACM0 and worked) when it was changed to ttyACM3 the connection worked and remained logged on instead of disconnecting with error 16 (modem closed connection)

Bug in Gnome-ppp's disovery process?

---

### Post by anoobp on 2009-08-26
Hi,
Anyone knows about nokia 6100 DKU-5 cable driver for ubuntu 9.04

---

