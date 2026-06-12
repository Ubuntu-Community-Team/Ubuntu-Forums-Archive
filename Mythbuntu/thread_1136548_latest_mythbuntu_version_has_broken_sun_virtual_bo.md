---
title: "latest mythbuntu version has broken sun virtual box"
date: 2009-04-25
forum: Mythbuntu
---

### Post by Arminius on 2009-04-25
hey, my virtual box was working fine, now when I try to start it up it says, 
quote
kernel driver not install rc=-1908

the virtualbox linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

'etc/init.d/vboxdrv setp'

as root. users of ubunutu should install the DKMS package first. This package keeps track of linux kernel changes and recompiles the vboxdrv kernel module if necessary.
end quote

so I went to the vboxdrv file, executed it, nothing happened, so not sure what to do now? how do u install DKMS packages? I"m a bit of a newb

---

### Post by schlort on 2009-04-25
It helps to provide the steps you've attempted and maybe copy/paste the error message if possible.  I've not ever seen a message such as 'kernel driver not install rc=-1908'; I must assume the problem is indeed a version mismatch.  If your recent upgrade installed a new kernel, you will need to recompile the VirtualBox kernel modules.  dkms makes it trivial to keep these current.  Anyway, let's go through everything real quick so you know what you're looking for.

Feel free to copy/paste these long commands.


Is dkms installed? If not, install it:
```
dpkg -l | grep -q "^ii.*dkms" && echo "dkms is installed" || sudo apt-get install dkms
```


There are two virtualbox modules for the recent versions of virtualbox.  These are called 'vboxnetflt' and 'vboxdrv'.  Your kernel version should match the vbox module versions.  Let's check:
```
echo -e "Kernel version:\t`uname -r`"
lsmod | grep 'vbox' | cut -f1 -d" " | xargs -n1 sh -c 'echo "$0:\t`modinfo -n $0 | cut -f4 -d"/"`"'
```
Your output should consist of the kernel version, and the two modules. e.g.:

Kernel version: 2.6.28-11-generic
vboxnetflt:     2.6.28-11-generic
vboxdrv:        2.6.28-11-generic


If these do not match, you need to recompile the kernel modules:
```
sudo /etc/init.d/vboxdrv setup
```


This will rebuild the modules and reload them for you.  You should now be good to go. :guitar:

---

### Post by Arminius on 2009-04-25
thanks, for your help, dkms was installed.
I solved it by just reinstalling virtual box, and my virtual xp was safe and well in the reinstalled version.

---

