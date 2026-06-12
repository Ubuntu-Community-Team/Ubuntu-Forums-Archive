---
title: "Please help me with usb-uirt"
date: 2009-04-29
forum: Mythbuntu
---

### Post by phroman on 2009-04-29
If I have one more drop of Redbull I'm gonna die.  I have my sound working, my firefly remote, all I need is to get my usb-uirt working to control my Direct TV Satellite box and the world is mine!

I feel that I've read every possible post, thread, and topic on this but I cannot get it working.  First here's my dmesg | grep -i usb

```
joe@mythserver1:~/Desktop$ dmesg | grep -i usb
[    0.400284] usbcore: registered new interface driver usbfs
[    0.400284] usbcore: registered new interface driver hub
[    0.400284] usbcore: registered new device driver usb
[    3.820084] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.820140] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    3.836007] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    3.836063] usb usb1: configuration #1 chosen from 1 choice
[    3.836090] hub 1-0:1.0: USB hub found
[    3.836221] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    3.852007] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    3.852064] usb usb2: configuration #1 chosen from 1 choice
[    3.852086] hub 2-0:1.0: USB hub found
[    3.852180] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.852190] uhci_hcd: USB Universal Host Controller Interface driver
[    3.852233] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    3.852297] usb usb3: configuration #1 chosen from 1 choice
[    3.852313] hub 3-0:1.0: USB hub found
[    3.852401] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    3.852470] usb usb4: configuration #1 chosen from 1 choice
[    3.852485] hub 4-0:1.0: USB hub found
[    3.852575] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    3.852638] usb usb5: configuration #1 chosen from 1 choice
[    3.852653] hub 5-0:1.0: USB hub found
[    3.852739] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    3.852801] usb usb6: configuration #1 chosen from 1 choice
[    3.852818] hub 6-0:1.0: USB hub found
[    3.852908] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    3.852970] usb usb7: configuration #1 chosen from 1 choice
[    3.852985] hub 7-0:1.0: USB hub found
[    3.853070] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    3.853131] usb usb8: configuration #1 chosen from 1 choice
[    3.853145] hub 8-0:1.0: USB hub found
[    3.853229] usbcore: registered new interface driver libusual
[    3.853247] usbcore: registered new interface driver usbserial
[    3.853254] USB Serial support registered for generic
[    3.853264] usbcore: registered new interface driver usbserial_generic
[    3.853265] usbserial: USB Serial Driver core
[    4.624009] usb 6-1: new low speed USB device using uhci_hcd and address 2
[    4.800843] usb 6-1: configuration #1 chosen from 1 choice
[    5.040010] usb 6-2: new low speed USB device using uhci_hcd and address 3
[    5.296894] usb 6-2: configuration #1 chosen from 1 choice
[    5.540009] usb 7-1: new low speed USB device using uhci_hcd and address 2
[    5.718992] usb 7-1: configuration #1 chosen from 1 choice
[    5.960010] usb 7-2: new full speed USB device using uhci_hcd and address 3
[    6.136994] usb 7-2: configuration #1 chosen from 1 choice
[    8.174027] usbcore: registered new interface driver hiddev
[    8.189993] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/input/input3
[    8.192540] generic-usb 0003:046D:C01D.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-1/input0
[    8.234241] USB Serial support registered for FTDI USB Serial Device
[    8.234313] ftdi_sio 7-2:1.0: FTDI USB Serial Device converter detected
[    8.234339] usb 7-2: Detected FT232BM
[    8.234375] usb 7-2: FTDI USB Serial Device converter now attached to ttyUSB0
[    8.234386] usbcore: registered new interface driver ftdi_sio
[    8.234388] ftdi_sio: v1.4.3:USB FTDI Serial Converters Driver
[    8.235543] lirc_atiusb: USB remote driver for LIRC $Revision: 1.69 $
[    8.235544] lirc_atiusb: Paul Miller <pmiller9@users.sourceforge.net>
[    8.236622] input:   USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0/input/input5
[    8.244622] generic-usb 0003:05AF:0802.0002: input,hidraw1: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:1d.0-2/input0
[    8.255956] lirc_atiusb[2]: X10 Wireless Technology Inc USB Receiver on usb7:2
[    8.265961] usbcore: registered new interface driver lirc_atiusb
[    8.332841] input:   USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.1/input/input6
[    8.334828] generic-usb 0003:05AF:0802.0003: input,hidraw2: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:1d.0-2/input1
[    8.334843] usbcore: registered new interface driver usbhid
[    8.334846] usbhid: v2.6:USB HID core driver
joe@mythserver1:~/Desktop$ 

```  

Adding IR Transmitter in MCC changes my Lirc config files and leaves my firefly remote not working, now that I've fixed that, I'm trying to edit my /etc/lirc/hardware.conf file manually.
Here is that file: 

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Snapstream X10 RF"
REMOTE_MODULES="lirc_dev lirc_atiusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="atiusb/lircd.conf.atiusb"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="USB_UIRT2 : Direct TV Receiver"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER="uirt2_raw"
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF="directtv/general.conf"
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

I do not know what the values of the settings in Chosen IR Transmitter should be.  I've tried everything I could possibly think of, honestly. 

Running irsend gives me this: 
 
```
joe@mythserver1:~/Desktop$ irsend SEND_ONCE directtv ok
irsend: command failed: SEND_ONCE directtv ok
irsend: hardware does not support sending
joe@mythserver1:~/Desktop$ 


``` 

So I seem to be stuck with irsend telling me that this device does not support sending, which is not correct.  I really, really would appreciate help in getting this working.  Let me know if there are any other files or anything I need to post.  Thank you very much.

---

### Post by phroman on 2009-05-01
Some progress has been made!!  I know this post is long, but please help me out if you can, I'm sooo close.  I made one change to my /etc/lirc/hardware.conf file, I added, under the Chosen IR Transmitter section, TRANSMITTER_DEVICE="/dev/lirc1". Full /etc/lirc/hardware.conf below:

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Snapstream_X10_RF"
REMOTE_MODULES="lirc_dev lirc_atiusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="atiusb/lircd.conf.atiusb"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="USB_UIRT2"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER="uirt2_raw"
TRANSMITTER_DEVICE="/dev/lirc1"
TRANSMITTER_LIRCD_CONF="directtv/general.conf"
TRANSMITTER_LIRCD_ARGS="-d /dev/ttyUSB0"

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

Now, I can use irsend from the command line to successfully send ir commands to control my Direct TV H21-100 box. I tried the code like this:  
```
irsend -d /dev/lirc1 SEND_ONCE USB_UIRT2 guide
```

This will bring up the direct tv guide! Suhweet.


I tested the channel-changing script from the command line with this.
```
/usr/local/bin/change-channel-lirc.pl 11
```

Successful channel change to channel 11.  Awsome.

MythTV Frontend, click on Watch TV, screen goes black for 5 seconds or so, and kicks me back to Frontend main menu. Not Cool. If I go into MythTV setup and remove the entry for the channel change script, I can watch tv in the front end and do everything except change channels.  So somehow MythTv/Front end is dying when it calls the channel change script. Where do I begin to diagnose this?  
If anyone has probs similar to mine and needs any config files or anything please let me know, I'd love to give some help back.  Thanks!

---

### Post by santhony on 2009-12-17
Did you get this to work?  This is exactly where I am out with my system...

---

### Post by santhony on 2009-12-29
I've still been tinkering with Ubuntu Karmic with MythTV.  All is working great... until you get to advanced features with IR.. remote controls..

I have a Snapstream Firefly and a USB-UIRT.

I can say that LIRC or IR in Linux is at best... a Train Wreck...  I've been trying for over a month now...   This makes setting up a Raid set with MDADM a walk in the park...

I know this will work.. just a matter of finding a comprehensive document/troubleshooting guide...  I've read plenty already...

I do have my Snapstream FF working.. Only on Channel 1 tho..  I cannot get irrecord to work for the other channels.. it dies out after the first key capture...  I have 4 remote clients working off my Mythtv setup.. So i need to program 4 different channels...

There's no way that I'm going back to Windows tho...  


Any last ditch suggestions?

My next option is to go try this device:
[http://www.commandir.com/content/view/19/31/](http://www.commandir.com/content/view/19/31/)

Command IR...

---

