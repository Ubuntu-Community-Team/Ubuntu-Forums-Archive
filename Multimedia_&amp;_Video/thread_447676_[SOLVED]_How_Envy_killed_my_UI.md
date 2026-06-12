---
title: "[SOLVED] How Envy killed my UI"
date: 2007-05-18
forum: Multimedia &amp; Video
---

### Post by lebron_jordan_kobe on 2007-05-18
I am very envious of those who got this script to work, tried it yesterday with Ubuntu 7.04 and a GEFORCE 7600GT............

1.) Installed the script
2.) Ran the UI version
3.) It did alot of stuff
4.) I let it autoconfigure my Xorg
5.) Restart

The screen blinks twice


THEN the BLUE SCREEN OF DEATH!!!!!!!!

(Reinactment maybe not actual words)

```


       *********************************************************
                         AN ERROR HAS OCCURED WITH XSERVER
                                   REVIEW THE EVENT LOG

                       YES                                        NO
      *********************************************************


```

So I click 'YES' it says 'NVIDIA Kernel' not found! Then I click 'OK' then  a similar BLUE screen comes up and NOW the UI won't load. Great stuff huh? I know someone else has had a similar problem with ENVY. Anyone else know how to use it without it killing your GNOME????????

---

### Post by Kobalt on 2007-05-18
I'd say don't use it (with all due respect to its maker Alberto) : now that Ubuntu comes with a Restricted Drivers Manager you can get your nVidia drivers installed in just a couple of clicks...

---

### Post by tseliot on 2007-05-18
Try typing:
```
sudo depmod -a
```
and reboot

---

### Post by lebron_jordan_kobe on 2007-05-18
What will 

sudo depmod -a

do? Is this done before or after I run ENVY?

---

### Post by akba0012 on 2007-08-23
This also happend to me this morning. 

Did sudo depmod -a work for you?

I would like to get back into Ubuntu without having to reinstall everything

---

### Post by tseliot on 2007-08-23
Restore the backup of your xorg.conf which Envy made

Boot in Recovery Mode (select it from the GRUB menu)

type:
```
cd /etc/X11/
```
```
ls
```
you'll see xorg.conf and other backup files (e.g. xorg.conf_backup_200703022015)

replace xorg.conf with a backup:
```
sudo cp name_of_your_backup_file xorg.conf
```

then reboot by typing:
```
reboot
```

---

### Post by akba0012 on 2007-08-23
Wow thanks man.

I will try it when I get home.

Then its that ellusive task of trying to get my screen resolution higher. I will try the Restricted Drivers Manager

---

### Post by tseliot on 2007-08-23
> **akba0012 said:**
> Wow thanks man.

I will try it when I get home.

Then its that ellusive task of trying to get my screen resolution higher. I will try the Restricted Drivers Manager
make sure you uninstall the driver through Envy before you do that.

---

### Post by akba0012 on 2007-08-23
> **tseliot said:**
> make sure you uninstall the driver through Envy before you do that.

Er.. How? :-| Sorry, i have no idea how to get around linux, I just want my resolutio up! haha. I think that is the hardest part for a noob to do. I'll get it though, sometime soon though. I hope! Thanks for your help so far Tesliot

---

### Post by tseliot on 2007-08-23
> **akba0012 said:**
> Er.. How? :-| Sorry, i have no idea how to get around linux, I just want my resolutio up! haha. I think that is the hardest part for a noob to do. I'll get it though, sometime soon though. I hope! Thanks for your help so far Tesliot

If you installed the driver through Envy you will have to uninstall it from there. Otherwise you won't need to uninstall anything

---

### Post by akba0012 on 2007-08-23
Oh ok, I gotcha. Input the commands you gave me to get Xserve back up, and then uninstall the drivers and THEN installed the restrictive drivers.

I thought you wanted me to uninstall envy drivers before getting xserve running, I just about gave up if I would have to uninstall envy though command lines. Thanks again.

---

### Post by akba0012 on 2007-08-23
Never mind ! I got it to work! hurra!

---

