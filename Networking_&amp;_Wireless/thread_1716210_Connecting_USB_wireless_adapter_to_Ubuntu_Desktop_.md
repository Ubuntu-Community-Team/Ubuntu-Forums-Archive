---
title: "Connecting USB wireless adapter to Ubuntu Desktop 10.10"
date: 2011-03-28
forum: Networking &amp; Wireless
---

### Post by intransit on 2011-03-28
I am trying to get a TP-LINK usb wireless adapter to work inside ubuntu desktop 10.10.

This is virtualised in VMWare on a Win 7 host, which may be causing problems.

When I plug the usb in nothing seems to be detected, though I am not familiar with ubuntu's behaviour. A brief google suggested trying the mount cmd, but output did not appear to change with/without the device plugged in. (I was making sure the device was actually connected to the ubuntu virtual in the vmware menu, so it was definetly connected to the virtual not the host.

I looked in /media and /dev 

/media just had floppy and /dev a large number of devices, but i'm not really sure what i'm looking for or what to do next from here.

Any ideas?

I guess its quite possible vmware can't have a wireless adapter connected to it, but google seems to suggest it will work (virtualised) with a windows OS.

Cheers


edit:

> 
lsusb

Bus 001 Device 006: ID 148f:2070 Ralink Technology, Corp. RT2070 Wireless Adapter


Appears to be detected...

---

### Post by galorin on 2011-03-28
Is Windows 7 actually handing the device off to VMware?  Haven't used it in ages, but I know on Oracle VirtualBox, you need to tell the host what USB devices to pass on to the guest.

The other thing to check, is when booted in to Ubuntu, run `tail -f /var/log/messages` in a terminal, and watch it when the USB device is plugged in.  It should see the event, even if it doesn't know what to do.

Also look in to lsusb and dmesg, both before and after the device is plugged.

---

### Post by galorin on 2011-03-28
Looks like I replied as you were editing.  Now it's a case of checking for the correct driver in lsmod, and if not, finding it and loading it in.

---

### Post by intransit on 2011-03-28
Sorry yes, I did. Thanks for your comments.

Believe I have the driver, it's come in a tar.bz2

I get an error when trying to make

> make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
rt73.ko failed to build!
make: *** [module] Error 1


I see here [http://ubuntuforums.org/showthread.php?p=10349588](http://ubuntuforums.org/showthread.php?p=10349588) this comment, which is probably the problem with this particular driver.

" I imagine that since rt73usb is included in the kernel, the CVS has not been updated for most recent kernels."

aha, in the readme:

> The rt73 chipset uses a firmware file which is loaded in device
    memory using the kernel firmware_class facility. 'make install'
    copy the firmware file to the standard firmwares location:
    /lib/firmware.

    However some linux distributions divert from the standard and e.g.
    use /lib/firmware/<KERNEL_VERSION>. If this is your case, you will
    have to manually move the firmware file to the right location.
    If you have problems with firmware loading, please ask on your
    distro's support media (forum, etc).

---

### Post by flash63 on 2011-03-28
Hallo,
first block rt2800usb
```
echo 'blacklist rt2800usb' | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Activate rt2870sta
```
echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "148f 2070" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
```
Plug the Stick in and test it:
```
sudo modprobe rt2870sta
iwconfig
```
and try to connect.

If the solution works create a new udev-Rule
```
sudo gedit /etc/udev/rules.d/10-wlan_stick.rules
```
Content:
```
# UDEV-Rule for Tp-Link TL-WN321G Rev.1 and compatible ID 148f:2070
SUBSYSTEM=="usb", ATTR{idVendor}=="148f", ATTR{idProduct}=="2070", RUN+="/sbin/modprobe rt2870sta"
```
Save it. After reboot the stick should work automatically.

---

