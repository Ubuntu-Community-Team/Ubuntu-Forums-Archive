---
title: "Sirius Stilletto 2 tried all I could think still won't work"
date: 2008-09-12
forum: Multimedia Software
---

### Post by drascus on 2008-09-12
I have a Sirius Stilletto 2 Radio and I have tried everything I could think of to get it to work. I tried Gnomad and mtp. but when I plug the device in it doesn't even seem to be listed in /dev/ when I run mtp-detect it says no devices found. I posted this originally to absolute beginners talk but didn't get any answers. any ideas??

here is the original post: [http://ubuntuforums.org/showthread.php?t=783208&highlight=sirius+stiletto](http://ubuntuforums.org/showthread.php?t=783208&highlight=sirius+stiletto)

---

### Post by cariboo on 2008-09-13
What more have you tried to get it to connect? Have you tried wifi have you tried transferring music to the sd car with a card reader. What is the output of:

```
lsusb
```

When the device is connected via usb cable?

Does work with windows?

Jim

---

### Post by drascus on 2008-09-15
Alright this what I get from running the code > drascus@drascus-laptop:~$ lsusb
Bus 005 Device 006: ID 18f6:0110  
Bus 005 Device 005: ID 05e3:f192 Genesys Logic, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 0b05:1712 ASUSTek Computer, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 0461:4d09 Primax Electronics, Ltd 
Bus 001 Device 004: ID 046d:c313 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  


but I get the same thing without the device plugged in so I don't think that helps. it works under windows. though I would rather not have to use windows.
oh and yes it's via usb...

---

### Post by patdabak on 2009-01-22
1.Install the mtpfs package

2.Make a folder where you wish to mount the player (I called mine MTPFS and put it in my home directory for simplicity's sake)

3. Mount radio: mtpfs <mount location> (for me it would be "mtpfs MTPFS")

To unmount: sudo umount MTPFS (or whatever you called the folder)

---

### Post by andysoule on 2011-05-02
I am trying also to get my Stiletto 2 to talk to ubuntu.  I tried the above and get an error.

Error: Error stating file '/home/andy/sirius': Transport endpoint is not connected
Please select another viewer and try again.

---

