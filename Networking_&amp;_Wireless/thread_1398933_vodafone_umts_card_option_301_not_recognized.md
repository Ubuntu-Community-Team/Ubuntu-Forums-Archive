---
title: "vodafone umts card option 301 not recognized"
date: 2010-02-05
forum: Networking &amp; Wireless
---

### Post by st_john_smith on 2010-02-05
I just received a german Vodafone UMTS PCMCIA card. The manufacturer is Option and it says something like 301 as model.

when I plug the card in, syslog says:

> Feb  5 10:56:17 IBMLinux kernel: [ 1101.456131] usb 8-1: new full speed USB device using ohci_hcd and address 6
Feb  5 10:56:17 IBMLinux kernel: [ 1101.672368] usb 8-1: configuration #1 chosen from 1 choice
Feb  5 10:56:17 IBMLinux kernel: [ 1101.690918] hso0: Disabled Privacy Extensions
Feb  5 10:56:17 IBMLinux kernel: [ 1102.004140] usb 8-1: usbfs: process 6029 (usb_modeswitch) did not claim interface 0 before use
Feb  5 10:56:17 IBMLinux kernel: [ 1102.013770] usb 8-1: usbfs: process 6027 (usb_modeswitch) did not claim interface 0 before use
Feb  5 10:56:17 IBMLinux modem-manager: (ttyHS3) opening serial device...
Feb  5 10:56:17 IBMLinux modem-manager: (ttyHS3): probe requested by plugin 'Option High-Speed'
Feb  5 10:56:17 IBMLinux modem-manager: (ttyHS2) opening serial device...
Feb  5 10:56:17 IBMLinux modem-manager: (ttyHS2): probe requested by plugin 'Option High-Speed'
Feb  5 10:56:17 IBMLinux usb_id[6043]: unable to access '/devices/pci0000:00/0000:00:1e.0/0000:15:00.0/0000:16:00.0/usb8/8-1/8-1:1.0/tty/ttyHS1'
Feb  5 10:56:17 IBMLinux usb_id[6044]: unable to access '/devices/pci0000:00/0000:00:1e.0/0000:15:00.0/0000:16:00.0/usb8/8-1/8-1:1.0/tty/ttyHS0'
Feb  5 10:56:17 IBMLinux usb_id[6046]: unable to access '/devices/pci0000:00/0000:00:1e.0/0000:15:00.0/0000:16:00.0/usb8/8-1/8-1:1.0/net/hso0'
Feb  5 10:56:17 IBMLinux NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:15:00.0/0000:16:00.0/usb8/8-1/8-1:1.0/net/hso0, iface: hso0)
Feb  5 10:56:17 IBMLinux NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:15:00.0/0000:16:00.0/usb8/8-1/8-1:1.0/net/hso0, iface: hso0): no ifupdown configuration found.
Feb  5 10:56:17 IBMLinux NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:15:00.0/0000:16:00.0/usb8/8-1/8-1:1.0/net/hso0, iface: hso0)
Feb  5 10:56:19 IBMLinux modem-manager: (ttyHS3) closing serial device...
Feb  5 10:56:19 IBMLinux modem-manager: (Option High-Speed): GSM modem /sys/devices/pci0000:00/0000:00:1e.0/0000:15:00.0/0000:16:00.0/usb8/8-1 claimed port ttyHS3
Feb  5 10:56:19 IBMLinux modem-manager: Added modem /sys/devices/pci0000:00/0000:00:1e.0/0000:15:00.0/0000:16:00.0/usb8/8-1
Feb  5 10:56:29 IBMLinux modem-manager: (ttyHS2) closing serial device...so obviously, the card is detected but for some reason deactivated.

any hint for getting this working is appreciated.

I'm on a Lenovo Thinkpad T61p with Ubuntu 9.10

---

### Post by alexfish on 2010-02-05
hi

this device looks as if connection type is   HSO 

you could try looking here for help 

[http://www.pharscape.org/](http://www.pharscape.org/)

possibly try the HSO connect  : also check out the forum

regards

alexfish

---

### Post by st_john_smith on 2010-02-05
Thanks or the hint.

I'm a few steps further....

Using comgt, the card is initialize and shows a blue light. Looks nice. ;)

Using wvdial (with a conf from another post) it seems to make a connection showing IP config data and all. Looks nice, too.

When I open firefox to try it, the computer freezes.

Anyone knows, what to do now?

---

### Post by alexfish on 2010-02-06
hi



Can you fill us in with a few details IE:are you using wvdial to make the actual connection and also details of any dialling properties ;also any parts of log files which may be relevant

also , look here see what you think

[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/91686](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/91686)

---

### Post by alexfish on 2010-02-06
hi



Can you fill us in with a few details IE:are you using wvdial to make the actual connection and also details of any dialling properties ;also any parts of log files which may be relevant,can you elaborate on this " conf"

also , look here see what you think

[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/91686](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/91686)

also check this post

[http://ubuntuforums.org/showthread.php?t=1389237](http://ubuntuforums.org/showthread.php?t=1389237)

---

### Post by st_john_smith on 2010-02-07
The links sound promising....
I would like to use HSOconnect anyway, as I don't have one device that thinks being a USB storage thing....but HSOConnect does not recognize my card so far.
Maybe I really have to remove NM and ModemManager....
I will also try upgrading the kernel ...

Meanwhile, here is some info:
My kernel is 
> 2.6.31-16-generic-pae

For getting connected, I do first a:
> comgt -d /dev/ttyHS3
after entering the pin:
> Waiting for Registration..(120 sec max)....
Registered on Home network: "Vodafone.de",0
Signal Quality: 21,99

After that I do:
> sudo wvdial hsdpa vodafone
with the following wvdial.conf:

> dirk@IBMLinux:~$ more /etc/wvdial.conf 

[Dialer Defaults]
Phone = *99***1#
Username = username
Password = password
Stupid Mode = 1
Dial Command = ATDT

[Dialer hsdpa]
Modem = /dev/ttyHS3
Baud = 460800
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem

[Dialer 2gonly]
Init4 = AT+COPS=0,0,"web.vodafone.de",0

[Dialer 3gonly]
Init4 = AT+COPS=0,0,"web.vodafone.de",2

[Dialer vodafone]
Init5 = AT+CGDCONT=1,"IP","web.vodafone.de";


[Dialer 384k]
Init6 = AT+CGEQMIN=1,4,64,384,64,384
Init7 = AT+CGEQREQ=1,4,64,384,64,384

[Dialer 144k]
Init6 = AT+CGEQMIN=1,4,64,144,64,144
Init7 = AT+CGEQREQ=1,4,64,144,64,144

[Dialer 64k]
Init6 = AT+CGEQMIN=1,4,64,64,64,64
Init7 = AT+CGEQREQ=1,4,64,64,64,64 

This seems to go well.
(Cannot really paste the output here as my computer will freeze then...)
It gives me some connection data incl IP addresses and everything.
I can ping a web address now.

When I open the browser, it gets an answer from the website and then the computer freezes (when getting the data...)

I will come back with results from kernel upgrade and HSOconnect, but maybe you can tell me something now...

---

### Post by st_john_smith on 2010-02-07
Meanwhile, I tried the following: 
*upgrade the kernel to 2.6.31-19-generic-pae
*install the 0zerocdoff package from pharscape.org (I think my kernel has one included, but maybe a newer/older version??)
*re-install hsolinkconnect package plus the hsoconnect app

unfortunately, hsoconnect still does not 'see' the card - the controls show not network and I cannot press 'connect'. I will ask the forum on pharscape.org for this..

On the other thread, I tried removing gnome network manager and modem manager and replacing it with wicd.

Now tried comgt/wvdial again.

'Nearly' same result:
I can even get half a webpage. 
Now the UMTS card switched from a green light to a blue light (2G to 3G? my coverage is not perfect at home) and the computer freezes again...

Any hints?

---

### Post by alexfish on 2010-02-08
Hi

you can check this post out
[http://ubuntuforums.org/showthread.php?t=49056](http://ubuntuforums.org/showthread.php?t=49056)

Note the bit about the Sim card pin number
''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
I am shooting in the dark here,since I don't know the device

assuming from the installation of ozerocdoff and the hsoconnect

the rules may have to be written 

below is an example of what can be done :

                                 [COLOR=#000080][SIZE=3]Next Step[/SIZE][/COLOR]

From The Terminal find the device ID's

[http://www.insanelymac.com/forum/lofiversion/index.php/t36764.html](http://www.insanelymac.com/forum/lofiversion/index.php/t36764.html)

Code:

you can try  :  lsusb  : or the ones suggested at the above site 


Open the file with

Code:

[COLOR=#000080][SIZE=2]sudo gedit /etc/udev/rules.d/51-hso-udev.rules[/SIZE][/COLOR]
[COLOR=#000080][SIZE=2]
[/SIZE][/COLOR]
                                   Edit id's ect "xxxx" and "yyyy" According to product info from the lsusb command  : Also not sure about the Deviceclass} =="00" please check

                                  [COLOR=#000080][SIZE=2]ATTRS{idVendor}=="xxxx", ATTRS{idProduct}=="yyyy", RUN+="/usr/sbin/ozerocdoff -wi 0x%s{idProduct}" [/SIZE][/COLOR]

Second line to paste in the SUBSYSTEM section:

Code:

[COLOR=#000080][SIZE=2]SUBSYSTEM=="usb_device", SYSFS{idVendor}=="xxxx", SYSFS{idProduct}=="yyyy", SYSFS{bDeviceClass}=="00", RUN+="/usr/sbin/ozerocdoff -wi 0x%s{idProduct}" [/SIZE][/COLOR]

                                 Save the file and exit gedit.
 

                                   
[COLOR=#000080]**Enter your APN **[/COLOR]

Use the Profile / Edit Connection menu. All network providers have different APN's [Find out From your Provider] also double check your phone number  , a lot of numbers are *99#


this is from a icon 5x5 post
also there was a problem with named servers


one post suggested installing                             resolvconf


Code:

                                  sudo apt-get install resolvconf
usually the above  details are posted at the site


regards
alexfish

---

