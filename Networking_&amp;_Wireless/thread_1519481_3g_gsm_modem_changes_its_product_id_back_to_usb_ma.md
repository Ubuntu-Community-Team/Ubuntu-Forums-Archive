---
title: "3g gsm modem changes its product id back to usb mass storage mode on reinserting"
date: 2010-06-28
forum: Networking &amp; Wireless
---

### Post by utkarsh009 on 2010-06-28
:confused:i have been asking questions on the forum but still haven't got any answer till now. Atleast solve this one. i used usb modeswitch to convert my usb dongle to modem mode for the first time i plugged it in. it worked perfectly. i connected to the net. but when i replug my device after taking it out it again changes its product id to usb mass storage mode and guess what, i even do not see a cd or a mass storage icon anywhere. its even not listed in the disk utility where all usb devices are listed. the only solution is that i have to reboot with device plugged in and then too the nm applet is not able to connect. it connects after 1 or 2 reboots. i am fed up. and wvdial and pppconfig are just craps. i haven't been ever able to connect using them. at least the nm applet connects after 1 or 2 reboots. how can i make my modem detected as modem even after replugging it?

---

### Post by alexfish on 2010-06-28
Hi

First you need some info

Which version of Ubuntu are you using

Boot up the computer without the device ; connect the device, then from the terminal post the results of

Code:

lsusb

then

Code:

ls -al /dev/serial/by-id/usb*

then 

Code:

ls -al /dev/disk/by-id/usb*Storage*

---

### Post by utkarsh009 on 2010-06-28
thanks alexfish for replying! i am using ubuntu 10.04 lucid lynx. the output of lsusb is :
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR=Blue]Bus 001 Device 004: ID 1c9e:f000[/COLOR]  
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 002: ID 5986:0241 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
the output of 2nd code is :
ls: cannot access /dev/serial/by-id/usb*: No such file or directory
the output of 3rd code is :
ls: cannot access /dev/disk/by-id/usb*Storage*: No such file or directory
---------------------------------
don't be mistaken that it is recognised as usb mass storage but only the id changes to f000 as in above output and no modem is detected. i use micromax mmx 310g in which the modem mode displays 1c9e:9605. i also didn't find much information about my device on the net (google) since my device has just been launched (i think so) but there is info about 300g. i managed to recognise the modem code i.e. 9605 by rebooting after installing the driver in windows. as i said it only works after successive reboots. hope this helps! can you suggest any method so that f000 remains 9605.:popcorn:

---

### Post by pdc on 2010-06-29
so this device

> 1c9e:f000 

is listed in the latest usb_modeswitch config file

> # MobiData MBD-200HU
#
# Contributor: Stefan Olejnik

;DefaultVendor=  0x1c9e
;DefaultProduct= 0xf000

;TargetVendor=   0x1c9e
;TargetProduct=  0x9000

;MessageContent="55534243123456788000000080000606f50402527000000000000000000000"




[http://www.draisberghof.de/usb_modeswitch/device_reference.txt](http://www.draisberghof.de/usb_modeswitch/device_reference.txt)

... so it should work: perhaps download the latest version of usb_modeswitch

1.1.3-1 

from here

[http://packages.debian.org/search?keywords=usb-modeswitch](http://packages.debian.org/search?keywords=usb-modeswitch)

(Sid unstable package)

if that doesn't work ......

join the usb_modeswitch forum

[http://www.draisberghof.de/usb_modeswitch/bb/](http://www.draisberghof.de/usb_modeswitch/bb/)

and Josh will help you out

---

### Post by alexfish on 2010-06-29
Hi all

as said in the first post the device worked first time but on subsequent boots the device fails to be recognised.

The relevant info as ask for : indicates the drivers are not loading and may also may indicate a deficiency in the Modem Manager the basic is laid out below

1. the modem manager in 10.04 may be 0.3 which I think was a GIT version as previous version in 9.10 was 0.8: some devices will not be recognised byNM and MM if the Storage device is fully removed from the system , so therefore only an eject command would be required:Explained, if the Storage  is fully removed then in some cases when the modem drivers are loading the mass storage can get attached to one of the tty ports or the tty ports can get reversed . this proves to be a problem with MM .And also for any dialer used : as the ports can vary.So this appears to be a port recognition problem: Sakis 3g may provide a solution

2. The Question here is ,why the drivers fail to load. At present I can only suggest trying to load the drivers with the following command from the terminal

Code:

sudo modprobe option

see what happens

3. As for the switching of the the device then best advice is given by PDC ; also as mentioned you could try sakis3g

regards

alexfish

---

### Post by utkarsh009 on 2010-06-30
wooooooooow! sakis 3g is just marvelous! this was what i expected from ubuntuforums. i asked a problem and got better than i wanted. and i am also getting increased speed. i am able to connect without subsequent reboots. but 1 problem still remains. i still have to boot up with my device plugged in to make it recognise as a modem (where id is 1c9e:9605). let me make my question clear.
1. i boot in with my device plugged in, the id is right.
2. i take out my device and replug it, the id changes back to 1c9e: f000. the id for modem mode is 1c9e:f000.
3. even when the id is 1c9e:f000, i don't see any usb mass storage device in my computer.
4. after replugging my device, to change its mode to modem mode i use usb modeswitch. it's also not able to recognise any mass storage device whose mode has to be switched. it just stops at a point. i then suspend the laptop and reopen it after which somtimes the id changes and sometimes not. only rebooting with device plugged in is a way to make its id 1c9e:9605 i.e. modem mode.
can anyone tell me why the id is changed from 1c9e:9605 (modem mode) to 1c9e:f000 (usb mass storage mode) on replugging and still no usb mass storage device is detected by the laptop.
(and sudo modprobe option doesn't help.) ):P

---

### Post by alexfish on 2010-06-30
Hi

Not sure as to what is exacly happening ,

points

1.it could be part of the udev and the rules associated with it, udev efforts now included "modem-modeswitch".So when the device is connected at boot then the device may be configuring ,also of note , I do know some devices will connect through the pppd at the same time. when these events occur it is almost impossible to detect the device, also NM will not detect the device , this part could be associated with the Modem Manager,as said I am not sure what is happening IE: these points are not conclusive as they maybe  to be kernel related.

2. is the "usb modeswitch" conflicting with the "udev modem-modeswitch".IE the new version of the usb modeswitch works when the device is pluged in . therefore the question to ask here is ." is the device been reset by the usb modeswitch. or is the udev effort  working after booting the computer .for a fix you may have to delve into the backend to blacklist certain devices or make new udev rules.


3. I don't want to decry udev's and Modem Managers efforts but I think having to **write rules** and **delve into the back-end of the system** to **suit each device** is not the way to go,

4. Sakis3g works and also has the usb modeswitch built into the script. one has to read the script to fully understand how it works, but for an out of the box experience a lot of readers with problems could give this a try ,

**utkarsh009**, keep in touch Sakis3g , as mention it uses the usb modeswitch, it gets updated on a regular basis

---

### Post by aashleshc on 2010-08-07
i just got a 3g bsnl usb datacard.
it was being recognised as a storage device (a cd on the desktop) untill i followed a few steps from [http://duopetalflower.blogspot.com/2010/05/configuring-bsnl-evdo-capitel-3g-usb.html](http://duopetalflower.blogspot.com/2010/05/configuring-bsnl-evdo-capitel-3g-usb.html)
TILL step 6.
it is not recognised as a mass storage now. but in wvdialconf i get the following error:

~$ wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.

-----------
this is what i got for my lsusb and the other two you asked to check for:


~$ lsusb
Bus 002 Device 007: ID 1c9e:f000  
Bus 002 Device 006: ID 413c:8160 Dell Computer Corp. 
Bus 002 Device 005: ID 413c:8162 Dell Computer Corp. 
Bus 002 Device 004: ID 413c:8161 Dell Computer Corp. 
Bus 002 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:6407 Microdia 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

~$ ls -al /dev/serial/by-id/usb*
lrwxrwxrwx 1 root root 13 2010-08-07 11:48 /dev/serial/by-id/usb-USB_Modem_USB_Modem_000000000000-if00-port0 -> ../../ttyUSB0

~$ ls -al /dev/disk/by-id/usb*Storage*
ls: cannot access /dev/disk/by-id/usb*Storage*: No such file or directory

--
beginning to get really frustrated now..  pleasse help me out here!!!!!!! :(:(

OH and in dmesg i get :
~$ dmesg | tail -20
[   24.699429]   domain 1: span 0-3 level MC
[   24.699430]    groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178)
[   24.699435] CPU3 attaching sched-domain:
[   24.699437]  domain 0: span 1,3 level SIBLING
[   24.699439]   groups: 3 (cpu_power = 589) 1 (cpu_power = 589)
[   24.699443]   domain 1: span 0-3 level MC
[   24.699445]    groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
[   25.746362] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   36.802403] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[   45.285476] input: Dell BT Travel Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4.3/2-1.4.3:1.0/bluetooth/hci0/hci0:11/input12
[   45.285583] generic-bluetooth 0005:046D:B006.0003: input,hidraw1: BLUETOOTH HID v1.24 Mouse [Dell BT Travel Mouse] on C4:46:19:EA:B9:3A
[   52.525092] usb 2-1.2: new high speed USB device using ehci_hcd and address 7
[   52.629802] usb 2-1.2: configuration #1 chosen from 1 choice
[   52.634049] usbserial_generic 2-1.2:1.0: generic converter detected
[   52.634099] usb 2-1.2: generic converter now attached to ttyUSB0
[  358.307987] USB Serial support registered for GSM modem (1-port)
[  358.308413] usbcore: registered new interface driver option
[  358.308418] option: v0.7.2:USB Driver for GSM modems
[  573.021401] NET: Registered protocol family 24
[  651.357296] pan0: no IPv6 routers present


...please please please help!

---

### Post by alexfish on 2010-08-07
from the info given the modem has one port on ttyUSB0
but is not giving any descriptors

the "ls -al /dev/disk/by-id/usb*Storage* " list command which looks at a file in path of "/dev/disk/by-id" with a filter "usb*Storage*" you

could try 

Code:

ls -al /dev/disk/by-id/usb* 

but may be pointless as the device has registered 

"usb-USB_Modem_USB_Modem_000000000000-if00-port0 -> ../../ttyUSB0"

[ 52.634099] usb 2-1.2: generic converter now attached to ttyUSB0
[ 358.307987] USB Serial support registered for GSM modem (1-port)
[ 358.308413] usbcore: registered new interface driver option
[ 358.308418] option: v0.7.2:USB Driver for GSM modems

you can check to see if the modem is responding by sending AT commands directly 
(for this you need two seperate terminals, one to monitor and one two send the commands)

open up a terminal end enter this code

tr -s "\n" < /dev/ttyUSB0

this terminal will just sit there waiting for a response from the modem on ttyUSB0

open up a second terminal and enter the basic AT command which stands for attention

Code:
echo -e "AT\r" > /dev/ttyUSB0

is there a response in the first terminal

---

### Post by pdc on 2010-08-07
so I think from the ID posted for this device

> 1c9e:f000

it is the same device as this ongoing thread 

[http://ubuntuforums.org/showthread.php?t=1547803](http://ubuntuforums.org/showthread.php?t=1547803)

is about;

except that 

> 1c9e:f000 is the device being seen as a storage device 

and in the second post, the device has been flipped and seen as

> 1c9e:9603

I say this because the usb_modeswitch data about this device: (I am going to say they are both the same ...) shows

> # MobiData MBD-200HU (aka 4G XS Stick W10/W14, aka **Micromax MMX 300G**,
# aka ChinaBird CBCPL68)
#
# Contributor: Chris

;DefaultVendor=  0x1c9e
;**DefaultProduct**= 0x**f000**

;TargetVendor=   0x1c9e
;**TargetProduct**=  0x**9603**

;MessageContent="55534243123456788000000080000606f50402527000000000000000000000"

---

