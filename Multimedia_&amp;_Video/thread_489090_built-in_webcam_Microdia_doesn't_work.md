---
title: "built-in webcam Microdia doesn't work"
date: 2007-07-01
forum: Multimedia &amp; Video
---

### Post by andrei.kouznetsov on 2007-07-01
I have a laptop MS1034 with built-in webcam and I'm running Ubuntu 7.04. The camera does not work.

lsusb shows
```

Bus 005 Device 004: ID 0c45:624f Microdia 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 002 Device 001: ID 0000:0000  

```

So, the name of my camera is Microdia. After googleing I've found out that spca5xx should work with it. So I tested if it's loaded
```

$modprobe -l *spca*
/lib/modules/2.6.20-16-generic/kernel/ubuntu/media/gspcav1/gspca.ko

```

So, the module is loaded (and as far as I know the module is supplied with ubuntu by default).
when I switch on the webcam, dmesg says
```

...
[159109.600000] usb 5-5: new high speed USB device using ehci_hcd and address 3
[159109.736000] usb 5-5: configuration #1 chosen from 1 choice
[159654.452000] Linux video capture interface: v2.00

```

But there is no device /dev/video. In fact, ls /dev/video* gives
```

ls: /dev/video*: No such file or directory

```

Any ideas how to make it work?

---

### Post by vivalant on 2007-09-09
This webcam should be supported by the SN9CXXX driver at [http://www.linux-projects.org](http://www.linux-projects.org)
Have fun

---

### Post by roaldz on 2007-10-16
It is not supported by SN9CXXX, I have the same webcam too.
Some proof:
```
[ 3387.628932] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.48
[ 3387.629334] usb 2-4: Sorry, this is not a SN9C1xx-based camera (vid:pid 0x0C45:0x624F)
[ 3387.629526] usbcore: registered new interface driver sn9c102

```I haven't managed to get a working linux driver for this webcam. It's in my Compal HEL81 Notebook. Some ideas?

---

### Post by vivalant on 2007-10-16
> **roaldz said:**
> It is not supported by SN9CXXX, I have the same webcam too.
Some proof:
```
[ 3387.628932] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.48
[ 3387.629334] usb 2-4: Sorry, this is not a SN9C1xx-based camera (vid:pid 0x0C45:0x624F)

```I haven't managed to get a working linux driver for this webcam. It's in my Compal HEL81 Notebook. Some ideas?

It looks like that webcam IS supported. From your output you are using the wrong SN9C1XX driver v1.48, not the generic SN9CXXX driver v2.0x. From the FAQ, they are said to be different drivers..

---

### Post by roaldz on 2007-10-17
I can't download the 64-bit driver (Damn closed-source developers!) Still no webcam for me..

---

### Post by mrpurple on 2007-11-10
some of you have installed that web cam sucessfully under gusty gibbon 64 ? if yes how ?
thank you

---

