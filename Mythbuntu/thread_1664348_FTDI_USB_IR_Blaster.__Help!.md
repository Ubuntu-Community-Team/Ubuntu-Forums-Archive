---
title: "FTDI USB IR Blaster.  Help!"
date: 2011-01-10
forum: Mythbuntu
---

### Post by zepfan on 2011-01-10
I just bought this Blaster to change my STB. I can't seem to get it to work! It says it works with lirc, the install guides that I can find are all fedora specific, and I can't seem to get them to work without screwing up my lirc and reinstalling. Anyone get this model working? I'd appreciate any advice.

Here's a link to the page. [http://www.irblaster.info/usb_blaster.html](http://www.irblaster.info/usb_blaster.html)

---

### Post by zepfan on 2011-01-10
```

[   12.721008] usbcore: registered new interface driver usbserial_generic
[   12.721008] usbserial: USB Serial Driver core
[   12.827572] USB Serial support registered for FTDI USB Serial Device
[   12.827620] ftdi_sio 3-3:1.0: FTDI USB Serial Device converter detected
[   12.827668] usb 3-3: Detected FT232RL
[   12.827670] usb 3-3: Number of endpoints 2
[   12.827673] usb 3-3: Endpoint 1 MaxPacketSize 64
[   12.827674] usb 3-3: Endpoint 2 MaxPacketSize 64
[   12.827676] usb 3-3: Setting MaxPacketSize 64
[   12.829721] usb 3-3: FTDI USB Serial Device converter now attached to ttyUSB0
[   12.829736] usbcore: registered new interface driver ftdi_sio
[   12.829738] ftdi_sio: v1.6.0:USB FTDI Serial Converters Driver

```

My Lirc conf
```


#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the Windows Media Center Transceivers/Remotes (all) remote:
include "/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb"

#Configuration for the Serial Port (UART) : Scientific Atlanta Cable box transmitter:
include "/usr/share/lirc/extras/transmitters/scientificatlanta/general.conf"

```

My hardware conf
```


# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Serial Port (UART) : Scientific Atlanta Cable box"
TRANSMITTER_MODULES="lirc_dev lirc_serial"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc1"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="scientificatlanta/general.conf"
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

```

When I run the Sendonce command it says it ran, but no light, and no channel change on the STB.  Should it be /dev/ttyUSB0 instead? I tried that and it said it couldn't access the socket. Any tips?

---

### Post by zepfan on 2011-01-11
Can any one offer advice? TTYUSB0 doesn't work.

---

### Post by larsolav on 2011-01-12
> #Chosen IR Transmitter
TRANSMITTER="**Serial Port (UART)** : Scientific Atlanta Cable box"
TRANSMITTER_MODULES="lirc_dev **lirc_serial**"
I think you may have set up the wrong blaster. The one in the link in your first post is a USB blaster, right? And from the quote above it looks like you set up a serial port blaster. I think you should go to the Mythbuntu Control Center (MCC) and see if under IR tab it lists a USB blaster for the Scientific Atlanta Cable box...

EDIT:
I see also on the website you link to: "LIRC under linux now has support for these cables. You must compile from source to use these cables." I have no idea how you do that, or if that can be set up in MCC... Anyone else know?

---

### Post by zepfan on 2011-01-12
> **larsolav said:**
> I think you may have set up the wrong blaster. The one in the link in your first post is a USB blaster, right? And from the quote above it looks like you set up a serial port blaster. I think you should go to the Mythbuntu Control Center (MCC) and see if under IR tab it lists a USB blaster for the Scientific Atlanta Cable box...

EDIT:
I see also on the website you link to: "LIRC under linux now has support for these cables. You must compile from source to use these cables." I have no idea how you do that, or if that can be set up in MCC... Anyone else know?
I tried the MCC route, none of them work. I was assuming since it listed as USB/Serial, that UART would work. Anyone have any advice as to compiling from source? I can't find a good ubuntu guide.

---

### Post by zepfan on 2011-01-13
Does anyone have this Blaster/Transmitter?

---

### Post by gratzimilian on 2011-02-05
> **zepfan said:**
> Does anyone have this Blaster/Transmitter?

I have..

Compiled lirc from source (as I had been told the package in 10.10 didn't support this device). Instructions are available from Albert Huitsing's page: [http://www.huitsing.nl/irftdi/](http://www.huitsing.nl/irftdi/)

The transmitter portion of my hardware.conf looked like this:

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER="ftdi"
TRANSMITTER_DEVICE="/dev/ttyUSB0"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS="-d /dev/ttyUSB0"

Used irsend to test which worked for this specific TV (but other devices I have had problems with):

sudo irsend SEND_ONCE Samsung_BN59-00609A MENU

Hope this helps

---

