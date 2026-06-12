---
title: "ZTE 636 connection drops after a while"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by bbullet on 2009-11-09
Hello people,

I live in Brazil and the 3G wave is picking up around here. I got a ilimited 3g 1 mega plan.

The modem I received is a ZTE 636.

It works perfectly in winxp, stay connected for hours without dropping the line, good speed.

The problem is that I am trying to get rid of winxp. I installed Ubuntu Karmic in my netbook (acer aspire one).

I tried to connect using network manager, it worked but the connection would not last. 

Then I tried to remove network manager and installed wvdial and wicd. Did the winxp trick AT+ZCDRUN=8 which disabled the pendrive mode.

I edited the wvdial to match my network provider login and password. 

I managed to connect, but again the connection would not last.

Can you guys help me? Lots of people here are having the same problem and the modem itself is quite good, helping me will help a lot of people, I will make a translated tutorial when I finally manage to get it working right. I already looked everywhere for the answer but I got no luck.

Here is my wvdial.conf

[Dialer Defaults]
Modem = /dev/ttyUSB2
Modem Type = Analog Modem
ISDN = 0
Baud = 921600
Dial Attempts = 1
Username = brt
Password = brt
Init1 = ATZ
Init2 = AT&F &D2 &C1
Init3 = ATS7=60 S30=0
Init4 = AT+CGDCONT=1,"IP","brt.br"
Phone = *99***1#
Stupid Mode = 1 

Here is my dmesg after connecting the 3g modem:

[  433.328163] usb 1-1: new high speed USB device using ehci_hcd and address 3
[  433.467508] usb 1-1: configuration #1 chosen from 1 choice
[  433.599180] Initializing USB Mass Storage driver...
[  433.599793] scsi2 : SCSI emulation for USB Mass Storage devices
[  433.600342] usbcore: registered new interface driver usb-storage
[  433.600362] USB Mass Storage support registered.
[  433.610338] usb-storage: device found at 3
[  433.610345] usb-storage: waiting for device to settle before scanning
[  433.619127] usbcore: registered new interface driver usbserial
[  433.619177] USB Serial support registered for generic
[  433.619284] usbcore: registered new interface driver usbserial_generic
[  433.619292] usbserial: USB Serial Driver core
[  433.637732] USB Serial support registered for GSM modem (1-port)
[  433.637879] option 1-1:1.0: GSM modem (1-port) converter detected
[  433.638082] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB0
[  433.638147] option 1-1:1.1: GSM modem (1-port) converter detected
[  433.638339] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB1
[  433.638412] option 1-1:1.3: GSM modem (1-port) converter detected
[  433.638625] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB2
[  433.638673] usbcore: registered new interface driver option
[  433.638682] option: v0.7.2:USB Driver for GSM modems
[  438.608894] usb-storage: device scan complete
[  438.610176] scsi 2:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
[  438.612435] sd 2:0:0:0: Attached scsi generic sg1 type 0
[  438.634127] sd 2:0:0:0: [sdb] Attached SCSI removable disk

Here is output of the wvdial command:

root@gilsan-laptop:/home/gilsan# wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT&F &D2 &C1
AT&F &D2 &C1
OK
--> Sending: ATS7=60 S30=0
ATS7=60 S30=0
OK
--> Sending: AT+CGDCONT=1,"IP","brt.br"
AT+CGDCONT=1,"IP","brt.br"
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Mon Nov  9 20:00:39 2009
--> Pid of pppd: 2167
--> Using interface ppp0
--> pppd: (&#972; `&#716; &#65533;&#1036; &#65533;&#1100; &#65533;&#1164; 
--> pppd: (&#972; `&#716; &#65533;&#1036; &#65533;&#1100; &#65533;&#1164; 
--> pppd: (&#972; `&#716; &#65533;&#1036; &#65533;&#1100; &#65533;&#1164; 
--> pppd: (&#972; `&#716; &#65533;&#1036; &#65533;&#1100; &#65533;&#1164; 
--> pppd: (&#972; `&#716; &#65533;&#1036; &#65533;&#1100; &#65533;&#1164; 
--> pppd: (&#972; `&#716; &#65533;&#1036; &#65533;&#1100; &#65533;&#1164; 
--> local  IP address 200.219.123.248
--> pppd: (&#972; `&#716; &#65533;&#1036; &#65533;&#1100; &#65533;&#1164; 
--> remote IP address 10.64.64.64
--> pppd: (&#972; `&#716; &#65533;&#1036; &#65533;&#1100; &#65533;&#1164; 
--> primary   DNS address 201.10.120.2
--> pppd: (&#972; `&#716; &#65533;&#1036; &#65533;&#1100; &#65533;&#1164; 
--> secondary DNS address 201.10.128.2
--> pppd: (&#972; `&#716; &#65533;&#1036; &#65533;&#1100; &#65533;&#1164; 


here is the dmesg after issuing the wvdial command:

[  709.359105] PPP BSD Compression module registered
[  709.394203] PPP Deflate Compression module registered

And here the output of the wvdial after loosing the connection:

--> Disconnecting at Mon Nov  9 20:50:50 2009
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot open /dev/ttyUSB2: No such file or directory
--> Cannot open /dev/ttyUSB2: No such file or directory
--> Cannot open /dev/ttyUSB2: No such file or directory
--> Disconnecting at Mon Nov  9 20:50:51 2009

It's amazing the modem will shutdown completely, turn off the blue blinking light. If I want to reconnect redialing won't work. I must unplug the modem and plug it again.

Does anyone knows a fix to make the connection last longer? The 3g signal around here is very good and it keeps droping all the time.

I kindly appreciate the help from the community. Thanks in advance.

---

### Post by andrein on 2009-12-17
Hello, I have this problem too.I am new to Ubuntu and I cant realize why zte modem continues to disconnect itself ( shutdown completely and disappears from network manager and from places/computer like its not connected to the computer).Can anyone help in this problem please.
At first wasnt like that.Before installing updates it was running for several hours and did not disconnected.Thanks
I have Ubuntu 9.1

---

### Post by andrein on 2009-12-19
Hello, its me again. These is what shows in syslog when the modem disconnects:

Dec 19 18:24:48 alex-desktop NetworkManager: Tried to set deprecated property gsm/band
Dec 19 18:29:05 alex-desktop pppd[4289]: Modem hangup
Dec 19 18:29:05 alex-desktop modem-manager: (ttyUSB2) closing serial device...
Dec 19 18:29:05 alex-desktop pppd[4289]: Connect time 59.2 minutes.
Dec 19 18:29:05 alex-desktop pppd[4289]: Sent 1568360 bytes, received 10621877 bytes.
Dec 19 18:29:05 alex-desktop modem-manager: Removed modem /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-6
Dec 19 18:29:05 alex-desktop NetworkManager: <info>  (ttyUSB2): now unmanaged
Dec 19 18:29:05 alex-desktop NetworkManager: <info>  (ttyUSB2): device state change: 8 -> 1 (reason 36)
Dec 19 18:29:05 alex-desktop NetworkManager: <info>  (ttyUSB2): deactivating device (reason: 36).
Dec 19 18:29:05 alex-desktop kernel: [17400.011495] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Dec 19 18:29:05 alex-desktop kernel: [17400.011519] option 1-6:1.0: device disconnected
Dec 19 18:29:05 alex-desktop kernel: [17400.011598] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Dec 19 18:29:05 alex-desktop kernel: [17400.011619] option 1-6:1.1: device disconnected
Dec 19 18:29:05 alex-desktop kernel: [17400.011698] option: option_instat_callback: error -108
Dec 19 18:29:05 alex-desktop kernel: [17400.013657] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
Dec 19 18:29:05 alex-desktop kernel: [17400.013675] option 1-6:1.3: device disconnected
Dec 19 18:29:05 alex-desktop NetworkManager: <info>  (ttyUSB2): cleaning up...
Dec 19 18:29:05 alex-desktop NetworkManager: <info>  (ttyUSB2): taking down device.
Dec 19 18:29:05 alex-desktop pppd[4289]: Connection terminated.
Dec 19 18:29:05 alex-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Dec 19 18:29:05 alex-desktop NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Dec 19 18:29:05 alex-desktop nm-dispatcher.action: Tried to set deprecated property gsm/band
Dec 19 18:29:05 alex-desktop nm-dispatcher.action: Error in get_property: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist#012
Dec 19 18:29:06 alex-desktop kernel: [17400.140026] usb 1-6: reset high speed USB device using ehci_hcd and address 9
Dec 19 18:29:07 alex-desktop pppd[4289]: Exit.
Dec 19 18:29:08 alex-desktop NetworkManager: <debug> [1261240148.000078] ensure_killed(): waiting for ppp pid 4289 to exit
Dec 19 18:29:08 alex-desktop NetworkManager: <debug> [1261240148.000200] ensure_killed(): ppp pid 4289 cleaned up
Dec 19 18:29:21 alex-desktop kernel: [17415.251273] usb 1-6: device descriptor read/64, error -110
Dec 19 18:29:36 alex-desktop kernel: [17430.481277] usb 1-6: device descriptor read/64, error -110
Dec 19 18:29:36 alex-desktop kernel: [17430.711289] usb 1-6: reset high speed USB device using ehci_hcd and address 9
Dec 19 18:29:51 alex-desktop kernel: [17445.831275] usb 1-6: device descriptor read/64, error -110
Dec 19 18:30:06 alex-desktop kernel: [17461.061276] usb 1-6: device descriptor read/64, error -110
Dec 19 18:30:07 alex-desktop kernel: [17461.291278] usb 1-6: reset high speed USB device using ehci_hcd and address 9
Dec 19 18:30:17 alex-desktop kernel: [17471.711266] usb 1-6: device not accepting address 9, error -110
Dec 19 18:30:17 alex-desktop kernel: [17471.831275] usb 1-6: reset high speed USB device using ehci_hcd and address 9

---

### Post by pdc on 2009-12-19
you might try joining some of these specialist forums

[http://linux.derkeiler.com/Newsgroups/comp.os.linux.networking/](http://linux.derkeiler.com/Newsgroups/comp.os.linux.networking/)

as they have experts who may be able to comment

in some distros, one needs to be a member of the dialout and uucp groups

---

### Post by GeorgeVita on 2009-12-20
Hi to all above! Just some notes: with my ZTE MF636 I can have a relative 'steady' connection on 9.10 using wvdial (or pppd) after 'stopping' network-manager and 'killing' modem-manager as described in [https://bugs.launchpad.net/bugs/408555](https://bugs.launchpad.net/bugs/408555)

Below are my actions for a fully updated 9.10 without any other 'trim' for ZTE modems:

- boot **without** modem
- **sudo stop network-manager**
- **sudo killall modem-manager**
- check that nothing of above is running: **ps -A | grep -i manager**
- attach modem, wait for the Virtual CD icon to appear, right click on it and **eject** it
- use any other way to connect as **wvdial** (as in 1st post), pppd commaaaaand, etc


Regards,
George

---

