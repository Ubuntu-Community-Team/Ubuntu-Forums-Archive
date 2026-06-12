---
title: "[SOLVED] Deleting Pics from Toshiba PDR-M61 Camera"
date: 2009-06-06
forum: Multimedia Software
---

### Post by Sidewinder1 on 2009-06-06
F-Spot has nothing in the menus to delete the pics from the camera. Does anyone know of any linux software that will accomplish this. I checked "Places" and the camera is not listed. Is there a command line option to delete all pics from the camera? It is recognized as Bus 003 Device 004 as shown below:

de@de-desktop:~$ lsusb
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 1132:4335 Toshiba Corp., Digital Media Equipment [hex] PDR-M61
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0573:4d30 Zoran Co. Personal Media Division (Nogatech) Hauppauge WinTV-USB FM Model 40211 Rev B123
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 003: ID 046d:c207 Logitech, Inc. WingMan Extreme Digital 3D
Bus 001 Device 001: ID 0000:0000  
de@de-desktop:~$ 

Any help would be more than greately appreciated!

TIA,

Side


Marked as solved 'cause I read where it is better to delete from camera itself as the file system on most cameras (fat32) is *very* fragile regarding manipulations etc...

---

