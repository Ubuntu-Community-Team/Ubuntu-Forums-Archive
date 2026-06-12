---
title: "Canyon CNP-WF518N2 USB wireless on Meerkat X64 bit not connecting to wireless"
date: 2010-11-18
forum: Networking &amp; Wireless
---

### Post by wernerj on 2010-11-18
i have a canyon usb wireless adapter that im trying to get to work on my Ubuntu 10.10 X64-bit pc. i want to keep to 64bit as i believe that this is the way forward, i did plug it in on my 64bit Win7 pc and it works without any hassle.

i am pretty new to Linux. i have googled a bit and tried various things, but i just dont seem to get this working.

i have tried to add my wireless network physically but as soon as it "connects", it just disappear, ive also tried to change my WPA2 to other options on my router, and have the same issue. i dont want to open my router for all to see...

ive tried this website : [http://blog.xff.lt/2009/12/28/canyon-cnp-wf518n2-usb-wireless-linux/](http://blog.xff.lt/2009/12/28/canyon-cnp-wf518n2-usb-wireless-linux/)  

it gets me pretty close but i dont know if it is because im running 64 bit and the latest kernel? 

any assistance would greatly be appreciated.

---

### Post by chili555 on 2010-11-18
64-bit and Realtek 8192 series, eh? I know I'm gonna hate myself, but here goes. Let's start with some diagnostic tools. Please run and post:```
lsmod | grep 819
dmesg | grep 819
la -al /lib/firmware/RTL8192SU
```Thanks.

---

### Post by wernerj on 2010-11-20
hi there this is what i got
 lsmod | grep 819
r8192s_usb            287340  0 
eeprom_93cx6            1345  1 r8192s_usb
werner@werner-ubuntu64x:~$ dmesg | grep 819
[    0.000000]       .init : 0xc0819000 - 0xc08c4000   ( 684 kB)
[   12.543130] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[   12.549488] Linux kernel driver for RTL8192 based WLAN cards
[   12.770632] usbcore: registered new interface driver rtl819xU
[   17.725618] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   17.725865] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   17.738247] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   17.738492] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   17.738498] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   17.977998] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   17.978255] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   17.990440] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   17.990630] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   17.990637] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
werner@werner-ubuntu64x:~$ la -al /lib/firmware/RTL8192SU
ls: cannot access /lib/firmware/RTL8192SU: No such file or directory

thanks in advance for any assistance you can provide
werner

---

### Post by chili555 on 2010-11-20
As you can see, the firmware was not found and loaded. To fix that, first remove your device. Next, let's create the correct directory:```
sudo mkdir /lib/firmware/RT8192SU
```Then proceed as outlined in this post: [http://ubuntuforums.org/showpost.php?p=10130242&postcount=50](http://ubuntuforums.org/showpost.php?p=10130242&postcount=50)

Post back if you get stuck or if it doesn't work as expected.

---

