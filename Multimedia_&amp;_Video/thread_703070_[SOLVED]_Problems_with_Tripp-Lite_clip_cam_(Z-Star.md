---
title: "[SOLVED] Problems with Tripp-Lite clip cam (Z-Star Microelectronics Corp. ZC0301 WebC"
date: 2008-02-21
forum: Multimedia &amp; Video
---

### Post by dshuck on 2008-02-21
I am trying to install a Tripp-Lite clip cam under Hardy.  From the information in lsusb...
```

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 046d:c401 Logitech, Inc. TrackMan Marble Wheel
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0ac8:301b Z-Star Microelectronics Corp. ZC0301 WebCam
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

... it appears that the camera should be supported with the spca5xx drivers as that the vender ID 0x301b appears in [this list](http://mxhaard.free.fr/spca5xx.html).  I downloaded this driver, made sure that my headers matched my kernel, and installed it based on the instructions in the README.

However, I can't seem to get it to work. For instance, when I open camorama, I get the message:

[[img]http://img120.imageshack.us/img120/6445/screenshoterrorcamoramata8.png[/img]](http://imageshack.us)

I am quickly running out of ideas and getting desperate.  Can anyone help me get this thing working?  

Thanks in advance!

---

### Post by dshuck on 2008-02-21
BTW... I don't know if it is helpful to anyone else, but lsmod gives me:

```
$ lsmod | grep zc
zc0301                 52356  0 
compat_ioctl32          2304  1 zc0301
videodev               29440  2 gspca,zc0301
v4l2_common            18304  2 zc0301,videodev
usbcore               145516  6 gspca,usbhid,zc0301,ehci_hcd,uhci_hcd

```

---

### Post by dshuck on 2008-02-21
Just an update... I followed the instructions here: [http://blog.myfenris.net/?p=377](http://blog.myfenris.net/?p=377)

Everything seemed to match up step by step until I got to the part where I did a ls on /dev/video0.  I receive an error that there is no folder or directory /dev/video0.

Any thoughts on this would be appreciated.

---

### Post by dshuck on 2008-02-25
UPDATE:  It is working now.  The fix?  I rolled back from Hardy to Feisty and it picked it up natively. :)

---

### Post by fendora on 2008-04-11
dshuck,

thanks for referring to my blog, i just recently upgrade to hardy and i dont have a time to test/connecting my webcam to hardy yet .. but ill try a.s.a.p might be this wkend so that i can give an idea or i might be got bump like you ... i will let u guys know the results ..

have u install the gspca-source from repo ? it might be not connected thats why when u ls on /dev/video0 it wont appear ...

try this ..

```

#!/bin/bash

sudo modprobe -r gspca
sudo modprobe -r zc0301
sudo modprobe gspca
dmesg

```

see the output of the dmesg to check whether your cam got connected or not ...

---

