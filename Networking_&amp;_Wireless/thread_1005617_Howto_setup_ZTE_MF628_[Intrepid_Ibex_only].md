---
title: "Howto setup ZTE MF628 [Intrepid Ibex only]"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by damienduff on 2008-12-08
Hi everyone, this is how I setup ZTE MF628 for 8.10.
Unfortunately, the same instructions dun work for 8.04 (at least not for me).

1. Get usb_modeswitch from [here]("http://www.draisberghof.de/usb_modeswitch/#download"). I must clarify I am using usb_modeswitch-0.9.5.tar.bz2, not the deb.

2. Untar and copy binary to /usr/sbin/
```

tar xjf usb_modeswitch-0.9.5.tar.bz2
cd usb_modeswitch-0.9.5/
sudo cp usb_modeswitch /usr/sbin/

```

I think this library is needed by usb_modeswitch
```

sudo apt-get install libusb-dev

```

3. Setup usb_modeswitch.conf
This is how my /etc/usb_modeswitch.conf looks like,
```

########################################################
# ZTE MF628
#
# Captured with "usbmon". Has a micro SD slot which can be
# activated alternatively
#
# Contributor: Alvaro Lopes <alvieboy at alvie dot com>

DefaultVendor=  0x19d2
DefaultProduct= 0x2000

# To modem mode:

TargetVendor=   0x19d2
TargetProduct=  0x0015

MessageEndpoint=0x08
MessageContent="5553424312345678000000000000061b000000030000000000000000000000"

```

4. Setup udev rules
sudo vi /etc/udev/rules.d/65-zte-mf628-modem.rules

This is how mine looks like,
```

SUBSYSTEM=="usb", ATTR{idVendor}=="19d2", ATTR{idProduct}=="2000", RUN+="/usr/sbin/usb_modeswitch"

```

5. As normal user, type "wvdialconf"
You will see something like this. The values are needed for Step 6.

```

ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB0<*1>: Modem Identifier: ATI -- Manufacturer: ZTE INCORPORATED
ttyUSB0<*1>: Speed 9600: AT -- OK
ttyUSB0<*1>: Max speed is 9600; that should be safe.

```

6. Next, modify /etc/wvdial.conf
(create the file if it dun exists).

sudo vi /etc/wvdial.conf
```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","<put ur APN here>"
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Modem = /dev/ttyUSB0
Baud = 9600
Phone = <value here depends on ISP>
Username = <value here depends on ISP>
Password = <value here depends on ISP>
Stupid Mode = yes

```

7. Finally, to connect
```

sudo wvdial

```

---

### Post by damienduff on 2008-12-08
For the benefit of StarHub users in Singapore.
My actual wvdial.conf is

```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","shinternet"
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Modem = /dev/ttyUSB0
Baud = 9600
Phone = *99#
Username = x
Password = x
Stupid Mode = yes

```

Note that, there is no authentication. Therefore the values for Username and Password is not important. But they cannot be blank, please use dummy values.

---

### Post by STrRedWolf on 2008-12-09
So NetworkManager uses wvdial?  Intresting.

---

