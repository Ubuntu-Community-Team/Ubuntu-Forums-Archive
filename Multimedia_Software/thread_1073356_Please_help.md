---
title: "Please help"
date: 2009-02-18
forum: Multimedia Software
---

### Post by shishir_knit on 2009-02-18
I was editing the xorg.conf for my ati driver
but when i restarted 
i could not see the GUI interface after login
so i went for <ctrl><alt><f1> and removed the changes in xorg.conf
i also ran recover
i replaced it also from other running system
but still i m not able to start my GUI interface in ubuntu 8.04


thanx for reply
it will be appreciated

---

### Post by albandy on 2009-02-18
sudo dpkg-reconfigure xserver-xorg
then
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start

---

### Post by shishir_knit on 2009-02-18
sorry but this did not worked

---

### Post by shishir_knit on 2009-02-18
i did not get any result out of it

---

### Post by albandy on 2009-02-18
reboot, select recovery mode in grub and when loaded select xfix

---

### Post by shishir_knit on 2009-02-18
i had tried that also 
it was told by my frnd 
but it also not
worked

---

### Post by shishir_knit on 2009-02-18
i also tried to replace xorg.conf by live cd file
but there was no result

---

### Post by shishir_knit on 2009-02-18
anybody please help me out in this
is there any special configuration in xserver-xorg
after running 
sudo dpkg-reconfigure xserver-xorg

---

### Post by overdrank on 2009-02-18
> **shishir_knit said:**
> anybody please help me out in this
is there any special configuration in xserver-xorg
after running 
sudo dpkg-reconfigure xserver-xorg

Please do not bump your thread so quickly. Did you backup your xorg before modifying it? If so you should be able to replace the backup.
What is the model of the ati card?

---

### Post by shishir_knit on 2009-02-18
no i hav not made backup of that
i just now tried to reinstall my xserver.xorg
but now can't even run the command
dpkg-reconfigure xserver-xorg

it is prompting error
that package is not installed properly

---

