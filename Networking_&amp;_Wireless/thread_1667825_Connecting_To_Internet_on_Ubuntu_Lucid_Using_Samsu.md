---
title: "Connecting To Internet on Ubuntu Lucid Using Samsung Corby Touch Phone"
date: 2011-01-15
forum: Networking &amp; Wireless
---

### Post by ivikas on 2011-01-15
Hello all,

I had to install the pc suite in Windows 7 to connect to the Internet and i had previous experience with Linux not being that internet connection friendly.Anyway i just gave it a try.It was a real wonder,i just opened network manager applet and was surprised to see that it detected my samsung modem and pulled out all the GPRS setting from my mobile(Using vodafone India) and connected to internet.But this surprise does not occur time to time.At first time it connected and some times it does not connect and some times it does.So i thought using wvdial and connect manually.

So here is my script,got from internet,modified a bit,works but highly unreliable(it disconnects very often and i thought any of you guys could get a hack around)

I typed the followed command on my terminal
```
lsusb
```

and the output was

```

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 004 Device 003: ID 04e8:6795 Samsung Electronics Co., Ltd **
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I used modprobe with the string i got from lsusb

```

modprobe usbserial vendor=04e8 product=0x6795

```

Then this is the script i got from the internet and modified a bit to put my connection settings

```

[Dialer Defaults]
Init1 = ATZ
Init2 = AT+CGDCONT=1,"IP","WWW","",0,0,------>This is extra modem initialization strings i recieved from vodafone India Customer Care(124)
Modem Type = Analog Modem
ISDN = 0
Phone = *99***1#-------------->Number to dial for Vodafone India
Modem = /dev/ttyACM0------------------------->Run "dmesg tail" in terminal without qoutes and you will find your modem name
Username =----------------------------------->My Mobile Number Here
Password =----------------------------------->My Mobile Number Here
Baud = 460800
Stupid Mode = 1

```

I dialed with wvdial  and connected to internet

```

vikas@vikas-desktop:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT+CGDCONT=1,"IP","WWW","",0,0,
AT+CGDCONT=1,"IP","WWW","",0,0,
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sat Jan 15 23:12:33 2011
--> Pid of pppd: 2606
--> Using interface ppp0
--> pppd: `Hï¿½[08]ï¿½Oï¿½[08]
--> pppd: `Hï¿½[08]ï¿½Oï¿½[08]
--> pppd: `Hï¿½[08]ï¿½Oï¿½[08]
--> pppd: `Hï¿½[08]ï¿½Oï¿½[08]
--> pppd: `Hï¿½[08]ï¿½Oï¿½[08]
--> pppd: `Hï¿½[08]ï¿½Oï¿½[08]
--> local  IP address 112.79.185.251
--> pppd: `Hï¿½[08]ï¿½Oï¿½[08]
--> remote IP address 0.79.185.251
--> pppd: `Hï¿½[08]ï¿½Oï¿½[08]
--> primary   DNS address 10.11.230.2
--> pppd: `Hï¿½[08]ï¿½Oï¿½[08]
--> secondary DNS address 10.11.230.3
--> pppd: `Hï¿½[08]ï¿½Oï¿½[08]

```

But just within 1 or 2 minutes it disconnects...giving this message...

```

--> Disconnecting at Sat Jan 15 23:14:33 2011
--> The PPP daemon has died: Lack of LCP echo responses (exit code = 15)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> Provider is overloaded(often the case) or line problem.
--> The PPP daemon has died. (exit code = 15)
vikas@vikas-desktop:~$ 

```

Any workaround on this will be highly appreciated,Thanks in advance.

with regards,
vikas

---

