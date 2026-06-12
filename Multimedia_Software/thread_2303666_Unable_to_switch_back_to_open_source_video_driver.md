---
title: "Unable to switch back to open source video driver?"
date: 2015-11-20
forum: Multimedia Software
---

### Post by pandoragami on 2015-11-20
Hello all,

I realize this thread is probably similar to something else but the problem I have is very simple in terms of explanation. Basically I tried to reconfigure my video driver to use the open source x.org 
video driver for an amd/ati card from the AMD Catalyst driver which is closed source. The problem I get to is somehow related to the startup of linux because the driver doesn't seem to load after reboot and
I get a 640x480 resolution instead ( I also cannot go into the System Settings application and change to a higher resolution). I can post whatever else is asked.

Thanks

---

### Post by Bashing-om on 2015-11-20
pandoragami; Sheesshhhh ...

The "Additional Drivers" utility should have performed the task nicely. So, it is terminal time to effect the driver change - and see if there are problems.

What release are you running, and what kernel are you booting ?
Not certain : then show :
```

lsb_release -a
uname -r

```
IF - and the stress here is on IF - you are running a NON-HWE enabled system then this will do the trick.
From the log in screen key combo ctl+alt+F1 will yield a console interface:
execute:
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak ##gets a no-longer needed file out of the way
sudo apt-get purge fglrx fglrx-amdcccle fglrx-updates fglrx-amdcccle-updates ##removes all the proprietary driver files
sudo apt-get install dkms ##cheap insurance - for installing supplementary versions of kernel modules (the driver is a module)
sudo apt-get install xserver-xorg-video-radeon ##the Open Source module it's self
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core ##just to make sure the related libraries and the xserver layer is clean and uncorrupted - the current version
sudo dpkg-reconfigure xserver-xorg ## just that, make the operating system forget the purged 'FGLRX' module, and pick up and use the new module(s) installed (radeon)
sudo update-initramfs -u ##again, cheap insurance, make sure the linux-image is rebuilt with the new libs and modules.

``` This is likely overkill ... but will not hurt a thing to clean all up, make sure the foundations are solid, and the system is happy with the changes.

Else for HWE we will have to redirect Xorg to the proper versions .
Just for your reference and thinking purposes:
```

sysop@1404mini:~$ apt-cache search libgl1-mesa-glx
libgl1-mesa-dev - free implementation of the OpenGL API -- GLX development files
libgl1-mesa-dri - free implementation of the OpenGL API -- DRI modules
libgl1-mesa-dri-dbg - Debugging symbols for the Mesa DRI modules
libgl1-mesa-glx - free implementation of the OpenGL API -- GLX runtime
libgl1-mesa-glx-dbg - Debugging symbols for the Mesa GLX runtime
libgl1-mesa-glx-lts-quantal - Transitional package for libgl1-mesa-glx
libgl1-mesa-glx-lts-quantal-dbg - Transitional package for libgl1-mesa-glx-dbg
libgl1-mesa-glx-lts-raring - Transitional package for libgl1-mesa-glx
libgl1-mesa-glx-lts-raring-dbg - Transitional package for libgl1-mesa-glx-dbg
libgl1-mesa-glx-lts-saucy - Transitional package for libgl1-mesa-glx
libgl1-mesa-glx-lts-saucy-dbg - Transitional package for libgl1-mesa-glx-dbg
libgl1-mesa-dev-lts-utopic - free implementation of the OpenGL API -- GLX development files
libgl1-mesa-dev-lts-vivid - free implementation of the OpenGL API -- GLX development files
libgl1-mesa-dri-lts-utopic - free implementation of the OpenGL API -- DRI modules
libgl1-mesa-dri-lts-utopic-dbg - Debugging symbols for the Mesa DRI modules
libgl1-mesa-dri-lts-vivid - free implementation of the OpenGL API -- DRI modules
libgl1-mesa-dri-lts-vivid-dbg - Debugging symbols for the Mesa DRI modules
libgl1-mesa-glx-lts-trusty - Transitional package for libgl1-mesa-glx
libgl1-mesa-glx-lts-trusty-dbg - Transitional package for libgl1-mesa-glx-dbg
libgl1-mesa-glx-lts-utopic - free implementation of the OpenGL API -- GLX runtime
libgl1-mesa-glx-lts-utopic-dbg - Debugging symbols for the Mesa GLX runtime
libgl1-mesa-glx-lts-vivid - free implementation of the OpenGL API -- GLX runtime
libgl1-mesa-glx-lts-vivid-dbg - Debugging symbols for the Mesa GLX runtime
sysop@1404mini:~

```
As you can see we must match kernels and packages to the correct release .

Reboot and you will be running the open source driver . 

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by pandoragami on 2015-11-20
Ok, I ran the two lines you asked for but not sure which set of code to run since I'm still unsure if this system is HWE or non-HWE. Thanks thus far.


pandoragami@pandoragami-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty
pandoragami@pandoragami-desktop:~$ uname -r
3.19.0-36-generic

---

### Post by Bashing-om on 2015-11-20
pandoragami; OK !

this:
> 
Description: Ubuntu 14.04.3 LTS
3.19.0-36-generic

indicates that you are HWE. so we make adjustments for HWE:
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak ##gets a no-longer needed file out of the way
sudo apt-get purge fglrx fglrx-amdcccle fglrx-updates fglrx-amdcccle-updates ##removes all the proprietary driver files
sudo apt-get install dkms ##cheap insurance - for installing supplementary versions of kernel modules (the driver is a module)
sudo apt-get install xserver-xorg-video-radeon-lts-vivid ##the Open Source module it's self
sudo apt-get install --reinstall libgl1-mesa-glx-lts-vivid libgl1-mesa-dri-lts-vivid xserver-xorg-core-lts-vivid ##just to make sure the related libraries and the xserver layer is clean and uncorrupted - the current version [color=red] here we support HWE [/color]
sudo dpkg-reconfigure xserver-xorg ## just that, make the operating system forget the purged 'FGLRX' module, and pick up and use the new module(s) installed (radeon)
sudo update-initramfs -u ##again, cheap insurance, make sure the linux-image is rebuilt with the new libs and modules.

```

[INDENT][INDENT]fire away
[INDENT][INDENT][INDENT]let's see the effect upon a reboot .
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by pandoragami on 2015-11-20
On this line before the last one I get,
```

 sudo dpkg-reconfigure xserver-xorg
dpkg-query: package 'xserver-xorg' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver-xorg is not installed


```

is this ok. Maybe that's the problem?


Here's the whole output from the terminal
```

pandoragami@pandoragami-desktop:~$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
[sudo] password for pandoragami: 
mv: cannot stat &#8216;/etc/X11/xorg.conf&#8217;: No such file or directory

```
```

pandoragami@pandoragami-desktop:~$ sudo apt-get purge fglrx fglrx-amdcccle fglrx-updates fglrx-amdcccle-updates
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'fglrx' is not installed, so not removed
Package 'fglrx-amdcccle' is not installed, so not removed
The following packages will be REMOVED:
  fglrx-amdcccle-updates* fglrx-updates*
0 upgraded, 0 newly installed, 2 to remove and 6 not upgraded.
After this operation, 182 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 148484 files and directories currently installed.)
Removing fglrx-amdcccle-updates (2:15.200-0ubuntu0.6) ...
Removing fglrx-updates (2:15.200-0ubuntu0.6) ...
update-alternatives: using /usr/lib/pxpress/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link
update-alternatives: using /usr/lib/pxpress/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link
Purging configuration files for fglrx-updates (2:15.200-0ubuntu0.6) ...
dpkg: warning: while removing fglrx-updates, directory '/etc/ati' not empty so not removed
dpkg: warning: while removing fglrx-updates, directory '/usr/lib32/fglrx' not empty so not removed
dpkg: warning: while removing fglrx-updates, directory '/usr/lib/x86_64-linux-gnu/xorg/extra-modules' not empty so not removed
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...

```
```

pandoragami@pandoragami-desktop:~$ sudo apt-get install dkms 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dkms is already the newest version.
dkms set to manually installed.
The following packages were automatically installed and are no longer required:
  fglrx-updates-core lib32gcc1 libc6-i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.

```
```

pandoragami@pandoragami-desktop:~$ sudo apt-get install xserver-xorg-video-radeon-lts-vivid
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-radeon-lts-vivid is already the newest version.
xserver-xorg-video-radeon-lts-vivid set to manually installed.
The following packages were automatically installed and are no longer required:
  fglrx-updates-core lib32gcc1 libc6-i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.

```
```

pandoragami@pandoragami-desktop:~$ sudo apt-get install --reinstall libgl1-mesa-glx-lts-vivid libgl1-mesa-dri-lts-vivid xserver-xorg-core-lts-vivid
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of libgl1-mesa-dri-lts-vivid is not possible, it cannot be downloaded.
Reinstallation of libgl1-mesa-glx-lts-vivid is not possible, it cannot be downloaded.
The following packages were automatically installed and are no longer required:
  fglrx-updates-core lib32gcc1 libc6-i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 6 not upgraded.
Need to get 1,291 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main xserver-xorg-core-lts-vivid amd64 2:1.17.1-0ubuntu3.1~trusty1 [1,291 kB]
Fetched 1,291 kB in 2s (569 kB/s)                        
(Reading database ... 148306 files and directories currently installed.)
Preparing to unpack .../xserver-xorg-core-lts-vivid_2%3a1.17.1-0ubuntu3.1~trusty1_amd64.deb ...
Unpacking xserver-xorg-core-lts-vivid (2:1.17.1-0ubuntu3.1~trusty1) over (2:1.17.1-0ubuntu3.1~trusty1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up xserver-xorg-core-lts-vivid (2:1.17.1-0ubuntu3.1~trusty1) ...

```
```

pandoragami@pandoragami-desktop:~$ sudo dpkg-reconfigure xserver-xorg
dpkg-query: package 'xserver-xorg' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver-xorg is not installed

```

---

### Post by Bashing-om on 2015-11-20
pandoragami; Uh Uh ..

Yeah .. we do have a hitch or 2 - guess why "Additional Drivers" was non-co-operative .

Let see what we can do to fix:
Our hints :
> 
dpkg-query: package 'xserver-xorg' is not installed and no information is available
Reinstallation of libgl1-mesa-dri-lts-vivid is not possible, it cannot be downloaded.
Reinstallation of libgl1-mesa-glx-lts-vivid is not possible, it cannot be downloaded.



xserver-xorg-core-lts-vivid : ##<- It is there and available 

But " libgl1-mesa-dri-lts-vivid" AND " ibgl1-mesa-glx-lts-vivid " are there and available !
per:
> 
sysop@1404mini:~$ apt-cache show xserver-xorg-core-lts-vivid
<snip>
Version: 2:1.17.1-0ubuntu3.1~trusty1
Filename: pool/main/x/xorg-server-lts-vivid/xserver-xorg-core-lts-vivid_1.17.1-0ubuntu3.1~trusty1_amd64.deb
<snip>

sysop@1404mini:~$ apt-cache show libgl1-mesa-dri-lts-vivid
<snip>
Version: 10.5.9-2ubuntu1~trusty2
Filename: pool/main/m/mesa-lts-vivid/libgl1-mesa-dri-lts-vivid_10.5.9-2ubuntu1~trusty2_amd64.deb
<snip>

sysop@1404mini:~$ apt-cache show libgl1-mesa-glx-lts-vivid
<snip>
Version: 10.5.9-2ubuntu1~trusty2
Filename: pool/main/m/mesa-lts-vivid/libgl1-mesa-glx-lts-vivid_10.5.9-2ubuntu1~trusty2_amd64.deb
<snIp>



show us :
```

dpkg -l "xserver-xorg*"
apt-cache search xserver-xorg

dpkg -l libgl1-mesa-dri-lts-vivid
apt-cache show libgl1-mesa-dri-lts-vivid

dpkg -l libgl1-mesa-glx-lts-vivid
apt-cache show libgl1-mesa-glx-lts-vivid

```
Please use code tags - maintains formatting and promotes readability ! Read as much code in a day as we do .. it is important ,
See:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Let's see why the system does not want to cope with them .

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by pandoragami on 2015-11-20
So I'm guessing everything is ok then right. I just need to run that last line of code 

```

sudo update-initramfs -u 
```

and then it's fine,here's the output for what you asked, the second one came in too long.
For  ```

dpkg -l "xserver-xorg*"


pandoragami@pandoragami-desktop:~$ dpkg -l "xserver-xorg*"
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  xserver-xorg   <none>       <none>       (no description available)
un  xserver-xorg-c <none>       <none>       (no description available)
ii  xserver-xorg-c 2:1.17.1-0ub amd64        Xorg X server - core server
un  xserver-xorg-c <none>       <none>       (no description available)
un  xserver-xorg-d <none>       <none>       (no description available)
un  xserver-xorg-d <none>       <none>       (no description available)
un  xserver-xorg-i <none>       <none>       (no description available)
un  xserver-xorg-i <none>       <none>       (no description available)
un  xserver-xorg-i <none>       <none>       (no description available)
un  xserver-xorg-i <none>       <none>       (no description available)
un  xserver-xorg-i <none>       <none>       (no description available)
un  xserver-xorg-i <none>       <none>       (no description available)
ii  xserver-xorg-i 1:7.7+7ubunt amd64        X.Org X server -- input driver me
un  xserver-xorg-i <none>       <none>       (no description available)
ii  xserver-xorg-i 1:2.9.0-1ubu amd64        X.Org X server -- evdev input dri
un  xserver-xorg-i <none>       <none>       (no description available)
un  xserver-xorg-i <none>       <none>       (no description available)
un  xserver-xorg-i <none>       <none>       (no description available)
ii  xserver-xorg-i 1:1.9.1-1~tr amd64        X.Org X server -- mouse input dri
un  xserver-xorg-i <none>       <none>       (no description available)
ii  xserver-xorg-i 1.8.1-1ubunt amd64        Synaptics TouchPad driver for X.O
un  xserver-xorg-i <none>       <none>       (no description available)
un  xserver-xorg-i <none>       <none>       (no description available)
ii  xserver-xorg-i 1:13.0.0-1ub amd64        X.Org X server -- VMMouse input d
un  xserver-xorg-i <none>       <none>       (no description available)
ii  xserver-xorg-i 1:0.25.0-0ub amd64        X.Org X server -- Wacom input dri
ii  xserver-xorg-l 1:7.7+7ubunt amd64        X.Org X server
un  xserver-xorg-r <none>       <none>       (no description available)
un  xserver-xorg-v <none>       <none>       (no description available)
un  xserver-xorg-v <none>       <none>       (no description available)
un  xserver-xorg-v <none>       <none>       (no description available)
un  xserver-xorg-v <none>       <none>       (no description available)
un  xserver-xorg-v <none>       <none>       (no description available)
un  xserver-xorg-v <none>       <none>       (no description available)
un  xserver-xorg-v <none>       <none>       (no description available)
un  xserver-xorg-v <none>       <none>       (no description available)
ii  xserver-xorg-v 1:7.7+7ubunt amd64        X.Org X server -- output driver m
un  xserver-xorg-v <none>       <none>       (no description available)
ii  xserver-xorg-v 1:7.5.0-1ubu amd64        X.Org X server -- AMD/ATI display
un  xserver-xorg-v <none>       <none>       (no description available)
ii  xserver-xorg-v 1:1.5.2-2ubu amd64        X.Org X server -- Cirrus display 
un  xserver-xorg-v <none>       <none>       (no description available)
un  xserver-xorg-v <none>       <none>       (no description available)
ii  xserver-xorg-v 1:0.4.4-1bui amd64        X.Org X server -- fbdev display d
un  xserver-xorg-v <none>       <none>       (no description available)
un  xserver-xorg-v <none>       <none>       (no description available)
un  xserver-xorg-v <none>       <none>       (no description available)
ii  xserver-xorg-v 2:2.99.917-1 amd64        X.Org X server -- Intel i8xx, i9x
un  xserver-xorg-v <none>       <none>       (no description available)
ii  xserver-xorg-v 6.9.4-2ubunt amd64        X.Org X server -- ATI Mach64 disp
un  xserver-xorg-v <none>       <none>       (no description available)
ii  xserver-xorg-v 1:1.6.3-2ubu amd64        X.Org X server -- MGA display dri
un  xserver-xorg-v <none>       <none>       (no description available)
un  xserver-xorg-v <none>       <none>       (no description available)
ii  xserver-xorg-v 1:1.2.8-1ubu amd64        X.Org X server -- Neomagic displa
un  xserver-xorg-v <none>       <none>       (no description available)
ii  xserver-xorg-v 1:1.0.11-1ub amd64        X.Org X server -- Nouveau display
un  xserver-xorg-v <none>       <none>       (no description available)
un  xserver-xorg-v <none>       <none>       (no description available)
ii  xserver-xorg-v 1:0.3.3-1ubu amd64        X.Org X server -- VIA display dri
un  xserver-xorg-v <none>       <none>       (no description available)
ii  xserver-xorg-v 6.9.2-1ubunt amd64        X.Org X server -- ATI r128 displa
un  xserver-xorg-v <none>       <none>       (no description available)
ii  xserver-xorg-v 1:7.5.0-1ubu amd64        X.Org X server -- AMD/ATI Radeon 
un  xserver-xorg-v <none>       <none>       (no description available)
ii  xserver-xorg-v 1:2.3.7-2ubu amd64        X.Org X server -- Savage display 
un  xserver-xorg-v <none>       <none>       (no description available)
ii  xserver-xorg-v 1:1.7.7-2ubu amd64        X.Org X server -- SiliconMotion d
un  xserver-xorg-v <none>       <none>       (no description available)
ii  xserver-xorg-v 1:0.9.6-2bui amd64        X.Org X server -- SiS USB display
un  xserver-xorg-v <none>       <none>       (no description available)
un  xserver-xorg-v <none>       <none>       (no description available)
ii  xserver-xorg-v 1:1.4.6-0ubu amd64        X.Org X server -- tdfx display dr
un  xserver-xorg-v <none>       <none>       (no description available)
ii  xserver-xorg-v 1:1.3.6-0ubu amd64        X.Org X server -- Trident display
un  xserver-xorg-v <none>       <none>       (no description available)
un  xserver-xorg-v <none>       <none>       (no description available)
ii  xserver-xorg-v 1:2.3.3-1bui amd64        X.Org X server -- VESA display dr
un  xserver-xorg-v <none>       <none>       (no description available)
un  xserver-xorg-v <none>       <none>       (no description available)
ii  xserver-xorg-v 1:13.1.0-0ub amd64        X.Org X server -- VMware display 



```

for 
apt-cache search xserver-xorg

```


eo-dummy
xserver-xorg-video-dummy-lts-raring - Transitional package for xserver-xorg-video-dummy
xserver-xorg-video-dummy-lts-saucy - Transitional package for xserver-xorg-video-dummy
xserver-xorg-video-fbdev - X.Org X server -- fbdev display driver
xserver-xorg-video-fbdev-lts-quantal - Transitional package for xserver-xorg-video-fbdev
xserver-xorg-video-fbdev-lts-raring - Transitional package for xserver-xorg-video-fbdev
xserver-xorg-video-fbdev-lts-saucy - Transitional package for xserver-xorg-video-fbdev
xserver-xorg-video-glamoregl - X.Org X server -- graphics acceleration module based on OpenGL
xserver-xorg-video-intel - X.Org X server -- Intel i8xx, i9xx display driver
xserver-xorg-video-intel-dbg - X.Org X server -- Intel i8xx, i9xx display driver (debug symbols)
xserver-xorg-video-intel-lts-quantal - Transitional package for xserver-xorg-video-intel
xserver-xorg-video-intel-lts-quantal-dbg - Transitional package for xserver-xorg-video-intel-dbg
xserver-xorg-video-intel-lts-raring - Transitional package for xserver-xorg-video-intel
xserver-xorg-video-intel-lts-raring-dbg - Transitional package for xserver-xorg-video-intel-dbg
xserver-xorg-video-intel-lts-saucy - Transitional package for xserver-xorg-video-intel
xserver-xorg-video-intel-lts-saucy-dbg - Transitional package for xserver-xorg-video-intel-dbg
xserver-xorg-video-mach64 - X.Org X server -- ATI Mach64 display driver
xserver-xorg-video-mach64-dbg - X.Org X server -- ATI display driver (debugging symbols)
xserver-xorg-video-mach64-lts-quantal - Transitional package for xserver-xorg-video-mach64
xserver-xorg-video-mach64-lts-quantal-dbg - Transitional package for xserver-xorg-video-mach64-dbg
xserver-xorg-video-mach64-lts-raring - Transitional package for xserver-xorg-video-mach64
xserver-xorg-video-mach64-lts-raring-dbg - Transitional package for xserver-xorg-video-mach64-dbg
xserver-xorg-video-mach64-lts-saucy - Transitional package for xserver-xorg-video-mach64
xserver-xorg-video-mach64-lts-saucy-dbg - Transitional package for xserver-xorg-video-mach64-dbg
xserver-xorg-video-mga - X.Org X server -- MGA display driver
xserver-xorg-video-mga-lts-quantal - Transitional package for xserver-xorg-video-mga
xserver-xorg-video-mga-lts-raring - Transitional package for xserver-xorg-video-mga
xserver-xorg-video-mga-lts-saucy - Transitional package for xserver-xorg-video-mga
xserver-xorg-video-modesetting - X.Org X server -- Generic modesetting driver
xserver-xorg-video-modesetting-dbg - X.Org X server -- Generic modesetting driver (debug symbols)
xserver-xorg-video-modesetting-lts-quantal - Transitional package for xserver-xorg-video-modesetting
xserver-xorg-video-modesetting-lts-quantal-dbg - Transitional package for xserver-xorg-video-modesetting-dbg
xserver-xorg-video-modesetting-lts-raring - Transitional package for xserver-xorg-video-modesetting
xserver-xorg-video-modesetting-lts-raring-dbg - Transitional package for xserver-xorg-video-modesetting-dbg
xserver-xorg-video-modesetting-lts-saucy - Transitional package for xserver-xorg-video-modesetting
xserver-xorg-video-modesetting-lts-saucy-dbg - Transitional package for xserver-xorg-video-modesetting-dbg
xserver-xorg-video-neomagic - X.Org X server -- Neomagic display driver
xserver-xorg-video-neomagic-lts-quantal - Transitional package for xserver-xorg-video-neomagic
xserver-xorg-video-neomagic-lts-raring - Transitional package for xserver-xorg-video-neomagic
xserver-xorg-video-neomagic-lts-saucy - Transitional package for xserver-xorg-video-neomagic
xserver-xorg-video-nouveau - X.Org X server -- Nouveau display driver
xserver-xorg-video-nouveau-dbg - X.Org X server -- Nouveau display driver (debug symbols)
xserver-xorg-video-nouveau-lts-quantal - Transitional package for xserver-xorg-video-nouveau
xserver-xorg-video-nouveau-lts-quantal-dbg - Transitional package for xserver-xorg-video-nouveau-dbg
xserver-xorg-video-nouveau-lts-raring - Transitional package for xserver-xorg-video-nouveau
xserver-xorg-video-nouveau-lts-raring-dbg - Transitional package for xserver-xorg-video-nouveau-dbg
xserver-xorg-video-nouveau-lts-saucy - Transitional package for xserver-xorg-video-nouveau
xserver-xorg-video-nouveau-lts-saucy-dbg - Transitional package for xserver-xorg-video-nouveau-dbg
xserver-xorg-video-openchrome - X.Org X server -- VIA display driver
xserver-xorg-video-openchrome-dbg - X.Org X server -- VIA display driver -- debugging symbols
xserver-xorg-video-openchrome-lts-quantal - Transitional package for xserver-xorg-video-openchrome
xserver-xorg-video-openchrome-lts-quantal-dbg - Transitional package for xserver-xorg-video-openchrome-dbg
xserver-xorg-video-openchrome-lts-raring - Transitional package for xserver-xorg-video-openchrome
xserver-xorg-video-openchrome-lts-raring-dbg - Transitional package for xserver-xorg-video-openchrome-dbg
xserver-xorg-video-openchrome-lts-saucy - Transitional package for xserver-xorg-video-openchrome
xserver-xorg-video-openchrome-lts-saucy-dbg - Transitional package for xserver-xorg-video-openchrome-dbg
xserver-xorg-video-qxl - X.Org X server -- QXL display driver
xserver-xorg-video-qxl-dbg - X.Org X server -- QXL display driver (debugging symbols)
xserver-xorg-video-r128 - X.Org X server -- ATI r128 display driver
xserver-xorg-video-r128-dbg - X.Org X server -- ATI r128 display driver (debugging symbols)
xserver-xorg-video-r128-lts-quantal - Transitional package for xserver-xorg-video-r128
xserver-xorg-video-r128-lts-quantal-dbg - Transitional package for xserver-xorg-video-r128-dbg
xserver-xorg-video-r128-lts-raring - Transitional package for xserver-xorg-video-r128
xserver-xorg-video-r128-lts-raring-dbg - Transitional package for xserver-xorg-video-r128-dbg
xserver-xorg-video-r128-lts-saucy - Transitional package for xserver-xorg-video-r128
xserver-xorg-video-r128-lts-saucy-dbg - Transitional package for xserver-xorg-video-r128-dbg
xserver-xorg-video-radeon - X.Org X server -- AMD/ATI Radeon display driver
xserver-xorg-video-radeon-dbg - X.Org X server -- AMD/ATI Radeon display driver (debugging symbols)
xserver-xorg-video-radeon-lts-quantal - Transitional package for xserver-xorg-video-radeon
xserver-xorg-video-radeon-lts-quantal-dbg - Transitional package for xserver-xorg-video-radeon-dbg
xserver-xorg-video-radeon-lts-raring - Transitional package for xserver-xorg-video-radeon
xserver-xorg-video-radeon-lts-raring-dbg - Transitional package for xserver-xorg-video-radeon-dbg
xserver-xorg-video-radeon-lts-saucy - Transitional package for xserver-xorg-video-radeon
xserver-xorg-video-radeon-lts-saucy-dbg - Transitional package for xserver-xorg-video-radeon-dbg
xserver-xorg-video-s3 - X.Org X server -- legacy S3 display driver
xserver-xorg-video-s3-lts-quantal - Transitional package for xserver-xorg-video-s3
xserver-xorg-video-s3-lts-raring - Transitional package for xserver-xorg-video-s3
xserver-xorg-video-s3-lts-saucy - Transitional package for xserver-xorg-video-s3
xserver-xorg-video-savage - X.Org X server -- Savage display driver
xserver-xorg-video-savage-lts-quantal - Transitional package for xserver-xorg-video-savage
xserver-xorg-video-savage-lts-raring - Transitional package for xserver-xorg-video-savage
xserver-xorg-video-savage-lts-saucy - Transitional package for xserver-xorg-video-savage
xserver-xorg-video-siliconmotion - X.Org X server -- SiliconMotion display driver
xserver-xorg-video-siliconmotion-lts-quantal - Transitional package for xserver-xorg-video-siliconmotion
xserver-xorg-video-siliconmotion-lts-raring - Transitional package for xserver-xorg-video-siliconmotion
xserver-xorg-video-siliconmotion-lts-saucy - Transitional package for xserver-xorg-video-siliconmotion
xserver-xorg-video-sis - X.Org X server -- SiS display driver
xserver-xorg-video-sis-lts-quantal - Transitional package for xserver-xorg-video-sis
xserver-xorg-video-sis-lts-raring - Transitional package for xserver-xorg-video-sis
xserver-xorg-video-sis-lts-saucy - Transitional package for xserver-xorg-video-sis
xserver-xorg-video-sisusb - X.Org X server -- SiS USB display driver
xserver-xorg-video-sisusb-lts-quantal - Transitional package for xserver-xorg-video-sisusb
xserver-xorg-video-sisusb-lts-raring - Transitional package for xserver-xorg-video-sisusb
xserver-xorg-video-sisusb-lts-saucy - Transitional package for xserver-xorg-video-sisusb
xserver-xorg-video-tdfx - X.Org X server -- tdfx display driver
xserver-xorg-video-tdfx-lts-quantal - Transitional package for xserver-xorg-video-tdfx
xserver-xorg-video-tdfx-lts-raring - Transitional package for xserver-xorg-video-tdfx
xserver-xorg-video-tdfx-lts-saucy - Transitional package for xserver-xorg-video-tdfx
xserver-xorg-video-trident - X.Org X server -- Trident display driver
xserver-xorg-video-trident-lts-quantal - Transitional package for xserver-xorg-video-trident
xserver-xorg-video-trident-lts-raring - Transitional package for xserver-xorg-video-trident
xserver-xorg-video-trident-lts-saucy - Transitional package for xserver-xorg-video-trident
xserver-xorg-video-vesa - X.Org X server -- VESA display driver
xserver-xorg-video-vesa-lts-quantal - Transitional package for xserver-xorg-video-vesa
xserver-xorg-video-vesa-lts-raring - Transitional package for xserver-xorg-video-vesa
xserver-xorg-video-vesa-lts-saucy - Transitional package for xserver-xorg-video-vesa
xserver-xorg-video-vmware - X.Org X server -- VMware display driver
xserver-xorg-video-vmware-lts-quantal - Transitional package for xserver-xorg-video-vmware
xserver-xorg-video-vmware-lts-raring - Transitional package for xserver-xorg-video-vmware
xserver-xorg-video-vmware-lts-saucy - Transitional package for xserver-xorg-video-vmware
xorg-server-source - Xorg X server - source files
xserver-xorg-input-acecad - X.Org X server -- AceCad input driver
xserver-xorg-input-aiptek - X.Org X server -- Aiptek input driver
xserver-xorg-input-elographics - X.Org X server -- ELOGraphics input driver
xserver-xorg-input-joystick - X.Org X server -- joystick input driver
xserver-xorg-input-joystick-dev - X.Org X server -- joystick input driver (development headers)
xserver-xorg-input-joystick-dev-lts-quantal - Transitional package for xserver-xorg-input-joystick-dev
xserver-xorg-input-joystick-dev-lts-raring - Transitional package for xserver-xorg-input-joystick-dev
xserver-xorg-input-joystick-dev-lts-saucy - Transitional package for xserver-xorg-input-joystick-dev
xserver-xorg-input-joystick-lts-quantal - Transitional package for xserver-xorg-input-joystick
xserver-xorg-input-joystick-lts-raring - Transitional package for xserver-xorg-input-joystick
xserver-xorg-input-joystick-lts-saucy - Transitional package for xserver-xorg-input-joystick
xserver-xorg-input-kbd - X.Org X server -- keyboard input driver
xserver-xorg-input-kbd-lts-quantal - Transitional package for xserver-xorg-input-kbd
xserver-xorg-input-kbd-lts-raring - Transitional package for xserver-xorg-input-kbd
xserver-xorg-input-kbd-lts-saucy - Transitional package for xserver-xorg-input-kbd
xserver-xorg-input-mtrack - Multitouch X input driver
xserver-xorg-input-mtrack-lts-quantal - Transitional package for xserver-xorg-input-mtrack
xserver-xorg-input-mtrack-lts-raring - Transitional package for xserver-xorg-input-mtrack
xserver-xorg-input-mtrack-lts-saucy - Transitional package for xserver-xorg-input-mtrack
xserver-xorg-input-multitouch - Multitouch X input driver
xserver-xorg-input-mutouch - X.Org X server -- muTouch input driver
xserver-xorg-xmir - Xorg - the X.Org X server (module for running nested in Mir)
xserver-xorg-video-geode - X.Org X server -- Geode GX2/LX display driver
xserver-xorg-video-geode-dbg - Geode GX2/LX display driver (debugging symbols)
xserver-xorg-video-geode-lts-quantal - Transitional package for xserver-xorg-video-geode
xserver-xorg-video-geode-lts-raring - Transitional package for xserver-xorg-video-geode
xserver-xorg-video-geode-lts-saucy - Transitional package for xserver-xorg-video-geode
xserver-xorg-core-lts-trusty - Transitional package for xserver-xorg-core
xserver-xorg-core-lts-trusty-dbg - Transitional package for xserver-xorg-core-dbg
xserver-xorg-core-lts-utopic - Xorg X server - core server
xserver-xorg-core-lts-utopic-dbg - Xorg - the X.Org X server (debugging symbols)
xserver-xorg-core-lts-vivid - Xorg X server - core server
xserver-xorg-core-lts-vivid-dbg - Xorg - the X.Org X server (debugging symbols)
xserver-xorg-dev-lts-trusty - Transitional package for xserver-xorg-dev
xserver-xorg-dev-lts-utopic - Xorg X server - development files
xserver-xorg-dev-lts-vivid - Xorg X server - development files
xserver-xorg-input-all-lts-trusty - Transitional package for xserver-xorg-input-all
xserver-xorg-input-all-lts-utopic - X.Org X server -- input driver metapackage
xserver-xorg-input-all-lts-vivid - X.Org X server -- input driver metapackage
xserver-xorg-input-evdev-dev-lts-trusty - Transitional package for xserver-xorg-input-evdev-dev
xserver-xorg-input-evdev-dev-lts-utopic - X.Org X server -- evdev input driver (development headers)
xserver-xorg-input-evdev-dev-lts-vivid - X.Org X server -- evdev input driver (development headers)
xserver-xorg-input-evdev-lts-trusty - Transitional package for xserver-xorg-input-evdev
xserver-xorg-input-evdev-lts-trusty-dbg - Transitional package for xserver-xorg-input-evdev-dbg
xserver-xorg-input-evdev-lts-utopic - X.Org X server -- evdev input driver
xserver-xorg-input-evdev-lts-utopic-dbg - X.Org X server -- evdev input driver (development headers)
xserver-xorg-input-evdev-lts-vivid - X.Org X server -- evdev input driver
xserver-xorg-input-evdev-lts-vivid-dbg - X.Org X server -- evdev input driver (development headers)
xserver-xorg-input-joystick-dev-lts-trusty - Transitional package for xserver-xorg-input-joystick-dev
xserver-xorg-input-joystick-lts-trusty - Transitional package for xserver-xorg-input-joystick
xserver-xorg-input-kbd-lts-trusty - Transitional package for xserver-xorg-input-kbd
xserver-xorg-input-mouse-lts-trusty - Transitional package for xserver-xorg-input-mouse
xserver-xorg-input-mouse-lts-utopic - X.Org X server -- mouse input driver
xserver-xorg-input-mouse-lts-vivid - X.Org X server -- mouse input driver
xserver-xorg-input-mtrack-lts-trusty - Transitional package for xserver-xorg-input-mtrack
xserver-xorg-input-synaptics-dev-lts-trusty - Transitional package for xserver-xorg-input-synaptics-dev
xserver-xorg-input-synaptics-dev-lts-utopic - Synaptics TouchPad driver for X.Org server (development headers)
xserver-xorg-input-synaptics-dev-lts-vivid - Synaptics TouchPad driver for X.Org server (development headers)
xserver-xorg-input-synaptics-lts-trusty - Transitional package for xserver-xorg-input-synaptics
xserver-xorg-input-synaptics-lts-trusty-dbg - Transitional package for xserver-xorg-input-synaptics-dbg
xserver-xorg-input-synaptics-lts-utopic - Synaptics TouchPad driver for X.Org server
xserver-xorg-input-synaptics-lts-utopic-dbg - Synaptics TouchPad driver for X.Org server
xserver-xorg-input-synaptics-lts-vivid - Synaptics TouchPad driver for X.Org server
xserver-xorg-input-synaptics-lts-vivid-dbg - Synaptics TouchPad driver for X.Org server
xserver-xorg-input-vmmouse-lts-trusty - Transitional package for xserver-xorg-input-vmmouse
xserver-xorg-input-vmmouse-lts-utopic - X.Org X server -- VMMouse input driver to use with VMWare
xserver-xorg-input-vmmouse-lts-vivid - X.Org X server -- VMMouse input driver to use with VMWare
xserver-xorg-input-void-lts-trusty - Transitional package for xserver-xorg-input-void
xserver-xorg-input-wacom-lts-trusty - Transitional package for xserver-xorg-input-wacom
xserver-xorg-input-wacom-lts-trusty-dbg - Transitional package for xserver-xorg-input-wacom-dbg
xserver-xorg-input-wacom-lts-utopic - X.Org X server -- Wacom input driver
xserver-xorg-input-wacom-lts-utopic-dbg - X.Org X server -- Wacom input driver
xserver-xorg-input-wacom-lts-vivid - X.Org X server -- Wacom input driver
xserver-xorg-input-wacom-lts-vivid-dbg - X.Org X server -- Wacom input driver
xserver-xorg-lts-precise - Transitional package for xserver-xorg
xserver-xorg-lts-trusty - Transitional package for xserver-xorg
xserver-xorg-lts-utopic - X.Org X server
xserver-xorg-lts-vivid - X.Org X server
xserver-xorg-video-all-lts-trusty - Transitional package for xserver-xorg-video-all
xserver-xorg-video-all-lts-utopic - X.Org X server -- output driver metapackage
xserver-xorg-video-all-lts-vivid - X.Org X server -- output driver metapackage
xserver-xorg-video-ati-lts-trusty - Transitional package for xserver-xorg-video-ati
xserver-xorg-video-ati-lts-trusty-dbg - Transitional package for xserver-xorg-video-ati-dbg
xserver-xorg-video-ati-lts-utopic - X.Org X server -- AMD/ATI display driver wrapper
xserver-xorg-video-ati-lts-utopic-dbg - X.Org X server -- AMD/ATI display driver wrapper (debugging symbols)
xserver-xorg-video-ati-lts-vivid - X.Org X server -- AMD/ATI display driver wrapper
xserver-xorg-video-ati-lts-vivid-dbg - X.Org X server -- AMD/ATI display driver wrapper (debugging symbols)
xserver-xorg-video-cirrus-lts-trusty - Transitional package for xserver-xorg-video-cirrus
xserver-xorg-video-cirrus-lts-utopic - X.Org X server -- Cirrus display driver
xserver-xorg-video-cirrus-lts-vivid - X.Org X server -- Cirrus display driver
xserver-xorg-video-dummy-lts-trusty - Transitional package for xserver-xorg-video-dummy
xserver-xorg-video-dummy-lts-utopic - X.Org X server -- dummy display driver
xserver-xorg-video-dummy-lts-vivid - X.Org X server -- dummy display driver
xserver-xorg-video-fbdev-lts-trusty - Transitional package for xserver-xorg-video-fbdev
xserver-xorg-video-fbdev-lts-utopic - X.Org X server -- fbdev display driver
xserver-xorg-video-fbdev-lts-vivid - X.Org X server -- fbdev display driver
xserver-xorg-video-glamoregl-lts-trusty - Transitional package for xserver-xorg-video-glamoregl
xserver-xorg-video-intel-lts-trusty - Transitional package for xserver-xorg-video-intel
xserver-xorg-video-intel-lts-trusty-dbg - Transitional package for xserver-xorg-video-intel-dbg
xserver-xorg-video-intel-lts-utopic - X.Org X server -- Intel i8xx, i9xx display driver
xserver-xorg-video-intel-lts-utopic-dbg - X.Org X server -- Intel i8xx, i9xx display driver (debug symbols)
xserver-xorg-video-intel-lts-vivid - X.Org X server -- Intel i8xx, i9xx display driver
xserver-xorg-video-intel-lts-vivid-dbg - X.Org X server -- Intel i8xx, i9xx display driver (debug symbols)
xserver-xorg-video-mach64-lts-trusty - Transitional package for xserver-xorg-video-mach64
xserver-xorg-video-mach64-lts-trusty-dbg - Transitional package for xserver-xorg-video-mach64-dbg
xserver-xorg-video-mach64-lts-utopic - X.Org X server -- ATI Mach64 display driver
xserver-xorg-video-mach64-lts-utopic-dbg - X.Org X server -- ATI display driver (debugging symbols)
xserver-xorg-video-mach64-lts-vivid - X.Org X server -- ATI Mach64 display driver
xserver-xorg-video-mach64-lts-vivid-dbg - X.Org X server -- ATI display driver (debugging symbols)
xserver-xorg-video-mga-lts-trusty - Transitional package for xserver-xorg-video-mga
xserver-xorg-video-mga-lts-utopic - X.Org X server -- MGA display driver
xserver-xorg-video-mga-lts-vivid - X.Org X server -- MGA display driver
xserver-xorg-video-modesetting-lts-trusty - Transitional package for xserver-xorg-video-modesetting
xserver-xorg-video-modesetting-lts-trusty-dbg - Transitional package for xserver-xorg-video-modesetting-dbg
xserver-xorg-video-modesetting-lts-utopic - X.Org X server -- Generic modesetting driver
xserver-xorg-video-modesetting-lts-utopic-dbg - X.Org X server -- Generic modesetting driver (debug symbols)
xserver-xorg-video-neomagic-lts-trusty - Transitional package for xserver-xorg-video-neomagic
xserver-xorg-video-neomagic-lts-utopic - X.Org X server -- Neomagic display driver
xserver-xorg-video-neomagic-lts-vivid - X.Org X server -- Neomagic display driver
xserver-xorg-video-nouveau-lts-trusty - Transitional package for xserver-xorg-video-nouveau
xserver-xorg-video-nouveau-lts-trusty-dbg - Transitional package for xserver-xorg-video-nouveau-dbg
xserver-xorg-video-nouveau-lts-utopic - X.Org X server -- Nouveau display driver
xserver-xorg-video-nouveau-lts-utopic-dbg - X.Org X server -- Nouveau display driver (debug symbols)
xserver-xorg-video-nouveau-lts-vivid - X.Org X server -- Nouveau display driver
xserver-xorg-video-nouveau-lts-vivid-dbg - X.Org X server -- Nouveau display driver (debug symbols)
xserver-xorg-video-openchrome-lts-trusty - Transitional package for xserver-xorg-video-openchrome
xserver-xorg-video-openchrome-lts-trusty-dbg - Transitional package for xserver-xorg-video-openchrome-dbg
xserver-xorg-video-openchrome-lts-utopic - X.Org X server -- VIA display driver
xserver-xorg-video-openchrome-lts-utopic-dbg - X.Org X server -- VIA display driver -- debugging symbols
xserver-xorg-video-openchrome-lts-vivid - X.Org X server -- VIA display driver
xserver-xorg-video-openchrome-lts-vivid-dbg - X.Org X server -- VIA display driver -- debugging symbols
xserver-xorg-video-qxl-lts-utopic - X.Org X server -- QXL display driver
xserver-xorg-video-qxl-lts-utopic-dbg - X.Org X server -- QXL display driver (debugging symbols)
xserver-xorg-video-qxl-lts-vivid - X.Org X server -- QXL display driver
xserver-xorg-video-qxl-lts-vivid-dbg - X.Org X server -- QXL display driver (debugging symbols)
xserver-xorg-video-r128-lts-trusty - Transitional package for xserver-xorg-video-r128
xserver-xorg-video-r128-lts-trusty-dbg - Transitional package for xserver-xorg-video-r128-dbg
xserver-xorg-video-r128-lts-utopic - X.Org X server -- ATI r128 display driver
xserver-xorg-video-r128-lts-utopic-dbg - X.Org X server -- ATI r128 display driver (debugging symbols)
xserver-xorg-video-r128-lts-vivid - X.Org X server -- ATI r128 display driver
xserver-xorg-video-r128-lts-vivid-dbg - X.Org X server -- ATI r128 display driver (debugging symbols)
xserver-xorg-video-radeon-lts-trusty - Transitional package for xserver-xorg-video-radeon
xserver-xorg-video-radeon-lts-trusty-dbg - Transitional package for xserver-xorg-video-radeon-dbg
xserver-xorg-video-radeon-lts-utopic - X.Org X server -- AMD/ATI Radeon display driver
xserver-xorg-video-radeon-lts-utopic-dbg - X.Org X server -- AMD/ATI Radeon display driver (debugging symbols)
xserver-xorg-video-radeon-lts-vivid - X.Org X server -- AMD/ATI Radeon display driver
xserver-xorg-video-radeon-lts-vivid-dbg - X.Org X server -- AMD/ATI Radeon display driver (debugging symbols)
xserver-xorg-video-s3-lts-trusty - Transitional package for xserver-xorg-video-s3
xserver-xorg-video-savage-lts-trusty - Transitional package for xserver-xorg-video-savage
xserver-xorg-video-savage-lts-utopic - X.Org X server -- Savage display driver
xserver-xorg-video-savage-lts-vivid - X.Org X server -- Savage display driver
xserver-xorg-video-siliconmotion-lts-trusty - Transitional package for xserver-xorg-video-siliconmotion
xserver-xorg-video-siliconmotion-lts-utopic - X.Org X server -- SiliconMotion display driver
xserver-xorg-video-siliconmotion-lts-vivid - X.Org X server -- SiliconMotion display driver
xserver-xorg-video-sis-lts-trusty - Transitional package for xserver-xorg-video-sis
xserver-xorg-video-sisusb-lts-trusty - Transitional package for xserver-xorg-video-sisusb
xserver-xorg-video-sisusb-lts-utopic - X.Org X server -- SiS USB display driver
xserver-xorg-video-sisusb-lts-vivid - X.Org X server -- SiS USB display driver
xserver-xorg-video-tdfx-lts-trusty - Transitional package for xserver-xorg-video-tdfx
xserver-xorg-video-tdfx-lts-utopic - X.Org X server -- tdfx display driver
xserver-xorg-video-tdfx-lts-vivid - X.Org X server -- tdfx display driver
xserver-xorg-video-trident-lts-trusty - Transitional package for xserver-xorg-video-trident
xserver-xorg-video-trident-lts-utopic - X.Org X server -- Trident display driver
xserver-xorg-video-trident-lts-vivid - X.Org X server -- Trident display driver
xserver-xorg-video-vesa-lts-trusty - Transitional package for xserver-xorg-video-vesa
xserver-xorg-video-vesa-lts-utopic - X.Org X server -- VESA display driver
xserver-xorg-video-vesa-lts-vivid - X.Org X server -- VESA display driver
xserver-xorg-video-vmware-lts-trusty - Transitional package for xserver-xorg-video-vmware
xserver-xorg-video-vmware-lts-utopic - X.Org X server -- VMware display driver
xserver-xorg-video-vmware-lts-vivid - X.Org X server -- VMware display driver
xserver-xorg-video-geode-lts-quantal-dbg - Transitional package for xserver-xorg-video-geode-dbg
xserver-xorg-video-geode-lts-raring-dbg - Transitional package for xserver-xorg-video-geode-dbg
xserver-xorg-video-geode-lts-saucy-dbg - Transitional package for xserver-xorg-video-geode-dbg
xserver-xorg-video-geode-lts-trusty - Transitional package for xserver-xorg-video-geode
xserver-xorg-video-geode-lts-trusty-dbg - Transitional package for xserver-xorg-video-geode-dbg
xorg-server-source-lts-utopic - Xorg X server - source files
xorg-server-source-lts-vivid - Xorg X server - source files
xserver-xorg-input-joystick-dev-lts-utopic - X.Org X server -- joystick input driver (development headers)
xserver-xorg-input-joystick-dev-lts-vivid - X.Org X server -- joystick input driver (development headers)
xserver-xorg-input-joystick-lts-utopic - X.Org X server -- joystick input driver
xserver-xorg-input-joystick-lts-vivid - X.Org X server -- joystick input driver
xserver-xorg-input-kbd-lts-utopic - X.Org X server -- keyboard input driver
xserver-xorg-input-kbd-lts-vivid - X.Org X server -- keyboard input driver
xserver-xorg-input-mtrack-lts-utopic - Multitouch X input driver
xserver-xorg-input-mtrack-lts-vivid - Multitouch X input driver
xserver-xorg-input-void-lts-utopic - X.Org X server -- void input driver
xserver-xorg-input-void-lts-vivid - X.Org X server -- void input driver
xserver-xorg-video-s3-lts-utopic - X.Org X server -- legacy S3 display driver
xserver-xorg-video-s3-lts-vivid - X.Org X server -- legacy S3 display driver
xserver-xorg-video-geode-lts-utopic - X.Org X server -- Geode GX2/LX display driver
xserver-xorg-video-geode-lts-utopic-dbg - Geode GX2/LX display driver (debugging symbols)
xserver-xorg-video-geode-lts-vivid - X.Org X server -- Geode GX2/LX display driver
xserver-xorg-video-geode-lts-vivid-dbg - Geode GX2/LX display driver (debugging symbols)
pandoragami@pandoragami-desktop:~$ 

```



for 
dpkg -l libgl1-mesa-dri-lts-vivid

```
pandoragami@pandoragami-desktop:~$ dpkg -l libgl1-mesa-dri-lts-vivid
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  libgl1-mesa-dr 10.5.9-2ubun amd64        free implementation of the OpenGL
pandoragami@pandoragami-desktop:~$
```


 
for 
apt-cache show libgl1-mesa-dri-lts-vivid

```

pandoragami@pandoragami-desktop:~$ apt-cache show libgl1-mesa-dri-lts-vivid
Package: libgl1-mesa-dri-lts-vivid
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 13603
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: amd64
Multi-Arch: same
Source: mesa-lts-vivid
Version: 10.5.9-2ubuntu1~trusty3
Replaces: libgl1-mesa-dri, libgl1-mesa-dri-experimental (<< 7.11.1), xlibmesa-dri (<< 1:7.0.0)
Provides: libgl1-mesa-dri, xorg-renamed-package, xorg-renamed-package-lts-vivid
Depends: libc6 (>= 2.17), libdrm-intel1 (>= 2.4.48), libdrm-nouveau2 (>= 2.4.38), libdrm-radeon1 (>= 2.4.31), libdrm2 (>= 2.4.38), libelf1 (>= 0.142), libexpat1 (>= 2.0.1), libgcc1 (>= 1:4.1.1), libllvm3.6, libstdc++6 (>= 4.6)
Pre-Depends: multiarch-support
Recommends: libtxc-dxtn-s2tc0 | libtxc-dxtn0
Breaks: libgl1-mesa-dri-experimental (<< 7.11.1), libgl1-mesa-glx-lts-vivid (<< 7.10.2-4), libgl1-mesa-glx-no-multiarch, xserver-xorg-core-lts-vivid (<< 2:1.14.3-5), xserver-xorg-core-no-multiarch
Conflicts: libgl1-mesa-dri, xlibmesa-dri (<< 1:7.0.0), xorg-renamed-package-lts-utopic
Conffiles:
 /etc/drirc 270076ee56f99c23978c677ca1ac71e4
Description-en: free implementation of the OpenGL API -- DRI modules
 This version of Mesa provides GLX and DRI capabilities: it is capable of
 both direct and indirect rendering.  For direct rendering, it can use DRI
 modules from the libgl1-mesa-dri package to accelerate drawing.
 .
 This package does not include the OpenGL library itself, only the DRI
 modules for accelerating direct rendering.
 .
 For a complete description of Mesa, please look at the
 libgl1-mesa-glx package.
Description-md5: 5f2b652ffc2f2781c936450c0c51bcc7
Homepage: http://mesa3d.sourceforge.net/
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>

Package: libgl1-mesa-dri-lts-vivid
Priority: optional
Section: libs
Installed-Size: 13603
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Architecture: amd64
Source: mesa-lts-vivid
Version: 10.5.9-2ubuntu1~trusty2
Replaces: libgl1-mesa-dri, libgl1-mesa-dri-experimental (<< 7.11.1), xlibmesa-dri (<< 1:7.0.0)
Provides: libgl1-mesa-dri, xorg-renamed-package, xorg-renamed-package-lts-vivid
Depends: libc6 (>= 2.17), libdrm-intel1 (>= 2.4.48), libdrm-nouveau2 (>= 2.4.38), libdrm-radeon1 (>= 2.4.31), libdrm2 (>= 2.4.38), libelf1 (>= 0.142), libexpat1 (>= 2.0.1), libgcc1 (>= 1:4.1.1), libllvm3.6, libstdc++6 (>= 4.6)
Pre-Depends: multiarch-support
Recommends: libtxc-dxtn-s2tc0 | libtxc-dxtn0
Conflicts: libgl1-mesa-dri, xlibmesa-dri (<< 1:7.0.0), xorg-renamed-package-lts-utopic
Breaks: libgl1-mesa-dri-experimental (<< 7.11.1), libgl1-mesa-glx-lts-vivid (<< 7.10.2-4), libgl1-mesa-glx-no-multiarch, xserver-xorg-core-lts-vivid (<< 2:1.14.3-5), xserver-xorg-core-no-multiarch
Filename: pool/main/m/mesa-lts-vivid/libgl1-mesa-dri-lts-vivid_10.5.9-2ubuntu1~trusty2_amd64.deb
Size: 3380460
MD5sum: e0ee84b48093088cc617de5efb3afa93
SHA1: 7ec399471ca724b551f7178966bacd908f809f34
SHA256: 1fe182f3ad5ea169560323b160c870beb0885edc46dc02d4a21600327b03fa30
Description-en: free implementation of the OpenGL API -- DRI modules
 This version of Mesa provides GLX and DRI capabilities: it is capable of
 both direct and indirect rendering.  For direct rendering, it can use DRI
 modules from the libgl1-mesa-dri package to accelerate drawing.
 .
 This package does not include the OpenGL library itself, only the DRI
 modules for accelerating direct rendering.
 .
 For a complete description of Mesa, please look at the
 libgl1-mesa-glx package.
Description-md5: 5f2b652ffc2f2781c936450c0c51bcc7
Multi-Arch: same
Homepage: http://mesa3d.sourceforge.net/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 9m



```

for 
dpkg -l libgl1-mesa-glx-lts-vivid

```

pandoragami@pandoragami-desktop:~$ dpkg -l libgl1-mesa-glx-lts-vivid
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  libgl1-mesa-gl 10.5.9-2ubun amd64        free implementation of the OpenGL
pandoragami@pandoragami-desktop:~$ 

```


for apt-cache show libgl1-mesa-glx-lts-vivid

```

pandoragami@pandoragami-desktop:~$ apt-cache show libgl1-mesa-glx-lts-vivid
Package: libgl1-mesa-glx-lts-vivid
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 689
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: amd64
Multi-Arch: same
Source: mesa-lts-vivid
Version: 10.5.9-2ubuntu1~trusty3
Replaces: libgl1, libgl1-mesa-dri-lts-vivid (<< 6.4.0), libgl1-mesa-glx
Provides: libgl1, libgl1-mesa-glx, xorg-renamed-package, xorg-renamed-package-lts-vivid
Depends: libc6 (>= 2.14), libdrm2 (>= 2.3.1), libexpat1 (>= 2.0.1), libglapi-mesa-lts-vivid (= 10.5.9-2ubuntu1~trusty3), libx11-6 (>= 2:1.4.99.1), libx11-xcb1, libxcb-dri2-0 (>= 1.8), libxcb-dri3-0, libxcb-glx0 (>= 1.8), libxcb-present0, libxcb-sync1, libxcb1 (>= 1.9.2), libxdamage1 (>= 1:1.1), libxext6, libxfixes3, libxshmfence1, libxxf86vm1, libudev1, libgl1-mesa-dri-lts-vivid (>= 7.2)
Pre-Depends: multiarch-support
Breaks: fglrx-glx (<< 1:11-6-1), glx-diversions (<< 0.4), libgl1-nvidia-alternatives (<= 275.09.07-1)
Conflicts: libgl1, libgl1-mesa-dri-lts-vivid (<< 6.4.0), libgl1-mesa-glx, xorg-renamed-package-lts-utopic
Description-en: free implementation of the OpenGL API -- GLX runtime
 Mesa is a 3-D graphics library with an API which is very similar to
 that of OpenGL.  To the extent that Mesa utilizes the OpenGL command
 syntax or state machine, it is being used with authorization from
 Silicon Graphics, Inc.  However, the author makes no claim that Mesa
 is in any way a compatible replacement for OpenGL or associated with
 Silicon Graphics, Inc.
 .
 This version of Mesa provides GLX and DRI capabilities: it is capable of
 both direct and indirect rendering.  For direct rendering, it can use DRI
 modules from the libgl1-mesa-dri package to accelerate drawing.
 .
 This package does not include the modules themselves: these can be found
 in the libgl1-mesa-dri package.
Description-md5: 55c9cfe284958a4586b3c6b8323ccf0c
Homepage: http://mesa3d.sourceforge.net/
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>

Package: libgl1-mesa-glx-lts-vivid
Priority: optional
Section: libs
Installed-Size: 689
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Architecture: amd64
Source: mesa-lts-vivid
Version: 10.5.9-2ubuntu1~trusty2
Replaces: libgl1, libgl1-mesa-dri-lts-vivid (<< 6.4.0), libgl1-mesa-glx
Provides: libgl1, libgl1-mesa-glx, xorg-renamed-package, xorg-renamed-package-lts-vivid
Depends: libc6 (>= 2.14), libdrm2 (>= 2.3.1), libexpat1 (>= 2.0.1), libglapi-mesa-lts-vivid (= 10.5.9-2ubuntu1~trusty2), libx11-6 (>= 2:1.4.99.1), libx11-xcb1, libxcb-dri2-0 (>= 1.8), libxcb-dri3-0, libxcb-glx0 (>= 1.8), libxcb-present0, libxcb-sync1, libxcb1 (>= 1.9.2), libxdamage1 (>= 1:1.1), libxext6, libxfixes3, libxshmfence1, libxxf86vm1, libudev1, libgl1-mesa-dri-lts-vivid (>= 7.2)
Pre-Depends: multiarch-support
Conflicts: libgl1, libgl1-mesa-dri-lts-vivid (<< 6.4.0), libgl1-mesa-glx, xorg-renamed-package-lts-utopic
Breaks: fglrx-glx (<< 1:11-6-1), glx-diversions (<< 0.4), libgl1-nvidia-alternatives (<= 275.09.07-1)
Filename: pool/main/m/mesa-lts-vivid/libgl1-mesa-glx-lts-vivid_10.5.9-2ubuntu1~trusty2_amd64.deb
Size: 144244
MD5sum: 689bc845707852eeddafec82cee5369c
SHA1: 947c92e931c928d1faa74b3dd9f457662d21fe34
SHA256: 70abf054b8385dac205124373880dd00c3bc2c5f857f7e6885554726a9459e57
Description-en: free implementation of the OpenGL API -- GLX runtime
 Mesa is a 3-D graphics library with an API which is very similar to
 that of OpenGL.  To the extent that Mesa utilizes the OpenGL command
 syntax or state machine, it is being used with authorization from
 Silicon Graphics, Inc.  However, the author makes no claim that Mesa
 is in any way a compatible replacement for OpenGL or associated with
 Silicon Graphics, Inc.
 .
 This version of Mesa provides GLX and DRI capabilities: it is capable of
 both direct and indirect rendering.  For direct rendering, it can use DRI
 modules from the libgl1-mesa-dri package to accelerate drawing.
 .
 This package does not include the modules themselves: these can be found
 in the libgl1-mesa-dri package.
Description-md5: 55c9cfe284958a4586b3c6b8323ccf0c
Multi-Arch: same
Homepage: http://mesa3d.sourceforge.net/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 9m

pandoragami@pandoragami-desktop:~$ 


```

---

### Post by Bashing-om on 2015-11-20
pandoragamil Yeah ..

Looks good to me .. 
I did have a thought .
Let's make sure all the HWE components are in place:
```

dpkg -l linux-generic-lts-vivid
dpkg -l libgl1-mesa-glx-lts-vivid
dpkg -l xserver-xorg-lts-vivid
dpkg -l linux-image-generic-lts-trusty

```
If all are 'ii" in that first column, we are good to proceed .

A fact that xserver-xorg has been superseded .
What returns:
```

sudo dpkg-reconfigure xserver-xorg-core-lts-vivid

```

Then we finish up with the "update-initramfs -u" if all is positive.

[INDENT][INDENT]I was worried there for a bit
[/INDENT][/INDENT]

---

### Post by pandoragami on 2015-11-20
Bad news, I rebooted and I'm back in 640x480 mode again. Maybe that second to last line was the problem.

---

### Post by Bashing-om on 2015-11-20
pandoragami: K ..

See my last .. then we look from there as to what is installed and what X is doing .

[INDENT][INDENT]I do enjoy a good puzzle
[/INDENT][/INDENT]

---

### Post by pandoragami on 2015-11-20
Thanks Bashing-om,

Anyways it works!

What I did was run this code again 

```


sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak ##gets a no-longer needed file out of the way
sudo apt-get purge fglrx fglrx-amdcccle fglrx-updates fglrx-amdcccle-updates ##removes all the proprietary driver files
sudo apt-get install dkms ##cheap insurance - for installing supplementary versions of kernel modules (the driver is a module)
sudo apt-get install xserver-xorg-video-radeon-lts-vivid ##the Open Source module it's self
sudo apt-get install --reinstall libgl1-mesa-glx-lts-vivid libgl1-mesa-dri-lts-vivid xserver-xorg-core-lts-vivid ##just to make sure the related libraries and the xserver layer is clean and uncorrupted - the current version [COLOR=red] here we support HWE [/COLOR]
sudo dpkg-reconfigure xserver-xorg ## just that, make the operating system forget the purged 'FGLRX' module, and pick up and use the new module(s) installed (radeon)
sudo update-initramfs -u ##again, cheap insurance, make sure the linux-image is rebuilt with the new libs and modules.


```

I had trouble with this line though: 
sudo apt-get install xserver-xorg-video-radeon-lts-vivid

and it was telling me that some other dependencies (2 of them, can't remember what they were called) were corrupt, so I reinstalled the first one it 
mentioned (took like 5 minutes) and then ran the line again:


sudo apt-get install xserver-xorg-video-radeon-lts-vivid

which said it was already installed, nothing to do. Then I skipped this line:

sudo apt-get install --reinstall libgl1-mesa-glx-lts-vivid libgl1-mesa-dri-lts-vivid xserver-xorg-core-lts-vivid

since I figured I just installed everything and then the last two lines went fine.

I then rebooted the computer and got to a blank screen right after the purplish background so I manually shut-off and rebooted again and it worked. Thanks

---

### Post by Bashing-om on 2015-11-20
pandoragami; Great !

Pleased it has worked out ..

Had to be "something" keeping the install from completing .

It's now
[INDENT][INDENT][INDENT]up up and away

[INDENT][INDENT][INDENT]look forward to seeing you next time
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

