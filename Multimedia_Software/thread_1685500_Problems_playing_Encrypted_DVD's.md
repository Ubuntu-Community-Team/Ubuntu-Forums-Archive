---
title: "Problems playing Encrypted DVD's"
date: 2011-02-10
forum: Multimedia Software
---

### Post by ostbahnx on 2011-02-10
I am having problems playing encrypted DVD's with both vlc and totem:

I have 6 unencrypted DVD's and they play in vlc and totem without problems.  I have even uninstalled
libdvdcss, and these 6 DVD's still play.  But I also have around 10 encrypted DVD's  and I get the following error messages shown below in debug mode:
$ export DVDCSS_VERBOSE=2 && vlc > vlc_output.log 2>&1

libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdcss debug: opening target `/dev/sr1'
libdvdcss debug: using libc for access
libdvdcss debug: disc is scrambled
libdvdcss debug: requesting AGID
libdvdcss error: ioctl SendChallenge failed
libdvdcss debug: could not get disc key
libdvdcss debug: using CSS key cache dir: /home/stephen/.dvdcss/NOSFERATU-2000120515281300-0000000000/

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000173
libdvdcss debug: getting title key at block 371 the classic wayostbahnx
libdvdcss debug: requesting AGID
libdvdcss error: ioctl SendChallenge failed
libdvdcss error: fatal error in vts css key
libdvdread: Error cracking CSS key for /VIDEO_TS/VIDEO_TS.VOB (0x00000173)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000022c
libdvdcss debug: getting title key at block 556 the classic way
libdvdcss debug: requesting AGID
libdvdcss error: ioctl SendChallenge failed
libdvdcss error: fatal error in vts css key
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x0000022c)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000b872
libdvdcss debug: getting title key at block 47218 the classic way
libdvdcss debug: requesting AGID
libdvdcss error: ioctl SendChallenge failed
libdvdcss error: fatal error in vts css key
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x0000b872)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x001d5c59
libdvdcss debug: getting title key at block 1924185 the classic way
libdvdcss debug: requesting AGID
libdvdcss error: ioctl SendChallenge failed
libdvdcss error: fatal error in vts css key
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_0.VOB (0x001d5c59)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001d5ca7
libdvdcss debug: getting title key at block 1924263 the classic wayostbahnx
libdvdcss debug: requesting AGID

ETC...

Here are the relevant revisions:
Ubuntu: 10.04
Kernel 2.6.32-28-generic
vlc 1.1.7
totem 2.30.2

libdvdnav4                           4.1.3-6
libdvdcss2                           1.2.10-0.3medibuntu1
libdvdread4                          4.1.3-8ubuntu1

 I also should mention, that I deleted the .dvdcss directory in my home directory.
But doesn't work.

thanks for your help.

Stephen

---

### Post by mc4man on 2011-02-10
What cd/dvd drive do you have? (in *-cdrom: section
```
sudo lshw -C disk
```

---

### Post by ostbahnx on 2011-02-11
*-cdrom
       description: DVD reader
       product: DVD-ROM 305
       vendor: HP
       physical id: 1.1.0
       bus info: scsi@1:1.1.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd1
       logical name: /dev/sr1
       logical name: /media/NOSFERATU
       version: 1.01
       capabilities: removable audio dvd
       configuration: ansiversion=2 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,iocharset=utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1
          logical name: /media/NOSFERATU
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,iocharset=utf8 state=mounted

---

### Post by ostbahnx on 2011-02-13
[SIZE=2]I have since upraded to Ubuntu 10.10 thinking the problem might get fixed, but I still have the same problem of not being able to play encrypted DVD's.

thanks for any help.

Stephen[/SIZE]

---

### Post by JRV on 2011-02-13
Install libdvdcss2 in Ubuntu 10.10 (Maverick Meercat)

If you are using a different version change "maverick" to the correct version name.

You need to add the following lines to /etc/apt/sources.list file or
you need to make sure you have enabled Universe and multiverse repositories Using GUI.

gksudo gedit /etc/apt/sources.list

Make sure you have the following two lines save and exit your file.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick universe multiverse

Now update the source list

sudo apt-get update

sudo apt-get install medibuntu-keyring

sudo apt-get update

For i386 Users install Codecs using the following command

sudo apt-get install w32codecs libdvdcss2

For amd64 Users install Codecs using the following command

sudo apt-get install w64codecs libdvdcss2

---

### Post by ostbahnx on 2011-02-13
I followed all the instructions, and got the following message after everything:

stephen@# stephen:~$ sudo apt-get install w32codecs libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
w32codecs is already the newest version.
libdvdcss2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

It still doesn't work, needless to say.

---

### Post by ostbahnx on 2011-02-14
I added the following lines to /etc/apt/sources.list:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick universe multiverse

Attached is the output from:
$ apt-get update

Below is the output from apt-get install medibuntu-keyring:

stephen@# stephen:~$ sudo apt-get install medibuntu-keyring
[sudo] password for stephen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
medibuntu-keyring is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

And now the final command: 
stephen@# stephen:~$ sudo apt-get install w32codecs libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
w32codecs is already the newest version.
libdvdcss2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by ostbahnx on 2011-02-14
Sorry,
Here is the output from apt-get update:


stephen@# stephen:~$ sudo apt-get update
sudo: unable to resolve host # stephen.server.local
everest.nwroom.net
[sudo] password for stephen: 
Sorry, try again.
[sudo] password for stephen: 
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en                                                          
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_US                                                       
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                                                                             
Get:3 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,066B]                                                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                                                                              
Ign [http://ppa.launchpad.net/rvm/mplayer/ubuntu/](http://ppa.launchpad.net/rvm/mplayer/ubuntu/) maverick/main Translation-en                                                  
Ign [http://ppa.launchpad.net/rvm/mplayer/ubuntu/](http://ppa.launchpad.net/rvm/mplayer/ubuntu/) maverick/main Translation-en_US           
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                                      
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                                          
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg                                         
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en                         
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                              
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US                
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                                          
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                              
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en                   
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US                
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release.gpg           
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/http://archive.ubuntu.com/ubuntu Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/http://archive.ubuntu.com/ubuntu Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                   
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages      
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/maverick Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/maverick Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiversedeb-src Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiversedeb-src Translation-en_US
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages             
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
  404  Not Found
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages             
  404  Not Found
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/multiverse i386 Packages
Fetched 2,610B in 2s (1,225B/s)
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/Release](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/Release)  Unable to find expected entry  multiversedeb-src/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch [http://ppa.launchpad.net/rvm/mplayer/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/rvm/mplayer/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/rvm/mplayer/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/rvm/mplayer/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
stephen@# stephen:~$

---

### Post by ostbahnx on 2011-02-15
> **mc4man said:**
> What cd/dvd drive do you have? (in *-cdrom: section
```
sudo lshw -C disk
```

sudo lshw -C disk
 *-cdrom
       description: DVD reader
       product: DVD-ROM 305
       vendor: HP
       physical id: 1.1.0
       bus info: scsi@1:1.1.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd1
       logical name: /dev/sr1
       logical name: /media/renaissance2
       version: 1.01
       capabilities: removable audio dvd
       configuration: ansiversion=2 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,iocharset=utf8 state=mounted status=ready

---

