---
title: "HOW TO install the Aiko 83D/ZTE 626 modem to Ubuntu and dial with wvdial"
date: 2009-12-27
forum: Networking &amp; Wireless
---

### Post by cirobr on 2009-12-27
This HOW TO aims to help connecting the Aiko 83D modem (a.k.a. ZTE MF626) on Ubuntu for usage with operator Vivo (Brazil). Tested version: Ubuntu Desktop Karmic.

Note: At the appropriate stages of this article, specific reference to the operator Vivo is done so that the reader is able to adapt this solution to his/her needs.

To start, install usb-modeswitch so that the modem is not recognized as an USB storage device when plugged to the USB port:

```
sudo apt-get install usb-modeswitch
```

Next, configure usb-modeswitch. First, edit the ZTE MF626 configuration on the file usb_modeswitch.conf  to reflect the needed changes for the operator Vivo (TargetProduct):

```
sudo gedit /etc/usb_modeswitch.conf
```

```
########################################################

# ZTE MF628+ (tested version from Telia / Sweden)
# ZTE MF626
# ZTE MF636 (aka "Telstra / BigPond 7.2 Mobile Card")
#
# Contributor: Joakim Wennergren


DefaultVendor=  0x19d2
DefaultProduct= 0x2000

TargetVendor=   0x19d2
TargetProduct=  0x0057

# only for reference
MessageEndpoint=0x01

MessageContent="55534243123456782000000080000c85010101180101010101000000000000"

# if that command doesn't work, try the other ("eject")
;MessageContent="5553424312345678000000000000061b000000030000000000000000000000"

```

Second, create a file with the below code. Again, note the code &#8220;0x0057&#8221;, which is a match for Vivo.

```
Sudo gedit /usr/share/hal/fdi/information/20thirdparty/20-zte-mf626.fdi
```

```
<!-- -*- SGML -*- -->
<deviceinfo version="0.2">
<device>
<!-- ZTE MF626 HSDPA USB Modem -->
<match key="@info.parent:usb.vendor_id" int="0x19d2">
<match key="@info.parent:usb.product_id" int="0x0057">
<match key="@info.parent:usb.interface.number" int="3">
<append key="modem.command_sets" type="strlist">GSM-07.07</append>
<append key="modem.command_sets" type="strlist">GSM-07.05</append>
<append key="info.capabilities" type="strlist">modem</append>
</match>
</match>
</match>
</device>
</deviceinfo>
```

Lastly, create rules for the computer to automatically switch on the modem when it is connected to an USB port. Note that this code is independent to the chosen operator: 

```
sudo gedit /etc/udev/rules.d/90-zte.rules
```

```
ACTION!="add", GOTO="ZTE_End"

SUBSYSTEM=="usb", SYSFS{idProduct}=="2000", SYSFS{idVendor}=="19d2", GOTO="ZTE_ZeroCD"

LABEL="ZTE_ZeroCD"
RUN+="/usr/sbin/usb_modeswitch -W -c /etc/usb_modeswitch.conf"

LABEL="ZTE_End"
```

Now that usb-modeswitch is installed, it is time to install and configure wvdial:

```
sudo apt-get install wvdial
```

Next, edit wvdial.conf to create the specific dial-in for the modem:

```
sudo gedit /etc/wvdial.conf
```

```
[Dialer 3g]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Modem = /dev/ttyUSB2
Baud = 921600
DialCommand = ATDT
Check Def Route = on
FlowControl = Hardware(CRTSCTS)
Username = vivo
Password = vivo
Phone = *99#
Stupid mode = 1
Auto Reconnect = on
Auto DNS = on
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2
Init3 = AT+CGDCONT=1,"IP","zap.vivo.com.br"
```

Then, set pppd with the appropriate permissions:

```
chmod +s /usr/sbin/pppd
```

Now, it is advisable to restart the computer and log back in. Then, plug the modem and wait for a few seconds. Its led will firstly turn red, then either green (3G network) or blue (2.5G network), indicating the modem has found the network and it is ready for dialing:

```
wvdial 3g
```

The green/blue led will blink on/off, indicating that the connection is established.

Note: to avoid execution errors when running wvdial, it is advisable to check the following:

- Make sure your user is part of the group &#8220;dip&#8221;.
- Set up appropriate permissions for pppd, as above.

References:

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)
[http://ubuntuforums.org/showthread.php?t=1005910](http://ubuntuforums.org/showthread.php?t=1005910)
[http://ubuntuforums.org/showthread.php?t=1202430&highlight=zte](http://ubuntuforums.org/showthread.php?t=1202430&highlight=zte)
[http://ubuntuforums.org/showthread.php?t=1147685](http://ubuntuforums.org/showthread.php?t=1147685)
[http://www.guiadohardware.net/tutoriais/3g-linux/](http://www.guiadohardware.net/tutoriais/3g-linux/)
[http://ubuntuforums.org/archive/index.php/t-1035950.html](http://ubuntuforums.org/archive/index.php/t-1035950.html)

---

### Post by Leoncio on 2010-01-02
God bless you, man!  I've been trying to connect my brother's and aunt's 3G for AGES (really, it's been almost a year) and after almost a dozen tries it was starting to get really frustrating.  Cheers!

---

