---
title: "unable to scan using HP laserjet m28W"
date: 2019-09-21
forum: Multimedia Software
---

### Post by lordcenzin on 2019-09-21
Hi all,
i am an old ubuntu user, and everytime i needed any help i was very lucky to be able to find it.
Now, unfortunately I am not.
I bought a multifunction printer/scanner from hp, since I read it was compatible (i needed to scan over wifi) but it seems it is not so easy to configure.
I installed hplip package with all dependencies, so that 
```

hp-doctor -r

```
does not give any error.
However when I start the scan command, it starts BUT after few seconds stops with error:
```

$ hp-scan 

HP Linux Imaging and Printing System (ver. 3.19.1)
Scan Utility ver. 2.2

Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


-----------------
| SELECT DEVICE |
-----------------

  Num       Scan device URI                                              
  --------  -------------------------------------------------------------
  0*        hpaio:/usb/HP_LaserJet_MFP_M28-M31?serial=VNC3K90935         
  1         hpaio:/net/HP_LaserJet_MFP_M28-M31?hostname=NPI45DD55.local  
  2         hpaio:/net/hp_laserjet_mfp_m28-m31?ip=192.168.1.4&queue=false

Enter number 0...2 for device (q=quit, <enter>=default: 0*) ?0
warning: No destinations specified. Adding 'file' destination by default.
Using device hpaio:/usb/HP_LaserJet_MFP_M28-M31?serial=VNC3K90935
Opening connection to device...

Resolution: 300dpi
Mode: gray
Compression: JPEG
Scan area (mm):
  Top left (x,y): (0.000000mm, 0.000000mm)
  Bottom right (x,y): (215.900009mm, 297.010681mm)
  Width: 215.900009mm
  Height: 297.010681mm
Destination(s): file
Output file: 
warning: File destination enabled with no output file specified.
Setting output format to PNG for greyscale mode.
warning: Defaulting to '/home/gennaro/hpscan001.png'.

Warming up...
 

Scanning...
error: SANE: Error during device I/O (code=9)
Closing device.

```
I searched a lot about this error, everyone is having it but not many soved it in the end.
I obtain the corresponding error also with xsane

On the other side, I tried Vuescan, and it worked perfectly. 
However, before buying the version, i would like to understand if I missed something or not.

Any suggestion?

Thanks in advance

---

### Post by Autodave on 2019-09-22
Are you using *simple scan *or *xsane?  Xsane *works fine for me, but I never could get simple scan to work.

---

