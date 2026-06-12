---
title: "Can't connect to wireless network with Linksys WUSB100"
date: 2010-04-01
forum: Networking &amp; Wireless
---

### Post by offbyone on 2010-04-01
Hello. I need a little help with a Linksys WUSB100 wireless adapter. I've tried it using the Ubuntu 9.10 live CD (both 32-bit and 64-bit versions) and while the adapter can see wireless networks, it can't connect to them. It asks me for my WPA2 key, but after trying to connect for about 30 seconds it asks me for it again. I've read other threads about this issue but they were kind of confusing.

I just need to know whether the adapter will work and if so, how to get it to connect. I'm so sick of Windows and I'd love to switch to Linux, but I won't be able to if I can't get my adapter to work.

Can anyone help? Thank you.

Edit: I just noticed the sticky about posting wireless tickets. I'm sorry, I don't have time to post it right now, but I will post all of that information when I get back. :)

---

### Post by chili555 on 2010-04-01
As in many things in life, it depends. Please run:```
lsusb
```If the usb.id is 1737:0078, then this is the process you should follow. [http://ubuntuforums.org/showpost.php?p=8591348&postcount=6](http://ubuntuforums.org/showpost.php?p=8591348&postcount=6)

If you need help executing this, post back and we'll help. If your usb.id is something different, let us know.

---

### Post by offbyone on 2010-04-01
I ran the command and it returned "1737:0070" as the ID. From what I've been able to gather from reading other stuff about this, doesn't this mean that I have the first version of the adapter (with 1737:0078 being the second)?

---

### Post by chili555 on 2010-04-01
Yessir! It also means that two drivers are probably loaded and conflicting. Let's do the following terminal commands:```
sudo su
echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot with your WUSB100 inserted and the ethernet cable detached. Post back with your report, please.

---

### Post by offbyone on 2010-04-01
> **chili555 said:**
> Yessir! It also means that two drivers are probably loaded and conflicting. Let's do the following terminal commands:```
sudo su
echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot with your WUSB100 inserted and the ethernet cable detached. Post back with your report, please.

I've been using the live CD to do this the whole time, so I can't restart. Is there a way to do this without restarting?

---

### Post by chili555 on 2010-04-01
We can sure try. Remove the device and do:```
sudo rmmod rt2870sta
sudo rmmod rt2800usb
```Then do the commands I listed above and reinsert the device. Run:```
iwconfig
```If you have a wireless interface, wlan0, perhaps, you are all set.

---

### Post by offbyone on 2010-04-01
Edit: Misunderstood something, but I understand now. Booting into Ubuntu.

---

### Post by offbyone on 2010-04-01
Alright, I tried the commands. I entered everything correctly, but I still can't get the adapter to connect. :(

---

### Post by chili555 on 2010-04-02
Please remove the device. Next do:```
sudo su
rmmod rt2870sta
rmmod rt2800usb
echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf
exit
```Re-insert the device.```
iwconfig
```Do you have a wireless interface? Detach the ethernet cable and click the Network Manager icon. Do you see networks? Can you click yours and connect?

If not, attach the ethernet cable, get a connection and post:```
dmesg | grep rt2
```Thanks.

---

### Post by offbyone on 2010-04-02
The wireless didn't work; I'm on Ubuntu right now on a wired connection. I ran dmesg and this is what I got.

```
ubuntu@ubuntu:~$ dmesg | grep rt2
[   53.549479] Registered led device: rt2800usb-phy0::radio
[   53.549494] Registered led device: rt2800usb-phy0::assoc
[   53.549507] Registered led device: rt2800usb-phy0::quality
[   53.552412] usbcore: registered new interface driver rt2800usb
[   53.679219] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   53.681570] usbcore: registered new interface driver rt2870
[   54.122824] rt2800usb 1-3:1.0: firmware: requesting rt2870.bin
[  115.779747] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x1004 with error -19.
[  115.779752] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1004 with error -19.
[  115.779756] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0208 with error -19.
[  115.779759] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0208 with error -19.
[  115.779763] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1004 with error -19.
[  115.779766] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1204 with error -19.
[  115.779769] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1328 with error -19.
[  115.779773] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0208 with error -19.
[  115.779776] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0c failed for offset 0x0000 with error -19.
[  115.779783] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[  115.779885] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[  115.779987] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[  115.780089] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[  115.780192] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[  115.780294] phy0 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xf7147d84
[  115.780298] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[  115.780401] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[  115.780503] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[  115.780606] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[  115.780709] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[  115.780811] phy0 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xf7147d8c
[  115.780864] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[  115.780967] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[  115.781070] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[  115.781173] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[  115.781275] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[  115.781378] phy0 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xf7147d94
[  115.781399] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[  115.781502] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[  115.781605] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[  115.781708] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[  115.781810] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[  115.781913] phy0 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xf7147d94
[  115.781936] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[  115.782039] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[  115.782141] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[  115.782244] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[  115.782347] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[  115.782449] phy0 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xf7147d94
[  153.498490] usbcore: deregistering interface driver rt2870
[  158.500917] usbcore: deregistering interface driver rt2800usb
[  179.629920] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[  179.634583] usbcore: registered new interface driver rt2870

```

---

### Post by offbyone on 2010-04-02
Bump.

---

### Post by chili555 on 2010-04-03
Let's try a little harder. Please remove the device. Please open a terminal and do:```
sudo su
rmmod rt2870sta
rmmod rt2800usb
echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf
echo "blacklist rt2x00usb" >> /etc/modprobe.d/blacklist.conf
echo "blacklist rt2x00lib" >> /etc/modprobe.d/blacklist.conf
exit
```Insert the device and report your result. If you cannot connect, again post:```
dmesg | grep rt2

```Thanks.

---

### Post by offbyone on 2010-04-03
Edit: Well this is embarrassing. I tried those last commands and they didn't work. However, when I logged into my router I found out that I was entering the wrong WPA2 passkey lol. Thanks for all of the help; I really appreciate it.

Just out of curiosity, I'm going to see if the first set of commands would have worked.

Edit 2: It turns out that the first set of commands fixed my problem. Actually, the device connected to the router without doing anything, but for some reason web pages would never load. But the first set of commands definitely fixed that.

Thanks again.

---

