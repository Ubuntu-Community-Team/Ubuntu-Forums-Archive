---
title: "Cannot pull pictures from SD card. Pictures half green or with lines."
date: 2011-05-01
forum: Multimedia Software
---

### Post by scooper77515 on 2011-05-01
Running Ubuntu 10.10 along side Windows7 on a 64-bit HP Pavilion dv7 Laptop. Everything works in Windows. Everything works in Ubuntu, except for 2 things. 

1) I can live with not being able to enable/disable wifi.
2) I cannot read photos from an SD card plugged into the laptops SD card reader. 

When I open the SD card in Ubuntu, I can see the file name, but the thumbnails show messed up pictures. Usually, the bottom half of the photo is solid green, and there are usually lines running through the photo, or it is divided into quadrants with one quadrant being ok, but the rest having the green and/or lines. 

I assume the driver for the card reader is not correct. 

Card reader works fine in Windows. So I have to reboot into windows, copy pictures from reader to a folder, then reboot into Ubuntu and I can see and open the photos just fine. Just cannot read and copy them from the card while in Ubuntu.

Any suggestions?

---

### Post by scooper77515 on 2011-05-01
Here is a sample picture...Copied from 8G SDHC Sandisk card.

Resized from Gimp, but still appears the same.

---

### Post by tgalati4 on 2011-05-01
Open a terminal in Ubuntu:

dmesg | tail

Then plug the SD card in and:

dmesg | tail -40

Note any errors.  Could be driver issue or lack of partitions on the SD card.  Put a partition table on it, but keep the format (probably FAT32).  I've noticed similar problems with a built-in card reader on one of my older computers, but not on a new card reader that I put into a much older computer.  Not all card readers are the same.  The Windows driver could have slower throughput, but less errors.

---

### Post by scooper77515 on 2011-05-01
After tail -40 it showed "New SD card at address 8fe4" then Card removed, then new card again, about 3 times. 

Is it mounting and unmounting over and over causing the errors?

---

### Post by tgalati4 on 2011-05-01
I don't have a listing handy from this machine, but it should say how many sectors and total size of the disk (SD card) and what device it was mounted as (/dev/sde1 for example).  Also any I/O errors will show up, which can happen when a card or reader don't behave.

Sometimes you can put the card in a camera and plug the camera into a USB and read the photos that way.

The mounting/unmounting problem could be a loose cable inside, or a bad socket that is not making a clean connection.  Sometimes kids stick gum in there because they can.

---

### Post by no2498 on 2011-05-02
a piece of dust will kill 1 too
in the reader or the usb port

---

### Post by scooper77515 on 2011-05-02
If dust or other disturbance, I would expect it to not read in Windows either.

OK, ran a couple other tests. If I have no pictures on it, it says "SD card mounted at 8fe4" but if I have pictures on it, it says "SD card found" and "sd card removed" the number of times that there are pictures on the disk. So 5 pictures on disk, it shows mounts/unmounts 5 times. 

No pictures, just mounts disk. 1 picture, mounts, unmounts, mounts. 

Make sense?

I also reformatted the disk from ubuntu, and stuck it back in camera. No difference.

---

### Post by no2498 on 2011-05-02
can you just open it not mount it
im still on 10.04 and i have to do it with my cam

---

### Post by scooper77515 on 2011-05-03
Not sure if I even have the usb cable for the camera anymore. 

I bet that would fix the problem, and verify that it is a bad driver for my on-board card reader.

---

