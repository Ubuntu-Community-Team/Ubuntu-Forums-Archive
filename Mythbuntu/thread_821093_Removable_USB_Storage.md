---
title: "Removable USB Storage"
date: 2008-06-06
forum: Mythbuntu
---

### Post by RTucker on 2008-06-06
Has any one had any luck or know how to get removable usb drives to work in mythtv? I got it working by creating symlinks to the drive path, but there are a few problems with this.
 
Firstly, the path is dependant on the label of the drive, ie. symlinks point to /media/*label_of_drive* which means that it only works for THAT drive, and it only works as long as you don't rename it.
 
Also, if you disconnect/reconnect the drive while the system is on, the reconnected drive shows up as /media/*label_of_drive*_ which breaks the symlinks.
 
Plus, mythtv keeps detecting new files/missing files when the drive changes/is removed/is connected, which works, but is not really ideal.
 
So, what I'm really asking is:
 
Is there any way to make any removable drive accessible to mythtv automatically? And, is there any way to get all or part of the library to function as a simple file browser without adding everything to its database or whatever it does to it?
 
Thanks in advance for any ideas.

---

### Post by ian dobson on 2008-06-07
Hi,

Couldn't you use UDEV to create a symbolic link for all USB drives that always points to the same mount?

I've never tried it myself for USB devices but I've seen it used for tuners that sometimes get video0 and at other times video1.

Regards
Ian Dobson

---

### Post by RTucker on 2008-06-08
Thanks for the info,
 
I've had a look in to UDEV and it looks like it might provide a partial solution. As far as I can see, it wont let me mount ant USB Mass Storage device as the same name automaticaly. But it wil let me mount any device plugged in to a certain USB port under the same name regardless of what it is, or when it is plugged in. Given the type of system this is, its not a big deal to dedicate one or two USB ports to this function and then create symlinks to have it show up as a 'USB' subfolder within the media library.
 
Still, does anyone know if you can get mythtv to simply act as a file browser for the videos folder, rather than adding/removing the files from its database everytime you change something?

---

