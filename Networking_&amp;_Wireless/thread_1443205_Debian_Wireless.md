---
title: "Debian Wireless"
date: 2010-03-30
forum: Networking &amp; Wireless
---

### Post by Lunami on 2010-03-30
Alright, I'm attempting to get wireless, by installing various packages from the install disk, and from my Windows machine via flash drive.

I can't seem to get it to work yet.

lsusb
Bus 001 Device 003: ID 0846:6a00 NetGear, Inc. WG111(v2) 54 Mbps Wireless [RealTek RTL8186L]

iwconfig
lo      No wireless extensions.

eth0    no wireless extensions.



I'm attempting to use wicd, but it isn't giving me the ability to even choose wireless. Granted, I can't get the driver for my USB to work either.

Before anyone asks, know, that I am unable to use ethernet. There really isn't even a point in asking about trying, it won't work.

I'll give more help when I'm asked, but realize, that since I'm using a flash drive to go back and forth between these two computers, replies may be some distance apart time-wise.

---

### Post by chili555 on 2010-03-30
I think this is supposed to work with the module rtl8187. Open a terminal and do:```
sudo modprobe rtl8187
iwconfig
```Do you now have a wireless interface?

---

### Post by Lunami on 2010-03-30
> **chili555 said:**
> I think this is supposed to work with the module rtl8187. Open a terminal and do:```
sudo modprobe rtl8187
iwconfig
```Do you now have a wireless interface?

When I use modprobe, it doesn't bring up a display, if it's supposed to. As for iwconfig, it's the same as what I posted a short time ago.

---

### Post by chili555 on 2010-03-30
> When I use modprobe, it doesn't bring up a display, if it's supposed to.It's not, if the module got inserted without error. Please post:```
dmesg | grep rtl8
```Let's see what the kernel has to say.

---

### Post by Lunami on 2010-03-30
To the Grep, I get

[ 5534.34689] usbcore: registered new interface driver rtl8187

---

### Post by chili555 on 2010-03-30
Please reboot with the device inserted. Then run:```
dmesg > dmesg.txt
zip dmesg.zip dmesg.txt
```Please transfer on a USB key and attach dmesg.zip to your reply.

---

### Post by Lunami on 2010-03-30
Alright, I believe this did it. Also, thanks for typing up those commands for me, I'll have to keep those in mind. Always nice to learn more commands.

---

### Post by chili555 on 2010-03-30
This is quite interesting:> [    9.369502] usb 1-1.1: new full speed USB device using uhci_hcd and address 3
[    9.513687] usb 1-1.1: [COLOR="Red"]rejected 1 configuration due to insufficient available bus power[/COLOR]
[    9.513712] usb 1-1.1: no configuration chosen from 1 choice
[    9.514021] usb 1-1.1: New USB device found, idVendor=0846, idProduct=6a00
[    9.514040] usb 1-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    9.514055] usb 1-1.1: Product: NETGEAR WG111v2
[    9.514066] usb 1-1.1: Manufacturer: NETGEAR WG111v2
[    9.514078] usb 1-1.1: SerialNumber: 001B2FAAF321I am Googling and suggest you do so, too.

---

### Post by Lunami on 2010-03-30
I may be able to help with that. See, this laptop only has but one USB port, so I have a hub I place in it. Four ports (So I can use my USB wireless and my flash drive.), so it may not have enough power because of that.

I'll restart the computer, and redo the dmesg, and I'll upload that again to this post here.

---

### Post by Lunami on 2010-03-30
Okay... it won't let me add the file again... sorry for the double post because of it.

---

### Post by chili555 on 2010-03-30
> usb 1-1: new full speed USB device using uhci_hcd and address 2
[    9.045270] [COLOR="Red"]usb 1-1: configuration #1 chosen from 1 choice[/COLOR]
[    9.052665] usb 1-1: New USB device found, idVendor=0846, idProduct=6a00
[    9.052688] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    9.052703] usb 1-1: Product: NETGEAR WG111v2
[    9.052715] usb 1-1: Manufacturer: NETGEAR WG111v2
[    9.052726] usb 1-1: SerialNumber: 001B2FAAF321Great! We got rid of the error. Now repeat:```
sudo modprobe rtl8187
iwconfig
```

---

### Post by Lunami on 2010-03-30
Same as earlier.

Modprobe has no output, and iwconfig has the same output.

---

### Post by chili555 on 2010-03-30
> [   34.060661] phy0: hwaddr 00:1b:2f:aa:f3:21, rtl8187 V1 + rtl8225z2
[   34.060762] usbcore: registered new interface driver rtl8187It actually already grabbed rtl8187. Did it create an interface?

---

### Post by Lunami on 2010-03-30
NOthing. Still eth0 and lo.

---

### Post by chili555 on 2010-03-30
```
[   75.361719] ADDRCONF(NETDEV_UP): [COLOR="Red"]wlan0[/COLOR]: link is not ready
```It looks like it *did* create an interface. Is it no longer there in iwconfig?

Do you use Network Mangler in Debian?

---

### Post by Lunami on 2010-03-30
> **chili555 said:**
> ```
[   75.361719] ADDRCONF(NETDEV_UP): [COLOR="Red"]wlan0[/COLOR]: link is not ready
```It looks like it *did* create an interface. Is it no longer there in iwconfig?

Do you use Network Mangler in Debian?

Alright, I got it now. I had to restart it again. But yes, it is there now.

---

### Post by Lunami on 2010-03-31
Alright, just booted up the computer. (My I hate GNOME.... this computer is far too old for it..)

I can find wireless now through my Wicd Network Manager (When it actually manages to load the thing correctly). However, all of them are showing a connection strength percentage of 84%, it's hidden, and it's the one I want. The rest are like 32, etc... Clearly not in this house. However, I can't seem to connect to it. It's not wep/wpa/etc... encrypted, just the name is hidden. But I still can't seem to connect to it. Any help would be appreciated.

---

### Post by chili555 on 2010-03-31
Here is a guide that might work for you:> 1. Open Wicd Network Manager
2. Click on Network - Hidden Network
3. Type the name of your hidden network's SSID
4. Hopefully after a few tries, you get it to connect - temporarily broadcast your SSID to help it out, if need be.
5. Once you have a connection, you can do this in the Wicd GUI or in the text file:
    A. In the Wicd GUI, Expand your SSID's properties and choose the "Scripts" button
        In the Pre-connection Script field, type:  iwconfig wlan0 essid YOUR_HIDDEN_SSID
    B. In a shell, type:  sudo  gedit  /etc/wicd/wireless-settings.conf
        Find the line reading "beforescript = None" and replace the word None with: iwconfig wlan0 essid YOUR_HIDDEN_SSID

---

### Post by Lunami on 2010-03-31
I follow with all of that, but I don't have access to the router to turn on the SSID broadcast. I'll try and see if I won't need to have it broadcasted.

---

