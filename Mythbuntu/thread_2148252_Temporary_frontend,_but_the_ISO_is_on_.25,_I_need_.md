---
title: "Temporary frontend, but the ISO is on .25, I need .26"
date: 2013-05-24
forum: Mythbuntu
---

### Post by AlecJ on 2013-05-24
After the unfortunate demise of the screen of my trusted IBM Thinkpad that was the Kitchen Frontend for many years.
 I need to use another laptop temporary, 
 but the 12.04.2 ISO is using .25 and the backend here is using .26, mismatched schema and an endless loop of the frontend restarting.

Even making a bootable USB from the ISO resulted in the same problem and it won't allow the USB to be written, read only image.

So here is my solution, I'm hopping there is a better one out their.

I made a DVD from the ISO image,

Then removed (unplugged) all hard drives from my system except the DVD drive and an 8GB USB stick  (in my case a 8GB SD card in a USB converter)

This is because when I tried with the drives connected Grub started moving and generally confusing me, so with only 1 drive theirs no escape or problems to the other drives.

Then I booted on the DVD and installed Mythbuntu (Frontend only) onto the USB as a drive (of course your laptop has to be able to boot from USB)

So Now I have a "hard drive" bootable and importantly writeable, but still on .25

Once booted you get the normal looping frontend as it tries to communicate with the backend.
 I was able to click the Applications menu top left in between the restating Frontend, the menu stays ontop of the frontend and from here you can start Myth Control Centre and start to update this mini Myth Disk.

Selecting .26 entering the password "YouMustBeThisTallToRide" as directed on the screen then a few goes at Update manager, and my disk is complete

Enter the Laptops BIOS or setup and change the Boot priority putting all the USB options at the top, save and reboot with the USB inserted.

The First boot is quite slow but seem to speed up subsequently, anyway tested live TV and the Audio was muted? 

had to open a terminal and use "aslamixer" to unmute.

This laptop has an Nvidia graphics card which gives a superb 15" picture, very smooth and fast.

So a bit of messing about but I'm happy with the result and can just unplug the USB and use my laptop as normal.

I did installed the Frontend and .26 fixes on the Desktop (mint 14) but it runs so badly jumping picture etc, I gave up.

All comments gratefully received...

---

