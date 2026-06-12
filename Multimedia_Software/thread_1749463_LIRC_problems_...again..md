---
title: "LIRC problems ...again."
date: 2011-05-04
forum: Multimedia Software
---

### Post by drpepper on 2011-05-04
Hey guys,

I'm close to giving up with LIRC, after many years of development, basic issues have not been ironed out (had the same issue 4 years ago using LIRC with a university project)

I installed LIRC to use with XBMC. It was working fine until I rebooted. I'm aware of the problem with the events, so I reconfigured lirc with dpkg-reconfigure but this hasn't worked. Even irw inst receiving any events now.

cat /proc/bus/input/devices shows the following.

```
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input2
U: Uniq=
H: Handlers=sysrq kbd event2 
B: PROP=0
B: EV=120013
B: KEY=4 2000000 3803078 f800d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Generic Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input5
U: Uniq=
H: Handlers=mouse1 event5 
B: PROP=0
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0003 Vendor=2040 Product=9950 Version=0100
N: Name="IR-receiver inside an USB DVB receiver"
P: Phys=usb-0000:09:06.2-1/ir0
S: Sysfs=/devices/pci0000:00/0000:00:10.0/0000:09:06.2/usb2/2-1/rc/rc0/input6
U: Uniq=
H: Handlers=kbd event6 
B: PROP=0
B: EV=100013
B: KEY=14afc336 284284d 0 0 0 4 80058000 2190 40000801 9e96c0 0 900200 ffc
B: MSC=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA NVidia Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:10.1/sound/card0/input7
U: Uniq=
H: Handlers=event7 
B: PROP=0
B: EV=21
B: SW=4

I: Bus=0003 Vendor=046d Product=c312 Version=0110
N: Name="LITEON Technology USB Multimedia Keyboard"
P: Phys=usb-0000:00:0b.0-8/input0
S: Sysfs=/devices/pci0000:00/0000:00:0b.0/usb3/3-8/3-8:1.0/input/input8
U: Uniq=
H: Handlers=sysrq kbd event3 
B: PROP=0
B: EV=120013
B: KEY=10000 7 ff9f207a c14057ff febeffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=093a Product=2510 Version=0111
N: Name="PIXART USB OPTICAL MOUSE"
P: Phys=usb-0000:00:0b.0-7/input0
S: Sysfs=/devices/pci0000:00/0000:00:0b.0/usb3/3-7/3-7:1.0/input/input9
U: Uniq=
H: Handlers=mouse0 event4 
B: PROP=0
B: EV=17
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103
B: MSC=10
```When it was working there was another IR device, other than "IR-receiver inside an USB DVB receiver" unfortunately I can not remember what it was named. My hardware.conf reflects the correct device i think.

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge Nova-T 500"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/by-path/pci-0000:09:06.2-event-ir"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge_novat500"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD=true

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

# Remote settings required by gnome-lirc-properties
REMOTE_MODEL="NOVA-T500"
REMOTE_VENDOR="Hauppauge"
```Not sure where to go from here, any help would be greatly appreciated :)

/cheers

---

### Post by andrewc6l on 2011-05-04
Not sure if this is the same problem. If LIRC dies after rebooting but can be restarted with the init script, try something like this:

[http://ubuntuforums.org/archive/index.php/t-1123639.html](http://ubuntuforums.org/archive/index.php/t-1123639.html)

---

