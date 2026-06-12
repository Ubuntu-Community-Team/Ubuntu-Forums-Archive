---
title: "nVidia driver in Feisty Errors"
date: 2007-05-07
forum: Multimedia &amp; Video
---

### Post by Tellisk on 2007-05-07
Hello.
I upgraded to 7.04 from 6.10 last night. And I've been trying to get my graphics card set up ever since I got home today.

I found a couple of ways people have said to do it, but nothing is working.

The error I get when I try from the Restricted Drivers Manager is:
E: /var/cache/apt/archives/nvidia-glx_1%3a1.0.9631+2.6.20.5-15.20_i386.deb: subprocess pre-installation script returned error exit status 2

And the error in terminal when I try ```
$ sudo apt-get install nvidia-glx-new

``` is

```
After unpacking 14.7MB of additional disk space will be used.
(Reading database ... 140910 files and directories currently installed.)
Unpacking nvidia-glx-new (from .../nvidia-glx-new_1.0.9755+2.6.20.5-15.20_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-new' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx'
dpkg: error processing /var/cache/apt/archives/nvidia-glx-new_1.0.9755+2.6.20.5-15.20_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-new_1.0.9755+2.6.20.5-15.20_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

If anyone can help, I'd be elated and much relieved. Thanks.

---

### Post by Tellisk on 2007-05-07
If it helps, it's a Biostar EGate GeForce 6800 card.

---

### Post by Nythain on 2007-05-07
sudo aptitude --purge remove nvidia-glx-new nvidia-kernel-common xorg-driver-fglrx
sudo aptitude clean
sudo aptitude update
sudo aptitude install nvidia-glx-new

that should take care of removing any previous attempts at installing it, and remove the fglrx driver wich is an ati driver i have no idea why you have installed, and try to reinstall just the driver package you need... theoretically and hopefully

---

### Post by Tellisk on 2007-05-07
Ok. That seems to have worked. Thanks a ton. It's installing now.

---

### Post by Tellisk on 2007-05-07
Hmm, that last step gave me the exact same error. I'll try running through them again in case I missed something.

---

### Post by Tellisk on 2007-05-07
Ok, here is the output from the last step:

```

The following NEW packages will be installed:
  linux-restricted-modules-2.6.20-15-386 nvidia-glx-new 
  nvidia-kernel-common 
0 packages upgraded, 3 newly installed, 0 to remove and 1 not upgraded.
Need to get 21.2MB of archives. After unpacking 57.9MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 http://archive.ubuntu.com feisty/restricted nvidia-kernel-common 20051028+1ubuntu7 [5176B]
Get:2 http://archive.ubuntu.com feisty/restricted linux-restricted-modules-2.6.20-15-386 2.6.20.5-15.20 [16.3MB]
Get:3 http://archive.ubuntu.com feisty/restricted nvidia-glx-new 1.0.9755+2.6.20.5-15.20 [4833kB]
Fetched 21.2MB in 2m9s (163kB/s)                                                
Selecting previously deselected package nvidia-kernel-common.
(Reading database ... 142728 files and directories currently installed.)
Unpacking nvidia-kernel-common (from .../nvidia-kernel-common_20051028+1ubuntu7_all.deb) ...
Selecting previously deselected package linux-restricted-modules-2.6.20-15-386.
Unpacking linux-restricted-modules-2.6.20-15-386 (from .../linux-restricted-modules-2.6.20-15-386_2.6.20.5-15.20_i386.deb) ...
Unpacking nvidia-glx-new (from .../nvidia-glx-new_1.0.9755+2.6.20.5-15.20_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-new' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx'
dpkg: error processing /var/cache/apt/archives/nvidia-glx-new_1.0.9755+2.6.20.5-15.20_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-new_1.0.9755+2.6.20.5-15.20_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up nvidia-kernel-common (20051028+1ubuntu7) ...

Setting up linux-restricted-modules-2.6.20-15-386 (2.6.20.5-15.20) ...


```

---

### Post by Tellisk on 2007-05-08
bump, because it's still not solved and fifth page won't get seen =(

---

### Post by anachreon_ on 2007-05-08
This is a long shot, but do you have nvidia-xconfig installed?  It conflicted with my install of the nvidia *proprietary* driver, and I had to remove it for the install to complete.  Since you're not installing the proprietary driver, and i don't see an error message for it, this probably isn't the issue, but if you have absolutely nothing else to try you could remove the nvidia-xconfig package and then re-try the driver install.

Also, unless you are completely committed to free software, you may want to consider just using the proprietary driver.  I'd recommend using Alberto Milone's "Envy" script to do the work for you:

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

If you choose to use it, follow the instructions closely and use the unstable version since the other versions don't support Feisty.

---

### Post by Tellisk on 2007-05-08
Thanks. I got the unstable version of Envy and am trying it now; will report back with results.

---

### Post by Tellisk on 2007-05-08
I encountered some errors when running Envy. I told it to continue anyway and it ran a little longer before finishing. It went on to reconfigure xorg.conf automatically for me and then told me to reboot, so I thought perhaps it had worked. But I still have no 3d acceleration and I can't access my nVidia Settings from Applications -> System Tools: "Failed to execute child process "/usr/bin/nvidia-settings" (No such file or directory)"

So I'm guessing it didn't work after all.

---

### Post by Tellisk on 2007-05-08
Ok here's the error:

Build of the package nvidia-kernel-source failed! How do you wish to proceed?

and when I select "VIEW    Examine the build log file," I get the utterly useless

"Build log starting, file:
/var/cache/modass/nividia-kernel-source.buildlog.2.6.21-15-386.1178667304
Date: Tue, 08 May 2007 19:35:04 -0400"

So I thought perhaps that file had some information, but when I opened it, it only said the exact same thing.

If I hit "Continue," it tells me "Pakcage nvidia-kernel-source was not build succesfully," blah blah blah.

I'm getting frustrated, but I do appreciate all the help and ideas so far.

---

### Post by Tellisk on 2007-05-09
Alright I think what I'm going to do is put my 6.10 cd in and burn it all down, start from scratch.

It's rather a pain, so I'm going to give it a little while's thought before I go through with it.

---

### Post by anachreon_ on 2007-05-09
Tellisk, did you check on the nvidia-xconfig package?  I had the same error finishing install because of that package.

---

### Post by tseliot on 2007-05-09
> **Tellisk said:**
> Ok, here is the output from the last step:

```

The following NEW packages will be installed:
  linux-restricted-modules-2.6.20-15-386 nvidia-glx-new 
  nvidia-kernel-common 
0 packages upgraded, 3 newly installed, 0 to remove and 1 not upgraded.
Need to get 21.2MB of archives. After unpacking 57.9MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 http://archive.ubuntu.com feisty/restricted nvidia-kernel-common 20051028+1ubuntu7 [5176B]
Get:2 http://archive.ubuntu.com feisty/restricted linux-restricted-modules-2.6.20-15-386 2.6.20.5-15.20 [16.3MB]
Get:3 http://archive.ubuntu.com feisty/restricted nvidia-glx-new 1.0.9755+2.6.20.5-15.20 [4833kB]
Fetched 21.2MB in 2m9s (163kB/s)                                                
Selecting previously deselected package nvidia-kernel-common.
(Reading database ... 142728 files and directories currently installed.)
Unpacking nvidia-kernel-common (from .../nvidia-kernel-common_20051028+1ubuntu7_all.deb) ...
Selecting previously deselected package linux-restricted-modules-2.6.20-15-386.
Unpacking linux-restricted-modules-2.6.20-15-386 (from .../linux-restricted-modules-2.6.20-15-386_2.6.20.5-15.20_i386.deb) ...
Unpacking nvidia-glx-new (from .../nvidia-glx-new_1.0.9755+2.6.20.5-15.20_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-new' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx'
dpkg: error processing /var/cache/apt/archives/nvidia-glx-new_1.0.9755+2.6.20.5-15.20_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-new_1.0.9755+2.6.20.5-15.20_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up nvidia-kernel-common (20051028+1ubuntu7) ...

Setting up linux-restricted-modules-2.6.20-15-386 (2.6.20.5-15.20) ...


```
Envy won't work if there is a mess with libraries.


Type:
```
sudo apt-get install -f
```

then:
```
sudo aptitude purge xorg-driver-fglrx nvidia-glx-new
```

then:
```
sudo apt-get install nvidia-glx-new
```

---

