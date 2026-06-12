---
title: "Camera SD Card and USB SD Card Reader Not Working Properly"
date: 2017-01-09
forum: Multimedia Software
---

### Post by pjmccartney123 on 2017-01-09
Hi,

I have a Canon G1X Mark 2 and I put the SD card into my laptop with Ubuntu 14.04LTS. It mounts the SD card in so far as I can see it on the bar on the left, but I can't open it to access the photos I have taken. I then bought an SD card reader with a USB on the other end of it. Same thing. It shows up on the bar on the left as pendrives do, but I cannot open it. There is sometimes an error message when I use the USB SD card reader which says "Unable to mount".

Any help guys?

Thanks

---

### Post by Autodave on 2017-01-09
Is the card readable in another machine?

---

### Post by pjmccartney123 on 2017-01-09
Hi Autodave. Thanks for your reply.

Yes it works in my laptop with Windows on it.

---

### Post by ron998 on 2017-01-09
> **pjmccartney123 said:**
> ... but I can't open it to access the photos I have taken...
Hi
Use
```
sudo gparted
```
View the drives /dev/sda, /dev/sdb etc.
See if your SD card is there and which format type is used, fat32 or whatever.

---

### Post by pjmccartney123 on 2017-01-09
Hi Ron998. Thanks for the reply. It doesn't have any information on gparted. If I open dev/sda it just has my HDD. If I choose the SD card which is dev/mmcblk0 (64gb) then it there is an exclamation mark next to the listing with the message "not mounted correctly". It does say it is "exfat" for the file system though, if that helps?

---

### Post by ron998 on 2017-01-09
> **pjmccartney123 said:**
> ... It does say it is "exfat" for the file system though...
Hi
Maybe you need some tools "exfat-fuse and exfat-utils".
Info from google search here ---> [http://askubuntu.com/questions/451364/how-to-enable-exfat-in-ubuntu-14-04](http://askubuntu.com/questions/451364/how-to-enable-exfat-in-ubuntu-14-04)

---

### Post by pjmccartney123 on 2017-01-10
Hi Ron998! Thanks so much. This was indeed the problem and the solution. I owe you a pint!

---

