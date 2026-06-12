---
title: "fglrx Widescreen Help"
date: 2006-06-17
forum: Multimedia &amp; Video
---

### Post by nrjCL on 2006-06-17
Ok, I am very very new to Linux... please keep that in mind.

I am trying to install the widescreen version of the fglrx driver for my ATI Radeon Xpress 200M, on my Widescreen Laptop.  I tried following the instructions I found on another thread.

Code:  
sudo apt-get install gcc-3.4 module-assistant
sudo dpkg -i fglrx-control_8.18.6-1_i386.deb
sudo dpkg -i fglrx-kernel-source_8.18.6-1_i386.deb
sudo dpkg -i xorg-driver-fglrx_8.18.6-1_i386.deb
sudo apt-get -f upgrade 

and when i get the .deb files it says "Invalid file/directory"...

Any help would be much appreciated!!

---

### Post by nrjCL on 2006-06-17
to be specific it says

dpkg: error processing fglrx-control_8.18.6-1_i386.deb (--install):
cannot access archive: No such file or directory
Errors were encountered while processing:
fglrx-control_8.18.6-1_i386.deb

---

### Post by Dakaru on 2006-06-17
I used the normal ATI drivers for my 19" Wide Screen monitor. 

Worked like a charm.

---

### Post by nrjCL on 2006-06-17
I used the regular fglrx drivers at first, but it wouldn't let me choose any widescreen resolutions... it restricted me to 1024x768.

The install that suppsedly fixed this problem can be seen here:

[http://doc.gwos.org/index.php/Install_ATI_fglrx_driver_for_widescreen](http://doc.gwos.org/index.php/Install_ATI_fglrx_driver_for_widescreen)

BUT all 3 .deb files could not be found when i tried the steps listed.

---

### Post by nrjCL on 2006-06-17
I got the original one to work as well, but it restricted me to 1024x768 resolutions.

[http://doc.gwos.org/index.php/Install_ATI_fglrx_driver_for_widescreen](http://doc.gwos.org/index.php/Install_ATI_fglrx_driver_for_widescreen)
this supposedly fixes that problem but all three .deb files couldn't be found.

---

### Post by ltmon on 2006-06-17
Where did you download the .deb files to?

It seems you are simply running the command from the wrong directory (i.e. a directory other than where those files are) and therefore the files cannot be found.

Before trying again make sure the downloaded .deb files are in your home directory, or change directory with "cd nameofdirectory" in the terminal.

L.

---

### Post by nrjCL on 2006-06-17
ok so I figured out what I was doing wrong before, and those .deb files are no longer being hosted.

so i went to another thread...
and download the drivers... upon running them I got this message

==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: Xorg 7.0.0

Detected version of X does not have a matching 'x700' directory
You may override the detected version using the following syntax:
     X_VERSION=<xdir> ./ati-driver-installer-<ver>-<arch>.run [--install]

The following values may be used for <xdir>:
    x410        XFree86 4.1.x
    x420        XFree86 4.2.x
    x430        XFree86 4.3.x
    x680        X.Org 6.8.x
    x690        X.Org 6.9.x
Removing temporary directory: fglrx-install
nrj@nrj-laptop:~$




I have no idea what to do now...

---

### Post by Dakaru on 2006-06-19
Just edit your Xorg File,

I have 1 res in my xorg and that is "1440x900" 

Works great.

---

### Post by ltmon on 2006-06-19
nrjCL: The best (and easiest) way to install the ati proprietry drivers are through the repositories.

The official howto is: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Following one of the many other methods that float around the forums can work, but the easiset I find is just to do as listed in the link above.

btw: The problem with your last try is that the drivers you downloaded do not yet recognize the version of Xorg in Dapper (7.0).  To get around it you need to type in the following:
```

X_VERSION=690 ./ati-driver-installer-<ver>-<arch>.run

```
Replacing <ver> and <arch> with the exact versions of the driver you have downloaded.

Cheers,

L.

---

