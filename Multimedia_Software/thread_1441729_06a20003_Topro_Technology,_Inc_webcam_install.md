---
title: "06a2:0003 Topro Technology, Inc webcam install"
date: 2010-03-29
forum: Multimedia Software
---

### Post by Berduchwal on 2010-03-29
I have been trying to get this web cam working for a long time.

lsusb:
```
Bus 004 Device 003: ID 06a2:0003 Topro Technology, Inc. 
```

dmesg
```
[ 1990.570050] usb 4-1: new full speed USB device using uhci_hcd and address 3
[ 1990.751460] usb 4-1: configuration #1 chosen from 1 choice

```

Kernel patch:
[https://patchwork.kernel.org/patch/16936/](https://patchwork.kernel.org/patch/16936/)

Driver project:
[http://code.google.com/p/tp68xx-webcam-drv/](http://code.google.com/p/tp68xx-webcam-drv/)

Cheese simply says no camera found.
Skryba says no devices found.

Since this kernel patch was 2009-04-07 which is nearly a year ago it should be in latest kernel?

cat /proc/version
```
Linux version 2.6.31-20-generic (buildd@crested) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010

```

I use 9.10 64bit.

Is there anyone up there who managed to get this camera working? Can you please let me know what can I do to get it running?

---

### Post by edea on 2010-07-09
I have this one (TOPCOM Mediakit USB 100):

[IMG]http://www.topcom.net/foto.asp?src=datasheets%2Ffiles%2FMediakit+USB+100.jpg&maxwidth=280&maxheight=280[/IMG]

And can't get it working either... It's detected too as:

> Bus 001 Device 006: ID 06a2:6810 Topro Technology, Inc. 

Did you have any luck?

---

### Post by Berduchwal on 2010-10-10
Still nothing for this one.

---

### Post by BicyclerBoy on 2011-01-17
I have been waiting for a long time for this thing to work.
Th webcam microscope was a regrettable purchase from Farnell.

The latest GSPCA 2.12.0 driver is supposed to support this webcam.
[http://moinejf.free.fr/](http://moinejf.free.fr/)

The topro part is recognized & the driver is loaded (lsmod).

On a 32 bit 10.10 netbook & using guvcview , I get black image & the webcam gets very hot.

So looks like should buy something that works.

---

