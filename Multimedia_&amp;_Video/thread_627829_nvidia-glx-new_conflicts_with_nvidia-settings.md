---
title: "nvidia-glx-new conflicts with nvidia-settings"
date: 2007-11-30
forum: Multimedia &amp; Video
---

### Post by darrenleeweber on 2007-11-30
I have a new Lenovo ThinkPad T61 with a default install of ubuntu 7.10 gutsy with amd64 option.

The laptop has an NVidia N140m

root@skiweber:~# lspci | grep nVidia
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 140M (rev a1)

I've installed nvidia-glx-new, but I don't see any entry in

Applications->System Tools-> Nvidia X Server Settings

How do I get a graphical config tool for this nvidia driver?


I've tried to install nvidia-settings, but it conflicts with nvidia-glx-new, eg:

root@skiweber:~# apt-get install nvidia-glx-new
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-glx-new is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

root@skiweber:~# apt-get install nvidia-settings
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Recommended packages:
  nvidia-glx-legacy
The following packages will be REMOVED:
  nvidia-glx-new
The following NEW packages will be installed:
  nvidia-settings
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 710kB of archives.
After unpacking 24.9MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.


Also nvidia-xconfig has an untidy fail on installation:

root@skiweber:~# apt-get install nvidia-xconfig
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  nvidia-xconfig
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/62.8kB of archives.
After unpacking 213kB of additional disk space will be used.
(Reading database ... 260274 files and directories currently installed.)
Unpacking nvidia-xconfig (from .../nvidia-xconfig_1.0+20070502-1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/nvidia-xconfig_1.0+20070502-1_amd64.deb (--unpack):
 trying to overwrite `/usr/bin/nvidia-xconfig', which is also in package nvidia-glx-new
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-xconfig_1.0+20070502-1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@skiweber:~#

---

### Post by dustigroove on 2007-12-22
If you have the nvidia-glx-new package installed then the settings program is included with it, you can just manually add a launcher within your menu for nvidia-settings.

Cheers.

---

