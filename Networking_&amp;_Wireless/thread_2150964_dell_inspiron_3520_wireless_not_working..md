---
title: "dell inspiron 3520 wireless not working."
date: 2013-06-02
forum: Networking &amp; Wireless
---

### Post by sbomb90 on 2013-06-02
Installed lubuntu 13.04 alongside windows 8 and  dell Inspiron 3520.  Everything seems to be working great except No wireless.  Seems like google searches keep leading me back to this thread ([http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560#215923](http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560#215923)).   I followed the 12.10 instuctions but when i type **[FONT=Ubuntu Mono]sudo dpkg -i wire*.deb [/FONT]**[FONT=Ubuntu Mono]into terminal[/FONT] I get this Error-

> Unpacking replacement wireless-bcm43142-dkms ...
Setting up wireless-bcm43142-dkms (6.20.55.19-1) ...
Loading new wireless-bcm43142-6.20.55.19 DKMS files...
Building only for 3.8.0-23-generic
Building initial module for 3.8.0-23-generic
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms_packages.py", line 22, in <module>
    import apport
ImportError: No module named apport
Error! Bad return status for module build on kernel: 3.8.0-23-generic (x86_64)
Consult /var/lib/dkms/wireless-bcm43142/6.20.55.19/build/make.log for more information.







Also--  Under "Addition Drivers"  there is a broadcom driver ( Broadcom Corporation: BCM43142 802.11b/g/n )  which has a little subheading which says "this device is not working". 

Not sure if im going to the right place for the driver I need or what steps I should take.  

Currently I can only connect to the internet using an Ethernet cable

---

### Post by sbomb90 on 2013-06-02
And it Randomly Started working.  I have NO idea if it was solved from switching it back and forth from the Proprietary driver or if it was me toggling the wifi switch a few times or if the gods just smiled on me.  Ill just go ahead and stop fiddling now though.  Sorry for a wasted thread.

---

