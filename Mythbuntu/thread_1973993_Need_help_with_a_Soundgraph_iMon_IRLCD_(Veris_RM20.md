---
title: "Need help with a Soundgraph iMon IR/LCD (Veris RM200 remote control and LCD display)"
date: 2012-05-05
forum: Mythbuntu
---

### Post by samihs72 on 2012-05-05
Hi!

Does anyone have Soundgraph iMon IR/LCD (Veris RM200 remote control and LCD display in computer case) lsusb=15c2:0038 and got it working with Mythbuntu 12.04?

This has been most difficult issue in Mythbuntu version upgrades in my history...

I would be appreciated of your help.

---

### Post by tgm4883 on 2012-05-05
Please don't add random issues onto another thread. Instead, open your own. :P

---

### Post by samihs72 on 2012-05-05
> **tgm4883 said:**
> Please don't add random issues onto another thread. Instead, open your own. :P
Ok, sorry... I thought, this would be relevant issue with Mythbuntu 10.04 --> 12.04 upgrade.

So, does anyone have Soundgraph iMon IR/LCD and used them with latest Mythbuntu 12.04? What kind of challenges you have had with them or do they work out-of-box, when configure lirc and choose "iMon Antec Veris" device during configuration?

Thanks in advance.

---

### Post by fatmonk on 2012-05-11
Not the best news I'm afraid, but early days...

It seems the LCD/VFD doesn't work 'out of the box' on 12.04. At least mine hasn't.

I've gone through the usual process of selecting various Soundgraph models and have activated LCD in frontent setting but not getting anything on the front display, and no remote response either.

I've also tried my Hauppage nova-t 500 remote and sensor and got no remote response.

Early days yet, I'll play some more and will post back results.

If anyone has any suggestions in the meantime that would be much appreciated.

-FM

---

### Post by fatmonk on 2012-05-22
Update...

It was my RM200 that was dead. Leaky batteries, but I've managed to repair it an dthe good news is that out of the box I can drive Mythbuntu 12.04.

At the moment I believe I have the wrong remote type selected as not all keys work, but it works in mouse mode and keyboard mode and the left and right mouse, enter and esc keys al work as well.

So I currently have basic Myth functionality without even trying - now I need to find a little bit of time to go through the setup to get it all working. With no effect I'm already a lot further on than I even got with 8.10.

Still nothing from the display on the front of the box though.. that needs more investgation - I'll update as I work things out.

-FM

---

### Post by Lester_Burnham on 2012-05-22
Hi,

Use irw in a terminal and press a few buttons on the remote. Match those names you see to the names in ~/.lirc/mythtv

I know with the mce remote some button names changed.

With the imon display. It used to use LCDproc, but I don't know if that has changed. Then you hads to edit /etc/LCDd.conf and use imon as the driver. I know in Mythbuntu 10.04, I had to add an options file with display=1 I think.

Lester

---

### Post by fatmonk on 2012-05-25
That was the clue I needed... lcdproc isn't installed by default in the Mythbuntu distro (I'd assumed it was seeing as the options are there to enable output to an LCD in Myth setup).

Anyway,

```
sudo apt-get-install lcdproc
```

and then editting LCDd.conf and lcdproc.conf got the LCD up and running for me.

Now I just need to tweak the options and do my IR setup properly and all is good.

(Sadly, before that I intend to do a full reinstall as I just realised that may hardware actually IS 64bit - I bought it 4 years ago so just kind of assumed I'd only bought a 32bit proc.. doh!)

So in short, it looks like 12.04 supports the Soundgraph iMon IR/LCD with RM200. Not quite out of the box, but most of it's there and no compiling is required - just the install of lcdproc, tweaking those config file smanually and doing the right bits in Myth setup.

-FM


-FM

---

### Post by roundhay on 2012-07-15
I have recently upgraded to Mythbuntu 12.04 from 9.04. I pretty much have everythign set up and working with the exception of the imon display that came with the Silerstone case.

I have spent most of today trying to find how-to's or threads which might help but I've not found anything that works.

I have the 15c2:ffdc Imon unit which I assume is the LCD not the VFD.

I am not using the imon unit for the IR control I am using a XT MCE remote and have this set up and working using it's own USB adapter. 

I have pasted the output of several commands below in case they can help someone to point me in the right direction.

lsusb:
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 003 Device 002: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
Bus 006 Device 002: ID 0471:0815 Philips (or NXP) eHome Infrared Receiver
Bus 008 Device 002: ID 413c:3016 Dell Computer Corp. Optical 5-Button Wheel Mouse
Bus 008 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard
```

dmesg | grep imon
```
[   18.484152] imon 3-1:1.0: Unknown 0xffdc device, defaulting to VFD and iMON IR (id 0x96)
[   18.547696] Registered IR keymap rc-imon-pad
[   18.556222] imon 3-1:1.0: iMON device (15c2:ffdc, intf0) on usb<3:2> initialized
[   18.556258] usbcore: registered new interface driver imon
[   18.964170] imon 3-1:1.0: Unsupported IR protocol specified, overriding to iMON IR protocol
[   18.978530] imon 3-1:1.0: Looks like you're trying to use an IR protocol this device does not support
[   18.978533] imon 3-1:1.0: Unsupported IR protocol specified, overriding to iMON IR protocol
[   19.908052] imon 3-1:1.0: Unsupported IR protocol specified, overriding to iMON IR protocol
[   19.923074] imon 3-1:1.0: Looks like you're trying to use an IR protocol this device does not support
[   19.923077] imon 3-1:1.0: Unsupported IR protocol specified, overriding to iMON IR protocol
[   21.126856] imon 3-1:1.0: Looks like you're trying to use an IR protocol this device does not support
[   21.126859] imon 3-1:1.0: Unsupported IR protocol specified, overriding to iMON IR protocol
```

cat /proc/bus/input/devices
```
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0003 Vendor=15c2 Product=ffdc Version=0000
N: Name="iMON Panel, Knob and Mouse(15c2:ffdc)"
P: Phys=usb-0000:00:1a.0-1/input1
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input2
U: Uniq=
H: Handlers=kbd mouse0 event2 
B: PROP=0
B: EV=100007
B: KEY=10800320 200000200000000 30000 400110000 411000000801 e168000000000 10000002
B: REL=103

I: Bus=0003 Vendor=15c2 Product=ffdc Version=0000
N: Name="iMON Remote (15c2:ffdc)"
P: Phys=usb-0000:00:1a.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/rc/rc0/input3
U: Uniq=
H: Handlers=kbd event3 
B: PROP=0
B: EV=100013
B: KEY=fff 0 4400000108c0320 2d5008000000000 30000 400119000 418614000801 809e168000000000 200000010004002
B: MSC=10

I: Bus=0003 Vendor=413c Product=3016 Version=0111
N: Name="Dell Premium USB Optical Mouse"
P: Phys=usb-0000:00:1d.2-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.0/input/input4
U: Uniq=
H: Handlers=mouse1 event4 
B: PROP=0
B: EV=17
B: KEY=31f0000 0 0 0 0
B: REL=143
B: MSC=10

I: Bus=0003 Vendor=0471 Product=0815 Version=0000
N: Name="Media Center Ed. eHome Infrared Remote Transceiver (0471:0815)"
P: Phys=usb-0000:00:1d.1-2
S: Sysfs=/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.0/rc/rc1/input5
U: Uniq=
H: Handlers=kbd event5 
B: PROP=0
B: EV=100013
B: KEY=fff 0 200108fc32e 237605100000000 0 700158000 419200004001 8e968000000000 10000000
B: MSC=10

I: Bus=0003 Vendor=413c Product=2003 Version=0110
N: Name="Dell Dell USB Keyboard"
P: Phys=usb-0000:00:1d.2-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.0/input/input6
U: Uniq=
H: Handlers=sysrq kbd event6 
B: PROP=0
B: EV=120013
B: KEY=1000000000007 ff9f207ac14057ff febeffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="MCE IR Keyboard/Mouse (mceusb)"
P: Phys=/input0
S: Sysfs=/devices/virtual/input/input7
U: Uniq=
H: Handlers=sysrq kbd mouse2 event7 
B: PROP=0
B: EV=100017
B: KEY=30000 7 ff87207ac14057ff febeffdfffefffff fffffffffffffffe
B: REL=3
B: MSC=10

I: Bus=0001 Vendor=6981 Product=8888 Version=0001
N: Name="cx23885 IR (TurboSight TBS 6981)"
P: Phys=pci-0000:04:00.0/ir0
S: Sysfs=/devices/pci0000:00/0000:00:1c.3/0000:04:00.0/rc/rc2/input8
U: Uniq=
H: Handlers=kbd event8 
B: PROP=0
B: EV=100013
B: KEY=c00 0 3000000108c0000 234301100000000 0 118000 418000000801 8e968000000000 ffc
B: MSC=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="MCE IR Keyboard/Mouse (cx23885)"
P: Phys=/input0
S: Sysfs=/devices/virtual/input/input9
U: Uniq=
H: Handlers=sysrq kbd mouse3 event9 
B: PROP=0
B: EV=100017
B: KEY=30000 7 ff87207ac14057ff febeffdfffefffff fffffffffffffffe
B: REL=3
B: MSC=10
```

sudo modprobe lirc_imon
```
FATAL: Error inserting lirc_imon (/lib/modules/3.2.0-26-generic/kernel/drivers/staging/media/lirc/lirc_imon.ko): Invalid argument
```

I have a feeling the driver is no loading correctly but I have no idea why.

---

### Post by jwhiteIT on 2012-07-16
Hi Guys,

Quite a confusing post.  There is a big difference between IMon LCD and VFD and how they work.  I'm still not 100% sure what each of you have, however Roundhay - 15c2:ffdc is the LCD VFD, selecting the Soundgraph iMon/VFD PAD will make it work out of the box (no config required)

fatmonk - I have the same issue with the remote where only some keys appear.  If you got this to work I was wondering if you could let me know how.  I have started new thred for it:
[http://ubuntuforums.org/showthread.php?t=2026951](http://ubuntuforums.org/showthread.php?t=2026951)

---

### Post by Lester_Burnham on 2012-07-17
Hi,

I have the 15c2:ffdc which is a VFD in a Thermaltake Bach case.
LCD is liquid crystal display, VFD is vacuum fluorescent display.

Maybe you missed the a slash between them when explaining above.
I have no interest in messing with the imon, when I can plug in an mce remote.

Lester

---

### Post by pinakibag on 2012-11-26
I have the same piece 15c2:0038 I tried changing LCDd.conf and lcdproc.conf but when I run lcdproc nothing happens on the LCD nor any error in the screen. Can you please tell me what exactly you changed in LCDd.conf & lcdproc.conf

---

### Post by BicyclerBoy on 2012-11-26
Did you set the imon protocol to 1 (1=15c2:0038 device) ?

In the old days the usbhid  driver would claim the imon devices..
Could look in dmesg or hwinfo
Search for the 15c2:0038 device & look for the driver listed..

The above usbhid problem is worked around with a entry in /etc/modprobe.d/*.conf
options usbhid quirks=0x15c2:0x0038:0x0004

---

### Post by inypd on 2012-12-15
[SIZE=2]Hi
I do have Mythbuntu 12.4 with imon IR/LCD using MCE remote control.
In the past i was searching many forums for solution and non of them had the right solution, so on the end I combine some of the to make everything working. Here is my solution

 [/SIZE][SIZE=2]**sudo gedit /etc/lirc/hardware.conf**[/SIZE]
[SIZE=2]  [/SIZE][SIZE=2]
[/SIZE]
[SIZE=2]# /etc/lirc/hardware.conf
#
 #Chosen Remote Control
 REMOTE="Soundgraph iMON IR/LCD"
 REMOTE_MODULES="lirc_dev lirc_imon"
 REMOTE_DRIVER="devinput"
 REMOTE_DEVICE="/dev/input/by-id/usb-15c2_0038-event-if00"
 REMOTE SOCKET=""
 REMOTE_LIRCD_CONF="imon/lircd.conf.imon-pad"
 REMOTE_LIRCD_ARGS=""
 
 #Chosen IR Transmitter
 TRANSMITTER="None"
 TRANSMITTER_MODULES=""
 TRANSMITTER_DRIVER=""
 TRANSMITTER_DEVICE=""
 TRANSMITTER_LIRCD_CONF=""
 TRANSMITTER_LIRCD_ARGS=""
 
 #Enable lircd
 START_LIRCD="true"
 
 #Don't start lircmd even if there seems to be a good config file
 START_LIRCMD=""
 
 #Try to load appropriate kernel modules
 LOAD_MODULES="false"
 
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


[/SIZE]
[SIZE=2]**sudo apt-get install lcdproc**[/SIZE]
[SIZE=2][/SIZE][SIZE=2]**sudo gedit /etc/LCDd.conf**[/SIZE]
[SIZE=2]  [/SIZE][SIZE=2]
[/SIZE]
[SIZE=2]# LCDd.conf -- configuration file for the LCDproc server daemon LCDd
#
# This file contains the configuration for the LCDd server.
# 
# The format is ini-file-like. It is divided into sections that start at
# markers that look like [section]. Comments are all line-based comments,
# and are lines that start with '#' or ';'.
#
# The server has a 'central' section named [server]. For the menu there is
# a section called [menu]. Further each driver has a section which
# defines how the driver acts.
#
# The drivers are activated by specifiying them in a driver= line in the
# server section, like:
#
#   Driver=curses
#
# This tells LCDd to use the curses driver.
# The first driver that is loaded and is capable of output defines the
# size of the display. The default driver to use is curses.
# If the driver is specified using the -d <driver> command line option,
# the Driver= options in the config file are ignored.
#
# The drivers read their own options from the respective sections.



## Server section with all kinds of settings for the LCDd server ##
[server]

# Where can we find the driver modules ?
# IMPORTANT: Make sure to change this setting to reflect your
#            specific setup! Otherwise LCDd won't be able to find
#            the driver modules and will thus not be able to
#            function properly.
# NOTE: Always place a slash as last character !
DriverPath=/usr/lib/lcdproc/

# Tells the server to load the given drivers. Multiple lines can be given.
# The name of the driver is case sensitive and determines the section
# where to look for further configuration options of the specific driver
# as well as the name of the dynamic driver module to load at runtime.
# The latter one can be changed by giving af File= directive in the
# driver specific section.
#
# The following drivers are supported:
#   bayrad, CFontz, CFontz633, CFontzPacket, curses, CwLnx, ea65, 
#   EyeboxOne, g15, glcdlib, glk, hd44780, icp_a106, imon, imonlcd, IOWarrior,
#   irman, joy, lb216, lcdm001, lcterm, lirc, lis, MD8800, ms6931, mtc_s16209x,
#   MtxOrb, mx5000, NoritakeVFD, picolcd, pyramid, sed1330, sed1520, serialPOS,
#   serialVFD, shuttleVFD, sli, stv5730, svga, t6963, text, tyan, ula200,
#   xosd
Driver=imonlcd

# Tells the driver to bind to the given interface
Bind=127.0.0.1

# Listen on this specified port; defaults to 13666.
Port=13666

# Sets the reporting level; defaults to 2 (warnings and errors only).
#ReportLevel=3

# Should we report to syslog instead of stderr ? [default: no; legal: yes, no]
#ReportToSyslog=yes

# User to run as.  LCDd will drop its root priviledges, if any,
# and run as this user instead.
User=nobody

# The server will stay in the foreground if set to true.
#Foreground=no

# Hello message: each entry represents a display line; default: builtin
Hello=""
#Hello="   LCDproc!"

# GoodBye message: each entry represents a display line; default: builtin
GoodBye=""
#GoodBye="   LCDproc!"

# Sets the default time in seconds to displays a screen.
WaitTime=5

# If yes, the the serverscreen will be rotated as a usual info screen. If no,
# it will be a background screen, only visible when no other screens are
# active. The special value 'blank' is similar to no, but only a blank screen
# is displayed. [default: on; legal: on, off, blank]
ServerScreen=no

# Set master backlight setting. If set to 'open' a client may control the
# backlight for its own screens (only). [default: open; legal: off, open, on]
Backlight=open

# Set master heartbeat setting. If set to 'open' a client may control the
# heartbeat for its own screens (only). [default: open; legal: off, open, on]
#Heartbeat=open

# set title scrolling speed [default: 10; legal: 0-10]
#TitleSpeed=10

# The "...Key=" lines define what the server does with keypresses that
# don't go to any client.
# These are the defaults:
ToggleRotateKey=Enter
PrevScreenKey=Left
NextScreenKey=Right
#ScrollUpKey=Up
#ScrollDownKey=Down

# If you have only 4 keys, you can choose to use this:
#ToggleRotateKey=Enter
#PrevScreenKey=Up
#NextScreenKey=Down

# If you have only 3 keys, you can choose to use this:
#ToggleRotateKey=Enter
#PrevScreenKey=Up



## The menu section. The menu is an internal LCDproc client. ##
[menu]
# You can configure what keys the menu should use. Note that the MenuKey
# will be reserved exclusively, the others work in shared mode.

# The following works excellent with 4 keys or more.
MenuKey=Escape
EnterKey=Enter
UpKey=Up
DownKey=Down
# If you have 6 keys you may define these as well
#LeftKey=Left
#RightKey=Right

# If you have only 3 keys, you could use something like this:
#MenuKey=Escape
#EnterKey=Enter
#DownKey=Down



### Driver sections are below this line, in alphabetical order  ###


## EMAC BayRAD driver ##
[bayrad]

# Select the output device to use [default: /dev/lcd]
Device=/dev/lcd

# Set the communication speed [default: 9600; legal:  1200, 2400, 9600, 19200]
Speed=9600



## CrystalFontz driver (for CF632 & CF634) ##
[CFontz]

# Select the output device to use [default: /dev/lcd]
Device=/dev/ttyS0
# Select the LCD size [default: 20x4]
Size=20x4
# Set the initial contrast [default: 560; legal: 0 - 1000]
Contrast=350
# Set the initial brightness [default: 1000; legal: 0 - 1000]
Brightness=1000
# Set the initial off-brightness [default: 0; legal: 0 - 1000]
# This value is used when the display is normally
# switched off in case LCDd is inactive
OffBrightness=0
# Set the communication speed [default: 9600; legal: 1200, 2400, 9600, 19200 or 115200]
Speed=9600
# Set the firmware version (New means >= 2.0) [default: no; legal: yes, no]
NewFirmware=no
# Reinitialize the LCD's BIOS [default: no; legal: yes, no]
# normally you shouldn't need this
Reboot=no



## CrystalFontz633 driver (for CF633 only) ##
[CFontz633]

# Select the output device to use [default: /dev/lcd]
Device=/dev/ttyS0
# Select the LCD type (size) [default: 16x2]
Size=16x2
# Set the initial contrast [default: 560; legal: 0 - 1000]
Contrast=350
# Set the initial brightness [default: 1000; legal: 0 - 1000]
Brightness=1000
# Set the initial off-brightness [default: 0; legal: 0 - 1000]
# This value is used when the display is normally
# switched off in case LCDd is inactive
OffBrightness=50
# Set the communication speed [default: 9600; legal: 1200, 2400, 9600, 19200, 115200]
Speed=19200
# Set the firmware version (New means >= 2.0) [default: no; legal: yes, no]
# Currently this flag is not in use, there is no such thing as NewFirmware. ;=)
#NewFirmware=no
# Reinitialize the LCD's BIOS [default: no; legal: yes, no]
# I want to reboot the LCD to make sure we start from a known state
Reboot=yes



## CrystalFontz packet driver (for CF631, CF633 & CF635) ##
[CFontzPacket]

# Select the LCD model [default: 633; legal: 631, 633, 635]
Model=635
# Select the output device to use [default: /dev/lcd]
Device=/dev/ttyUSB0
# Select the LCD size [default: depending on model: 635: 20x4, 631: 20x2, 633: 16x2]
Size=20x4
# Set the initial contrast [default: 560; legal: 0 - 1000]
Contrast=350
# Set the initial brightness [default: 1000; legal: 0 - 1000]
Brightness=1000
# Set the initial off-brightness [default: 0; legal: 0 - 1000]
# This value is used when the display is normally
# switched off in case LCDd is inactive
OffBrightness=50
# Set the communication speed [default: 9600; legal: 1200, 2400, 9600, 19200, 115200]
Speed=115200
# Set the firmware version (New means >= 2.0) [default: no; legal: yes, no]
# Currently this flag is not in use, there is no such thing as NewFirmware. ;=)
#NewFirmware=no
# Reinitialize the LCD's BIOS [default: no; legal: yes, no]
# I want to reboot the LCD to make sure we start from a known state
Reboot=yes



## Curses driver ##
[curses]

# color settings
# foreground color [default: blue]
Foreground=blue
# background color when "backlight" is off [default: cyan]
Background=cyan
# background color when "backlight" is on [default: red]
Backlight=red

# display size [default: 20x4]
Size=20x4

# What position (X,Y) to start the left top corner at...
# Default: (7,7)
TopLeftX=7
TopLeftY=7

# use ASC symbols for icons & bars [default: no; legal, yes, no]
UseACS=no

# draw Border [default: yes; legal: yes, no]
DrawBorder=yes



## Cwlinux driver ##
[CwLnx]

# Select the LCD model [default: 12232; legal: 12232, 12832, 1602]
Model=12232

# Select the output device to use [default: /dev/lcd]
Device=/dev/ttyUSB0

# Select the LCD size [default: depending on model: 12232: 20x4, 12832: 21x4, 1602: 16x2]
Size=20x4

# Set the communication speed [default: 19200; legal: 9600, 19200]
Speed=19200

# Reinitialize the LCD's BIOS [default: no; legal: yes, no]
# normally you shouldn't need this
Reboot=no

# If you have a keypad connected. Keypad layout is currently not
# configureable from the config file.
Keypad=yes

# If you have a non-standard keypad you can associate any keystrings to keys.
# There are 6 input keys in the CwLnx hardware that generate characters
# from 'A' to 'F'.
#
# The following is the built-in default mapping hardcoded in the driver.
# You can leave those unchanged if you have a standard keypad.
# You can change it if you want to report other keystrings or have a non
# standard keypad.
# KeyMap_A=Up
# KeyMap_B=Down
# KeyMap_C=Left
# KeyMap_D=Right
# KeyMap_E=Enter
# KeyMap_F=Escape

# keypad_test_mode permits to test keypad assignement
# Default value is no
#keypad_test_mode=yes



## ea65 driver for the display in AOpen XC Cube AV EA65 media barebones ##
[ea65]

# Device is fixed /dev/ttyS1
# Width and Height are fixed 9x1

# As the VFD is self luminescent we don't have a backlight
# But we can use the backlight functions to control the front LEDs
# Brightness 0 to 299 -> LEDs off
# Brightness 300 to 699 -> LEDs half bright
# Brightness 700 to 1000 -> LEDs full bright
Brightness=500
# OffBrightness is the the value used for the 'backlight off' state
OffBrightness=0



## EyeboxOne driver ##
[EyeboxOne]

# Select the output device to use [default: /dev/ttyS1]
#Device=/dev/cua01
Device=/dev/ttyS1

# Set the display size [default: 20x4]
Size=20x4

# Switch on the backlight? [default: yes]
Backlight=yes

# Switch on the cursor? [default: no]
Cursor=no

# Set the communication speed [default: 19200; legal: 1200, 2400, 9600, 19200]
Speed=19200

# Enter Key is a \r character, so it's hardcoded in the driver
LeftKey=D
RightKey=C
UpKey=A
DownKey=B
EscapeKey=P

# You can find out which key of your display sends which
# character by setting keypad_test_mode to yes and running
# LCDd. LCDd will output all characters it receives.
# Afterwards you can modify the settings above and set
# keypad_set_mode to no again.
keypad_test_mode=no

## g15 driver for Logitech G15 Keyboard LCDs ##
[g15]

# Display size (currently unused)
size=20x5

## glcdlib meta driver for graphical LCDs ##
[glcdlib]

## mandatory:

# which graphical display supported by graphlcd-base to use [default: image]
# (see /etc/graphlcd.conf for possible drivers)
Driver=noritake800

# no=use graphlcd bitmap fonts (they have only one size / font file)
# yes=use fonts supported by FreeType2 (needs Freetype2 support in libglcdprocdriver and its dependants)
UseFT2=yes

# text resolution in fixed width characters [default: 16x4]
# (if it won't fit according to available physical pixel resolutioni
# and the minimum available font face size in pixels, then 
# 'DebugBorder' will automatically be turned on)
TextResolution=20x4

# path to font file to use
FontFile=/usr/share/fonts/corefonts/courbd.ttf

## these only apply if UseFT2=yes:

# character encoding to use
CharEncoding=iso8859-2

# minumum size in pixels in which fonts should be rendered
MinFontFaceSize=7x12

## optional:
Brightness=50                   # Brightness (in %) if applicable
Contrast=50                     # Contrast (in %) if applicable
Backlight=no                    # Backlight if applicable
UpsideDown=no                   # flip image upside down
Invert=no                       # invert light/dark pixels
ShowDebugFrame=no               # turns on/off 1 pixel thick debugging
                                # border whithin the usable text area,
                                # for setting up TextResolution and
                                # MinFontFaceSize (if using FT2);
ShowBigBorder=no                # border around the unused area
ShowThinBorder=yes              # border around the unused area
PixelShiftX=0
PixelShiftY=2



## Matrix Orbital GLK driver ##
[glk]

# select the serial device to use [default: /dev/lcd]
Device=/dev/lcd

# set the initial contrast value [default: 560; legal: 0 - 1000]
Contrast=560

# set the serial port speed [default: 19200; legal: 9600, 19200, 38400]
Speed=19200



## Hitachi HD44780 driver ##
[hd44780]

# Select what type of connection. See documentation for types.
ConnectionType=4bit

# Port where the LPT is [ususal: 0x278, 0x378 and 0x3BC]
Port=0x378

# Device of the serial interface [default: /dev/lcd]
Device=/dev/ttyS0

# Bitrate of the serial port (0 for interface default)
Speed=0

# If you have a keypad connected.
# You may also need to configure the keypad layout further on in this file.
Keypad=no

# Set the initial contrast (bwctusb and lcd2usb) [default: 500; legal: 0 - 1000]
Contrast=0

# Set brightness of the backlight (lcd2usb only) [default: 0; legal 0 - 1000]
#Brightness=1000
#OffBrightness=0

# If you have a switchable backlight.
Backlight=no

# If you have the additional output port ("bargraph") and you want to
# be able to control it with the lcdproc OUTPUT command
OutputPort=no

# Specifies if the last line is pixel addressable or it controls an
# underline effect. [default: true (= pixel addressable); legal: yes, no]
#Lastline=true

# Specifies the size of the LCD.
# In case of multiple combined displays, this should be the total size.
Size=20x4

# For multiple combined displays: how many lines does each display have.
# Vspan=2,2 means both displays have 2 lines.
#vspan=2,2

# If you have an HD66712, a KS0073 or an other 'almost HD44780-compatible',
# set this flag to get into extended mode (4-line linear).
#ExtendedMode=yes

# In extended mode, on some controllers like the ST7036 (in 3 line mode)
# the next line in DDRAM won't start 0x20 higher. [default: 0x20]
#LineAddress=0x10

# Character map to to map ISO-8859-1 to the LCD's character set
# [default: hd44780_default; legal: hd44780_default, hd44780_euro, 
#  ea_ks0073, sed1278f_0b ]
CharMap=hd44780_default

# If your display is slow and cannot keep up with the flow of data from
# LCDd, garbage can appear on the LCDd. Set this delay factor to 2 or 4
# to increase the delays. Default: 1.
#DelayMult=2

# Some displays (e.g. vdr-wakeup) need a message from the driver to that it
# is still alive. When set to a value bigger then null the character in the
# upper left corner is updated every <KeepAliveDisplay> seconds. Default: 0.
#KeepAliveDisplay=0

# If you experience occasional garbage on your display you can use this
# option as workaround. If set to a value bigger than null it forces a
# full screen refresh <RefreshDiplay> seconds. Default: 0.
#RefreshDisplay=5

# You can reduce the inserted delays by setting this to false.
# On fast PCs it is possible your LCD does not respond correctly.
# Default: true.
DelayBus=true

# If you have a keypad you can assign keystrings to the keys.
# See documentation for used terms and how to wire it.
# For example to give directly connected key 4 the string "Enter", use:
#   KeyDirect_4=Enter
# For matrix keys use the X and Y coordinates of the key:
#   KeyMatrix_1_3=Enter
KeyMatrix_4_1=Enter
KeyMatrix_4_2=Up
KeyMatrix_4_3=Down
KeyMatrix_4_4=Escape



## ICP A106 driver ##
[icp_a106]
Device=/dev/ttyS1

## Code Mercenaries IO-Warrior driver ##
[IOWarrior]

# display dimensions
Size=20x4

# serial number [exactly as listed by usbview]
# (if not given, the 1st IOWarrior found gets used)
#SerialNumber=00000674

# If you have an HD66712, a KS0073 or an other 'almost HD44780-compatible',
# set this flag to get into extended mode (4-line linear).
#ExtendedMode=yes

# Specifies if the last line is pixel addressable or it controls an
# underline effect. [default: true (= pixel addressable); legal: yes, no]
#Lastline=true



## Soundgraph/Ahanix/Silverstone/Uneed/Accent iMON driver ##
[imon]

# select the device to use
Device=/dev/lcd0

# display dimensions
Size=16x2



## Soundgraph iMON LCD ##
[imonlcd]
# Specify which iMon protocol should be used [legal: 0=15c2:ffdc device,
# 1=15c2:0038 device; default: 0]
Protocol=1

# Set the exit behavior [legal: 0=leave shutdown message, 1=show the big clock,
# 2=blank device; default: 1]
OnExit=2

# Select the output device to use [default: /dev/lcd0]
Device=/dev/lcd0

# Select the displays contrast [default: 200; legal: 0-1000]
Contrast=200

# Specify the size of the display in pixels [default: 96x16]
#Size=96x16

# Set the backlight state [default: on; legal: on, off]
#Backlight=on

# Set the disc mode [legal: 0=spin the "slim" disc - two disc segments,
# 1=their complement spinning; default: 0]
#DiscMode=0



## IrMan driver ##
[IrMan]
# in case of trouble with IrMan, try the Lirc emulator for IrMan

# Select the input device to use
#Device=/dev/irman

# Select the configuration file to use
#Config=/etc/irman.cfg



## IRtrans driver ##
[irtrans]

# Does the device have a backlight? [default: no; legal: yes, no]
#Backlight=no

# IRTrans device to connect to [default: localhost]
#Hostname=localhost

# display dimensions
Size=16x2



## Joystick driver ##
[joy]

# Select the input device to use [default: /dev/js0]
Device=/dev/js0

# set the axis map
Map_Axis1neg=Left
Map_Axis1pos=Right
Map_Axis2neg=Up
Map_Axis2pos=Down

# set the button map
Map_Button1=Enter
Map_Button2=Escape



## LB216 driver ##
[lb216]

# Select the output device to use [default: /dev/lcd]
Device=/dev/lcd

# Set the initial brightness [default: 255; legal: 0 - 255]
Brightness=255

# Set the communication speed [default: 9600; legal: 2400, 9600]
Speed=9600

# Reinitialize the LCD's BIOS [default: no; legal: yes, no]
Reboot=no



## LCDM001 driver ##
[lcdm001]

Device=/dev/ttyS1

# keypad settings
# Keyname      Function
#              Normal context              Menu context
# -------      --------------              ------------
# PauseKey     Pause/Continue              Enter/select
# BackKey      Back(Go to previous screen) Up/Left
# ForwardKey   Forward(Go to next screen)  Down/Right
# MainMenuKey  Open main menu              Exit/Cancel
PauseKey=LeftKey
BackKey=UpKey
ForwardKey=DownKey
MainMenuKey=RightKey

# You can rearrange the settings here.
# If your device is broken, have a look at server/drivers/lcdm001.h



## HNE LCTerm driver ##
[lcterm]
Device=/dev/ttyS1
Size=16x2



## LIRC input driver ##
[lirc]

# Specify an alternative location of the lircrc file [default: ~/.lircrc]
#lircrc=/etc/lircrc.lcdproc

# Must be the same as in your lircrc
#prog=lcdd



## LIS MCE 2005 driver ##
[lis]

# Set the initial brightness [default: 1000; legal: 0 - 1000]
# 0-250 = 25%, 251-500 = 50%, 501-750 = 75%, 751-1000 = 100%
#Brightness=1000

# Columns by lines [default: 20x2]
#Size=20x2

# USB Vendor ID [default: 0x0403]
# Change only if testing a compatible device.
#VendorID=0x0403

# USB Product ID [default: 0x6001]
# Change only if testing a compatible device.
#ProductID=0x6001



##The driver for the VFD of the Medion MD8800 PC ##
[MD8800]
# device to use [default: /dev/ttyS1]
#Device=/dev/ttyS1

# display size [default: 16x2]
#Size=16x2

# Set the initial brightness [default: 1000; legal: 0 - 1000]
Brightness=1000
# Set the initial off-brightness [default: 0; legal: 0 - 1000]
# This value is used when the display is normally
# switched off in case LCDd is inactive
OffBrightness=50



## MSI MS-6931 driver for displays in 1HU servers ##
[ms6931]

# device to use [default: /dev/ttyS1]
Device=/dev/ttyS1

# display size [default: 16x2]
#Size=16x2



## MTC-S16209x driver ##
[mtc_s16209x]

# Select the output device to use [default: /dev/lcd]
Device=/dev/lcd

# Set the initial brightness [default: 255; legal: 0 - 255]
Brightness=255

# Reinitialize the LCD's BIOS [default: no; legal: yes, no]
Reboot=no



## Matrix Orbital driver ##
[MtxOrb]

# Select the output device to use [default: /dev/lcd]
Device=/dev/ttyS0

# Set the display size [default: 20x4]
Size=20x4

# Set the display type [default: lcd; legal: lcd, lkd, vfd, vkd]
Type=lkd

# Set the initial contrast [default: 480]
# NOTE: The driver will ignore this if the display
#       is a vfd or vkd as they don't have this feature
Contrast=480

# Some old displays do not have an adjustable backlight but only can
# switch the backlight on/off. If you experience randomly appearing block
# characters, try setting this to false. [default: yes; legal: yes, no]
hasAdjustableBacklight=no

# Set the initial brightness [default: 1000; legal: 0 - 1000]
Brightness=1000
# Set the initial off-brightness [default: 0; legal: 0 - 1000]
# This value is used when the display is normally
# switched off in case LCDd is inactive
OffBrightness=0

# Set the communication speed [default: 19200; legal: 1200, 2400, 9600, 19200]
Speed=19200

# The following table translates from MtxOrb key letters to logical key names.
# By default no keys are mapped, meaning the keypad is not used at all.
#KeyMap_A=Left
#KeyMap_B=Right
#KeyMap_C=Up
#KeyMap_D=Down
#KeyMap_E=Enter
#KeyMap_F=Escape
# See the [menu] section for an explanation of the key mappings

# You can find out which key of your display sends which
# character by setting keypad_test_mode to yes and running
# LCDd. LCDd will output all characters it receives.
# Afterwards you can modify the settings above and set
# keypad_set_mode to no again.
keypad_test_mode=no



## mx5000 driver for LCD display on the Logitech MX5000 keyboard ##
[mx5000]

# Select the output device to use [default: /dev/hiddev0]
Device = /dev/hiddev0
# Time to wait in ms after the refresh screen has been sent [default: 1000]
WaitAfterRefresh = 1000

## Noritake VFD driver ##
[NoritakeVFD]
# device where the VFD is. Usual values are /dev/ttyS0 and /dev/ttyS1 [default: /dev/lcd]
Device=/dev/ttyS0
# Specifies the size of the LCD.
Size=20x4
# Set the initial brightness [default: 1000; legal: 0 - 1000]
Brightness=1000
# Set the initial off-brightness [default: 0; legal: 0 - 1000]
# This value is used when the display is normally
# switched off in case LCDd is inactive
OffBrightness=50
# set the serial port speed [default: 9600, legal: 1200, 2400, 9600, 19200, 115200]
Speed=9600
# Set serial data parity [default: 0 (None), legal: 0(=none), 1(=odd), 2(=even)]
Parity=0
# re-initialize the VFD [default: no; legal: yes, no]
Reboot=no



## Mini-box.com picoLCD (usblcd) driver ##
[picolcd]

# KeyTimeout is the time that LCDd spends waiting for a key press before cycling 
# through other duties.  Higher values make LCDd use less CPU time and make 
# key presses more detectable.  Lower values make LCDd more responsive but a 
# little prone to missing key presses.  500 (.5 second) is the default and a
# balanced value.
KeyTimeout=500

# Set the initial brightness [default: 1000; legal: 0 - 1000]
Brightness=1000

# Set the initial contrast [default: 1000; legal: 0 - 1000]
Contrast=1000

# Light the keys? i[default: on; legal: on, off]
Keylights=on

# If Keylights is on, the you can unlight specific keys below:
# Key0 is the directional pad.  Key1 - Key5 correspond to the F1 - F5 keys.  
# There is no LED for the +/- keys.  This is a handy way to indicate to users 
# which keys are disabled.  [default: on; legal: on, off]
Key0Light=on
Key1Light=on
Key2Light=on
Key3Light=on
Key4Light=on
Key5Light=on

# Host name or IP address of the LIRC instance that is to receive IR codes
# If not set, or set to an empty value, IR support is disabled.
#LircHost=127.0.0.1

# UDP port on which LIRC is listening [default: 8765; legal: 1 - 65535]
LircPort=8765

# Duration in jiffies of the synthesized sync pulse [default: 64; 0 to suppress]
LircSync=64

# Duration in jiffies of the synthesized gap; 0 to suppress, default 2048.
# This is really the fixed duration of an entire IR command; individual pulse/space 
# durations are deducted from this to determine the duration of the trailing gap.
LircLength=2048



## Pyramid LCD driver ##
[pyramid]

# device to connect to [default: /dev/lcd]
Device=/dev/ttyUSB0



## Seiko Epson 1330 driver ##
[sed1330]

# Port where the LPT is. Common values are 0x278, 0x378 and 0x3BC
Port=0x378

# Type of LCD module (legal: G321D, G121C, G242C, G191D, G2446, SP14Q002)
# Note: Currently only tested with G321D & SP14Q002.
Type=G321D

# Width x Height of a character cell in pixels [legal: 6x7 - 8x16; default: 6x10]
CellSize=6x10

# Select what type of connection [legal: classic, bitshaker; default: classic]
ConnectionType=classic



## Seiko Epson 1520 driver ##
[sed1520]

# Port where the LPT is. Usual values are 0x278, 0x378 and 0x3BC
Port=0x378



## serial POS display driver ##
[serialPOS]

# Device to use in serial modea [default: /dev/lcd]
Device=/dev/lcd

# Specifies the size of the display in characters. [default: 16x2]
Size=16x2

# Set the communication protocol to use with the POS display.
# [default: AEDEX; legal: IEE, Epson, Emax, IBM, LogicControls, Ultimate]
Type=AEDEX

# communication baud rate with the display [default: 9600; legal: 1200, 2400, 19200, 115200]
Speed=9600



## Serial VFD driver ##
## Drives various (see below) serial 5x7dot VFD's.  ##
[serialVFD]

# Specifies the displaytype.[default: 0]
# 0 NEC (FIPC8367 based) VFDs.
# 1 KD Rev 2.1.
# 2 Noritake VFDs (*).
# 3 Futaba VFDs
# 4 IEE S03601-95B
# 5 IEE S03601-96-080 (*)
# 6 Futaba NA202SD08FA (allmost IEE compatible)
# 7 Samsung 20S207DA4 and 20S207DA6
# 8 Nixdorf BA6x / VT100
# (* most should work, not testet yet.)
Type=0

# "no" if display connected serial, "yes" if connected parallel. [default: no(=serial)]
use_parallel=no

# Number of Custom-Characters [default: displaytype dependent]
#Custom-Characters=0

# Portaddress where the LPT is. Used in parallelmode only. Usual values are 0x278, 0x378 and 0x3BC
Port=0x378

# Set parallel port timingdelay (us). Used in parallelmode only. [default: 2; legal: 0 - 255]
#PortWait=2

# Device to use in serial mode. Usual values are /dev/ttyS0 and /dev/ttyS1
Device=/dev/ttyS1

# Specifies the size of the VFD.
Size=20x2

# Set the initial brightness [default: 1000; legal: 0 - 1000]
# (4 steps 0-250, 251-500, 501-750, 751-1000)
Brightness=1000
# Set the initial off-brightness [default: 0; legal: 0 - 1000]
# This value is used when the display is normally
# switched off in case LCDd is inactive
# (4 steps 0-250, 251-500, 501-750, 751-1000)
OffBrightness=0

# set the serial port speed [default: 9600; legal: 1200, 2400, 9600, 19200, 115200]
Speed=9600

# enable ISO 8859 1 compatibility [default: yes; legal: yes, no]
#ISO_8859_1=yes



## shuttleVFD driver ##
[shuttleVFD]
# No options



## stv5730 driver ##
[stv5730]

# Port the device is connected to [default: 0x378]
Port=0x378



## SVGAlib driver ##
[svga]

# svgalib mode to use [default: G320x240x256; legal: supported svgalib modes]
#Mode=G640x480x256

# set display size [default: 20x4]
Size=20x4

# Set the initial contrast [default: 500; legal: 0 - 1000]
# Can be set but does not change anything internally
Contrast=500

# Set the initial brightness [default: 1000; legal: 1 - 1000]
Brightness=1000

# Set the initial off-brightness [default: 500; legal: 1 - 1000]
# This value is used when the display is normally
# switched off in case LCDd is inactive
OffBrightness=500



## Text driver ##
[text]
# Set the display size [default: 20x4]
Size=20x4



## Toshiba T6963 driver ##
[t6963]

# set display size [default: 20x6]
Size=20x6

# port to use [default: 0x378; legal: 0x200 - 0x400]
Port=0x378

# Is ECP mode on? [default: yes; legal: yes, no]
#ECPlpt=yes

# Use graphics? [default: no; legal: yes, no]
#graphic=no



## Tyan Barebones LCD driver (GS10 & GS12 series) ##
[tyan]

# Select the output device to use [default: /dev/lcd]
Device=/dev/lcd

# Set the communication speed [default: 9600; legal: 4800, 9600]
Speed=9600

# set display size [default: 16x2]
Size=16x2



## ELV ula200 driver ##
[ula200]

# Select the LCD size [default: 20x4]
Size=20x4

# If you have a non standard keypad you can associate any keystrings to keys.
# There are 6 input key in the CwLnx hardware that generate characters
# from 'A' to 'F'.
#
# The following it the built-in default mapping hardcoded in the driver.
# You can leave those unchanged if you have a standard keypad.
# You can change it if you want to report other keystrings or have a non
# standard keypad.
# KeyMap_A=Up
# KeyMap_B=Down
# KeyMap_C=Left
# KeyMap_D=Right
# KeyMap_E=Enter
# KeyMap_F=Escape



## Wirz SLI LCD driver ##
[sli]

# Select the output device to use [default: /dev/lcd]
Device=/dev/lcd

# Set the communication speed [default: 19200; legal: 1200, 2400, 9600, 19200, 38400, 57600, 115200]
Speed=19200



## OnScreen Display using libxosd ##
[xosd]

# set display size [default: 20x4]
Size=20x4

# Offset in pixels from the top-left corner of the monitor [default: 0x0]
Offset=200x200

# X font to use, in XLFD format, as given by "xfontsel"
Font=-*-terminus-*-r-*-*-*-320-*-*-*-*-*

# EOF
[/SIZE]
[SIZE=2]
[/SIZE]
[SIZE=2]
[/SIZE]
**[SIZE=2]Go to [SIZE=2]M[/SIZE]ythTV   setup>Appearances>LCD device display  and enable LCD device.[/SIZE]**
[B][SIZE=2]
[/SIZE][/B]
**[SIZE=2]sudo /etc/init.d/LCDd restart[/SIZE]**
**[SIZE=2]  [/SIZE]****[SIZE=2] [/SIZE]**
**[SIZE=2]  [/SIZE]****[SIZE=2]sudo gedit /etc/lirc/lircd.conf[/SIZE]**
[SIZE=2]
[/SIZE][SIZE=2]#include "/usr/share/lirc/remotes/imon/lircd.conf.imon"
 include "/usr/share/lirc/remotes/devinput/lircd.conf.devinput"


[/SIZE]
[SIZE=2]  [/SIZE]**[SIZE=2]sudo apt-get install ir-keytable[/SIZE]**
**[SIZE=3]  [/SIZE]****[SIZE=3] [/SIZE]**
**[SIZE=3]  [/SIZE]****[SIZE=3]sudo gedit /etc/rc.local[/SIZE]**
[SIZE=2]  
#!/bin/sh -e
#
# rc.local

ir-keytable -w /lib/udev/rc_keymaps/imon_mce
exit 0

sudo gedit ~/.lirc/mythtv  

# LIRCRC
# Author(s): Mario Limonciello, Nick Fox, John Baab, Edited by Chris Murphy
# Created for use with Mythbuntu 10.10
begin
    remote = devinput
    prog = mythtv
    button = KEY_EXIT
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_RECORD
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_PLAY
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_REWIND
    config = <
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_PAUSE
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_FASTFORWARD
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_PREVIOUS
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_STOP
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_NEXT
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_NEXT
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_BACKSPACE
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_SELECT
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_CONTEXT_MENU
    config = Q
    repeat = 0
    delay = 0
end 

begin
    remote = devinput
    prog = mythtv
    button = KEY_COMPOSE
    config = Z
    repeat = 0
    delay = 0
end 


begin
    remote = devinput
    prog = mythtv
    button = KEY_OK
    config = Enter
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_ENTER
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_UP
    config = Up
    repeat = 3
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_DOWN
    config = Down
    repeat = 3
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_LEFT
    config = Left
    repeat = 3
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_RIGHT
    config = Right
    repeat = 3
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_ESC
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_EPG
    config = S
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_PROG1
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_INFO
    config = I
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_MUTE
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_VOLUMEUP
    config = ]
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_VOLUMEDOWN
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_CHANNELUP
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_CHANNELDOWN
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_TIME
    config = F8
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_NUMERIC_1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_NUMERIC_2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_NUMERIC_3
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_NUMERIC_4
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_NUMERIC_5
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_NUMERIC_6
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_NUMERIC_7
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_NUMERIC_8
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_NUMERIC_9
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_NUMERIC_0
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_NUMERIC_POUND
    config = D
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_NUMERIC_STAR
    config = ?
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_BOOKMARKS
    config = C
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_MEDIA
    config = O
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_ZOOM
    config = W
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_SCREEN
    config = F
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_MENU
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_SUBTITLE
    config = T
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_LANGUAGE
    config = +
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_VIDEO
    config = \U
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_MEDIA
    config = \M
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_CAMERA
    config = \I
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_GREEN
    config = \T
    repeat = 0
    delay = 0
end

begin
    remote = devinput
    prog = mythtv
    button = KEY_DVD
    config = \D
    repeat = 0
    delay = 0
end

[SIZE=2][/SIZE]

Af[SIZE=2][SIZE=2]ter these [/SIZE][SIZE=2][SIZE=2][SIZE=2]updates[/SIZE] and modifications [SIZE=2][SIZE=2]everything was working the way i won[SIZE=2]ted :p[/SIZE][/SIZE] [/SIZE][/SIZE][/SIZE][/SIZE]
[/SIZE]

---

### Post by ako673de on 2012-12-23
Hello,

I'm using yaVDR 0.5 which is based on Ubuntu 12.04. I have an iMon VFD  with Antec Fusion RM200 remote (Vendor:Product=15c2:0044). I already  managed to get the VFD to work and the knob/mute knob worked OOTB.

However, the remote still lacks certain functions:
- The mouse/cursor switch key has no effect
- => I didn't ever see the mouse functionality at work
- In general some keys (e.g. ENTER) are not being recognized at all

Internet research was quite confusing. Most posts recommend to  reconfigure "ir-keytables". But investigation of my system showed, that  it obviously is constructed a bit different. It does not use  ir-keytables for the RM200 at all but binds it directly via eventlircd and it's udev-based evmaps rules.

With this very basic in-deep knowledge of my system I well might manage  to activate the missing and reconfigure the mixed up keys, but for sure  activation of the mouse/cursor switch is beyond my abilities.

Any ideas are welcome.

best regards
ako673de

---

### Post by omel on 2013-07-02
> **pinakibag said:**
> I have the same piece 15c2:0038 I tried changing LCDd.conf and lcdproc.conf but when I run lcdproc nothing happens on the LCD nor any error in the screen. Can you please tell me what exactly you changed in LCDd.conf & lcdproc.conf

Hi

Did you get this working ??

If so what did you do ??

Regards

---

### Post by tgm4883 on 2013-07-02
When wanting to post to a thread that nobody has posted to in 6+ months, instead, open a new thread.

---

