---
title: "camera and card reader not working"
date: 2008-04-12
forum: Multimedia &amp; Video
---

### Post by bnuk013 on 2008-04-12
neither my camera or card reader is working.  the card reader is an internal USB reader, it works with windows and the slots show up under "computer" in ubuntu, but they all say there are empty. If i keep the card in the camera it doesn't show on "computer" or f-spot.  however a plain ol' flash drive works fine whether i plug it in the front, back or the USB plug on the card reader itself.  8.04 beta right now but I am pretty sure the card reader worked with 7.10

---

### Post by bnuk013 on 2008-04-13
I noticed today that the card is showing up and is mounted but i get this error when i try to open it:

[I]The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "XD SLOT__".[/I]

i had named the different slots in windows, could that be a problem?

---

### Post by xc3RnbFO8P on 2008-04-13
Go to System > Administration > Users and Groups , your user name
see if there is a unchecked box

---

### Post by bnuk013 on 2008-04-13
Okay a few were unchecked, I checked them and so now the card reader works.  They weren't items that I would have thought mattered:
"send receive faxes"
"use scanner"
"use tape drives"

However the camera is still not getting picked up at all.  I have an older nikon that just works as mass storage and it works fine.  Following the example other similar threads here is my lsusb output.  obviously the fuji is the camera, realtek is either audio or LAN.  keep in mind I'm a complete newcomer and do not know the most basic terminal commands.

:~$ lsusb
Bus 005 Device 009: ID 04cb:01c6 Fuji Photo Film Co., Ltd 
Bus 005 Device 002: ID 0bda:0151 Realtek Semiconductor Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by xc3RnbFO8P on 2008-04-13
Plugin the camera and in terminal: **f-spot-import**

Or you could install kphotoAlbum from Synaptic Package Manager.
Search kphoto and install: **KphotoAlbum** and **Kipi-plugins**

In KphotoAlbum: Plugins> Import> Digital Camera> Setup> Add (find your camera)

---

### Post by bnuk013 on 2008-04-14
Ok yes, F-spot does pick up the camera.  However Picasa does not but I guess I need to take that issue elsewhere.  Is it not supposed to show up anywhere else or show any notification when a camera is plugged in?

---

### Post by xc3RnbFO8P on 2008-04-14
> **bnuk013 said:**
> Ok yes, F-spot does pick up the camera.  However Picasa does not but I guess I need to take that issue elsewhere.  Is it not supposed to show up anywhere else or show any notification when a camera is plugged in?

Yes in System> preferences> Removable drives and media preferences

---

### Post by xc3RnbFO8P on 2008-04-14
I got this command in Digital Camera:
> gnome-volume-manager-gthumb %h

---

