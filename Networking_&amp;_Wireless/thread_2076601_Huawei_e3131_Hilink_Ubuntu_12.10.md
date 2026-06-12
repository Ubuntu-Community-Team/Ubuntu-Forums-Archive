---
title: "Huawei e3131 Hilink Ubuntu 12.10"
date: 2012-10-26
forum: Networking &amp; Wireless
---

### Post by qbasasa on 2012-10-26
Hello, 
some time ago i had problem with connecting two Huawei e3131 Hilink modems to Ubuntu.
Hilink formware installed on modem makes it impossible.

To make the switch plug in the modem wait for Hilink to initialize and go to:
[HTML]http://192.168.1.1[/HTML]
Make sure automatic connect and reconect is disabled, disable everything even delete AP using web page.
go to:
[HTML]http://192.168.1.1/html/switchProjectMode.html[/HTML]
modem will disconnect and switch to serial, new device should apear in:
[HTML]/dev/ttyUSB*[/HTML]
connect to it using com trminal of your choice:
EX.
```
minicom -D /dev/ttyUSB0
```
To enable gms modem mode execute the following:
```
AT^U2DIAG=0
```
To switch back HiLink execute:
```
AT^U2DIAG=119
```
Remove the modem and plug it again for changes to take effect.

If after pluging in there are no /dev/ttyUSB* devices check lsusb:
```
# lsusb
Bus 002 Device 002: ID 12d1:1c05 Huawei Technologies Co., Ltd. E173s 3G broadband stick (modem on)
Bus 003 Device 002: ID 0930:0508 Toshiba Corp. Integrated Bluetooth HCI
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
If there is a modem availible...
```
$modprobe usbserial
$modprobe serial
$echo "12d1 1c05" > /sys/bus/usb-serial/drivers/option1/new_id 

```
Now /dev/ttyUSB* should apear.

Use wvdial to connect:

Edit wvdial config:
```
nano /etc/wvdial.conf
```
thats what's my config:
```
[Dialer aero1]
Modem = /dev/ttyUSB0
Init1 = ATRC=0
Init2 = AT^CURC=0
Init3 = AT+CGDCONT=1,"IP","darmowy"
Phone = *99#
Stupid mode = yes
Username = "aero"
Password = "aero"
Dial Attempts = 0
Auto Reconect = yes

[Dialer aero2]
Modem = /dev/ttyUSB3
Init1 = ATRC=0
Init2 = AT^CURC=0
Init3 = AT+CGDCONT=1,"IP","darmowy"
Phone = *99#
Stupid mode = yes

```

to connect execute:
```
wvdial aero1
wvdial aero2
```

the modem will auto reconnect to the network if connection is lost.
Cheers!

---

### Post by jake0 on 2012-12-01
Hi qbasasa,

I am stuck after setting the stick to modem mode. I would like to reset it to HiLink, but I got no idea how to do so without ttyUSB. Can you help me please??

EDIT: Got it. Where is the delete button for a post?

---

### Post by antymat on 2013-03-03
This solution has a few disadvantages, the gravest is - it will not connect to (probably) any Vodafone-based network in Germany. Yes, the diode will be solid blue/green/cyan, but there will be no connection.  There is another way, using just what is already there: usbmodeswitch.  Look here [http://uma-wiki.network-mobility.org/index.php5?title=HSDPA_Interface_-_Configuration_Instructions](http://uma-wiki.network-mobility.org/index.php5?title=HSDPA_Interface_-_Configuration_Instructions) , go to the instructions for E353. The modems have the same USB id, and they behave the same (tested on both). There is no need for any special actions other than adding one config file.

---

### Post by xwizzy on 2013-03-23
Pls am jerry by name and am using hauwei e303s-1 modem...... I recently updated my firmware  to e303update21.005.11.16.200 now i am not seeing any network and i cant even detect itz com port... Pls help hw do i get my default modem features back...
h t t p : / / 1 9 2 . 1 6 8 . 1 . 1 is not working

---

### Post by xwizzy on 2013-03-23
Even if i want to update its showing findin port failed............ I cnt acess or see any network on my dasboard.. Its saying the device has been disconnected or is not available.......pls help....

---

