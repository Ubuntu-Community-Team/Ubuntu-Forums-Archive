---
title: "USB Internet Key X225S (1bbb:f000, 1bbb:0017) on Ubuntu 10.04"
date: 2010-09-18
forum: Networking &amp; Wireless
---

### Post by nicolaasuni on 2010-09-18
Author:* Nicola Asuni ([http://nicolaasuni.tecnick.com](http://nicolaasuni.tecnick.com)).*

This guide covers the installation of the Internet USB modem key identified as "TCT Mobile Limited One Touch X225S-2CWNIT1" (1bbb:f000, 1bbb:0017) on Ubuntu Linux 10.04 Lucid Lynx Desktop AMD64 (2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64 GNU/Linux).

This guide can be also used to install similar flip-flop USB devices but you have to change the codes to fit your situation.

First remove the PIN from your SIM card using a mobile phone.

Insert the usb key on your computer, wait few seconds and from terminal (Applications > Accessories > Terminal) type:

```

lsusb

```On the list of devices you should read:

```

...
Bus 001 Device 004: ID 1bbb:f000 T & A Mobile Phones
...

```The 1bbb:f000 is the code for memory device mode, we need to switch to modem mode (1bbb:0017).

Disconnect the key.

Dowload the latest usb-modeswitch and relative data from [http://www.draisberghof.de/usb_modeswitch](http://www.draisberghof.de/usb_modeswitch)

For Ubuntu 10.04 you can use the precompiled Debian packages at:
[http://packages.debian.org/squeeze/usb-modeswitch](http://packages.debian.org/squeeze/usb-modeswitch)
[http://packages.debian.org/squeeze/usb-modeswitch-data](http://packages.debian.org/squeeze/usb-modeswitch-data)
download the deb files for your computer architecture.
Open Terminal, move to the download folder and install the deb packages:

```

cd /path/to/download
sudo dpkg -i usb-modeswitch_*
sudo dpkg -i usb-modeswitch-data*

```Install wvdial, modemmanager and all dependencies from default repositories:

```

sudo aptitude install wvdial modemmanager

```Create a usb-modeswitch configuration file for your usb key to switch from memory mode (1bbb:f000) to modem mode (1bbb:0017):

```

sudo gedit /etc/usb-modeswitch-x225s.conf

```Paste the following code, save and close gedit:

```

# Alcatel X225S

DefaultVendor=  0x1bbb
DefaultProduct= 0xf000

TargetVendor=   0x1bbb
TargetProduct=  0x0017

MessageContent="55534243123456788000000080000606f50402527000000000000000000000"

```Create the rules to automatically switch from memory mode (1bbb:f000) to modem mode (1bbb:0017) and load drivers:

```

sudo gedit /etc/udev/rules.d/50-x225s.rules

```Paste the following code, save and close gedit:

```

SUBSYSTEM=="usb", SYSFS{idVendor}=="1bbb", SYSFS{idProduct}=="f000", RUN+="/usr/sbin/usb_modeswitch -c /etc/usb-modeswitch-x225s.conf"
SUBSYSTEM=="usb", SYSFS{idVendor}=="1bbb", SYSFS{idProduct}=="0017", RUN+="/sbin/modprobe usbserial vendor=0x1bbb product=0x0017"

```Unfortunately the Ubuntu Network Manager seems not enough stable to use this modem, so we use a wvdial script to connect.

Create a wvdial configuration script:

```

sudo gedit /etc/wvdial.conf

```Paste the following code, save and close gedit:

```

[Dialer Defaults]
Modem = /dev/ttyUSB4
ISDN = 0
Modem Type = Analog Modem
Baud = 460800
Init1 = ATX3
Init2 = AT&F Q0 V1 E0 S0=0 &C1 &D2 +FCLASS=0
Init3 = at+cgdcont=1,"IP","internet.wind"
Phone = *99#
Dial Attempts = 5
Stupid Mode = on
Dial Command = ATDT
Idle Seconds = 7200
Ask Passwords = 0
Password = "Wind"
Username = "Wind"
Carrier Check = on
New PPPD = 1
Auto DNS = on

```The Modem port may be different on your system.
The Init3, Username and Password must be changed to fit your ISP (This example is for Italian Wind Operator).

Restart the computer.
Attach the USB key, wait few seconds and check the key mode using lsusb:

```

lsusb

```Now you should read:

```

...
Bus 002 Device 007: ID 1bbb:0017 T & A Mobile Phones
...

```The usb key is successfully switched to modem mode (1bbb:0017).

To connect to the Internet you can now type on terminal:

```

sudo wvdial

```When the connection is estabilished the ligh on the key turns to fixed green.
Keep this window open to keep the internet connection opened.
To close the internet connection, select the terminal window where wvdial is running and press CTRL-C buttons on keyboard. If the modem light stay fixed green, then you have to remove the usb key to close the connection.

You can also create a launcher on the desktop to automatically invoke the wvdial command:
Click on the Desktop with the right mouse button and choose "Create Launcher...", choose a name and set the following command:

```

gksudo wvdial

```Note: Be sure that the "File > Work Offline" option on Mozilla Firefox is unchecked.

---

### Post by andreh8 on 2011-04-07
Thanks for sharing this article ! It was very useful for me.

Your instructions worked for me as well for a modem which I bought
as 'Alcatel OTX-220' (but which has the same VIDs/PIDs in disk
as well as in modem mode). On a label close to the sim card
slot I can read 'TCT Mobile X220L'.

I noticed that on 10.04.2 LTS, the packages usb-modeswitch and
usb-modeswitch-data were already known to apt-cache so I could
just install them using 


```

apt-get install usb-modeswitch
apt-get install usb-modeswitch-data

```

(no need to download from the Debian repository)

I also commented out the init3 line (which seems to be specific
to your internet provider).

I could disable the PIN using the Windows tool which came on the 
storage space on the modem (i.e. no need to insert it into
a mobile phone to do that).

---

### Post by jerkam on 2011-05-28
hi,
i live in France and i bought an usb key 3G alcatel X220L (chez Bouygues Telecom). This tutorial is very good...

Merci Beaucoup!!
Grazie mille!!
thanks a lot!!

---

