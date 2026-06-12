---
title: "Tutorial Wireless WUSB600N (Linksys Wireless-N and others)"
date: 2009-04-16
forum: Networking &amp; Wireless
---

### Post by marcelkoopman on 2009-04-16
This tutorial describes how to get the Linksys Wireless-N USB Network Adepter to work. Note that the chip is a WUSB600N which is also found on other similar devices.

[SIZE="3"]Building a custom kernel[/SIZE]
I've found the best way to get it to work is by using a custom kernel.
If you do not know how to build your own kernel, please read [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

It is possible to build the driver outside of the kernel, but this seems to fail with the current driver version.

However you still need the ralink driver. Download it from [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html) 
You need the RT2870USB(RT2870/RT2770) driver.

In the kernel configuration, go to staging drivers, select Y and select the RT2870 as Module or just Y.

Before you build the kernel two files need to be adjusted:

1. /usr/src/linux/drivers/staging/rt2860/config.mk
- Change HAS_WPA_SUPPLICANT=n to HAS_WPA_SUPPLICANT=y
- Change HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n to HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

2. /usr/src/linux/drivers/staging/rt2870/rt2870.h

Add this line:
{USB_DEVICE(0x1737,0x0071)}, /* WUSB600N */ \

This needs to be between the other USB_DEVICE lines.

Now build this kernel and install the debian packages.

[SIZE="3"]Configuring via the RT2870STA.dat file[/SIZE]
Last thing to do is configure. Go to the driver that you downloaded, untar it and to the following:

sudo mkdir -p /etc/Wireless/RT2870STA

Then copy over the file RT2870STA.dat to /etc/Wireless/RT2870STA
sodo cp RT2870STA.dat /etc/Wireless/RT2870STA

Last thing to do is configure you ESSID in the file:
sudo vi /etc/Wireless/RT2870STA/RT2870STA.dat
Changed ESSID=... to ESSID=linksys (this is an example)

Now reboot.

If all goes well, you will see the usb wireless device green led flashing.
Next use the command iwconfig:

Output should be somewhat similar to:

marcel@marcel-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:"linksys"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:18:F8:7A:35:DC   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-53 dBm  Noise level:-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Now use your network manager like wicd and enter ra0 as device to manage.

Thats it, now you should have a wireless internet connection.

Let me know what you think of this tutorial!

---

