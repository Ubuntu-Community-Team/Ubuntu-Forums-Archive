---
title: "How to get working  HUAWEI Mobile Broadband, Model E1750 on UBUNTU 9.04"
date: 2009-08-21
forum: Networking &amp; Wireless
---

### Post by eeBus on 2009-08-21
I'm a newbie to Linux, but loving it!
I'm using a Lenovo S10e with Ubuntu Remix 9.04 loaded.
Wireless connectivity is fine, but mobile broadband is my problem.

I'm in Latvia and I'm trying to get the Huawei HSPA USB stick to work on my Linux system. This is a Pay As You Go USB 3G-modem as provided by the TELE2 telecomm provider here. The device is a 'multiple device' with PC installation being from the flash storage. PC installation is straight forward which installs a 'Tele2 Mobile Partner' application with which you can connect the modem, view usage statistics, send SMS messages and top up the credit. Closing the app, closes the modem connection.

I've tried following and implementing [www.draisberghof.de/usb_modeswitch]("http://www.draisberghof.de/usb_modeswitch") but that didn't help.

I've run usbsnoop to get the correct character string, but I can't get it to work on Ubuntu.

I hope someone can help.

---

### Post by GeorgeVita on 2009-08-21
Hi **eeBus**, welcome to this forum!

You can try the ideas from:
[http://ubuntuforums.org/showthread.php?t=1211787](http://ubuntuforums.org/showthread.php?t=1211787) (post#3)

You need first to find vendorID : productID using```
lsusb
```

If still facing problems, post your progress to follow up.

Regards,
George

---

### Post by eeBus on 2009-08-23
Thanks for your speedy reply!

Followed your suggestions of thread 1211787 post#3 but the modem still failed to connect.

I then followed the instructions in [https://wiki.ubuntu.com/NetworkManager/Hardware/3G/Probing#Testingyourmodem](https://wiki.ubuntu.com/NetworkManager/Hardware/3G/Probing#Testingyourmodem) but with no success.

Here are the details!

udev-extras was already installed.
    Reading state information... Done
    udev-extras is already the newest version.
    0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Added the custom udev rules. Surprisingly the E1750 had the same product number as the E1550!

    echo 'SUBSYSTEM=="usb", SYSFS{idProduct}=="1446", SYSFS{idVendor}=="12d1", RUN+="/lib/udev/modem-modeswitch --vendor 0x12d1 --product 0x1446 --type option-zerocd"' | sudo tee  /etc/udev/rules.d/45-huawei1550.rules

Before E1750 plugged in.
boa@alslinux:~$ lsusb
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 002: ID 5986:0241 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2150 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
boa@alslinux:~$ 

After E1750 plugged in
boa@alslinux:~$ lsusb
Bus 001 Device 005: ID 12d1:1446 Huawei Technologies Co., Ltd. 
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 002: ID 5986:0241 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2150 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

tail end of dmesg
[10835.971166] sd 18:0:0:0: [sdc] Attached SCSI removable disk
[10835.973492] sd 18:0:0:0: Attached scsi generic sg2 type 0
[10882.130369] usb 1-2: USB disconnect, address 11
[11008.776156] usb 1-2: new high speed USB device using ehci_hcd and address 12
[11008.916871] usb 1-2: configuration #1 chosen from 1 choice
[11008.922025] scsi19 : SCSI emulation for USB Mass Storage devices
[11008.924981] usb-storage: device found at 12
[11008.924994] usb-storage: waiting for device to settle before scanning
[11008.925298] scsi20 : SCSI emulation for USB Mass Storage devices
[11008.928117] usb-storage: device found at 12
[11008.928131] usb-storage: waiting for device to settle before scanning
[11011.113406] usb 1-2: usbfs: process 9998 (modem-modeswitc) did not claim interface 0 before use
[11013.925472] usb-storage: device scan complete
[11013.926352] scsi 20:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
[11013.935433] sd 20:0:0:0: [sdc] Attached SCSI removable disk
[11013.938082] sd 20:0:0:0: Attached scsi generic sg2 type 0
[11441.319424] usbcore: registered new interface driver usbserial
[11441.319507] USB Serial support registered for generic
[11441.319646] usbserial_generic 1-2:1.0: generic converter detected
[11441.319970] usb 1-2: generic converter now attached to ttyUSB0
[11441.323126] usbcore: registered new interface driver usbserial_generic
[11441.323144] usbserial: USB Serial Driver core

Then tried all sorts of configurations for the Network Manager. None of which gave a connection.

Prior to contacting the forum I did try to install the application from the USB flash storage using Wine.
The application (Tele2 Mobile Partner) installation always failed . (It would start the setup, fail to show the license agreement, not allow the 'agree' button to be pressed, then kill the window)

Following the Network Manager probing instructions, wvdial gives:
boa@alslinux:~$ lsusb
Bus 001 Device 016: ID 12d1:1446 Huawei Technologies Co., Ltd. 
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 002: ID 5986:0241 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2150 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
boa@alslinux:~$ sudo wvdial cellular
[sudo] password for boa: 
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Cannot open /dev/ttyUSB0: No such device
--> Cannot get information for serial port.
--> Cannot open /dev/ttyUSB0: No such device
--> Cannot get information for serial port.
--> Cannot open /dev/ttyUSB0: No such device
boa@alslinux:~$ 

By the way I have noticed that every time I unplug and reinsert the USB stick the Device number increases. Is there a clue here?

Thanks once again
eeBus

---

### Post by GeorgeVita on 2009-08-23
Hi **eeBus**, you need to do some tests in order to learn and find out what is happening:

1. check contents of file created: ```
sudo cat /etc/udev/rules.d/45-huawei1550.rules
```
2. **boot without** modem, **wait** for the system to load, **attach** modem, **wait** 15 seconds, open a terminal window:  ```
dmesg | grep ttyU
``` ```
ls /dev/ttyU*
```
3. check if port created is useful:
If you have at least /dev/ttyUSB (you must also have /dev/ttyUSB1) try again 'sudo wvdial ...' (just to see if it sees the /dev/ttyUSB0 port).

4. try new N.M. setup:
Delete any existing mobile broadband connection (right click n.m. icon, edit connections, mobile broadband, click on any provider, delete) and try adding  a new one. Check APN, username, password.
N.M. default settings: **Latvia Tele2** APN=**internet.tele2.lv** user=**gprs** pass=**internet**

DO NOT USE wine and the windows s/w. In any faulty try (for this 'test' period) better reboot.

Regards,
George

---

### Post by eeBus on 2009-08-23
Hi George,

 1. check contents of file created: ```
sudo cat /etc/udev/rules.d/45-huawei1550.rules
```

boa@alslinux:~$ sudo cat /etc/udev/rules.d/45-huawei1550.rules
[sudo] password for boa: 
SUBSYSTEM=="usb", SYSFS{idProduct}=="1446", SYSFS{idVendor}=="12d1", RUN+="/lib/udev/modem-modeswitch --vendor 0x12d1 --product 0x1446 --type option-zerocd"
boa@alslinux:~$ 


2. **boot without** modem, **wait** for the system to load, **attach** modem, **wait** 15 seconds,
Done

boa@alslinux:~$ dmesg | grep ttyU
Nothing returned. Just came back to the command prompt.

boa@alslinux:~$ ls /dev/ttyU*
ls: cannot access /dev/ttyU*: No such file or directory
boa@alslinux:~$

Hmmm. So no device!
Didn't do any further tests!

boa@alslinux:~$ lsusb
Bus 001 Device 005: ID 12d1:1446 Huawei Technologies Co., Ltd. 
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 002: ID 5986:0241 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2150 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Just so that you can see that the modem is connected!

Cheers
eeBus

---

### Post by GeorgeVita on 2009-08-23
Hi again,
check **lsusb** again, when you see the modem (12d1:1446), run the command manually:```
/lib/udev/modem-modeswitch --vendor 0x12d1 --product 0x1446 --type option-zerocd
``` wait some seconds and test [B]ls /dev/ttyU*[/B
If nothing yet, try:```
sudo modprobe usbserial vendor=0x12d1 product=0x1446
```and check again **ls /dev/ttyU***

If nothing of above work BUT you see any CD-DRIVE appeared try to eject it manually and check again **ls /dev/ttyU*** (or last lines of dmesg).

We want to see the ports created!

I cannot understand why it worked fine with other users at:
[http://ubuntuforums.org/showthread.php?t=1211787](http://ubuntuforums.org/showthread.php?t=1211787)

Possibly you could post a question there (additional to our tries).

G

---

### Post by eeBus on 2009-08-23
Hi George,

Thanks for your time and patience! Here are the results of the latest tests.

boa@alslinux:~$ lsusb
Bus 001 Device 005: ID 12d1:1446 Huawei Technologies Co., Ltd. 
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 002: ID 5986:0241 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2150 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
boa@alslinux:~$ /lib/udev/modem-modeswitch --vendor 0x12d1 --product 0x1446 --type option-zerocd
boa@alslinux:~$ ls /dev/ttyU*
ls: cannot access /dev/ttyU*: No such file or directory
boa@alslinux:~$ sudo modprobe usbserial vendor=0x12d1 product=0x1446
[sudo] password for boa: 
boa@alslinux:~$ ls /dev/ttyU*
/dev/ttyUSB0
boa@alslinux:~$ 

So! Do we see a port now?

I cannot understand why it worked fine with other users at:
[http://ubuntuforums.org/showthread.php?t=1211787](http://ubuntuforums.org/showthread.php?t=1211787)

Possibly you could post a question there (additional to our tries).
I don't understand it too. I'll post a question to Macchi.
I wonder if the problem is because the device is Pre-Pay, and I don't know what the "Tele2 Mobile Partner" does, and interfaces with the device.

B4N
eeBus


G[/quote]

---

### Post by GeorgeVita on 2009-08-23
Just /dev/ttyUSB0 possibly is not good.

Now our options to try are:

1. manual setup on NM icon (right click, edit connections, mobile broadband, add, ...) and then see if it shows your connection to try it (left click on icon, click on providers name).
2. 'terminal' alternative, as wvdial (is not included as standard, and you must follow instructions from link at my signature)
3. 'I feel lucky' terminal command, when you have /dev/ttyUSB0:```
pppd ttyUSB0 nodetach defaultroute noipdefault lock usepeerdns connect 'chat "" "at" "" "at" "OK" "at&f" "OK" "atz" "OK" "at+cgdcont=1,'IP','internet.tele2.lv'" OK "atdt*99***1#" CONNECT' user gprs password internet
``` (copy all above to terminal & press enter. If not connected press CTRL-C and retry)

4. Wait for some help from others with the same modem

Regards,
George

---

### Post by eeBus on 2009-08-23
No joy with the Network Manager option.

I feel lucky didn't work. I tried all sorts of options as you can see.

wvdial is as you can see, modem not responding. 

Thanks for your help, and let's see if Macchi has any ideas!

Cheers
eeBus


[  537.910344] usbcore: registered new interface driver usbserial
[  537.910399] USB Serial support registered for generic
[  537.910489] usbserial_generic 1-2:1.0: generic converter detected
[  537.910707] usb 1-2: generic converter now attached to **ttyUSB0**
[  537.910756] usbcore: registered new interface driver usbserial_generic
[  537.910764] usbserial: USB Serial Driver core
[ 1970.197231] ACPI: EC: GPE storm detected, transactions will use polling mode
[ 1971.700931] ACPI: EC: missing confirmations, switch off interrupt mode.
[ 2275.663745] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f4f1c000
[ 2276.483019] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f4f1c000
[ 2277.716429] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f4f1c000
[ 2281.398481] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f4f1c000
[ 2282.627234] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f4f1c000
[ 2283.446425] TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f4f1c000
boa@alslinux:~$ pppd ttyUSB0 nodetach defaultroute noipdefault lock usepeerdns connect 'chat "" "at" "" "at" "OK" "at&f" "OK" "atz" "OK" "at+cgdcont=1,'IP','internet.tele2.lv'" OK "atdt*99***1#" CONNECT' user gprs password internet
bash: /usr/sbin/pppd: Permission denied
boa@alslinux:~$ pppd ttyUSB0 nodetach defaultroute noipdefault lock usepeerdns connect 'chat "" "at" "" "at" "OK" "at&f" "OK" "atz" "OK" "at+cgdcont=1,'IP','internet.tele2.lv'" OK "atdt*99***1#" CONNECT' user wap password wap
bash: /usr/sbin/pppd: Permission denied
boa@alslinux:~$ pppd ttyUSB0 nodetach defaultroute noipdefault lock usepeerdns connect 'chat "" "at" "" "at" "OK" "at&f" "OK" "atz" "OK" "at+cgdcont=1,'IP','data.tele2.lv'" OK "atdt*99***1#" CONNECT' user wap password wap
bash: /usr/sbin/pppd: Permission denied
boa@alslinux:~$ pppd ttyUSB0 nodetach defaultroute noipdefault lock usepeerdns connect 'chat "" "at" "" "at" "OK" "at&f" "OK" "atz" "OK" "at+cgdcont=1,'IP','data.tele2.lv'" OK "atdt*99***1#" CONNECT' user gprs password internet
bash: /usr/sbin/pppd: Permission denied
boa@alslinux:~$ pppd ttyUSB0 nodetach defaultroute noipdefault lock usepeerdns connect 'chat "" "at" "" "at" "OK" "at&f" "OK" "atz" "OK" "at+cgdcont=1,'IP','data.tele2.lv'" OK "atdt*99#" CONNECT' user gprs password internet
bash: /usr/sbin/pppd: Permission denied
boa@alslinux:~$ pppd ttyUSB0 nodetach defaultroute noipdefault lock usepeerdns connect 'chat "" "at" "" "at" "OK" "at&f" "OK" "atz" "OK" "at+cgdcont=1,'IP','data.tele2.lv'" OK "atdt*99#" CONNECT' user wap password wap
bash: /usr/sbin/pppd: Permission denied
boa@alslinux:~$ pppd ttyUSB0 nodetach defaultroute noipdefault lock usepeerdns connect 'chat "" "at" "" "at" "OK" "at&f" "OK" "atz" "OK" "at+cgdcont=1,'IP','internet.tele2.lv'" OK "atdt*99#" CONNECT' user gprs password internet
bash: /usr/sbin/pppd: Permission denied
boa@alslinux:~$ pppd ttyUSB0 nodetach defaultroute noipdefault lock usepeerdns connect 'chat "" "at" "" "at" "OK" "at&f" "OK" "atz" "OK" "at+cgdcont=1,'IP','internet.tele2.lv'" OK "atdt*99#" CONNECT' user gprs password internet
bash: /usr/sbin/pppd: Permission denied

boa@alslinux:~$ sudo wvdial cellular
[sudo] password for boa: 
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.
boa@alslinux:~$

---

### Post by GeorgeVita on 2009-08-23
EDIT: I edited this post as more tests cannot give us a way, so concluding:

The most possible reason is that Huawei uses the same code for E1750 & E1550 (ZeroCD=12d1:1446) but internally (firmware) is different. Real modem must appear after 'ejecting' the ZeroCD or by 'switching' the device to modem state (**12d1:1001**) and then can be usbserial-ized to get the /dev/ttyUSBx communication ports.

A simple 'sudo eject srX' is OK (srX is the CD-ROM created after inserting modem) and can be implemented if kernel and other drivers are not exist. 
 
modem-modeswitch sends a 'rezero' command to the USB peripheral, but is this tested to E1750? The problem comes when some slight different models appear as 12d1:1446 and this command is not accepted.

usb_modeswitch uses a 'sync' stream of databytes that are different for every modem type and you need snoop/sniff program to 'catch' it. Probably searching internet we could find another user that already has configured usb_modeswitch for E1750 (my searches hit some chinese/hungarian/swedish posts and I couldn't determine the 'working' one).

Regards,
George

---

### Post by eeBus on 2009-08-24
Lots here for me to digest and try to understand!

>  The most possible reason is that Huawei uses the same code for E1750 & E1550 (ZeroCD=12d1:1446) but internally (firmware) is different.
Agreed.

> Real modem must appear after 'ejecting' the ZeroCD or by 'switching' the device to modem state (12d1:1001) and then can be usbserial-ized to get the /dev/ttyUSBx communication ports.
By ZeroCD do you mean the flash drive that contains the windows application and drivers?
Please note that inserting the device now does not bring up the flash drive. I assumed that this meant it had been switch to modem mode.

> A simple 'sudo eject srX' is OK (srX is the CD-ROM created after inserting modem) and can be implemented if kernel and other drivers are not exist.
I was able to eject the device from Nautilus before our work. I'm assuming that the 45-huawei1550.rules is responsible for the drive no longer appearing when I plug it in?

> modem-modeswitch sends a 'rezero' command to the USB peripheral, but is this tested to E1750? The problem comes when some slight different models appear as 12d1:1446 and this command is not accepted.

usb_modeswitch uses a 'sync' stream of databytes that are different for every modem type and you need snoop/sniff program to 'catch' it. Probably searching internet we could find another user that already has configured usb_modeswitch for E1750 (my searches hit some chinese/hungarian/swedish posts and I couldn't determine the 'working' one).

I followed 
[http://ubuntuforums.org/showthread.php?t=1193355&highlight=huawei+e1550+settings&page=3](http://ubuntuforums.org/showthread.php?t=1193355&highlight=huawei+e1550+settings&page=3) post 24

Attached is the UsbSnoop.log file, and below my attempt at deciphering the data

boa@alslinux:~/Desktop$ cat /etc/usb_modeswitch.conf
# /etc/usb_modeswitch.conf
#
# Last modified: 2009-06-09
#
# Configuration for usb_modeswitch, a mode switching tool for controlling
# flip flop (multiple device) USB gear
#
# Main purpose is to trigger the switching of several known UMTS modems
# from storage device mode ("ZeroCD TM" for use with MS Windows) to modem
# (serial) device mode
#
# Detailed instructions and a friendly forum on the homepage:
# [http://www.draisberghof.de/usb_modeswitch](http://www.draisberghof.de/usb_modeswitch)
#
# News update: you want to read the paragraph about troubleshooting there
# if you run into problems !!!

########################################################
# Huawei E1750
#

DefaultVendor = 0x12d1
DefaultProduct = 0x1446

MessageEndpoint = 0x01
MessageContent = "55534243000000000000000000000011060000000000000000000000000000"


boa@alslinux:~/Desktop$ 

Finally dmesg shows
[18716.018586] usb-storage: device found at 5
[18716.018598] usb-storage: waiting for device to settle before scanning
[18718.224100] usb 1-2: usbfs: **process 18949 (modem-modeswitc) did not claim interface 0** before use
[18721.017095] usb-storage: device scan complete

Is there a clue here that sic modem-modeswitc did not claim the interface?

Cheers
eeBus

---

### Post by GeorgeVita on 2009-08-24
> By ZeroCD do you mean the flash drive that contains the windows application and drivers?Yes.> Please note that inserting the device now does not bring up the flash drive. I assumed that this meant it had been switch to modem mode.ZeroCD ejected, not switched successfully as we do not get the communication ports.> I was able to eject the device from Nautilus before our work. I'm assuming that **the 45-huawei1550.rules is responsible for the drive no longer appearing** when I plug it in?Yes, but this method did not worked for your modem.> I followed [http://ubuntuforums.org/showthread.php?t=1193355&highlight=huawei+e1550+settings&page=3](http://ubuntuforums.org/showthread.php?t=1193355&highlight=huawei+e1550+settings&page=3) post 24 ...
```
# Huawei E1750

DefaultVendor = 0x12d1
DefaultProduct = 0x1446

MessageEndpoint = 0x01
MessageContent = "55534243000000000000000000000011060000000000000000000000000000"

``` according to above []("http://ubuntuforums.org/showpost.php?p=7533144&postcount=24") it seems FINE!

To test it you need to remove udev-extras and all .fdi files you have created (for modem-modeswitch & usb_modeswitch). You will try it manually waiting 10-15 seconds after attaching the modem. Check all files, reboot without modem, attach it, wait 15 seconds, check 'dmesg', 'lsusb', 'ls /dev/ttyU*',run usb_modeswitch, wait some seconds, check again dmesg etc.

Note: as I do not have your hardware, I am just giving ideas and provide 'brainstorming' on where could be the problem. Today I read all info from usb_modeswitch site & forum, I noticed some changes/additions they made for Huawei modems, but I think you are very close so first give it another try (usb_modeswitch).

Last version is: [http://www.draisberghof.de/usb_modeswitch/usb_modeswitch-1.0.4.tar.bz2](http://www.draisberghof.de/usb_modeswitch/usb_modeswitch-1.0.4.tar.bz2)
Last configuration file: [http://www.draisberghof.de/usb_modeswitch/usb_modeswitch.conf](http://www.draisberghof.de/usb_modeswitch/usb_modeswitch.conf)
Info: [http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

Below are '**part**' of **usb_modeswitch.conf** for **Huawei** modems: ```
# /etc/usb_modeswitch.conf (Last modified: 2009-08-24)
#
# * DetachStorageOnly <0/1>  -d
# Some devices just need to be detached from the usb-storage driver to initiate the mode switching. Using this feature
# instead of removing the whole usbstorage module keeps other storage devices working.
#
# * HuaweiMode <0/1>         -H
# Some Huawei devices can be switched by a special control message.
########################################################
# Huawei E220 (aka "Vodafone EasyBox II", aka "T-Mobile wnw Box Micro")
# Huawei E230, E270, E870 and probably most other Huawei devices (just adapt product ID)
# Two options: 1. removal of "usb-storage"  2. the special control
# message found by Miroslav Bobovsky Contributor: Hans Kurent, Denis Sutter, Vincent Teoh

;DefaultVendor=  0x12d1;
;DefaultProduct= 0x1003

# choose one of these:
;DetachStorageOnly=1
;HuaweiMode=1

########################################################
# Huawei E169
#
# Contributor: Dale Lane

;DefaultVendor=  0x12d1;
;DefaultProduct= 0x1001

# choose one of these:
;DetachStorageOnly=1
;HuaweiMode=1

########################################################
# Huawei E180
#
# Contributor: Tom Dawahare

;DefaultVendor=  0x12d1
;DefaultProduct= 0x1414

# choose one of these:
;DetachStorageOnly=1
;HuaweiMode=1

########################################################
# Huawei E630
# You might also try to use the Huawei sequence with it
# Beware: there are modem-only variants around - no storage, no switching necessary!
# Contributor: Joakim Wenrgren

;DefaultVendor=  0x1033
;DefaultProduct= 0x0035

;TargetVendor=   0x12d1
;TargetProduct=  0x1003

;DetachStorageOnly=1


```

Good Luck,
George

---

### Post by eeBus on 2009-08-24
Ah! How do I remove udev-extras and the .fdi files?

---

### Post by GeorgeVita on 2009-08-24
> **eeBus said:**
> Ah! How do I remove udev-extras and the .fdi files?

System > Administration > Synaptic Package Manager
type udev-extras at 'Quick search' window
when shown below right click on green box and 'Mark for Removal'

From your posts shown 2 .fdi files, delete them with: ```
sudo rm /etc/udev/rules.d/45-huawei1550.rules
sudo rm /etc/udev/rules.d/45-huawei1660.rules
```

Regards,
George

---

### Post by eeBus on 2009-08-24
I ended up doing sudo apt-get purge udev-extras
I'm assuming that is the same as synaptec.
I've rmed the files. So now I will SLOWLY and CAREFULLY work my way through the 3 links that you have provided.
Is that correct?

---

### Post by GeorgeVita on 2009-08-24
Yes. it is better to get the recent version and try your existed configuration file as it seems OK. Later if you do not succeed you are going to try new option as described to their newer .conf file (I mean DetachStorageOnly=1 AND/OR HuaweiMode=1 AND/OR message and endpoint)

G

---

### Post by eeBus on 2009-08-25
Because I'm on Ubuntu 9.04 I decided that I needed to recompile usb_modeswitch

I get lots of compilations errors because I don't know how to get the libusb to be used.

Synaptic shows that I have installed[INDENT]libusb-0.1-4 Canonical supported
libusb-1.0-0 not Canonical supported
[/INDENT]So how does the 
```
$ gcc -l usb -o usb_modeswitch usb_modeswitch.c
```know where to go?
What should be the command line?
What should I do with libusb?

---

### Post by GeorgeVita on 2009-08-25
> **eeBus said:**
> Because I'm on Ubuntu 9.04 I decided that I needed to recompile usb_modeswitch

I get lots of compilations errors because I don't know how to get the libusb to be used.

Synaptic shows that I have installed[INDENT]libusb-0.1-4 Canonical supported
libusb-1.0-0 not Canonical supported
[/INDENT]So how does the 
```
$ gcc -l usb -o usb_modeswitch usb_modeswitch.c
```know where to go?
What should be the command line?
What should I do with libusb?

Sorry I do not know how to do above action! Just ideas: Find a 'ready one' .deb from other ubuntu user and/or open a new thread asking help.

G

---

### Post by eeBus on 2009-08-25
This reply posted using the E1750 modem!!! :)

It was not easy, but thank you for your help, patience and persistence!

I'll try to document everything so that there is a record for the forum!!!

(It will probably be next week)

Thank you once again....

I can't really believe it...

The next challenge will be to emulate the MS windows "Mobile Partner" so that I can apply credit via SMS.

Cheers
eeBu2

---

### Post by GeorgeVita on 2009-08-25
> **eeBus said:**
> This reply posted using the E1750 modem!!! :)
... I'll try to **document** everything so that there is a record for the forum!!!

Well Done! It would be very helpful to make your HowTo!

Regards,
George

---

### Post by jumpingfrog on 2009-09-27
Hi all,
i was wondering if you could help me to connect my usb internet key(E1750) on ubuntu 8( I need a old version of ubuntu ).
I see your answer on ubuntu 9 but I didn't understand it(too deep on ubunto and lack of my english). Anyway I hope you could give me a clue in order to solve my problem and not return to Wintrash-xp.
This is what i did:
sudo gedit /etc/wvdial.conf
then I pasted this:
[Dialer Defaults]
Modem = /dev/ttyUSB0
ISDN = offModem
Type = AnalogModem
Baud = 460800
#Init = AT+CPIN= xxxxxxx
Init2 = ATX3
Init3 = AT+COPS?
Init4 = AT+CGDCONT=1,”ip”,”tre.it”
Phone = *99#
Dial Attempts = 1
Dial Command = ATM1L3DT
Ask Password = off
Password = tre
Username = tre
Auto Reconnect = off
Abort on Busy = off
Carrier Check = on
Check Def Route = on
Abort on No Dialtone = on
Stupid Mode = on
Idle Seconds = 0
Auto DNS = on
saved and closed the file, then:
sudo gedit /etc/resolv.conf
Pasted the followng ns:
nameserver 62.13.171.1
nameserver 62.13.171.2
Then: sudo wvdial
This is the error:
-->Wvdial: internet dialer version 1.68
-->Cannot opern /dev/ttyUSB0: no such file or directory
Any clue? I tried also with manual network configuration but i cannot see it as modem!
 
I just see it as HardDrive on my desktop
:confused:

---

### Post by GeorgeVita on 2009-09-27
Hi **jumpingfrog**,
you must first determine what system activity occur after inserting the modem, so try the following:
- Boot ubuntu 8.xx (**which one will be used?)**
- **wait** for the system to load
- open a **terminal** window (Applications > Accessories > Terminal)```
sudo dmesg -c
```
- attach your modem, **wait** 20 seconds ```
lsusb
``` ```
dmesg
``` ```
uname -a
```
- post here: Ubuntu version and the output of above commands (**except** sudo dmesg -c)

Next steps: If any CDROM appear you must 'eject it', check **lsusb** for a new vendorID : productID and then try to create any communication port ('sudo modprobe usbserial vendor=0xVVVV product=0xPPPP')

Regards,
George

---

### Post by jumpingfrog on 2009-09-27
The version installed is: ubuntu-8.04.3-desktop-i386.iso
 
Here's the spool:
 
massimo@massimo-laptop:~$ dmesg -c
klogctl: Operation not permitted
massimo@massimo-laptop:~$ sudo dmesg -c
[sudo] password for massimo: 
[ 19.455450] sd 0:0:0:0: Attached scsi generic sg0 type 0
[ 19.455487] sr 1:0:0:0: Attached scsi generic sg1 type 5
[ 19.489185] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[ 19.489194] Uniform CD-ROM driver Revision: 3.20
[ 19.489275] sr 1:0:0:0: Attached scsi CD-ROM sr0
[ 19.741147] Attempting manual resume
[ 19.741153] swsusp: Resume From Partition 8:5
[ 19.741155] PM: Checking swsusp image.
[ 54.462919] [drm] writeback test succeeded in 1 usecs
[ 136.262635] ACPI: EC: non-query interrupt received, switching to interrupt mode
.... 
massimo@massimo-laptop:~$ lsusb
Bus 004 Device 002: ID 12d1:1446 Huawei Technologies Co., Ltd. 
Bus 004 Device 001: ID 0000:0000 
Bus 003 Device 001: ID 0000:0000 
Bus 002 Device 001: ID 0000:0000 
Bus 001 Device 001: ID 0000:0000 
 
massimo@massimo-laptop:~$ dmesg 
[ 423.704493] usb 4-1: new high speed USB device using ehci_hcd and address 2
[ 423.839059] usb 4-1: configuration #1 chosen from 1 choice
[ 424.229164] usbcore: registered new interface driver libusual
[ 424.291769] Initializing USB Mass Storage driver...
[ 424.296072] scsi2 : SCSI emulation for USB Mass Storage devices
[ 424.303758] usb-storage: device found at 2
[ 424.303766] usb-storage: waiting for device to settle before scanning
[ 424.306530] scsi3 : SCSI emulation for USB Mass Storage devices
[ 424.315742] usbcore: registered new interface driver usb-storage
[ 424.315753] USB Mass Storage support registered.
[ 424.316456] usb-storage: device found at 2
[ 424.316461] usb-storage: waiting for device to settle before scanning
[ 429.297881] usb-storage: device scan complete
[ 429.298631] scsi 2:0:0:0: CD-ROM HUAWEI Mass Storage 2.31 PQ: 0 ANSI: 2
[ 429.314772] usb-storage: device scan complete
[ 429.316352] scsi 3:0:0:0: Direct-Access HUAWEI SD Storage 2.31 PQ: 0 ANSI: 2
[ 429.319058] sr1: scsi-1 drive
[ 429.319141] sr 2:0:0:0: Attached scsi CD-ROM sr1
[ 429.319200] sr 2:0:0:0: Attached scsi generic sg2 type 5
[ 429.320900] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[ 429.321336] sd 3:0:0:0: Attached scsi generic sg3 type 0
[ 441.435790] ISO 9660 Extensions: Microsoft Joliet Level 1
[ 441.437172] ISOFS: changing to secondary root
 
massimo@massimo-laptop:~$ uname -a
Linux massimo-laptop 2.6.24-24-generic #1 SMP Tue Jul 7 19:46:39 UTC 2009 i686 GNU/Linux
 
 
It seems that ubuntu recognize the usbmodem but i tried differente ttyusb0 , tty001 and so on but still i cant see it. :confused:
Maybe it s so easy but i dont really know how to do

---

### Post by GeorgeVita on 2009-09-27
> **jumpingfrog said:**
> ...
Bus 004 Device 002: ID **12d1:1446** Huawei Technologies Co., Ltd. 
...
[  429.298631] scsi 2:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[  429.314772] usb-storage: device scan complete
[  429.316352] scsi 3:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
[  429.319058] sr1: scsi-1 drive
[  429.319141] sr 2:0:0:0: Attached scsi CD-ROM [SIZE="3"]**sr1**[/SIZE]
[  429.319200] sr 2:0:0:0: Attached scsi generic sg2 type 5
[  429.320900] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[  429.321336] sd 3:0:0:0: Attached scsi generic sg3 type 0
[  441.435790] ISO 9660 Extensions: Microsoft Joliet Level 1
[  441.437172] ISOFS: changing to secondary root
...
Linux massimo-laptop **2.6.24-24-generic #1** SMP Tue Jul 7 19:46:39 UTC 2009 i686 GNU/Linux

Repeat above, check **sr1** (or any other like sr0 or sr2) and eject it: ```
sudo eject sr1
```Try again **lsusb** to see any new productID (12d1:ABCD) and use this to: ```
sudo modprobe usbserial vendor=0x12d1 product=0xABCD
``` (replace ABCD with the productID from last **lsusb** command). Finally check for the ports: ```
ls /dev/ttyU*
```

Good Luck!
G

---

### Post by jumpingfrog on 2009-09-28
Hi George, 
im sorry to bother you again but i got an error probing the modem and i don't know if I made a mistake. Here s the output after ejecting the CD ROM:
 
[EMAIL="massimo@massimo-laptop:~$"]massimo@massimo-laptop:~$[/EMAIL] sudo eject sr0
[EMAIL="massimo@massimo-laptop:~$"]massimo@massimo-laptop:~$[/EMAIL] lsusb
Bus 004 Device 002: ID 12d1:1446 Huawei Technologies Co., Ltd. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
[EMAIL="massimo@massimo-laptop:~$"]massimo@massimo-laptop:~$[/EMAIL] sudo modprobe usbserial vendor-0x12d1 product-1446
FATAL: Error inserting usbserial (/lib/modules/2.6.24-24-generic/kernel/drivers/usb/serial/usbserial.ko): Unknown symbol in module, or unknown parameter (see dmesg)
[EMAIL="massimo@massimo-laptop:~$"]massimo@massimo-laptop:~$[/EMAIL] dmesg
[  324.888107] usb 4-1: new high speed USB device using ehci_hcd and address 2
[  325.022471] usb 4-1: configuration #1 chosen from 1 choice
[  325.466548] usbcore: registered new interface driver libusual
[  325.531265] Initializing USB Mass Storage driver...
[  325.535526] scsi2 : SCSI emulation for USB Mass Storage devices
[  325.540818] usb-storage: device found at 2
[  325.540825] usb-storage: waiting for device to settle before scanning
[  325.547695] scsi3 : SCSI emulation for USB Mass Storage devices
[  325.549806] usbcore: registered new interface driver usb-storage
[  325.549817] USB Mass Storage support registered.
[  325.550487] usb-storage: device found at 2
[  325.550494] usb-storage: waiting for device to settle before scanning
[  330.533093] usb-storage: device scan complete
[  330.534089] scsi 2:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[  330.550641] usb-storage: device scan complete
[  330.552058] scsi 3:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
[  330.554895] sr1: scsi-1 drive
[  330.554978] sr 2:0:0:0: Attached scsi CD-ROM sr1
[  330.555037] sr 2:0:0:0: Attached scsi generic sg2 type 5
[  330.556612] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[  330.556906] sd 3:0:0:0: Attached scsi generic sg3 type 0
[  342.072374] ISO 9660 Extensions: Microsoft Joliet Level 1
[  342.073632] ISOFS: changing to secondary root
[  477.164887] usbserial: Unknown parameter `vendor-0x12d1'
 
Any help?

---

### Post by GeorgeVita on 2009-09-29
> **jumpingfrog said:**
> ... sudo eject **[SIZE="3"]sr0[/SIZE]**
...
sudo modprobe usbserial vendor[COLOR="Red"]**[SIZE="4"]-[/SIZE]**[/COLOR]0x12d1 product[COLOR="Red"]**[SIZE="4"]-[/SIZE]**[/COLOR]1446
...
... (from dmesg shown as **sr1**)
[  330.533093] usb-storage: device scan complete
[  330.534089] scsi 2:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[  330.550641] usb-storage: device scan complete
[  330.552058] scsi 3:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
[  330.554895] sr1: scsi-1 drive
[  330.554978] sr 2:0:0:0: Attached scsi **[SIZE="3"]CD-ROM sr1[/SIZE]**

First try to understand the steps and then try them:
- **lsusb** lists all USB peripherals and their vendorID : productID
(a Huawei modem is listed as 12d1 : xxxx)
- **dmesg** shows all system activity and at this point you need to determine the name of Huawei virtual **CD-ROM** (above shown as **sr1** and not sr0)
- **sudo dmesg -c** shows all system activity and **clears** it. Next dmesg will have just the 'new' system activity (less to read) so it can be used some seconds after every step (attachment of modem, eject of virtual drive, modprobe usbserial) to check the results.
- **sudo modprobe ...** command needs **=** after the parameter name and **you must use the latest from lsusb AFTER ejecting** the correct CD-ROM

Read again my previous post, and try!

**[size=3][COLOR="DarkSlateBlue"]Edit:[/COLOR][/size]** above tested with 8.04.2 LiveUSB and worked for my ZTE MF636.
More at: [http://ubuntuforums.org/showpost.php?p=8026271&postcount=61](http://ubuntuforums.org/showpost.php?p=8026271&postcount=61)

Regards,
George

---

### Post by jumpingfrog on 2009-09-29
I hope you ll be not mad at me. I saw all my mistake but I still can get it right. 
I did eject the sr1 but so far it keeps to attach srx+1.....
 
[EMAIL="massimo@massimo-laptop:~$"]massimo@massimo-laptop:~$[/EMAIL] sudo dmesg -c
[ 2356.393084] usb 4-3: USB disconnect, address 6
[ 2362.149524] usb 4-3: new high speed USB device using ehci_hcd and address 7
[ 2362.284087] usb 4-3: configuration #1 chosen from 1 choice
[ 2362.318156] scsi12 : SCSI emulation for USB Mass Storage devices
[ 2362.320508] usb-storage: device found at 7
[ 2362.320515] usb-storage: waiting for device to settle before scanning
[ 2362.337295] scsi13 : SCSI emulation for USB Mass Storage devices
[ 2362.338289] usb-storage: device found at 7
[ 2362.338296] usb-storage: waiting for device to settle before scanning
[ 2367.311532] usb-storage: device scan complete
[ 2367.312783] scsi 12:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[ 2367.334464] sr2: scsi-1 drive
[ 2367.334568] sr 12:0:0:0: Attached scsi CD-ROM sr2
[ 2367.334633] sr 12:0:0:0: Attached scsi generic sg2 type 5
[ 2367.342700] usb-storage: device scan complete
[ 2367.344104] scsi 13:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
[ 2367.346182] sd 13:0:0:0: [sdb] Attached SCSI removable disk
[ 2367.346599] sd 13:0:0:0: Attached scsi generic sg3 type 0
[ 2378.591468] ISO 9660 Extensions: Microsoft Joliet Level 1
[ 2378.592848] ISOFS: changing to secondary root
[ 2417.257786] usb 4-3: USB disconnect, address 7
[ 2422.122833] usb 4-3: new high speed USB device using ehci_hcd and address 8
[ 2422.257370] usb 4-3: configuration #1 chosen from 1 choice
[ 2422.292862] scsi14 : SCSI emulation for USB Mass Storage devices
[ 2422.299424] usb-storage: device found at 8
[ 2422.299431] usb-storage: waiting for device to settle before scanning
[ 2422.310699] scsi15 : SCSI emulation for USB Mass Storage devices
[ 2422.326738] usb-storage: device found at 8
[ 2422.326746] usb-storage: waiting for device to settle before scanning
[ 2427.292679] usb-storage: device scan complete
[ 2427.293554] scsi 14:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[ 2427.321350] sr3: scsi-1 drive
[ 2427.321450] sr 14:0:0:0: Attached scsi CD-ROM sr3
[ 2427.321514] sr 14:0:0:0: Attached scsi generic sg2 type 5
[ 2427.336012] usb-storage: device scan complete
[ 2427.337362] scsi 15:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
[ 2427.339301] sd 15:0:0:0: [sdb] Attached SCSI removable disk
[ 2427.339723] sd 15:0:0:0: Attached scsi generic sg3 type 0
[ 2438.525048] ISO 9660 Extensions: Microsoft Joliet Level 1
[ 2438.526440] ISOFS: changing to secondary root
[ 2441.552409] usb 4-3: USB disconnect, address 8
[ 2474.613977] usb 4-3: new high speed USB device using ehci_hcd and address 9
[ 2474.748338] usb 4-3: configuration #1 chosen from 1 choice
[ 2474.783725] scsi16 : SCSI emulation for USB Mass Storage devices
[ 2474.789980] usb-storage: device found at 9
[ 2474.789989] usb-storage: waiting for device to settle before scanning
[ 2474.801768] scsi17 : SCSI emulation for USB Mass Storage devices
[ 2474.809876] usb-storage: device found at 9
[ 2474.809884] usb-storage: waiting for device to settle before scanning
[ 2479.784394] usb-storage: device scan complete
[ 2479.785267] scsi 16:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[ 2479.807303] sr4: scsi-1 drive
[ 2479.807407] sr 16:0:0:0: Attached scsi CD-ROM sr4
[ 2479.807470] sr 16:0:0:0: Attached scsi generic sg2 type 5
[ 2479.815135] usb-storage: device scan complete
[ 2479.816466] scsi 17:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
[ 2479.818409] sd 17:0:0:0: [sdb] Attached SCSI removable disk
[ 2479.818832] sd 17:0:0:0: Attached scsi generic sg3 type 0
[ 2492.503025] ISO 9660 Extensions: Microsoft Joliet Level 1
[ 2492.504362] ISOFS: changing to secondary root
[ 2607.966321] usb 4-3: USB disconnect, address 9

---- here i did plug the usb internet key
 
[EMAIL="massimo@massimo-laptop:~$"]massimo@massimo-laptop:~$[/EMAIL] dmesg
[ 2659.543330] usb 4-3: new high speed USB device using ehci_hcd and address 10
[ 2659.677716] usb 4-3: configuration #1 chosen from 1 choice
[ 2659.712242] scsi18 : SCSI emulation for USB Mass Storage devices
[ 2659.719339] usb-storage: device found at 10
[ 2659.719347] usb-storage: waiting for device to settle before scanning
[ 2659.731086] scsi19 : SCSI emulation for USB Mass Storage devices
[ 2659.732122] usb-storage: device found at 10
[ 2659.732128] usb-storage: waiting for device to settle before scanning
[ 2664.713150] usb-storage: device scan complete
[ 2664.714024] scsi 18:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[ 2664.733963] usb-storage: device scan complete
[ 2664.734355] sr5: scsi-1 drive
[ 2664.734448] sr 18:0:0:0: Attached scsi CD-ROM sr5
[ 2664.734510] sr 18:0:0:0: Attached scsi generic sg2 type 5
[ 2664.736132] scsi 19:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
[ 2664.738417] sd 19:0:0:0: [sdb] Attached SCSI removable disk
[ 2664.738812] sd 19:0:0:0: Attached scsi generic sg3 type 0

 
[EMAIL="massimo@massimo-laptop:~$"]massimo@massimo-laptop:~$[/EMAIL] sudo eject sr5
[EMAIL="massimo@massimo-laptop:~$"]massimo@massimo-laptop:~$[/EMAIL] lsusb
Bus 004 Device 010: ID 12d1:1446 Huawei Technologies Co., Ltd. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

-- the vendor and product are rightly always the same
 
[EMAIL="massimo@massimo-laptop:~$"]massimo@massimo-laptop:~$[/EMAIL] sudo modprobe usbserial vendor=0x12d1 product=0x1446
[EMAIL="massimo@massimo-laptop:~$"]massimo@massimo-laptop:~$[/EMAIL] ls /etc/ttyU*
ls: cannot access /etc/ttyU*: No such file or directory

 
[EMAIL="massimo@massimo-laptop:~$"]massimo@massimo-laptop:~$[/EMAIL] dmesg
[ 2659.543330] usb 4-3: new high speed USB device using ehci_hcd and address 10
[ 2659.677716] usb 4-3: configuration #1 chosen from 1 choice
[ 2659.712242] scsi18 : SCSI emulation for USB Mass Storage devices
[ 2659.719339] usb-storage: device found at 10
[ 2659.719347] usb-storage: waiting for device to settle before scanning
[ 2659.731086] scsi19 : SCSI emulation for USB Mass Storage devices
[ 2659.732122] usb-storage: device found at 10
[ 2659.732128] usb-storage: waiting for device to settle before scanning
[ 2664.713150] usb-storage: device scan complete
[ 2664.714024] scsi 18:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[ 2664.733963] usb-storage: device scan complete
[ 2664.734355] sr5: scsi-1 drive
[ 2664.734448] sr 18:0:0:0: Attached scsi CD-ROM sr5
[ 2664.734510] sr 18:0:0:0: Attached scsi generic sg2 type 5
[ 2664.736132] scsi 19:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
[ 2664.738417] sd 19:0:0:0: [sdb] Attached SCSI removable disk
[ 2664.738812] sd 19:0:0:0: Attached scsi generic sg3 type 0
[ 2676.245070] ISO 9660 Extensions: Microsoft Joliet Level 1
[ 2676.246328] ISOFS: changing to secondary root

---

### Post by GeorgeVita on 2009-09-29
... I know you (we) are trying hard!
... also we are trying to use it to an older version and not at the 'thread's title!
... and we do not know if it changes productID but this ID is not usable.

A note: **sudo dmesg -c** is used just to clear previous dmesg lines. It shows all initial system activity that we do not need. So post here lines starting from the NEXT command (not the output of 'sudo dmesg -c')

Finally: the accumulative **srX** (+1) means that it is not ejected properly (it is not your fault).

Try to boot WITHOUT the modem
Attach it and **wait**
When the CDROM appear to Desktop, right click on icon and click 'eject volume'
Open a terminal window, check lsusb for any new 12d1 : 1001 (or 1003) and if found try again 'sudo modprobe ...'

If not succeeded: <end of our tries!>
Newer Ubuntu proposed, and take this thread from the start.

Good luck again,
George

---

### Post by jumpingfrog on 2009-09-30
I gave up. I tried but without any results(don't know if my fault or not). Anyway I'll try with some different Linux edition / version. I had some problem with the installation of Ubuntu 9 and Kubuntu so that was why i tried with Ubuntu 8 which I had no installation problem.
Anyway thanks again.
See ya.

Angelo

---

### Post by jacobdongon on 2009-10-04
[B]Huawei e1550 broadband:

I had it working when I reformatted my computer. I left the modem plugged in and let ubuntu installed, at first I was reluctant but it suddenly brought up the setup wizard of the modem, and it got me excited and continued and I got conneted. Unfortunately it stopped working when I updated my ubuntu 9.04 with a libv something update, my modem stopped working and my modem returned to being a plug and play memory card reader. Then, I read about this simple step in flipping the modem which I thought doesn't work, I found out that when you have flipped the modem it works right then and there but it has to be in one usb slot after flipping it, weird but that's how it worked for me, till now!

HERE'S THE FLIPPING METHOD I GOT FROM ONE OF THE GUYS IN THIS SAME WEBSITE:
I copied and paste the message and forgot to include the name of that guy! If you read this thank you so much you helped me a lot!!!

[/B]   	 	 	 	 	 	  [SIZE=2]Anyway for 8.10 you need udev-extras:[/SIZE]
 [SIZE=2]sudo apt-get install udev-extras[/SIZE]
 

 [SIZE=2]Add a udev rule:[/SIZE]
 [SIZE=2]gksu gedit /etc/udev/rules.d/15-huawei-e1550.rules[/SIZE]
 

 [SIZE=2]What we’re doing is telling udev that when this device is plugged in to switch its mode.  Paste this and save:[/SIZE]
 [SIZE=2]SUBSYSTEM=="usb",[/SIZE]
 [SIZE=2]SYSFS{idProduct}=="1446",[/SIZE]
 [SIZE=2]SYSFS{idVendor}=="12d1",[/SIZE]
 [SIZE=2]RUN+="/lib/udev/modem-modeswitch --vendor 0x12d1 --product 0x1446 --type option-zerocd"[/SIZE]


[SIZE=2]I didn't understand what all this was about I just followed his instructions it worked, after 3 weeks when I plugged the modem back to its original position.
[/SIZE]

---

### Post by Sylslay on 2009-10-27
that softwere is good for start: 

[http://www.global3g.strony.pl/](http://www.global3g.strony.pl/) 

dowlload  global3g-1.0-beta2-r29-i386.tar.gz 
32/64 bits ?

run

press tab "Ustawienia", choose Yours "Jezyk/Language"

have fun

is't sharwere, but working for fiew minuts, almost on any distro and Huawei modems
and than You can , figure out right setting for nm-aplets or wvdial

PS. In firefox need tick "offline" mode. And You are online

---

### Post by cliffskoog on 2009-12-01
Hello,

I'm in Ireland, and had a problem with three.ireland's huawei E175O usb broadband dongle on ubuntu 9.1.

I found a bash script here:

[http://fr.sourceforge.jp/projects/sfnet_huaweie1750ubun/](http://fr.sourceforge.jp/projects/sfnet_huaweie1750ubun/)

that made it work very nicely!

good luck!
Cliff

---

### Post by cr0bar on 2009-12-18
> **cliffskoog said:**
> Hello,

I'm in Ireland, and had a problem with three.ireland's huawei E175O usb broadband dongle on ubuntu 9.1.

I found a bash script here:

[http://fr.sourceforge.jp/projects/sfnet_huaweie1750ubun/](http://fr.sourceforge.jp/projects/sfnet_huaweie1750ubun/)

that made it work very nicely!

good luck!
Cliff

I've the same USB modem on 3 Ireland and Ubuntu 9.10, ran that script and it works like a charm!

Beforehand I was using an old XP PC, with my wireless router plugged in via the ethernet jack, and the 3G connection and it bridged. This is a little less complex.

---

### Post by AlNaimi on 2009-12-19
Hi there
I'm very beginner with ubuntu...
How could i run this bash script?
...........................
when I do ./Huawei_E1750.sh on termial, i download this file...usb_modeswitch-1.0.2.tar.bz2
Then i do , make install, & i get make install
and this i got
yoyo@yoyo-laptop:~/Desktop/usb_modeswitch-1.0.2$ make install
mkdir -p /usr/sbin
install ./usb_modeswitch /usr/sbin
install: cannot create regular file `/usr/sbin/usb_modeswitch': Permission denied
make: *** [install] Error 1

---

### Post by pdc on 2009-12-19
I suspect someone will advice you need that you need to be logged in as 

SUDO 

to install

so I suspect the command would be

> sudo install whateverand you will be asked for your sudo password

---

### Post by cr0bar on 2009-12-20
If the .sh script is in, say, Downloads, just paste in the console:

```
sudo bash ~/Downloads/Huawei_E1750.sh
```

I just did this for my Sabayon Linux install too, worked like a charm when I plugged it in, and set the connection up in the Mobile Broadband tab in Network Connections.

---

### Post by caughtforpace on 2010-01-12
> **cliffskoog said:**
> Hello,
 
I'm in Ireland, and had a problem with three.ireland's huawei E175O usb broadband dongle on ubuntu 9.1.
 
I found a bash script here:
 
[http://fr.sourceforge.jp/projects/sfnet_huaweie1750ubun/](http://fr.sourceforge.jp/projects/sfnet_huaweie1750ubun/)
 
that made it work very nicely!
 
good luck!
Cliff
 
Hello
 
Im a complete novice at this craic
how do i go about installing the above.
step by step please.

---

### Post by pdc on 2010-01-12
1) go to the site in link that is given
2) click on the file that is called Huawei and ends in .sh
2a) download this to a directory on your system: many download downloads into a directory called Downloads
2b) Open a terminal 
2c) issue the command> cd Downloads
2d) issue the command> ls it asks your system to list what is in the directory called Downloads; if the Huawei is there ...................................
3) copy and paste the command that crobar talks about into a terminal
4) hit the enter key
5) enter your sudo password
6) things should happen
7) as I understand it, then go to Network manager: radio signal icon on the top right of the top panel; 
8) RIGHT-CLICK; select edit connections
9) select MOBILE BROADBAND
10) select ADD
11) choose your country: Eire? and your network
12) accept
13) close
14) LEFT-CLICK now on network manager; what you set up should be there; click on the little circle to connect
15) stand back; gaze in amazement if it connect up
16) load up Firefox
17) tell us if this works

---

### Post by caughtforpace on 2010-01-13
thanks for this.
i wont be able to do it until the weekend.
i will post results asap
 
thanks again

---

### Post by caughtforpace on 2010-01-14
> **pdc said:**
> 1) go to the site in link that is given
2) click on the file that is called Huawei and ends in .sh
2a) download this to a directory on your system: many download downloads into a directory called Downloads
2b) Open a terminal 
2c) issue the command 
cd Downloads 
2d) issue the command 
ls
it asks your system to list what is in the directory called Downloads; if the Huawei is there ...................................
3) copy and paste the command that crobar talks about into a terminal
4) hit the enter key
5) enter your sudo password
6) things should happen
7) as I understand it, then go to Network manager: radio signal icon on the top right of the top panel; 
8) RIGHT-CLICK; select edit connections
9) select MOBILE BROADBAND
10) select ADD
11) choose your country: Eire? and your network
12) accept
13) close
14) LEFT-CLICK now on network manager; what you set up should be there; click on the little circle to connect
15) stand back; gaze in amazement if it connect up
16) load up Firefox
17) tell us if this works
 
Ok
 
steps 1-4 all ok
at step 5. i entered my sudo password (my ubuntu login password i assume, definitely entered correctly)
 
i got Unknown id: /home/darragh/Downloads/Huawei_e1750.sh
 
any ideas.
 
this is probably a stupid question 
(if i ran the Huawei E1750 through a RS232 port via a USB-RS232 adaptor cable. Would ubuntu then recognise it as a modem rather than a storage device)

---

### Post by GeorgeVita on 2010-01-14
Hi **caughtforpace**, the command that **cr0bar** gave you is misspelled. Try: ```
sudo sh ~/Downloads/Huawei_E1750.sh
```

>>> take care about correct filename: Huawei_**E**1750.sh and not Huawei_**e**1750.sh

This script downloads some libraries and the usb_modeswitch program, then it appends valid data for E1750 to usb_modeswitch.conf (configuration file), creates an 'auto-run' rule (15-huawei-e1750.rules) and finally restarts udev to enable all changes.

You must be connected to internet via other method to download above mentioned packages.

> **caughtforpace said:**
> ...if i ran the Huawei E1750 through a RS232 port via a USB-RS232 adaptor cable. Would ubuntu then recognise it as a modem rather than a storage device This cannot be done because USB uses a 'host' to control a 'peripheral'. The modem is a 'peripheral' and the USB to RS232 cable acts as a 'peripheral' at the USB side.

Regards,
George

---

### Post by Alex22 on 2010-07-26
Hallo Guys, that's what I gathered on the Net (and it works ;] ) 

The problem **lies not in GSM settings**, so don't bother with AT commands, card's PIN disabling or APN/user setting. Network Manager works perfectly ok.

The answer is that **some modems are recognized as USB storage sticks**, not modem sticks. The answer is **usb_modeswitch** program from repos.
I had some problems with bespoken script, so i did it with those 3 steps
(it works for all GSM networks and i think for most modems):

1. Install this prog:
sudo apt-get install usb_modeswitch

2. Create its config file:
sudo gedit /etc/usb_modeswitch.conf

File content to be pasted ans saved:

DefaultVendor=  0x**12d1**
DefaultProduct= 0x**1446**

TargetVendor = 0x12d1
TargetProduct= 0x1001
MessageContent="55534243000000000000000000000011060000000000000000000000000000"
MessageEndpoint=0x01
CheckSuccess=5

3. Create file with UDEV rule for acting with usb_modeswitch when plugged stick is dynamically recognized:
sudo gedit /etc/udev/rules.d/15-huawei-e1750.rules

File content to be pasted ans saved:

SUBSYSTEM=="usb",
SYSFS{idProduct}=="**1446**",
SYSFS{idVendor}=="**12d1**",
RUN+="/usr/sbin/usb_modeswitch"

Only things to be customized by you, are product and vendor ids in step 3, and default vendor and product ids in step 2 (as highlighted).
Enter yours, found in **lsusb** command output.

But please, don't touch target vendor and product ids!



Now you can forget, that you had the "problem" modem. Feel free to restart, unplug, plug, have wired ethernet connection simultaneously.

I must end, coz the light of my Huawei E1750 is flashing blue so strong. ;)
Good Luck, greetz from yesterday hot and sunny, today cloudy Krakow.

P.S. Please feed back, if it works for other modem models and GSM networks.

---

### Post by DantePasquale on 2010-09-14
Dang, so close after following your post! But, I get the following in my syslog:

```
Sep 14 23:38:09 dexter kernel: [  163.342757] usb 2-6: new high speed USB device using ehci_hcd and address 2
Sep 14 23:38:09 dexter kernel: [  163.493398] usb 2-6: configuration #1 chosen from 1 choice
Sep 14 23:38:09 dexter kernel: [  163.495214] usbserial_generic 2-6:1.0: generic converter detected
Sep 14 23:38:09 dexter kernel: [  163.495355] usb 2-6: generic converter now attached to ttyUSB0
Sep 14 23:38:09 dexter kernel: [  163.495471] usbserial_generic 2-6:1.1: generic converter detected
Sep 14 23:38:09 dexter kernel: [  163.495574] usb 2-6: generic converter now attached to ttyUSB1
Sep 14 23:38:09 dexter kernel: [  163.840931] generic ttyUSB0: generic converter now disconnected from ttyUSB0
Sep 14 23:38:09 dexter kernel: [  163.840961] usbserial_generic 2-6:1.0: device disconnected
Sep 14 23:38:10 dexter kernel: [  164.919903] Initializing USB Mass Storage driver...
Sep 14 23:38:10 dexter kernel: [  164.941040] scsi4 : SCSI emulation for USB Mass Storage devices
Sep 14 23:38:10 dexter kernel: [  164.941240] usb-storage: device found at 2
Sep 14 23:38:10 dexter kernel: [  164.941243] usb-storage: waiting for device to settle before scanning
Sep 14 23:38:10 dexter kernel: [  164.941293] usbcore: registered new interface driver usb-storage
Sep 14 23:38:10 dexter kernel: [  164.941296] USB Mass Storage support registered.
Sep 14 23:38:10 dexter modem-manager: (Huawei): (ttyUSB1) deferring support check
Sep 14 23:38:10 dexter usb_id[3253]: unable to access '/devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0/ttyUSB0/tty/ttyUSB0'
Sep 14 23:38:10 dexter usb_id[3254]: unable to access '/devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0/ttyUSB0/tty/ttyUSB0'
Sep 14 23:38:13 dexter modem-manager: (ttyUSB1): re-checking support...
Sep 14 23:38:13 dexter modem-manager: (Huawei): (ttyUSB1) deferring support check
Sep 14 23:38:15 dexter kernel: [  169.943575] usb-storage: device scan complete
Sep 14 23:38:16 dexter modem-manager: (ttyUSB1): re-checking support...
Sep 14 23:38:16 dexter modem-manager: (Huawei): (ttyUSB1) deferring support check
Sep 14 23:38:19 dexter modem-manager: (ttyUSB1): re-checking support...
```


The last line just repeats forever. When I bring up network-manager to add the mobile broadband connection, it doesn't show a broadband device to add the info for ;(

Any ideas?

---

### Post by lallalla on 2010-12-16
> **cliffskoog said:**
> Hello,

I'm in Ireland, and had a problem with three.ireland's huawei E175O usb broadband dongle on ubuntu 9.1.

I found a bash script here:

[http://fr.sourceforge.jp/projects/sfnet_huaweie1750ubun/](http://fr.sourceforge.jp/projects/sfnet_huaweie1750ubun/)

that made it work very nicely!

good luck!
Cliff


PLUS 1. downloaded the bash and model connected immediately. Thanks!!

---

