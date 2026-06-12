---
title: "Try install ATI driver, says no such file in dir"
date: 2006-08-07
forum: Multimedia &amp; Video
---

### Post by WalmartSniperLX on 2006-08-07
I followed these instructions that I found on this forum. Here are the steps ive completed:

Install necessary tools:
Code:
sudo apt-get update 
sudo apt-get install module-assistant build-essential 
sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base


But when it comes to this:



Create .deb packages:

Code:
chmod +x ati-driver-installer-8.26.18-x86.run
./ati-driver-installer-8.26.18-x86.run --buildpkg Ubuntu/dapper


or any code that involves the name of the driver it says there's no such file in the directory. I just started working with Ubuntu/linux last night so im a complete noob at this. Thanks

Edit: O yeah and i have the 32 bit version and a Radeon x1600 :)

---

### Post by jaimz on 2006-08-07
you did download it to your home folder right?
because you need to have it in the home folder
oh and there's the 8.27.10 drivers out now
so you might want to get those

well just download the latest one
put it in your home folder
and continue on what you were doing with those steps

---

### Post by KabalS on 2006-08-07
same problem here
it gives me this error
[HTML]
LD_PRELOAD= dh_shlibdeps
dpkg: /usr/i486-linux-gnu/lib/libpthread.so.0 not found.
dpkg: /usr/i486-linux-gnu/lib/libstdc++.so.5 not found.
dpkg: /usr/i486-linux-gnu/lib/libm.so.6 not found.
dpkg: /usr/i486-linux-gnu/lib/libgcc_s.so.1 not found.
dpkg: /usr/i486-linux-gnu/lib/libc.so.6 not found.
dpkg: /usr/i486-linux-gnu/lib/libXext.so.6 not found.
dpkg: /usr/i486-linux-gnu/lib/libX11.so.6 not found.
dpkg: /usr/i486-linux-gnu/lib/libdl.so.2 not found.
dpkg: /usr/i486-linux-gnu/lib/librt.so.1 not found.
dpkg: /usr/i486-linux-gnu/lib/libGL.so.1 not found.
dpkg: /usr/i486-linux-gnu/lib/libXrandr.so.2 not found.
dpkg: /usr/i486-linux-gnu/lib/libXrender.so.1 not found.
dpkg: /usr/i486-linux-gnu/lib/libfglrx_gamma.so.1 not found.
dpkg-shlibdeps: failure: dpkg --search gave error exit status 1
dh_shlibdeps: command returned error code 256
[/HTML]

I also tryed to make an installation without debs. but it gives me another error.Still no luck here

---

### Post by jaimz on 2006-08-07
ok start all over again

using this method

[http://ubuntuforums.org/showthread.php?t=204910]("http://ubuntuforums.org/showthread.php?t=204910")

I'm pretty sure that's where you started from in the first place

but make sure the latest drivers are in the home folder

> chmod +x ati-driver-installer-8.26.18-x86.run
./ati-driver-installer-8.26.18-x86.run --buildpkg Ubuntu/dapper

instead of putting in the old drivers 8.26.18

just change that to 8.17.10 (the one on your home folder)
and it should work

---

### Post by KabalS on 2006-08-07
tried again..
the problem is that I don't have such dir:
..
/i486-linux-gnu/
..
I have tried to crate it and  simlink the libs, but notting has changed.

---

### Post by WalmartSniperLX on 2006-08-07
> **jaimz said:**
> you did download it to your home folder right?
because you need to have it in the home folder
oh and there's the 8.27.10 drivers out now
so you might want to get those

well just download the latest one
put it in your home folder
and continue on what you were doing with those steps

O woah that might be it. Its on the desktop

---

### Post by WalmartSniperLX on 2006-08-07
> **jaimz said:**
> ok start all over again

using this method

[http://ubuntuforums.org/showthread.php?t=204910]("http://ubuntuforums.org/showthread.php?t=204910")

I'm pretty sure that's where you started from in the first place

but make sure the latest drivers are in the home folder



instead of putting in the old drivers 8.26.18

just change that to 8.17.10 (the one on your home folder)
and it should work

Ok i did that, and it uncomrpessed and said successful.

---

### Post by WalmartSniperLX on 2006-08-07
Ok now i created the deb packages and i see them in the folder, but when i go to install them, i get the same sort of message saying no such drive in archive :(  Is there something else im missing or forgot to do?

Edit: wait wait my bad lol typo. its working :p ](*,)

EDIT: Ok here we go. Im now on this step of the instructions:

Compile the kernel module:


Code:
sudo module-assistant prepare,update 
sudo module-assistant build,install fglrx 
sudo depmod


And when i type it in, it says module-assistant isnt a valid code :confused:

---

### Post by WalmartSniperLX on 2006-08-07
Ok well i decided to skip that step since it wasnt working and just finished it. The driver installed correctly and everything is FAST!!!!!! completely unloaded my cpu of ubuntu's desktop graphics. WOOHOOO! Thanks for the help guys! Wouldnt have gotten anywhere w.o. ur help!!! :p :-D

---

### Post by WalmartSniperLX on 2006-08-07
Ok one thing i would like to know tho is that after installing the driver my cpu is running at constant load. Is that normal for linux? I mean before i was getting mean downtime online (full 6mb/s) and now with the load i cant get all that info threaded. Also it hangs with other tasks when im running something else. 100% load... whats wrong

---

### Post by darrenm on 2006-08-07
open a command line, run top and have a look what is taking all the CPU.

---

### Post by WalmartSniperLX on 2006-08-07
i just did and it says its the ati driver (atieventsd)

---

### Post by whatever on 2006-08-07
> **WalmartSniperLX said:**
> i just did and it says its the ati driver (atieventsd)
atieventsd is NOT the driver. it's a daemon which offers hotplug support for digital flat panels and thermal event power management. if you don't need these features you may kill the daemon.

---

### Post by WalmartSniperLX on 2006-08-07
ok awesome thanks a lot.

---

### Post by loclei on 2006-11-11
> **WalmartSniperLX said:**
> I followed these instructions that I found on this forum. Here are the steps ive completed:

1.Install necessary tools:
Code:
sudo apt-get update 
sudo apt-get install module-assistant build-essential 
sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base

2.Create .deb packages:

Code:
chmod +x ati-driver-installer-8.26.18-x86.run
./ati-driver-installer-8.26.18-x86.run --buildpkg Ubuntu/dapper


at 1 i get
```

sudo apt-get update
Errhttp://security.ubuntu.com edgy-security Release.gpg
  Temporary failure resolving ‘security.ubuntu.com’
Errhttp://security.ubuntu.com edgy-security/main Translation-en_GB
  Temporary failure resolving ‘security.ubuntu.com’
Errhttp://security.ubuntu.com edgy-security/restricted Translation-en_GB
  Temporary failure resolving ‘security.ubuntu.com’
Errhttp://security.ubuntu.com edgy-security/multiverse Translation-en_GB
  Temporary failure resolving ‘security.ubuntu.com’
Errhttp://archive.ubuntu.com edgy Release.gpg
  Temporary failure resolving ‘archive.ubuntu.com’
Errhttp://archive.ubuntu.com edgy/main Translation-en_GB
  Temporary failure resolving ‘archive.ubuntu.com’
Errhttp://archive.ubuntu.com edgy/restricted Translation-en_GB
  Temporary failure resolving ‘archive.ubuntu.com’
Errhttp://archive.ubuntu.com edgy/multiverse Translation-en_GB
  Temporary failure resolving ‘archive.ubuntu.com’
Errhttp://archive.ubuntu.com edgy/universe Translation-en_GB
  Temporary failure resolving ‘archive.ubuntu.com’
Errhttp://archive.ubuntu.com edgy-updates Release.gpg
  Temporary failure resolving ‘archive.ubuntu.com’
Errhttp://archive.ubuntu.com edgy-updates/main Translation-en_GB
  Temporary failure resolving ‘archive.ubuntu.com’
Errhttp://archive.ubuntu.com edgy-updates/restricted Translation-en_GB
  Temporary failure resolving ‘archive.ubuntu.com’
Errhttp://archive.ubuntu.com edgy-updates/multiverse Translation-en_GB
  Temporary failure resolving ‘archive.ubuntu.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg)  Temporary failure resolving ‘archive.ubuntu.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_GB.bz2)  Temporary failure resolving ‘archive.ubuntu.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_GB.bz2)  Temporary failure resolving ‘archive.ubuntu.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_GB.bz2)  Temporary failure resolving ‘archive.ubuntu.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_GB.bz2)  Temporary failure resolving ‘archive.ubuntu.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg)  Temporary failure resolving ‘archive.ubuntu.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_GB.bz2)  Temporary failure resolving ‘archive.ubuntu.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_GB.bz2)  Temporary failure resolving ‘archive.ubuntu.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/i18n/Translation-en_GB.bz2)  Temporary failure resolving ‘archive.ubuntu.com’
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg)  Temporary failure resolving ‘security.ubuntu.com’
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-en_GB.bz2)  Temporary failure resolving ‘security.ubuntu.com’
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-en_GB.bz2)  Temporary failure resolving ‘security.ubuntu.com’
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/i18n/Translation-en_GB.bz2)  Temporary failure resolving ‘security.ubuntu.com’
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
```



at 2 i get

```

user@user-desktop:~$ sudo mv /bin/sh /bin/SH
user@user-desktop:~$ sudo ln -s /bin/bash /bin/sh
user@user-desktop:~$ ./ati-driver-installer-8.28.8.run --buildpkg Ubuntu/dapper
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/dapper
./packages/Ubuntu/ati-packager.sh: line 56: dpkg-architecture: command not found
Error: unsupported architecture: 
Removing temporary directory: fglrx-install

```

can someone help me?

---

### Post by darrenm on 2006-11-11
Its looks like you werent connected to the internet for the first one or if so then you are connected via a proxy server?

---

