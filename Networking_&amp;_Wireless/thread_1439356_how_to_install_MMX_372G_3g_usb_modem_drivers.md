---
title: "how to install MMX 372G 3g usb modem drivers"
date: 2010-03-26
forum: Networking &amp; Wireless
---

### Post by pankaj143gupta on 2010-03-26
hello friends...
i am new to ubuntu ( unix paltform) i've mircomax MMX 372G 3g usb modem. i use this modem in windows XP by BSNL 2g prepaid connection. in windows based systems when i plug the device in the system the device drives are automaticaly get installed.
when i tried to connect this device in ubuntu 9.10 there is a CD Rom disk is showing... i am unable to install the device drivers and the application program for stablish the network connection. please give me full solution or rpm files by which i can use the modem in ubuntu..
i m new to this platform so please explain the procedure to use this device...
thanks in advance....

---

### Post by dineshs on 2010-03-26
Pl read this
[http://packages.ubuntu.com/karmic/usb-modeswitch](http://packages.ubuntu.com/karmic/usb-modeswitch)
I think you need to install modeswitch first.Then rightclick on the network manager icon - edit connection-mobile broadband-add

---

### Post by pankaj143gupta on 2010-03-31
the usb mode switch is not detecting my modem.... please explain in detail... i m unable to configure it....

---

### Post by pdc on 2010-03-31
open a terminal 

type

> lsusb

copy and paste the result back here

---

### Post by dineshs on 2010-04-01
Did you go thru this post?
[http://ubuntuforums.org/showthread.php?t=1417505&highlight=usb+modeswitch](http://ubuntuforums.org/showthread.php?t=1417505&highlight=usb+modeswitch)

---

### Post by pankaj143gupta on 2010-04-01
panky@ubuntu:~$ lsusb
Bus 001 Device 004: ID 05c6:f000 Qualcomm, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
panky@ubuntu:~$

---

### Post by dineshs on 2010-04-01
Did you try this
[http://ubuntuforums.org/showpost.php?p=9035205&postcount=7](http://ubuntuforums.org/showpost.php?p=9035205&postcount=7)

---

### Post by pankaj143gupta on 2010-04-01
yes i tried this... bt it is not working.

---

### Post by pdc on 2010-04-01
so confirming that

> 05c6:f000

is recognised in usb_modeswitch 

[http://www.draisberghof.de/usb_modeswitch/usb_modeswitch.setup](http://www.draisberghof.de/usb_modeswitch/usb_modeswitch.setup)

and its entry is

> # Siptune LM-75 ("LinuxModem")
#
# Contributor: Antti Turunen

;DefaultVendor=  0x05c6
;DefaultProduct= 0xf000

;TargetVendor=   0x05c6
;TargetProduct=  0x9000

# only for reference and 0.x versions
# MessageEndpoint=0x01

;MessageContent="5553424312345678000000000000061b000000020000000000000000000000"


---

### Post by pankaj143gupta on 2010-04-02
yes.
[IMG]http://www.glowfoto.com/static_image/01-230209L/3779/png/04/2010/img4/glowfoto[/IMG]

---

### Post by pdc on 2010-04-02
I am intrigued how you answering 

> yes

helps us move forward, but nevertheless ............

what happens if you copy and paste

> sudo usb_modeswitch -v 05c6 -p f000 -V 05c6 -P 9000 

into a terminal, and hit the ENTER key

then type

> lsusb

in a terminal

---

### Post by pankaj143gupta on 2010-04-02
[FONT=&quot]panky@ubuntu:~$ sudo usb_modeswitch -v 05c6 -p f000 -V 05c6 -P 9000
[sudo] password for panky: 

Looking for target devices ...
 Found devices in target mode or class (1)
Looking for default devices ...
 No devices in default mode or class found. Nothing to do. Bye.

panky@ubuntu:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05c6:9000 Qualcomm, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
panky@ubuntu:~$ 
[/FONT]

---

### Post by pdc on 2010-04-02
so the first time we asked you to type

> lsusb

you got this for your device

> ID 05c6:f000 

now you get 

> ID 05c6:9000 

so you see ........ your device has been unmasked; or "flipped"

usb_modeswitch has changed the device already, hence why it gave you the result of 

> *No devices in default mode or class found. Nothing to do. Bye*. 

.. it had already done its work ..

...... so hopefully from being seen as a virtual CD-ROM device, your device is now seen as a modem

so now type (copy and paste)

> dmesg | grep tty

in a terminal

..  you should get some results saying ttyUSB0 and ttyUSB1 

.. if so .....

Now follow the instructions in this thread:

[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

go half-way down the page 

"Create a mobile broadband connection .."

You need to be able to identify the country you live in; and the provider you have an account with;

---

### Post by pankaj143gupta on 2010-04-03
hello sir i tried all above method and the virtual disk is not showing right now. i m attatching some screen shots of the process which i follow to create a connection.
initial screen shot-   

[IMG]http://sites.google.com/site/pankaj143gupta/Home/01.png[/IMG]


 
[IMG]http://sites.google.com/site/pankaj143gupta/Home/02.png?attredirects=0&d=1[/IMG]



than i started to create a new connection i follow these steps - 

[IMG]http://sites.google.com/site/pankaj143gupta/Home/03.png?attredirects=0&d=1[/IMG]

[IMG]http://sites.google.com/site/pankaj143gupta/Home/04.png?attredirects=0&d=1[/IMG]



[IMG]http://sites.google.com/site/pankaj143gupta/Home/06.png?attredirects=0&d=1[/IMG]


[IMG]http://sites.google.com/site/pankaj143gupta/Home/07.png?attredirects=0&d=1[/IMG]

---

### Post by pankaj143gupta on 2010-04-03
[IMG]http://sites.google.com/site/pankaj143gupta/Home/08.png?attredirects=0&d=1[/IMG]


[IMG]http://sites.google.com/site/pankaj143gupta/Home/09.png?attredirects=0&d=1[/IMG]

[IMG]http://sites.google.com/site/pankaj143gupta/Home/10.png?attredirects=0&d=1[/IMG]




[IMG]http://sites.google.com/site/pankaj143gupta/Home/11.png?attredirects=0&d=1[/IMG]

then  i clicked on close button. after adding new  mobile broadband  connection i tried to connect this connection but it is not showing in  the connections list-

[IMG]http://sites.google.com/site/pankaj143gupta/Home/12.png?attredirects=0&d=1[/IMG]

---

### Post by pdc on 2010-04-03
with the modem inserted

type

> lsusb

if you get a result containing

> ID 05c6:9000 

then copy and paste into the terminal

> dmesg | grep tty 

and tell us what you get

---

### Post by pankaj143gupta on 2010-04-03
[FONT=&quot]panky@ubuntu:~$ dmesg | grep tty 
[    0.001020] console [tty0] enabled
[    0.918902] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.919476] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
panky@ubuntu:~$ 

 [/FONT]

---

### Post by pdc on 2010-04-03
can we again have 

> lsusb

to see what your device ID is?

and 

> tail -f /var/log/messages

and also

> dmesg | grep -e "modem" -e "tty" 

and 

> uname -r

here is a post from a fellow-countryman of yours

[http://ubuntuforums.org/showthread.php?t=1417505&page=1](http://ubuntuforums.org/showthread.php?t=1417505&page=1)

post #7

...... this is how it should go ...........

---

### Post by pankaj143gupta on 2010-04-03
[FONT=&quot]panky@ubuntu:~$ lsusb
Bus 001 Device 002: ID 05c6:9000 Qualcomm, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



panky@ubuntu:~$ tail -f /var/log/messages 
Apr  4 02:13:10 ubuntu kernel: [   25.254689] type=1505 audit(1270361590.692:16): operation="profile_replace" pid=937 name=/usr/bin/evince
Apr  4 02:13:10 ubuntu kernel: [   25.268663] type=1505 audit(1270361590.708:17): operation="profile_replace" pid=937 name=/usr/bin/evince-previewer
Apr  4 02:13:10 ubuntu kernel: [   25.277147] type=1505 audit(1270361590.716:18): operation="profile_replace" pid=937 name=/usr/bin/evince-thumbnailer
Apr  4 02:13:10 ubuntu kernel: [   25.289293] type=1505 audit(1270361590.728:19): operation="profile_replace" pid=939 name=/usr/lib/cups/backend/cups-pdf
Apr  4 02:13:10 ubuntu kernel: [   25.290260] type=1505 audit(1270361590.728:20): operation="profile_replace" pid=939 name=/usr/sbin/cupsd
Apr  4 02:13:10 ubuntu kernel: [   25.294040] type=1505 audit(1270361590.732:21): operation="profile_replace" pid=940 name=/usr/sbin/tcpdump
Apr  4 02:13:12 ubuntu kernel: [   26.749457] [drm] Setting GART location based on new memory map
Apr  4 02:13:12 ubuntu kernel: [   26.750156] [drm] Loading R300 Microcode
Apr  4 02:13:12 ubuntu kernel: [   26.750196] [drm] Num pipes: 4
Apr  4 02:13:12 ubuntu kernel: [   26.750205] [drm] writeback test succeeded in 1 usecs

^Z
[2]+  Stopped                 tail -f /var/log/messages




panky@ubuntu:~$ dmesg | grep -e "modem" -e "tty" 
[    0.001023] console [tty0] enabled
[    0.918665] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.919238] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A



panky@ubuntu:~$ uname -r 
2.6.31-14-generic


panky@ubuntu:~$ 
[/FONT]

---

### Post by pdc on 2010-04-03
you are running an old version of this 9.10 

your kernel number is

> 2.6.31-14-

the latest I believe is 

> 2.6.31-17-

........ whatever ....... you need to update ..........

here is the link

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

for safety, post on the install forum on how to do this correctly

you need to do this;

EXAMPLE:

When I plug in a modem, I get:

> sb-storage: device found at 6
[31977.702994] usb-storage: waiting for device to settle before scanning
[31977.703012] usbcore: registered new interface driver usb-storage
[31977.703017] USB Mass Storage support registered.
[31982.703116] usb-storage: device scan complete
[31982.706112] scsi 2:0:0:0: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
[31982.731832] sr1: scsi-1 drive
[31982.732020] sr 2:0:0:0: Attached scsi CD-ROM sr1


and when I "flip" the device I get

> usb-storage: device found at 7
[32019.862430] usb-storage: waiting for device to settle before scanning
[32019.879514] usbcore: registered new interface driver usbserial
[32019.879536] USB Serial support registered for generic
[32019.879617] usbcore: registered new interface driver usbserial_generic
[32019.879620] usbserial: USB Serial Driver core
[32019.882611] USB Serial support registered for GSM modem (1-port)
[32019.882692] option 1-2:1.0: GSM modem (1-port) converter detected
[32019.882818] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
[32019.882847] option 1-2:1.1: GSM modem (1-port) converter detected
[32019.882926] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
[32019.882954] option 1-2:1.2: GSM modem (1-port) converter detected
[32019.883025] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
[32019.883053] option 1-2:1.3: GSM modem (1-port) converter detected
[32019.883157] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB3
[32019.883185] option 1-2:1.4: GSM modem (1-port) converter detected
[32019.883286] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB4
[32019.883313] usbcore: registered new interface driver option
[32019.883317] option: v0.7.2:USB Driver for GSM modems


you are getting none of this

---

### Post by dineshs on 2010-04-04
Please forgive me if I am interfering.I am in alearning stage.Since usb-modswitch has done its work,I think the next step would be
```
sudo modprobe usbserial vendor=0x05c6 product=0x9000
```
Then run 
```
wvdialconf
```
if wvdial is installed(or try gnome-ppp to detect modem)

---

### Post by pankaj143gupta on 2010-04-07
> **dineshs said:**
> Please forgive me if I am interfering.I am in alearning stage.Since usb-modswitch has done its work,I think the next step would be
```
sudo modprobe usbserial vendor=0x05c6 product=0x9000
```Then run 
```
wvdialconf
```if wvdial is installed(or try gnome-ppp to detect modem)



its worling now. thanks for your kind support.

---

### Post by pdc on 2010-04-07
well done to dineshs; I didn't think modprobe usbserial was needed;

great to hear you are up and running

---

