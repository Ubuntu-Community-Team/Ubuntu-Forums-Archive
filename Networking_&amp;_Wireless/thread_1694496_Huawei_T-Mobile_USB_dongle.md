---
title: "Huawei T-Mobile USB dongle"
date: 2011-02-24
forum: Networking &amp; Wireless
---

### Post by doperative on 2011-02-24
I bought a Huawei T-Mobile USB dongle, I plugged it it but it don't connect, how can I get it to work on Ubuntu. I previously tried with a borrowed Virgin and O3 dongle and they worked no problem ..

---

### Post by alexfish on 2011-02-24
Hi

Can post which version of Ubuntu

+ results of this command from the terminal

```
lsusb -t
```

---

### Post by doperative on 2011-02-25
> **alexfish said:**
> Hi
 
Can post which version of Ubuntu
 
+ results of this command from the terminal
 
```
lsusb -t
```
 
 
Will do, as soon as I get home, I can't access the Internet at home ..
 
I tried manually installing from the network icon, but I get a prompt for a keyring password. I entered my own username password but it was rejected. I see solutions to that elsewhere, I'll try when I get back.

---

### Post by alexfish on 2011-02-25
Hi

without info hard to solve , + if no other means of connection
most common problems with huawie devices are

the option driver failing to load ,if 3g can try from the terminal
```
sudo modprobe option
```see what happens

also depending on version of Ubuntu try this command from the terminal
```
usb-devices
```this will provide most of the info required

Can also ask if any other connection manager installed, other than the network
manager

as regards keyring manger can also look at this thread
[http://ubuntuforums.org/showthread.php?t=384905](http://ubuntuforums.org/showthread.php?t=384905)

---

### Post by doperative on 2011-03-01
> **alexfish said:**
> without info hard to solve , + if no other means of connection most common problems with huawie devices are ..
 
**Ubuntu** 10.04.2 LTS (**Lucid** Lynx)
 
 
Right, I tried this:
$lsusb
$modprobe usbserial vendor=0x12d1 product=0x1446
 
Bus 001 Device 016: ID 12d1:1446 Huawei Technologies Co., Ltd. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 
When I select "New Mobile Broadband Connection" the "Create a connection for this mobile broadband device:" is greyed out. Any solutions?
 
[IMG]http://www.uploadimage.co.uk/images/77681282056411250990.png[/IMG]

---

### Post by alexfish on 2011-03-01
Hi

looks if need usb_modeswitch

look in synaptic or software center

if no Internet connection can suggest downloading sakis3g on a system with Internet and save to usb stick ,

[http://www.sakis3g.org/](http://www.sakis3g.org/)

---

### Post by doperative on 2011-03-02
Ubuntu 9.10 - the Karmic Koala 
HUAWEI Mobile Broadband
Model E1750
HSPA USB Stick
C E0682
 
> **alexfish said:**
> Hi
 
looks if need usb_modeswitch
 
look in synaptic or software center
 
if no Internet connection can suggest downloading sakis3g on a system with Internet and save to usb stick ,
 
[http://www.sakis3g.org/](http://www.sakis3g.org/)
 

 
$lsusb
 
Bus 001 Device 035: ID 12d1:1446 Huawei Technologies Co., Ltd. 
 
On advice from another page ...
 
$sudo nano /etc/udev/rules.d/15-huawei-155x.rules
 
- cut -
SUBSYSTEM=="usb",
ATTRS{idProduct}=="1446",
ATTRS{idVendor}=="12d1",
RUN+="/lib/udev/modem-modeswitch --vendor 0x$attr{idVendor} --product 0x$attr{idProduct} --type option-zerocd"
- paste -
 
# reboot
# plugin HUAWEI
 
$tail -n 100 /var/log/messages
 
Mar 1 23:16:08 sys kernel: [ 366.084084] usb 1-1: new high speed USB device using ehci_hcd and address 3
Mar 1 23:16:08 sys kernel: [ 366.219020] usb 1-1: configuration #1 chosen from 1 choice
Mar 1 23:16:11 sys kernel: [ 369.332993] usb 1-1: usbfs: process 2165 (modem-modeswitc) did not claim interface 0 before use
Mar 1 23:16:11 sys kernel: [ 369.397577] Initializing USB Mass Storage driver...
Mar 1 23:16:11 sys kernel: [ 369.402927] scsi5 : SCSI emulation for USB Mass Storage devices
Mar 1 23:16:11 sys kernel: [ 369.410448] scsi6 : SCSI emulation for USB Mass Storage devices
Mar 1 23:16:11 sys kernel: [ 369.411308] usbcore: registered new interface driver usb-storage
Mar 1 23:16:11 sys kernel: [ 369.411326] USB Mass Storage support registered.
Mar 1 23:16:12 sys kernel: [ 370.450987] usb 1-1: usbfs: process 2169 (modem-modeswitc) did not claim interface 0 before use
Mar 1 23:16:12 sys kernel: [ 370.470271] usb 1-1: usbfs: process 2178 (modem-modeswitc) did not claim interface 0 before use
Mar 1 23:16:12 sys kernel: [ 370.477271] usb 1-1: usbfs: process 2181 (modem-modeswitc) did not claim interface 0 before use
Mar 1 23:16:12 sys kernel: [ 370.493033] usb 1-1: usbfs: process 2182 (modem-modeswitc) did not claim interface 0 before use
Mar 1 23:16:16 sys kernel: [ 374.413654] scsi 6:0:0:0: Direct-Access HUAWEI SD Storage 2.31 PQ: 0 ANSI: 2
Mar 1 23:16:16 sys kernel: [ 374.415430] sd 6:0:0:0: Attached scsi generic sg4 type 0
Mar 1 23:16:16 sys kernel: [ 374.431735] sd 6:0:0:0: [sdc] Attached SCSI removable disk
Mar 1 23:16:17 sys kernel: [ 375.502082] usb 1-1: usbfs: process 2185 (modem-modeswitc) did not claim interface 0 before use
------
 
manually running modem-modeswitch
 
$/lib/udev/modem-modeswitch -d --vendor 0x12d1 --product 0x1446 --type option-zerocd
 
D: Found mass storage device:
D: Endpoints: 2
D: Class: 0x8
D: SubClass: 0x6
D: Protocol: 0x50
D: Found modem mass storage device '120'
D: 120: found already attached driver 'usbfs'
D: 120: failed to switch device to modem mode.

---

### Post by alexfish on 2011-03-02
Hi

there is a difference between usb-modeswitch and usb_modeswitch

the udev usb-modeswitch is now depreciated in later versions of Ubuntu to usb_modeswitch

notice the difference

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)


according to sakis3g your model is part of the lastest emeded sakis3g : hence it should not conflict with installed versions of usb_modeswitch or any of the udev-usb-modeswitch
so can be used as a tool for switching + has the ability to update hal etc/

---

### Post by graysonc on 2011-03-10
I have recently got a t-mobile 615 Mobile Broadband stick ( Huawei E173 ) working in Kubuntu 10.10 and 10.04.

See my notes [here]("http://sussexcomputerworks.co.uk/computer-services-and-web-design/tech-stuff/43-linux/76-kubuntu-1004-and-the-t-mobile-broadband-615-usb-device.html")

---

### Post by doperative on 2011-03-12
> **graysonc said:**
> I have recently got a t-mobile 615 Mobile Broadband stick ( Huawei E173 ) working in Kubuntu 10.10 and 10.04.

See my notes [here]("http://sussexcomputerworks.co.uk/computer-services-and-web-design/tech-stuff/43-linux/76-kubuntu-1004-and-the-t-mobile-broadband-615-usb-device.html")

Thanks ..

I previously borrowed an Virgin/O2 device and they worked on a previous Ubuntu version, so I assumed the Huawei would.

Still no luck: I figure it's the BIOS as in the computer won't even boot with the device plugged in ...

---

