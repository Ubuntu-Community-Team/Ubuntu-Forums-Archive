---
title: "3G USB modem TechFaith Unstable workaround"
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by bchaussade on 2010-05-02
Hello,

Here is my problem, I have an USB 3G Modem to access broadband internet.
The USB 3G Modem is a flying angel from TechFaith company.

The modem works fine under Windows XP. The USB 3G Modem propose a data partition with an automatic installation of its driver and software.
When I plug the device to the 9.04 Ubuntu workstation it mounts the data partition, but does not find the 3G modem device.

I search the internet to find a solution, and the only working solution I found is the following. However, this solution is not stable, after some minutes the device is dropped (no more ttyUSB). I can not use the same process to enable the device. 

```
su -
eject /dev/sr1
modprobe -v option
echo "1d09 1026" >/sys/bus/usb-serial/drivers/option1/new_id
```

/dev/sr1 is the data partition of the USB modem (lsusb reports it v:1d09 p:1025)
After the eject command, lsusb reports the modem on the bus: v:1d09 p:1026.
After a short time follwing the modprobe command, the /dev/ttyUSB appears and after a short time the network manager propose the connection.
I used the wizard to configure the braodband access (Brunei/B-mobile).

It works for somes minutes, and then the connection drops, the /dev/ttyUSB desappears and I can not redo the process.

Any ideas on how I should it make works fine?

A secondary question, I have to enter the commands in a root shell, the sudo command will not enable the device. Why it does not works with sudo?

thx,
baptiste.

---

### Post by alexfish on 2010-05-02
Hi bchaussade  
 

 does this help
 

 [COLOR=#980101]**[ubuntu]**[/COLOR] [How To : Mobile Broadband Connections [ Ubuntu 10.04 : 9.10 : 9.04 ]]("http://ubuntuforums.org/showthread.php?t=1466490")


regards

alexfish

---

### Post by bchaussade on 2010-05-02
Alexfish,

I'll give a try on the different options I did not yet try, and I'll come back to you with the result.

thx,
Baptiste

---

### Post by bchaussade on 2010-05-10
No solution were found regarding the link provided.


It does not resolve the Techfaith hardware compatibility. I did not find document about this vendor.

Do anybody have some hints or documents about techfaith?

---

### Post by alexfish on 2010-05-10
hi

what happens if you just do the modprobe serial

Code:

sudo modprobe usbserial vendor=0X1d09 product=0x1025

check the modem and the ports with

Code:

dmesg | grep -e "modem" -e "tty"

added:

found a thread here ,although also need to find out why the connection is dropping ; can you post details of the log file from where it connects to end of termination

[http://ubuntuforums.org/showthread.php?t=1281217](http://ubuntuforums.org/showthread.php?t=1281217)

---

### Post by bchaussade on 2010-05-11
hi,

Here the step I took:

1. Eject the device from the GUI

2. sudo modprobe usbserial vendor=0X1d09 product=0x1026

Here the result of the modprobe command in the log:

```
dmesg | grep -e "modem" -e "tty"
[  351.225940] usb 1-1: generic converter now attached to ttyUSB0
[  351.225998] usb 1-1: generic converter now attached to ttyUSB1
[  351.226056] usb 1-1: generic converter now attached to ttyUSB2
[  351.252534] USB Serial support registered for GSM modem (1-port)
[  351.252614] option: v0.7.2:USB Driver for GSM modems
[  361.272550] USB Serial deregistering driver GSM modem (1-port)
[  361.288614] generic ttyUSB2: generic converter now disconnected from ttyUSB2
[  361.288689] generic ttyUSB1: generic converter now disconnected from ttyUSB1
[  361.288760] generic ttyUSB0: generic converter now disconnected from ttyUSB0
[  361.298804] usb 1-1: generic converter now attached to ttyUSB0
[  361.298862] usb 1-1: generic converter now attached to ttyUSB1
[  361.298918] usb 1-1: generic converter now attached to ttyUSB2
[  361.302612] USB Serial support registered for GSM modem (1-port)
[  361.302693] option: v0.7.2:USB Driver for GSM modems
[  361.376046] USB Serial deregistering driver GSM modem (1-port)
[  361.396117] generic ttyUSB2: generic converter now disconnected from ttyUSB2
[  361.396191] generic ttyUSB1: generic converter now disconnected from ttyUSB1
[  361.396260] generic ttyUSB0: generic converter now disconnected from ttyUSB0
[  361.405075] usb 1-1: generic converter now attached to ttyUSB0
[  361.405134] usb 1-1: generic converter now attached to ttyUSB1
[  361.405193] usb 1-1: generic converter now attached to ttyUSB2
[  361.412567] USB Serial support registered for GSM modem (1-port)
[  361.412651] option: v0.7.2:USB Driver for GSM modems
[  361.469540] USB Serial deregistering driver GSM modem (1-port)
[  361.485618] generic ttyUSB2: generic converter now disconnected from ttyUSB2
[  361.485690] generic ttyUSB1: generic converter now disconnected from ttyUSB1
[  361.485786] generic ttyUSB0: generic converter now disconnected from ttyUSB0
[  361.497252] usb 1-1: generic converter now attached to ttyUSB0
[  361.497313] usb 1-1: generic converter now attached to ttyUSB1
[  361.497371] usb 1-1: generic converter now attached to ttyUSB2
[  361.503199] USB Serial support registered for GSM modem (1-port)
[  361.503282] option: v0.7.2:USB Driver for GSM modems
[  361.577064] USB Serial deregistering driver GSM modem (1-port)
[  361.582741] USB Serial support registered for GSM modem (1-port)
[  361.582819] option: v0.7.2:USB Driver for GSM modems

```

Then, I try to use the Gnome Network Manager applet to connect and nothing happen (It works on the other USB modem I am using currently). I even try a new configuration throught the wizard that detect the USB modemn techfaith.

I also try a minicom one /dev/ttyUSB1 & /dev/ttyUSB2, I had an echo at the AT command.


I add the information that are in the syslog while I was trying to connect with the network manager.
```

May 11 21:59:10 bato-9-10 kernel: [  361.396117] generic ttyUSB2: generic converter now disconnected from ttyUSB2
May 11 21:59:10 bato-9-10 kernel: [  361.396133] usbserial_generic 1-1:1.3: device disconnected
May 11 21:59:10 bato-9-10 kernel: [  361.396191] generic ttyUSB1: generic converter now disconnected from ttyUSB1
May 11 21:59:10 bato-9-10 kernel: [  361.396205] usbserial_generic 1-1:1.1: device disconnected
May 11 21:59:10 bato-9-10 kernel: [  361.396260] generic ttyUSB0: generic converter now disconnected from ttyUSB0
May 11 21:59:10 bato-9-10 kernel: [  361.396273] usbserial_generic 1-1:1.0: device disconnected
May 11 21:59:10 bato-9-10 kernel: [  361.396294] USB Serial deregistering driver generic
May 11 21:59:10 bato-9-10 kernel: [  361.396314] usbcore: deregistering interface driver usbserial
May 11 21:59:10 bato-9-10 kernel: [  361.404962] usbcore: registered new interface driver usbserial
May 11 21:59:10 bato-9-10 kernel: [  361.404981] USB Serial support registered for generic
May 11 21:59:10 bato-9-10 kernel: [  361.405004] usbserial_generic 1-1:1.0: generic converter detected
May 11 21:59:10 bato-9-10 kernel: [  361.405075] usb 1-1: generic converter now attached to ttyUSB0
May 11 21:59:10 bato-9-10 kernel: [  361.405086] usbserial_generic 1-1:1.1: generic converter detected
May 11 21:59:10 bato-9-10 kernel: [  361.405134] usb 1-1: generic converter now attached to ttyUSB1
May 11 21:59:10 bato-9-10 kernel: [  361.405144] usbserial_generic 1-1:1.3: generic converter detected
May 11 21:59:10 bato-9-10 kernel: [  361.405193] usb 1-1: generic converter now attached to ttyUSB2
May 11 21:59:10 bato-9-10 kernel: [  361.405210] usbcore: registered new interface driver usbserial_generic
May 11 21:59:10 bato-9-10 kernel: [  361.405212] usbserial: USB Serial Driver core
May 11 21:59:10 bato-9-10 kernel: [  361.412567] USB Serial support registered for GSM modem (1-port)
May 11 21:59:10 bato-9-10 kernel: [  361.412648] usbcore: registered new interface driver option
May 11 21:59:10 bato-9-10 kernel: [  361.412651] option: v0.7.2:USB Driver for GSM modems
May 11 21:59:10 bato-9-10 kernel: [  361.469509] usbcore: deregistering interface driver option
May 11 21:59:10 bato-9-10 modem-manager: (ttyUSB0) opening serial device...
May 11 21:59:10 bato-9-10 kernel: [  361.469540] USB Serial deregistering driver GSM modem (1-port)
May 11 21:59:10 bato-9-10 kernel: [  361.485514] usbcore: deregistering interface driver usbserial_generic
May 11 21:59:10 bato-9-10 kernel: [  361.485618] generic ttyUSB2: generic converter now disconnected from ttyUSB2
May 11 21:59:10 bato-9-10 kernel: [  361.485634] usbserial_generic 1-1:1.3: device disconnected
May 11 21:59:10 bato-9-10 kernel: [  361.485690] generic ttyUSB1: generic converter now disconnected from ttyUSB1
May 11 21:59:10 bato-9-10 kernel: [  361.485704] usbserial_generic 1-1:1.1: device disconnected
May 11 21:59:10 bato-9-10 usb_id[4900]: unable to access '/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/ttyUSB0/tty/ttyUSB0'
May 11 21:59:10 bato-9-10 kernel: [  361.485786] generic ttyUSB0: generic converter now disconnected from ttyUSB0
May 11 21:59:10 bato-9-10 kernel: [  361.485802] usbserial_generic 1-1:1.0: device disconnected
May 11 21:59:10 bato-9-10 kernel: [  361.485822] USB Serial deregistering driver generic
May 11 21:59:10 bato-9-10 kernel: [  361.485842] usbcore: deregistering interface driver usbserial
May 11 21:59:10 bato-9-10 kernel: [  361.497133] usbcore: registered new interface driver usbserial
May 11 21:59:10 bato-9-10 kernel: [  361.497150] USB Serial support registered for generic
May 11 21:59:10 bato-9-10 kernel: [  361.497177] usbserial_generic 1-1:1.0: generic converter detected
May 11 21:59:10 bato-9-10 kernel: [  361.497252] usb 1-1: generic converter now attached to ttyUSB0
May 11 21:59:10 bato-9-10 kernel: [  361.497262] usbserial_generic 1-1:1.1: generic converter detected
May 11 21:59:10 bato-9-10 kernel: [  361.497313] usb 1-1: generic converter now attached to ttyUSB1
May 11 21:59:10 bato-9-10 kernel: [  361.497323] usbserial_generic 1-1:1.3: generic converter detected
May 11 21:59:10 bato-9-10 kernel: [  361.497371] usb 1-1: generic converter now attached to ttyUSB2
May 11 21:59:10 bato-9-10 kernel: [  361.497387] usbcore: registered new interface driver usbserial_generic
May 11 21:59:10 bato-9-10 kernel: [  361.497390] usbserial: USB Serial Driver core
May 11 21:59:10 bato-9-10 kernel: [  361.503199] USB Serial support registered for GSM modem (1-port)
May 11 21:59:10 bato-9-10 kernel: [  361.503279] usbcore: registered new interface driver option
May 11 21:59:10 bato-9-10 kernel: [  361.503282] option: v0.7.2:USB Driver for GSM modems
May 11 21:59:10 bato-9-10 modem-manager: (ttyUSB0) opening serial device...
May 11 21:59:10 bato-9-10 modem-manager: (ttyUSB0) opening serial device...
May 11 21:59:10 bato-9-10 modem-manager: (ttyUSB0): probe requested by plugin 'Generic'
May 11 21:59:10 bato-9-10 modem-manager: (ttyUSB1) opening serial device...
May 11 21:59:10 bato-9-10 modem-manager: (ttyUSB1): probe requested by plugin 'Generic'
May 11 21:59:10 bato-9-10 modem-manager: (ttyUSB1) closing serial device...
May 11 21:59:10 bato-9-10 modem-manager: (ttyUSB1) opening serial device...
May 11 21:59:11 bato-9-10 modem-manager: last message repeated 2 times
May 11 21:59:11 bato-9-10 modem-manager: (ttyUSB1): probe requested by plugin 'Generic'
May 11 21:59:11 bato-9-10 kernel: [  361.577030] usbcore: deregistering interface driver option
May 11 21:59:11 bato-9-10 kernel: [  361.577064] USB Serial deregistering driver GSM modem (1-port)
May 11 21:59:11 bato-9-10 kernel: [  361.582741] USB Serial support registered for GSM modem (1-port)
May 11 21:59:11 bato-9-10 kernel: [  361.582817] usbcore: registered new interface driver option
May 11 21:59:11 bato-9-10 kernel: [  361.582819] option: v0.7.2:USB Driver for GSM modems
May 11 21:59:11 bato-9-10 modem-manager: (ttyUSB2) opening serial device...
May 11 21:59:11 bato-9-10 modem-manager: (ttyUSB2) opening serial device...
May 11 21:59:11 bato-9-10 modem-manager: (ttyUSB2): probe requested by plugin 'Generic'
May 11 21:59:11 bato-9-10 modem-manager: (ttyUSB2) closing serial device...
May 11 21:59:11 bato-9-10 modem-manager: (ttyUSB2) opening serial device...
May 11 21:59:11 bato-9-10 modem-manager: (ttyUSB2): probe requested by plugin 'Generic'
May 11 21:59:11 bato-9-10 modem-manager: (ttyUSB2) closing serial device...
May 11 21:59:11 bato-9-10 modem-manager: (ttyUSB2) opening serial device...
May 11 21:59:11 bato-9-10 modem-manager: (ttyUSB2): probe requested by plugin 'Generic'
May 11 21:59:13 bato-9-10 modem-manager: (ttyUSB1) closing serial device...
May 11 21:59:13 bato-9-10 modem-manager: (Generic): GSM modem /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-1 claimed port ttyUSB1
May 11 21:59:13 bato-9-10 modem-manager: Added modem /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-1
May 11 21:59:13 bato-9-10 modem-manager: Exported modem /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-1 as /org/freedesktop/ModemManager/Modems/0
May 11 21:59:13 bato-9-10 modem-manager: (ttyUSB2) closing serial device...
May 11 21:59:13 bato-9-10 modem-manager: (Generic): GSM modem /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-1 claimed port ttyUSB2
May 11 21:59:13 bato-9-10 NetworkManager: <info>  (ttyUSB1): new GSM device (driver: 'generic')
May 11 21:59:13 bato-9-10 NetworkManager: <info>  (ttyUSB1): exported as /org/freedesktop/NetworkManager/Devices/1
May 11 21:59:13 bato-9-10 NetworkManager: <info>  (ttyUSB1): now managed
May 11 21:59:13 bato-9-10 NetworkManager: <info>  (ttyUSB1): device state change: 1 -> 2 (reason 2)
May 11 21:59:13 bato-9-10 NetworkManager: <info>  (ttyUSB1): deactivating device (reason: 2).
May 11 21:59:13 bato-9-10 NetworkManager: flush_routes: assertion `iface_idx >= 0' failed
May 11 21:59:13 bato-9-10 NetworkManager: flush_addresses: assertion `iface_idx >= 0' failed
May 11 21:59:13 bato-9-10 NetworkManager: <info>  (ttyUSB1): device state change: 2 -> 3 (reason 0)
May 11 21:59:22 bato-9-10 modem-manager: (ttyUSB0) closing serial device...
May 11 22:01:01 bato-9-10 NetworkManager: <info>  Activation (ttyUSB1) starting connection 'B-Mobile Par défaut 1'
May 11 22:01:01 bato-9-10 NetworkManager: <info>  (ttyUSB1): device state change: 3 -> 4 (reason 0)
May 11 22:01:01 bato-9-10 NetworkManager: <info>  Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) scheduled...
May 11 22:01:01 bato-9-10 NetworkManager: <info>  Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) started...
May 11 22:01:01 bato-9-10 NetworkManager: <info>  Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) complete.
May 11 22:01:01 bato-9-10 modem-manager: (ttyUSB1) opening serial device...
May 11 22:02:01 bato-9-10 NetworkManager: <WARN>  stage1_prepare_done(): GSM modem connection failed: Network timeout
May 11 22:02:01 bato-9-10 NetworkManager: <info>  (ttyUSB1): device state change: 4 -> 9 (reason 1)
May 11 22:02:01 bato-9-10 NetworkManager: <info>  Marking connection 'B-Mobile Par défaut 1' invalid.
May 11 22:02:01 bato-9-10 NetworkManager: <info>  Activation (ttyUSB1) failed.
May 11 22:02:01 bato-9-10 NetworkManager: <info>  (ttyUSB1): device state change: 9 -> 3 (reason 0)
May 11 22:02:01 bato-9-10 NetworkManager: <info>  (ttyUSB1): deactivating device (reason: 0).
May 11 22:02:01 bato-9-10 NetworkManager: flush_routes: assertion `iface_idx >= 0' failed
May 11 22:02:01 bato-9-10 NetworkManager: flush_addresses: assertion `iface_idx >= 0' failed
May 11 22:02:01 bato-9-10 modem-manager: (ttyUSB1) closing serial device...

```

Here the log from a dropping ttyUSB. I need to reproduce a relevant capture, this capture was not connected, it was in the connecting attempt.

```

May 11 20:42:03 bato-9-10 kernel: [ 7156.988831] generic ttyUSB0: generic converter now disconnected from ttyUSB0
May 11 20:42:03 bato-9-10 kernel: [ 7156.988854] usbserial_generic 1-1:1.0: device disconnected
May 11 20:42:03 bato-9-10 kernel: [ 7156.989023] generic ttyUSB1: generic converter now disconnected from ttyUSB1
May 11 20:42:03 bato-9-10 kernel: [ 7156.989043] usbserial_generic 1-1:1.1: device disconnected
May 11 20:42:03 bato-9-10 kernel: [ 7156.989135] generic ttyUSB2: generic converter now disconnected from ttyUSB2
May 11 20:42:03 bato-9-10 kernel: [ 7156.989151] usbserial_generic 1-1:1.3: device disconnected
May 11 20:42:03 bato-9-10 kernel: [ 7156.992696] modem-manager[824]: segfault at 0 ip b777d166 sp bfa15aa8 error 6 in libdbus-1.so.3.4.0[b775f000+37000]
May 11 20:42:03 bato-9-10 kernel: [ 7157.101523] usb 1-1: reset high speed USB device using ehci_hcd and address 7
May 11 20:42:03 bato-9-10 kernel: [ 7157.101523] usb 1-1: reset high speed USB device using ehci_hcd and address 7
May 11 20:42:33 bato-9-10 kernel: [ 7187.648523] usb 1-1: reset high speed USB device using ehci_hcd and address 7
May 11 20:43:04 bato-9-10 kernel: [ 7218.196023] usb 1-1: reset high speed USB device using ehci_hcd and address 7
May 11 20:43:14 bato-9-10 kernel: [ 7228.717024] usb 1-1: reset high speed USB device using ehci_hcd and address 7

```

I add also the log from the Win XP driver (It is a translation my OS is not internationaly readeable ! :) )

[INDENT]Hardware Identification: usb\vid_1d09&pid_1026&mi_03

115200,8,N,1, ctsfl=0, rtsctl=1

Init modem
Send : AT<cr>

Receive : <cr><lf>OK<cr><lf>

Interpreted Answer : OK

Send : ATE0V1<cr>

Receive : <cr><lf>OK<cr><lf>

Interpreted Answer : OK

Send : AT<cr>

Receive : <cr><lf>OK<cr><lf>

Interpreted Answer : OK

Send Init sequence
Send : AT+CGDCONT=1,"IP","bmobilewap","0.0.0.0",0,0;+CGQMIN=1,0,0,0,0,0;+CGQREQ=1,0,0,0,0,0;+CGEQREQ=1,4,0,0,0,0,2,0,"0E0","0E0",3,0,0;+CGEQMIN=1,3,0,0,0,0,0,0,"0E0","0E0",2,0,0<cr>

Receive : <cr><lf>OK<cr><lf>

Interpreted Answer : OK
Wait a call
Send : ATS0=0<cr>

Receive*: <cr><lf>OK<cr><lf>

Interpreted answer : OK

115200,8,N,1, ctsfl=0, rtsctl=1

Init Modem
Send : AT<cr>

Receive : <cr><lf>OK<cr><lf>

Interpreted : OK

Send : ATE0V1<cr>

Receive : <cr><lf>OK<cr><lf>

Interpreted Answer : OK

Send : AT<cr>

Receive : <cr><lf>OK<cr><lf>

Interpreted Answer : OK

Send Init sequence
Send : AT+CGDCONT=1,"IP","bmobilewap","0.0.0.0",0,0;+CGQMIN=1,0,0,0,0,0;+CGQREQ=1,0,0,0,0,0;+CGEQREQ=1,4,0,0,0,0,2,0,"0E0","0E0",3,0,0;+CGEQMIN=1,3,0,0,0,0,0,0,"0E0","0E0",2,0,0<cr>

Receive : <cr><lf>OK<cr><lf>

Interpreted Answer : OK

Dialing

Send : ATDT*##***##<cr>

Receive : <cr><lf>CONNECT<cr><lf>

Interpreted : Connected

Connected at 115200 bits/s.
Error: control not connected or unknown
Data compression not set or unknown
[/INDENT]

It does 2 times the init step and then it dial and connects. It works fine even with the two last lines.

I'll capture the log of a dropping session as soon as possible, and post it.

Thanks,

---

