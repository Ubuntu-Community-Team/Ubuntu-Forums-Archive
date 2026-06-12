---
title: "FusionHDTV DVB-T Lite Installation"
date: 2007-06-18
forum: Multimedia &amp; Video
---

### Post by Muffy on 2007-06-18
I have a FusionHDTV DBB-T Lite digital TV card that I need to get installed in Ubuntu 6.10 Edgy. Does anybody know how I can do this?

---

### Post by koshari on 2007-06-18
you need to load the correct module at startup,  to do this add the module name to the modules file. there are 2 modules for this card depending on the age of it, the below info is for the bt8xx chipset version of the card 

 loading the module for the dvico lite dvb-t card

This card is quite popular in Australia and operates well with MythTV. It is supported by stock kernels of 2.6.9 or later.

The only command necessary to get the card to work is:

```
/sbin/modprobe dvb-bt8xx
```

or simply place

```
dvb-bt8xx
```

in the /etc/modules list for it to load at bootime

then the system will registar the device under /dev/dvb/

then use scan utils and tzap to tune your frequencies, you ana then view using mythtv or
 some other viewing program like kaffeine.

---

