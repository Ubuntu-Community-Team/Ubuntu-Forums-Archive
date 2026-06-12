---
title: "HOWTO: TrueMobile 1180 USB and ALL prism2_usb based cards"
date: 2009-11-25
forum: Networking &amp; Wireless
---

### Post by opt1k on 2009-11-25
Update:::
If you are brave and want the updated firmware permanently flashed to your card please view:
[http://linux.junsun.net/intersil-prism/](http://linux.junsun.net/intersil-prism/)

The firmware on the truemobile devices appears to be very buggy even in windows, and it also has horrible range.  These issues are addressed in newer versions of the prism2 firmware.

Read that howto for information on flashing.

______________________________
Module Install Guide
______________________________


Truemobile 1180 USB prism2 version:
I bought one of these cards off ebay for $3.00 hoping it would work right. 

My god what a nightmare!.

The default prism2_usb, and ndiswrapper were very flaky on this card without the proper firmware.

___________________
note: I know about 
linux-wlan-ng-firmware - firmware files used by the linux-wlan-ng driver
It does not include the firmware needed for this device.
___________________


So here is what you need to do...

open up your terminal.

1. get a root prompt

$ sudo bash

2. lets work in /root

# cd /root

3. Get the this big firmware bzip tarball

# wget [http://www.red-bean.com/~proski/firmware/Latest-prism.tar.bz2](http://www.red-bean.com/~proski/firmware/Latest-prism.tar.bz2)

4. Extract

# bzip2 -d Latest-prism.tar.bz2 ; tar xvf Latest-prism.tar

5. We need the Firmware for the Truemobile card 'prism2_ru.hex' in /lib/firmware so we will copy ru010803.hex to /lib/firmware/prism2_ru.hex since that is the file modprobe will be looking for...

# cp `find ./Latest-prism -name ru010803.hex` /lib/firmware/prism2_ru.hex

6. Load the module and test the adapter out!

# modprobe prism2_usb ; dmesg | grep prism2_usb ; sleep 4 ; iwlist scan

You should see something like:

[  136.731764] prism2_usb: module is from the staging directory, the quality is unknown, you have been warned.
[  136.741482] prism2_usb: Checking for firmware prism2_ru.hex
[  136.857291] prism2_usb: prism2_ru.hex will be processed, size 177560
[  139.483864] prism2_usb: firmware loading finished.
[  140.584456] usbcore: registered new interface driver prism2_usb

root@user-desktop:/root# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: *********************
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:off
                    ESSID:"print server"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=000004f6f590b041
                    Extra: Last beacon: 1690ms ago
                    IE: Unknown: 00137072696E742073657276657220313439303939
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 06020000



7. Good so lets add it to our startup modules list

# echo prism2_usb >> /etc/modules

(alternatively you can add the whole modprobe prism2_usb line to your rc.local)


8. Enjoy!



Lazy Install:

$ sudo bash
# cd /root
# wget [http://www.red-bean.com/~proski/firmware/Latest-prism.tar.bz2](http://www.red-bean.com/~proski/firmware/Latest-prism.tar.bz2)
# bzip2 -d Latest-prism.tar.bz2 ; tar xvf Latest-prism.tar
# cp `find ./Latest-prism -name ru010803.hex` /lib/firmware/prism2_ru.hex
# modprobe prism2_usb ; dmesg | grep prism2_usb ; sleep 4 ; iwlist scan
# echo prism2_usb >> /etc/modules

---

### Post by tormod on 2010-05-28
In 10.04 you just need to install the prism2-usb-firmware-installer package and the firmware will be downloaded and installed automatically.

For earlier releases, you need to install linux-wlan-ng-firmware _and_ run linux-wlan-ng-build-firmware-deb, then install the .deb package that will be produced. However there was a bug in Karmic (bug 478874) and although there is a fix available it has not been uploaded by the SRU team. Anyway installing the Lucid prism2-usb-firmware-installer package in Karmic works fine also.

---

