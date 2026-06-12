---
title: "MRL Error in XINE-UI"
date: 2008-10-16
forum: Multimedia Software
---

### Post by Black Razor on 2008-10-16
I'm getting a weird error installing xine-ui.  When I try to play DVD's I get this error:

There is no input plugin available to handle 'dvd:/'.   Maybe MRL syntax is wrong or file /stream source doesn't exist.

Here is a copy of the terminal output:

libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading

The weird thing is I can play DVD's in Totem, just not Xine.  Anyone know how to fix this?

---

### Post by shirilover on 2008-10-16
You need to open the preferences for xine and set the dvd resource location to the of your DVD drive.
By default, this is set to /dev/dvd; however, your drive is probably something else.

---

### Post by Black Razor on 2008-10-18
Well I tried that before, and again at your request, but for some reason it doesn't like that my primary DVD drive identifies itself as 'cdrom0'.  It still gives that error even if I set it to the device id.

---

### Post by mc4man on 2008-10-18
run this to get the /dev links of your drive. 
```
sudo lshw -C disk
```

---

