---
title: "Problem after upgrade Ubuntu 10.04 to 10.10 beta"
date: 2010-09-20
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by mbogevik on 2010-09-20
Hei all.  I have upgraded my Ubuntu 64b from 10.04 to Ubuntu 10.10 beta.  This was done by "Alt + F2" entering "update-manager -d".  All the processes seemed to go fine but after reboot I got problems.  Then I only a text based terminal comes up.  No GUI interface at all.  What could go wrong ?  Or did I miss something in upgrade procedure ?  And can I fix this ??

Thanks for all help

---

### Post by jakeyyoyo on 2010-09-20
exactly the same issue here

---

### Post by wilee-nilee on 2010-09-20
Okay can the second poster start their own thread as well, as this may not be the same problem and it is difficult to follow two different things in one thread.;)

OP can you be more descriptive of what happens when you boot do you get to a command line to log in, if so log in then run startx. If it is a graphics driver problem you may need to hold down shift when you power up to see the grub menu hit e and put nomodeset  right at the end of the first kernel and then hold down the ctrl key and hit x to boot.

Also state whether you have everything you want saved backed up or not.

---

### Post by mbogevik on 2010-09-20
Yes, I get the command line and are able to log in.  I have tried all the suggestions you gave without any luck.  Here is what error log shows :

  (EE) Failed to load /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
  (EE) Failed to load module "fglrx" (loader failed, 7)
  (EE) No drivers available

  Fatal server error:
  No screens found

So it may seem that it is my graphic cards driver that is the problem (Gigabyte Radeon HD 4550 512 MB).
I have tried to put "nomodeset" after kernel line on both places, but it may be a detail I have missed out here.

---

### Post by uRock on 2010-09-20
Moved to MM Testing and Discussion.[URL="http://ubuntuforums.org/forumdisplay.php?f=385"]
[/URL]

---

### Post by wilee-nilee on 2010-09-20
> **mbogevik said:**
> Yes, I get the command line and are able to log in.  I have tried all the suggestions you gave without any luck.  Here is what error log shows :

  (EE) Failed to load /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
  (EE) Failed to load module "fglrx" (loader failed, 7)
  (EE) No drivers available

  Fatal server error:
  No screens found

So it may seem that it is my graphic cards driver that is the problem (Gigabyte Radeon HD 4550 512 MB).
I have tried to put "nomodeset" after kernel line on both places, but it may be a detail I have missed out here.

Hopefully somebody will see what is up here and have some answers.

---

### Post by Arla on 2010-09-20
Did you see my post?

[http://ubuntuforums.org/showthread.php?t=1569083&page=2](http://ubuntuforums.org/showthread.php?t=1569083&page=2)

I seemed to resolve it by removing the nomodeset option.

---

### Post by mbogevik on 2010-09-21
I do not have "nomodeset" in my boot.  Anyway I tought this command was a force command to use a default graphic card driver that works on "all" cards ?

Thanks for trying to help :)  I will continue my search tonight when I'm home from work..

---

### Post by wilee-nilee on 2010-09-21
> **mbogevik said:**
> I do not have "nomodeset" in my boot.  Anyway I tought this command was a force command to use a default graphic card driver that works on "all" cards ?

Thanks for trying to help :)  I will continue my search tonight when I'm home from work..

nomodeset=low graphics mode to have access to install any drivers needed if that is the problem.

---

### Post by mbogevik on 2010-09-21
I also tried this suggestion (Empty all lines in /etc/X11/xorg.conf) only with result that monitor goes to standby when trying to boot, also in recovery mode.

[http://ubuntuforums.org/showthread.php?t=1576047&highlight=beta](http://ubuntuforums.org/showthread.php?t=1576047&highlight=beta)

---

### Post by ktp on 2010-09-21
I am guessing you were using proprietary ati drivers before upgrading.  If so please purge it and remove/backup the xorg.conf file and see if that fixes it.

this might help also:
[http://ubuntuforums.org/showthread.php?t=1549872](http://ubuntuforums.org/showthread.php?t=1549872)

---

### Post by mbogevik on 2010-09-21
I have removed and updated the drivers (xserver-xorg) with no other result.  Not until I copied the xorg.conf.failsafe into xorg.conf and changed line 3 to "Driver "fbdev"" I got Ubuntu up working.
However, without any proprietary VGA driver in "Additional Drivers", and downloading 64 bit drivers from ATI/AMD was no success when installing, returning "Error: ./default_policy.sh does not support version"

What worries me is why Ubuntu 10.10 beta installer did not disable my proprietary driver when this was specially specified by installer during installation procedure ?

So my Ubuntu is up, so far in bad graphic, so if anyone out there please can tell me is there is a way of getting proprietary now called "Additional Drivers" to contain a ATI driver again, please let me know :)

---

### Post by ktp on 2010-09-21
you have to wait until amd gives driver that supports xorg-server 1.9

---

### Post by mbogevik on 2010-09-21
> **ktp said:**
> you have to wait until amd gives driver that supports xorg-server 1.9

Ok, thanks, I would think there is not more that I can do at this point.

I remember when AMD took over ATI, they promised that ATI driver for Linux should get same priority as Linux.  I think not...

---

### Post by mbogevik on 2010-09-23
Starting Ubuntu in "recovery mode" and selecting to reset graphic when entering safe mode now makes Ubuntu 10.10 beta working normal with ATI card again (in normal start).
The problem seems to be that even upgrade program says it would disable the proprietary ati driver it did not do that at all, with result that driver crashed since it dit not support the kernel version.

So 3D effects works fine (compiz) and I am starting my testing :)

---

### Post by ktp on 2010-09-23
> **mbogevik said:**
> Ok, thanks, I would think there is not more that I can do at this point.

I remember when AMD took over ATI, they promised that ATI driver for Linux should get same priority as Linux.  I think not...

I guess you didn't have to wait to long since updated drivers landed...just update and enable/install them.

---

### Post by hislordship on 2010-10-02
I am having the exact same problem but don't understand what the solution is you have come up with if any?

---

