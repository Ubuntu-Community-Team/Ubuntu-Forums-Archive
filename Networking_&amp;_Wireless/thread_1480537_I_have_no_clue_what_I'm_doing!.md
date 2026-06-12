---
title: "I have no clue what I'm doing!"
date: 2010-05-11
forum: Networking &amp; Wireless
---

### Post by Mimichii on 2010-05-11
Okay so my friend returns my computer to me with Linux (Ubuntu) installed on it. I haven't a clue how this O/S works, so I'm trying to figure out how to set my wireless up on it.

I've looked over guides, some say there's supposed to be something that lists wireless networks available, but there isn't. 

The only thing that seems to be available is the top right thing that says "network connections" and lets me click wireless and "add".  I don't know what to do from there. 

Can anyone help?

---

### Post by lisati on 2010-05-11
First thing to check: is the wireless adapater switched on? Many laptops come with a switch or a button that can be used to disable and/or enable wireless.

---

### Post by Mimichii on 2010-05-11
> **lisati said:**
> First thing to check: is the wireless adapater switched on? Many laptops come with a switch or a button that can be used to disable and/or enable wireless.

It's actually a desktop and the wireless card works just as it always has.

---

### Post by Iowan on 2010-05-11
Welcome to Ubuntu and the Forums!
I'm a bit curious - were you expecting to get the computer back with Ubuntu? For some it would be an opportunity - for others, an imposition.

If you're willing to "go under the hood" - open a terminal (Applications>Accessories>Terminal) and enter:```
sudo lshw -C network >lshw.txt
``` The first parts lists the networking hardware, the ">lshw.txt" copies it to a file. You can copy that file to a floppy or USB stick and post it here. More details if you need them... :)

---

