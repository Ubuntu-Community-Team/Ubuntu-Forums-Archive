---
title: "lubuntu do not detect 3g mobile broadband huawei"
date: 2010-05-04
forum: Networking &amp; Wireless
---

### Post by alexfish on 2010-05-04
hi

can you boot up the computer without the modem wait for the system to settle then connect the modem

post the results of these commands from the terminal 

Code:

dmesg | grep -e "modem" -e "tty" 

Code:

lsusb

thanks in advance 

alexfish

---

### Post by phillw on 2010-05-06
Hi, one of the people on the #lubuntu IRC channel has released a work-around for lubuntu 10.04, as the work-around for ubuntu 10.04 does not work with lubuntu. (one day maybe they'll fix it at the kernel level and we can have 3G devices working out of the box as used to happen).

> NM Mobile Broadband workaround

Lubuntu ships with console PPP dialer wvdial, and menu driven PPP
configuration utility pppconfig.


1. wvdialconf/wvdial
********************

Plug in your modem and run "sudo wvdialconf". If everything is ok,
wvdial will generate a configuration file /etc/wvdial.conf

Edit this file, uncomment and enter Phone, Password and Username.

Run "sudo wvdial" to get a connection

If you need to enter an Access point, add following lines to the
/etc/wvdial.conf:

Init1 = ATZ
Init2 = AT+CGDCONT=1,"IP","your.access.point.name"


2. pppconfig/pon/poff/plog
**************************

Run "sudo pppconfig"

Select "Create a connection"

Enter connection name, e.g.: 3g

Select "Use dynamic DNS"

Check Authentication Method for provider and hit "Ok"

Enter username

Enter password

Enter port speed

Select Tone

Enter phone number, e.g.: #777

Try autoprobe modem.
If it fails just enter your modem device, e.g.: /dev/ttyUSB0
To find out your modem device unplug it/plug it, run "dmesg" and see
log output.

Select "Finished Write files and return to main menu"

Quit

A new configuration file will be placed in /etc/ppp/peers/ folder.

Now when you have made a PPP configuration run "sudo pon 3g" to
initiate connection.
"3g" is a provider name you've entered before.

Run "sudo plog" to see connection log output.

Run "sudo poff" to disconnect.

Regards,
Phill.

---

### Post by alexfish on 2010-05-13
hi all

don't know what happen to the original OP , my post was in response to it:

anyhow , this work around would apply may to any version of Ubuntu if the Network Manager fails to connect , generally the case where the modem has multiple control lines

this is the reason for the {dmesg | grep -e "modem" -e "tty"} this is important as with wvdial and ppp , you  may have to manually enter the ttyX to get the correct connection

below is an example :

alexfish@alexfish-desktop:~$ dmesg | grep -e "modem" -e "tty"
[    0.000000] console [tty0] enabled
[    0.262965] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.263234] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   22.298251] USB Serial support registered for GSM modem (1-port)
[   22.298430] option 1-10:1.0: GSM modem (1-port) converter detected
[   22.298610] usb 1-10: GSM modem (1-port) converter now attached to [COLOR=Blue]ttyUSB0[/COLOR]
[   22.298628] option 1-10:1.1: GSM modem (1-port) converter detected
[   22.298766] usb 1-10: GSM modem (1-port) converter now attached to[COLOR=Blue] ttyUSB1[/COLOR]
[   22.298787] option 1-10:1.3: GSM modem (1-port) converter detected
[   22.298957] usb 1-10: GSM modem (1-port) converter now attached to [COLOR=Blue]ttyUSB2[/COLOR]
[   22.299000] option: v0.7.2:USB Driver for GSM modems
alexfish@alexfish-desktop:~$ 

this modem has TWO control lines ttyUSB1 and ttyUSB2 , in some instances the dialler may select ttyUSB0 or ttyUSB1 automatically, but I know this modem works on ttyUSB2

you will have to try them, from the results of the {dmesg | grep -e "modem" -e "tty"}

in response to the above comment  (one day maybe they'll fix it at the kernel level and we can have 3G  devices working out of the box as used to happen).user could try **Sakis3g** details can be found here

[How To : Mobile Broadband Connections [ Ubuntu  10.04 : 9.10 : 9.04 ]]("http://ubuntuforums.org/showthread.php?t=1466490")

to highlight **kernel leve**l problem , I would highlight **Modem  problem** and **software problem** , one been the modem firmware  and the other is the software which connects the modem, **it can't be a  kernel issue** if the **modem is detected on the system** with the  above command

regards

alexfish

---

### Post by Bagustrix on 2010-07-24
I have tried your 3G mobile broadband connection setting, but I still cannot connect to the internet. By default, my probe modem is on ttyS0 (cannot connect), and I changed to ttyUSB0, it's still unconnected. From the wvdial output, cannot configure pppd.
Any one has idea, so my mobile device can be detected by network manager as usual and I can build my network as on ubuntu??

---

### Post by pdc on 2010-07-24
turn your computer on; plug your device in;

open a terminal

tell us what

> lsusb says: copy and paste the results back here;

ALSO: copy and paste the command below into a terminal

> dmesg | grep tty 

and tell us what you get;

let's go from there .............

---

### Post by Alex22 on 2010-07-31
Guys, good news! :D

I found out, what is needed, to get the regular Ubuntu method (based on NetworkManager) working. No matter - straight one or workaround with usb_modeswitch.

The answer is, you just need to install small text-based **modem-manager**.

**sudo apt-get install modemmanager**

That's it. Works beautifully after restart.

Greetz, Alex

---

### Post by jpxsat on 2010-08-03
Doesn't work for me...
Since i don't have internet connection via 3g modem, i've downloaded the .deb package in another computer and installed it... and it doesn't work!! :(

---

### Post by jcris on 2010-08-03
@jpxsat
After you install modemmanager, plug in your 3g modem, and right click your network manager icon down by the clock. You should now see a new checkbox that says enable mobile broadband, if you check that all should work fine. It should throw up a dialog to configure your new 3g connection.

---

### Post by gauravkumar on 2010-08-04
Please help somebody...UBUNTU 10.04
i have tried many things from **wvdial to modswitch** but still nothing works for the same issue.....
Only once it got connected as i mentioned in my earlier post...but after restarting its gone again...
When i go to System->Preferences->Network Connections and try to  add the new Mobile connection, it does not even detect the device...
Even gnome-ppp and "wvdial netconnect" does not work.....Both are not able to detect the device....
Below is the Log to clarify things...

gaurav@gaurav-laptop:/$ lsusb
Bus 002 Device 005: ID 12d1:1446 Huawei Technologies Co., Ltd. 
Bus 002 Device 003: ID 0bc2:2120 Seagate RSS LLC 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 413c:8162 Dell Computer Corp. 
Bus 001 Device 005: ID 413c:8161 Dell Computer Corp. 
Bus 001 Device 004: ID 0c45:6417 Microdia 
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
gaurav@gaurav-laptop:/$ sudo wvdial netconnect
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
gaurav@gaurav-laptop:/$ 
gaurav@gaurav-laptop:/$ gnome-ppp

(gnome-ppp:8001): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gnome-ppp:8001): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
WVCONF: /home/gaurav/.wvdial.conf
GNOME PPP: STDOUT: Editing `/dev/null'.
GNOME PPP: STDERR: Modem Port Scan<*1>: S0   S1   S2   S3   
GNOME PPP: STDOUT: 
GNOME PPP: STDOUT: Scanning your serial ports for a modem.
GNOME PPP: STDOUT: 
GNOME PPP: STDOUT: 
GNOME PPP: STDOUT: 
GNOME PPP: STDOUT: Sorry, no modem was detected!  Is it in use by another program?
GNOME PPP: STDOUT: Did you configure it properly with setserial?
GNOME PPP: STDOUT: 
GNOME PPP: STDOUT: Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)
GNOME PPP: STDOUT: 
GNOME PPP: STDOUT: If you still have problems, send mail to <wvdial-list@lists.nit.ca>.

---

### Post by pdc on 2010-08-04
in lsusb when it says

> 12d1:1446

this is the ID of a device that has NOT switched from being seen as storage device; 

go here

[http://packages.debian.org/sid/usb-modeswitch](http://packages.debian.org/sid/usb-modeswitch)

go down the page; select the right version of usb_modeswitch (ie i386 for 32bit etc)

download; install; reboot  your system; now plug your device in;

type

> lsusb

you should now see 

> 0x12d1:0x14ac ..... or some such number: 

the point is it should be different to the original 1446 ..

now copy and paste this into a terminal

> dmesg | grep tty

and hopefully you will see ttyUSB0 or somesuch:

and you could now configure ..

any joy?

---

### Post by Alex22 on 2010-08-04
Hallo again guys,

As **pdc** said, **1446** is this dr. Hyde part of the stick (storage). To turn it to modem, you use **usb_modeswitch** program. 
Don't bother using wvdial or some text based pppd confs with secret hacking "AT" commands, **coz' your problem is not in the net management, but in the modem discovery!** (even if it's seen in the lsusb, but as a stick, as we said just above)

DETAILED SOLUTION (as example, with my huawei 1750):

1) ```
sudo apt-get install usb_modeswitch
```

2) then make its conf file (**/etc/usb_modeswitch.conf**) look like:

```
DefaultVendor=  0x12d1
DefaultProduct= 0x1446

TargetVendor = 0x12d1
TargetProduct= 0x1001
MessageContent="55534243000000000000000000000011060000000000000000000000000000"
MessageEndpoint=0x01
CheckSuccess=5
```

3) Then make the Udev rule, to launch usb_modeswitch, when the stick is found (**/etc/udev/rules.d/15-huawei-e1750.rules**):

```
SUBSYSTEM=="usb", 
SYSFS{idProduct}=="1446", 
SYSFS{idVendor}=="12d1", 
RUN+="/usr/sbin/usb_modeswitch"
```


**Some additional tips**: Above method is only for huawei 1750. If you have different model, change idProduct in point 3 and DefaultProduct in point 2. It's to be easily found by simple **lsusb** command. 
Don't change "Target" params. 

If you wanna use some else manufacturer's modem, try changing also Vendor Id, but i don't know what should be as Target Product Id. Maybe some generic modem (some even, low, nice number ;) )


!!!IMPORTANT!!!
[b]But, there are always some sour buts. The problem lies in the "MessageContent" and the "Message Endpoint". They are different for every model of modem and can be found by using some USB sniffer program, similiar to Ethernet or wifi sniffers.
They say it's easy with Windows programs.
But i didn't manage to get info using Linux programs and using Wine showed no messages either.

Much of Luck
[/b]

P.S. In Ubuntu i have no /dev/ttyUSB0 at all. In Lubuntu it was present.

---

### Post by gauravkumar on 2010-08-10
Thanks a ton dude....

---

