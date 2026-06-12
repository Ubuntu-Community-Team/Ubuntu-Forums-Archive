---
title: "ndiswrapper error in ubuntu 6.0.6"
date: 2006-07-08
forum: Networking &amp; Wireless
---

### Post by Geeke on 2006-07-08
I have a trendnet TEW-421PC wirelss card and I am trying to get it to work in ubuntu 6.0.6 with ndiswrapper. when I do the following below I get a error message.

geeke19@geeke19-laptop:~$ apt-get install ndiswrapper -utils ndisgtk
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
geeke19@geeke19-laptop:~$


It never asked me to make a root password or username. So how can I fix this so I can install ndiswrapper and get my wireless card to work.

Thanks

Geeke

---

### Post by vest1 on 2006-07-08
First guess is you should try 
$sudo apt-get install ndiswrapper -utils ndisgtk
and then just enter your password.

---

### Post by Geeke on 2006-07-08
I done it and got this message


sh-3.1$ sudo apt-get install ndiswrapper -utils ndisgtk
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ndiswrapper
sh-3.1$


I went to Synaptic Package Manager and it says   ndiswrapper is already installed cause it says  STATUS:INSTALLED.

---

### Post by scameronde on 2006-07-10
Maybe it is a typo?

>> geeke19@geeke19-laptop:~$ apt-get install ndiswrapper -utils ndisgtk

you seem to have a space between 'ndiswrapper' and '-utils'. The package you are looking for is 'ndiswrapper-utils', because 'ndiswrapper' is already installed in Ubuntu 6.06.

The problem with this package is, it is NOT on the Ubuntu CD (at least not on mine). So you have to access the repositories using normal LAN.

Your root password is the password of the first user you added during the installation of Ubuntu. If you have done nothing special, it is the password you use to log into your system.

If you opened a regular shell, you should do a:

>> sudo apt-get install ndiswrapper-utils ndisgtk

sudo then will ask for your password (the 'root' password).

---

### Post by Geeke on 2006-07-10
sh-3.1$ sudo apt-get install ndiswrapper-utils ndisgtk
Password:
Reading package lists... Done
Building dependency tree... Done
ndiswrapper-utils is already the newest version.
E: Couldn't find package ndisgtk


I am getting this info on how to install it from this thread

[http://www.ubuntuforums.org/showthread.php?t=201673&highlight=trendnet](http://www.ubuntuforums.org/showthread.php?t=201673&highlight=trendnet)


Do I just need to go onto step 3?

Thanks

---

### Post by stupidkid on 2006-07-10
Don't use ndisgtk, I've had bad experiences with that program. Just run, 
```

sudo ndiswrapper -i DRIVER.inf
sudo ndiswrapper -l (and you should see: driver present, hardware present)
sudo modprobe ndiswrapper

```

---

### Post by Geeke on 2006-07-11
root@geeke19-laptop:~# sudo ndiswrapper -i mrv8000c.inf
mrv8000c is already installed. Use -e to remove it
root@geeke19-laptop:~# sudo ndiswrapper -i
Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile        Install driver described by 'inffile'
-d devid driver   Use installed 'driver' for 'devid'
-e driver         Remove 'driver'
-l                List installed drivers
-m                Write configuration for modprobe


where 'devid' is either PCIID or USBID of the form XXXX:XXXX
root@geeke19-laptop:~#




I guess I am to stupid to use linux if I cant even get my wireless card to install :( :(

---

### Post by Geeke on 2006-07-16
bump :-k

---

