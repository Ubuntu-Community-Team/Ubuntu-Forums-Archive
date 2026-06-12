---
title: "Siemens sx541 's file server (samba problem?)"
date: 2006-06-07
forum: Networking &amp; Wireless
---

### Post by tribaal on 2006-06-07
Hi all

Today I bought a shiny new Siemens sx541 wireless router.

It's an amazing piece of hardware, that not only does wireless routing, but also DSL modem, ethernet router (4 ports), VoIP (using a regular phone), printserver, webserver (http, FTP,...), dynamic DNS synchronisation, and... fileserver!

Everything except the latter worked as a charm out of the box with Ubuntu, and I'm overall really satisfied with it. I really recommend this piece of hardware if you're looking to buy a nice router.

The router has an USB port, to connect a printer or some mass storage device, and that works quite well: you can manage everything from the web-based config interface.
The fileserver, however, is supposed to masquerade as a windows machine (you get to set a hostname, a workgroup/domain and a description), that serves whatever there is plugged in the USB port (if it's mass storage). So I plugged in my external HDD (250Gb), and that seemed to work pretty well, until I tried to access the files from the network with Ubuntu: 

The hostname isn't really working (it doesn't appear in the "windows network" list), but I managed to access it by IP adress instead. I can see the root folder that's shared (named after my USB HDD's partition name, it's FAT32), but I cannot list it's contents, let alone access a file.

I cruised on the Siemens forums, and seemed to understand that others were experiencing the same problem, but the forums are all in German, and I cannot read it.

Does anybody else have this particular router? Did you get the fileserver to work with Ubuntu? How?

Thanks a load

- trib'

---

### Post by adrpater on 2007-05-11
This is like my question [http://ubuntuforums.org/showthread.php?p=2636361](http://ubuntuforums.org/showthread.php?p=2636361)
Though the problem remains unresolved!

---

