---
title: "compile rtl8180. no rule to make target"
date: 2005-12-08
forum: Networking &amp; Wireless
---

### Post by ronaldor on 2005-12-08
Hi,
I'm trying to compile the driver for my wlan.
The instructions said that I should only type make in the directory.
After I install the build-essential, I could execute make, but the make give-me some erros such below:

realtek_rtl8180/rtl8180-0.21$ make
Makefile:8: /lib/modules/2.6.10-5-386/build/.config: No such file or directory
make: *** No rule to make target
`/lib/modules/2.6.10-5-386/build/.config'.

I read that I should install the kernel-source to solve the problem. I've installed this. I get it, run "dpkg -i ..." and after this "tar --bzip2 -xvf ....".
But the problem persists.

What can I do?

---

### Post by cwaldbieser on 2005-12-08
[QUOTE=ronaldor]Hi,
I'm trying to compile the driver for my wlan.
The instructions said that I should only type make in the directory.
After I install the build-essential, I could execute make, but the make give-me some erros such below:

realtek_rtl8180/rtl8180-0.21$ make
Makefile:8: /lib/modules/2.6.10-5-386/build/.config: No such file or directory
make: *** No rule to make target
`/lib/modules/2.6.10-5-386/build/.config'.

I read that I should install the kernel-source to solve the problem. I've installed this. I get it, run "dpkg -i ..." and after this "tar --bzip2 -xvf ....".
But the problem persists.

What can I do?[/QUOTE]

Does 
```

$ ls -al /lib/modules/2.6.10-5-386/build

```
show that .config actually exists now?

---

### Post by ronaldor on 2005-12-08
No, build doesn't exist.

---

### Post by cwaldbieser on 2005-12-08
[QUOTE=ronaldor]No, build doesn't exist.[/QUOTE]
Do you have a URL where you got the source package from?  Or is it in synaptic?  If you can point me to where you got it from, I would try to take a look at it and see if I could figure out what needs to be done.

---

### Post by ronaldor on 2005-12-08
Hi, I get it in this url: [http://packages.ubuntu.com/breezy/devel/linux-source-2.6.12](http://packages.ubuntu.com/breezy/devel/linux-source-2.6.12)

The real message is:
realtek_rtl8180/rtl8180-0.21$ make
Makefile:8: /lib/modules/2.6.10-5-386/build/.config: No such file or directory
make: *** No rule to make target
`/lib/modules/**2.6.12-9-386**/build/.config'.

I'm using Ubuntu 5.10.

---

### Post by cwaldbieser on 2005-12-08
[QUOTE=ronaldor]Hi, I get it in this url: [http://packages.ubuntu.com/breezy/devel/linux-source-2.6.12](http://packages.ubuntu.com/breezy/devel/linux-source-2.6.12)

The real message is:
realtek_rtl8180/rtl8180-0.21$ make
Makefile:8: /lib/modules/2.6.10-5-386/build/.config: No such file or directory
make: *** No rule to make target
`/lib/modules/**2.6.12-9-386**/build/.config'.

I'm using Ubuntu 5.10.[/QUOTE]
Sorry, I meant the URL for the realtek drivers.

---

### Post by ronaldor on 2005-12-08
I've got the last version on cvs.
[http://sourceforge.net/projects/rtl8180-sa2400](http://sourceforge.net/projects/rtl8180-sa2400)

---

### Post by ronaldor on 2005-12-08
I've tryed with the version 0.21, but the problem is the same.

---

### Post by cwaldbieser on 2005-12-08
[QUOTE=ronaldor]I've tryed with the version 0.21, but the problem is the same.[/QUOTE]
OK, I just tried with the one in sourceforge-- you need to get the binary .deb for the linux-headers-2.6.12-9-386 (not the source .deb), but even when I got those, there was a build error I got.
```

make -C /lib/modules/2.6.12-10-686/build SUBDIRS=/home/carl/downloads/rtl8180-0.21 MODVERDIR=/home/carl/downloads/rtl8180-0.21 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-686'
  CC [M]  /home/carl/downloads/rtl8180-0.21/r8180_core.o
/home/carl/downloads/rtl8180-0.21/r8180_core.c: In function `rtl8180_pci_probe':
/home/carl/downloads/rtl8180-0.21/r8180_core.c:3632: error: structure has no member named `slot_name'
make[2]: *** [/home/carl/downloads/rtl8180-0.21/r8180_core.o] Error 1
make[1]: *** [_module_/home/carl/downloads/rtl8180-0.21] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-686'
make: *** [2.6] Error 2

```

I will look and see if the manufacturer has anything more useful.  If not, I can try to see if I can figure out the error and correct it.

---

### Post by cwaldbieser on 2005-12-08
OK, the driver I pulled from realtek's site has the same error.  I will take a look and see if I can figure out what it is complaining about.

---

### Post by cwaldbieser on 2005-12-08
[QUOTE=ronaldor]I've tryed with the version 0.21, but the problem is the same.[/QUOTE]
OK, I figured out that the source code they are using is trying to compile against a version of the headers where one of the structs is slighlty different.  I am attachinging my modified file for you to try.  I changed line 3636 where a "pci_dev" structure was trying to access a "slots" member which apparently does not exist in my kerenl headers.

I will also try to get you the URL for the .deb you need for the linux headers.

---

### Post by cwaldbieser on 2005-12-08
[QUOTE=ronaldor]I've tryed with the version 0.21, but the problem is the same.[/QUOTE]
OK, I guess I really needed to know what kernel version you are using before I could get you the correct URL.  Here is an example:

[]("http://packages.ubuntu.com/breezy/devel/linux-headers-2.6.12-10-386")
If you go to the terminal and type
```

$ uname -a
Linux kepler 2.6.12-10-686 #1 Fri Nov 18 12:09:04 UTC 2005 i686 GNU/Linux

```
you will see something like the output I got.  The 2.6.12-10-686 is my kernel version.  Yours will probably be slightly different.  Anyway, that version number should match the linux-headers version number in the URL.  That will tell you which .deb to get and install.

I hope I wasn't too confusing with my explanations.

---

### Post by ronaldor on 2005-12-09
Hi the version that I'm using is this: 2.6.12-9-386
I'm using ubuntu 5.10 breezy.
I've downloaded the package linux-source-2.6.12 (2.6.12-10.24), and execute this commands:
dpkg -i linux-source-2.6.12_2.6.12-10.24_all.deb
After this, another file was created and I extract it.

Is this really necessary? Or It isn't necessary and the only thing that I should get was the linux-headers?

I don't understand some thing. My kernel version is 2.6.12-9-386, but the linux-source and linux-headers available in [http://packages.ubuntu.com/breezy/devel/](http://packages.ubuntu.com/breezy/devel/) has the version 2.6.12-10.24-386.  Should I get the version 2.6.12-9 or can I get this 2.6.12.10 ?

Why this gpl driver doesn't came installed in ubuntu ?

Is this files available on my ubuntu cdrom?

Thank you very much for help.

---

### Post by ronaldor on 2005-12-09
In the G:\pool\main\l\linux-source-2.6.12 directory of my ubuntu cdrom there are this files:
linux-headers-2.6.12-9-386_2.6.12-9.23_i386.deb
linux-headers-2.6.12-9_2.6.12-9.23_i386.deb

---

### Post by cwaldbieser on 2005-12-09
[QUOTE=ronaldor]In the G:\pool\main\l\linux-source-2.6.12 directory of my ubuntu cdrom there are this files:
linux-headers-2.6.12-9-386_2.6.12-9.23_i386.deb
linux-headers-2.6.12-9_2.6.12-9.23_i386.deb[/QUOTE]

You should only need the appropriate linux-headers package.  Since it looks like they are on your install CD, the easiest way to do that is to open up Synaptic and to put your install CD in the CDROM drive.  Then, search for "linux-header".  It will show you all the linux-header packages available, and you can just pick the one that matches your kernel version.  It will load this package from the CDROM and install it for you.

---

### Post by ronaldor on 2005-12-10
Hi,
I've removed the linux-source and installed the linux-header.
Now, it is complaining about gcc-3.4. But there isn't gcc-3.4 in my ubuntu cdrom.

Look some menssages:

/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found.
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found.

make[1]: gcc-3.4: command not found

---

### Post by cwaldbieser on 2005-12-10
[QUOTE=ronaldor]Hi,
I've removed the linux-source and installed the linux-header.
Now, it is complaining about gcc-3.4. But there isn't gcc-3.4 in my ubuntu cdrom.

Look some menssages:

/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found.
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found.

make[1]: gcc-3.4: command not found[/QUOTE]

Well, I have got the old linux-headers myself, and I told make to use  gcc3.4, so hopefully the following archive will have what you need in it.  You should just uncompress it and go in the directory and type:
```

$ sudo make install

```
and hopefully it will install the modules I pre-built for you and everything will work.  If not, you can try downloading the gcc3.4 packages via another computer, but that is a pain in my experience.

---

### Post by ronaldor on 2005-12-11
Ok, thank you very much.
I'll try it now.

---

