---
title: "Sierra 598 USB for Sprint Broadband-HELP ME!!"
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by BobbyJ10465 on 2009-02-11
Hi All, 
p
I came across the Sprint Mobile Broadband Setup guide for linux. Being new to this stuff (former Windows user), I followed everything to a T! I have the KPPP set up, the terminal sees the USB cable connected, the broadband card is working...but no connection. I continue to get an error message...
EXIT STATUS 0, which means nothing to me. 

The ONLY thing I could think of that may be an issue is that this setup guide I have been using does not provide a vendor ID and product ID as I believe this is a new modem being provided. I did take an educated guess when setting up, and again, the terminal recognizes that I do have a sierra modem connected. 

Can someone please assist? I would greatly appreciate it.

---

### Post by rovert1214 on 2009-02-12
I am having the same problem. My friend has the compass 597 and it worked as soon as i plugged it in so i figured this one would be the same. I am running Intrepid. The 598 shows up correctly when i lsusb but i can't get it to come up in network manager like the 597 did.

---

### Post by cdtech on 2009-02-12
I'm using the EVDO USB device. List the device using:
```
lsusb
```
This should show the product and vendor ID.
```
Bus 004 Device 002: ID 064e:a101 Suyin Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 4971:ce15  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID **1410:4100**  
Bus 001 Device 003: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 001 Device 001: ID 0000:0000
```

---

### Post by cdtech on 2009-02-12
Which driver are you using?

---

### Post by tjsadler on 2009-02-16
I am having a problem with the same card. I followed the sprint guide for linux but if I use Gnome PPP it dials and then sits there saying "waiting for prompt..." If I use KPPP it logs on and then says PPPD Daemon has died error 0. Frustrating! I don't want to go back to XP just for one stupid piece of hardware!

---

### Post by CRCarl on 2009-04-22
You need to modify your /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi file.


```
sudo vim /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi
```

find the section starting on line 220

> <!-- Sierra Wireless -->
<match key="@info.parent:usb.vendor_id" int="0x1199">
<!-- EM5625,2x MC5720,2x MC5725,AirCard 595,AirCard 597E,USB Dongle 595U,AirCard 580, Compass 597 -->
<match key="@info.parent:usb.product_id" int_outof="0x0017;0x0018;0x0218;0x0020;0x0220;0x00 19;0x0021;0x0120;0x0112;0x0023;***0x0025***">
<match key="@info.parent:usb.interface.number" int="0">
<match key="serial.port" int="0">
<append key="modem.command_sets" type="strlist">IS-707-A</append>
</match>
</match>
</match>

Add the product_id 0x0025 as above. Save the file, exit. Remove the modem, re-insert. Should do it!

Craig

---

