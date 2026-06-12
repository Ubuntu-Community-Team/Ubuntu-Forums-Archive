---
title: "Wireless adapter not detected (USB, 11.10)"
date: 2011-10-21
forum: Networking &amp; Wireless
---

### Post by False_Karma on 2011-10-21
Yeaaah, I give up. I've tried to fix this myself for a while now to no avail, so: Another thread about wireless problems. 

I'm using a Buffalo USB wireless adapter, which was somewhat functional with 11.04. It wasn't working perfectly, as it had an annoying tendency of cutting off my connection whenever downloading large-ish files (all the way from streams on YouTube), but it **worked.** 

I did a dist-upgrade, and for some reason it didn't cut off once while downloading new packages. And, as you might guess, it stopped working altogether after that. Nothing. Network manager shows nothing. After I disconnect and reconnect the usb stick, dmesg only says
```

[ 2310.450056] usb 1-5: USB disconnect, device number 4
[ 2315.748084] usb 1-5: new high speed USB device number 5 using ehci_hcd

```
 I've now connected myself with a wired connection, but it's highly impractical, so I'd like to set up the wireless one asap.  

_Some (possibly relevant) information_

**lsusb**
```

*snip*
Bus 001 Device 004: ID 0411:016f MelCo., Inc. Buffalo WLI-UC-G301N Wireless LAN Adapter
*snip*

```

**iwconfig**
```

lo        no wireless extensions.

eth0      no wireless extensions.

```

**lsusb -vvv**
```

Bus 001 Device 004: ID 0411:016f MelCo., Inc. Buffalo WLI-UC-G301N Wireless LAN Adapter
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0411 MelCo., Inc.
  idProduct          0x016f Buffalo WLI-UC-G301N Wireless LAN Adapter
  bcdDevice            1.01
  iManufacturer           1 Ralink
  iProduct                2 802.11 n WLAN
  iSerial                 3 1.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           67
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              450mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           7
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              5 1.0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x05  EP 5 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
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

```
 
[B]ls /etc/Wireless/
sudo modprobe RT2860STA[/B]

```
adminuser@Ubuntu-PC:/etc/Wireless/RT2860STA$ ls /etc/Wireless
RT2860STA
adminuser@Ubuntu-PC:/etc/Wireless/RT2860STA$  sudo modprobe RT2860STA
[sudo] password for adminuser: 
FATAL: Module RT2860STA not found.

```

Any help would be appreciated, thanks!


EDIT:

Oh yeah, I forgot something. Whenever I boot the PC, it takes a good while longer than it used to. It seems Ubuntu is "setting up the Network configuration" and then something like "Taking up to 60 more seconds to set up the Network configuration" or something akin to that. Also

**sudo /etc/init.d/networking restart**
```
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                                                                                                                                         wpa_supplicant: /sbin/wpa_supplicant daemon failed to start
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
Cannot find device "eth1"
Failed to bring up eth1.
Cannot find device "wlan0"
Failed to bring up wlan0.
```

---

### Post by jawilljr on 2011-10-21
Try this instead:

```
sudo modprobe rt2800usb
```

And try and connect.

If it works then you need to unblacklist rt2800usb.

Jerry

---

### Post by False_Karma on 2011-10-21
Awesome, that did it!

The connection is slow and the PC still takes ages to boot since it's trying to configure the network, but it works, and that's the most important thing. Thank you! :-)

(Oh, if it doesn't take too much time, would someone care to explain to me why I had to blacklist the drivers in the past to make the wireless work, and now I had to unblacklist them to do the same. Doesn't actually matter, I'd just like to learn more.)

---

### Post by jawilljr on 2011-10-21
The reason why is because of [this commit](https://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=fefecc6989b4b24276797270c0e229c07be02ad3)

For speed issues you could try to turn off power management:

```
sudo iwconfig wlan0 power off
```

Of course change wlan0 to your device.

Jerry

---

### Post by False_Karma on 2011-10-22
Thanks for the advice, and for the link. iwconfig wlan0 power off (or something else I tried) fixed the speed issues, and the wireless is actually just as fast as the wired connection, but I've discovered another problem that's kind of... weird.

I don't think it's actually related to my original one, but making a new thread seemed pointless. I don't actually know how to describe it properly, but what seems to be going on is this:

Whenever I try to play any kind of audio (Flash, .avis, .mp3s, even the notification sound for Opera's GMail extension), the "sending" speeds on System Monitor's Network graph go to max, making the "receiving" speeds drop to zero, rendering any kind of Internet use impossible. This doesn't seem to be related to a specific sound system, as it was recreated with both ALSA and Pulseaudio.

I don't know if there's something I'm missing here, but these two things don't seem to be connected in any way, so this seemed somewhat unusual to me. 

The picture below is a System Monitor screenshot. It didn't occur to me to change my system language to English prior taking the screenshot, but I translated everything (?) relevant. 

[IMG]http://i53.tinypic.com/2w3e1c0.png[/IMG]

TL;DR: Computer starts uploading huge amounts of data when playing audio, dropping the downloading rates to zero.

---

### Post by False_Karma on 2011-10-22
Bumping the sound issue. It seems really weird, even a single beep from a confirmation prompt or similar momentarily halts all incoming Internet traffic.

---

### Post by jawilljr on 2011-10-22
Sorry.. I can't help you on that...I am using [this adapter](http://www.newegg.com/Product/Product.aspx?Item=N82E16833156254) which uses rt2800usb in Oneiric... and I am not seeing that problem.

I agree it is a weird problem.

Jerry

---

### Post by False_Karma on 2011-10-22
> **jawilljr said:**
> Sorry.. I can't help you on that...I am using [this adapter](http://www.newegg.com/Product/Product.aspx?Item=N82E16833156254) which uses rt2800usb in Oneiric... and I am not seeing that problem.

I agree it is a weird problem.

Jerry

You've been more than helpful already, thank you : )

I'm guessing this isn't happening because of my adapter, but is a completely different problem.

I got my Internet up and running now, thanks to you, and I wouldn't even had brought this sound thing up hadn't it seemed so unusual to me.

---

### Post by False_Karma on 2011-10-23
Well, it seems to have fixed itself. Active audio still seems to cause data being uploaded, but it doesn't make the downloading speeds drop all the way down to zero anymore. I don't know what I did, if anything, I just booted the machine this morning and it started working.

---

