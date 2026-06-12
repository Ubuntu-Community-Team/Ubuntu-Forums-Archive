---
title: "Video capture with Kino"
date: 2008-11-15
forum: Multimedia Software
---

### Post by 73ckn797 on 2008-11-15
I am trying to enable video capture through a firewire connection using Kino.

I followed a tutorial at:
[http://e4.video.blip.tv/2060000252563/Ddennedy-KinoScreencastTutorialCapturingDV563.ogg](http://e4.video.blip.tv/2060000252563/Ddennedy-KinoScreencastTutorialCapturingDV563.ogg)

I am getting the message "The raw1394 module must be loaded, and you must have read and write access to /dev/raw1394".

Following the tutorial I do not show specific video permission as a group.

> ls -l /dev/raw1394
crw-rw---- 1 root disk 171, 0 2008-11-15 13:43 /dev/raw1394

Shouldn't it show video instead of disk? 

Is the "171" a group number?

Below are results of terminal:

> lsmod | grep 1394
raw1394                32348  0 
ohci1394               37936  0 
ieee1394               96324  2 raw1394,ohci1394

>  groups
adm dialout fax cdrom floppy tape audio dip plugdev scanner fuse lpadmin admin sambashare vboxusers usbuser video

What can I do to gain the access I need?

The firewire pci card is showing up:

> lspci
01:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)

I am running Intrepid 8.10. signature shows system specs for desktop.

---

### Post by xc3RnbFO8P on 2008-11-15
Try **sudo kino**

---

### Post by DuncanNZ on 2009-02-23
Hi there, since you're having trouble with capture over Firewire to Kino you might want to look at my recent update of the [https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire) page. Please let me know if there are any problems with that guide.

---

