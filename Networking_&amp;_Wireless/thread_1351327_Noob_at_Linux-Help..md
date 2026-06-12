---
title: "Noob at Linux-Help."
date: 2009-12-10
forum: Networking &amp; Wireless
---

### Post by charlesC8188 on 2009-12-10
This is my first time using a linux os. I d/l Ubuntu 9.10, burned it to a disc, made a partition on windows 7 of 20gb's, installed Ubuntu successfully. Now when the main GUI appears it's very basic nothing flashy at all. Then I point to the internet connections and nothing. I even tried to input all the specifications manually such as the wpa key, ipv4 settings, ssid, and all the other settings and still can't connect to the net, or even to my router. I have taken a few screen shots of the issues. I need to connect to the internet. I use Windows 7 (64bit), Windows Vista (32bit), and just installed Ubuntu 9.10 (64bit), all on separate partitions. I have a wireless connection only, no access to a wired connection. I have a linksys wireless N wrt160n router with a usb wireless N linksys adapter. Also another issue I am having is with the graphic's. I have an Radeon HD 4350 (1gb) graphic card with a Pentium dual core processor (2.5ghz) with 3gb of ram. When I go to the appearance settings in Ubuntu and try to turn on the advanced display settings all I get is an error message, when I'm sure my card can handle it. Anyone that can help it will be greatly appreciated. Below are the pictures of the error I have received. Feel free to contact me via messenger as well.

[IMG]http://i331.photobucket.com/albums/l450/charlesC8188/ubuntoerror4.png[/IMG]
[IMG]http://i331.photobucket.com/albums/l450/charlesC8188/Screenshot.png[/IMG]
[IMG]http://i331.photobucket.com/albums/l450/charlesC8188/ubuntuerror2.png[/IMG]
[IMG]http://i331.photobucket.com/albums/l450/charlesC8188/ubuntu-error3.png[/IMG]
[IMG]http://i331.photobucket.com/albums/l450/charlesC8188/ubuntu-ipconfigerror.png[/IMG]

Thanks in advance,


charlesC8188:D

---

### Post by teward on 2009-12-10
The command ipconfig is only in Windows.

The similar command in linux is ifconfig.  But it seems you're having other problems as well.

---

### Post by teward on 2009-12-10
(sorry for double post)

Some graphics cards physically can't handle advanced desktop effects.  Even if you **think** your card can handle it, they sometimes cant because of the way the drivers function.

---

### Post by chili555 on 2009-12-10
Those Windows drivers will not, without some work, get your wireless going. Please set the driver CD aside for now.

The reason you are getting 'not found' errors is because you are not connected to the internet so the apt-get system can not get the files!

It is:```
iwlist scan
```and not:```
i wlist scan
```Your computer will tell us what kind of wireless adapter it has if you plug in the device, open a terminal and do:```
lsusb
```We don't need a screenshot, just write down the part that looks like a Linksys wireless device and post it all here.

---

### Post by charlesC8188 on 2009-12-10
Ok i booted up Ubuntu and did what you told me to do, my findings are below. And thanks again for your help.

[IMG]http://i331.photobucket.com/albums/l450/charlesC8188/error-1.jpg[/IMG]

---

### Post by chili555 on 2009-12-10
You said you have:> usb wireless N linksys adapterDid you plug it in to your computer? I see nothing resembling a wireless adapter here. ???

---

### Post by charlesC8188 on 2009-12-10
yes i have a WUSB600N Linksys wireless-n USB network adapter with Dual-band. It's plugged into one of the rear usb 2.0 ports.

---

### Post by chili555 on 2009-12-10
It's very mysterious that we see your keyboard, mouse, printer, card reader and flash drive, but not your wireless. Please open a terminal and do:```
sudo modprobe rt2870sta
lsmod | grep rt
```Please post the result.

---

### Post by charlesC8188 on 2009-12-10
Followed your instructions, results follow:

[IMG]http://i331.photobucket.com/albums/l450/charlesC8188/sudoerror.png[/IMG]


Also, any idea why I can't use the advanced or even basic visual settings? It's stuck on "none".

Thanks.

---

### Post by chili555 on 2009-12-10
As to your visual settings, I have no idea. I suggest a separate posting in 'General Help.'

My request was for two separate command entries. In other words, *sudo modprobe rt2870sta*, followed by Enter; and then *lsmod | grep rt*, followed by Enter. Not all in one command. However we have already found a problem. Your terminal output says see *dmesg* for information. Please do:```
dmesg | grep rt2870sta > dmesg,txt
```You will find a text file in your Home directory called *dmesg.txt*. Drag and drop it on to that flash drive and copy and paste it into your reply. It's getting late here in the woods, so I will check with you tomorrow.

---

