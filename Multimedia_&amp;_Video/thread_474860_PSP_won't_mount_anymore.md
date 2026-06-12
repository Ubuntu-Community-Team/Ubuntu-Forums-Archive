---
title: "PSP won't mount anymore"
date: 2007-06-15
forum: Multimedia &amp; Video
---

### Post by wolfen69 on 2007-06-15
i've never had a problem until today. i checked all my removable drive settings, but dont understand why. i have no problem connecting any other usb device. any suggestions?
this is my lsusb:

Bus 002 Device 021: ID 054c:01c8 Sony Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 010: ID 047d:106b Kensington 
Bus 001 Device 009: ID 043d:0093 Lexmark International, Inc. 
Bus 001 Device 006: ID 0609:031d SMK Manufacturing, Inc. 
Bus 001 Device 007: ID 0764:0501 Cyber Power System, Inc. 
Bus 001 Device 001: ID 0000:0000  

it obviously sees the device. don't know what else to do.

---

### Post by wolfen69 on 2007-06-15
bump

---

### Post by Adam_GUI on 2007-06-15
Just a shot in the dark, but works similarly with my PSP.

Is the PSP set to USB mode?

My PSP will only mount when the system is in USB mode.

---

### Post by wolfen69 on 2007-06-15
yes, it was in usb mode. i HAD to get files over to it, so i put the files on a thumb drive, rebooted, put in a Sabayon live cd, and transferred them over via sabayon.(which has no problem seeing any drive. it is my favorite live cd)

but i dont want to have to go through that every time.

---

### Post by wolfen69 on 2007-06-15
i was  using the ntfs automount program downloaded from automatix. so i uninstalled it, rebooted, installed it again, and everything works now. i dont want to use automatix, but until there is an easier way to mount drives with read and write, i'll be using it.

---

