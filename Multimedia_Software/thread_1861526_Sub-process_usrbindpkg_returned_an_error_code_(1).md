---
title: "Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2011-10-15
forum: Multimedia Software
---

### Post by adam.webb on 2011-10-15
Hi All,

I'm having some problems with (re-)installing drivers for my nVidia Geforce GT550M. I have an ASUS laptop with dual graphics cards, and was trying to get them working properly with Unity (but that's another story). I followed a suggestion and upgraded to a newer version of the nVidia drivers. That was when everything died, and I have tried to return to the standard (nvidia-current) drivers by uninstalling the drivers which I installed, and installing nvidia-current drivers.

But now when I try to install nvidia-current I get the series of error messages bellow. I have tried uninstalling and purging nvidia-current (as it seems to be partially installed badly), and installing with apt-get -f install, all without any headway.

Does anyone have any suggestions?

Cheers

Adam

PS I'm running 11.04, trying to get this sorted before I upgrade.

```
$ sudo apt-get install nvidia-current
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  nvidia-current
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 56.8 MB of archives.
After this operation, 179 MB of additional disk space will be used.
Get:1 http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ natty/main nvidia-current amd64 285.05.09-0ubuntu1~natty~xup1 [56.8 MB]
Fetched 56.8 MB in 6min 48s (139 kB/s)                                         
Selecting previously deselected package nvidia-current.
(Reading database ... 337913 files and directories currently installed.)
Unpacking nvidia-current (from .../nvidia-current_285.05.09-0ubuntu1~natty~xup1_amd64.deb) ...
Processing triggers for man-db ...
Setting up nvidia-current (285.05.09-0ubuntu1~natty~xup1) ...
update-alternatives: error: alternative link /usr/share/man/man1/nvidia-xconfig.1.gz is already managed by x86_64-linux-gnu_gl_conf.
dpkg: error processing nvidia-current (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 nvidia-current
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by RealEnder on 2011-10-16
Hi,
I seems there is some leftovers from fglrx ATI/AMD binary driver.
You can do this:
```
sudo update-alternatives --remove-all x86_64-linux-gnu_gl_conf
```
then
```
sudo aptitude safe-upgrade
```
This should fix it.

---

### Post by cherrywaves on 2011-10-16
have been searching high and low for this, fixed it, thank you!

---

### Post by freemeliberty on 2012-06-01
Hi, I am having a similar issue after I tried getting gimp 2.8. Now I am locked out of my Ubuntu Software Center. Not sure if the fix on this will help but I did get the same error code:

The following packages were automatically installed and are no longer required:
  libbabl-0.0-0 libgegl-0.0-0
Use 'apt-get autoremove' to remove them.
Suggested packages:
  gimp-data-extras
The following packages will be upgraded:
  gimp
1 upgraded, 0 newly installed, 0 to remove and 26 not upgraded.
Need to get 0 B/6,005 kB of archives.
After this operation, 2,159 kB of additional disk space will be used.
(Reading database ... 178238 files and directories currently installed.)
Preparing to replace gimp 2.6.12-1ubuntu1 (using .../gimp_2.8.0-1ubuntu0ppa4~precise_i386.deb) ...
Unpacking replacement gimp ...
dpkg: error processing /var/cache/apt/archives/gimp_2.8.0-1ubuntu0ppa4~precise_i386.deb (--unpack):
 trying to overwrite '/usr/lib/gimp/2.0/plug-ins/file-xmc', which is also in package gimp-plugin-registry 3.5.4-1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/gimp_2.8.0-1ubuntu0ppa4~precise_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

