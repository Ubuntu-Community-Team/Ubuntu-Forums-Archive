---
title: "f-spot + Canon Rebel XT problems"
date: 2008-01-24
forum: Multimedia &amp; Video
---

### Post by human39 on 2008-01-24
Hello everybody.

I'm having an odd problem with copying photo's directly from my Canon Rebel XT to f-spot (0.4.0)

The problem.  I plug my camera in and start it import.  It starts downloading "Previews" of the pictures on the card.  I have about 800 files on my kingston 4gb CF card.  I should mention that the card is almost full.  Probably only about 200 megs left.

It starts downloading the previews fairly quick, then it stalls on about photo 235, the progress bar slows to a crawl and the previews past that point never show up.

dmesg shows the following after the error:

usb 5-2: usbfs: USBDEVFS_CONTROL failed cmd f-spot rqt 64 rq 4 len 115 ret -110

Running: Ubuntu 7.10
Linux hostname 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux

Side notes: In the import drop down section says "Normal Mode" in parans.

libgphoto versions:
ii  libgphoto2-2                               2.4.0-2ubuntu2                            gphoto2 digital camera library
ii  libgphoto2-port0                           2.4.0-2ubuntu2                            gphoto2 digital camera port library

Any help would be appreciated.

---

### Post by human39 on 2008-01-25
A follow up on this:

I put my CF card in my card reader and it seems to be eventually throwing an error when copying all the pictures to my drive.  I'm using the cli 'cp' to do this.

It copies successfully for a few minutes then it starts to throw:

FAT: Directory bread(block 2143) failed
scsi 9:0:0:0: rejecting I/O to dead device

If I go back and start at where it left off, it works again for a few minutes then Ubuntu throws a dialog screen that tells me that its removing the device from the system along with the error above.

Its almost acting like a timeout error, um, without the actual timeout error. :)

---

