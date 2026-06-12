---
title: "Dell 5720 3G Verizon modem No Carrier errors (Lucid 10.04 x86)"
date: 2012-03-15
forum: Networking &amp; Wireless
---

### Post by jl3128 on 2012-03-15
Hello All,

I am having a difficult time trying to get my 3G modem working.  It's a Verizon Dell 5720 which according to [https://wiki.ubuntu.com/NetworkManager/Hardware/3G](https://wiki.ubuntu.com/NetworkManager/Hardware/3G) is supposed to work out of the box.  I stopped trying to use Network-Manager, and just want to get it going with wvdial.  

When I run wvdial I get the following (the last part repeats over and over until I ctrl+C:

```

--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATX3
ATX3
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L3DT#777
--> Waiting for carrier.
ATM1L3DT#777
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATM1L3DT#777
--> Waiting for carrier.
ATM1L3DT#777
NO CARRIER

```Here is the latest iteration of my wvdial.conf:

```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Password = vzw
Ask Password = off
Phone = #777
Modem Type = Analog Modem
Stupid Mode = on
Baud = 9600
Dial Command = ATM1L3DT
Modem = /dev/ttyUSB0
Init = ATX3
ISDN = 0
Username = <mynumber>@vzw3g.com
Carrier Check = no

```lsusb -v: 

```

Bus 004 Device 003: ID 413c:8133 Dell Computer Corp. Wireless 5720 VZW Mobile Broadband (EVDO Rev-A) Minicard GPS Port
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x413c Dell Computer Corp.
  idProduct          0x8133 Wireless 5720 VZW Mobile Broadband (EVDO Rev-A) Minicard GPS Port
  bcdDevice            0.00
  iManufacturer           1 Novatel Wireless Inc.
  iProduct                2 Novatel Wireless CDMA
  iSerial                 0 
  bNumConfigurations      1
<snip>


```from dmesg:

```

[    0.000000] console [tty0] enabled
[   13.886719] USB Serial support registered for GSM modem (1-port)
[   13.886901] option 4-1:1.0: GSM modem (1-port) converter detected
[   13.887143] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[   13.887202] option 4-1:1.1: GSM modem (1-port) converter detected
[   13.887403] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[   13.887461] option: v0.7.2:USB Driver for GSM modems

```

I have spent the past week googling, and reading posts, however, I just can't get it to work.  I can't seem to find the magic set of configuration parameters (probably because I don't know what is actually wrong) I have tried many different settings in wvdial.conf, without success.  

Any help or suggestions would be *greatly* appreciated.

Thank you!

---

