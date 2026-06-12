---
title: "OSS screwed synaptic!"
date: 2006-11-04
forum: Multimedia &amp; Video
---

### Post by Echo35 on 2006-11-04
I attempted to install OSS from the .deb file off the website, only to have it fail. Now, whenever I try to open synaptic, I get this error:

E: The package oss-linux-regparm needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

Then, it won't let me view any files nor will it let me get updates. I can't even view anything that has been installed in synaptic. This is urgent as I can't update at all! Please help!

---

### Post by FyreBrand on 2006-11-04
Did you get the install packages from Opensound/4Front Technologies?  If you Google that package (oss-linux-regparm) the package shows up from their site.  It's an RPM though and not a deb.  You could try installing it from their site.

Another option would be to use the terminal and remove the package that way using aptitude or apt-get.

---

### Post by Echo35 on 2006-11-04
Yes, it's a .deb, I checked. I tried removing it already:

$ sudo apt-get remove oss-linux-regparm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package oss-linux-regparm needs to be reinstalled, but I can't find an archive for it.

Same exact error when I do *anything* with dpkg or apt or synaptic or any package manager I own.

---

### Post by FyreBrand on 2006-11-04
Well I'm reading through the dpkg man pages.  Here is something important about the flag that says reinstall is required
[quote=dpkg man page] reinst-required
              A  package  marked  reinst-required  is  broken  and  requires reinstallation. These packages cannot be removed, unless forced with option
              --force-remove-reinstreq.[/quote]So I don't think you should necessarily force a removal at this point mostly because I don't know what the consequences of that would be.  I think what you should do is try reinstalling that with dpkg and see what happens.

First make sure you have the right .deb from the OSS site.  Did you download the i386 regparm deb?

Then does dpkg let you reinstall it?

I did a little more searching and found that the Ubuntu Kernel didn't have regparm set, at least not when the thread was written.  I did the following command on my machine to see what I would get:
```
cat /boot/config-2.6.17-10-generic | grep REGP
``` and I got this: CONFIG_REGPARM=y
So it appears that regparm is now set in the Kernel (too bad I don't really understand what that means yet).

Another question I have is why you are using the OSS instead of ALSA?  I'm not trying to pry here but ALSA seems so much easier to install than OSS.

---

### Post by az on 2006-11-04
This is why you should avoid installing packages from non-ubuntu sources.

The package manager is telling you that it cannot do what you ask.  Probably, the package is partially installed and the removeal scripts are not installed yet.  You need to install the package properly to be able to remove it.

---

### Post by Echo35 on 2006-11-04
> **FyreBrand said:**
> Well I'm reading through the dpkg man pages.  Here is something important about the flag that says reinstall is required
So I don't think you should necessarily force a removal at this point mostly because I don't know what the consequences of that would be.  I think what you should do is try reinstalling that with dpkg and see what happens.

First make sure you have the right .deb from the OSS site.  Did you download the i386 regparm deb?

Then does dpkg let you reinstall it?

I did a little more searching and found that the Ubuntu Kernel didn't have regparm set, at least not when the thread was written.  I did the following command on my machine to see what I would get:
```
cat /boot/config-2.6.17-10-generic | grep REGP
``` and I got this: CONFIG_REGPARM=y
So it appears that regparm is now set in the Kernel (too bad I don't really understand what that means yet).

Another question I have is why you are using the OSS instead of ALSA?  I'm not trying to pry here but ALSA seems so much easier to install than OSS.

Ah, but I can't install it either. Same message no matter how I invoke any package manager. Even gdebi.

EDIT: I already have ASLA, it's just Doom likes OSS better so I tried it out and now look what happened!

---

### Post by Echo35 on 2006-11-05
$ sudo dpkg -i oss-linux-regparm_v4.0rc2-177_i386.deb
(Reading database ... 136797 files and directories currently installed.)
Preparing to replace oss-linux-regparm v4.0rc2-177 (using oss-linux-regparm_v4.0rc2-177_i386.deb) ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: error processing oss-linux-regparm_v4.0rc2-177_i386.deb (--install):
 subprocess new pre-removal script returned error exit status 2
Building OSS Modules for Linux-unknown 2.6.17-10-386
cd: 3: can't cd to /usr/lib/oss/build
sh: Can't open install.sh
Starting Open Sound System
/usr/sbin/soundon: 18: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
cat: /usr/lib/oss/version.dat: No such file or directory
/usr/sbin/soundon: 19: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 21: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 23: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 29: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 29: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 36: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
No /usr/lib/oss/etc/installed_drivers - cannot continue
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
 oss-linux-regparm_v4.0rc2-177_i386.deb

Seems like I'm close, but what's wrong? Sorry for being such a pain but this is really quite odd.

---

### Post by blackcoatman on 2006-11-15
I was having the same problem and I managed to find a way around. As the dpkg message says, there are some files and folders missing. So... what i did was manually extract the .deb file (there should be a way for the rpm too) and there were 2 tar.gz in it. I only need to extract the "data" one. Then I had an "etc" and a "usr" folder with all the oss files. So, I copied the contents to the corresponding system "etc" and "usr" folders, tried dpkg --remove oss-linux and voila! it was sweetly removed, and synaptic is running again. To copy the files as I said, do:

```
sudo cp -r /the path you extracted data/etc /

sudo cp -r /the path you extracted data/usr /

dpkg --remove oss-linux
```

As an example, my line was like that (allready as root):

```
cp -r '/home/bcman/Desktop/oss-linux_v4.0rc2-177_i386.deb_FILES/data.tar.gz_FILES/usr' /
```

That's all :)

---

