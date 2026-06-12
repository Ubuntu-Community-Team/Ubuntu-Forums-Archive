---
title: "BXA121:stuck on installing ATI grafics card"
date: 2008-02-10
forum: Multimedia &amp; Video
---

### Post by BXA121 on 2008-02-10
Just tried to Instal grafics drivers ATI.
 i used this guide to help me get the right drivers and to set it up right.

[http://wiki.cchtml.com/index.php/Ubu...allation_Guide](http://wiki.cchtml.com/index.php/Ubu...allation_Guide)

also used this , but to a lesser degree [http://ubuntuforums.org/showthread.php?t=515573&page=25](http://ubuntuforums.org/showthread.php?t=515573&page=25)

i enabled the restricted ati driver and i also allowed the universe and multi verse repositories in the software sources program.

i have installed the fglrx driver and it works with my system - however, i am unable to use the 3D effects that ubuntu comes with -it simply says unable to enable - or someit like that.

any ideas on how to fix this?
the drivers installed - it works fine - but 3d effects are not working. and i hope in the future to install beryl on my system.

any help would be great.
__________________

---

### Post by jan quark on 2008-02-10
run this

```
sudo apt-get install xserver-xgl
```

and select xclient session during login

then you should be able to select the advanced effects

---

### Post by BXA121 on 2008-02-10
just tried that. i got this in terminal 


"lXXXXXXXr:~$ sudo apt-get install xserver-xgl
[sudo] password for XXXXXXXr:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xgl is already the newest version.
The following packages were automatically installed and are no longer required:
  gnome-bin libgtk1.2 libglib1.2 libgnome32 kdebase-data gnome-libs-data
  libatk1-ruby1.8 kicker libart2 libgnorbagtk0 gdk-imlib1 pump adept-common
  libkonq4 libept0 libgnomeui32 libxapian15 libdb3 libglib2-ruby1.8 debtags
  libcairo-ruby1.8 libgdk-pixbuf2-ruby1.8 libgtk1.2-common imlib-base xsu
  liborbit0 gdk-imlib11 libgtk2-ruby1.8 libgnomesupport0 libgtk2-ruby libzvt2
  ddccontrol-db libpango1-ruby1.8 libgnorba27
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."
when i restart the system, i get an error - ill find out in a sec..

ok so i cannot login to xserver. 
i can only get into linux through gnome failsafe. any ideas?

---

### Post by BXA121 on 2008-02-10
heres what i got when i try  fglrxinfo

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 PRO
OpenGL version string: 1.4 (2.1.7276 Release)

Segmentation fault (core dumped)

does this help?:confused:

---

### Post by BXA121 on 2008-02-11
Come on guys! 

little help!

---

### Post by Giannis68 on 2008-02-11
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

**Segmentation Fault with glxinfo/fglrxinfo**

 If fglrxinfo or glxinfo returns a Segmentation fault like this: 
 $ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 1.4 (2.1.7170 Release)

Segmentation fault
Set output of libGL to verbose with 
 $ export LIBGL_DEBUG=verbose Run fglrxinfo or glxinfo again 
 libGL: XF86DRIGetClientDriverName: 8.44.3 fglrx (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/fglrx_dri.so
libGL error: dlopen /usr/lib/dri/fglrx_dri.so failed (/usr/lib/dri/fglrx_dri.so: cannot open shared object file: Permission denied)
libGL error: unable to load driver: fglrx_dri.so
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 1.4 (2.1.7170 Release)

Segmentation fault Don't know if its always fglrx_dri.so, but the fix is to add read permissions to the file. 
Check if read permission is not there 
 ls -l /usr/lib/dri/ |grep fglrx_dri
-rw-rw---- 1 root root 17462688 2008-01-13 17:42 fglrx_dri.so
Add read permission 
 $ sudo chmod +r /usr/lib/dri/fglrx_dri.so Check read permission 
 ls -l /usr/lib/dri/ |grep fglrx_dri
-rw-rw-r-- 1 root root 17462688 2008-01-13 17:42 fglrx_dri.so
**[[edit]("http://wiki.cchtml.com/index.php?title=Ubuntu_Gutsy_Installation_Guide&action=edit&section=19")]  libGL error **

 [LIST]
[*] fglrxinfo gives:  libGL.so.1: cannot open shared object file.
[*] Check the permission of the libGL.so.1.2 file with command:[/LIST]  ls -l /usr/lib/libGL*
[LIST]
[*] The file permission of libGL.so.1.2 should be "-rw-rw-r--".  If the permission reads "-rw-rw----", do command[/LIST]  sudo chmod o+r /usr/lib/libGL.so.1.2
[LIST]
[*] If the permission is correct, fixed with command:[/LIST] sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1

---

### Post by BXA121 on 2008-02-11
linuxuser@linuxuser:~$ export LIBGL_DEBUG=verbose

linuxuser@linuxuser:~$ fglrxinfo

libGL: XF86DRIGetClientDriverName: 8.45.4 fglrx (screen 0)
libGL: OpenDriver: trying /usr/X11R6/lib/modules/dri/fglrx_dri.so
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 5, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 5, (OK)
drmOpenByBusid: drmOpenMinor returns 5
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 PRO
OpenGL version string: 2.1.7276 Release

linuxuser@linuxuser:~$ ls -l /usr/lib/dri/ |grep fglrx_dri

-rw-r--r-- 1 root root 15475880 2008-02-10 01:46 fglrx_dri.so

i already added wright ability to the so file. 
and i have finally got the segment error problem sorted out. however. my xml server is STILL not working. 
i still cannot boot into xml. i always have to use failsafe gnome

---

### Post by BXA121 on 2008-02-12
ok so no soloution...


so how do i uninstall xserver?

---

### Post by BXA121 on 2008-02-19
Solved:

i reinstalled ubuntu, i setup my wireless and found this guide: 

really helped!

[http://www.ubuntu1501.com/2007/12/installing-newest-ati-driver.html](http://www.ubuntu1501.com/2007/12/installing-newest-ati-driver.html)

nice novel way to solve this problem!

---

