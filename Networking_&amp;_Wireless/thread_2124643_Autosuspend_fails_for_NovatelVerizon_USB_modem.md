---
title: "Autosuspend fails for Novatel/Verizon USB modem"
date: 2013-03-11
forum: Networking &amp; Wireless
---

### Post by Eagleski on 2013-03-11
Folks, 

I have invested time in getting a Novatel 551L modem working on my 12.10 Ubuntu.  This modem is the current Verizon one that supports RPSMA ext antenna connections.  The challenge is getting it to autosuspend when not in use.  

The drivers that Novatel states they use are option and cdc_ether.  Also usbserial and usbserial_generic are loaded.

root@eric-ThinkPad-R61:/sys/bus/usb/drivers# ls
cdc_ether  hub  libusual  option  usb  usbfs  usbhid  usbserial  usbserial_generic

root@eric-ThinkPad-R61:/sys/bus/usb/drivers# lsusb
Bus 002 Device 005: ID 1410:b001 Novatel Wireless 
Bus 005 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

relevant dmesg:
[ 8395.808144] usb 2-2: >new high-speed USB device number 5 using ehci_hcd
[ 8395.941455] usb 2-2: >config 1 has an invalid interface number: 6 but max is 5
[ 8395.941466] usb 2-2: >config 1 has an invalid interface number: 7 but max is 5
[ 8395.941473] usb 2-2: >config 1 has an invalid interface number: 7 but max is 5
[ 8395.941480] usb 2-2: >config 1 has no interface number 3
[ 8395.941487] usb 2-2: >config 1 has no interface number 5
[ 8395.942947] usb 2-2: >New USB device found, idVendor=1410, idProduct=b001
[ 8395.942957] usb 2-2: >New USB device strings: Mfr=4, Product=3, SerialNumber=5
[ 8395.942965] usb 2-2: >Product: Novatel Wireless 4G
[ 8395.942972] usb 2-2: >Manufacturer: Novatel Wireless, Inc.
[ 8395.942979] usb 2-2: >SerialNumber: 990000924145721
[ 8395.944593] option 2-2:1.0: >GSM modem (1-port) converter detected
[ 8395.944995] usb 2-2: >GSM modem (1-port) converter now attached to ttyUSB0
[ 8395.945252] option 2-2:1.1: >GSM modem (1-port) converter detected
[ 8395.945599] usb 2-2: >GSM modem (1-port) converter now attached to ttyUSB1
[ 8395.945821] option 2-2:1.2: >GSM modem (1-port) converter detected
[ 8395.946165] usb 2-2: >GSM modem (1-port) converter now attached to ttyUSB2
[ 8395.946370] option 2-2:1.4: >GSM modem (1-port) converter detected
[ 8395.946708] usb 2-2: >GSM modem (1-port) converter now attached to ttyUSB3
[ 8395.948224] cdc_ether 2-2:1.6: >wwan0: register 'cdc_ether' at usb-0000:00:1d.7-2, Mobile Broadband Network Device, 00:a0:c6:00:00:00
root@eric-ThinkPad-R61:/sys/bus/usb/drivers# ^C

verified device and path
root@eric-ThinkPad-R61:/sys/bus/usb/devices# ls
1-0:1.0  2-2:1.0  2-2:1.4  3-0:1.0  5-1      6-0:1.0  usb2  usb5
2-0:1.0  2-2:1.1  2-2:1.6  4-0:1.0  5-1:1.0  7-0:1.0  usb3  usb6
2-2      2-2:1.2  2-2:1.7  5-0:1.0  5-1:1.1  usb1     usb4  usb7
root@eric-ThinkPad-R61:/sys/bus/usb/devices# cd 2-2
root@eric-ThinkPad-R61:/sys/bus/usb/devices/2-2# ls
2-2:1.0     avoid_reset_quirk    bMaxPacketSize0     dev        manufacturer  serial
2-2:1.1     bcdDevice            bMaxPower           devnum     maxchild      speed
2-2:1.2     bConfigurationValue  bNumConfigurations  devpath    power         subsystem
2-2:1.4     bDeviceClass         bNumInterfaces      driver     product       uevent
2-2:1.6     bDeviceProtocol      busnum              ep_00      quirks        urbnum
2-2:1.7     bDeviceSubClass      configuration       idProduct  removable     version
authorized  bmAttributes         descriptors         idVendor   remove
root@eric-ThinkPad-R61:/sys/bus/usb/devices/2-2# cat devnum
5
root@eric-ThinkPad-R61:/sys/bus/usb/devices/2-2# cat devpath
2
root@eric-ThinkPad-R61:/sys/bus/usb/devices/2-2# 

then issued:
root@eric-ThinkPad-R61:/sys/bus/usb/devices# echo 2 > 2-2/power/autosuspend
root@eric-ThinkPad-R61:/sys/bus/usb/devices# cat 2-2/power/autosuspend
2
root@eric-ThinkPad-R61:/sys/bus/usb/devices# echo auto > 2-2/power/level
root@eric-ThinkPad-R61:/sys/bus/usb/devices# cat 2-2/power/level
auto
root@eric-ThinkPad-R61:/sys/bus/usb/devices# 

The modem LED stays lit indefinitely after this.  I expected it to go out.

I see there's a possibly relevant patch at
[http://lists.debian.org/debian-qa-packages/2011/07/msg00052.html](http://lists.debian.org/debian-qa-packages/2011/07/msg00052.html)
but not sure how to tell if that is built into this release.

I would appreciate any help in softening the blows of my head to the wall.  Novatel gave me nothing to go on.

Thanks.

---

### Post by bmork on 2013-03-21
> **Eagleski said:**
> Folks, 

I have invested time in getting a Novatel 551L modem working on my 12.10 Ubuntu.  This modem is the current Verizon one that supports RPSMA ext antenna connections.  The challenge is getting it to autosuspend when not in use.  



Look at the "runtime_*" files to verify that autosuspend works. If runtime_suspended_time > 0 then the device has been autosuspended.  Example:

```

bjorn@nemi:~$ grep . /sys/bus/usb/devices/2-4/power/*
/sys/bus/usb/devices/2-4/power/active_duration:7141824
/sys/bus/usb/devices/2-4/power/async:enabled
/sys/bus/usb/devices/2-4/power/autosuspend:2
/sys/bus/usb/devices/2-4/power/autosuspend_delay_ms:2000
/sys/bus/usb/devices/2-4/power/connected_duration:9939484
/sys/bus/usb/devices/2-4/power/control:auto
/sys/bus/usb/devices/2-4/power/level:auto
/sys/bus/usb/devices/2-4/power/persist:1
/sys/bus/usb/devices/2-4/power/runtime_active_kids:0
/sys/bus/usb/devices/2-4/power/runtime_active_time:7141596
/sys/bus/usb/devices/2-4/power/runtime_enabled:enabled
/sys/bus/usb/devices/2-4/power/runtime_status:suspended
/sys/bus/usb/devices/2-4/power/runtime_suspended_time:2797644
/sys/bus/usb/devices/2-4/power/runtime_usage:0
/sys/bus/usb/devices/2-4/power/wakeup:disabled

```

Note that it won't autosuspend while in use unless the device supports "Remote Wakeup".  You can verify this using "lsusb -vd 1410:b001".  You will see the "Remote Wakeup" flag under Configuration Descriptor->bmAttributes if it is supported.  If not, then the device can only be autosuspended when the drivers know it isn't in use.  Which means that the network device must be down and none of the tty devices can be open.  This probably means that it cannot be autosuspended with ModemManager running, I guess.

But let's find out if it does support "Remote Wakeup".  Example from a device with such support:

```

  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          175
    bNumInterfaces          6
    bConfigurationValue     1
    iConfiguration          1 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA

```

---

