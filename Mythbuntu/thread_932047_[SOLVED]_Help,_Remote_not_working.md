---
title: "[SOLVED] Help, Remote not working"
date: 2008-09-27
forum: Mythbuntu
---

### Post by kublikhan on 2008-09-27
Upgraded to MythBuntu 8.04. My remote control is not working. I recorded a new lircd.conf file with irrecord and mode2 works, but irw does not work(no output). I have been editing lircd.conf and hardware.conf and am not confident either file is correct at this point. I made sure "REMOTE" from hardware.conf and "name" from lircd.conf are the same, but that did not help. Is there any other place I need to update the remote's name? Are the other lines correct? Both hardware.conf and lircd.conf should be in etc/lirc/ right?  Any other ideas to get this working?

hardware.conf and lircd.conf:
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="hauppauge"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"
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

```

# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.3pre1(default) on Sat Sep 27 21:33:43 2008
#
# contributed by 
#
# brand:                       /root/lircd.conf
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name   hauppauge
  flags RAW_CODES|CONST_LENGTH
  eps            30
  aeps          100

  ptrail          0
  repeat     0     0
  gap          106314

      begin raw_codes

          name up
             2750     800     500     350     550     350
              500     800     550     800    1400     800
              500     400     500     350     500     400
              500     350     500     400     500     400
              500     350     500     400     500     400
              450     400     950     400     500     400
              450     400     500     850     450     400
              500     400     500     400     450     400
              950     800     500     400     500     400
              450     400     500     400     900     450
              450     400     500     400     450     850
              500

          name down
             2750     750     550     350     550     350
              500     800     500     800    1400     850
              500     350     500     400     500     350
              550     350     500     400     500     350
              500     400     500     400     500     350
              500     400     950     400     450     400
              500     400     500     350     500     850
              500     400     450     400     500     400
              900     850     500     400     450     400
              500     400     500     400     900     400
              500     400     500     400     450     400
              500

          name right
             2750     800     550     350     500     350
              550     800     500     800    1400     800
              500     400     500     350     550     350
              500     400     500     350     500     400
              500     400     500     350     500     400
              500     400     900     400     500     400
              500     350     500     850     500     400
              450     400     500     400     500     350
              950     850     450     400     500     400
              500     400     900     850     500     400
              450     400     500     400     900

          name left
             2700     800     550     350     500     350
              550     800     500     800    1400     800
              550     350     500     400     500     350
              500     400     500     400     500     350
              500     400     500     400     450     400
              500     400     900     400     500     400
              500     400     450     400     500     850
              450     400     500     400     500     400
              900     850     500     400     450     400
              500     400     900     850     500     400
              450     400     500     400     500     400
              500

          name power
             2750     750     550     350     550     350
              500     800     550     800    1400     800
              500     350     550     350     500     400
              500     350     500     400     500     400
              500     350     500     400     500     400
              450     400     950     400     500     350
              500     400     500     800     500     400
              500     400     450     400     500     400
              950     800     500     400     500     400
              450     400     500     400     500     400
              900     400     500     800     500     400
              500

          name window
             2750     800     550     300     550     350
              550     800     500     800    1400     800
              500     400     500     350     550     350
              500     400     500     350     500     400
              500     400     500     350     500     400
              500     400     900     400     500     400
              500     350     500     400     500     800
              500     400     500     400     450     400
              950     850     450     400     500     400
              500     400     450     400     500     400
              900     400     500     850     900

          name ok
             2750     800     550     300     550     350
              550     750     550     800    1400     800
              500     400     500     350     550     350
              500     400     500     350     500     400
              500     400     450     400     500     400
              500     350     950     400     500     400
              450     400     500     850     450     400
              500     400     500     400     450     400
              950     850     450     400     500     400
              500     400     900     850     450     400
              500     400     950     800     550

      end raw_codes

end remote

```

---

### Post by nasha on 2008-09-28
What remote control are you using?

Is it connected via USB, Serial, via Tuner Card?

Have you tried using Mythbuntu Control Centre to set up the remote?

Did the remote work prior to upgrade to 8.04? Are you using the same settings in your lircd.conf? (8.04 lircd.conf has a slightly different format to previous versions)

---

### Post by kublikhan on 2008-09-28
Remote control is a hauppauge. It is connected via USB. It worked in MythBuntu 7, but someone else set that up. I reformatted my system before install the latest version of mythbuntu. The format of the lircd.conf file was generated by irrecord. Mythbuntu Control Centre did not help.

---

### Post by nasha on 2008-09-28
Here are some links you might find very useful:

"Here we'll look at getting the remote control that comes with the Hauppauge Nova-T working using the LIRC package. Contrary to almost everything you'll read on the web, this can be done without compiling LIRC."
[HTML]http://parker1.co.uk/mythtv_ubuntu2.php
[/HTML]

"Hi, after a week I'm still struggling with the same issues I mentioned in post 1. In an effort to get try to get more help I wish to give some extra information that I think may be relevant.

First if all here is the contents of /etc/lirc/hardware.conf :-"
[HTML]http://ubuntuforums.org/showthread.php?t=594890[/HTML]


"HOWTO: Hauppauge Remote Control in Kubuntu"
[HTML]http://www.hardwareforums.com/howto-hauppauge-remote-control-kubuntu-11929/[/HTML]

---

### Post by kublikhan on 2008-09-28
> **nasha said:**
> Here are some links you might find very useful:

"Here we'll look at getting the remote control that comes with the Hauppauge Nova-T working using the LIRC package. Contrary to almost everything you'll read on the web, this can be done without compiling LIRC."
[HTML]http://parker1.co.uk/mythtv_ubuntu2.php
[/HTML]

"Hi, after a week I'm still struggling with the same issues I mentioned in post 1. In an effort to get try to get more help I wish to give some extra information that I think may be relevant.

First if all here is the contents of /etc/lirc/hardware.conf :-"
[HTML]http://ubuntuforums.org/showthread.php?t=594890[/HTML]

"HOWTO: Hauppauge Remote Control in Kubuntu"
[HTML]http://www.hardwareforums.com/howto-hauppauge-remote-control-kubuntu-11929/[/HTML]
When I run cat /proc/bus/input/devices I don't see anything that could be my hauppauge. Just a bunch of mouse, keyboard, and power button stuff. Maybe my remote doesn't use an eventN device? Without an eventN device, I can't proceed any further with these 3 guides.

---

### Post by anonymousdog on 2008-09-28
How about the outputs of 'ls /dev/lirc*' and 'sudo lsusb -v'.  Let's identify what you have.

---

### Post by kublikhan on 2008-09-28
ls -la /dev/lirc*:
```
crw-rw---- 1 root root 61, 0 2008-09-28 12:04 /dev/lirc0
srw-rw-rw- 1 root root     0 2008-09-28 13:43 /dev/lircd

```

lsusb -v:
```
Bus 003 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.24-19-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:02.2
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
Hub Descriptor:
  bLength              11
  bDescriptorType      41
  nNbrPorts             8
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
    TT think time 8 FS bits
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00 0x00
  PortPwrCtrlMask    0xff 0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
   Port 7: 0000.0100 power
   Port 8: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 002 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.24-19-generic ohci_hcd
  iProduct                2 OHCI Host Controller
  iSerial                 1 0000:00:02.1
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             4
  wHubCharacteristic 0x0002
    No power switching (usb 1.0)
    Ganged overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 001 Device 004: ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x046d Logitech, Inc.
  idProduct          0xc00e M-BJ69 Optical Wheel Mouse
  bcdDevice           11.10
  iManufacturer           1 Logitech
  iProduct                2 USB-PS/2 Optical Mouse
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               98mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      52
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)

Bus 001 Device 003: ID 0609:031d SMK Manufacturing, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        16
  idVendor           0x0609 SMK Manufacturing, Inc.
  idProduct          0x031d 
  bcdDevice            0.00
  iManufacturer           1 SMK
  iProduct                2 eHome Infrared Transceiver
  iSerial                 3 SM004aRk
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               0
Device Status:     0x0001
  Self Powered

Bus 001 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.24-19-generic ohci_hcd
  iProduct                2 OHCI Host Controller
  iSerial                 1 0000:00:02.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             4
  wHubCharacteristic 0x0002
    No power switching (usb 1.0)
    Ganged overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0103 power enable connect
   Port 2: 0000.0303 lowspeed power enable connect
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

```

---

### Post by anonymousdog on 2008-09-28
Looks like you have one of the standard MCE remotes with transceiver.  [This page](http://www.mythtv.org/wiki/index.php/MCE_Remote) may help, but that's supposed to work out of the box with the settings created by the MCC for "windows media center remotes (new version Phillips et al)".

---

### Post by kublikhan on 2008-09-28
I got irw working. I had to change my modules line 
from:
MODULES="lirc_dev lirc_i2c"
to:
MODULES="lirc_mceusb2"

---

### Post by anonymousdog on 2008-09-28
Good.  Looks like you're almost home.

---

### Post by kublikhan on 2008-09-28
I grabbed a full lircd.conf file, populated my mythtv lircrc file and now have a fully function remote in mythtv. Problem solved. Thanx everyone.

---

