---
title: "Zonet ZEW2508 drivers won't install"
date: 2010-06-15
forum: Networking &amp; Wireless
---

### Post by con5021 on 2010-06-15
First, I'm extremely new to Linux and Ubuntu, so my understanding of it is very, very limited. I've got version 10.4, also.

I have a Zonet ZEW2508 USB wireless adapter and the drivers that come with it won't install. Are there any drivers that work with Ubuntu?

Ubuntu does appear to see that it's plugged in, however.

Thanks

---

### Post by chili555 on 2010-06-15
With the device plugged in, please open Applications > Accessories > Terminal and run:```
lsusb
```We are looking for the usb.id. Is it 148f:2070? If it is, the device is supposed to work with the module rt2800usb which is already on your system. Please now do:```
sudo modprobe rt2800usb
iwconfig
```Is there a wireless interface, wlan0? If so, click the Network Manager icon at the top right and see your network and connect.

If my guesswork is all wrong, post:```
lsusb
```

---

### Post by con5021 on 2010-06-16
This is the result of lsusb:
```
 	 	 Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 004 Device 003: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0  
 Bus 004 Device 002: ID 047b:0011 Silitek Corp.  
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 002 Device 003: ID 0930:6544 Toshiba Corp. Kingston DataTraveler 2.0 Stick (2GB)  
 Bus 002 Device 002: ID 148f:2070 Ralink Technology, Corp.  
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 
```

With iwconfig:
```
 	 	 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 wlan0     IEEE 802.11bgn  ESSID:off/any   
           Mode:Managed  Access Point: Not-Associated   Tx-Power=9 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off  
           Power Management:on  
            
 
```

The network doesn't show up in the network manager, though.

---

### Post by chili555 on 2010-06-16
Let's have a look at:```
lsmod | grep rt2
dmesg | grep -i rt2
```Thanks.

---

### Post by con5021 on 2010-06-16
lsmod | grep rt2:
```
 	 	 rt2800usb              33496  0  
 rt2x00usb              11260  1 rt2800usb  
 rt2x00lib              32133  2 rt2800usb,rt2x00usb  
 led_class               3732  1 rt2x00lib  
 mac80211              238128  2 rt2x00usb,rt2x00lib  
 cfg80211              148386  2 rt2x00lib,mac80211  
 crc_ccitt               1675  1 rt2800usb  
 
```

dmesg | grep -i rt2:
```
 	 	 [    7.790523] Registered led device: rt2800usb-phy0::radio  
 [    7.790536] Registered led device: rt2800usb-phy0::assoc  
 [    7.790551] Registered led device: rt2800usb-phy0::quality  
 [    7.792161] usbcore: registered new interface driver rt2800usb  
 [    8.481351] rt2800usb 2-3:1.0: firmware: requesting rt2870.bi
 
```

---

### Post by chili555 on 2010-06-16
> [    8.481351] rt2800usb 2-3:1.0: firmware: requesting rt2870.biIs that all there is? We need to know if the firmware was correctly loaded or not found. You might also check:```
dmesg | grep -i firm
```Your *lsmod* looks perfect.

---

### Post by con5021 on 2010-06-16
> **chili555 said:**
> Is that all there is? We need to know if the firmware was correctly loaded or not found. 
Yep. I tried again and it was the same.

This is from dmesg | grep -i firm:
```
           [    1.155778] [Firmware Bug]: powernow-k8: No compatible ACPI _PSS objects found.  
 [    1.155779] [Firmware Bug]: powernow-k8: Try again with latest BIOS.  
 [    8.737641] rt2800usb 2-3:1.0: firmware: requesting rt2870.bin  
 
```

It appears that you can download rt2870.bin from here [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) under [Firmware  RT28XX/RT30XX USB series (RT2870/RT2770/RT3572/RT3070).]("http://www.ralinktech.com/license_us.php?n=2&p=1&t=U0wyRnpjMlYwY3k4eU1ERXdMekF6THpNeEwyUnZkMjVzYjJGa01UWXpPRGs1T0Rnek5pNTZhWEE5UFQxU1ZESTROekJmUm1seWJYZGhjbVZmVmpJeUM%3D")
I don't know if that would help or what to do with it if it does, however.

---

### Post by chili555 on 2010-06-16
It doesn't seem to be complaining about failing to load the firmware. Maybe it's already on your system. Please do:```
ls /lib/firmware | grep 2870
```What is the result of:```
sudo iwlist wlan0 scan
```Thanks.

---

### Post by con5021 on 2010-06-16
For the first one I got:
```
 	 	 rt2870.bin
 
```

The next one:
```
 	 	 wlan0     No scan results
 
```

---

### Post by X=RT on 2010-06-24
I have the same problem...

---

### Post by con5021 on 2010-06-24
Does anybody have a solution to this? 

I'd like to start using Ubuntu more, but without internet, it's not useful to me.

---

### Post by Jim-BobH on 2010-08-07
I don't have anything like a solution, but I have _exactly_ the same problem.

I'll "watch" this thread in hopes for help.

Thanks for any help.

Jim

---

