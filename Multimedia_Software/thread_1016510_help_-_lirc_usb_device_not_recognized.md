---
title: "help - lirc usb device not recognized"
date: 2008-12-20
forum: Multimedia Software
---

### Post by kelargo on 2008-12-20
I'm using intrepid and I have a VLsystem mplay usb receiver installed.

> $ lsusb
Bus 001 Device 007: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC

and I manually edited lircd.conf to use the mplay remote

> /etc/lirc# cat lircd.conf
include "/usr/share/lirc/remotes/vlsystem/lircd.conf.mplay"


If I launch "Infrared Remote Control" from settings, I am able to select the VLSystem MPlay Blast remote from "IR Remote Control".

but the choice of receivers does not show any of the USB devices. 
and "auto-detect" does not help, either. Nothing is detected.

How can I get lircd to load with the proper hardware driver - "mplay" ?

thank you

---

### Post by kelargo on 2008-12-20
this is lsusb -v :


```
Bus 001 Device 007: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Device Descriptor:                                                                                      
  bLength                18                                                                             
  bDescriptorType         1                                                                             
  bcdUSB               2.00                                                                             
  bDeviceClass            0 (Defined at Interface level)                                                
  bDeviceSubClass         0                                                                             
  bDeviceProtocol         0                                                                             
  bMaxPacketSize0         8                                                                             
  idVendor           0x0403 Future Technology Devices International, Ltd                                
  idProduct          0x6001 FT232 USB-Serial (UART) IC                                                  
  bcdDevice            6.00                                                                             
  iManufacturer           1 FTDI                                                                        
  iProduct                2 FT232R USB UART                                                             
  iSerial                 3 A3000F9O                                                                    
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
    MaxPower               90mA                                                                         
    Interface Descriptor:                                                                               
      bLength                 9                                                                         
      bDescriptorType         4                                                                         
      bInterfaceNumber        0                                                                         
      bAlternateSetting       0                                                                         
      bNumEndpoints           2                                                                         
      bInterfaceClass       255 Vendor Specific Class                                                   
      bInterfaceSubClass    255 Vendor Specific Subclass                                                
      bInterfaceProtocol    255 Vendor Specific Protocol                                                
      iInterface              2 FT232R USB UART                                                         
      Endpoint Descriptor:                                                                              
        bLength                 7                                                                       
        bDescriptorType         5                                                                       
        bEndpointAddress     0x81  EP 1 IN                                                              
        bmAttributes            2                                                                       
          Transfer Type            Bulk                                                                 
          Synch Type               None                                                                 
          Usage Type               Data                                                                 
        wMaxPacketSize     0x0040  1x 64 bytes                                                          
        bInterval               0                                                                       
      Endpoint Descriptor:                                                                              
        bLength                 7                                                                       
        bDescriptorType         5                                                                       
        bEndpointAddress     0x02  EP 2 OUT                                                             
        bmAttributes            2                                                                       
          Transfer Type            Bulk                                                                 
          Synch Type               None                                                                 
          Usage Type               Data                                                                 
        wMaxPacketSize     0x0040  1x 64 bytes                                                          
        bInterval               0                                                                       
Device Status:     0x0000                                                                               
  (Bus Powered)                                                                                    


```

---

### Post by kelargo on 2008-12-20
I get this error when trying to load the lirc_serial module

> # modprobe lirc_serial
FATAL: Error inserting lirc_serial (/lib/modules/2.6.27-11-generic/kernel/ubuntu/lirc/lirc_serial/lirc_serial.ko): Device or resource busy


and here is my hardware.conf... I think it is correct.. but I'm not sure why lirc_serial does not load.. ?

what to do next? thanks!

> # /etc/init.d/lirc start -v
 * Loading LIRC modules                                                                                                                                   [ OK ]
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf



cat /etc/lirc/hardware.conf

> 
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="VLSystem MPlay Blast"
REMOTE_MODULES="lirc_serial"
REMOTE_DRIVER="mplay"
REMOTE_DEVICE="/dev/ttyUSB0"
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
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
REMOTE_MODEL="MPlay Blast"
REMOTE_VENDOR="VLSystem"

# Receiver settings required by gnome-lirc-properties
RECEIVER_MODEL="Serial Port Receiver"
RECEIVER_VENDOR="Generic"


---

### Post by kelargo on 2008-12-20
I added an entry in this bug:
[URL="https://bugs.launchpad.net/ubuntu/+source/linux/+bug/298791"]
https://bugs.launchpad.net/ubuntu/+source/linux/+bug/298791[/URL]

---

### Post by rhk on 2009-08-22
I have the same remote or at least the receiver:

dmesg says 
[ 1969.984022] usb 7-1: new full speed USB device using uhci_hcd and address 3
[ 1970.235772] usb 7-1: configuration #1 chosen from 1 choice
[ 1970.238660] ftdi_sio 7-1:1.0: FTDI USB Serial Device converter detected
[ 1970.238679] usb 7-1: Detected FT232RL
[ 1970.238725] usb 7-1: FTDI USB Serial Device converter now attached to ttyUSB0

and 
lsusb:

Bus 007 Device 003: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC


I'm using Jaunty and I get exactly the same errors as you when trying to load lirc serial drivers. The bug you reported should now be fixed? All tips are appreciated!

r

---

### Post by rhk on 2009-08-25
Funny enough it works in Jaunty with no problems: 

plug it in, install lirc from repositories, select "Vlsys Mplay blast" as type. Take the config files here: [http://forum.ubuntu-fi.org/index.php?topic=28620.msg220076#msg220076](http://forum.ubuntu-fi.org/index.php?topic=28620.msg220076#msg220076)

No kernel modules required. Bulk-Jaunty kernel.

Not bad!

r

---

