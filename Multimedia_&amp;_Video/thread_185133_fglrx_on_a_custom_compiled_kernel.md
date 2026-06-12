---
title: "fglrx on a custom compiled kernel"
date: 2006-05-31
forum: Multimedia &amp; Video
---

### Post by ashrack on 2006-05-31
I always built custom compiled kernels for myself. BUt with DAPPER I have a problem with compiling FGLRX MODULE.
I used this line to compile it:
```
root@tom:/usr/src/linux# make-kpkg clean && make-kpkg --append-to-version=-hiber-fglrx kernel_image kernel_headers modules_image

```
and I attach the error that I get when it started to compile FGLRX module:
[ATTACH]9189[/ATTACH]

ps. I have 'fglrx-kernel-source' installed and also untarred.

---

### Post by Jasman on 2006-05-31
I'm having the same problem, and I've also tried method 2 of the fglrx Dapper installation wiki, as well as using Kano's fglrx install script (seems to do the same thing). Nothing works all the way through to create custom debs. Mucking with files (such as Makefile.kbuild in the fglrx-kernel-source package) makes the process go further, but it always craps out. I even had a deb generated, but it gives an unresolvable dependency error when trying to install. I should say I have both a custom kernel and custom kernel headers, and the it's running fine.

Has anyone managed to install the ATI proprietary drivers on a custom kernel with the latest Ubuntu kernel source (2.6.15-23)? Thanks for any input.

---

### Post by Jasman on 2006-06-01
This may be a restricted modules or fglrx-kernel-source bug issue:

[https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/45563]("https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/45563")

---

### Post by ashrack on 2006-06-03
yep am expiriencing the same issues. But none of the DEVs are responding.
How to get their attention__

---

### Post by Jasman on 2006-06-05
I reposted this issue in Dapper forums, but no one has commented yet. I think devs are rushing to respond to initial problems with the release, some of which folks were calling showstoppers (eg, not being able to print at all). It'll probably be a while before this issue is addressed.

---

### Post by ashrack on 2006-06-08
:(

---

### Post by Jasman on 2006-06-08
This is from that bug report thread. Problems compiling modules against custom kernels continue into the 2.6.17 series, but:

> I was able to compile the module only by using fglrx-kernel-source package built from ati-installer 8.25.18, and then changing the version number to match ubuntu's one..

I'll have to give this a try. Again, it would be nice if the devs would address this problem. I don't think this is a carryover from Debian.

---

### Post by ashrack on 2006-06-09
[QUOTE=Jasman]I was able to compile the module only by using fglrx-kernel-source package built from ati-installer 8.25.18, and then changing the version number to match ubuntu's one..[/QUOTE]

how could I do that??

---

### Post by Jasman on 2006-06-12
I don't know. If I try it, and it works, I'll post how I did it. I haven't been using my Ubuntu install lately because of this problem.

---

### Post by ashrack on 2006-06-14
and has it worked

---

### Post by Jasman on 2006-06-14
Compiled it using instructions on the bug tracking thread, but what I compiled isn't compatible with the other necessary packages, so no, it hasn't worked. The bug is being looked into, though.

---

### Post by Jasman on 2006-06-20
Well, I don't even know if I can explain what I just did, but I pretty much got fglrx working on my custom kernel. The first thing I did was uninstall the kernel-specific linux-restricted-modules package that's in the Ubuntu repositories, as well as linux-restricted-modules-common. Then I downloaded the source for this package from here
[http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.15/linux-restricted-modules-2.6.15_2.6.15.11.orig.tar.gz]("http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.15/linux-restricted-modules-2.6.15_2.6.15.11.orig.tar.gz")
I built the ati/fglrx piece of this package against my custom kernel and installed it. In order to complete the installation, I had to get the process numbers for gdm (gnome display manager) through the system monitor application, then CTL-ALT-F3 to enter root prompt, su to login as root (and I had to do sudo passwd root to make a root password), kill gdm with its associated process numbers, and finally run the make install script in the linux-restricted-modules package I'd just built. I had to do all of this to allow the install to overwrite some files (radeon?). If there's an easier way to kill gdm in the terminal display, I'd like to know, since gdm-stop doesn't work at all, even though it's in the man entry.

After all of this, I followed instructions for building the ATI package from ATI, which can be found elsewhere. I elected to build for Ubuntu 6.06 (for some reason, there's a named and a numbered option for each Ubuntu release - eg, Dapper and 6.06 are different options). The most annoying part here was that the graphical front end for the ATI package didn't fit on my display, and I couldn't resize it. I had to fumble my way through the selection screen and then it bombed out but re-ran itself in a text-based window, which then, for some reason, went ahead and built all the debs without a hitch.

Finally, I installed the xorg-driver-fglrx, fglrx-control, and fglrx-sources pakages and then changed the word "ati" to "fglrx" in my /ect/X11/xorg.conf file and rebooted.

Oh, I also just remembered that I was supposed to blacklist flgrx in /etc/default/linux-restriced-modules-common, which I didn't do before going through all of this, because I had uninstalled linux-restricted-modules-common. I might fiddle around now with blacklisting and reinstalling that, but I don't even know what it does.

Bottom line, I have an fglrx ATI control panel that allows me to switch screens (tv-out, which is the only reason I'm doing all of this anyway), and glxgears shows 3-D gears spinning. We'll see how long this lasts before it breaks.

---

