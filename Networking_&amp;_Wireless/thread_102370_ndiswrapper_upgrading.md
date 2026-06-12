---
title: "ndiswrapper upgrading"
date: 2005-12-11
forum: Networking &amp; Wireless
---

### Post by Britten on 2005-12-11
anytime i upgrade ndiswrapper it will not work anymore... infact... i have to install ndiswrapper 1.1 for it to work after reboot... if i install 1.5 it will work.. but then  when i add ndiswrapper to the modules file and reboot it gives me version errors... so i have to install 1.1.... any ideas on what i am doing wrong?

---

### Post by az on 2005-12-11
The newest version of ndiswrapper always uses the newest version of the INF file.  You may need to update your windows driver.  

You also need to have matching versions of the ndiswrapper module (in the kernel) and ndiswrapper-utils (the seperate package)

---

### Post by Britten on 2005-12-11
please explain to me how i get the correct version in the kernel

---

### Post by az on 2005-12-12
Ndiswrapper is comprised of the module and the userspace tool.  

The version of ndiswrapper that ships with ubuntu has the module as part of the kernel.  You do not need to install a seperate module package.  To make ndiswrapper work, you install the ndiswrapper-utils package for the userspace tool.

Some people compile a different version of ndiswrapper to try to gete it to work.  In doing so, they create a different version of the ndiswrapper-utils.  If you have tried to install one of these custom packages, and would like to go back and use the stock version that came with your kernel, be sure to remove the custom modules and make sure that you are using the original ndiswrapper module with the version of the ndiswrapper-utils package that comes with the distro.

---

### Post by Britten on 2005-12-12
ok.... please explain in noob talk... how do i use the ndiswrapper-utils that come with the distro? i have always just downloaded the newest version and compiled...

---

### Post by TrinitronX on 2005-12-12
So is there any way of getting the newer version of ndiswrapper installed, perhaps by removing the already-included kernel modules or by compiling a custom kernel?
The one that ships with ubuntu has never worked correctly for me at all, it always gives memory errors about the windows driver allocating too much memory or something.  The only way my card works is with the pre-installed madwifi drivers.
I want my wireless card to support WPA2, and so I would need to either figure out how to get madwifi to do that right, or get the new version of ndiswrapper installed correctly and then install my windows drivers (which work perfectly in windows to support WPA2).
Any ideas/advice on what route to take?

---

### Post by Lambert on 2005-12-12
I have not done this so somebody correct anything I'm missing.

1. unload the module from the kernel
```
sudo modprobe -r ndiswrapper
``` 
2. uninstall the driver
```
sudo ndiswrapper -e driver
``` 
3. Uninstall ndiswrapper. Instructions [here]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Uninstall") 

4. Install newest ndiswrapper witht [these]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation") instructions

You need to install a package build-essentails from the repositories to compile a program

---

### Post by az on 2005-12-12
[QUOTE=TrinitronX]So is there any way of getting the newer version of ndiswrapper installed, perhaps by removing the already-included kernel modules or by compiling a custom kernel?[/QUOTE]

Yes, but my point is that you often do not need to.  wiki.ubuntu.com/UserDocumentation - look at ndiswrapper)

"ok.... please explain in noob talk... how do i use the ndiswrapper-utils that come with the distro? i"

Well, first of all, remove any other version you have installed by compiling.   Then, make sure that you have the stock kernel modul by reinstalling your kernel.

sudo apt-get install --reinstall linux-image-2.6.12-9-386 (or 686 or k7 or whatever)

then install the ndiswrapper-utils package

sudo apt-get install ndiswrapper-utils

You are done.  You can also just use synaptic to reinstall the kernel and install ndiswrapper-utils (version 1.1-4ubuntu2).

---

### Post by TrinitronX on 2005-12-12
Hmm... I'm trying to install the pre-included ndiswrapper, but when I try to remove the module from the kernel, it seems it doesn't want to let go of it for some reason.
Here's what I did:
```

trinitronx@Arcturus:~/src/ndiswrapper-1.7$ sudo make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /sbin/loadndisdriver
removing /usr/sbin/ndiswrapper
removing /lib/modules/2.6.12.121005/kernel/drivers/net/ndiswrapper
/bin/rm: cannot remove `/lib/modules/2.6.12.121005/kernel/drivers/net/ndiswrapper': Is a directory
removing /lib/modules/2.6.12.121005/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
removing /lib/modules/2.6.12.121005/misc/ndiswrapper.ko
trinitronx@Arcturus:~/src/ndiswrapper-1.7$ modprobe -l | grep ndis
/lib/modules/2.6.12.121005/misc/ndiswrapper.ko
/lib/modules/2.6.12.121005/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
trinitronx@Arcturus:~/src/ndiswrapper-1.7$ sudo modprobe -r ndiswrapper
trinitronx@Arcturus:~/src/ndiswrapper-1.7$ modprobe -l | grep ndis
/lib/modules/2.6.12.121005/misc/ndiswrapper.ko
/lib/modules/2.6.12.121005/kernel/drivers/net/ndiswrapper/ndiswrapper.ko

```

EDIT: just tried doing another 'make uninstall' like the uninstall guide recommends, and got this:
```

NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /lib/modules/2.6.12.121005/kernel/drivers/net/ndiswrapper
/bin/rm: cannot remove `/lib/modules/2.6.12.121005/kernel/drivers/net/ndiswrapper': Is a directory
make: *** [uninstall] Error 1

```

---

### Post by mlomker on 2005-12-12
[QUOTE=Britten]ok.... please explain in noob talk... how do i use the ndiswrapper-utils that come with the distro? i have always just downloaded the newest version and compiled...[/QUOTE]

Yup, they changed things in Breezy.  There's a package called linux-restricted-modules and if you try overwrite the kernel's version of ndiswrapper.ko it'll just copy back the older version once you reboot.  You have to uninstall that package in order to upgrade any module that's a part of the package.  The problem is that a lot of video drivers, wireless drivers, etc are a part of that package.  You have to compile all of them that you need manually before removing the package.

My ATI [video driver how-to's]("http://ubuntuforums.org/showthread.php?t=78466") walk through how to remove it for that reason.

---

### Post by TrinitronX on 2005-12-12
[QUOTE=mlomker]Yup, they changed things in Breezy.  There's a package called linux-restricted-modules and if you try overwrite the kernel's version of ndiswrapper.ko it'll just copy back the older version once you reboot.  You have to uninstall that package in order to upgrade any module that's a part of the package.  The problem is that a lot of video drivers, wireless drivers, etc are a part of that package.  You have to compile all of them that you need manually before removing the package.

My ATI [video driver how-to's]("http://ubuntuforums.org/showthread.php?t=78466") walk through how to remove it for that reason.[/QUOTE]

I have followed your guide, and want to see if I can get the new version of ndiswrapper installed.  Is there a way to use module-assistant to make a package and install it from the new ndiswrapper source?  Also, last time I tried installing a new ndiswrapper version (before following your guide and building a new kernel) I got some errors about version incompatabilities.  Was this due to the new ndiswrapper module not being sync'ed up with the ndiswrapper utilities?

---

### Post by mlomker on 2005-12-12
[QUOTE=TrinitronX]Is there a way to use module-assistant to make a package and install it from the new ndiswrapper source?[/QUOTE]

There are instructions on the bottom of the how-to for the source that is in the repos.  The source that you get from elsewhere won't be packaged to use it...have to do the ./configure, make, make install routine.

> Was this due to the new ndiswrapper module not being sync'ed up with the ndiswrapper utilities?

Probably, but I don't use ndiswrapper so I can't say for certain.

---

### Post by az on 2005-12-12
Ndiswrapper is GPLed and is part of the linux-image package, not linux-restricted-modules.

I seem to remember that the ubuntu devs put the precompiled ndiswrapper module in 
/lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper
/lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko

while the ndiswrapper source package puts it in
/lib/modules/2.6.12-9-386/kernel/drivers/misc

I have not compiled a version of ndiswrapper in a while, but I remember than when I did it, I had two ndiswrapper modules there and the kernel would use the first one it bumped into (/lib/modules/2.6.12-9-386/kernel/drivers/misc)

Clever.

It would be interesting to see if it still works that way if you omitted this step:
QUOTE:

"5. By default, the rules file that is responsible for specifying Debian packaging parameters specifies an install directory different from where Ubuntu keeps the same module. I adjusted by rules file to install in the proper place like so

cd /usr/src/ndiswrapper-1.1
sed -e "s/misc/kernel\/drivers\/net\/ndiswrapper/g" debian/rules > debian/temp
mv debian/temp debian/rules"

found here:
[https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto)

Anyway, if you use the wrong ndiswrapper-utils for the module version, it probably will not work.

Is *everyone* now confused?

Helpful commands:

locate ndiswrapper
dmesg|grep ndiswrapper
dpkg -l|grep ndiswrapper

---

### Post by mlomker on 2005-12-12
[QUOTE=azz]Ndiswrapper is GPLed and is part of the linux-image package, not linux-restricted-modules.
[/QUOTE]

You're mistaken--it's in both.  A search using apt-file would quickly confirm that.  

It's the one in linux-restricted that causes the newer driver to be overwritten at every boot--the one in linux-image is static.  The linux-restricted-modules-common script causes that to occur.  I don't know why they created that beast but it makes some maintenance tasks a real pain.

---

### Post by az on 2005-12-12
emma@ubuntu1:~$ dpkg -L linux-restricted-modules-2.6.12-9-386|grep ndiswrapper
emma@ubuntu1:~$

Not there.

also:

[http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=ndiswrapper.ko&searchmode=searchfiles&case=insensitive&version=breezy&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=ndiswrapper.ko&searchmode=searchfiles&case=insensitive&version=breezy&arch=i386)

---

### Post by mlomker on 2005-12-12
[QUOTE=azz]emma@ubuntu1:~$ dpkg -L linux-restricted-modules-2.6.12-9-386|grep ndiswrapper
emma@ubuntu1:~$

Not there.
[/quote]

I double-checked and I was mistaken.  I wonder why people were having trouble with my how-to, then?  Oh, well.

---

### Post by TrinitronX on 2005-12-12
Ok.. so far i've grabbed a copy of ndiswrapper-1.7 (source), and done a 'make uninstall' a bunch of times until the only thing listed was an error due to a directory not being able to be removed.
So, I went into my /lib/modules/<kernel version> folder, and looked around for those folders/files that still were there.  I just removed those, and now I'm able to do this:
```

trinitronx@Arcturus:~$ sudo modprobe -r ndiswrapper
trinitronx@Arcturus:~$ modprobe -l | grep ndiswrapper
/lib/modules/2.6.12.121005/misc/ndiswrapper.ko
/lib/modules/2.6.12.121005/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
trinitronx@Arcturus:~$ ls /lib/modules/2.6.12.121005/misc/
fglrx.ko
trinitronx@Arcturus:~$ ls /lib/modules/2.6.12.121005/kernel/drivers/net/ndiswrapper
ls: /lib/modules/2.6.12.121005/kernel/drivers/net/ndiswrapper: No such file or directory

```

So.. as you can see.. the ndiswrapper.ko files do not exist in my kernel's module folder right now, but for some reason they're still loaded in the kernel.  I'm going to do a reboot now and see if they disappear from modprobe.  Hopefully none of this stuff messes up my being able to use the madwifi drivers still.. otherwise I'll have to boot my older kernel to come back and post my findings.

EDIT: ok.. after rebooting, and doing another 'sudo depmod', when I use 'modprobe -l | grep ndiswrapper', it returns nothing.  I also went into synaptic and uninstalled: ndisgtk, ndiswrapper-utils, ndiswrapper, and ndiswrapper-source.  Now I should be ready to compile the new ndiswrapper.  From what I understand, compiling this new version will also install the new utilities?  Also, will there be any conflicts with the old wireless-tools package?

---

### Post by Britten on 2005-12-12
well im confused as all get out... but if i use ndiswrapper 1.1 it works.... so.... maybe i should just use it????

---

