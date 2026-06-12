---
title: "loooow resolution, cant edit xorg.conf :("
date: 2006-08-10
forum: Multimedia &amp; Video
---

### Post by ccherie on 2006-08-10
hey
my video card is ATI FireGL V5200 P4, I follow the [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually)
to install it. but the best resolution I can choose is 1024x768 :mad: 

I tried:
> sudo dpkg-reconfigure -phigh xserver-xorg
but then got some error:

> xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20060810141844
dexconf: error: cannot generate configuration file;
xserver-xorg/config/write_files_section not set.  Aborting.  Reconfigure the X
server with "dpkg-reconfigure xserver-xorg" to correct this problem.
xserver-xorg postinst warning: error while preparing new Xorg X server
   configuration file in /etc/X11/xorg.conf.dpkg-new; not attempting to
   update existing configuration


I also tried to use 
> gedit /etc/X11/xorg.conf
it also gives the error as:
> Could not save the file /etc/X11/xorg.conf.
You do not have the permissions necessary to save the file. Please, check that you typed the location correctly and try again.


can someone help me solve this resolution problem? and how can i change the  folder/file's permission in ubuntu?
Thanks

---

### Post by DumDum on 2006-08-10
Try

```
sudo gedit /etc/xorg.conf
```

---

### Post by DumDum on 2006-08-10
Sory the correct command is;

```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by ccherie on 2006-08-10
> **DumDum said:**
> Try

```
sudo gedit /etc/xorg.conf
```
Thanks, now I am able to edit/save the Xorg.
But, no matter what solution I add to the Xorg, the best solution is always 1024x768  :(

---

### Post by ccherie on 2006-08-10
following [https://wiki.ubuntu.com/CommonProblemsGraphics?highlight=%28commonproblemsgraphics%29](https://wiki.ubuntu.com/CommonProblemsGraphics?highlight=%28commonproblemsgraphics%29)
now it has higher resolution :D

---

