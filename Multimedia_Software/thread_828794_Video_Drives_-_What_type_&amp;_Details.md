---
title: "Video Drives - What type &amp; Details"
date: 2008-06-14
forum: Multimedia Software
---

### Post by zombrax on 2008-06-14
hey all,

just wanting to know what command i can use to see what video drivers (the type & ver) are installed on my laptop?

also is there a way that i can manually get the system to check for updates?

my resolution and everythign is fine; its just that when i run some media files i get a line across my laptop screen. 


many thanks

---

### Post by lswest on 2008-06-14
you can check the drivers by doing this: ```
lshw -C Display
``` which will print out the section with information about your display (e.g. video card) and there will be a line in the last part of info that reads "driver=" and the bit afterwards are the drivers you're using.  about the version, that depends on what your card is.  However, chances are you can google the driver name and find out which version is in the repos with ```
sudo aptitude show [packagename]
```

---

