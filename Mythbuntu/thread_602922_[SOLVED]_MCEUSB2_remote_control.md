---
title: "[SOLVED] MCEUSB2 remote control"
date: 2007-11-04
forum: Mythbuntu
---

### Post by lfuzzy on 2007-11-04
I have a Firefly mini remote control, but it does'nt work with Mythbuntu though it's perfect for BeyondTV and and Vista Media Center.

I am looking for a remote control to work with Mythbuntu. From reading the posts, it seems MCEUSB2 is a good choice. How do I know which ones are MCEUSB2?

I found this one on amzon.com:

[http://www.kinamax.com/product/Item/RC-MCE.htm](http://www.kinamax.com/product/Item/RC-MCE.htm)

Is it MCEUSB2?

Thanks,

---

### Post by tgm4883 on 2007-11-05
[http://www.mythtv.org/wiki/index.php/MCE_Remote](http://www.mythtv.org/wiki/index.php/MCE_Remote)

---

### Post by road2elysium on 2007-11-06
> **lfuzzy said:**
> 

[http://www.kinamax.com/product/Item/RC-MCE.htm](http://www.kinamax.com/product/Item/RC-MCE.htm)



I just set this one up using the mceusb2 drivers.  Works just fine.


Edit:  Correction.  The remote works with basic functionality regardless of designated remote drivers in the Mythbuntu Control Center.  There's a way around it as well -- akin to the Firefly mini remote control instructions.  I'll post further below.

---

### Post by lucidblue on 2007-11-08
I just got this remote and am setting up mythtv more as a front-end for media that I already have.

I actually saw this post before I bought it and I assumed it would work.  My system picks up the receiver instantly, but uses the usbkbd driver, so it really is just seeing the remote as a keyboard...

I could probably make this work, but I know you said it works with lirc_usbmce2 driver, I can load that and then lircd with no errors, but when I run irw, I see no output, when hitting buttons on the remote, it just enters numbers or whatever into the console.

I'm just concerned that I won't be able to have full functionality if I can't map the keys.

Could you post your lircd.conf and lircrc file?  It's the exact remote, so if I see yours, I'll know better where to start.

Thanks for any info!

---

### Post by road2elysium on 2007-11-14
> **lucidblue said:**
> 
I actually saw this post before I bought it and I assumed it would work.  My system picks up the receiver instantly, but uses the usbkbd driver, so it really is just seeing the remote as a keyboard...


You can view the IR details by doing the following.
```
lsusb
```
> Bus 003 Device 003: ID 1241:e000 Belkin 

```
sudo lsusb -D /proc/bus/usb/003/003
```
> Device: ID 1241:e000 Belkin 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x1241 Belkin
  idProduct          0xe000 
  bcdDevice            2.00
  iManufacturer           1 HOLTEK
  iProduct                2 USB Keyboard
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           59
    bNumInterfaces          2
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
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      63
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
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
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
          wDescriptorLength     157
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)


---

### Post by road2elysium on 2007-11-14
> **lucidblue said:**
> 
I could probably make this work, but I know you said it works with lirc_usbmce2 driver, I can load that and then lircd with no errors, but when I run irw, I see no output, when hitting buttons on the remote, it just enters numbers or whatever into the console.


I was able to set up an irrecord to grab the codes for the remote as follows:

```
sudo irrecord --driver=dev/input --device=/dev/input/by-id/usb-HOLTEK_USB_Keyboard-event-kbd ~/lircd-kinamax.conf
```

---

### Post by road2elysium on 2007-11-14
> **lfuzzy said:**
> I have a Firefly mini remote control, but it does'nt work with Mythbuntu though it's perfect for BeyondTV and and Vista Media Center.


I found that the Kinamax remote is quite similar to the Firefly mini remote in that it is recognized as a Human Interface Device (HID) and should work with basic functionality without drivers.  Check out the following wiki page to complete the functionality.

[http://www.mythtv.org/wiki/index.php/Snapstream_firefly_mini](http://www.mythtv.org/wiki/index.php/Snapstream_firefly_mini)

---

### Post by lucidblue on 2007-11-14
Totally just had to edit this, quoted the wrong part.
I was looking at that, do you think the kernel patch is really necessary? With the irrecord, what type of info does that log?  I looked in the list of pre-made lirc.conf files, but couldn't find the kinamax listed.

---

### Post by road2elysium on 2007-11-14
I believe the kernel patch is only to gain functionality of a few remaining buttons.

Irrecord logs IR remote codes.   It can generate an index of codes to button names which normally resides in the /etc/lirc/lircd.conf file.

---

### Post by lucidblue on 2007-11-14
> **road2elysium said:**
> I believe the kernel patch is only to gain functionality of a few remaining buttons.

Irrecord logs IR remote codes.   It can generate an index of codes to button names which normally resides in the /etc/lircd.conf file.

Oh, cool, I'll give that a shot, thanks!  I'll be sure to post back findings! :)

---

### Post by lucidblue on 2007-11-21
> **road2elysium said:**
> I was able to set up an irrecord to grab the codes for the remote as follows:

```
sudo irrecord --driver=dev/input --device=/dev/input/by-id/usb-HOLTEK_USB_Keyboard-event-kbd ~/lircd-kinamax.conf
```

I tried the above, and it seemed to work for the most part, I think the only buttons that wouldn't work were the volume and mute, but I'm not 100% that the 'channel up & down' where picked up -- no big deal really.

So now I've got an lircd.conf (or whatever), and now the next step I think is to make an .lircdrc file? My understanding is that I need to assign functions to the named buttons now.

The problem tho, is the command I have to run to get irw to show anything is 'irw --driver=/dev/input --device=/dev/input/by-id/usb-HOLTEK_USB_Keyboard-event-kdb' <-- almost exaclty that, the --driver switch might be a little different, but it means the same thing.  When I do this, I seem to get correct output (it shows the keys pressed) for the first couple, then (and I can't tell  yet if this just has to do with the certain keys pressed), it will start showing:

asterisk  00000xxxxx <-- whatever the number is
eight      00000xxxxx <-- whatever

^^^^^  and repeat like that no matter what key is press, it seems to show those two, or a combination of 'asterisk' (for that key's name) and another key, two for every one key press.

It almost seems to be after a couple key presses, then it'll start doing that.  I assume that's what lircd sees as presses, so wouldn't that start getting screwy?

*** Also, when did you load the lircd_mceusb2 driver? is it even needed?  maybe that's my issue?

Thanks for the help 
-- lucidblue

---

