---
title: "Cisco Valet Connector AM10 in Ubuntu 11.04"
date: 2011-07-20
forum: Networking &amp; Wireless
---

### Post by ohmysql on 2011-07-20
I'm using Ubuntu 11.04. I'm trying to get a Cisco Valet Connector AM10 to work. It's one of those ZeroCD USB devices that is both storage and modem.

Using this link:

[http://linuxwireless.org/en/users/Drivers/rt2800usb/devices?highlight=%28am10%29](http://linuxwireless.org/en/users/Drivers/rt2800usb/devices?highlight=%28am10%29)

I filled out usb_modeswitch like this:

```
# Configuration for the usb_modeswitch package, a mode switching tool for
# USB devices providing multiple states or modes
#
# This file is evaluated by the wrapper script "usb_modeswitch_dispatcher"
# in /usr/sbin
# To enable an option, set it to "1", "yes" or "true" (case doesn't matter)
# Everything else counts as "disable"


# Disable automatic mode switching globally (e.g. to access the original
# install storage)

DisableSwitching=0


# Enable logging (results in a extensive report file in /var/log, named
# "usb_modeswitch_<interface-name>" (and probably others)

EnableLogging=0

# DAS edit 2011-07-20

# Cisco Valet Connector AM10
#
# Contributor: ohmysql (quite the n00b so please help if you see errors)

# No. 1
DefaultVendor= 0x1307
DefaultProduct= 0x0169
TargetVendor= 0x13b1
TargetProduct= 0x0031
#MessageEndpoint=0×01
MessageContent="5553424312345678c00000008000069f030000000000000000000000000000"
```And here's what I get when I run:

```
sudo usb_modeswitch -c /etc/usb_modeswitch.conf
```> Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found devices in default mode, class or configuration (1)
Accessing device 006 on bus 001 ...
Getting the current device configuration ...
 OK, got current device configuration (1)
Error: message endpoint not given or found. Aborting.
HELP!

---

### Post by chili555 on 2011-07-21
I know very little about usb_modeswitch, but I noticed your post went 15 hours without a peep, so maybe you'll accept a suggestion from an amateur. The error message is:> Error: [COLOR="Red"]message endpoint[/COLOR] not given or found. Aborting. However, 'message endpoint' is commented out in your .conf file:> <snip>
# No. 1
DefaultVendor= 0x1307
DefaultProduct= 0x0169
TargetVendor= 0x13b1
TargetProduct= 0x0031
[COLOR="Red"]**#**[/COLOR]MessageEndpoint=0×01
MessageContent="5553424312345678c00000008000069f030000000000000000000000000000"Does the behavior improve if you remove the hash?

---

### Post by ohmysql on 2011-07-21
> **chili555 said:**
> I know very little about usb_modeswitch, but I noticed your post went 15 hours without a peep, so maybe you'll accept a suggestion from an amateur. The error message is:However, 'message endpoint' is commented out in your .conf file:Does the behavior improve if you remove the hash?

Hello,

Thanks for the reply. No, I've tried removing the hash and changing the value to a few things found on the internet - 01, 05 and it still says it can't find the endpoint.

Thanks for the suggestion - I've been googling trying to figure out where the end point of USB devices is listed. If only I had windows so I could plug this in and spy on how it works there.

Maybe that would help.

David

---

### Post by chili555 on 2011-07-21
Dr. Chili is not one to curse, but....curses, now I have to learn about usb_modeswitch. I thought I had a clean getaway.> DefaultVendor= 0x[COLOR="Red"]1307[/COLOR]
DefaultProduct= 0x[COLOR="Red"]0169[/COLOR]
TargetVendor= 0x[COLOR="Red"]13b1[/COLOR]
TargetProduct= 0x[COLOR="Red"]0031[/COLOR]Where did these numbers come from? How does it relate to:```
sudo lsusb -v
```Feel free to redact the not-a-Cisco parts.

---

### Post by ohmysql on 2011-07-21
> **chili555 said:**
> Dr. Chili is not one to curse, but....curses, now I have to learn about usb_modeswitch. I thought I had a clean getaway.Where did these numbers come from? How does it relate to:```
sudo lsusb -v
```Feel free to redact the not-a-Cisco parts.

Chili, you're a lot classier than I am. I've been cursing since I purchased this thing.

More than anything, what you can do to help is just be someone to bounce ideas off. I mean if you Google something and find different things than me, that's even better.

Yeah, I've been trying to learn usb_modeswitch - I don't find it easy.

To answer your question, I got those target numbers from here:

[http://linuxwireless.org/en/users/Drivers/rt2800usb/devices?highlight=%28am10%29]("http://linuxwireless.org/en/users/Drivers/rt2800usb/devices?highlight=%28am10%29")

Here are the AM10 parts of that code. Note for some reason, there appears to be two devices?

```
 lsusb

Bus 001 Device 005: ID 1307:1169 Transcend Information, Inc. TS2GJF210 JetFlash 210 2GB
Bus 001 Device 003: ID 1307:0169 Transcend Information, Inc. 

ubuntu:~$ sudo lsusb -v

Bus 001 Device 005: ID 1307:1169 Transcend Information, Inc. TS2GJF210 JetFlash 210 2GB
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x1307 Transcend Information, Inc.
  idProduct          0x1169 TS2GJF210 JetFlash 210 2GB
  bcdDevice            1.00
  iManufacturer           1 Cisco Systems, Inc.
  iProduct                5 Cisco AM10 AM10
  iSerial                 3 000000000000D9
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower               98mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               8
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

Bus 001 Device 003: ID 1307:0169 Transcend Information, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x1307 Transcend Information, Inc.
  idProduct          0x0169 
  bcdDevice            1.00
  iManufacturer           1 Cisco Systems, Inc.
  iProduct                4 Cisco AM10 USB Hub
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower               98mA
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
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval               8
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             3
  wHubCharacteristic 0x0004
    Ganged power switching
    Compound device
    Ganged overcurrent protection
    TT think time 8 FS bits
  bPwrOn2PwrGood       50 * 2 milli seconds
  bHubContrCurrent     49 milli Ampere
  DeviceRemovable    0x0a
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0503 highspeed power enable connect
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered

```

---

### Post by chili555 on 2011-07-21
I think there ***are*** two devices; the flash drive part has the (Windows) software that drives the wireless device. As I understand usb_modeswitch, it's objective is to hop over the flash drive part and just use the wireless device with Linux drivers. I am confident that those smarter than me will hop in here and correct me. I will be grateful for the assistance.

You have:> # No. 1
DefaultVendor= 0x1307
DefaultProduct= 0x0169
TargetVendor= 0x13b1
TargetProduct= 0x0031
#MessageEndpoint=0×01
MessageContent="5553424312345678c00000008000069f03 0000000000000000000000000000" I'm guessing the Default pieces correspond to:> ID 1307:1169 Transcend Information, Inc. TS2GJF210 JetFlash 210 2GBThe first experiment I'd suggest is to change the Default parts to 0x1307 and 0x1169.

The Target parts you have as 0x13b1 and 0x0031. That doesn't correspond to anything that I see in lsusb. > ID 1307:0169 Transcend Information, Inc. I'd change the Target parts to 0x1307 and 0x0169.

I'd then run the command again:```
sudo usb_modeswitch -c /etc/usb_modeswitch.conf
```Look for clues as to what's happening under the hood and let's see what it says. If we're both lucky and smart today, it will work.

If we're not, then my next experiment would be to reverse what I suggested and try again.

---

### Post by ohmysql on 2011-07-21
> **chili555 said:**
> I think there ***are*** two devices; the flash drive part has the (Windows) software that drives the wireless device. As I understand usb_modeswitch, it's objective is to hop over the flash drive part and just use the wireless device with Linux drivers. I am confident that those smarter than me will hop in here and correct me. I will be grateful for the assistance.

You have:I'm guessing the Default pieces correspond to:The first experiment I'd suggest is to change the Default parts to 0x1307 and 0x1169.

The Target parts you have as 0x13b1 and 0x0031. That doesn't correspond to anything that I see in lsusb. I'd change the Target parts to 0x1307 and 0x0169.

I'd then run the command again:```
sudo usb_modeswitch -c /etc/usb_modeswitch.conf
```Look for clues as to what's happening under the hood and let's see what it says. If we're both lucky and smart today, it will work.

If we're not, then my next experiment would be to reverse what I suggested and try again.

W00t! Ok, we are one step closer. Thank you so much for the ideas. Here's the code that worked:

```
DefaultVendor= 0x1307
DefaultProduct= 0x1169
TargetVendor= 0x13b1
#0x1307
TargetProduct= 0x0031
#0x0169
#MessageEndpoint=0×05
MessageContent="5553424312345678c00000008000069f030000000000000000000000000000"
```
If you put in any other values for default vendor it doesn't work, and it doesn't seem to care much what you put for TargetVendor, (though that may prove to be quite important later...).

Here's the response it gives:

```
Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found devices in default mode, class or configuration (1)
Accessing device 005 on bus 001 ...
Getting the current device configuration ...
 OK, got current device configuration (1)
Using endpoints 0x01 (out) and 0x82 (in)
Using endpoints 0x01 (out) and 0x82 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached
```

Then it hangs there forever. BUT Linux doesn't claim there's a USB storage device plugged in there anymore. Well, at least my home menu doesn't have it listed on the side anymore. But, here are the contents of lsusb:

```
Bus 002 Device 003: ID 045e:007d Microsoft Corp. Notebook Optical Mouse
Bus 002 Device 002: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 1307:1169 Transcend Information, Inc. TS2GJF210 JetFlash 210 2GB
Bus 001 Device 003: ID 1307:0169 Transcend Information, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

So, nothing has changed there.

I've been following this tutorial.

[http://standy.blog.ugm.ac.id/2010/02/09/how-to-set-up-or-install-zte-mg880-usb-modem-in-ubuntu-jaunty-9-04/](http://standy.blog.ugm.ac.id/2010/02/09/how-to-set-up-or-install-zte-mg880-usb-modem-in-ubuntu-jaunty-9-04/)

The next step he says (assuming this device is acting like a modem) is to:

> [LEFT][COLOR=#000000][FONT=Times New Roman]Next,  you must modprobe your modem as usbserial into kernel … (different  method with other ubuntu version) with “sudo gedit /boot/grub/menu.lst”  in terminal.[/FONT][/COLOR][/LEFT]
 [LEFT][COLOR=#000000][FONT=Times New Roman]Compare, add and edit yours to be like this :[/FONT][/COLOR][/LEFT]


menu.lst is blank, so I'm not quite sure what to do. Does that mean to add something in /etc/modules?

I think I'm one step closer.

---

### Post by chili555 on 2011-07-21
I don't think you have a modem; I think you have an ordinary wireless device that connectes to the signal from your wireless router, yes? No? I think our next step is to figure out the correct driver and load it and see if we can bring it to life. It is late here, so I will attack this tomorrow. I suggest you Google for 1307:0169. Early hints suggest the Ralink RT3072 chipset, but I am not yet persuaded.

---

### Post by ohmysql on 2011-07-22
Check out this thread:

[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=635&postdays=0&postorder=asc&start=15](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=635&postdays=0&postorder=asc&start=15)

Wow... they've put a lot of work in and not necessarily gotten very far.

---

### Post by chili555 on 2011-07-22
They've gotten as far as any I've been able to find on the web; that is, as far as you and not very far at all...sadly. My search for a wireless driver for 1307:0169 comes up pretty sparse; mostly coming back to valiant but fruitless attempts to get usb_modeswitch going.

What is in the flash storage part? Does it automount to your desktop if you insert it and just wait for it? Is it a Windows .exe? Maybe we can unravel it and see what driver it thinks it wants from the .inf file.

We could compile RT3072 and add the device ID to it and see what happens. We could make history!

---

### Post by ohmysql on 2011-07-23
> **chili555 said:**
> They've gotten as far as any I've been able to find on the web; that is, as far as you and not very far at all...sadly. My search for a wireless driver for 1307:0169 comes up pretty sparse; mostly coming back to valiant but fruitless attempts to get usb_modeswitch going.

What is in the flash storage part? Does it automount to your desktop if you insert it and just wait for it? Is it a Windows .exe? Maybe we can unravel it and see what driver it thinks it wants from the .inf file.

We could compile RT3072 and add the device ID to it and see what happens. We could make history!

Hi Chili,

I like your attitude. Because no one's ever done this before, we can make history, we can help the next person foolish enough to purchase this hardware, we can live our open source values. Me, I was thinking "no one's ever done this before, we're screwed."

I appreciate your hanging in there.

Yes, the flash storage automounts if you plug it in. Ubuntu says "oh a new storage device". Then when I run usb_modeswitch the storage device disappears, which is really great. I've installed a driver - maybe it's the wrong one? Here's the driver I tried to install: 2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO

I think I did make and make install.

When I type:

```
locate 3572
``` it finds a driver location. Let me know if I need to do more, I've never compiled a driver before. . Assuming Ubuntu is recognizing this thing as a wireness device, do you know what the next step would be?

Totally, like, oh my SQL!!

---

### Post by chili555 on 2011-07-23
> When I type:

Code:

locate 3572

it finds a driver location. Does it find /lib/modules/..etc../rt3572sta.ko? If not, we have more work to do.

We hope the driver recognizes the device, so let's see if the driver sees it:```
modinfo rt3572sta | grep 0169
```I must confess, I already know the answer and I'm leading you to an understanding of the next round of surgery we're going to perform.> I like your attitude. Because no one's ever done this before, we can make history, we can help the next personIt's easy to do when my wireless works fine and I have all the time in the world!

Of course, you could return the device and buy something that works out of the box and be happy. But then we'd have to live with the shame that the mystery is still unsolved and Ballmer is laughing all the way to the bank. Oh, the humanity!!!> Yes, the flash storage automounts if you plug it in.When you right-click the icon that appears on your desktop and select Open, what's in there?

---

### Post by ohmysql on 2011-07-23
> **chili555 said:**
> Does it find /lib/modules/..etc../rt3572sta.ko? If not, we have more work to do.

We hope the driver recognizes the device, so let's see if the driver sees it:```
modinfo rt3572sta | grep 0169
```I must confess, I already know the answer and I'm leading you to an understanding of the next round of surgery we're going to perform.It's easy to do when my wireless works fine and I have all the time in the world!

Of course, you could return the device and buy something that works out of the box and be happy. But then we'd have to live with the shame that the mystery is still unsolved and Ballmer is laughing all the way to the bank. Oh, the humanity!!!When you right-click the icon that appears on your desktop and select Open, what's in there?

Ah yes, I forgot to answer one of your questions, thank you.

Yes when I do locate 3572 it returns:

```
/lib/modules/2.6.38-10-generic/kernel/drivers/net/wireless/rt3572sta.ko
```

When I do:

```
modinfo rt3572sta | grep 0169
```

It doesn't find anything. But when I do:

```
modinfo rt3572sta | grep 1169
```

It returns:

```
alias:          usb:v1307p1169d*dc*dsc*dp*ic*isc*ip*
```

I'm not ashamed to tell you I have no idea what that means, but I hope it's good.

I am very much ok with you knowing the answer and leading me to it! I'd love to learn how to do this myself and the principles behind it, so thank you.

To answer your other question about automount, what's in the folder are basically the windows and Mac drivers.

There's a windows setup executable, documentation, mac setup. And then there's a folder called drivers, which may be what you're driving at. Well, just in case, and not wanting to get caught flat-footed, I took ndiswrapper and converted the Windows Vista driver I found. Not sure how well that worked, though. When I look in System Settings > Windows Wireless Drivers it does list netr28ux.inf (the file that was in there), so that can't be all bad.

So following the steps we did earlier, I did locate netr28ux.inf which returns:

```
/etc/ndiswrapper/netr28ux/netr28ux.inf
```

But when I do:

```
modinfo netr28ux | grep 1169
```

It returns:

```
ERROR: modinfo: could not find module netr28ux
```

I'm experiencing one of those sneaking Linux-newbie suspicions that modinfo should have found that driver. But I'll be curious what you think and what the next step might be.

---

### Post by chili555 on 2011-07-23
> I took ndiswrapper and converted the Windows Vista driver I found. Not sure how well that worked, It won't work because ndiswrapper wants the XP driver. Here is a snip from *man ndiswrapper-1.9*:> DESCRIPTION
       ndiswrapper is two parts: user space tool that is used to intall ***Windows XP  drivers*** and kernel module to load the Windows XP drivers. Both are called ndiswrapper.The way to see if ndiswrapper is doing the job is:```
ndiswrapper -l
```That's a lower-case L for 'list.' Also check:```
dmesg | grep ndis
```Using the Vista driver, dmesg ought to be pretty unhappy.

I suggest you try to point usb_modeswitch at rt3572sta and see if it comes to life. Since ndiswrapper conflicts and is the wrong .inf anyway, I suggest you erase it in any case:```
sudo ndiswrapper -e netr28ux
```I'd love to read the XP .inf file, because I think it gives us clues as to the intended correct driver. Can you copy it to your desktop, right-click it and select Compress, zip it and attach it to your reply using the paperclip tool at the top of the reply box?> But when I do:

Code:

modinfo rt3572sta | grep 1169

It returns:

Code:

alias:          usb:v1307p1169d*dc*dsc*dp*ic*isc*ip*

I'm not ashamed to tell you I have no idea what that means, but I hope it's good.
I think it means that the underlying wireless device is actually 1307:1169 and we have the correct driver.

Now, do you know how to inform usb_modeswitch that we wish to use rt3572sta? I wonder if you just modprobe it and then run your command.```
sudo modprobe rt3572sta
sudo usb_modeswitch -c /etc/usb_modeswitch.conf
```I am anxiously awaiting your report. I hate to admit it, but this is fun.

---

### Post by ohmysql on 2011-07-24
> **chili555 said:**
> It won't work because ndiswrapper wants the XP driver. Here is a snip from *man ndiswrapper-1.9*:The way to see if ndiswrapper is doing the job is:```
ndiswrapper -l
```That's a lower-case L for 'list.' Also check:```
dmesg | grep ndis
```Using the Vista driver, dmesg ought to be pretty unhappy.

I suggest you try to point usb_modeswitch at rt3572sta and see if it comes to life. Since ndiswrapper conflicts and is the wrong .inf anyway, I suggest you erase it in any case:```
sudo ndiswrapper -e netr28ux
```I'd love to read the XP .inf file, because I think it gives us clues as to the intended correct driver. Can you copy it to your desktop, right-click it and select Compress, zip it and attach it to your reply using the paperclip tool at the top of the reply box?I think it means that the underlying wireless device is actually 1307:1169 and we have the correct driver.

Now, do you know how to inform usb_modeswitch that we wish to use rt3572sta? I wonder if you just modprobe it and then run your command.```
sudo modprobe rt3572sta
sudo usb_modeswitch -c /etc/usb_modeswitch.conf
```I am anxiously awaiting your report. I hate to admit it, but this is fun.

Hi Chili,

Thanks for the reply. I'm definitely glad to hear you're having fun - the help is huge for me and I'm glad it's a nice challenge for you. I agree - if we can conquer this, there would probably be a few grateful open sourcers out there.

I ran this:

```
sudo ndiswrapper -e netr28ux
```So that driver is gone for the moment. I went to the Cisco website and downloaded the XP driver (which I've attached here) and then ran ndiswrapper on it. For me, that just means browsing to the directory and doing:
```

sudo ndiswrapper -m
sudo ndiswrapper -mi
sudo ndiswrapper -ma
sudo ndiswrapper -i rt2870.inf
```Afterwards, when I ran:

```
ndiswrapper -l
```rt2870 did show up so we're good on that front. On the other hand, when I run:

```
dmesg | grep ndis
modinfo rt2870sta | grep 0031
modinfo rt2870sta | grep 13b1
modinfo rt2870sta | grep 1169
modinfo rt2870sta | grep 0169
modinfo rt2870sta | grep 1307

``` I get nothing for any of these commands. I'll be really curious what you think of the XP driver... it seems to be looking for an entirely different device!

I am also not sure how to point usb_modprobe at the correct driver. But the admin here posted an interesting response recently that might explain why:

[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=635&postdays=0&postorder=asc&start=15](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=635&postdays=0&postorder=asc&start=15)

He  suggests I change the udev rules instead of bothering with USB modeswitch.

Also, I tried the modprobe command you suggested and got an error:
```

sudo modprobe rt2870sta
FATAL: Error inserting rt2870sta (/lib/modules/2.6.38-10-generic/kernel/drivers/staging/rt2870/rt2870sta.ko): Device or resource busy
```Do you have any idea why modprobe wouldn't work?

I'll be curious what you think of the XP driver. I'm a little stumped, but I think I'm yet another step closer (and I'm realizing this may be a 22 step process...)

---

### Post by chili555 on 2011-07-24
Man! This is awesome! The driver genie in me (or so I assume myself to be) is salivating. 

I think the modprobe failed either, in order of likeliness, because another driver, ndiswrapper, was driving the USB wireless device, or that it was already loaded. You could check:```
sudo modprobe rt2870sta
lsmod | grep rt2
```The rt2870 family is actually subdivided in Linux to several subfamilies; our old pal rt3572sta is one of them. You can see lots of referneces to 2870 in the source code. Coincidentally, I had two discussions going last evening on this forum about that very subject.

rt2870sta is the native Linux driver; it is *not *the same as ndiswrapper, although they have similar names. Once you install ndiswrapper to use Windows XP drivers, all the rules change. The commands become 'ndiswrapper -<some_switch>.' The modinfo, etc. commands are for native drivers only, not for ndiswrapper.

Here is a relevant line from the .inf file. I have highlighted the most interesting part:> Cisco]

; DisplayName               Section                 DeviceID

; -----------               -------                 --------

%**cisco_am10.DeviceDesc**%     = cisco_am10.ndi,            USB\VID_[COLOR="Red"]13B1[/COLOR]&PID_[COLOR="Red"]0031[/COLOR]

%linksys_AG_v2.DeviceDesc%  = linksys_ae1000.ndi,        USB\VID_13B1&PID_002FWhen you run:```
sudo usb_modeswitch -c /etc/usb_modeswitch.conf
sudo modprobe ndiswrapper
ndiswrapper -l
```Does it show the device 13b1:0031 is present? Does the device start? Spark? Smoke? Light up??

My current thinking is that once we get the device to start and connect once, we'll tweak a couple of files to make it run automagically during boot so that you log in to a working connection.

---

### Post by jasonr2210 on 2011-07-25
I am also interested to see if you get this working. I just installed ubuntu as dual boot with windows 7 and I am also using the Cisco valet connector for wireless. If you manage to get this working, detailed instructions for a buntu-noob would be awesome

---

### Post by chili555 on 2011-07-25
We will do just that. From my internet searches, I believe that there are others trying to get this device going and so far not successfully. 

I have just one caveat. There are working out of the box USB wireless devices that you can buy for a few dollars. You could be connected and happy in a short time. ohmysql and I are working on this because we don't know when to quit and we never say never. I feel very good about our chances but I have no certainty that it will work. I am 100% certain that *I* will work.

If you want wireless connectivity and want it now, I'd look elsewhere. If you love a mystery, stay tuned.

---

### Post by chili555 on 2011-07-25
@ohmysql--

If you want to attack the udev piece of the puzzle as mentioned here: [http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=635&postdays=0&postorder=asc&start=15](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=635&postdays=0&postorder=asc&start=15)

This is what I'd do:```
sudo su
gedit /etc/modules
```Add a single line:```
ndiswrapper
```That will pre-load ndiswrapper at boot. Proofread carefully, save and close gedit. Now do```
gedit /etc/udev/rules.d/70-persistent-net.rules
```Add a new entry: ```
# USB device 0x13B1:0x0031 (ndiswrapper)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="[COLOR="Red"]??:??:??:??:??[/COLOR]", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

```Have you found the MAC address of the underlying wireless device after you run usb_modeswitch and the storage part disappears? We need to find and add that. It may be printed on the device.

---

### Post by ohmysql on 2011-07-25
> **chili555 said:**
> Man! This is awesome! The driver genie in me (or so I assume myself to be) is salivating. 

I think the modprobe failed either, in order of likeliness, because another driver, ndiswrapper, was driving the USB wireless device, or that it was already loaded. You could check:```
sudo modprobe rt2870sta
lsmod | grep rt2
```Just so you know, I ran this code and it said the driver was busy. When you do ```
lsmod | grep rt3
```[/quote] When I run this code it comes up with the rt3572sta driver. So I think that's why the 2870 isn't installing with sudo modprobe. I guess we can play with that later to see which driver works best. I think you'll agree with that by the time I finish replying to this thread.

> The rt2870 family is actually subdivided in Linux to several subfamilies; our old pal rt3572sta is one of them. You can see lots of referneces to 2870 in the source code. Coincidentally, I had two discussions going last evening on this forum about that very subject.

Good to know.
> 
rt2870sta is the native Linux driver; it is *not *the same as ndiswrapper, although they have similar names. Once you install ndiswrapper to use Windows XP drivers, all the rules change. The commands become 'ndiswrapper -<some_switch>.' The modinfo, etc. commands are for native drivers only, not for ndiswrapper. Also very good to know. That said, I am able to do sudo modprobe ndiswrapper, and now if I do lsmod | grep ndiswrapper it appears. Not sure what that means or that's how to use ndiswrapper. But I have a feeling we'll need to play with udev first.

> Here is a relevant line from the .inf file. I have highlighted the most interesting part: I'm so glad you thought to look up the ports we should be seeing. I didn't even think of that. It's crazy that 1169 and 0169 don't even appear anywhere in the file. That makes it clear we have some udeving to do before we can use this ndiswrapped file.

> When you run:```
sudo usb_modeswitch -c /etc/usb_modeswitch.conf
sudo modprobe ndiswrapper
ndiswrapper -l
```Does it show the device 13b1:0031 is present? Does the device start? Spark? Smoke? Light up??

My current thinking is that once we get the device to start and connect once, we'll tweak a couple of files to make it run automagically during boot so that you log in to a working connection.

Great, sounds like a plan to me. So let me tell you what my system sees and then I'll reply to your other post.

Right now when I do ndiswrapper -l (lower case L) I get:

```
rt2870 : driver installed
``` So far so good.
When I boot up and do lsusb I get:

```
Bus 001 Device 005: ID 1307:1169 Transcend Information, Inc. TS2GJF210 JetFlash 210 2GB
Bus 001 Device 004: ID 1307:0169 Transcend Information, Inc. 
```
When I run:

```
sudo usb_modeswitch -c /etc/usb_modeswitch.conf

###Here is the config file:

# Configuration for the usb_modeswitch package, a mode switching tool for
# USB devices providing multiple states or modes
#
# This file is evaluated by the wrapper script "usb_modeswitch_dispatcher"
# in /usr/sbin
# To enable an option, set it to "1", "yes" or "true" (case doesn't matter)
# Everything else counts as "disable"


# Disable automatic mode switching globally (e.g. to access the original
# install storage)

DisableSwitching=0


# Enable logging (results in a extensive report file in /var/log, named
# "usb_modeswitch_<interface-name>" (and probably others)

EnableLogging=1

# oms edit 2011-07-20

# Cisco Valet Connector AM10
#
# Contributor: ohmysql (quite the n00b so please help if you see errors)

# No. 1
DefaultVendor= 0x1307
DefaultProduct= 0x1169
TargetVendor= 0x13b1
#0x1307

TargetProduct= 0x0031
#0x0169

#MessageEndpoint=0×05

MessageContent="55534243d84c04820000000000000afd000300241300000000000000000000"
MessageContent2="55534243d84c04820000000000000afd000110732400000000000000000000"
NeedResponse=1

CheckSuccess=3

#Found these numbers here: http://linuxwireless.org/en/users/Drivers/rt2800usb/devices?highlight=%28am10%29
#DefaultVendor= 0x13b1
#DefaultProduct= 0x0031
```It seems to work, the USB device vanishes. But when I run lsusb again, I get:

```
Bus 001 Device 005: ID 1307:1169 Transcend Information, Inc. TS2GJF210 JetFlash 210 2GB
Bus 001 Device 004: ID 1307:0169 Transcend Information, Inc.
``` A.k.a., the same thing.

So nothing happens with the wireless. The ndiswrapper doesn't recognize it because it's looking for 13b1x0031 and I still have 1307x1169. I'm not totally sure why rt3572sta isn't finding anything, because supposedly that's the USB device it's looking for. Let me reply to your other message. Let me know if I seem to be missing anything. But the consensus seems to be that udev will have the answer to this.

OMS

---

### Post by ohmysql on 2011-07-25
> **chili555 said:**
> @ohmysql--

If you want to attack the udev piece of the puzzle as mentioned here: [http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=635&postdays=0&postorder=asc&start=15](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=635&postdays=0&postorder=asc&start=15)

This is what I'd do:```
sudo su
gedit /etc/modules
```Add a single line:```
ndiswrapper
```That will pre-load ndiswrapper at boot. Proofread carefully, save and close gedit.
Done. I'd added rt3572sta in the /etc/modules files, so I commented that out.
> Now do```
gedit /etc/udev/rules.d/70-persistent-net.rules
```Add a new entry: ```
# USB device 0x13B1:0x0031 (ndiswrapper)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="[COLOR=Red]??:??:??:??:??[/COLOR]", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

```Have you found the MAC address of the underlying wireless device after you run usb_modeswitch and the storage part disappears? We need to find and add that. It may be printed on the device.Ok, I've done all this, I changed the udev rules and added the MAC address, which was printed on the back of the device. I'm going to restart and we'll see what happens.

Hmm, nothing so far. It's showing up as a USB device. Probably I need to stop it from doing that. And it's still under 1307x1169. Any thoughts on the next step?

Also, now that I'm plugged into Ethernet, that shouldn't prevent me from seeing wireless networks, right?

---

### Post by chili555 on 2011-07-25
We need to work on two issues, aside from udev as I mentioned above. First, we can use the native driver rt3572sta or ndiswrapper; *not both*. I happen to know, based on many years of experience, that the rt3572sta, built from source code, has some minor problems. I expect that it would, since it is built for Ubuntu, Mint, Fedora, RHEL, Suse, WhathaveyouLinux, etc. It's a one size mostly almost fits all. That's fine if that's all the driver we have.

You, on the other hand, have the .inf and .sys files right off of the device and have installed ndiswrapper. I would expect it to not only work, but work a bit better than rt3572sta. Therefor, I suggest you blacklist rt3572sta. It can be reversed at any time if we decide to try the native driver instead. Please do: ```
sudo su
echo "blacklist rt3572sta" >> /etc/modprobe.d/blacklist.conf
rmmod -f rt3572sta
exit
```The second issue we (read: you, since you have the device) need to work on is actually getting the flip-flop to stop seeing a USB storage device in lsusb and start seeing a wireless device enumerated 13B1:0031. I assume you fine-tune your /etc/usb_modeswitch.conf file and after you run the command, the storage device goes away and the wireless device comes out of the bushes. I wonder if the 
TargetVendor= 0x13b1 and
TargetProduct= 0x0031 are still in your .conf file. > Also, now that I'm plugged into Ethernet, that shouldn't prevent me from seeing wireless networks, right? No. It will probably prevent you from connecting, but not seeing.

At this point, I'd suggest you fine tune the .conf file and see if we can get the wireless device to appear. If so, ndiswrapper should grab it and run.

Are you around for the next few hours so we can bat this back and forth?

---

### Post by ohmysql on 2011-07-25
> **chili555 said:**
> We need to work on two issues, aside from udev as I mentioned above. First, we can use the native driver rt3572sta or ndiswrapper; *not both*. I happen to know, based on many years of experience, that the rt3572sta, built from source code, has some minor problems. I expect that it would, since it is built for Ubuntu, Mint, Fedora, RHEL, Suse, WhathaveyouLinux, etc. It's a one size mostly almost fits all. That's fine if that's all the driver we have.

You, on the other hand, have the .inf and .sys files right off of the device and have installed ndiswrapper. I would expect it to not only work, but work a bit better than rt3572sta. Therefor, I suggest you blacklist rt3572sta. It can be reversed at any time if we decide to try the native driver instead. Please do: ```
sudo su
echo "blacklist rt3572sta" >> /etc/modprobe.d/blacklist.conf
rmmod -f rt3572sta
exit
``` This is done, thanks for the suggestion on the driver.

> The second issue we (read: you, since you have the device) need to work on is actually getting the flip-flop to stop seeing a USB storage device in lsusb and start seeing a wireless device enumerated 13B1:0031. I assume you fine-tune your /etc/usb_modeswitch.conf file and after you run the command, the storage device goes away and the wireless device comes out of the bushes. I wonder if the 
TargetVendor= 0x13b1 and
TargetProduct= 0x0031 are still in your .conf file. No. It will probably prevent you from connecting, but not seeing.I agree - I have no idea why we can't get those USB vendor and product values to appear. Yes, those TargetVendor and TargetProduct lines are still there. I can't find any evidence that they've done anything.

Also, for the record, that may be one advantage to the rt3572sta file, that it appears to be looking for 1307x1169. But that said, although after running usb_modeswitch the USB storage device disappears from my desktop, lsusb still has it listed as a USB storage device at 1307x1169. Hmm, that's a part I do not understand.

> At this point, I'd suggest you fine tune the .conf file and see if we can get the wireless device to appear. If so, ndiswrapper should grab it and run.Do you have a sense of why the person from the draisberghof.de forum suggested that modeswitch is not appropriate for this task? Do you think it's possible to assign a new USB product/vendor value through udev?

Just so know you, the usb_modeswitch code I posted a few posts ago is still the one I'm using. You'll note I have logging switched to on. If I go and read the log, this is what it says:
```

SB_ModeSwitch log from Mon Jul 25 21:42:31 EDT 2011

raw args from udev: /1-4.1:1.0

Using global config file: /etc/usb_modeswitch.conf
Bus ID for device not given by udev.
 Trying to determine it from kernel name (1-4.1:1.0) ...
USB dir exists: /sys/bus/usb/devices/1-4.1
----------------
USB values from sysfs:
  manufacturer    Cisco Systems, Inc.
  product    Cisco AM10 AM10
  serial    000000000000D9
----------------
Found packed config collection /usr/share/usb_modeswitch/configPack.tar.gz
Searching overriding entries named: /etc/usb_modeswitch.d/1307:1169*
Aargh! Config file missing for 1307:1169! Exiting
```

I'm having another strange Linux-n00b/b00b intuitions that I may have stumbled upon something important. I've been looking in /sys/bus/usb/devices/1-4.1 but I don't understand what's in this directory.

> Are you around for the next few hours so we can bat this back and forth?Clearly I wasn't and I'm about go to bed. But I'll be up early tomorrow and checking e-mail throughout the day. I just moved to Montreal so I'm doing a lot of move in stuff (including trying to get this wireless card to work :)). I'm having fun with this too - though I confess I feel a greater sense of not-having-a-choice.

OMS

---

### Post by chili555 on 2011-07-26
Montreal? I hearda that place! They got that rainbow money up there, and they speak the Franglish: "S'il vous plait, donnez moi deux tie-rod ends." OK, seriously...

I had a look in the /usr/share/usb_modeswitch/configPack.tar.gz file and it looks like this:> -rw-r--r-- root/root       304 2011-02-26 13:52 19d2:0110
-rw-r--r-- root/root       274 2010-06-20 18:00 19d2:0115
-rw-r--r-- root/root       491 2010-06-20 18:00 19d2:1001
-rw-r--r-- root/root       287 2010-06-20 18:00 19d2:1007
-rw-r--r-- root/root       287 2010-06-20 18:00 19d2:1009
-rw-r--r-- root/root       491 2010-08-16 18:00 19d2:1013
-rw-r--r-- root/root       524 2011-02-26 12:52 19d2:2000
-rw-r--r-- root/root       276 2010-06-20 18:00 19d2:fff5
-rw-r--r-- root/root       268 2010-06-20 18:00 19d2:fff6
-rw-r--r-- root/root       411 2010-12-22 18:17 1a8d:1000The first part are obviously permission and owner. The three-digit number I don't understand at all. The date (and time??) seems to be for reference and I doubt has anything to do with operation. The last part is undoubtedly the usb.id for the device; in your case,  1307:1169. I don't think it would be hard to unpack the file, add the device id and tar.gz it again...if we only knew what to put in.

I think it looks for a separate configuration file: /etc/usb_modeswitch.d/1307:1169 when it can't find your device in /usr/share/usb_modeswitch/configPack.tar.gz. Of course, it can't find one, because we haven't written one; we don't have a clue as to what goes in there. I wonder if Josh over at draisberghof.de forum could offer a suggestion.> Do you have a sense of why the person from the draisberghof.de forum suggested that modeswitch is not appropriate for this task? Do you think it's possible to assign a new USB product/vendor value through udev?I do not. If I understand anything about usb_modeswitch, I think you have to get the Linux kernel to skip over the storage part and see and then be able to use the wireless part. I have no idea how udev could accomplish this without modeswitch. See next post.> I've been looking in /sys/bus/usb/devices/1-4.1 but I don't understand what's in this directory.What *is* in there?```
ls /sys/bus/usb/devices/1-4.1
```

---

### Post by chili555 on 2011-07-26
Ahhh! I see it now. He says:> I can already tell you that usb_modeswitch is not the right tool to load the driver.

That would be "udev". It looks at a list of rules everytime a device on the system is changed (added / removed). It can check certain things like USB IDs but also much more sophisticated properties, and trigger any action you want if all the conditions in the "rule" are met.

usb_modeswitch is using this for an automatic run each time a known device is plugged. You can just define a new rule to load the driver automatically after the switching has happened.

Re-reading the whole topic again - did you get that "13b1:0031" device at some point? Maybe the vanishing of the storage is not enough to make the wireless device appear ...

I'll have annother look at that log no. 5. What he is saying is the usb_modeswitch is not the way to call the wireless driver; in our case, ndiswrapper. He is saying that udev is the process to attach the driver to the underlying wireless device. What udev is saying, roughly, is, if we see anyone walking around named "13b1:0031," introduce them to ndiswrapper and let them go play together. I believe when you amended /etc/udev/rules.d/70-persistent-net.rules, you took care of that part.

I remain optimistic that as soon as you get the underlying wireless device to appear, that we'll be all set.

Please see attached.

I wonder if I can walk in to my local Walmart and say, "S'il vous plait, donnez moi un Cisco Valet."

---

### Post by chili555 on 2011-07-26
I suggest, as a trial to see what the logs say, that you do:```
sudo gedit /etc/usb_modeswitch.d/1307:1169
```Add one line:```
[SIZE="3"]-rw-r--r-- root/root 287 2010-06-20 18:00  1307:1169[/SIZE]
```Proofread, save and close gedit. Note the first part has double minus after the Rs.

---

### Post by ohmysql on 2011-07-26
> **chili555 said:**
> Montreal? I hearda that place! They got that rainbow money up there, and they speak the Franglish: "S'il vous plait, donnez moi deux tie-rod ends." OK, seriously... It's all true :)

> I had a look in the /usr/share/usb_modeswitch/configPack.tar.gz file and it looks like this:The first part are obviously permission and owner. The three-digit number I don't understand at all. The date (and time??) seems to be for reference and I doubt has anything to do with operation. The last part is undoubtedly the usb.id for the device; in your case,  1307:1169. I don't think it would be hard to unpack the file, add the device id and tar.gz it again...if we only knew what to put in.As far as I can tell, my tar doesn't look like that. Well anyway, yes, and it looks like from the log that we can add a 1307:1169 file somewhere else, that we don't need to add it to the .tar.

> I think it looks for a separate configuration file: /etc/usb_modeswitch.d/1307:1169 when it can't find your device in /usr/share/usb_modeswitch/configPack.tar.gz. Of course, it can't find one, because we haven't written one; we don't have a clue as to what goes in there. I wonder if Josh over at draisberghof.de forum could offer a suggestion.I do not. If I understand anything about usb_modeswitch, I think you have to get the Linux kernel to skip over the storage part and see and then be able to use the wireless part. I have no idea how udev could accomplish this without modeswitch. See next post.What *is* in there?```
ls /sys/bus/usb/devices/1-4.1
```

I agree. Here are the contents of that folder by the way:

```
1-4.1:1.0            bDeviceSubClass     configuration  idProduct     remove
authorized           bmAttributes        descriptors    idVendor      serial
avoid_reset_quirk    bMaxPacketSize0     dev            manufacturer  speed
bcdDevice            bMaxPower           devnum         maxchild      subsystem
bConfigurationValue  bNumConfigurations  devpath        power         uevent
bDeviceClass         bNumInterfaces      driver         product       urbnum
bDeviceProtocol      busnum              ep_00          quirks        version
```

---

### Post by ohmysql on 2011-08-02
[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?p=4912#4912](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?p=4912#4912)

We finally got it working on this thread. Totally awesome. I'm writing using the AM10 right now on 11.04.

oh my SQL!!!

---

### Post by chili555 on 2011-08-03
Awesome! Great work.

---

### Post by ohmysql on 2011-08-18
I would say if you get the latest version of usb_modeswitch it will find a wireless device. But we still have driver issues. Not sure if I should mark this as solved or not.

I'm pretty tempted to open a new thread just dedicated to figuring out which driver is which.

---

### Post by chili555 on 2011-08-18
The correct driver is either ndiswrapper and the included Windows XP .inf file or the Linux driver rt3572sta. As the man at the corner store says, you pays yer money and you takes yer chances. If it's working satisfactorily with ndiswrapper now, then that's a prefectly valid method. It's easy enough to temporarily try the Linux driver:```
sudo ifconfig wlan0 down
sudo rmmod -f ndiswrapper
sudo modprobe rt3572sta
iwconfig
```Did a wireless interface, ra0 perhaps, get created? Can you connect? Is it better or worse?

---

### Post by ljmartz on 2012-08-16
I am a new Ubuntu user...so new that I know enough to get lost but not how to find my way home!

I have installed Ubuntu 12.04 in dual-boot mode on my laptop that is also loaded w/ Vista (I will not detail the steps it took to complete that process.  Lets just say at this point, based on the installation process, I'm not convinced that Ubuntu is any better than Vista).  After finally getting Ubuntu loaded, updated, and driver for my wifi card installed (using an Ethernet connection) I have absolutely no wireless connection.

I am using a Cisco Valet router that is hard wired to my desktop and on my laptop (booted in Vista) I connect wirelessly.  The Cisco Valet has a USB setup key (not the AM10) that I ran to set up connection on the laptop the first time.  As with the AM10, the setup key is only supported by Windows and Mac.

Here is my question: will the wonderful work that you accomplished here work for me or do I need to go down a different road?

---

### Post by ohmysql on 2012-08-16
> **ljmartz said:**
> I am a new Ubuntu user...so new that I know enough to get lost but not how to find my way home!

I have installed Ubuntu 12.04 in dual-boot mode on my laptop that is also loaded w/ Vista (I will not detail the steps it took to complete that process.  Lets just say at this point, based on the installation process, I'm not convinced that Ubuntu is any better than Vista).  After finally getting Ubuntu loaded, updated, and driver for my wifi card installed (using an Ethernet connection) I have absolutely no wireless connection.

I am using a Cisco Valet router that is hard wired to my desktop and on my laptop (booted in Vista) I connect wirelessly.  The Cisco Valet has a USB setup key (not the AM10) that I ran to set up connection on the laptop the first time.  As with the AM10, the setup key is only supported by Windows and Mac.

Here is my question: will the wonderful work that you accomplished here work for me or do I need to go down a different road?

Hmm, probably won't help you much! What's the model number of the WiFi card you're using?

You might want to make an account here and ask him to help you. But we'll see:

[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?p=6057#6057](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?p=6057#6057)

---

### Post by ljmartz on 2012-08-16
> Hmm, probably won't help you much! What's the model number of the WiFi card you're using?According to the lspci -v command I am running a Broadcom Corp BCM 4311 802.33b/g, Subsystem: Dell Wireless 1390 Wlan Mini-card.

According to [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom)
the 4311 is supported but there is no mention of the Dell Wireless 1390 Mini-Card.

I did find a helpful piece of info in the above referenced link that states that on dual-boot machines that the wireless card has to be active in Windows before booting to Ubuntu or the card will not work in Ubuntu.  After trying this technique, I at least have the wifi light lit on my laptop, but the network options still do not show any wireless network options.

---

### Post by chili555 on 2012-08-16
> **ljmartz said:**
> According to the lspci -v command I am running a Broadcom Corp BCM 4311 802.33b/g, Subsystem: Dell Wireless 1390 Wlan Mini-card.

According to [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom)
the 4311 is supported but there is no mention of the Dell Wireless 1390 Mini-Card.

I did find a helpful piece of info in the above referenced link that states that on dual-boot machines that the wireless card has to be active in Windows before booting to Ubuntu or the card will not work in Ubuntu.  After trying this technique, I at least have the wifi light lit on my laptop, but the network options still do not show any wireless network options.If you'd like to get your Broadcom working, please post a new thread including:```
lspci -nn | grep 0280
rfkill list all
dmesg | grep b43
```I'll be happy to help.

---

### Post by ljmartz on 2012-08-16
> If you'd like to get your Broadcom working, please post a new thread including: 	Code:
 	lspci -nn | grep 0280 rfkill list all dmesg | grep b43


New thread in this forum?

---

### Post by chili555 on 2012-08-16
> **ljmartz said:**
> New thread in this forum?Yes, please.

---

### Post by maihoaomv on 2012-12-31
I've read through this post and a couple others and I'm still confused. Everything I've tried here hasn't worked. Did anyone get this thing to work?

The device I have works with win 7, win xp, linux mint 13 and linux mint 14 pretty much plug-n-play so I know the device is working.  I'm trying  to get it to work on a headless (non gui) nas device (seagate goflex home) that has debian squeeze installed. The problem is it has an ARM processor (marvell) rather than an i386/i686 processor which, I suspect, would not be able to load and run a widows driver. 

So I'm lost as to how go about what steps I need to take to get it to work. 
modprobe -l indicates the following 5 kernel modules are loaded
> 
root@GoFlexHome:/home/maihoa# modprobe -l |grep rt2800
kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
kernel/drivers/net/wireless/rt2x00/rt2800usb.ko

root@GoFlexHome:/home/maihoa# modprobe -l |grep ndis
kernel/drivers/net/wireless/rndis_wlan.ko
kernel/drivers/net/usb/rndis_host.ko
When I try to run usb_modeswitch I get an error

What am I missing? Can anyone help me with this? I realize I'm not running ubuntu. Any ideas or thoughts other than it can't be done would be appreciated.

---

### Post by ohmysql on 2013-01-02
> **maihoaomv said:**
> I've read through this post and a couple others and I'm still confused. Everything I've tried here hasn't worked. Did anyone get this thing to work?

The device I have works with win 7, win xp, linux mint 13 and linux mint 14 pretty much plug-n-play so I know the device is working.  I'm trying  to get it to work on a headless (non gui) nas device (seagate goflex home) that has debian squeeze installed. The problem is it has an ARM processor (marvell) rather than an i386/i686 processor which, I suspect, would not be able to load and run a widows driver. 

So I'm lost as to how go about what steps I need to take to get it to work. 
modprobe -l indicates the following 5 kernel modules are loaded
When I try to run usb_modeswitch I get an error

What am I missing? Can anyone help me with this? I realize I'm not running ubuntu. Any ideas or thoughts other than it can't be done would be appreciated.

 A couple things to check - are you running the latest version of mode_switch? I'd be stunned if the processor is the problem.  What does lsusb return?  I would really suggest posting here:  [http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?p=4884#4884](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?p=4884#4884)  Mr. Modeswitch has been very helpful to me.

---

