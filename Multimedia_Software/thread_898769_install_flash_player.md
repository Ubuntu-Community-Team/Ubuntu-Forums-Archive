---
title: "install flash player"
date: 2008-08-23
forum: Multimedia Software
---

### Post by spamalot on 2008-08-23
hello, here's a problem i have. any help appreciated.


./install_flash_player_9_linux.tar.gz saved

Download done.
Flash Plugin installed

Setting up gnash-common (0.8.2-0ubuntu3)

Setting up gnash 
Setting up mozilla-plugin-gnash

Processing triggers for libc6
ldconfig deffered processing now taking place
Errors encountered while processing:
john
E: Sub-process /usr/bin/dpkg returned error code (1)
a package failed to install. Trying to recover:
Setting up john (1.6-40.3ubuntu1) ...
stat: cannot stat /var/run/john: no such file or directory
dpkg: error processing john (--configure):
subprocess post-installation script returned error exit status 1

---

### Post by youthforlinux on 2008-08-23
try this:

```
sudo aptitude purge flashplugin-nonfree && sudo aptitude install flashplugin-nonfree
```

---

### Post by spamalot on 2008-09-02
thanks for the advice, but it did not work for me. that's after upgrading to 8.04 and restarting the system. i have absolutely no audio and/or video capability. a way to diagnose the problem. 

here's the output from the suggested command:

~$ sudo aptitude purge flashplugin-nonfree && sudo aptitude install flashplugin-nonfree
[sudo] password for er: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages will be REMOVED:
  flashplugin-nonfree{p} 
The following partially installed packages will be configured:
  john 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 168kB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
(Reading database ... 200044 files and directories currently installed.)
Removing flashplugin-nonfree ...
Purging configuration files for flashplugin-nonfree ...
Setting up john (1.6-40.3ubuntu1) ...
stat: cannot stat `/var/run/john': No such file or directory
dpkg: error processing john (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 john
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up john (1.6-40.3ubuntu1) ...
stat: cannot stat `/var/run/john': No such file or directory
dpkg: error processing john (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 john
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done   

[http://www.cnn.com/video/live/live.html?stream=stream3](http://www.cnn.com/video/live/live.html?stream=stream3)

PLUGIN ERROR:
Oops! You need the latest version of the Flash PlugIn/ActiveX Player to view this video. Download it now.

Please restart your browser after the plugin is installed.

---

### Post by wolfen69 on 2008-09-02
do not run gnash and flash at the same time. start over. completely remove flash and gnash. then:
```
sudo apt-get clean
```
then
```
sudo apt-get autoremove
```
then
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by wolfen69 on 2008-09-02
as far as viewing that site, you are out of luck. it obviously needs windows plugins to view.

---

### Post by spamalot on 2008-09-02
Removing gnash and flash (with Synaptic) produce errors related to john similar to those below, but I've been able to play a video on youtube. Many thanks for the advice. :)

er@ubuntu:~$ sudo apt-get clean
er@ubuntu:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up john (1.6-40.3ubuntu1) ...
stat: cannot stat `/var/run/john': No such file or directory
dpkg: error processing john (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 john
E: Sub-process /usr/bin/dpkg returned an error code (1)
er@ubuntu:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  konqueror-nsplugins libflashsupport ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 18.7kB of archives.
After this operation, 168kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse flashplugin-nonfree 9.0.124.0ubuntu2 [18.7kB]
Fetched 18.7kB in 0s (52.2kB/s)          
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 199982 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.124.0ubuntu2_amd64.deb) ...
Setting up john (1.6-40.3ubuntu1) ...
stat: cannot stat `/var/run/john': No such file or directory
dpkg: error processing john (--configure):
 subprocess post-installation script returned error exit status 1
Setting up flashplugin-nonfree (9.0.124.0ubuntu2) ...
Downloading...
--14:39:21--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 96.7.66.70
Connecting to fpdownload.macromedia.com|96.7.66.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,044,538 (2.9M) [application/x-gzip]

    0K .......... .......... .......... .......... ..........  1%    1.05 MB/s
   50K .......... .......... .......... .......... ..........  3%    1.68 MB/s
  100K .......... .......... .......... .......... ..........  5%    1.77 MB/s
  150K .......... .......... .......... .......... ..........  6%    1.73 MB/s
  200K .......... .......... .......... .......... ..........  8%    1.67 MB/s
  250K .......... .......... .......... .......... .......... 10%    1.47 MB/s
  300K .......... .......... .......... .......... .......... 11%    1.30 MB/s
  350K .......... .......... .......... .......... .......... 13%    1.70 MB/s
  400K .......... .......... .......... .......... .......... 15%    1.90 MB/s
  450K .......... .......... .......... .......... .......... 16%    1.76 MB/s
  500K .......... .......... .......... .......... .......... 18%    1.84 MB/s
  550K .......... .......... .......... .......... .......... 20%    1.84 MB/s
  600K .......... .......... .......... .......... .......... 21%    1.67 MB/s
  650K .......... .......... .......... .......... .......... 23%    1.84 MB/s
  700K .......... .......... .......... .......... .......... 25%    1.61 MB/s
  750K .......... .......... .......... .......... .......... 26%    1.70 MB/s
  800K .......... .......... .......... .......... .......... 28%    1.66 MB/s
  850K .......... .......... .......... .......... .......... 30%    1.72 MB/s
  900K .......... .......... .......... .......... .......... 31%    1.83 MB/s
  950K .......... .......... .......... .......... .......... 33%    1.87 MB/s
 1000K .......... .......... .......... .......... .......... 35%    1.68 MB/s
 1050K .......... .......... .......... .......... .......... 36%    1.58 MB/s
 1100K .......... .......... .......... .......... .......... 38%    1.83 MB/s
 1150K .......... .......... .......... .......... .......... 40%    1.75 MB/s
 1200K .......... .......... .......... .......... .......... 42%    1.78 MB/s
 1250K .......... .......... .......... .......... .......... 43%    1.62 MB/s
 1300K .......... .......... .......... .......... .......... 45%    1.87 MB/s
 1350K .......... .......... .......... .......... .......... 47%    1.64 MB/s
 1400K .......... .......... .......... .......... .......... 48%    1.74 MB/s
 1450K .......... .......... .......... .......... .......... 50%    1.87 MB/s
 1500K .......... .......... .......... .......... .......... 52%    1.70 MB/s
 1550K .......... .......... .......... .......... .......... 53%    1.90 MB/s
 1600K .......... .......... .......... .......... .......... 55%    1.86 MB/s
 1650K .......... .......... .......... .......... .......... 57%    1.63 MB/s
 1700K .......... .......... .......... .......... .......... 58%    1.68 MB/s
 1750K .......... .......... .......... .......... .......... 60%    1.52 MB/s
 1800K .......... .......... .......... .......... .......... 62%    1.78 MB/s
 1850K .......... .......... .......... .......... .......... 63%    1.83 MB/s
 1900K .......... .......... .......... .......... .......... 65%    1.84 MB/s
 1950K .......... .......... .......... .......... .......... 67%    1.65 MB/s
 2000K .......... .......... .......... .......... .......... 68%    1.77 MB/s
 2050K .......... .......... .......... .......... .......... 70%    1.69 MB/s
 2100K .......... .......... .......... .......... .......... 72%    1.82 MB/s
 2150K .......... .......... .......... .......... .......... 73%    1.79 MB/s
 2200K .......... .......... .......... .......... .......... 75%    1.65 MB/s
 2250K .......... .......... .......... .......... .......... 77%    1.74 MB/s
 2300K .......... .......... .......... .......... .......... 79%    1.72 MB/s
 2350K .......... .......... .......... .......... .......... 80%    1.77 MB/s
 2400K .......... .......... .......... .......... .......... 82%    1.82 MB/s
 2450K .......... .......... .......... .......... .......... 84%    1.69 MB/s
 2500K .......... .......... .......... .......... .......... 85%    1.83 MB/s
 2550K .......... .......... .......... .......... .......... 87%    1.78 MB/s
 2600K .......... .......... .......... .......... .......... 89%    1.68 MB/s
 2650K .......... .......... .......... .......... .......... 90%    1.62 MB/s
 2700K .......... .......... .......... .......... .......... 92%    1.87 MB/s
 2750K .......... .......... .......... .......... .......... 94%    1.79 MB/s
 2800K .......... .......... .......... .......... .......... 95%    1.74 MB/s
 2850K .......... .......... .......... .......... .......... 97%    1.63 MB/s
 2900K .......... .......... .......... .......... .......... 99%    1.85 MB/s
 2950K .......... .......... ...                             100%    1.68 MB/s

14:39:23 (1.71 MB/s) - `./install_flash_player_9_linux.tar.gz' saved [3044538/3044538]

Download done.
Flash Plugin installed.

Errors were encountered while processing:
 john
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

