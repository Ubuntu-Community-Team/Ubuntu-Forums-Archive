---
title: "ZTE MF633+ HSUPA USB Modem with Karmic"
date: 2010-04-01
forum: Networking &amp; Wireless
---

### Post by Homer2288 on 2010-04-01
Hi there,

I am an absolute linux newbie. I've installed 9.10 Karmic Koala on me laptop. Everything works perfectly, and faster than the floppy windows.  However, I've come across one little road block. 

I have a Zte MF633+ Telstra (aka Hellstra) 7.2 usb modem. I have searched the forum and there is no thread on this type of modem. 

I have enthusiastically installed usb_modeswitch package found on ubuntu packages website. As the conf file does not have an entry for MF633+ I chose the closest one

########################################################
# ZTE MF628+ (tested version from Telia / Sweden)
# ZTE MF626
# ZTE MF636 (aka "Telstra / BigPond 7.2 Mobile Card")
#
# Contributor: Joakim Wennergren

After making changes to the conf file, I run usb_modeswitch and the modem came alive. Fantastic. Internet was working, hunkydory it seems. I turned off laptop, unplug the usb modem. The next day, turn it on, plug in modem. And the modem did not activate. It was showing red light, not the regular blue light when it's detected and activated ready to go. 

I've run the usb_modeswitch again and still not working.

I've followed suggestions on the forum for some other ZTE modems. I have basically, created a hal fdi file and a rule. I've also tried wvdial but it says :

--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB2: No such file or directory
--> Cannot open /dev/ttyUSB2: No such file or directory
--> Cannot open /dev/ttyUSB2: No such file or directory

I would greatly appreciate it if someone can assist. Thanks in advance.

---

### Post by pdc on 2010-04-02
hi; 

in a terminal type in 

> lsusb

If you get 

> 19d2:2000 your modem is being seen as CD-ROM device

if it says something like

> 19d2:0031

it has been flipped and is seen as a modem;

if you get the latter

copy and paste

> dmesg | grep tty

into a terminal and tell us the result

---

### Post by Homer2288 on 2010-04-04
heres the result of lsusb & dmesg | grep tty

homer@Voyager-T43:~$ lsusb
Bus 003 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 19d2:2000 ONDA Communication S.p.A. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
homer@Voyager-T43:~$ dmesg | grep tty
[    0.001221] console [tty0] enabled
[    1.160504] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A
[    1.162334] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[   19.905005] ttyS1: LSR safety check engaged!


I've also tried sudo eject sr0 but sr0 seems to be associated to the actual CD-Rom on the laptop.


homer@Voyager-T43:~$ homer@Voyager-T43:~$ dmesg | grep CD-ROM
[    1.503203] scsi 1:0:0:0: CD-ROM            MATSHITA UJDA765 DVD/CDRW 1.70 PQ: 0 ANSI: 5
[    1.506293] Uniform CD-ROM driver Revision: 3.20
[    1.506366] sr 1:0:0:0: Attached scsi CD-ROM sr0
homer@Voyager-T43:~$

---

### Post by Homer2288 on 2010-04-04
This is what happens when I run usb_modeswitch.

homer@Voyager-T43:~$ sudo /usr/sbin/usb_modeswitch -W -c /etc/usb_modeswitch.conf
[sudo] password for homer: 

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Reading config file: /etc/usb_modeswitch.conf
DefaultVendor=  0x19d2
DefaultProduct= 0x2000
TargetVendor=   0x19d2
TargetProduct=  0x0031
TargetClass=    not set

DetachStorageOnly=0
HuaweiMode=0
SierraMode=0
SonyMode=0
MessageEndpoint=0x01
MessageContent="55534243123456782000000080000c85010101180101010101000000000000"
NeedResponse=0
ResponseEndpoint= not set
Interface=0x00

InquireDevice enabled (default)
Success check disabled

usb_set_debug: Setting debugging level to 15 (on)
usb_os_find_busses: Found 003
usb_os_find_busses: Found 002
usb_os_find_busses: Found 004
usb_os_find_busses: Found 005
usb_os_find_busses: Found 001
usb_os_find_devices: Found 002 on 003
skipped 1 class/vendor specific interface descriptors
usb_os_find_devices: Found 001 on 003
error obtaining child information: Inappropriate ioctl for device
usb_os_find_devices: Found 001 on 002
usb_os_find_devices: Found 001 on 004
usb_os_find_devices: Found 001 on 005
usb_os_find_devices: Found 003 on 001
usb_os_find_devices: Found 001 on 001
error obtaining child information: Inappropriate ioctl for device

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found default devices (1)
Accessing device 003 on bus 001 ...
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usbfs")
 OK, driver "usbfs" detached
USB error: error submitting URB: Device or resource busy
 Could not get INQUIRY response (error -16)

Device description data (identification)
-------------------------
Manufacturer: ZTE,Incorporated
     Product: ZTE WCDMA Technologies MSM
  Serial No.: 1234567890ABCDEF
-------------------------
Looking for active driver ...
 OK, driver found ("usbfs")
 OK, driver "usbfs" detached
Setting up communication with interface 0 ...
Trying to send the message to endpoint 0x01 ...
 Sending the message returned error -110. Trying to continue
-> Run lsusb to note any changes. Bye.

---

### Post by Homer2288 on 2010-04-04
I think this part of dmesg is related to when I plug in the modem to the instance I ran usb_modeswitch. It looks like the modem not being recognised is due to the last few lines, saying it did not claim interface 0 before use.

[   66.000171] usb 1-4: new high speed USB device using ehci_hcd and address 3
[   66.521362] usb 1-4: configuration #1 chosen from 1 choice
[   66.785568] Initializing USB Mass Storage driver...
[   66.786549] scsi2 : SCSI emulation for USB Mass Storage devices
[   66.786692] usbcore: registered new interface driver usb-storage
[   66.786696] USB Mass Storage support registered.
[   66.788498] usb-storage: device found at 3
[   66.788500] usb-storage: waiting for device to settle before scanning
[  426.492660] usb 1-4: usbfs: process 1822 (usb_modeswitch) did not claim interface 0 before use
[  426.504179] usb 1-4: usbfs: process 1951 (usb_modeswitch) did not claim interface 0 before use
[  426.536156] usb 1-4: usbfs: process 1822 (usb_modeswitch) did not claim interface 0 before use

---

### Post by alexfish on 2010-04-04
Hi
looking at the above messages

there is a possibility this device does not require the usb modeswitch

try removing usb modeswitch, reboot the computer without the dongle

 plug the dongle in , if the device shows up on the desktop simply eject the device

you can check to see if it has flipped by the lsusb command from the terminal

check before and after the device is ejected, there should be two separate ID's

if this works then try configuring with the network manager

also you can leave it plugged in at boot time as the device should be recognised by the kernel  and will be ready for use when the desktop has loaded

regards

alexfish

---

### Post by Homer2288 on 2010-04-05
Thanks Alexfish. I was trying to solve a simple problem with a complicated solution. My bad.
I have uninstalled usb_modeswitch rebooted the lappy. Plug in the modem, ejected it as you mentioned. 
Checked lsusb, it has put it in modem mode, ie. 0x0031 and says it is a ZTE MF636, but this is actually a MF633+ ,anyway it works. 
Set it up again in Network Manager, it picked up the modem just fine. I am now connected to the internet. It is working now woohoo. Happy as Larry. Thanks!

---

### Post by pdc on 2010-04-06
well done Homer; enjoy;

I think you will find that you will need to "eject" each time you insert the device;

George Vita guided me towards a good solution; so your computer will recognise your modem each time you insert it, and flip it for you, ready to connect up

> sudo gedit /etc/udev/rules.d/zte_eject.rules

likely a blank page will open; paste into it

> SYSFS{idVendor}=="19d2", SYSFS{idProduct}=="2000", RUN+="/usr/bin/eject %k", OPTIONS+="last_rule"


Save; close;

now your system should do the "ejecting" for you ..

---

### Post by Homer2288 on 2010-04-06
thanks for that PDC, and thank u George Vita for your contribution.

---

