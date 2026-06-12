---
title: "Neotel(cdma usb modem) working on Ubuntu"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by Beanmonster on 2009-05-14
For all South African users out there who want to get their neotel up and running:

Decided to install Jaunty as my Hardy was very messy. I've been running linux since Breezy but still regard myself as a noobie. 

After much trial and tribulation, and many failed attempts on Hardy, I finally got my Neotel Prime running, first time round on Jaunty.

Following is a step-by-step process which I take _NO CREDIT_ for!

I am merely posting this in an attempt to make the process a bit easier to understand and follow for all linux(Ubuntu) users out there wishing to use Neotel.

This was done on a fresh installation of Ubuntu 9.04 Jaunty Jackalope.

*It helps having an internet connection for the first step of the process... Otherwise packages can be downloaded seperately and google will provide details on unpacking and installing.*

```
Step 1)
First download the necessary packages we need.

Open System>Administration>Synaptic Package Manager

Find and install:
[CODE]     1) wvdial
     2) linux-source
```

If the above are not listed, open terminal, use the code(s):
```
     1) $ sudo apt-get install wvdial
     2) $ sudo apt-get install linux-source
```

Step 2)  --- All credit goes to [cbrunsdonza ]("http://mybroadband.co.za/vb/showpost.php?p=2751375&postcount=6")for this step ---

Open a terminal and type: 
```
$ sudo -s
$ cd /usr/src
$ tar xjvf linux-source-2.6.28.tar.bz2
$ gedit /usr/src/linux-source-2.6.28/drivers/usb/serial/option.c
```

"Now look for static struct usb_device_id option_ids[] about line 300 and add the following just above it:"
```
        // +++ chrisb
        #define NEOTEL_DEVICE_VENDOR_ID                 0x1d09
        #define NEOTEL_DEVICE_PRODUCT_ID                0x4000
        // +++
```

"and then in the struct add:" (the line in **BOLD**)
```
static struct usb_device_id option_ids[] = {
    **{ USB_DEVICE(NEOTEL_DEVICE_VENDOR_ID, NEOTEL_DEVICE_PRODUCT_ID) },**
    { USB_DEVICE(OPTION_VENDOR_ID, OPTION_PRODUCT_COLT) },
    { USB_DEVICE(OPTION_VENDOR_ID, OPTION_PRODUCT_RICOLA) },
```

save and close gedit.

"To compile:"
```
$  cd /usr/src/linux-source-2.6.28/drivers/usb/serial/
$  make -C /lib/modules/`uname -r`/build M=`pwd`
```

If successful you should see a long list without errors resembling the following:
```
             make: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
               LD      /usr/src/linux-source-2.6.24/drivers/usb/serial/built-in.o
               CC [M]  /usr/src/linux-source-2.6.24/drivers/usb/serial/usb-serial.o
               CC [M]  /usr/src/linux-source-2.6.24/drivers/usb/serial/generic.o
               CC [M]  /usr/src/linux-source-2.6.24/drivers/usb/serial/bus.o
             ....
             make: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
```

"Backup the old drivers"
```
$  mv /lib/modules/2.6.28-11-generic/kernel/drivers/usb/serial/option.ko /lib/modules/2.6.28-11-generic/kernel/drivers/usb/serial/option.ko.backup
```

"Now add new drivers (compiled):"
```
$ cp  /usr/src/linux-source-2.6.28/drivers/usb/serial/option.ko  /lib/modules/2.6.28-11-generic/kernel/drivers/usb/serial/option.ko
```

"You also need to load the new option:"
```
$ gedit /etc/modules
```

"And just add to the end of the file:"
```
        option
```

Reboot your computer, open a terminal again and type:
```
$ lsusb
```

Which should produce, among others:
```
Bus 002 Device 002: ID 1d09:4000 TechFaith Wireless Technology Limited
```

Step 3) --- All credit goes to [potgietdl]("http://mybroadband.co.za/vb/showpost.php?p=2547473&postcount=59") ---

Open a terminal and type:
```
$ sudo -s
```

And then:
```
$ wvdialconf
```

Which should produce something similar to:
```
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   
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

**Found a modem on /dev/ttyUSB0.**
Modem configuration written to /etc/wvdial.conf.
ttyUSB0<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

```

Now run:
> $ gedit /etc/wvdial.conf

Copy and paste the following and change your username and password:
```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 9600
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Stupid Mode = 1
Phone = #777
Modem = /dev/ttyUSB0
Username = **1234567890**@neotel.co.za
Dial Command = ATDT
Password = **1234**
Baud = 460800
PPPD Options = crtcts multilink usepeerdns lock defaultroute

[Dialer neotel]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Baud = 460800
Stupid Mode = 1
Modem = /dev/ttyUSB0
Modem Type = USB Modem
Dial Command = ATDT
PPPD Options = crtcts multilink usepeerdns lock defaultroute
```

Save and close gedit

Step 4)

In the terminal, as any user, type: 
> $ wvdial

Which, if successful, should result in:
> --> WvDial: Internet dialer version 1.60
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
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Thu May 14 22:59:46 2009
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 4541
--> Using interface ppp0
--> pppd: 0&#65533;[1c][08]P&#65533;[1c][08]
--> pppd: 0&#65533;[1c][08]P&#65533;[1c][08]
--> pppd: 0&#65533;[1c][08]P&#65533;[1c][08]
--> pppd: 0&#65533;[1c][08]P&#65533;[1c][08]
--> pppd: 0&#65533;[1c][08]P&#65533;[1c][08]
--> local  IP address 41.174.2.250
--> pppd: 0&#65533;[1c][08]P&#65533;[1c][08]
--> remote IP address 2.2.2.2
--> pppd: 0&#65533;[1c][08]P&#65533;[1c][08]
--> primary   DNS address 41.160.0.36
--> pppd: 0&#65533;[1c][08]P&#65533;[1c][08]
--> secondary DNS address 41.160.0.37
--> pppd: 0&#65533;[1c][08]P&#65533;[1c][08]


[B]and a fully working internet connection!!!!! :D
[/B]

to disconnect, in the terminal that is running wvdial, **hold ctrl-c**[/CODE]

Thank you once again to [cbrunsdonza]("http://mybroadband.co.za/vb/member.php?u=60296") and [potgietdl]("http://mybroadband.co.za/vb/member.php?u=62853")

I really hope this helps somebody and I really hope it works as nicely as it worked for me.

I haven't looked at a graphical way of dialing yet but I'll keep everybody updated. :p

---

### Post by gsrkashyap on 2009-05-15
hey just a piece of advice 
how can you do apt-get install wvdial if you dont have internet connection? so it's better you mention that get wvdial & linux-source from other source of internet connection.

wht do u say?

---

### Post by Beanmonster on 2009-05-16
> It helps having an internet connection for the first step of the process... Otherwise packages can be downloaded seperately and google will provide details on unpacking and installing.

:) thanks for the lookout though :)

---

### Post by wimbleberry on 2009-07-22
Hi guys

I have spent alot of time with this now and even went to the lengths of installing a VM, because the VM controller passes the host USB Neotel connection to the VM as an ethernet connection and I could download packages that way. I can't get the serial usb file to compile.

make -C /lib/modules/`uname -r`/build M=`pwd` is where it falls over for me. I get the following error message:

make: *** /lib/modules/uname -r/build: No such file or directory. Stop.

I am using the monkey see, monkey do technique and don't have any insight into how to fix the problem. Is the 'uname -r' piece meant to be a user specific name sequence? Or did I miss a component somewhere?

Vanilla JJ 9.04 installed off the downloaded ISO image, relatively old PC, but runs XP fine.

Ta for help.

---

### Post by GeoffreyBernardo on 2009-10-11
When I try to back-up the old drivers and when I try to load the new ones, I get the error "cp: cannot create regular file" and "no such file or directory'.

What could be the problem?

---

### Post by diepes on 2010-05-02
> **wimbleberry said:**
> Hi guys
...
make: *** /lib/modules/uname -r/build: No such file or directory. Stop.
...
'uname -r' piece meant to be a user specific name sequence? 
...
Ta for help.

uname -r    should give you the current version e.g. 2.6.32-21-generic
it is a way to find the correct directory for the module code.

Your problem is that you use the wrong quotes for it, you should use the back tick on both side's, this causes bash to execure it and replace it with the version.

The back tick is the one on the top left on my computer, just under escape >`<
tiny tick leaning to the left.

you can test with   # echo `uname -r`
if this gives you the version you have the right tick.

Cheers,

---

### Post by andre_v on 2010-08-17
On lucid the setup is fairly straight forward

sudo su
modprobe -v option
echo "1d09 4000" > /sys/bus/usb-serial/drivers/option1/new_id

The first time you connect you need to edit the connection properties to reflect your phone number and password.

1) My connection keep on dropping if i do not have an alternative connection available. If I connect my cellphone (do not activate the connection) and then select the neotel connection, it connects and stays connected.
2) I also need to issue the commands every time the pc is rebooted.

Does anyone know about a permanent fix for these two issues?

---

### Post by alexfish on 2010-08-17
hi

as regards the connection when the phone is connected . are you using Network Manager if so ,note the addresses in the connection information , check when using the device and no phone , then both , 

can you post the results of primary and secondary servers 

or from the terminal

Code:
cat /etc/resolv.conf

have seen a few posts regarding this device , as regards dropping the connection
have not seen a fix for this as yet but will try to help

can you post results of

Code:

uname -m

and 

uname -r



regards

alexfish

---

### Post by andre_v on 2010-08-20
Hi Alexfish,
Thanks for the response.

When the phone is not connected, there is a popup stating that the connection is successful which then disconnects immediately thereafter. 

Here is the information you requested:
nameserver 41.160.0.36
nameserver 41.160.128.12
uname -m  -> x86_64
uname -r  -> 2.6.32-24-generic

Also not sure whether it was clear in the previous post: I connect the phone and see the option to use the phone as modem, but do not need to activate the connection. Thought it might be a problem with the networkmanager, but unsure how to test.

---

### Post by alexfish on 2010-08-20
> **andre_v said:**
> Hi Alexfish,
Thanks for the response.

When the phone is not connected, there is a popup stating that the connection is successful which then disconnects immediately thereafter. 

Here is the information you requested:
nameserver 41.160.0.36
nameserver 41.160.128.12
uname -m  -> x86_64
uname -r  -> 2.6.32-24-generic

Also not sure whether it was clear in the previous post: I connect the phone and see the option to use the phone as modem, but do not need to activate the connection. Thought it might be a problem with the networkmanager, but unsure how to test.

hi Andre

need to **clarify** the **addresses** from previous post

as regards the connection when the phone is connected . are you using  Network Manager if so ,note the addresses in the connection information ,  check when using the **device and no phone** , then **both** ,
(**Device only...............**)

I will be able to ascertain if the Network Manager is by passing the modem  and using the phone (when both devices are connect)  , 

Have you tried the device on 32bit

can you post the addresses via Private Message

Regards

alexfish

---

### Post by Nick Kruger on 2010-08-20
I've also just connected with my Neotel phone.

Couldn't do it with 9.04, but it's easy with 10.04

1.  lsusb
2.  sudo modprobe usbserial vendor=0x1d09 product=0x4000
3.  ls /dev/ttyU*

Now it shows up in Network Connections / Mobile Broadband and you can add connection.

Don't know enough yet follow all the topics discussed in this thread, but did any find a way to avoid 1 and 2 above every time I restart the computer ?

Thanks,
Nick (Cape Town)

---

### Post by Nick Kruger on 2010-08-20
Hi Andre-V

I managed to find a solution which seems to work.

1. sudo nano /etc/rc.local

2. add this before the exit 0 line 

modprobe usbserial vendor=0x1d09 product=0x4000

When I reboot my Neotel connection starts automatically.

Nick Kruger

---

