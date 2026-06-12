---
title: "Help with kernel problem building lirc"
date: 2010-04-26
forum: Mythbuntu
---

### Post by Lepy on 2010-04-26
I have a laptop frontend with a Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) running 10.04 and .23.

I have 3 kernels installed on the machine:
2.6.31-21-generic
2.6.32-21-generic
2.6.33-020633-generic

32 and 33 have some bad bugs, notably with movement on the screen, the display flickers and jerks randomly, and when playing a video from the frontend, the screen goes blank with this error showing up in the logs:
```
[drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
```

These bugs are on launchpad, but 31 is working perfectly on the machine, aside from the remote. The remote did not work on 32 either, but building lirc from the svn completes successfully and results in a functioning remote. 

When I try to build lirc on 31, everything works fine until configure looks for the kernel sources (which are installed)
```
:~/sources/lirc$ ./configure.sh
configure: error: *** you need to have the Linux kernel source installed
	for this driver

```

I guess this is a problem because of the upgrade to Lucid. I get these errors when booting 31:
```
mount: mounting none on /dev failed: No such device
chroot: cannot execute /etc/apparmor/initrmfs: No such file or dir
```

Are the kernel sources not being linked appropriately? Hopefully a later kernel will fix the jerky/hang problems, but for now, 31 works 100% besides this lirc build error. Any idea how I can get the source built? Thanks!

---

### Post by pu15e on 2010-04-26
Assuming you do actually have the sources installed, do you also have the -headers package installed for the appropriate kernel? ;-)

Cheers,
 Mattt.

---

### Post by Lepy on 2010-04-26
Maybe I don't:

```
$ dpkg --get-selections linux-*
linux-firmware					install
linux-generic					install
linux-headers-2.6.32-21				install
linux-headers-2.6.32-21-386			install
linux-headers-2.6.32-21-generic			install
linux-headers-2.6.32-21-generic-pae		install
linux-headers-2.6.33-020633			install
linux-headers-2.6.33-020633-generic		install
linux-headers-386				install
linux-headers-generic				install
linux-image-2.6.31-14-generic			deinstall
linux-image-2.6.31-17-generic			deinstall
linux-image-2.6.31-18-generic			deinstall
linux-image-2.6.31-19-generic			deinstall
linux-image-2.6.31-20-generic			deinstall
linux-image-2.6.31-21-generic			install
linux-image-2.6.32-21-generic			install
linux-image-2.6.33-020633-generic		install
linux-image-generic				install
linux-libc-dev					install
linux-sound-base				install
linux-source					install
linux-source-2.6.32				install

```

Initially, I had problems with building lirc on 31, so I upgraded to 32 and got all the other problems; however, config and build worked on the first try and the remote started working.

Only 31 header package available is "linux-headers-2.6.31-10-rt"
I'll give this a shot.

---

### Post by Lepy on 2010-04-26
You were right. Headers were the first thing I checked when I was  trouble-shooting a few days ago, but since it compiled under 32 after trying 31, I got wrapped up in solving the 32 bugs.

Installing linux-headers-2.6.31-10-rt did not work, so...I got all the latest 31 packages from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
Installed, compiled, and now have the remote working.

Thanks!

---

