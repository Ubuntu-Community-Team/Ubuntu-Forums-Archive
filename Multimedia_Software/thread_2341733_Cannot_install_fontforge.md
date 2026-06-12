---
title: "Cannot install fontforge"
date: 2016-10-31
forum: Multimedia Software
---

### Post by asmox79 on 2016-10-31
Hello!
I have tried to reinstall my font since I use fontforge to make a new one. I noticed there is no option to remove a font without a *font-manager*. I had got some errors during installing this package, problems were related to fontforge. I tried to remove fontforge and install font-manager. And now I cannot install fontforge again:
```
~$ sudo apt-get install fontforgeReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libcaca0:i386 libcairo2:i386 libpixman-1-0:i386 libsdl1.2debian:i386
  libxcb-render0:i386 libxcb-shm0:i386 nvidia-331-updates
  nvidia-opencl-icd-331-updates odbcinst1debian2:i386 python3-tz
  vlc-plugin-pulse
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  fontforge-common
Suggested packages:
  fontforge-doc potrace
The following NEW packages will be installed:
  fontforge fontforge-common
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1723 kB of archives.
After this operation, 7506 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
(Reading database ... 391678 files and directories currently installed.)
Preparing to unpack .../fontforge-common_20161012-0ubuntu1~trusty_all.deb ...
Unpacking fontforge-common (20161012-0ubuntu1~trusty) ...
dpkg: error processing archive /var/cache/apt/archives/fontforge-common_20161012-0ubuntu1~trusty_all.deb (--unpack):
 trying to overwrite '/usr/share/fontforge/Adobe-Japan1-6.cidmap', which is also in package fontforge-extras 0.3-4ubuntu1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Selecting previously unselected package fontforge.
Preparing to unpack .../fontforge_20161012-0ubuntu1~trusty_amd64.deb ...
Unpacking fontforge (20161012-0ubuntu1~trusty) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for menu (2.1.46ubuntu1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/fontforge-common_20161012-0ubuntu1~trusty_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I have tried removing fontconfig-config as at this topic: [http://askubuntu.com/questions/576693/failed-upgrading-12-10-14-04-error-with-fontconfig](http://askubuntu.com/questions/576693/failed-upgrading-12-10-14-04-error-with-fontconfig)
But it gives me additional error:
```
$ sudo apt-get remove --purge fontconfig-config
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 fontconfig : Depends: fontconfig-config but it is not going to be installed
 fontforge : Depends: fontforge-common (= 20161012-0ubuntu1~trusty) but it is not going to be installed
 libfontconfig1 : Depends: fontconfig-config (= 2.11.0-0ubuntu4.2) but it is not going to be installed
 libfontconfig1:i386 : Depends: fontconfig-config:i386 (= 2.11.0-0ubuntu4.2)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

So I tried using this command, with no results:
```
$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libcaca0:i386 libcairo2:i386 libpixman-1-0:i386 libsdl1.2debian:i386
  libxcb-render0:i386 libxcb-shm0:i386 nvidia-331-updates
  nvidia-opencl-icd-331-updates odbcinst1debian2:i386 python3-tz
  vlc-plugin-pulse
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  fontforge-common
The following NEW packages will be installed:
  fontforge-common
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1712 kB of archives.
After this operation, 7431 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 391688 files and directories currently installed.)
Preparing to unpack .../fontforge-common_20161012-0ubuntu1~trusty_all.deb ...
Unpacking fontforge-common (20161012-0ubuntu1~trusty) ...
dpkg: error processing archive /var/cache/apt/archives/fontforge-common_20161012-0ubuntu1~trusty_all.deb (--unpack):
 trying to overwrite '/usr/share/fontforge/Adobe-Japan1-6.cidmap', which is also in package fontforge-extras 0.3-4ubuntu1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/fontforge-common_20161012-0ubuntu1~trusty_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I actually don't know what to do. Please help me.

---

