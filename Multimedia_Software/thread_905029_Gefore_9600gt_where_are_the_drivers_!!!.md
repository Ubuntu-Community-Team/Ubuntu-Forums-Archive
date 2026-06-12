---
title: "Gefore 9600gt where are the drivers ?!??!?!"
date: 2008-08-29
forum: Multimedia Software
---

### Post by circusmonkey on 2008-08-29
why is it Ubuntu 8.04 hardy does not work with geforce 9600 gt cards , no matter what I do nothing works .....envy packages , ubuntu packages Ive tried the lot. 

at the current rate of time I am spending just trying to get ubuntu running I could of bought 1 mac book pro , which actually works out of the box without all the headaches

and now when I go to the package manager I get 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

lol ....... awesome

---

### Post by asenine on 2008-08-29
If you're asking for drivers, just ask for it and don't have a BAWWWWWWWWWfest.

Have you tried

```
sudo apt-get install nvidia-glx-new
```

?

---

### Post by tuxxy on 2008-08-29
```
sudo dpkg --configure -a
```

---

### Post by circusmonkey on 2008-08-29
Nice try, they don't work ....nor does envy. You cannot even uninstall the glx_new without a good ole bug coming up and if you have a duel monitor set up , well thats another whole world of pain 

I find it beggars belief a consumer card sold by the millions cannot work out of the box with ubuntu ....

---

### Post by gruvsyco on 2008-08-30
Weird, I thought the restricted drivers thing was because I was running SLI.  Anyways, I have 2x 9600GT and this is what's worked over several install this last week.

```
sudo apt-get remove envyng-gtk
sudo envy --uninstall-all 
sudo dpkg -P envy 
sudo apt-get remove --purge nvidia*
sudo rm /lib/restricted-modules/.nvidia*
sudo nvidia-installer --uninstall
```

```
sudo apt-get install build-essential
```

[Download the nvidia drivers]("http://www.nvidia.com/object/linux_display_ia32_173.14.12.html") (that's the 32 bit as of today) from their site...  [64bit]("http://www.nvidia.com/object/linux_display_amd64_177.13.html")

In nautilus, right click the file, properties, permissions.  Check allow executing file as a program.  Under Basic, I also renamed the file to nvidia.run... just makes it easier to type in later.

make sure you have the header files and restricted modules for your current kernel installed.

```
sudo gedit /etc/default/linux-restricted-modules-common
```

find the line that says:
DISABLED_MODULES="" and change it to:
DISABLED_MODULES="nv"

save and close.

Close everything.  (Firefox, pidgin, etc.)

ctrl+alt+F1 to get a console and log in.

```
sudo /etc/init.d/gdm stop
```

this will kill your X session

go to where ever you downloaded your driver (default is /home/*username*).  You may already be in that directory.  If you renamed your file like I did above then:

```
sudo ./nvidia.run
```

answer yes to everything that it prompts.

reboot.

---

### Post by REMcCain on 2008-08-30
> **circusmonkey said:**
> 
I find it beggars belief a consumer card sold by the millions cannot work out of the box with ubuntu ....

Looks like Vista isn't the only release with serious issues...

---

