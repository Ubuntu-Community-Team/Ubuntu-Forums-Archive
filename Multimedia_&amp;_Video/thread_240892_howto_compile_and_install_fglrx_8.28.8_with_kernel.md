---
title: "howto compile and install fglrx 8.28.8 with kernel &gt;= 2.6.17"
date: 2006-08-21
forum: Multimedia &amp; Video
---

### Post by zasf on 2006-08-21
```
# compile and install your own kernel
cd ~
mkdir ati
cd ati
# download the latest ati installer
wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.28.8.run
chmod +x ati-driver-installer-8.28.8.run
LANG=C LC_ALL=C ./ati-driver-installer-8.28.8.run --buildpkg Ubuntu/dapper
# install the source (tar.bz2 file will be placed in /usr/src)
sudo dpkg -i fglrx-kernel-source_8.28.8-1_i386.deb
cd /usr/src
# untar fglrx.tar.bz2 (will be unzipped in /usr/src/modules/fglrx)
sudo tar xvf fglrx.tar.bz2
# patch
cd /usr/src/modules/fglrx
# download attached patch
cat fglrx.patch | patch -p0
# make sure that /usr/src/linux point to the right kernel
cd /usr/src/linux
[COLOR="Red"]# you may need to do 'make scripts' if it complains about modpost[/COLOR]
# substitute '-z2' with your own, debs will be placed in /usr/src
sudo make-kpkg --append-to-version=-z2 modules_image
cd /usr/src
# install the kernel module and xorg driver
sudo dpkg -i ~/ati/xorg-driver-fglrx_8.28.8-1_i386.deb
sudo dpkg -i fglrx-kernel-2.6.17-mm6-z_8.28.8-1+1_i386.deb
# reboot and check with
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X700 Generic
OpenGL version string: 2.0.6011 (8.28.8)
```

---

### Post by cocoapunk on 2006-08-26
Thanks for this great howto :)

Apparently, I'm making the wrong kernel package with make-kpkg. I was wondering what to do about that. fglrx is working fine ($: dmesg|grep fglrx
[17179598.424000] [fglrx] module loaded - fglrx 8.28.8 [Aug 17 2007] on minor 0) but I'm getting this error in Xorg (/var/log/Xorg.0.log):

(EE) module ABI major version (0) doesn't match the server's version (1)
(EE) Failed to load module "fglrx" (module requirement mismatch, 0)
(EE) No drivers available.

I know this is because it can't find the patch

When i do make-kpkg modules_image it works fine (I do notice a few error lines from firegl_control.c, which is already patched), but apparently I'm messing up the kernel type

Here is my uname -a:
Linux 2.6.17-6-686 #2 SMP Fri Aug 11 22:09:15 UTC 2006 i686 GNU/Linux

/proc/version:
Linux version 2.6.17-6-686 (root@rothera) (gcc version 4.1.2 20060716) ... (Ubuntu 4.1.1-9ubuntu1)) #2 SMP Fri Aug 11...

My main questions are:

How can i get the -z2 kernel? (i search repos.)
and/or 
How do i do make-kpkg for my kernel?
and finally
Is it possible that there is a system specific problem with the patch and my system? (missing libs, etc.)

Thanks a lot :)

Edit: 

The deb i get at the end is : fglrx-kernel-2.6.17-6-686_8.28.8-1+2.6.17-6-686-10.00.Custom_i386.deb

---

### Post by zasf on 2006-08-27
> **cocoapunk said:**
> Thanks for this great howto :)

Apparently, I'm making the wrong kernel package with make-kpkg. I was wondering what to do about that. fglrx is working fine ($: dmesg|grep fglrx
[17179598.424000] [fglrx] module loaded - fglrx 8.28.8 [Aug 17 2007] on minor 0)

hum ok, so the module gets loaded, as you say it compiled fine and it works

> **cocoapunk said:**
> but I'm getting this error in Xorg (/var/log/Xorg.0.log):

(EE) module ABI major version (0) doesn't match the server's version (1)
(EE) Failed to load module "fglrx" (module requirement mismatch, 0)
(EE) No drivers available.


it says 'no drivers available', did you dpkg -i xorg-driver-fglrx_8.28.8-1_i386.deb? it is made by the ati installer like fglrx-kernel-source_8.28.8-1_i386.deb

> **cocoapunk said:**
> I know this is because it can't find the patch

When i do make-kpkg modules_image it works fine (I do notice a few error lines from firegl_control.c, which is already patched), but apparently I'm messing up the kernel type

Here is my uname -a:
Linux 2.6.17-6-686 #2 SMP Fri Aug 11 22:09:15 UTC 2006 i686 GNU/Linux

/proc/version:
Linux version 2.6.17-6-686 (root@rothera) (gcc version 4.1.2 20060716) ... (Ubuntu 4.1.1-9ubuntu1)) #2 SMP Fri Aug 11...

My main questions are:

How can i get the -z2 kernel? (i search repos.)
and/or 
How do i do make-kpkg for my kernel?
and finally
Is it possible that there is a system specific problem with the patch and my system? (missing libs, etc.)

Thanks a lot :)

Edit: 

The deb i get at the end is : fglrx-kernel-2.6.17-6-686_8.28.8-1+2.6.17-6-686-10.00.Custom_i386.deb

the deb you get should be right, you compiled it for you own kernel I suppose '2.6.17-6-686', the '-z2' is just a suffix to personalize your kernel.. I use zY, where Y is the version, but you might want to use your own or nothing (you choosed -686 I guess).

Try to do
```
dpkg -i xorg-driver-fglrx_8.28.8-1_i386.deb
```

you should be fine.

Don't forget to let me know if it worked

---

### Post by mcl1150 on 2008-05-05
procedure works well until I get to step 5:

LANG=C LC_ALL=C ./ati-driver-installer-8.28.8.run --buildpkg Ubuntu/dapper

I am assuming that it is because it is building a package for the dapper release and I am using the hardy release of Ubuntu.

Any help on making this compile for Ubuntu 8.04 (hardy)?

Thanks in advance.

m.--

---

### Post by zasf on 2008-05-05
First of all, you should try to understand what you're typing and not just copy and paste. You're trying to make packages for a different version of Ubuntu.

Secondly, you should use a more recent guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

---

