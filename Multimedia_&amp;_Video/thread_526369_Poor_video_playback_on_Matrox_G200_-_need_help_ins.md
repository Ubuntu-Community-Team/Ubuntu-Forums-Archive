---
title: "Poor video playback on Matrox G200 - need help installing mga-vid"
date: 2007-08-15
forum: Multimedia &amp; Video
---

### Post by Orfeo-40 on 2007-08-15
Hi everyone - just joined up!

After many years running SuSE I've installed Kubuntu Feisty and am very pleased I did. However, I do have a couple of problems: one been video playback. I've installed numerous codecs and can play back mpg, avi, DVD etc, but often have horizontal white lines flickering on the right hand side of the picture.

I'm using an old, I mean OLD, Matrox Mystique G200 AGP. I made some changes to my xorg.conf file having looked at my old SuSE install, but they made no difference and have reverted to original settings.

Exploring Adept I found "mga-vid-source". I've installed it, but in Adept it says:

[INDENT]This package just contain the sources needed to build the kernel module. To actually use it, you'll have to compile it to match your installed kernel. Refer to /usr/share/doc/mga-vid-source/README.Debian for information on how to do this.[/INDENT]

So I refer to the README, and I really don't understand what to do next, as I'm unfamiliar with kernel related matters. It sounds like I need to produce a deb package to install normally, but it must match my kernel version so needs to be build locally. The README.Debian instructs:

[INDENT]You can compile the module by untarring the mga-vid.tar.gz tarball you'll
find in /usr/src , and then entering the top-level kernel source directory
of the kernel you want to compile the module for, and issue the command:

 # fakeroot make-kpkg modules_image

module assistant does also work on this package

You should end up with a mga-vid-*.deb file in the parent directory, which
you can install as usual with 'dpkg -i'.

Obviously the kernel needs to support modules for the driver to work. ;-)[/INDENT]

I've untarred mga-vid.tar.gz in /usr/src. I ran uname -r to check my kernel version, and I think the "top-level kernel source directory" is /usr/src/linux-headers-2.6.20-16-generic, am I right?

But this is where I'm totally confused! If I run the fakeroot command here, how does the system know I want to do something with the mga-vid files? Do I need to move this folder, or its contents, somewhere?

Any help on what to do here would be much appreciated - even if it doesn't fix the video playback problem!

Thanks.

Andy

---

### Post by mzembe on 2007-08-15
You'll need the build-essential package and the header directory is not the kernel source although sometimes all you need is the kernel headers. Get the kernel source package too, you'll know you found it when you have to download a zillion megs.. you might need to make a symlink in the /usr/src directory like "ln -s linux-blah-blah-version linux " so you have a /usr/src/linux path to whichever version is current. 

root@feistytude:/home/deevnil# ls /usr/src/linux
arch       Debian.src.changelog  ipc              mm              scripts
block      Documentation         Kbuild           modules         security
conf.vars  drivers               kernel           net             sound
COPYING    firmware              kernel-versions  package-list    ubuntu
CREDITS    fs                    lib              README          usr
crypto     include               MAINTAINERS      README.Debian
debian     init                  Makefile         REPORTING-BUGS
root@feistytude:/home/deevnil# ls /usr/src/
linux  linux-source-2.6.20  linux-source-2.6.20.tar.bz2
root@feistytude:/home/deevnil# 

is what I have, note the 'linux' directory is just a symlink to linux-source-2.6.20 that userland scripts are more comfortable with. If I remember correctly, I had to " tar -xvjf linux-source-2.6.20.tar.bz2 " in the /usr/src directory after installing the kernel source with synaptic to actually have the source available and also note the absence of a kernel header directory (those are included with the source under /usr/src/linux/include - the script should be able to find them) it probably won't hurt to run : make mrproper;make headers_check in the linux directory but I'm not sure if it's necessary so just try to make the package first.
I know the nvidia has a nice script that works like it's supposed to, I never had any luck with ati working without fooling around with stuff... vmware is really touchy, etc. hopefully the mga script will see the kernel source and know what to do with it, run the uname stuff and get everything where it belongs.... if it compiles clean and creates a .deb that installs gracefully you may need to run depmod -a but for all I know that is no longer necessary or runs during the boot process or whatever.
But you may need more than just the headers, which is what you are describing. 
maybe those modules are already there and you just need to install proprietary codecs and make them available to th the media player (like vlc) It seems like the G200 and G400 stuff is pretty standard and ought to be going on already - do an lsmod and cat/var/log/Xorg.0.log and post it. Somebody could probably tell from that stuff if it's a driver or codec issue. I'm just wondering because SuSE always has the non-free codecs and firmwares, maybe the player is falling back to some less than optimal rendering strategy that isn't driver related? I dunno, I'm just bored and talking ****.

---

### Post by Orfeo-40 on 2007-08-16
Many thanks for the reply, Mzembe. I've had a play but am still pretty lost. I checked I had the build-essential package installed, and I had, and I added the kernel-source and untarred it in /usr/scr. A directory listing was identical to yours - which was a relief!

I left the mga-vid folder where it was at /usr/scr/modules

From within the /usr/scr/linux (symlink created as you suggested), I ran
[INDENT]# fakeroot make-kpkg modules_image[/INDENT]
as instructed in the README. The output received was:
[INDENT]exec debian/rules  DEBIAN_REVISION=2.6.20-16.29  modules_image
====== making target .config [new prereqs: Makefile]======

test -f .config || test ! -f .config.save || \
                            cp -pf .config.save .config
test -f .config || test ! -f ./debian/Config/config.i686 || \
                            cp -pf ./debian/Config/config.i686 .config
test -f .config || test ! -f ./debian/config || \
                            cp -pf ./debian/config  .config
test -f .config || (echo "*** Need a config file .config" && false)
====== making .config because of Makefile ======

test -f .config || test ! -f .config.save || \
                            cp -pf .config.save .config
test -f .config || test ! -f .config || \
                            cp -pf .config .config
test -f .config || test ! -f ./debian/config || \
                            cp -pf ./debian/config  .config
test -f .config || (echo "*** Need a config file .config" && false)
echo "The UTS Release version in include/linux/version.h"; echo "     \"\" "; echo "does not match current version:"; echo "     \"2.6.20.3-ubuntu1\" "; echo "Please correct this."; exit 2
The UTS Release version in include/linux/version.h
     ""
does not match current version:
     "2.6.20.3-ubuntu1"
Please correct this.
make: *** [modules_image] Error 2[/INDENT]

Hmm, I can see this source is for Debian 2.6.20-16.29 by looking in the Debian.src.changelog (I'm learning as I go here!), so what is this current version of 2.6.20.6-ubuntu1 ? I couldn't find the location of the include/linux/version.h referred to.

Any pointers?

Andy

---

