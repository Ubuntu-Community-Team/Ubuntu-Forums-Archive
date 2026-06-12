---
title: "realtek usb wireless adapter"
date: 2011-01-14
forum: Networking &amp; Wireless
---

### Post by gandaran on 2011-01-14
[CENTER]> Bus 001 Device 007: ID 0bda:8171 Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter
this adapter shows up in network manager when connected to computer but doesn't detect network and cant connect to any network I have setup in nm, the adapter works fine in windows and it's supposed to work in linux or do I have to install drivers?[/CENTER]

---

### Post by Diehardshorty on 2011-01-14
Try this link it helped me get my card recognized and install the drivers also find wifi networks

[http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html](http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html)

---

### Post by chili555 on 2011-01-14
This device is supposed to work with the driver r8192s_usb that's already in recent kernels. Often, firmware is needed. Please open Applications > Accessories > Terminal and run and post:```
dmesg | grep 819
```Thanks.

---

### Post by Diehardshorty on 2011-01-14
Edit: Double post woops

---

### Post by gandaran on 2011-01-15
> **chili555 said:**
> This device is supposed to work with the driver r8192s_usb that's already in recent kernels. Often, firmware is needed. Please open Applications > Accessories > Terminal and run and post:```
dmesg | grep 819
```Thanks.
> mfp@MSI:~$ dmesg | grep 819
[    0.000000]       .init : 0xc0819000 - 0xc08c5000   ( 688 kB)
[  448.557965] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[  448.571736] Linux kernel driver for RTL8192 based WLAN cards
[  448.759937] usbcore: registered new interface driver rtl819xU
[  448.812956] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[  448.813198] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[  448.826327] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[  448.826575] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[  448.826582] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[  448.853296] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[  448.853627] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[  448.868137] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[  448.868471] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[  448.868478] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
mfp@MSI:~$ 


so looks like firmware is needed?

---

### Post by chili555 on 2011-01-15
The driver is looking for the firmware in /lib/firmware/RTL8192SU. You may have the firmware in RTL8192S[COLOR="Red"]E[/COLOR]. Check with:```
ls /lib/firmware/RTL8192SE
```If you find this:> rtl8192sfw492.bin  rtl8192sfw74.bin  rtl8192sfw.binThen you have the needed firmware in another directory. Let's make a new directory and copy over the firmware:```
sudo mkdir /lib/firmware/RTL8192SU
sudp cp /lib/firmware/RTL8192SE/* /lib/firmware/RTL8192SU
```Now remove and reload the driver module:```
sudo rmmod -f r8192s_usb
sudo modprobe r8192s_usb
```Are things working now?

---

### Post by gandaran on 2011-01-15
> **chili555 said:**
> The driver is looking for the firmware in /lib/firmware/RTL8192SU. You may have the firmware in RTL8192S[COLOR="Red"]E[/COLOR]. Check with:```
ls /lib/firmware/RTL8192SE
```If you find this:Then you have the needed firmware in another directory. Let's make a new directory and copy over the firmware:```
sudo mkdir /lib/firmware/RTL8192SU
sudp cp /lib/firmware/RTL8192SE/* /lib/firmware/RTL8192SU
```Now remove and reload the driver module:```
sudo rmmod -f r8192s_usb
sudo modprobe r8192s_usb
```Are things working now?
not yet but nearly :D
the wireless adapter can see networks now and tries to connect, I enter the wpa password and it tries to connect but doesn't and asks again for the password confirmation.
thanks for the help.

---

### Post by chili555 on 2011-01-15
Is your network WPA, WPA2 or the dreaded mixed WPA *and* WPA2 mode? Can you change to WPA2 alone?

EDIT:

d00d! Does this sound like your problem?  [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html)

Post back if you need guidance getting the proper firmware downloaded and installed. Sorry, I just found this.

---

### Post by gandaran on 2011-01-16
> **chili555 said:**
> Is your network WPA, WPA2 or the dreaded mixed WPA *and* WPA2 mode? Can you change to WPA2 alone?

EDIT:

d00d! Does this sound like your problem?  [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html)

Post back if you need guidance getting the proper firmware downloaded and installed. Sorry, I just found this.
thank you for all the help 
now it's working very well with the new firmware:D
> wget [http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz](http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz)
gunzip rtl8192sfw.bin.gz
sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/

---

