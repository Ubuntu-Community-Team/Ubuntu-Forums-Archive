---
title: "ZTE AC2726 1x/EVDO Modem : Connect to Internet"
date: 2010-02-20
forum: Networking &amp; Wireless
---

### Post by LinDoc on 2010-02-20
Please help me good people. I have never connected to the internet using ZTE EVDO modem. I know it's being recognised but connection cannot be made. Am new to Ubuntu and Linux. The modem works well in windows. Somebody rescue me please.

---

### Post by pdc on 2010-02-21
if you open a terminal and type

> lsusb

and tell us what you get; 

(I assume it will be 19d2:fff5)

here is a post on how to install; have a read

[http://techsk.blogspot.com/2009/09/installing-usb-modem-zte-ac2726-in.html](http://techsk.blogspot.com/2009/09/installing-usb-modem-zte-ac2726-in.html)

OR:

plug your modem in; 

if you get an icon on the desktop; (ie a little picture for the modem:) RIGHT-CLICK on it;

select EJECT;

then go to Network manager and configure as per this guide:

[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

.......... the guide starts half-way down the page at "CREATE a mobile broadband connection .............."

---

### Post by LinDoc on 2010-02-21
lsusb gives me


******> Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 007: ID 19d2:fff1 ONDA Communication S.p.A. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 018: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Actually i have tried the procedures suggested in those links. However am told this that NO CARRIER . I just have no idea what that is.

---

### Post by pdc on 2010-02-22
so you have two modems plugged in ...........

a ZTE one .............

and a Huawei E220 ...............?

have you tried configuring the latter, if your account has any credit on it?

---

### Post by cong06 on 2010-05-17
I tried the steps on:
[http://techsk.blogspot.com/2009/09/installing-usb-modem-zte-ac2726-in.html](http://techsk.blogspot.com/2009/09/installing-usb-modem-zte-ac2726-in.html)

by doing:
```

wget http://za.archive.ubuntu.com/ubuntu/pool/universe/u/usb-modeswitch/usb-modeswitch_1.0.2-1_i386.deb
sudo dpkg -i usb-modeswitch_1.0.2-1_i386.deb

```
Then I ran the modprobe:
```

root@kimende-s:~# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 008: ID 19d2:fff1  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
root@kimende-s:~# modprobe usbserial vendor=0x19d2 product=0xfff1

```

Re-plugging shows it's still a drive, though:
```


May 17 12:53:49 kimende-s kernel: [ 1763.412023] usb 3-2: new full speed USB device using ohci_hcd and address 9
May 17 12:53:49 kimende-s kernel: [ 1763.627633] usb 3-2: configuration #1 chosen from 1 choice
May 17 12:53:49 kimende-s kernel: [ 1763.630398] scsi17 : SCSI emulation for USB Mass Storage devices
May 17 12:53:50 kimende-s kernel: [ 1763.763342] usb 3-2: USB disconnect, address 9
May 17 12:53:51 kimende-s kernel: [ 1765.310392] usb 3-2: new full speed USB device using ohci_hcd and address 10
May 17 12:53:51 kimende-s kernel: [ 1765.520227] usb 3-2: configuration #1 chosen from 1 choice
May 17 12:53:51 kimende-s kernel: [ 1765.538426] scsi18 : SCSI emulation for USB Mass Storage devices
May 17 12:53:56 kimende-s kernel: [ 1770.544530] scsi 18:0:0:0: Direct-Access     ZTE      USB Storage FFF1 2.31 PQ: 0 ANSI: 2
May 17 12:53:56 kimende-s kernel: [ 1770.556655] sd 18:0:0:0: [sdb] Attached SCSI removable disk
May 17 12:53:56 kimende-s kernel: [ 1770.556824] sd 18:0:0:0: Attached scsi generic sg2 type 0

```

Maybe the real question is how do I get it to work with the Network Manager?

Note: to answer the coming questions, I would like to switch off my Huawei E220 HSDPA Modem, since it's more expensive. I have to use it now though, in order to visit the forums.

---

### Post by pdc on 2010-05-17
here is a clipping from the config file for the latest usb_modeswitch 1.1.2

> # ZTE AC8710
# ZTE AC2726
# and others
#
# Many new ZTE devices use this sequence. There are
# several ID combinations; check your default
#
# Contributor: Michael Khurtsiya, Amit Pundir and others

;DefaultVendor=  0x19d2
;DefaultProduct= 0xfff5

;TargetVendor=   0x19d2
;TargetProduct=  0xffff

# No. 2

;DefaultVendor=  0x19d2
;DefaultProduct= 0xfff6

;TargetVendor=   0x19d2
;**TargetProduct**=  0x**fff1**

# No. 3

;DefaultVendor=  0x19d2
;DefaultProduct= 0xfff5

;TargetVendor=   0x19d2
;TargetProduct=  0xfff1

# only for reference and 0.x versions
# MessageEndpoint=0x05

;MessageContent="5553424312345678c00000008000069f030000000000000000000000000000"


I highlighted the entry that applies to your device

so looks like it has flipped; as you say;

I would suggest you subscribe to the usb_modeswitch forum: 

[http://www.draisberghof.de/usb_modeswitch/bb/](http://www.draisberghof.de/usb_modeswitch/bb/)

Josh oversees it and is very knowledgable; see if he can resolve your issues, and come back here when your device is being flipped, and clearly seen as a modem

(he may also tell you to install the latest version 1.1.2 which you can get from here

[http://packages.debian.org/search?keywords=usb-modeswitch](http://packages.debian.org/search?keywords=usb-modeswitch)

these are debian repositories

---

### Post by cong06 on 2010-05-21
Well, the suggestion of upgrading usb-modeswitch worked.
I installed it from the debian sid.

Now the device shows up in the Network Manager, I'm just not sure what's going on.
When I "dial" it flashes as if it's connecting and then quickly returns to "no connection"


configurations:
number: #777
user: orangefixplus
password: <password with the device, probably not private, but no point in posting>

Everything else is default, there's no real other settings to set.

First off, this is a CMDA device, isn't it? as opposed to GSM...
As I have 2 other GSM connections set up, I would have expected them to show up when I plug any GSM modem in. Since they don't show up when I plug in the ZTE AC2726, it must not be GSM...

syslog (on connection):
```


May 21 10:13:35 kimende-s NetworkManager: <info>  Activation (ttyUSB0) starting connection 'Orange' 
May 21 10:13:35 kimende-s NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 4 
May 21 10:13:35 kimende-s NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled... 
May 21 10:13:35 kimende-s NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started... 
May 21 10:13:35 kimende-s NetworkManager: <debug> [1274426015.551377] nm_serial_device_open(): (ttyUSB0) opening device... 
May 21 10:13:35 kimende-s NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete. 
May 21 10:13:35 kimende-s NetworkManager: <info>  (ttyUSB0): powering up... 
May 21 10:13:35 kimende-s NetworkManager: <WARN>  dial_done(): No carrier 
May 21 10:13:35 kimende-s NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 9 
May 21 10:13:35 kimende-s NetworkManager: <debug> [1274426015.767167] nm_serial_device_close(): Closing device 'ttyUSB0' 
May 21 10:13:35 kimende-s NetworkManager: <info>  Marking connection 'Orange' invalid. 
May 21 10:13:35 kimende-s NetworkManager: <info>  Activation (ttyUSB0) failed. 
May 21 10:13:35 kimende-s NetworkManager: <info>  (ttyUSB0): device state change: 9 -> 3 
May 21 10:13:35 kimende-s NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 0). 
May 21 10:13:35 kimende-s NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
May 21 10:13:35 kimende-s NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed

```

syslog (on inserting the device)
```


May 21 10:13:03 kimende-s kernel: [ 3398.443217] usb 2-2: new full speed USB device using ohci_hcd and address 10
May 21 10:13:03 kimende-s kernel: [ 3398.652214] usb 2-2: configuration #1 chosen from 1 choice
May 21 10:13:03 kimende-s kernel: [ 3398.660047] scsi46 : SCSI emulation for USB Mass Storage devices
May 21 10:13:03 kimende-s kernel: [ 3398.664695] usb-storage: device found at 10
May 21 10:13:03 kimende-s kernel: [ 3398.664701] usb-storage: waiting for device to settle before scanning
May 21 10:13:03 kimende-s usb_modeswitch: switching 19d2:fff5 (ZTE, Incorporated: USB Storage)
May 21 10:13:04 kimende-s kernel: [ 3399.415647] usb 2-2: USB disconnect, address 10
May 21 10:13:05 kimende-s kernel: [ 3400.964029] usb 2-2: new full speed USB device using ohci_hcd and address 11
May 21 10:13:05 kimende-s kernel: [ 3401.168617] usb 2-2: configuration #1 chosen from 1 choice
May 21 10:13:05 kimende-s kernel: [ 3401.171188] option 2-2:1.0: GSM modem (1-port) converter detected
May 21 10:13:05 kimende-s kernel: [ 3401.171292] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
May 21 10:13:05 kimende-s kernel: [ 3401.174303] option 2-2:1.1: GSM modem (1-port) converter detected
May 21 10:13:05 kimende-s kernel: [ 3401.177120] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
May 21 10:13:05 kimende-s kernel: [ 3401.179334] option 2-2:1.2: GSM modem (1-port) converter detected
May 21 10:13:05 kimende-s kernel: [ 3401.179438] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
May 21 10:13:05 kimende-s kernel: [ 3401.182338] option 2-2:1.3: GSM modem (1-port) converter detected
May 21 10:13:05 kimende-s kernel: [ 3401.182448] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB3
May 21 10:13:05 kimende-s kernel: [ 3401.185354] option 2-2:1.4: GSM modem (1-port) converter detected
May 21 10:13:05 kimende-s kernel: [ 3401.185461] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB4
May 21 10:13:05 kimende-s kernel: [ 3401.196070] scsi47 : SCSI emulation for USB Mass Storage devices
May 21 10:13:05 kimende-s kernel: [ 3401.201044] usb-storage: device found at 11
May 21 10:13:05 kimende-s kernel: [ 3401.201049] usb-storage: waiting for device to settle before scanning
May 21 10:13:06 kimende-s usb_modeswitch: switched to 19d2:fff1 (ZTE, Incorporated: ZTE CDMA Tech)
May 21 10:13:06 kimende-s logger: usb_modeswitch: adding device ID 19d2:fff1 to driver "option"
May 21 10:13:06 kimende-s NetworkManager: <info>  (ttyUSB0): found serial port (udev:CDMA  hal:) 
May 21 10:13:06 kimende-s NetworkManager: <info>  (ttyUSB0): deferring until all ports found 
May 21 10:13:10 kimende-s kernel: [ 3406.201528] usb-storage: device scan complete
May 21 10:13:10 kimende-s kernel: [ 3406.205250] scsi 47:0:0:0: Direct-Access     ZTE      USB Storage FFF1 2.31 PQ: 0 ANSI: 2
May 21 10:13:10 kimende-s kernel: [ 3406.211658] sd 47:0:0:0: [sdc] Attached SCSI removable disk
May 21 10:13:10 kimende-s kernel: [ 3406.211812] sd 47:0:0:0: Attached scsi generic sg3 type 0
May 21 10:13:10 kimende-s NetworkManager: <info>  Re-checking deferred serial ports 
May 21 10:13:11 kimende-s NetworkManager: <info>  (ttyUSB0): new Modem device (driver: 'option') 
May 21 10:13:11 kimende-s NetworkManager: <info>  (ttyUSB0): exported as /org/freedesktop/Hal/devices/usb_device_19d2_fff1_noserial_if0_serial_usb_0 
May 21 10:13:12 kimende-s NetworkManager: <info>  (ttyUSB2): ignoring due to lack of mobile broadband capabilties 
May 21 10:13:12 kimende-s NetworkManager: <info>  (ttyUSB4): ignoring due to lack of mobile broadband capabilties 
May 21 10:13:15 kimende-s NetworkManager: <info>  (ttyUSB0): device state change: 1 -> 2 
May 21 10:13:15 kimende-s NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 2). 
May 21 10:13:15 kimende-s NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
May 21 10:13:15 kimende-s NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed
May 21 10:13:15 kimende-s NetworkManager: <info>  (ttyUSB0): device state change: 2 -> 3 
May 21 10:13:15 kimende-s NetworkManager: <info>  (ttyUSB3): ignoring due to lack of mobile broadband capabilties 
May 21 10:13:17 kimende-s NetworkManager: <info>  (ttyUSB1): ignoring due to lack of mobile broadband capabilties 
May 21 10:13:35 kimende-s NetworkManager: <info>  Activation (ttyUSB0) starting connection 'Orange' 
May 21 10:13:35 kimende-s NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 4 
May 21 10:13:35 kimende-s NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled... 
May 21 10:13:35 kimende-s NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started... 
May 21 10:13:35 kimende-s NetworkManager: <debug> [1274426015.551377] nm_serial_device_open(): (ttyUSB0) opening device... 
May 21 10:13:35 kimende-s NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete. 
May 21 10:13:35 kimende-s NetworkManager: <info>  (ttyUSB0): powering up... 
May 21 10:13:35 kimende-s NetworkManager: <WARN>  dial_done(): No carrier 
May 21 10:13:35 kimende-s NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 9 
May 21 10:13:35 kimende-s NetworkManager: <debug> [1274426015.767167] nm_serial_device_close(): Closing device 'ttyUSB0' 
May 21 10:13:35 kimende-s NetworkManager: <info>  Marking connection 'Orange' invalid. 
May 21 10:13:35 kimende-s NetworkManager: <info>  Activation (ttyUSB0) failed. 
May 21 10:13:35 kimende-s NetworkManager: <info>  (ttyUSB0): device state change: 9 -> 3 
May 21 10:13:35 kimende-s NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 0). 
May 21 10:13:35 kimende-s NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
May 21 10:13:35 kimende-s NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed

```

---

### Post by alexfish on 2010-05-21
hi

looking at the above , it is possible the modem manager is returning the wrong enumeration for the device, this can happen if the device is capable of both CDMA AND GSM 

can you try  using ppp or wvdial 

also looks if up to 5 ports are registering 

I could suggest using the following code from the terminal

Code:

dmesg | grep -e "modem" -e "tty"  

when in  wvdial or ppp , try different ports listed from the above command

see how you get on

also remember there can be a difference with the init codes when using CDMA


regards

alexfish

---

### Post by cong06 on 2010-05-21
Well, I tried gnome-ppp since it gives the control of wvdial, and I haven't had a chance to figure out wvdial yet...

The default settings with gnome-ppp do the same thing that the network manager was doing, but like you said, the init codes are probably different.

So I changed them. I found a page:
[http://sam1blog.blogspot.com/2008/03/connect-internet-via-nokia-2116-cdma-ca.html](http://sam1blog.blogspot.com/2008/03/connect-internet-via-nokia-2116-cdma-ca.html)
where someone was using cdma...
So I copied these:
```

AT+crm=1
AT+cso=33
ATE0V1

```

and so it returns this:
```


--> Ignoring malformed input line: ";Do NOT edit this file by hand!"
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT+crm=1
AT+crm=1
OK
--> Sending: AT+cso=33
AT+cso=33
ERROR
--> Bad init string.

```

Any help to find the init codes?

---

### Post by alexfish on 2010-05-21
hi

from the post where you had the connection with wvdial works

look at the wvdial.conf file and enter same details in the Gnomeppp , you will have to use the Setting to get to the pages / 

don't follow **init codes** from **other sources** unless your **absolutely sure** they are for your **modem and your provider** .

also the int codes should be capital  look at the error

AT+crm=1
OK
--> Sending: AT+cso=33
AT+cso=33
ERROR
--> Bad init string.

 so from this , your modem may not recognise the command , or maybe has to be in capital letters

could you post the details of the wvdial.conf file , 

regards

alex fish

---

### Post by pdc on 2010-05-21
very happy to be told I am wrong, but I understand with CDMA, there is no simcard, so when you dial #777 the crucial ID is username and password; ..... they gotta be right ..... that's how CDMA knows who is ringing it ..

with GSM, and a simcard, it is that device that the network detects, and username and password are essentially "blank" for those systems;

so in this blog, 

> [http://techsk.blogspot.com/2009/09/installing-usb-modem-zte-ac2726-in.html](http://techsk.blogspot.com/2009/09/installing-usb-modem-zte-ac2726-in.html)

the blogger quotes
> Password = <**Your Password**>
Username = <**Your Login Name**>.......... so they need to be right

the log seems to say the device is switched; and fine as ttyUSB0;

my money is on the script being the problem, not the device: ie check wvdial.conf if using wvdial .......... etc

I worry 

> orangfixplus is too general to be the correct username ?

---

### Post by cong06 on 2010-05-22
> **pdc said:**
> very happy to be told I am wrong, but I understand with CDMA, there is no simcard, so when you dial #777 the crucial ID is username and password; ..... they gotta be right ..... that's how CDMA knows who is ringing it ..

with GSM, and a simcard, it is that device that the network detects, and username and password are essentially "blank" for those systems;

Well, maybe my "CDMA" can also act as a GSM... The interesting thing about this CDMA is that it has a SIM Card (or RUIM card, as they call it in the manual) and while they are very specific about the "#777" and the username and password, they only say that the username should be "orangefixedplus" and the password the same for all devices.
> 
On "Settings type in the "User Name:" orangefixedplus and "Password:" xxx. Under "Mode" choose "EVDO".

It's in a manual that there is no way they would make a different one for each modem.

I was going to take a picture, but:
1) camera not available right now
2) I think I explained well enough?

Unfortunately there's no documentation. I'll probably have to call the company... but I'm not too optimistic about their response.
Any ideas on reverse engineering the windows software? (actually, it comes with support for mac OSX also...)

---

### Post by cong06 on 2010-06-02
No luck from Orange, Telecom Kenya "We only support windows"

Anyway, as 10.04 is out, I'm focusing more on getting it to work in Lucid (though again, fixing it in jaunty would be appreciated).

Here's "/var/log/syslog" in lucid.
```

Jun  2 12:29:47 ubuntu1 NetworkManager: <info>  Marking connection 'Orange' invalid.
Jun  2 12:29:47 ubuntu1 NetworkManager: <info>  Activation (ttyUSB0) failed.
Jun  2 12:29:47 ubuntu1 NetworkManager: <info>  (ttyUSB0): device state change: 9 -> 3 (reason 0)
Jun  2 12:29:47 ubuntu1 NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 0).
Jun  2 12:30:23 ubuntu1 NetworkManager: <WARN>  stage1_prepare_done(): CDMA modem connection failed: (32) No service
Jun  2 12:30:23 ubuntu1 NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 9 (reason 0)
Jun  2 12:30:23 ubuntu1 NetworkManager: <info>  Activation (ttyUSB0) failed.
Jun  2 12:30:23 ubuntu1 NetworkManager: <info>  (ttyUSB0): device state change: 9 -> 3 (reason 0)
Jun  2 12:30:23 ubuntu1 NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 0).
Jun  2 12:30:36 ubuntu1 NetworkManager: <info>  Activation (ttyUSB0) starting connection 'Orange'
Jun  2 12:30:36 ubuntu1 NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 4 (reason 0)
Jun  2 12:30:36 ubuntu1 NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  2 12:30:36 ubuntu1 NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
Jun  2 12:30:36 ubuntu1 NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
Jun  2 12:31:37 ubuntu1 NetworkManager: <WARN>  stage1_prepare_done(): CDMA modem connection failed: (32) No service
Jun  2 12:31:37 ubuntu1 NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 9 (reason 0)
Jun  2 12:31:37 ubuntu1 NetworkManager: <info>  Marking connection 'Orange' invalid.
Jun  2 12:31:37 ubuntu1 NetworkManager: <info>  Activation (ttyUSB0) failed.
Jun  2 12:31:37 ubuntu1 NetworkManager: <info>  (ttyUSB0): device state change: 9 -> 3 (reason 0)
Jun  2 12:31:37 ubuntu1 NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 0).

```

---

### Post by pdc on 2010-06-02
I would again recommend you join the usb_modeswitch forum

[http://www.draisberghof.de/usb_modeswitch/bb/](http://www.draisberghof.de/usb_modeswitch/bb/)

Josh oversees the usb_modeswitch and is moderator of his forum;

he knows a vast amount

---

### Post by alexfish on 2010-06-02
Hi cong06

looking through your posts ,and the log files , indicate at times two modems have been connected at the same time

can you clarify which modem you are trying to configure

also when trying to configure a modem ensure that only that modem is connected

we can now start from this , and post the results

from the terminal 

Code:

dmesg | grep -e "modem" -e "tty"

---

### Post by cong06 on 2010-06-02
True. Some of the other posts have been with more then one modem. However, the lucid post was only one modem, the one in question.

```

dmesg | grep -e "modem" -e "tty"
[    0.000000] console [tty0] enabled
[    0.374372] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.374538] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.375147] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.375386] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[  311.191970] USB Serial support registered for GSM modem (1-port)
[  311.193672] option 2-2:1.0: GSM modem (1-port) converter detected
[  311.195513] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
[  311.195594] option 2-2:1.1: GSM modem (1-port) converter detected
[  311.197021] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
[  311.197111] option 2-2:1.2: GSM modem (1-port) converter detected
[  311.201443] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
[  311.201540] option 2-2:1.3: GSM modem (1-port) converter detected
[  311.204893] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB3
[  311.204988] option 2-2:1.4: GSM modem (1-port) converter detected
[  311.207680] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB4
[  311.207816] option: v0.7.2:USB Driver for GSM modems
[  334.230863] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  334.240171] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  334.247254] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[  334.261393] option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
[  334.266388] option1 ttyUSB4: GSM modem (1-port) converter now disconnected from ttyUSB4
[  348.271649] option 2-1:1.0: GSM modem (1-port) converter detected
[  348.271915] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB0
[  348.275588] option 2-1:1.1: GSM modem (1-port) converter detected
[  348.280837] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB1
[  348.283066] option 2-1:1.2: GSM modem (1-port) converter detected
[  348.292719] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB2
[  348.297916] option 2-1:1.3: GSM modem (1-port) converter detected
[  348.298184] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB3
[  348.303599] option 2-1:1.4: GSM modem (1-port) converter detected
[  348.313594] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB4
[  366.967688] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  366.968567] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  366.968941] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[  366.969307] option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
[  366.969670] option1 ttyUSB4: GSM modem (1-port) converter now disconnected from ttyUSB4
[  384.974489] option 1-2:1.0: GSM modem (1-port) converter detected
[  384.974751] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
[  384.977351] option 1-2:1.1: GSM modem (1-port) converter detected
[  384.977876] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
[  384.981036] option 1-2:1.2: GSM modem (1-port) converter detected
[  384.985285] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
[  384.998881] option 1-2:1.3: GSM modem (1-port) converter detected
[  384.999700] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB3
[  385.003174] option 1-2:1.4: GSM modem (1-port) converter detected
[  385.004797] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB4
[  519.737985] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  519.738991] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  519.739377] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[  519.739736] option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
[  519.762748] option1 ttyUSB4: GSM modem (1-port) converter now disconnected from ttyUSB4
[ 1052.594892] option 1-2:1.0: GSM modem (1-port) converter detected
[ 1052.595177] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
[ 1052.597574] option 1-2:1.1: GSM modem (1-port) converter detected
[ 1052.598138] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
[ 1052.601126] option 1-2:1.2: GSM modem (1-port) converter detected
[ 1052.612005] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
[ 1052.619587] option 1-2:1.3: GSM modem (1-port) converter detected
[ 1052.620696] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB3
[ 1052.625697] option 1-2:1.4: GSM modem (1-port) converter detected
[ 1052.626528] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB4
[ 1087.159354] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[ 1087.169786] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[ 1087.177021] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[ 1087.186130] option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
[ 1087.196167] option1 ttyUSB4: GSM modem (1-port) converter now disconnected from ttyUSB4
[ 1101.689837] option 1-2:1.0: GSM modem (1-port) converter detected
[ 1101.690100] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
[ 1101.696464] option 1-2:1.1: GSM modem (1-port) converter detected
[ 1101.697008] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
[ 1101.698950] option 1-2:1.2: GSM modem (1-port) converter detected
[ 1101.699516] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
[ 1101.703065] option 1-2:1.3: GSM modem (1-port) converter detected
[ 1101.717273] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB3
[ 1101.723246] option 1-2:1.4: GSM modem (1-port) converter detected
[ 1101.724645] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB4

```
I feel I should mention at this point the modem was detected to being /dev/ttyUSB0

---

### Post by alexfish on 2010-06-02
OK

the device is recognised

your device would appear to have 4 ports , some of the ports can have other functions, as what they all are I can only guess, the first thing is to get the modem working , for now I suggest using wvdial as this will allow you to see what the other ports can be accessed, this is hard to do with NM. As NM uses the modem manager , not the easiest thing to negotiate if you a novice.
 
To find out  actual dev/ ttyXXXX  is using the same port number try this command from the terminal
 
Code:

grep . /sys/bus/usb/devices/*/tty*/port_number
 
if the highlighted port_numbers are the same then everything should be ok
 
if you have been trying the modem with NM , disconnect the modem and reconnect
 

 Next we will back up of your wvdial.conf . Then configure wvdial
 

to back up of your wvdial.conf

**Code:**
 
sudo su
 
then
 
**Code:**
 
cp /etc/wvdial.conf /etc/wvdial.conf_bak
 
then to delete the contents of the wvdial.conf
 
**Code:**
 
echo -n > /etc/wvdial.conf
 
then
 
**Code:**
 
wvdialconf
 
now have a look at the wvdial.conf
 
**Code:**

 gedit /etc/wvdial.conf
 
you will have to decide which port to use  
 buy changing the  
 
**Modem = /dev/ttyUSB0** to use one of the other ports IE :**Modem = /dev/ttyUSB2** or other
 
also remove the  “** ; **“  to look like and enter your details after the =
 
Phone = <Target Phone Number> 
Username = <Your Login Name>
  Password = <Your Password>
 
save and exit gedit

to test the connection
[B]
Code:[/B]

wvdial


 how did this go
 

 please remember to only have one modem attached  , and for now plug it into the same port
 

  I also suspect this modem may be capable of sms texts , for this you could install wammu

---

### Post by dineshs on 2010-06-02
This link gives another option for init string
[http://blog.jfdesignnet.com/?p=414](http://blog.jfdesignnet.com/?p=414)

---

### Post by cong06 on 2010-06-03
> **alexfish said:**
> 
grep . /sys/bus/usb/devices/*/tty*/port_number

(I like codeblocks)
```

/sys/bus/usb/devices/1-2:1.0/tty0/port_number:0
/sys/bus/usb/devices/1-2:1.1/tty1/port_number:0
/sys/bus/usb/devices/1-2:1.2/tty2/port_number:0
/sys/bus/usb/devices/1-2:1.3/tty3/port_number:0
/sys/bus/usb/devices/1-2:1.4/tty4/port_number:0

```

> **alexfish said:**
>  

you will have to decide which port to use  
 buy changing the  
 
**Modem = /dev/ttyUSB0** to use one of the other ports IE :**Modem = /dev/ttyUSB2** or other

Well, you just had me delete this stuff.
So I went ahead and ran "wvdialconf" and created a configuration.
Since wvidalconf knows which modem it's on better then me, I figure I should just trust 

> **alexfish said:**
>  
also remove the  “** ; **“  to look like and enter your details after the =
 
Phone = <Target Phone Number> 
Username = <Your Login Name>
  Password = <Your Password>
 


Done. wvdial returns this:
```

root@phaff:~# wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
NO CARRIER
--> No Carrier!  Trying again.
^CCaught signal 2:  Attempting to exit gracefully...
--> Disconnecting at Thu Jun  3 10:28:28 2010

```
Looks like it did when I used gnome-ppp (except it doesn't know how to quit).
I suspect that while you enjoy wvidal, gnome-ppp = wvdial using wvdialconf. Especially since gnome-ppp actually runs wvdial.

---

### Post by cong06 on 2010-06-03
> **dineshs said:**
> This link gives another option for init string
[http://blog.jfdesignnet.com/?p=414](http://blog.jfdesignnet.com/?p=414)

Unfortunately that Init string is the same one that gnome-ppp and wvdialconf gives as the default Init2.

So I've tried it with no luck.

:/

---

### Post by cong06 on 2010-06-03
I just remembered that the modem has a PIN number. There should be an Init string to place the pin..

I tried:
```

Init3= AT+CPIN=XXXX

```

But it doesn't like the string. "--> Bad init string."
There will have to be a way to send the PIN number to the modem...

---

### Post by alexfish on 2010-06-03
> **cong06 said:**
> I just remembered that the modem has a PIN number. There should be an Init string to place the pin..

I tried:
```

Init3= AT+CPIN=XXXX

```

But it doesn't like the string. "--> Bad init string."
There will have to be a way to send the PIN number to the modem...

I think the first init should be the pin number

IE: Init1= AT+CPIN=XXXX

then renumber the others

---

### Post by cong06 on 2010-06-03
Unfortunately I already thought of that:
```


root@phaff:~# wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: AT+CPIN=XXXX
AT+CPIN=XXXX
ERROR
--> Bad init string.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: AT+CPIN=XXXX
AT+CPIN=XXXX
ERROR
--> Bad init string.
^CCaught signal 2:  Attempting to exit gracefully...

```

wvdial.conf:
```


[Dialer Defaults]
Init1 = AT+CPIN=XXXX
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Phone = #777
ISDN = 0
Username = orangefixedplus
Init2 = ATZ
Password = orange
Modem = /dev/ttyUSB0
Baud = 9600

```

---

### Post by alexfish on 2010-06-04
hi

the modem is not recognising the code been sent

have you tried different modem ports

where it says Modem = /dev/ ttyXXXX

---

### Post by cong06 on 2010-06-04
I tried "/dev/ttyUSB1" to "/dev/ttyUSB4"
And got this output for all of them:
```

--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: AT+CPIN=XXXX
--> Sending: ATQ0
--> Re-Sending: AT+CPIN=XXXX
--> Modem not responding.

```

I think I should note that when I created a blank wvdial.conf file and re-ran wvdialconf, it gave this output:
```


Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB0<*1>: Modem Identifier: ATI -- Manufacturer: QUALCOMM INCORPORATED
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
It looks like somethings failing...

---

### Post by alexfish on 2010-06-04
Strange ? 

the Identifier ATI for a zte device normally looks like this one below , this has been done through a serial terminal although this is a different model

ATI

responce

Manufacturer: ZTE INCORPORATED 
Model: MF626 
Revision: BD_TMOP673M3V1.0.1B07 
IMEI: xxxxxxxxxxxx
+GCAP: +CGSM,+DS,+ES

what kind of system do you have , desktop or laptop and the make etc

and can you post the results of , from the terminal

Code:

lsusb

---

### Post by cong06 on 2010-06-04
> **alexfish said:**
> Strange ? 

the Identifier ATI for a zte device normally looks like this one below , this has been done through a serial terminal although this is a different model

ATI

responce

Manufacturer: ZTE INCORPORATED 
Model: MF626 
Revision: BD_TMOP673M3V1.0.1B07 
IMEI: xxxxxxxxxxxx
+GCAP: +CGSM,+DS,+ES

what kind of system do you have , desktop or laptop and the make etc

In order to have a computer that does not have two modems plugged in, I'm using lucid, Ubuntu Netbook Remix on my Asus Eee PC 701SD.
> **alexfish said:**
> 
and can you post the results of , from the terminal

Code:

lsusb
```

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR="Red"]Bus 002 Device 007: ID 19d2:fff1 ONDA Communication S.p.A.[/COLOR]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 125f:1036 A-DATA Technology Co., Ltd. 
Bus 001 Device 002: ID 093a:2700 Pixart Imaging, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
The device is reddened. It must be that device, because:
1) on removing it it disappears
2) It has the same id as the device: 19d2:fff1

But it certainly looks differently than I expected.

---

### Post by alexfish on 2010-06-05
hi

Possible your locked out , but can't tell from here , but does not matter what you try to send ,gets rejected by the modem , so I suggest you contacted your provider.

also here is a tip for finding if the modem requires the cpin use the AT command AT+CPIN?

the first inits would look like the below , this modem requires a PIN number

init1 = AT+CPIN?
init2 = AT+CPIN = 2874
init3 = AT+CPIN?

the below is the response

--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.

--> Sending: AT+CPIN?

AT+CPIN?
[COLOR=Blue]+CPIN: SIM PIN[/COLOR] <==== modem requires sim pin
[COLOR=Blue]OK[/COLOR]

--> Sending: AT+CPIN = 2874
[COLOR=Blue]AT+CPIN = 2874 [/COLOR]
[COLOR=Blue]OK [/COLOR]                     <===Pin code accepted

--> Sending: AT+CPIN?
AT+CPIN?
[COLOR=Blue]+CPIN: READY [/COLOR] <======shows the modem is now ready
[COLOR=Blue]OK[/COLOR]

For info
To ascertain which code must be entered (or not), the following query command can be
used: AT+CPIN?
The possible responses are:
    +CPIN: READY          ME is not pending for any password
    +CPIN: UIM PIN        CHV1 is required
    +CPIN: UIM PUK        PUK1 is required
    +CPIN: UIM PIN2       CHV2 is required
    +CPIN: UIM PUK2       PUK2 is required
    +CPIN: PH-UIM PIN     UIM lock (phone-to-UIM) is required
    +CPIN: PH-NET PIN     Network personalization is required
    +CME ERROR: <err>     SIM failure (13) absent (10) etc.

Note: that in this case the mobile equipment does not end its response with the OK string.
The response &#8216;+CME ERROR: 13&#8217; (SIM failure) is returned after 10 unsuccessful PUK
attempts. The SIM card is then out of order and must be replaced by a new one.



regards

alexfish

---

