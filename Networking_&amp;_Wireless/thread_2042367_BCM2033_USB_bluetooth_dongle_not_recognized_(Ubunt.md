---
title: "BCM2033 USB bluetooth dongle not recognized (Ubuntu 12.04)"
date: 2012-08-14
forum: Networking &amp; Wireless
---

### Post by veroslav on 2012-08-14
Hi,

I am trying to get my USB Bluetooth adapter working in Ubuntu 12.04 but so far without success. I have installed linux-firmware-nonfree (in order to get bcm2033-fw.bin) but it hasn't made any difference. 

Below are the few outputs I think are relevant:

```
user@user-desktop:~$ lsusb | grep Bluetooth
Bus 001 Device 004: ID 0a5c:2033 Broadcom Corp. BCM2033 Bluetooth
``````
user@user-desktop:~$ hciconfig -a
user@user-desktop:~$
``````
user@user-desktop:~$ hcitool dev
Devices:
```I searched the google but the few relevant results I found were really old and were targeting older versions of Ubuntu.

I appreciate any kind of help on how I can proceed.

Thank you in advance.

---

### Post by veroslav on 2012-08-15
Bump

---

### Post by chili555 on 2012-08-15
DISCLAIMER: I know nothing about bluetooth, but I know a tiny bit about drivers and firmware. I think your device works with the driver bcm203x:```
$ modinfo bcm203x
filename:       /lib/modules/3.2.0-29-generic-pae/kernel/drivers/bluetooth/bcm203x.ko
firmware:       BCM2033-FW.bin
firmware:       BCM2033-MD.hex
license:        GPL
version:        1.2
description:    Broadcom Blutonium firmware driver ver 1.2
author:         Marcel Holtmann <marcel@holtmann.org>
srcversion:     DCD8C5172505945434A6A41
alias:          usb:v[COLOR="Red"]0A5C[/COLOR]p[COLOR="Red"]2033[/COLOR]d*dc*dsc*dp*ic*isc*ip*
depends:        bluetooth
intree:         Y
vermagic:       3.2.0-29-generic-pae SMP mod_unload modversions 686 

```I suggest you load it and check the message logs for any clues:```
sudo modprobe bcm203x
dmesg | grep bcm203x
```That's about all I can suggest.

---

### Post by veroslav on 2012-08-16
Thank you for your reply chili555.

I will have a go later today and come back with the results.

Kind Regards,
Veroslav

---

### Post by veroslav on 2012-08-17
Hi again,

running lsmod, it appears that the bcm203x module is already loaded:

```
user@user-desktop:~$ lsmod | grep bcm203x
bcm203x                12710  0 
bluetooth             180104  12 bnep,rfcomm,btusb,bcm203x
```Running dmesg as suggested above gives the following output:

```
user@user-desktop:~$ dmesg | grep bcm203x
[   18.336418] bcm203x: probe of 1-1.4:1.0 failed with error -5
[   18.336456] usbcore: registered new interface driver bcm203x
```Does anybody knows what the error above (-5) means and what I should do in order to fix it? Thanks again!

/Veroslav

---

### Post by chili555 on 2012-08-17
As I said, I'm in over my head, but this might be helpful: [http://ubuntuforums.org/showthread.php?t=1244049](http://ubuntuforums.org/showthread.php?t=1244049)

---

### Post by veroslav on 2012-08-17
Hi chili555!

No problem, I am very thankful for your effort and time :)

I am also way over head with this one, I just thought it would be cool to see whether I could get my ps3 controller to work through bluetooth, as I didn't have any success by connecting it directly through usb. I am not in a hurry to get it to work but so far I managed to get all of my hardware working so this is another fun challenge.

I found the thread you linked to just before and I noticed that the 'bluetooth' package was not installed, so I did that but unfortunately without success (still the same error message in the logs).

The next step will be to download bluez-firmware package that was mentioned in the thread and see if I get lucky. I want to learn more about it first though, in order to know exactly what I am doing.

Appreciate your help very much!

/Veroslav

---

### Post by veroslav on 2012-08-19
BUMP

Does anyone has any more suggestions? I am stuck at the moment and I don't know what to try out next, need some suggestions.

Thanks!

---

### Post by veroslav on 2012-08-21
And a final BUMP...

---

### Post by nubutun on 2012-11-09
Not a finite solution; but one step closer :):

I'm having the same issue; [COLOR=Blue][BCM2033]("http://www.broadcom.com/products/BCM2033")[/COLOR] on a TECOM Broadcom Corp. Bluetooth dongle.

The dmesg 
*bcm203x: probe of NNN failed with error -5*
we can find the reason for in the kernel source code: [COLOR=Blue][drivers/bluetooth/bcm203x.c#L196]("http://lxr.linux.no/#linux+v3.6.6/drivers/bluetooth/bcm203x.c#L196")[/COLOR]

The error code -5 is -[COLOR=Blue][EIO]("http://lxr.linux.no/#linux+v3.6.6/include/asm-generic/errno-base.h#L8")[/COLOR]

In other words the file BCM2033-MD.hex is missing. Further [COLOR=Blue][down the code]("http://lxr.linux.no/#linux+v3.6.6/drivers/bluetooth/bcm203x.c#L223")[/COLOR] we also see BCM2033-FW.bin is needed.

These files can be found in [COLOR=Blue][bluez-firmware-1.2.tar.gz]("http://bluez.sf.net/download/bluez-firmware-1.2.tar.gz")[/COLOR] from [COLOR=Blue][http://www.bluez.org/download/](http://www.bluez.org/download/)[/COLOR].

Copy the files 

[LIST]
[*]bluez-firmware-1.2/broadcom/BCM2033-MD.hex
[*]bluez-firmware-1.2/broadcom/BCM20333-FW.bin
[/LIST]
to /lib/firmware/


Now the dongle gives no errors when attached - but I'm still not able to detect it using BlueZ.
```
$ hcitool dev 
Devices: 
$ hciconfig -a
(No output)
```I have done:
```

# Removed dongle
$ modprobe -r bcm203x
# Inserted dongle
$ dmesg | tail
[40767.152052] usb 5-2: USB disconnect, device number 11
[40773.484430] usbcore: deregistering interface driver bcm203x
[40792.936031] usb 5-2: new full-speed USB device number 12 using uhci_hcd
[40793.082819] usb 5-2: New USB device found, idVendor=0a5c, idProduct=2033
[40793.082825] usb 5-2: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[40793.102311] usbcore: registered new interface driver bcm203x
# Restarted bluetooth
$ sudo service bluetooth restart
# etc ...

```Perhaps this can give a hint?

```


$ sudo lsusb -t -s 005:012
5-2:1.1: No such file or directory
5-2:1.2: No such file or directory
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 1: Dev 2, If 0, Class=HID, Driver=usbhid, 1.5M
    |__ Port 2: Dev 12, If 0, Class='bInterfaceClass 0xe0 not yet handled', Driver=bcm203x, 12M
    |__ Port 2: Dev 12, If 1, Class='bInterfaceClass 0xe0 not yet handled', Driver=, 12M
    |__ Port 2: Dev 12, If 2, Class=vend., Driver=, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/4p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/4p, 480M
    |__ Port 4: Dev 2, If 0, Class=stor., Driver=usb-storage, 480M

```

---

