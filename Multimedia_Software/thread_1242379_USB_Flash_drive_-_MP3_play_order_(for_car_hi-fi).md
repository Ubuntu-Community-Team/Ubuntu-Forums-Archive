---
title: "USB Flash drive - MP3 play order (for car hi-fi)"
date: 2009-08-17
forum: Multimedia Software
---

### Post by BFG on 2009-08-17
I have a Pioneer [DEH-P700BT]("http://www.pioneer.eu/eur/products/archive/DEH-P700BT/index.h") car head unit that accepts USB flash drives, but albums play out of sequence, even when filenames and ID3 tags are correct.


On reading up on this, it's a known problem and the result of the head unit playing files in the order in which it finds them on the flash drive, which is based on the order they were transfered. Nautilus seems to transfer files out of sequence.

Is there a Ubuntu command which can touch the files on the USB drive to put them in the right order?

Which file system format does ubuntu use for flash drives?


There are some windows solutions (which I'd rather not use):
[http://www.murraymoffatt.com/software-problem-0010.html](http://www.murraymoffatt.com/software-problem-0010.html)
[http://www8.pair.com/dmurdoch/programs/lfnsort.htm](http://www8.pair.com/dmurdoch/programs/lfnsort.htm)


Edit:

Found fatsort, will give that a try.
[http://packages.ubuntu.com/jaunty/fatsort](http://packages.ubuntu.com/jaunty/fatsort)


Info here: [http://ubuntuforums.org/showthread.php?t=872062](http://ubuntuforums.org/showthread.php?t=872062)

---

### Post by bfkmnemonic on 2012-04-19
I have the same problem.

Did it work?

I am thinking of maybe doing something like:
BASH# for I in `ls *.mp3` ; do mount /dev/usb /media/usb ; cp $I /media/usb/ ; umount /media/usb ; done

Where /dev/usb is the usb device

---

