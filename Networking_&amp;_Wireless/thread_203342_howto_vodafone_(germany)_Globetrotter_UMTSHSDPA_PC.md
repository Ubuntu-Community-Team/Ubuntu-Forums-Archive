---
title: "howto: vodafone (germany) Globetrotter UMTS/HSDPA PCMCIA Card"
date: 2006-06-25
forum: Networking &amp; Wireless
---

### Post by info2 on 2006-06-25
Hello out there.
Yesterday i got a UMTS/HSDPA-PCMCIA Card from my local vodafone-dealer.
The hardware i have is a newer model and doesn't emulate USB-Devices like the older ones.
I used many howto's allover the internet. The most usefull i've found on [http://www.pharscape.org/]("http://www.pharscape.org/")  and thay also provide the tools i use, so much thanks to them.

This is how i've done. I'll be lucky if others can make it, too, and maybe find even better ways to use that card.

Card:
[INDENT]Option GT 3G+ EMEA  (GlobeTrotter 3G+)
The Serial starts with "NL"
Fortunatly, the original vendor of that card provides a driver-package.[/INDENT]
:!: If you want to eject the card from the slot, use "sudo cardctl eject" bevore. Sometimes Dapper hung after I pulled out the card.

"lspci" reports the card like that:
> 0000:02:00.0 Network controller: Option N.V.: Unknown device 000c
 


What we need: 
[INDENT]the driver [here]("http://www.pharscape.org/3G/nozomi.tgz")
wvdial (is shipped with dapper)
gcom [here]("http://www.pharscape.org/3G/gcom")
the "build-essential" - package 
the Kernel-Headers for your kernel
a cup of fresh roasted ubuntu[/INDENT]


######basics######
The UMTS-card will book in the UMTS-network and open a connection between the CARD and the ENDPOINT.
The Laptop uses a ppp-connection to communicate with the CARD, not with the card's ENDPOINT. Thats why we can and NEED to disable compression in our ppp-connection. The UMTS-card will compress data for itself.


######the driver module######
First you need to make the driver. Extract the archive, open a terminal, change directory to where you have extracted it and run "make".
This will hopefully have created a module named "nozomi.ko"

I have created the directory and copied it to /lib/modules/<matching kernel-directory>/kernel/drivers/umts/

You can use any other directory, just change the path in the following script.

Now let's check the module:
Insert the PCMCIA-card
Insert the module with
> sudo insmod /lib/modules/2.6.15-25-686/kernel/drivers/umts/nozomi.ko
(or where ever you put the module)

If everything is crunchy now, you will have 4 new devices. Check it:
> admin@soulrage:~$ ls /dev/noz*
/dev/noz0  /dev/noz1  /dev/noz2  /dev/noz3
With the four devices, you can be online and send/recieve sms without breaking the connection.


######gcom######
gcom is a tool that initialize the UMTS-Card. We surely don't really need it since we can do it with wvdeal and AT-Commands, too, but i wasn't able to find out how :) Also, gcom informs you about the card's properties and the signal strength (what we can also find out with AT-Commands)

Extract the archive somewhere, open a terminal and change directory to where you have extracted it. 
Run "make all". This will create an executable. I also run "sudo make install", you don't need it but then you have to add a path to the following script, pointing to the executable.

Now let's check gcom:
> admin@soulrage:~$ sudo gcom -d /dev/noz0 info
##### GlobeTrotter Configuration #####
Manufacturer Text:      Option
IMEI and Serial Number: xxxxxxxxxxxxxxxxxxx,NLxxxxxxxx
Manufacturer's Revision: (Date: Feb 06 2006, Time: 12:53:15)
Hardware Revision:      2.1
Network Locked:         0
Customisation:          Not defined
Band settings:          Europe 900/1800MHz (4)
Auto Attach:
##### END #####


If it looks like this it looks good.

Now you can check if the card accept your pin:
> admin@soulrage:~$ sudo gcom -d /dev/noz0

Enter PIN number: 1234
Waiting for Registration..(120 sec max).....
Registered on Home network: "Vodafone.de",0
Signal Quality: 12,0


If it looks like that, it looks very well.


######config wvdial######
We need to create/change two files:

Attention: You may need to change "web.vodafone.de" to the Accesspoint-Name
that is used where you live. To get a list of APN's, there is a script in the directory where you compiled gcom. Run that command there:
> admin@soulrage:~/Desktop/gcom$ sudo ./gcom -d /dev/noz0 operator
SIM ready
Waiting for Registration..(120 sec max)
Registered on Home network: "Vodafone.de",0
Signal Quality: 12,0
Getting Operator list: .........

+COPS: (2,"Vodafone.de","voda DE","26202",0),(1,"Vodafone.de","voda DE","26202",2),(3,"o2 - de","o2 - de","26207",0),(3,"E-Plus","E-Plus","26203",2),(3,"T-Mobile D","TMO D","26201",0),(3,"E-Plus","E-Plus","26203",0),,(0, 1, 3),(0-2)

==============================================================
Format: (Access,Long Name, Short Name, Network ID [,Technology])
Access: 2 - Registered, 1 - Available, 3 - Forbidden
Technology: 0 - GSM/GPRS, 2 - UMTS (Not available on all cards)

Enter the Network ID to attempt manual registration
 [blank = automatic selection]:
Registration request accepted
Command was: AT+COPS=0

You don't need to change the username and password, vodafone ignores them, but i think an empty string will close the ppp-connection, so let it as it is.

/etc/wvdial.conf:
> [Dialer Defaults]
Phone = *99***1#
Username = username
Password = password
Stupid Mode = 1
Dial Command = ATDT

[Dialer hsdpa]
Modem = /dev/noz0
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

/etc/ppp/peers/wvdial:
> plugin passwordfd.so
noauth
name wvdial
replacedefaultroute
noipdefault
nomagic
usepeerdns
ipcp-accept-local
ipcp-accept-remote
nomp
noccp
nopredictor1
novj
novjccomp
nobsdcomp

Don't ask me what all those parameters stand for, i don't know, and i don't know if all of them are neccessary.

Now let's check if you can use your UMTS :)  (Yes, you better pray now)
If you run all Checks before, you just need to run. (If not, use the Script in the next part)
> sudo wvdial hsdpa vodafone You can force a lower speed with adding "384k" to the command, but who want to do that? :)

You may need to try it two or three times, I didn't get connectet at the first time sometimes. But if it work, it will look like that:
> admin@soulrage:~/Desktop/gcom$ sudo wvdial hsdpa vodafone
--> WvDial: Internet dialer version 1.55
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","web.vodafone.de";
AT+CGDCONT=1,"IP","web.vodafone.de";
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
CONNECT 1800000
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sun Jun 25 10:41:14 2006
--> Pid of pppd: 8622
--> Using interface ppp0
--> local  IP address 10.226.212.160
--> remote IP address 10.64.64.64
--> primary   DNS address 139.7.30.125
--> secondary DNS address 139.7.30.126



######script for running everything######
To let UTMS start with one click or one command, i use the following script:


> #!/bin/bash
echo "loading module"
sudo insmod /lib/modules/2.6.15-25-686/kernel/drivers/umts/nozomi.ko

echo "initialising umts card"
gcom -d /dev/noz0
wait

echo "trying to connect"
sudo wvdial hsdpa vodafone



That is working for me. 
Note that I use a PCMCIA-Card of the newest generation. If you own an older one (the driver don't work for you) , google for it or look at [http://www.pharscape.org/]("http://www.pharscape.org/").

I hope this howto is useful so somebody. 
I also hopy, that you will post comments and make the howto better. Maybe somebody is familar with AT-Commands and can tell us how to get some status-messages like current link-quality, etc, so that we can make a graphical interface some day.

I also hope that Edgy will have better UTMS-Support. I think UMTS will be used often in the near future. I have 1.8MBit with that Card and it costs about 60 Euro a Month at the moment. Since i need to travel a lot, being here and there for month, this is the only way to have Internet everywhere i am.


=the-fallen=

---

### Post by hfdragon on 2006-06-25
Thanks for your post !

Now I know that UMTS PCMCIA cards can work with Dapper :-)

I'm having problems with my Novatel Merlin U530, which was working quite well with Breey, but i'st wotking properly now with dapper.

---

### Post by info2 on 2006-06-25
Your Merlin must be one of those Cards that emulate USB-Devices, isn't it?
I hope you can make it work again. :)

---

### Post by hfdragon on 2006-06-26
Not at all, it is a PCMCIA card which creates a serial port... no USB at all.

I don't have any specific driver, I only use the stadard pcmcia and serial drivers.

There is no problem when I insert the card, I can create a connection (ppp0) without any problem, but the connection is sloooooow, and I have a lot of errors (receiving packets) when I check with ifconfig.

---

### Post by info2 on 2006-06-28
Maybe you set up a slow serial communication rate?

---

### Post by hfdragon on 2006-06-28
I don't think so, since it was working fine with hoary and breezy, and I didn't change anything since..

And the number of errors on RX packets is really high (about 25% of packets)...

---

### Post by amasidlover on 2006-07-27
I'm having a very similar problem, very high RX error percentage - although it seems that this is specifically causing problems with connections made to https , imaps and ssmtp sites - ordinary http is working but very slow.

---

### Post by hfdragon on 2006-07-27
I think I've found where the problem comes from :

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/45928]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/45928")

It's a kernel issue, and it has been corrected in kernel 2.6.16..

I've build a custom kernel 2.6.17 and now it is working perfectly.

I think we'll have to wait for edgy eft to have it corrected.

---

### Post by mips on 2006-07-27
info2,

Would you be so kind as to post this in the Howto section as well if you haven't already.

---

### Post by francesco1964 on 2006-09-24
Hi,

I was using UMTS Merlin U530 since 5.04 with no problems, and with 5.10 too with a 2002 Aspire with 1.3 GHz Celeron.

Then I've used 5.10 with Thinkpad R52 with 1.8 GHz Centrino, and have the problem that the pcmcia modem worked only if you move on the touchpad, it used to set the pcmcia card with the same interrupt.

Then with Dapper 6.06 on the same machine, the interrupt is now 3 the modem works ok, the connection goes ok, but I get wrong gateway routing...

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
62.13.160.101   0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
0.0.0.0         0.0.0.0         0.0.0.0         UG    0      0        0 ppp0

I've tryed to delete the worng routing and to set the good one

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
62.13.160.101   0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
0.0.0.0         62.13.160.101   0.0.0.0         UG    0      0        0 ppp0

but still not working

Thanks for any help

Francesco

---

### Post by Jalex on 2006-10-31
Hi

I am brand new to Ubuntu, I am trying to get my Globetrotter UMTS card to work. When I try to make the driver nozomi.ko, I get an error In function 'receive_data' struct tty_struct has no member named 'flip'

I would appreciate help.

---

### Post by jesnev on 2006-11-15
Hi,
this is just to add that I have the same problem. And I am not new,...
I have never needed to  compile a driver before, but this seems to be the first time. 
Why do I get:
Warning: Compiling for 2.6: 
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/jn/GlobeTrotter/nozomi modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/jn/GlobeTrotter/nozomi/nozomi.o
/home/jn/GlobeTrotter/nozomi/nozomi.c: In function ‘receive_data’:
/home/jn/GlobeTrotter/nozomi/nozomi.c:947: error: ‘struct tty_struct’ has no member named ‘flip’
make[2]: *** [/home/jn/GlobeTrotter/nozomi/nozomi.o] Error 1
make[1]: *** [_module_/home/jn/GlobeTrotter/nozomi] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [default] Error 2
???????
Quite frustrating. It all works fine in Windows XP.

---

### Post by daller on 2006-11-19
I'm running Edgy Eft, and have problems with the card named "Globetrotter 3G QUAD" and Model:"GT 3G QUAD" 

It's an Option Globetrotter 3G card, with serial "QL*"

I think I've fiddled a little to much, since it asks for a PUK code now :( - Any ideas?

Anyway, this is what happens when I plug it in:

```
Nov 19 13:22:04 localhost kernel: [17179828.256000] pccard: CardBus card inserted into slot 0
Nov 19 13:22:04 localhost kernel: [17179828.256000] yenta EnE: chaning testregister 0xC9, 04 -> 04
Nov 19 13:22:04 localhost NetworkManager: <debug info>^I[1163938924.453689] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1033_35').
Nov 19 13:22:04 localhost NetworkManager: <debug info>^I[1163938924.567560] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1033_35_0').
Nov 19 13:22:04 localhost kernel: [17179828.432000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
Nov 19 13:22:04 localhost kernel: [17179828.432000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
Nov 19 13:22:04 localhost kernel: [17179828.432000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
Nov 19 13:22:04 localhost kernel: [17179828.432000] PCI: Setting latency timer of device 0000:02:00.0 to 64
Nov 19 13:22:04 localhost kernel: [17179828.432000] ohci_hcd 0000:02:00.0: OHCI Host Controller
Nov 19 13:22:04 localhost kernel: [17179828.432000] ohci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 5
Nov 19 13:22:04 localhost kernel: [17179828.432000] ohci_hcd 0000:02:00.0: irq 10, io mem 0xe2000000
Nov 19 13:22:04 localhost kernel: [17179828.516000] usb usb5: configuration #1 chosen from 1 choice
Nov 19 13:22:04 localhost kernel: [17179828.516000] hub 5-0:1.0: USB hub found
Nov 19 13:22:04 localhost kernel: [17179828.516000] hub 5-0:1.0: 1 port detected
Nov 19 13:22:04 localhost kernel: [17179828.620000] PCI: Enabling device 0000:02:00.1 (0000 -> 0002)
Nov 19 13:22:04 localhost kernel: [17179828.620000] ACPI: PCI Interrupt 0000:02:00.1[B] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
Nov 19 13:22:04 localhost kernel: [17179828.620000] PCI: Setting latency timer of device 0000:02:00.1 to 64
Nov 19 13:22:04 localhost kernel: [17179828.620000] ohci_hcd 0000:02:00.1: OHCI Host Controller
Nov 19 13:22:04 localhost kernel: [17179828.620000] ohci_hcd 0000:02:00.1: new USB bus registered, assigned bus number 6
Nov 19 13:22:04 localhost kernel: [17179828.620000] ohci_hcd 0000:02:00.1: irq 10, io mem 0xe2001000
Nov 19 13:22:04 localhost kernel: [17179828.708000] usb usb6: configuration #1 chosen from 1 choice
Nov 19 13:22:04 localhost kernel: [17179828.708000] hub 6-0:1.0: USB hub found
Nov 19 13:22:04 localhost kernel: [17179828.708000] hub 6-0:1.0: 1 port detected
Nov 19 13:22:05 localhost NetworkManager: <debug info>^I[1163938925.006258] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_02_00_1').
Nov 19 13:22:05 localhost NetworkManager: <debug info>^I[1163938925.065330] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_02_00_0').
Nov 19 13:22:05 localhost NetworkManager: <debug info>^I[1163938925.110200] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_02_00_1_if0').
Nov 19 13:22:05 localhost NetworkManager: <debug info>^I[1163938925.172053] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_02_00_0_if0').
Nov 19 13:22:05 localhost NetworkManager: <debug info>^I[1163938925.250977] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_02_00_0_usbraw').
Nov 19 13:22:05 localhost NetworkManager: <debug info>^I[1163938925.296604] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_02_00_1_usbraw').
Nov 19 13:22:07 localhost kernel: [17179831.068000] ohci_hcd 0000:02:00.1: wakeup
Nov 19 13:22:07 localhost kernel: [17179831.452000] usb 6-1: new full speed USB device using ohci_hcd and address 2
Nov 19 13:22:07 localhost kernel: [17179831.664000] usb 6-1: configuration #1 chosen from 1 choice
Nov 19 13:22:07 localhost NetworkManager: <debug info>^I[1163938927.861818] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_af0_6300__Serial_Numbe').
Nov 19 13:22:07 localhost NetworkManager: <debug info>^I[1163938927.909043] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_af0_6300__Serial_Numbe_if0').
Nov 19 13:22:07 localhost NetworkManager: <debug info>^I[1163938927.968372] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_af0_6300__Serial_Numbe_if1').
Nov 19 13:22:08 localhost NetworkManager: <debug info>^I[1163938928.012860] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_af0_6300__Serial_Numbe_if2').
Nov 19 13:22:08 localhost NetworkManager: <debug info>^I[1163938928.078164] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_af0_6300__Serial_Numbe_if3').
Nov 19 13:22:08 localhost kernel: [17179832.012000] usbcore: registered new driver usbserial
Nov 19 13:22:08 localhost kernel: [17179832.012000] drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
Nov 19 13:22:08 localhost kernel: [17179832.012000] usbcore: registered new driver usbserial_generic
Nov 19 13:22:08 localhost kernel: [17179832.012000] drivers/usb/serial/usb-serial.c: USB Serial Driver core
Nov 19 13:22:08 localhost kernel: [17179832.016000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Option 3G data card
Nov 19 13:22:08 localhost kernel: [17179832.016000] option 6-1:1.0: Option 3G data card converter detected
Nov 19 13:22:08 localhost kernel: [17179832.020000] usb 6-1: Option 3G data card converter now attached to ttyUSB0
Nov 19 13:22:08 localhost kernel: [17179832.020000] option 6-1:1.1: Option 3G data card converter detected
Nov 19 13:22:08 localhost kernel: [17179832.020000] usb 6-1: Option 3G data card converter now attached to ttyUSB1
Nov 19 13:22:08 localhost kernel: [17179832.020000] option 6-1:1.2: Option 3G data card converter detected
Nov 19 13:22:08 localhost kernel: [17179832.020000] usb 6-1: Option 3G data card converter now attached to ttyUSB2
Nov 19 13:22:08 localhost kernel: [17179832.020000] option 6-1:1.3: Option 3G data card converter detected
Nov 19 13:22:08 localhost kernel: [17179832.020000] usb 6-1: Option 3G data card converter now attached to ttyUSB3
Nov 19 13:22:08 localhost kernel: [17179832.020000] usbcore: registered new driver option
Nov 19 13:22:08 localhost kernel: [17179832.020000] drivers/usb/serial/option.c: Option Card (PC-Card to) USB to Serial Driver: v0.4
Nov 19 13:22:08 localhost NetworkManager: <debug info>^I[1163938928.194435] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_af0_6300__Serial_Numbe_if2_serial_usb_2').
Nov 19 13:22:08 localhost NetworkManager: <debug info>^I[1163938928.218645] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_af0_6300__Serial_Numbe_if0_serial_usb_0').
Nov 19 13:22:08 localhost NetworkManager: <debug info>^I[1163938928.242503] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_af0_6300__Serial_Numbe_if3_serial_usb_3').
Nov 19 13:22:08 localhost NetworkManager: <debug info>^I[1163938928.281788] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_af0_6300__Serial_Numbe_usbraw').
Nov 19 13:22:08 localhost NetworkManager: <debug info>^I[1163938928.305524] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_af0_6300__Serial_Numbe_if1_serial_usb_1').
```

It seems fine, doesn't it?

But I can't connect! (Must admit that I'm a newbie on the field of dialup modems!)

The APN I've been given is "data.tre.dk", and then my PIN XXXX.

What other info is ISP specific?

I've been trying with wvdial.

I can't extract the driver-package properly - It gives me an error!, and I get this trying to compile:

```
Warning: Compiling for 2.6:
make -C /lib/modules/2.6.17-10-386/build SUBDIRS=/home/daniel/downloads/nozomi modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-386'
  CC [M]  /home/daniel/downloads/nozomi/nozomi.o
/home/daniel/downloads/nozomi/nozomi.c: In function &#8216;receive_data&#8217;:
/home/daniel/downloads/nozomi/nozomi.c:947: error: &#8216;struct tty_struct&#8217; has no member named &#8216;flip&#8217;
/home/daniel/downloads/nozomi/nozomi.c: In function &#8216;ntty_unthrottle&#8217;:
/home/daniel/downloads/nozomi/nozomi.c:1995: warning: comparison of distinct pointer types lacks a cast
/home/daniel/downloads/nozomi/nozomi.c: In function &#8216;ntty_throttle&#8217;:
/home/daniel/downloads/nozomi/nozomi.c:2008: warning: comparison of distinct pointer types lacks a cast
make[2]: *** [/home/daniel/downloads/nozomi/nozomi.o] Error 1
make[1]: *** [_module_/home/daniel/downloads/nozomi] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-386'
make: *** [default] Error 2
```

I have build-essential and kernel-headers installed! 

Any help?

---

### Post by mips on 2006-11-20
> **daller said:**
> 
I think I've fiddled a little to much, since it asks for a PUK code now :( - Any ideas?


Yes, call your service provider for the PUK code. Usually when you enter a PIN code incorrectly a few times in a row it locks up the device, in order to unlock it you need a PUK code. Called a security feature...

---

### Post by daller on 2006-11-20
> **mips said:**
> Yes, call your service provider for the PUK code. Usually when you enter a PIN code incorrectly a few times in a row it locks up the device, in order to unlock it you need a PUK code. Called a security feature...

I have the PUK code! - But how do I apply it?

---

### Post by mips on 2006-11-20
> **daller said:**
> I have the PUK code! - But how do I apply it?

Sorry, I wish I knew but I don't. Only know how to enter it into a cellphone...

---

### Post by jesnev on 2006-11-21
> **daller said:**
> I have the PUK code! - But how do I apply it?

It is easy. Put the SIM card in a cellular phone with 3G functionality. Then you can enter PUK. Use the meny in the phone. The SIM is locked and the PUK will open the SIM card. 
/jesnev

---

### Post by daller on 2006-11-21
> **jesnev said:**
> It is easy. Put the SIM card in a cellular phone with 3G functionality. Then you can enter PUK. Use the meny in the phone. The SIM is locked and the PUK will open the SIM card. 
/jesnev

Yes, I thought of that too! - But I have no 3G cellphone!

Isn't it possible through the Datacard?

---

### Post by lewiz on 2006-12-19
Hi guys.  Thanks for the useful tutorial.  I adapted this config file and a bunch of other sites to create a wvdial.conf that works with T-Mobile UK.  Here's the wvdial.conf (all of the other stuff was done as per the parent post, although I am using 2.2alpha of the driver, and comgt instead):

```
[Dialer Defaults]
Phone = *99***1#
Username = username
Password = password
Stupid Mode = 1

[Dialer tmobile]
Modem = /dev/noz0
Baud = 460800
Init1 = ATZ
#Init2 = AT_OPSYS=3,2
Init3 = AT+CGDCONT=1,"IP","general.t-mobile.uk"
```Hope this is some help :)

---

### Post by ea66 on 2007-02-22
First of all thanks man... that's really something. However a have a couple of simple [possibly 
silly questions]:
1. Will the card automatically chose the fastest connection avaliable at my current location? What I mean is will I be able to use 3G/HSPDA where avaliable or am I permanently stuck on EDGE [that's the most popular mode in poland at the moment] and will it switch between HSPDA/3G and EDGE/GPRS on the fly or do I have to disconnect and connect again by hand to switch modes?
2. Do I need to do something fancy to disconnect [how can i do it?] and remove the card or can I just unplug it and be happy?:)
3. There is a script which allows to check the apn name of my network and is shoud be in the same folder where gcom was compilated... the trouble is I installed gcom from Ubuntu repositories and I can't find this script. Any ideas where it might be?

---

### Post by amitz on 2007-03-22
> **daller said:**
> Yes, I thought of that too! - But I have no 3G cellphone!

Isn't it possible through the Datacard?

You can use your non 3G cellphone.

---

### Post by laurent on 2007-03-28
Hello,

I'm in trouble negociting the pppd on VOXmobile (Luxembourg).

I get:

pid of pppd : 7501
pppd : HX?01][06][08]
[06][08]
pppd : HX?01][06][08]
[06][08]
pppd : HX?01][06][08]
[06][08]
pppd : HX?01][06][08]
[06][08]
Disconnecting...
PPP dqemon hqs died : a modem hung up the phone (exit code = 16)

amd in the messages log:

IPCP : timeout sending Config-Requests

Anyone ?

Regards,
Laurent.

---

### Post by laurent on 2007-04-12
Hello,

i missed the APN name of my provider...and him too :-)

VoxMobile Lixembourg vox.lu

On they site but on the GRPS section.

Cheers,
Laurent.

---

### Post by michaelpo on 2007-09-18
hi..
i'm using ubuntu/linuxmint
how do i get Option Globetrotter GT 3G+ EMEA card working?
i've installed gcom..
then i run the command at terminal: gcom -d /dev/noz0...
which returns the result:

SIM ready
Waiting for Registration..(120 sec max)
Registered on Home network: "MY MAXIS",2
Signal Quality: 21,99

it seems i'm connected to the 3g...
but... how do i get ubuntu/linuxmint to connect through the 3g card?
or do i setup at the menu -> system -> network?

when i type the command gcom
or when i type the command gcom -d /dev/modem
Can't open GlobeTrotter /dev/modem.

[email]michaelpo@gmail.com[/email]

---

### Post by dinuop on 2007-11-29
how can i know what type of Kernel-Headers  required for my ubuntu

i m using amd64bit gutsy ubuntu 7.10

---

### Post by saint00 on 2008-01-06
hi,

i have followed your tutorial till ```
 sudo insmod /lib/modules/2.6.15-25-686/kernel/drivers/umts/nozomi.ko
```

an nothing was crunchy ;-)

the module is loaded ```
 nina@nina-laptop:/etc$ lsmod
Module                  Size  Used by
nozomi                 30888  0
option                 11008  0
usbserial              34920  1 option

```

but i can`t finde the devices 
there are no such things as 
/dev/noz*

Where are my devices?

please help
thanks saint00

p.s.: am using Kubuntu 7.10

---

