---
title: "Mobile Broadband doesn't working"
date: 2010-07-09
forum: Networking &amp; Wireless
---

### Post by Kognit on 2010-07-09
Hi

My friend switch to Ubuntu (he has a 9.10) and want to set up the mobile broadband. He has a usb modem stick Hyundai mb-810. We tried everything - from the usb-modeswitch to wvdial and nothing works. We have read millions of pages of tutorials and forums but still - nothing works. He is now thinking to go to Windoze XP and leaving the Linux community though he is impressed with the Ubuntu. 
Can anybody please help?

Thanks for replies!

---

### Post by pdc on 2010-07-10
plug the modem in;

open a terminal 

1) type in 

> lsusb

and tell us what you get 

2) **_copy and paste_** this command into a terminal 

> dmesg | grep tty

and copy and paste the results back here

---

### Post by Kognit on 2010-07-10
Hi

Thank you very much for responding.

Here is my lsusb:
```
Bus 002 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 1e0e:9000  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

And my dmesg | grep tty :
```
    0.001827] console [tty0] enabled
[   50.667732] usb 1-5: GSM modem (1-port) converter now attached to ttyUSB0
[   50.667799] usb 1-5: GSM modem (1-port) converter now attached to ttyUSB1
[   50.667897] usb 1-5: GSM modem (1-port) converter now attached to ttyUSB2
[  113.530903] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  113.531133] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  113.548995] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[  139.034672] usb 1-5: GSM modem (1-port) converter now attached to ttyUSB0
[  139.034936] usb 1-5: GSM modem (1-port) converter now attached to ttyUSB1
[  139.035602] usb 1-5: GSM modem (1-port) converter now attached to ttyUSB2

```

If i do sudo wvdial digi:
```
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 +FCLASS=0
ATQ0 V1 E1 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATD*99#
--> Waiting for carrier.
ATD*99***1#
ERROR
--> Invalid dial command.
--> Disconnecting at Sat Jul 10 15:58:35 2010
 
```

My wvdial.conf:
```
[Dialer Defaults]
[Dialer digi]
Init1 = ATZ
Init2 = ATQ0 V1 E1 +FCLASS=0
Modem Type = USB Modem
ISDN = 0
Phone = *99#
Modem = /dev/ttyUSB2
New PPPD = yes
Baud = 9600
Idle Seconds = 0
Auto Reconnect = 1
Auto DNS = 1
Stupid Mode = 1
Compuserve = 0
Dial Command = ATD
Ask Password = 0
FlowControl = NOFLOW
Username = user
Password = pass 
```

thank you again for reply and i really hope we will find solution :)

---

### Post by pdc on 2010-07-10
well; good news is you have an active, ready to go modem

I wonder if network manager would do all this for you:

try this post: go Half-say down the page to 

"Create a mobile broadband connection" and follow the instructions

[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

I note your wvdial says

> Invalid dial command.

I note your script does not have an IP setting for your telecom provider

eg if you wanted to dial into MObistar in Belgium

[http://modmyi.com/wiki/index.php/Carrier_APN_Settings#Mobistar](http://modmyi.com/wiki/index.php/Carrier_APN_Settings#Mobistar)

you would need to have their APN setting

> internet.be in your script 

the wvdial.conf that I use is 

> [Dialer Defaults]
Modem = /dev/ttyUSB2
Modem Type = Analog Modem
ISDN*= 0
Baud = 460800
Dial Attempts = 1
Username = user
Password = pass
Init1 = ATZ
Init2 = AT&F &D2 &C1
Init3 = ATS7=60 S30=0 S0=0
Init4 = AT+CGDCONT=1,"IP","whateveryourtelecois.com"
Phone = *99#
Stupid Mode = 1

so you could try that: and replace

> whateveryourtelecois.com

with the correct APN setting by googling on the values for your provider

---

### Post by Kognit on 2010-07-10
Hello

Thanks for reply. I changed my wvdial.conf to:

```
[Dialer defaults]
[Dialer digi]
Init1 = ATZ
Init2 = AT&F &D2 &C1
Init3 = ATS7=60 S30=0 S0=0
Init4 = AT+CGDCONT=1,"IP","internet"

Modem Type = Analog Modem
Phone = *99#
ISDN* = 0

Password = pass
New PPPD = yes
stupid Mode = 1
Username = user
Modem = /dev/ttyUSB2
Baud = 9600
```

and from the terminal i get this:
```
milan@milan-laptop:~$ sudo wvdial digi
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 +FCLASS=0
ATQ0 V1 E1 +FCLASS=0
OK
--> Modem initialized.
--> Sending: DT*99#
--> Waiting for carrier.
--> Timed out while dialing.  Trying again.
--> Sending: DT*99#
--> Waiting for carrier.
--> Timed out while dialing.  Trying again.
--> Sending: DT*99#
--> Waiting for carrier.
--> Timed out while dialing.  Trying again.
^CCaught signal 2:  Attempting to exit gracefully...
--> Disconnecting at Sun Jul 11 00:26:18 2010

```

This process was stopped by me with CTRL+C, because it doesn't end. 
I really don't know what to do since i am struggling here for a couple of days. 

On some sites i have read that i should deactivate the PIN code but i really don't know how.

I tried with the links you have posted but i am confused because i have hso module but when i do lsmod | grep hso, nothing happens.

Any other suggestions?

Thank you for your help!

---

### Post by pdc on 2010-07-10
> i should deactivate the PIN code

I have done this by taking the simcard out of a modem; putting it in a cellphone; turning off the pin code there, and then putting it back in the modem again; 

I don't think it is make or break

> Baud = 9600

but I have a much higher baud rate ...

(did you try the network manager solution I suggested?)


another suggestion:if you don't want to do the above

download sakis 3g

[http://www.sakis3g.org/](http://www.sakis3g.org/)

this is the intro page

download page gives you this

sakis 3g has good diagnostics and a good forum to diagnose

---

### Post by Kognit on 2010-07-10
Yes, i tried the network manager solution but doesn't work - mobile broadband doesn't show up.

I have changed baud, but the output is the same.

I will try your next solution. Hope it works. 

thx

---

### Post by pdc on 2010-07-10
> but i am confused because i have hso module but when i do lsmod | grep hso, nothing happens.

I don't think you need to do any of that: your device is recognised as a modem

> # Option iCON 210
# PROLiNK PHS100 (various looks)
# Hyundai Mobile MB-810
#
# One report of switching with DetachStorageOnly. Needs at least
# a second to settle before binding to usbserial
#
# Contributor: wahlm, Peter Kraker, Pakdhetimin Sekum

;DefaultVendor=  0x1e0e
;DefaultProduct= 0xf000

;TargetVendor=   0x1e0e
;TargetProduct=  0x**9000**

;MessageContent="555342431234567800000000000006bd000000020000000000000000000000"

;NeedResponse=1

the core of this is that 9000 is the TargetProduct in usb_modeswitch's file, and the device you have; has been "flipped"; and recognised now as a modem; 

You are sure there is credit on it; which country are you? which provider?

---

### Post by Kognit on 2010-07-10
YEAHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHH

With your excellent help it works now. I downloaded the script and works perfectly.

THAAAAAAAAAAAAAANKS.

I should buy you a beer.

I am from Slovenia. Thank you again. Really. You can't imagine how much time i put on it. 

thanks again and have a great day :)

Bye

:)

---

### Post by pdc on 2010-07-10
great work! well done; enjoy

sakis is a bit to the south-east of you in Greece, and he will be delighted with your success

best wishes

If I get to Slovenia some day, I will take you up on our offer of a beer!

---

### Post by gape on 2011-02-17
i got it to work too
:P

where do i post a litle error in netvork connections
mobile broadband
?
all is gr8 and works out of the box, but 
APN addres : internet

(ubuntu thinks its still internetpro
infact probably it is - with postpaid ... but mostly we use prepaid - wich is not an option to chooze from (and internetpro needs to be changed to internet))

---

### Post by greasesicle on 2011-02-21
Hello this is what I get for 
    
 			  	 	 	 	 		 		 			 			 				 				**Re: Mobile Broadband doesn't working** 			
 			 			 		   		 		 		Hi

Thank you very much for responding.

Here is my lsusb:
 	Code:
 	Bus 002 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 1e0e:9000  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
And my dmesg | grep tty :
 	Code:
 	    0.001827] console [tty0] enabled
[   50.667732] usb 1-5: GSM modem (1-port) converter now attached to ttyUSB0
[   50.667799] usb 1-5: GSM modem (1-port) converter now attached to ttyUSB1
[   50.667897] usb 1-5: GSM modem (1-port) converter now attached to ttyUSB2
[  113.530903] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  113.531133] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  113.548995] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[  139.034672] usb 1-5: GSM modem (1-port) converter now attached to ttyUSB0
[  139.034936] usb 1-5: GSM modem (1-port) converter now attached to ttyUSB1
[  139.035602] usb 1-5: GSM modem (1-port) converter now attached to ttyUSB2 
If i do sudo wvdial digi
I get nothing.

I have the AT&T USB Velocity data card.  My version of Ubuntu is 
Distributor ID:    Ubuntu
Description:    Ubuntu 10.10
Release:    10.10
Codename:    maverick

What should I do if I don't get a response to sudo wvdial digi?

---

### Post by Kognit on 2011-02-21
I don't know a lot about broadband devices but sakis script works perfectly. If you want to download it:

[sakis3g]("http://www.sakis3g.org/")

Follow the instructions from sakis website and everything should be fine.

---

