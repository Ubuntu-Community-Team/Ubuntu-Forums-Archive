---
title: "problems with dvd playback"
date: 2007-12-18
forum: Multimedia &amp; Video
---

### Post by tdclemens on 2007-12-18
Hi all,

I am using xine-ui to play DVD's. the problem is when I play the DVD i get a message "The souce can't be read.Maybe you don't have enough rights for this or source doesn't contain data (e.g.: no disc in drive). (Error opening vtsN=-1 domain=2)."

I ran xine-check and everything was good except

[ hint ] Your DVD drive seems not to be attached via ATAPI.
         This might be due to the use of an ide-scsi emulation.
         If you really have a SCSI DVD drive, your SCSI controller is likely
         to do perfect DMA, so there's no reason to worry about this.
         However, if you're using ide-scsi, there is a chance that DMA is
         disabled for the DVD drive. Moreover, I don't know how to enable
         DMA in that case, so you probably have to live with some performance
         loss. (FIXME: check for /proc/ide, provide solution)
         press <enter> to continue...

I am not sure this would cause a problem.
When I run xine in the command prompt the approximate output i get is:

This is xine (X11 gui) - a free video player v0.99.5.
(c) 2000-2007 The xine Team.
AFD changed from -2 to -1
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Attempting to retrieve all CSS keys
...
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x000284ec)!!

Maybe that error would help.
To make a long story short I found this issue in another forum and the guy installed the packages w32codecs, libxine-extracodecs and libdvdcss2 using some other repositories. 

Does anyone know what repositories I can use to get these packages - maybe they will fix my problem.

Thanks!

---

### Post by justinlawrence on 2008-05-18
Hi there, I am getting the same problem. I noticed as well that, since my upgrade to 8.04, my laptop (IBM thinkpad lenovo R60e) has slowed down considerably and there has been a lot more hard disk activity. I initially thought that I just needed more memory, but now have eventually tracked it down to a DMA problem and a further research leads me to believe this is a kernel problem.

If you run hdparm /dev/sda1 (or whatever your / drive is (find out using df -h), it shows:

 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device

This is what I believe is the actual problem.

Please can someone assist as I have looked and looked for almost 20 hours without coming any closer to a solution?

Is it possible for us to use a more (or less) up-to-date kernel? Might that help?

Thanks so much!

---

### Post by freddyg on 2008-05-18
hey guys, install libdvdcss2 from medibuntu.org, this enabled my playback

---

