---
title: "BCM 4306 Rev 2 Wifi Dell Latitude D600"
date: 2011-11-07
forum: Networking &amp; Wireless
---

### Post by grogger13 on 2011-11-07
Fresh install of 11.10 on old Dell Latitude d600
Problem: Wireless card not working.  Under "Wireless Networks" in the toolbar is says "device not ready (firmware missing)"

The first thing i did was found out that I had a BCM4306 rev2 chipset based on this output from the command "lspci -nvn | grep -i net"
```
~$ lspci -nvn | grep -i net
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5702X Gigabit Ethernet [14e4:16a6] (rev 02)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11a/b/g [14e4:4324] (rev 02)

```

From there i tried installing fwcutter and b43legacy firmware from synaptic(had to install synaptic also)

After a reboot and nothing showing up in the "Additional Drivers" section i tried installing the regular b43 firmware.

After a reboot again still nothing in the "Additional Drivers" section.  Then I found a tutorial that gave me these commands 

sudo dpkg-reconfigure firmware-b43legacy-installer

and 

sudo dpkg-reconfigure firmware-b43-installer


First i chose to try the legacy command first and received this error

```
~$ sudo dpkg-reconfigure firmware-b43legacy-installer
[: 17: missing ]
[: 17: missing ]
No supported card found.
Use b43 firmware. This is just for the b43legacy driver.
Aborting.

```

So from there i tried to reinstall b43 firmware and recieved this output:

```
Setting up firmware-b43-installer (1:014-9) ...
An unsupported BCM4301, BCM4303, BCM4306 or BCM4306/2 device was found.
Use b43legacy firmware (firmware-b43legacy-installer package) instead.
Aborting.
```

However, the software center and synaptic both listed b43 as being installed so i tried

```
~$ sudo dpkg-reconfigure firmware-b43-installer
An unsupported BCM4301, BCM4303, BCM4306 or BCM4306/2 device was found.
Use b43legacy firmware (firmware-b43legacy-installer package) instead.
Aborting.

```

I did also try installing the b43 lpphy drivers and after a reboot also nothing showed up in the "Additional Drivers" section.

What is most confusing to me is how I received an output saying the b43Legacy firmware did not detect any device, but the b43 firmware says it detects a legacy device and to use the legacy firmware.  Does anyone have any idea what to do?

---

### Post by pdc on 2011-11-07
this site

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

suggests two consecutive commands

> sudo apt-get install b43-fwcutter

and then 

> sudo apt-get install firmware-b43legacy-installer

I wonder if you delete your current installs of b43 related software;

and do the above............

I wonder where you got the 

> sudo dpkg-reconfigure firmware-b43legacy-installer

from

---

### Post by grogger13 on 2011-11-13
I found it from a tutorial somewhere but i cant seem to relocate that same troubleshooting tutorial

---

### Post by j_talbain on 2011-11-14
I am having the same problem as you. 
When I run lspci -v, it comes back with BCM4306 rev 03. And lists the card as a Dell Truemobile 1450 pci. 
But what confuses me is the supported cards list. (here: [http://wireless.kernel.org/en/users/Drivers/b43/devices](http://wireless.kernel.org/en/users/Drivers/b43/devices)) The list shows that the 1450 is BCM4309* and it shares the same offset with the BCM4306 of 0x4324. Granted that I have no idea how to use this extra information, maybe this will help someone out.

On a different tack, is there a way to manually assign a driver to a specific piece of hardware in linux? If the list at wireless.kernel.org is correct, the drivers support this specific hardware but maybe the installer is confused by the conflicting information provided. Ideas anyone?

*corrected

---

### Post by pdc on 2011-11-15
this post

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

would suggest you need the b43

this forum runs on information; so if you need help, do supply some information

---

### Post by j_talbain on 2011-11-15
As the OP stated:
> 
grogger13:

First i chose to try the legacy command first and received this error

     ```
~$ sudo dpkg-reconfigure firmware-b43legacy-installer [: 17: missing ] [: 17: missing ] No supported card found. Use b43 firmware. This is just for the b43legacy driver. Aborting. 
```So from there i tried to reinstall b43 firmware and recieved this output:

     ```
Setting up firmware-b43-installer (1:014-9) ... An unsupported BCM4301, BCM4303, BCM4306 or BCM4306/2 device was found. Use b43legacy firmware (firmware-b43legacy-installer package) instead. Aborting. 
```The installer bounces you from b43 to b43legacy. It doesn't pickup the card. That is why I asked if you can manually assign drivers to a device.

---

### Post by Bernmeister on 2011-12-15
Managed to get this sorted on Dell Latitude D505, Lubuntu 11.10. 

wifi details:

```
lspci -vvnn | grep 14e4
01:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11a/b/g [14e4:4324] (rev 03)
```

I also was bouncing between legacy and non-legacy and after several reads of [http://wireless.kernel.org/en/users/Drivers/b43]("http://wireless.kernel.org/en/users/Drivers/b43") followed this procedure:

1) ```
sudo apt-get install b43-fwcutter
```

2) From the subsection "If you are using the b43 driver from older kernel" from the above URL, do the following:

```
wget http://mirror2.openwrt.org/sources/broadcom-wl-5.10.56.27.3_mipsel.tar.bz2
tar xjf broadcom-wl-5.10.56.27.3_mipsel.tar.bz2
sudo b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" broadcom-wl-5.10.56.27.3/driver/wl_apsta/wl_prebuilt.o
```

Reboot!

---

### Post by chrisolof on 2012-01-24
For a bcm4306 on a Dell Inspiron 5150 the steps were:
```

export FIRMWARE_INSTALL_DIR="/lib/firmware"

wget http://mirror2.openwrt.org/sources/broadcom-wl-5.10.56.27.3_mipsel.tar.bz2

tar xjf broadcom-wl-5.10.56.27.3_mipsel.tar.bz2

sudo b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" broadcom-wl-5.10.56.27.3/driver/wl_apsta/wl_prebuilt.o

sudo modprobe b43
```

---

### Post by wildmanne39 on 2013-01-27
Hi, this is an old thread so it has been closed please start a new thread of your own with a descriptive title. 
Thanks

---

