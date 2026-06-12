---
title: "USB-P1KH voip phone"
date: 2009-12-21
forum: Multimedia Software
---

### Post by Tulth on 2009-12-21
I recently purchased a usb voip phone online.  This phone looks identical to the phone [listed here on amazon]("http://www.amazon.com/VOIP-Phone-Support-Skype-Messenger/dp/B000BQPY22"). I believe it is model USB-P1KH.

I'm trying to get it to work as a sip client phone.  I am running kernel 2.6.31-16-generic, amd64.

```
> lsusb
Bus 001 Device 011: ID 6993:b700 Freshtel 
```

When I first plug the phone in I can execute the following commands
```
>sudo mount -t usbfs none /proc/bus/usb 
>sudo cat /proc/bus/usb/devices
T:  Bus=01 Lev=02 Prnt=02 Port=02 Cnt=02 Dev#= 10 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=6993 ProdID=b700 Rev= 0.01
S:  Manufacturer=Yealink Network Technology Ltd.
S:  Product=VOIP USB Phone 
C:* #Ifs= 4 Cfg#= 1 Atr=80 MxPwr=500mA
I:* If#= 0 Alt= 0 #EPs= 0 Cls=01(audio) Sub=01 Prot=00 Driver=snd-usb-audio
I:* If#= 1 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
I:  If#= 1 Alt= 1 #EPs= 1 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
E:  Ad=02(O) Atr=09(Isoc) MxPS= 192 Ivl=1ms
I:* If#= 2 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
I:  If#= 2 Alt= 1 #EPs= 1 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
E:  Ad=83(I) Atr=01(Isoc) MxPS=  16 Ivl=1ms
I:* If#= 3 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=48ms

```

My research on this device on the web led me to [this page]("http://www.devbase.at/voip/yeaphone-download.php") serving about this family of devices.

I think my kernel originally had this version of the kernel module
```
#define DRIVER_VERSION "yld-20051230"
```

This version only has support for 
```
.idVendor		= 0x6993,
.idProduct		= 0xb001,
```

So I downloaded the newest kernel module version:
```
>svn co --username guest --password readonly svn://devbase.homelinux.org:5070/voip/yealink-module
```

I note that this seems to support my usb device:
```
#define USB_YEALINK_VENDOR_ID	0x6993
#define USB_YEALINK_PRODUCT_ID1	0xb001
#define USB_YEALINK_PRODUCT_ID2	0xb700
```

after some apt-getting for dev packages , I can run
```
>make
```
and it builds yealink.ko .  Now here I'm not sure what to do.  I end up running 
```
>sudo install -m 644 yealink.ko /lib/modules/2.6.31-16-generic/kernel/drivers/yealink.ko
>sudo depmod -a
>sudo update-initramfs -u

```
Then I reboot.  However it still does not load:
```
>dmesg
...
[  174.151542] usb 1-1.3: new full speed USB device using ehci_hcd and address 10
[  174.285813] usb 1-1.3: configuration #1 chosen from 1 choice
[  174.334506] generic-usb 0003:6993:B700.0007: hiddev96,hidraw2: USB HID v1.10 Device [Yealink Network Technology Ltd. VOIP USB Phone ] on usb-0000:00:1a.7-1.3/input3
...
>sudo mount -t usbfs none /proc/bus/usb 
>sudo cat /proc/bus/usb/devices
T:  Bus=01 Lev=02 Prnt=02 Port=02 Cnt=02 Dev#= 10 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=6993 ProdID=b700 Rev= 0.01
S:  Manufacturer=Yealink Network Technology Ltd.
S:  Product=VOIP USB Phone 
C:* #Ifs= 4 Cfg#= 1 Atr=80 MxPwr=500mA
I:* If#= 0 Alt= 0 #EPs= 0 Cls=01(audio) Sub=01 Prot=00 Driver=snd-usb-audio
I:* If#= 1 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
I:  If#= 1 Alt= 1 #EPs= 1 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
E:  Ad=02(O) Atr=09(Isoc) MxPS= 192 Ivl=1ms
I:* If#= 2 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
I:  If#= 2 Alt= 1 #EPs= 1 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
E:  Ad=83(I) Atr=01(Isoc) MxPS=  16 Ivl=1ms
I:* If#= 3 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=48ms

```

It is still loading usbhid.  I try creating a file, ```
/etc/udev/rules.d/99-yealink.rules
```, as suggested on [http://www.nslu2-linux.org/wiki/HowTo/ConnectUSBPhone](http://www.nslu2-linux.org/wiki/HowTo/ConnectUSBPhone), with these contents:
```
KERNEL=="event*", DRIVERS=="yealink", GROUP="voice", RUN+="/bin/sh -c '/bin/chgrp voice /sys$env{PHYSDEVPATH}/*'"

```

Still no luck its usbhid.  So I try creating ```
/etc/modprobe.d/usbhid.conf
```
with these contents
```
options usbhid quirks=0x6993:0xb700:0x03
options usbhid quirks=0x6993:0xb700:0x0003
options usbhid quirks=0x6993:0xb700:0x04
options usbhid quirks=0x6993:0xb700:0x0004
options usbhid quirks=0x6993:0xb700:0x01
options usbhid quirks=0x6993:0xb700:0x0001
options usbhid quirks=0x6993:0xb700:0x02
options usbhid quirks=0x6993:0xb700:0x0002

```
but still no luck.

I finally got this to boot usbhid:
```
>cd /sys/bus/usb/drivers/usbhid/
>sudo echo -n 1-1.3:1.3 > unbind
```
(previous lsing on /sys/bus/usb/drivers/usbhid/ with and without the phon eplugged in indicated the right device was 1-1.3:1.3)

now I do:
```
>sudo rmmod yealink
>sudo modprobe yealink
>dmesg
...
[ 2036.896118] usbcore: deregistering interface driver yealink
[ 2040.115770] yealink: Detected Model USB-P1KH (Version 0x1008)
[ 2040.243743] yealink: Serial Number 6a8dfb9da696
[ 2040.243848] input: Yealink USB-P1KH as /devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1.3/1-1.3:1.3/input/input7
[ 2040.570123] usbcore: registered new interface driver yealink
[ 2040.570128] yealink: Yealink phone driver: 20090418 (C) Thomas Reitmayr, Henk Vergonet
...
>sudo cat /proc/bus/usb/devices
T:  Bus=01 Lev=02 Prnt=02 Port=02 Cnt=02 Dev#= 11 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=6993 ProdID=b700 Rev= 0.01
S:  Manufacturer=Yealink Network Technology Ltd.
S:  Product=VOIP USB Phone 
C:* #Ifs= 4 Cfg#= 1 Atr=80 MxPwr=500mA
I:* If#= 0 Alt= 0 #EPs= 0 Cls=01(audio) Sub=01 Prot=00 Driver=snd-usb-audio
I:* If#= 1 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
I:  If#= 1 Alt= 1 #EPs= 1 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
E:  Ad=02(O) Atr=09(Isoc) MxPS= 192 Ivl=1ms
I:* If#= 2 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
I:  If#= 2 Alt= 1 #EPs= 1 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
E:  Ad=83(I) Atr=01(Isoc) MxPS=  16 Ivl=1ms
I:* If#= 3 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=yealink
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=48ms

```

So this is as far as I've gotten.  I'm not sure why its not automatically loading the yealink driver.  Anyone have suggestions?

---

### Post by Tulth on 2009-12-22
Update: I couldn't figure out how else to do it, so I decided this would be a good time to learn some bash scripting.  Below is my first working cut at a script to: find the yealink, boot usbhid (or whatever is on its keypad/lcd interface), then reload the yealink kernel module.
```
#!/bin/bash
# this script's purpose is to boot the stupid usbhid driver off the
#   yealink phone and allow the yealink kernl driver to takeover
# this script is intended to be run by root
ylName="Yealink USB-P1KH"
ylVendor=6993
ylProduct=B700
subDevice=1.3
deviceModule=yealink
# upper/lowercase string conversions
function toLower() { echo $1 | tr "[:upper:]" "[:lower:]" ; }
function toUpper() { echo $1 | tr "[:lower:]" "[:upper:]" ; }
# returns 0 for match, anything else is not a match
function is_yl_match() {
    if [ $1 = "$ylVendor" ] && [ $2 = "$ylProduct" ] ; then
        return 0
    else
        return 1
    fi
}
# returns 0 for yl device present, anything else is not present
function is_yl_present() {
    local result
    for i in /sys/bus/usb/devices/*; do  
        if [ -f "$i/idVendor" ]; then
            if [ -f "$i/idProduct" ]; then
                rawVendor=`cat $i/idVendor`
                rawProduct=`cat $i/idProduct`
                wVendor=`toUpper $rawVendor`
                wProduct=`toUpper $rawProduct`
                is_yl_match $wVendor $wProduct
                result=$?
                if [[ result -eq 0 ]] ; then
                    return 0
                fi
            fi
        fi
    done
    return 1
}
# assumes device is present!
function get_yl_device_str() {
    local result
    for i in /sys/bus/usb/devices/*; do  
        if [ -f "$i/idVendor" ]; then
            if [ -f "$i/idProduct" ]; then
                rawVendor=`cat $i/idVendor`
                rawProduct=`cat $i/idProduct`
                wVendor=`toUpper $rawVendor`
                wProduct=`toUpper $rawProduct`
                is_yl_match $wVendor $wProduct
                result=$?
                if [[ result -eq 0 ]] ; then
                    echo $i ;
                    return 0
                fi
            fi
        fi
    done
    return 1
}
# MAIN
is_yl_present
result=$?
if [ $result -ne 0 ] ; then
    echo ERROR: $ylName \(VID: $ylVendor, PID: $ylProduct\) not found!
    exit 1 # device not present
fi
# determine the device paths
ylDevPath="$(get_yl_device_str)"
ylDev=`basename $ylDevPath`
ylSubDev=$ylDev:$subDevice
ylSubDevPath=$ylDevPath/$ylSubDev
# boot whatever is on the device off
if [ ! -e "$ylSubDevPath/driver/unbind" ] ; then
    echo WARNING: unbind driver capability not found \($ylSubDevPath/driver/unbind missing\)
else    
    echo -n $ylSubDev > $ylSubDevPath/driver/unbind
fi
# get the right device module on it
modprobe -r $deviceModule
modprobe $deviceModule

```

---

### Post by Tulth on 2009-12-22
I now have the script above running at phone plug in by creating the file **/etc/udev/rules.d **and adding this line:
```
DRIVER=="usbhid", ACTION=="add|change", SUBSYSTEMS=="usb", ATTRS{idVendor}=="6993", ATTRS{idProduct}=="b700", RUN+="/usr/local/yealink_script.sh"
```

I think this is a very ugly way of making this work, anyone know of how to do this the right way?

---

### Post by ethos_dacapo on 2010-02-21
Do you have this working with the latest kernel? If so can you walk me through the process of getting this thing working. I bought this phone specifically because it claimed to be linux compatible and so far its been no more than a headset to me.

---

