---
title: "Wireless not working: Sitecom WL-344."
date: 2010-06-20
forum: Networking &amp; Wireless
---

### Post by mtf09 on 2010-06-20
Hey there,

I'm running ubuntu 10.04 with the sitecom wl-344 USB wireless networking dongle. I read that the device should work with the rt2800usb driver however I get this error in the terminal:

```

michael@michael-desktop:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 046d:c71c Logitech, Inc. 
Bus 004 Device 003: ID 046d:c71b Logitech, Inc. 
Bus 004 Device 002: ID 046d:0b06 Logitech, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0df6:0040 Sitecom Europe B.V. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
michael@michael-desktop:~$ dmesg | grep rt2
[    9.111195] phy0 -> rt2800usb_init_eeprom: Error - Invalid RT chipset detected.
[    9.111235] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[    9.111290] usbcore: registered new interface driver rt2800usb
michael@michael-desktop:~$ 
```

I have no idea what to do now so any help would be appreciated!

Thanks,
Mike.

---

### Post by Cowabuntu on 2010-07-03
I'm having exactly the same problem. Any luck in resolving it? I am digging through a lot of posts and possible solutions, but nothing helped so far...

---

### Post by flash63 on 2010-07-03
Hello,
block rt2800usb ... 
```
echo 'blacklist rt2800usb' | sudo tee -a /etc/modprobe.d/blacklist.conf
```
restart, and try this
```
echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "0df6 0040" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
sudo modprobe rt2870sta
dmesg | egrep 'rt28|usb|Phy'
iwconfig
sudo iwlist scan
```(the first Line allocate the Chipset-ID to the driver rt2870sta)

If the solution works, activiate it automatically by a new udev-Rule
```
sudo gedit /etc/udev/rules.d/10-wlan.rules
```
Insert the following code and save the file
```
# UDEV-Rule for Sitecom WL-344 ID 0df6:0040
SUBSYSTEM=="usb", SYSFS{idVendor}=="0df6", SYSFS{idProduct}=="0040", RUN+="/sbin/modprobe rt2870sta"
```
Activate it (or restart)
```
sudo service udev reload
```

---

### Post by Cowabuntu on 2010-07-03
Great, it is working perfectly now. Thanks a million!

---

### Post by Edzilla on 2010-07-19
That worked for me too, thank you very much

---

### Post by nkaryeli@gmail.com on 2011-03-30
Can you help me please? I have tried all above, but it still not working. The system prompts me with a password for network key. I'm sure the password is ok.

I have attached a zip file for more info.

Thanks in advance

Necati

---

### Post by schisco on 2011-04-08
hi everybody 
i have installed xubuntu 10.10 on my pc and i need to install the wireless usb adapter sitecom wl-349 v3 001
can you help me?
thanks

---

### Post by Catherine Waymouth on 2012-11-01
Hi, 
 
I'm also havingproblems with my WL344 wifi adaptor. I put in the code as copied from post #3 but it returns the following:
 
freyja@freyja-GeForce:~$ echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "0df6 0040" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
[sudo] password for freyja: 
install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "0df6 0040" > /sys/bus/usb/drivers/rt2870/new_id
[EMAIL="freyja@freyja-GeForce:~$"]freyja@freyja-GeForce:~$[/EMAIL] sudo modprobe rt2870sta
[EMAIL="freyja@freyja-GeForce:~$"]freyja@freyja-GeForce:~$[/EMAIL] dmesg | egrep 'rt28|usb|Phy'
[ 0.004304] CPU: Physical Processor ID: 0
[ 0.191069] usbcore: registered new interface driver usbfs
[ 0.191077] usbcore: registered new interface driver hub
[ 0.191099] usbcore: registered new device driver usb
[ 1.128052] usb 1-5: new high speed USB device using ehci_hcd and address 2
[ 10.457598] Registered led device: rt2800usb-phy0::radio
[ 10.457614] Registered led device: rt2800usb-phy0::assoc
[ 10.457629] Registered led device: rt2800usb-phy0::quality
[ 10.457981] usbcore: registered new interface driver rt2800usb
[ 143.174676] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[ 143.182343] rtusb init --->
[ 143.182377] usbcore: registered new interface driver rt2870
[EMAIL="freyja@freyja-GeForce:~$"]freyja@freyja-GeForce:~$[/EMAIL] iwconfig
lo no wireless extensions.
eth0 no wireless extensions.
wlan0 IEEE 802.11bgn ESSID:off/any 
Mode:Managed Access Point: Not-Associated Tx-Power=0 dBm 
Retry long limit:7 RTS thr:off Fragment thr:off
Power Management:on
[EMAIL="freyja@freyja-GeForce:~$"]freyja@freyja-GeForce:~$[/EMAIL] sudo iwlist scan
lo Interface doesn't support scanning.
eth0 Interface doesn't support scanning.
wlan0 Interface doesn't support scanning : Network is down
 
Does this mean anything to anyone? All it means to me is that my wifi doesn't work but it works fine on a borrowed Windows mini laptop!!
 
Any help thankfully received, although I realise this thread is pretty old now :-)
 
Cath.

---

### Post by Catherine Waymouth on 2012-11-07
Sorted! I didn't realise that the previous fix code had to be put in a line at a time :-)

---

