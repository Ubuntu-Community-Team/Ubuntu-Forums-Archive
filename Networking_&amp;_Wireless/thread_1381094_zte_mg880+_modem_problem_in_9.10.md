---
title: "zte mg880+ modem problem in 9.10"
date: 2010-01-14
forum: Networking &amp; Wireless
---

### Post by abose@linux on 2010-01-14
hi everybody today i'm posting my thread first from ubuntu 9.10.i'm really ecstatic to let u people know that i'm able to connect to net from linux.first of all i would like to thank the people who made usb_modeswitch and all the member of this forum without whom i won't be successful.now the steps i've followed are,--

[LIST=1]
[*]installed usb_modeswitch-1.0.7
[*]did a modprobe with my default vendor and product id
[*]put a rule in /etc/udev/rules.d
[*]configure wvdial
[*]and voila
[/LIST]
i'm online:D:popcorn:

---

### Post by pdc on 2010-01-14
well done; great work;

tell us how you configured wvdial;;

1.0.7 usb_modeswitch is a tar.gaz file? You did well to get that going: as a seeming newcomer to linux ? !! smart work

---

### Post by raunhar on 2010-03-15
I also got a ZTE MG880 Reloance connect USB Modem.

How do i get this file and what procedure to follow

Please help

---

### Post by raunhar on 2010-03-15
lsusb shows the device as ONDA Communications at Bus 005 device 006 ID 19d2;fffd.

also the link to the file usb_modes...-1.0.5.tar.bz2  is broken.

Pl. suggest a way out.

Thanks in advance.

---

### Post by pdc on 2010-03-15
this is the home of usb_modeswitch

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

I see the latest version is 1.1

if you go here

[http://packages.debian.org/search?keywords=usb-modeswitch](http://packages.debian.org/search?keywords=usb-modeswitch)

and download the sid unstable version, that is configured as a .deb package and can be installed into Ubuntu more easily; (and from this site, you should be able to trust its authenticity)

............ the first post in this forum actually conceals a lot: there are several detailed steps in here, that would have been garnered from several posts

which country are you in? which provider?

---

### Post by raunhar on 2010-03-15
I am in India, and will be using Reliance net Connect1X.

Downloaded the file and installed. Next what.

---

### Post by raunhar on 2010-03-16
Please Please Please help.

I am desperate to use it.

---

### Post by pdc on 2010-03-16
have a read at this post

[http://jebus.nu/tech-corner/sprint-u300](http://jebus.nu/tech-corner/sprint-u300)

it shows you some of the steps that abose@linux whizzed through in #1

firstly open a terminal and type

> lsusb

tell us what that says

have a read at this post

[http://linuxondesktop.blogspot.com/2009/07/configuring-reliance-netconnect-on.html](http://linuxondesktop.blogspot.com/2009/07/configuring-reliance-netconnect-on.html)

this covers the later step of setting up wvdial

---

### Post by raunhar on 2010-03-16
Thank you for the reply.
lsusb shows this device as
Bus 005 Device 007: ID 19d2:fffd ONDA Communication S.p.A. 

sudo lsusb -v shows
Bus 005 Device 007: ID 19d2:fffd ONDA Communication S.p.A. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.01
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        16
  idVendor           0x19d2 ONDA Communication S.p.A.
  idProduct          0xfffd 
  bcdDevice            0.00
  iManufacturer           1 ZTE, Incorporated
  iProduct                2 ZTE CDMA Tech
  iSerial                 3 Serial Number

---

### Post by raunhar on 2010-03-16
How to save the rule file.

---

### Post by pdc on 2010-03-16
before any rule, take the modem out;

plug it in again, and type

> sudo -f tail/var/log/messages

and paste the result back here

---

### Post by raunhar on 2010-03-16
The folder etc/... doesnot have the permission

---

### Post by pdc on 2010-03-16
I can't understand why permission was not granted

instead, try

> dmesg

look for 

> ttyUSB0 

and 

> ttyUSB1

paste back a sample if that appears

---

### Post by raunhar on 2010-03-16
ttyUSB0 & ttyUSB1 Not found. I am attaching a txt version of mesg

While saving the rule file, this is the error
Could not save the file /etc/udev/rules.d/50-u300modem.rules.
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

---

### Post by pdc on 2010-03-16
it does not appear that usb_modeswitch is "flipping" the modem;

so ............

....... if you take the modem out, and plug it in

..........do you get an icon appear on your desktop?

---

### Post by raunhar on 2010-03-16
No icon appaer.

The result of sudo -f is 
sudo -f tail/var/log/messages
sudo: invalid option -- 'f'
usage: sudo [-n] -h | -K | -k | -L | -V | -v
usage: sudo -l[l] [-AnS] [-g groupname|#gid] [-U username] [-u username|#uid]
            [-g groupname|#gid] [command]
usage: sudo [-AbEHnPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AnS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] file ...


I really appreciate your taking so much time with me.

---

### Post by pdc on 2010-03-16
well if you are trying the tail message

type

> tail -f /var/log/messages

tell what it shows after you take the modem out and plug it in again

(copy and paste my text to ensure it transfers correctly ...........)

---

### Post by raunhar on 2010-03-16
With modem plugged in
punnvs@punnvs:~$ tail -f /var/log/messages
Mar 16 12:53:23 punnvs kernel: [ 2911.860123] usb 5-1: new full speed USB device using uhci_hcd and address 9
Mar 16 12:53:23 punnvs kernel: [ 2912.380112] usb 5-1: new full speed USB device using uhci_hcd and address 10
Mar 16 12:53:24 punnvs kernel: [ 2913.276089] usb 5-1: new full speed USB device using uhci_hcd and address 11
Mar 16 12:53:24 punnvs kernel: [ 2913.496943] usb 5-1: configuration #1 chosen from 1 choice
Mar 16 13:03:50 punnvs kernel: [ 3538.880161] usb 5-1: USB disconnect, address 11
Mar 16 13:03:54 punnvs kernel: [ 3543.376115] usb 5-1: new full speed USB device using uhci_hcd and address 12
Mar 16 13:03:55 punnvs kernel: [ 3543.936129] usb 5-1: new full speed USB device using uhci_hcd and address 13
Mar 16 13:03:55 punnvs kernel: [ 3544.496070] usb 5-1: new full speed USB device using uhci_hcd and address 14
Mar 16 13:03:56 punnvs kernel: [ 3545.624104] usb 5-1: new full speed USB device using uhci_hcd and address 16
Mar 16 13:03:57 punnvs kernel: [ 3545.851314] usb 5-1: configuration #1 chosen from 1 choice



Without the modem:
tail -f /var/log/messages
Mar 16 12:53:23 punnvs kernel: [ 2912.380112] usb 5-1: new full speed USB device using uhci_hcd and address 10
Mar 16 12:53:24 punnvs kernel: [ 2913.276089] usb 5-1: new full speed USB device using uhci_hcd and address 11
Mar 16 12:53:24 punnvs kernel: [ 2913.496943] usb 5-1: configuration #1 chosen from 1 choice
Mar 16 13:03:50 punnvs kernel: [ 3538.880161] usb 5-1: USB disconnect, address 11
Mar 16 13:03:54 punnvs kernel: [ 3543.376115] usb 5-1: new full speed USB device using uhci_hcd and address 12
Mar 16 13:03:55 punnvs kernel: [ 3543.936129] usb 5-1: new full speed USB device using uhci_hcd and address 13
Mar 16 13:03:55 punnvs kernel: [ 3544.496070] usb 5-1: new full speed USB device using uhci_hcd and address 14
Mar 16 13:03:56 punnvs kernel: [ 3545.624104] usb 5-1: new full speed USB device using uhci_hcd and address 16
Mar 16 13:03:57 punnvs kernel: [ 3545.851314] usb 5-1: configuration #1 chosen from 1 choice
Mar 16 13:05:51 punnvs kernel: [ 3659.904146] usb 5-1: USB disconnect, address 16

---

### Post by pdc on 2010-03-16
now try

> sudo modprobe usbserial vendor=0×19d2 product=0×fffd

and

give us 

> tail -f /var/log/messages

again


........... we would hope to see some mention of ttyUSB0 and ttyUSB1 ..

---

### Post by raunhar on 2010-03-16
modprobe gives:
FATAL: Error inserting usbserial (/lib/modules/2.6.31-20-generic/kernel/drivers/usb/serial/usbserial.ko): Invalid argument

---

### Post by pdc on 2010-03-16
we need to "flip" your modem

do this without the modem plugged in

> gksu gedit /etc/udev/rules.d/zte_eject.rules

*that will open the text editor gedit with adminstrator powers*

[B][U]paste this into the empty file
[/U][/B]
> SYSFS{idVendor}=="19d2", SYSFS{idProduct}=="fffd", RUN+="/usr/bin/eject %k", OPTIONS+="last_rule" 

save; close file

plug modem in

type

> lsusb

what do you get?

if the fffd has changed, you need to install wvdial as from the posting I gave you earlier ........

---

### Post by raunhar on 2010-03-16
Here is the result of lsusb
Bus 005 Device 011: ID 19d2:fffd ONDA Communication S.p.A.

---

### Post by pdc on 2010-03-16
you need to go off and google search yourself on 

> linux zte mg880 modem

it used to work in ubuntu 7.04 !!!!!!!!!!!!!!

maybe download ubuntu 8.10 or 9.04 (yes, you still can ........... and try a live CD of either of those .............)

---

### Post by raunhar on 2010-03-16
Thanks for your time.

Will it work in 9.04

---

### Post by raunhar on 2010-03-16
Got it working.
As advised by you, I searched it and found the topic. It followed it and it was done.
After attaching the modem, I gace the modprobe command (the same as you had informed) but with sudo and the device got listed in dmesg.

Thanks a lot.
This is the line that i used.
sudo modprobe usbserial vendor=0x19d2 product=0xfffd

---

