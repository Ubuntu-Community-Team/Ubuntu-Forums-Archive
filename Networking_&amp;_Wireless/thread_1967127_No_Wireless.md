---
title: "No Wireless"
date: 2012-04-27
forum: Networking &amp; Wireless
---

### Post by harfin on 2012-04-27
Hi
Long haul but upgraded to 12.04 today and now no wireless.
Belkin unit works fine on windows side.
Tried rebooting several times.
Network icon has check for enable networking but no mention of anything relating to enable wireless
On edit connections window my homehub connection is listed and when I doubleclick that all seems ok and the wireless security tab has right security level and right password.
System just doesn't connect to internet.
Help!!!

Alan

---

### Post by gordintoronto on 2012-04-27
Are you connected to your router? Can you browse to 192.168.1.1 (or whatever address your router takes)?

In Edit Connections, is "all users" clicked?

---

### Post by whistlerspa on 2012-04-28
I'm not sure if this is relevant for you but I've found that internet doesn't work if an ethernet cable is also connected to the router.

---

### Post by whistlerspa on 2012-04-28
I'm not sure if this is relevant for you but I've found that internet doesn't work if an ethernet cable is also connected to the router.

---

### Post by harfin on 2012-04-28
*> **gordintoronto said:**
> Are you connected to your router? Can you browse to 192.168.1.1 (or whatever address your router takes)?

In Edit Connections, is "all users" clicked?
 
Dont understand "browse in this context ", sorry.
"All users" is clicked. 

As regards ethernet cables, none are connected to the pc.

Any other suggestions?

Alan

---

### Post by mörgæs on 2012-04-28
Moved to the networking forum.

---

### Post by harfin on 2012-04-28
l> **harfin said:**
> *
 
Dont understand "browse in this context", sorry.
"All users" is clicked.

As regards ethernet cables, none are connected to the pc.

Any other suggestions?

Alan

Perhaps I should add that thePC is a Dell Inspiron and that it has a Belkin USB Wireless device that connects to a BT HomeHub plugged into my phone socket.

The HomeHub works fine with my Netbook (which I am using for this message).

The Belkin works fine for the Dell when on the Windows side.

All were working fine until 12.04
Alan

---

### Post by harfin on 2012-04-28
Any takers?
Alan

---

### Post by harfin on 2012-04-28
I have started Network Tools and it states that Loopback Interface (lo) with configure greyed out. There are two lines of IP information lone for IPv6 and the other for IPv4.

IPv6 shows IP Address ::1, Netmask/Prefix 128, Scope Host
IPv4 shows  IP Address 127.0.0.1 Netmask/Prefix 255.0.0.0

I don't understand the rest!

Alan

---

### Post by harfin on 2012-04-28
Under currently installed network drivers, it shows rt2870, Hardware Present Yes  (thats the driver for my USB Belkin device

The device has a steady blue light gowing, not flickering on/off etc like it does when it is talking to my Home Hub

Alan

---

### Post by harfin on 2012-04-28
I have opened Configuration Editor - Connection and under the area 'Key Documentation' for the HomeHub it shows 
   (warning sign icon) then 'This key has no schema'    
Is this relevant to my problem?

Everything but connecting via the usb Belkin device to my HomeHub works fine

Alan

---

### Post by chili555 on 2012-04-28
All these posts and nobody asked the important questions. Please open a terminal and show us:```
lsusb
rfkill list all
lsmod | grep rt2
dmesg | grep -i rt2
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by harfin on 2012-04-28
> **chili555 said:**
> All these posts and nobody asked the important  questions. Please open a terminal and show us:```
lsusb
rfkill list all
lsmod | grep rt2
dmesg | grep -i rt2
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.
Bus 001 Device 001: ID 1d6b:002 Linux Foundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:002 Linux Foundation 2.0 root hub 
Bus 003 Device 001: ID 1d6b:001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:001 Linux Foundation 1.1 root hub 
Bus 006 Device 001: ID 1d6b00 1 Linux Foundation 1.1 root hub 
Bus 001 Device 002: ID 0
46d:09a4 Logitech, Inc. QuickCam E 3500
 Bus 002 Device 003: ID 0bc2:2300 Seagate RSS LLC
Bus 002 Device 004: ID 050d:815c Belkin Components F5D8053 N Wireless USB Adapter v3000 [Ralink RT2870]
Bus 004 Device 002: ID 413c:2105 Dell Computer Corp Model L100 Keyboard
Bus 004 Device 003: ID 045e:00cb Microsoft Corp Basic Optical Mouse v2.0
Bus 006 Device 002: ID: 04d8:003f Microchip Technology Inc

Post the others in a moment
Alan

---

### Post by harfin on 2012-04-28
> **harfin said:**
> Bus 001 Device 001: ID 1d6b:002 Linux Foundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:002 Linux Foundation 2.0 root hub 
Bus 003 Device 001: ID 1d6b:001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:001 Linux Foundation 1.1 root hub 
Bus 006 Device 001: ID 1d6b00 1 Linux Foundation 1.1 root hub 
Bus 001 Device 002: ID 0
46d:09a4 Logitech, Inc. QuickCam E 3500
 Bus 002 Device 003: ID 0bc2:2300 Seagate RSS LLC
Bus 002 Device 004: ID 050d:815c Belkin Components F5D8053 N Wireless USB Adapter v3000 [Ralink RT2870]
Bus 004 Device 002: ID 413c:2105 Dell Computer Corp Model L100 Keyboard
Bus 004 Device 003: ID 045e:00cb Microsoft Corp Basic Optical Mouse v2.0
Bus 006 Device 002: ID: 04d8:003f Microchip Technology Inc

Post the others in a moment
Alan

rfkill list all produced nothing just returned my a new line prefaced by "alanhart@ubuntu"

lsmod etc same result

dmseg etc same result

Alan

---

### Post by chili555 on 2012-04-28
Please try loading the correct module first and then look for messages:```
sudo modprobe rt2800usb
dmesg | grep -i rt2
```Thanks.

---

### Post by harfin on 2012-04-28
> **chili555 said:**
> Please try loading the correct module first and then look for messages:```
sudo modprobe rt2800usb
dmesg | grep -i rt2
```Thanks.
Wow.
Just getting the response from your first bit, and lo and behold my system connected to the internet!

The response, 
WARNING All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release
[24000.162501] Registered led device: rt2800usb-ph0::radio
[24000.162545] Registered led device: rt2800usb-ph0::assoc
[24000.162586] Registered led device: rt2800usb-ph0::quality
[LEFT][24000.162637 usbcore: registered new interface driver rt2800usb

How strange is that?

Alan


[/LEFT]

---

### Post by chili555 on 2012-04-28
> Just getting the response from your first bit, and lo and behold my system connected to the internet!Lo and behold, indeed! Your readings suggest the correct module wasn't loading on boot; let's fix that. Please do:```
sudo su
echo rt2800usb >> /etc/modules
exit
```Next, please use thread tools at the top to Mark Solved.

Have fun!

---

### Post by harfin on 2012-04-28
> **chili555 said:**
> Lo and behold, indeed! Your readings suggest the correct module wasn't loading on boot; let's fix that. Please do:```
sudo su
echo rt2800usb >> /etc/modules
exit
```Next, please use thread tools at the top to Mark Solved.

Have fun!
That's great!

Sincere thanks for all your help.

Regards
Alan

---

