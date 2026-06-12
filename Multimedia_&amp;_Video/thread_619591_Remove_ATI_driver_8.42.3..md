---
title: "Remove ATI driver 8.42.3."
date: 2007-11-21
forum: Multimedia &amp; Video
---

### Post by Rippie on 2007-11-21
Hello people.

I've found a how-to how to get XGL to work with my ATI Radeon Mobility X1600 card. But it tells me that done from a clean install i should enable the ATI driver from the restricted driver and then install XGL server.

Now .... I've installed the latest version of ATI's driver 8.42.3 and desperately trying to get desktop effects to work PROPERLY !!! (they work, but very bad). So what do i need to do to not let my system use that driver ??

I dont think its enough just to enable the restricted driver for ATI and then install XGL server

Can anyone give me some hints ?

---

### Post by Prospero2006 on 2007-11-21
FYI:
The 8.42 driver didn't work for me, but after installing 8.40 it worked like a charm.
I'd try to install a few of the previous versions and see what comes.

Are you using the script where you have to type --buildpkg Ubuntu/gutsy at the end?
Then you dpkg -i all the debs and run m-a and all that?

---

### Post by Rippie on 2007-11-22
Hello ....

I have been using method 2 from this site

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

But how do i install an older version ?

---

### Post by Rippie on 2007-11-22
I've tried this morning to use the backup of the original xorg.conf file, and remove fglrx from:

```
/etc/default/linux-restricted-modules-common
```

After that i rebooted my laptop, and i enabled ATI from restricted drivers manager. and it seems that im able to use desktop effects, now i just need to run some more test when get home ;)

---

