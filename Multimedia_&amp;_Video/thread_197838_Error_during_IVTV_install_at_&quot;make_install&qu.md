---
title: "Error during IVTV install at &quot;make install&quot;"
date: 2006-06-16
forum: Multimedia &amp; Video
---

### Post by planetmn on 2006-06-16
Hello,
I am trying to compile the IVTV drivers for my PVR-150 card.  I am following the directions in Hyams guide at [http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)

After I have downloaded and untarred the drivers, I make the file and then make install.  I seem to be getting errors during make install, the response is posted below.

```
root@mythtv:~/ivtv-0.4.4# make install
make -C driver install
make[1]: Entering directory `/root/ivtv-0.4.4/driver'
make -C /lib/modules/2.6.15-23-386/build M=/root/ivtv-0.4.4/driver modules
make[2]: Entering directory `/usr/src/linux-source-2.6.15'

  WARNING: Symbol version dump /usr/src/linux-source-2.6.15/Module.symvers
           is missing; modules will have no dependencies and modversions.

  Building modules, stage 2.
  MODPOST
make[2]: Leaving directory `/usr/src/linux-source-2.6.15'
make INSTALL_MOD_PATH= INSTALL_MOD_DIR=ivtv \
                -C /lib/modules/2.6.15-23-386/build M=/root/ivtv-0.4.4/driver modules_install
make[2]: Entering directory `/usr/src/linux-source-2.6.15'
  INSTALL /root/ivtv-0.4.4/driver/ivtv-fb.ko
cp: omitting directory `/lib/modules/2.6.15-23-386'
make[3]: *** [/root/ivtv-0.4.4/driver/ivtv-fb.ko] Error 1
make[2]: *** [modules_install] Error 2
make[2]: Leaving directory `/usr/src/linux-source-2.6.15'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/root/ivtv-0.4.4/driver'
make: *** [install] Error 2
```

Does anybody know what these errors are and how to fix them?  Is the fact that I'm missing Module.symvers (this warning comes up during the make command as well) have anything to do with it?

Thanks,
dave

---

### Post by vmifox on 2006-07-04
I'm having the same problem, except that I don't get the error messages after the Module.symvers warning.

Did you get this fixed?  How?

---

### Post by planetmn on 2006-07-13
No, I didn't get this fixed.  I kept trying to restart the whole MythTV installation procedure, and after a while got fed up.  I like Ubuntu as an OS, but it was just too much learning linux and trying to get a tuner/mythtv going.  So I downloaded and installed MythDora, which worked right after installation.

-dave

---

### Post by Prefader on 2006-08-28
I'm probably too late to help here, but just in case -

I had the *exact* problem you guys did - the culprit was a space at the end of the "EXTRAVERSION= -26-686" line in /usr/src/linux/Makefile - made sure it was wiped and *poof*, modules compiled.  Whitespace can be *so* annoying!!!!

Hope that helps someone.  :)

---

### Post by audiobottle on 2006-08-28
I don't know if I did something unique, but I was able to find the file by doing a ```
find /usr/src -name Module.symvers
```

The file was under /usr/src/linux-headers-2.6.15-26-686, so I just copied it to /usr/src/linux```
 cp /usr/src/linux-headers-2.6.15-26-686/Module.symvers /usr/src/linux
``` and it works fine now.

---

### Post by dancro on 2006-09-04
I got the same error, and also some errors during make install.  Thanks to prefader, I fixed /usr/src/linux/Makefile ```
EXTRAVERSION = 26-386
``` and insured that there was no space following.  That did nothing for the missing Module.symvers message, but it did get rid of the errors during make install.

Then I entered ```
cp /usr/src/linux-headers-2.6.15-26-386/Module.symvers /usr/src/linux
``` to copy Module.symvers based on audiobottle's suggestion, and did make and make install again.  That resulted in new errors, conflicts for cx25840.ko and saa7127.ko.  

Based on Hyam's how-to, I was prepared for those.  He says that the output will tell you what to do about any conflicts.  It says to hide or delete them.  I chose to hide them by copying and pasting the directions that printed out during the make install.  
```
mv /lib/modules/2.6.15-26-386/kernel/drivers/media/video/saa7127.ko /lib/modules/2.6.15-26-386/kernel/drivers/media/video/saa7127.ko.HIDE
``` ```
mv /lib/modules/2.6.15-26-386/kernel/drivers/media/video/cx25840/cx25840.ko /lib/modules/2.6.15-26-386/kernel/drivers/media/video/cx25840/cx25840.ko.HIDE
```I did depmod after each mv, then I did make and make install again and got no errors.       

By the way, I am following Sean Gardner's how to and making good progress.

+:D

---

### Post by morphodone on 2006-09-17
> **Prefader said:**
> I'm probably too late to help here, but just in case -

I had the *exact* problem you guys did - the culprit was a space at the end of the "EXTRAVERSION= -26-686" line in /usr/src/linux/Makefile - made sure it was wiped and *poof*, modules compiled.  Whitespace can be *so* annoying!!!!

Hope that helps someone.  :)

thanks bro

---

