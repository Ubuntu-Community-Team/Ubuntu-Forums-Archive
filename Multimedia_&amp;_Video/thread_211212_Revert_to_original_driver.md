---
title: "Revert to original driver?"
date: 2006-07-07
forum: Multimedia &amp; Video
---

### Post by kewldude606 on 2006-07-07
So I've been on a quest to install XGL.  Unfortunately, my computer hates me so after my first crusade I had to reformat my hdd and start over with Ubuntu.  Now, however, I think that there is some hope for not having to reinstall because I can boot off the LiveCD fine, its just my install that's screwy.

So how can I revert to my original set of drivers for my video card?  I have an ATi Radeon 9200 with 128mb of RAM (on the card).  I have full access to the command line on that machine, and I can get online with it.

Google really let me down today :(.

Oh, and I tried resetting my xorg.conf, didn't work.

---

### Post by raldz on 2006-07-08
the good thing about Ubuntu is, it creates backups of your xorg.conf everytime you change configuration.. just try to restore a previously working xorg.conf..

go to /etc/X11/ and look for files "xorg.conf.xxx" where "x" could be any alphanumeric code.. 

```
sudo cp /etc/X11/xorg.conf.xxxx /etc/X11/xorg.conf
```

xorg.conf.xxx << this should be your previously good working config..

---

### Post by kewldude606 on 2006-07-08
> **raldz said:**
> the good thing about Ubuntu is, it creates backups of your xorg.conf everytime you change configuration.. just try to restore a previously working xorg.conf..

go to /etc/X11/ and look for files "xorg.conf.xxx" where "x" could be any alphanumeric code.. 

```
sudo cp /etc/X11/xorg.conf.xxxx /etc/X11/xorg.conf
```

xorg.conf.xxx << this should be your previously good working config..

I tried that, it didn't work.

Also, if I try to boot up normaly, I get a lot of "scheduling while atomic" errors.

---

### Post by kewldude606 on 2006-07-08
Is there a way to do something like a "repair install" for Windows where it just replaces the system files with the system files from the CD (i.e. everything except the home directory)?

I'm really looking for any idea here....

---

### Post by Billquinn1 on 2006-07-08
Did you think about resetting your xorg file with

$ sudo dpkg-reconfigure xserver-xorg


Take all the defaults and that should be what you had to start.

---

### Post by raldz on 2006-07-08
ATI drivers works pretty well on Dapper.. it's just probably a messed up config..

If you could run the live CD or have another Ubuntu on another machine, the documentation is pretty simple on how to install and configure your ATI driver.. just Go to System > Help > System Doc > Desktop Guide > Configuring Your System > Hardware, there is a section there on that same page on how to install ATI drivers properly..

---

### Post by kewldude606 on 2006-07-09
I followed Raldz directions and it incorperated what Billquinn said.

For future reference:
```
sudp apt-get install xorg-driver-fglrx
sudo dpkg-reconfigure xserver-xorg
# Say yes to auto-detect
# Pick fglrx when it asks for a driver
```

---

