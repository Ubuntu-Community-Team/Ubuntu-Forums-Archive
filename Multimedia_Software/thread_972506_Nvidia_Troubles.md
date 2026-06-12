---
title: "Nvidia Troubles"
date: 2008-11-05
forum: Multimedia Software
---

### Post by jus71n742 on 2008-11-05
I am having a tough time figuring out simply how to get the drivers to install.  I have tried most things that I can think of. Any assistance is greatly appreciated.

---

### Post by Ng Oon-Ee on 2008-11-05
What version of Ubuntu, Hardy or Intrepid?

Easiest way is to search in Synaptic for something called envyng. If you're in Hardy, install envyng-gtk for a GUI, you can then run it from the menus.

If you're in Intrepid, the GTK has not been updated, so install envyng-core, then open up a terminal and type

```
envyng -t
```

To open up envyng in textual mode. Follow the on-screen instructions.

---

### Post by jus71n742 on 2008-11-06
ok that almost worked.  I don't think envyng cam get the updated drivers for my card
Nvidia 9800 GTX+

---

### Post by Ng Oon-Ee on 2008-11-07
Just a note, when asking for help here, it would be helpful if you provided as much detail as needed, concerning what exactly the problem is, what exactly you've tried to do, what was wrong with what you tried to do, etc...

"that almost worked" is quite hard for me to decipher, did you get an error while downloading it? Did running it give you an error?

When using envyng I normally prefer to manually select the specific driver/version to install, for your (very up-to-date) card I'd select NVidia at the first prompt and the latest version (177.* I believe).

Also, a quick search of the forums may help you more. I'm pretty sure lots of people have ignored your thread, since it doesn't provide much (any) information on your specific problem and also since there's been many threads on this issue.

---

### Post by jus71n742 on 2008-11-07
Yes I realized that and typed it in a hurry.  I have figured out a way to do it that will work ....only problem is the I need to disable X and I have no idea how to since telinit 3 and init 3 both didn't work

---

### Post by dabl on 2008-11-07
> **jus71n742 said:**
> 

I need to disable X and I have no idea how to 



1. Ctrl-Alt-F1, log in to tty1 console.

2. ```
sudo /etc/init.d/gdm stop
```

or "kdm stop" for kubuntu

3. When you're done installing the Nvidia driver, run ```
sudo nvidia-xconfig
``` to write a new xorg.conf file

4. Then ```
sudo /etc/init.d/gdm start
```

or just ```
startx
``` from the $ prompt.

---

### Post by jus71n742 on 2008-11-07
OK thanks again for that working.... Now I am trying to figure out how to get Nvidia to see my additional monitors (3) I tried changing the number of actual desktops but it did nothing.  
So any suggestions for that would also be greatly appreciated

---

### Post by jus71n742 on 2008-11-24
OK I am uterlly amazed right now....I followed what you have told me.
It is failing to work....gdm won't stop 
I input the command for it to stop (no typo since I copied and pasted) I get GNOME stoping....
then I have $ again
then running sudo sh driver file name.run

I get this error
```

 Installation has failed.  Please see the file
         '/var/log/nvidia-installer.log' for details.  You may find            
         suggestions on fixing installation problems in the README available   
         on the Linux driver download page at www.nvidia.com.

```

really confused since I had this working less than 2 weeks ago
( had to reinstall windows a few times so I have to do it all again

---

### Post by pgatrick on 2008-11-24
> **jus71n742 said:**
> OK thanks again for that working.... Now I am trying to figure out how to get Nvidia to see my additional monitors (3) I tried changing the number of actual desktops but it did nothing.  
So any suggestions for that would also be greatly appreciated

You should be able to handle that through the NVIDIA-xserver-settings program, if that doesn't work you can manually edit your xorg.conf, read the man file for it for more info on that.

Of course that doesn't matter if you can't get the driver installed.
Could you post the installer error log?
Also, do you have all the tools installed necessary for running the driver?
(build-eessentials I think the package is called, has gcc, the kernel header files, etc.)

---

### Post by jus71n742 on 2008-11-24
I figured out how to get the monitors going once I get the drivers installed.

Thats all I need right now to get the drivers back on since Windows threw a fit so to speak and I had to reinstall about 324 times.

I need to figure out how to get 
```

sudo apt-get install libc6-dev-amd64

```
after running
```

sudo apt-get update

```

still can't find the package
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libc6-dev-amd64

```

---

### Post by pgatrick on 2008-11-25
> **jus71n742 said:**
> I figured out how to get the monitors going once I get the drivers installed.

Thats all I need right now to get the drivers back on since Windows threw a fit so to speak and I had to reinstall about 324 times.

I need to figure out how to get 
```

sudo apt-get install libc6-dev-amd64

```
after running
```

sudo apt-get update

```

still can't find the package
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libc6-dev-amd64

```
 I'm not on ubuntu so I can't say if libc6-dev-amd64 is in the repositories, but if it is I wouldn't think it would have the amd64 bit on there since everything is the 64bit version if you're using a 64bit distro. Try 
```
sudo apt-get install libc6-dev
```
And if it still can't find it, run 
```
apt-cache search libc6
```
 and see what it turns up, you might just have the name of the package a bit wrong.

---

### Post by jus71n742 on 2008-11-25
I ran that and I get the following
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libc6-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
justin@napalm-desktop:~$ sudo apt-cache search libc6
libtext-iconv-perl - converts between character sets in Perl
debian-policy - Debian Policy Manual and related documents
libapt-rpm-pkg-libc6.7-6-2 - APT for RPM library
libcompfaceg1 - Compress/decompress images for mailheaders, libc6 runtime
libcompfaceg1-dev - Compress/decompress images for mailheaders, libc6 devel
manpages-ja-dev - Japanese version of the manual pages (for developers)
manpages-pt-dev - Portuguese Versions of the Manual Pages
apt - Advanced front-end for dpkg
apt-utils - APT utility programs
libc6 - GNU C Library: Shared libraries
libc6-dbg - GNU C Library: Libraries with debugging symbols
libc6-dev - GNU C Library: Development Libraries and Header Files
libc6-dev-i386 - GNU C Library: 32bit development libraries for AMD64
libc6-i386 - GNU C Library: 32bit shared libraries for AMD64
libc6-pic - GNU C Library: PIC archive library
libc6-prof - GNU C Library: Profiling Libraries

```
Now it refuses to run in a high graphics mode which is odd and will not allow me to configure the xnvidia file

---

### Post by pgatrick on 2008-11-26
Well you already have libc6-dev installed, so that's not the prooblem. No way to know what went wrong though without the nvidia installers error log.
```
/var/log/nvidia-installer.log
```

---

