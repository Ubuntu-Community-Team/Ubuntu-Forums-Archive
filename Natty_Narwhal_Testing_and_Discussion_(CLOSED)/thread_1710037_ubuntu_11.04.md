---
title: "ubuntu 11.04"
date: 2011-03-19
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Heiny on 2011-03-19
Hi all, just testing the 11.04 (natty) and got problems installing printer drivers. printer is Canon MF4370dn. Was working well under previous version but now when trying to install it got this error message opening the drivers with GDebi (Error: Dependency is not satisfiable: cupsys)

don't know what to do.....if any of you got an idea that will be really appreciated.

Thanks, Mike.:confused:

---

### Post by howefield on 2011-03-19
Moved to "*Natty Narwhal Testing and Discussion*"

---

### Post by terry_gardener on 2011-03-19
> **Heiny said:**
> Hi all, just testing the 11.04 (natty) and got problems installing printer drivers. printer is Canon MF4370dn. Was working well under previous version but now when trying to install it got this error message opening the drivers with GDebi (Error: Dependency is not satisfiable: cupsys)

don't know what to do.....if any of you got an idea that will be really appreciated.

Thanks, Mike.:confused:

i had this problem with image scan software from the epson dx4400. 
make sure that you have all the dependencies for the required and them open the terminal and install using dpkg instead 

should be something like "sudo dpkg -i nameofdeb.deb

if there is dependencies issues it will tell you the name of the package needed then just install the required package and then retry.

---

### Post by Heiny on 2011-03-19
Hi, i've tried to reinstall cupsys and i've had to install cupsys-common before. Installed cupsys-common and got the following error:

(reading database...182569 files and directories currently installed.)
Unpaking cupsys-common (from.../home/mike/Downloads/cupsys-common_1.3.7-1ubuntu3.12_all.deb (--install):

trying to overwrite '/usr/share/cups/charsets/utf-8' , wich is also in package cups-common 1.4.6-3
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
/home/mike/Downloads/cupsys-common_1.3.7-1ubuntu3.12_all.deb


i'm still lost....does it mean that i've already have cupsys-common version installed and not compatible with what i'm trying to install?:confused::confused:

Regards, Mike.

---

### Post by mc4man on 2011-03-19
> Unpaking cupsys-common (from.../home/mike/Downloads/cupsys-common_1.3.7-1ubuntu3.12_all.deb (--install): Looking at the package version it seems you're using a cupsys-common from hardy. Don't think that will fly too well in natty

Looking at this post it seems people where getting this to work in maverick by using a lucid version of cupsys
[http://ubuntuforums.org/showthread.php?t=1592487](http://ubuntuforums.org/showthread.php?t=1592487)

Overall don't have any ex. w/ this issue, I'd try to find a natty solution from people who have a similar printer.

---

### Post by Heiny on 2011-03-19
=D>=D> Thank you for the hint!!!

I've followed this link:
install this transitional package: [http://security.ubuntu.com/ubuntu/po...ntu1.2_all.deb](http://security.ubuntu.com/ubuntu/po...ntu1.2_all.deb)

after i've installed: sudo apt-get install gs-esp

and i've installed my drivers for canon and installed the printer.

Works like magic !!!!!!!!

Thank you, you get me out of my nightmare lol!


Regards, Mike.

---

### Post by mathew.chacko on 2011-04-08
I have the same problem with Canon MF 4412 printer. The URL link gives me 404 error. Any idea?

Thanks in advance. Mat.

> **Heiny said:**
> =D>=D> Thank you for the hint!!!

I've followed this link:
install this transitional package: [http://security.ubuntu.com/ubuntu/po...ntu1.2_all.deb](http://security.ubuntu.com/ubuntu/po...ntu1.2_all.deb)

after i've installed: sudo apt-get install gs-esp

and i've installed my drivers for canon and installed the printer.

Works like magic !!!!!!!!

Thank you, you get me out of my nightmare lol!


Regards, Mike.

---

### Post by Heiny on 2011-04-08
Try to install cupsys with this link. sorry the other one is closed...hope this one will work. Let me know!

[http://security.ubuntu.com/ubuntu/pool/universe/c/cups/cupsys_1.4.3-1ubuntu1.3_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/c/cups/cupsys_1.4.3-1ubuntu1.3_all.deb)

---

### Post by mathew.chacko on 2011-04-23
Thanks Heiny. But no success :( cupsys got installed but not the canon common driver. Error "Dependency is not satisfiable: gs-esp"

Cheers, Mat.

> **Heiny said:**
> Try to install cupsys with this link. sorry the other one is closed...hope this one will work. Let me know!

[http://security.ubuntu.com/ubuntu/pool/universe/c/cups/cupsys_1.4.3-1ubuntu1.3_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/c/cups/cupsys_1.4.3-1ubuntu1.3_all.deb)

---

