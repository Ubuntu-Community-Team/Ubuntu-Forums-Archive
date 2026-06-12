---
title: "Aircrack - kernel build error"
date: 2009-02-20
forum: Networking &amp; Wireless
---

### Post by mostofmonty on 2009-02-20
Hey all,

First post on forums, ive been trying to get aircrack-ng working with ubuntu 8.10 (2.6.27-11-generic) and found what looks to be the set of instructions im after at 


file:///media/disk/Ubuntu%20Stuff/AirCrack/index.php.htm

Get the tools and kernel source so you can recompile.
"sudo apt-get install kernel-package libncurses5-dev fakeroot wget bzip2 linux-source"

Go to your source directory and unpack the kernel source, and go into the source directory.
"cd /usr/src"
"sudo tar jxvf linux-source-2.6.27.tar.bz2"
"cd linux-source-2.6.27"

Copy your existing kernel configuration into the linux source folder. This allows you to keep your existing settings, but add in support for injection.
"sudo cp /boot/config-`uname -r` ./.config"

Take the 3 patched source files posted at the top and replace the ones in your linux source folder.
"sudo mv iwl-sta.c iwl-tx.c iwl-agn.c /usr/src/linux-source-2.6.27/drivers/net/wireless/iwlwifi"

Now go to the root directory of your linux source code (/usr/src/linux-source-2.6.27) and begin the build, now that you have put the 3 modified files in.
"cd /usr/src/linux-source-2.6.27"
"sudo make-kpkg clean"
"sudo fakeroot make-kpkg - -initrd - -append-to-version=-injection kernel_image kernel_headers"

The compile to rebuild the kernel will take a few minutes. Once it completes with hopefully no errors, you should see 2 packages that have been built.
linux-image-2.6.27.10-injection_2.6.27.10-injection-10.00.Custom_i386.deb
linux-headers-2.6.27.10-injection_2.6.27.10-injection-10.00.Custom_i386.deb

Install the new kernel and headers that you just compiled by using dpkg. This will add the new kernel automatically to your boot menu options.
"sudo dpkg -i linux-image-2.6.27.10-injection_2.6.27.10-injection-10.00.Custom_i386.deb"
"sudo spkg -i linux-headers-2.6.27.10-injection_2.6.27.10-injection-10.00.Custom_i386.deb"


now all the steps seem to complete without trouble up until the 
```

"sudo fakeroot make-kpkg - -initrd - -append-to-version=-injection kernel_image kernel_headers" 
```

command, i get the error (or problem?)

```
Error: Unknown target - Unknown target - 
use --targets to display help on valid targets.
```

im relatively new to linux, and have no idea what this output means, any help would be greatly appreciated,

mostofmonty

---

### Post by kevdog on 2009-02-21
Ive compiled aircrack from svn, however I only have experience in relation to broadcom chipsets and not intel.  It would look by the error message you are getting, that the command you are trying to use has been listed incorrectly.  The command is not complete.  I would suggest posting on the aircracking forums or on #aircrack and ask them what the correct command should be!

---

### Post by mostofmonty on 2009-02-25
Thanks kevdog, im glad it wasnt my error after all, was worried about that. For the meantime i am just using an external usb wireless key with the rt73 drivers... working well :D

still, would like to get the internal card injecting... ill see if i can find the right command...

thanks again

---

### Post by kevdog on 2009-02-25
Are you sure the syntax of this command is correct:
sudo fakeroot make-kpkg - -initrd - -append-to-version=-injection kernel_image kernel_headers

That looks suspicious to me!

---

### Post by Siph0n on 2009-02-25
Are you just trying to install aircrack-ng? If so you can get it from the repo's. It isn't a TOO out of date version.

Or why not just get it from svn?
```

sudo apt-get install subversion build-essential libssl-dev
```

Type from your home dir (or wherever u want to put aircrack-ng:
```
svn co http://trac.aircrack-ng.org/svn/trunk/ aircrack-ng
```

Than go into the aircrack-ng directory and type:
```
make
sudo make install
```

It is now installed.

Or from the website [http://www.aircrack-ng.org/doku.php?id=downloads](http://www.aircrack-ng.org/doku.php?id=downloads)
After you download it type:
```
sudo apt-get install build-essential libssl-dev
```

Than extract aircrack-ng-1.0-rc2.tar.gz to whereever you want (home dir)

Than go into that directory and type:
```
make
sudo make install

```
It is installed this way too.

---

### Post by iasenko on 2009-02-27
Hey I'm also stuck on this problem,you have to remove two spaces :

```

sudo fakeroot make-kpkg --initrd --append-to-version=-injection kernel_image kernel_headers


```
but I still receive error msg : 

```

@ubuntu:/usr/src/linux-source-2.6.27$ sudo fakeroot make-kpkg --initrd --append-to-version=-injection kernel_image kernel_headers exec debian/rules  DEBIAN_REVISION=2.6.27.13-injection-10.00.Custom  APPEND_TO_VERSION=-injection  INITRD=YES  kernel_image kernel_headers 
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 3: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator

====== making target CONFIG-common [new prereqs: testdir]======

====== making target CONFIG-common [new prereqs: stamp-conf]======
This is kernel package version 11.001-0.1.
====== making stamp-arch-conf because of  ======

====== making target CONFIG-arch [new prereqs: stamp-arch-conf]======
====== making conf.vars because of .config ======

Makefile:528: /usr/src/linux-source-2.6.27/arch/xen/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-source-2.6.27/arch/xen/Makefile'.  Stop.
make: *** [conf.vars] Error 2
```

Any ideas what to do?

---

