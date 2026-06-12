---
title: "yet another nvidia problem... unable to uninstall nvidia-glx"
date: 2008-05-14
forum: Multimedia Software
---

### Post by Keldek on 2008-05-14
I've recently installed some ubuntustudio packages, which in turn required me to upgrade my kernel from 2.6.24-16-generic to 2.6.24-16-rt, which in turn broke my nvidia drivers.

I followed a set of instructions here on the forums:
```
sudo gedit /etc/default/linux-restricted-modules-common


DISABLED_MODULES="nv nv_new"


sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-4.1 xserver-xorg-dev


sudo apt-get --purge remove nvidia-glx nvidia-glx-new nvidia-settings nvidia-kernel-common

sudo rm /etc/init.d/nvidia-* 

sudo rm /lib/linux-restricted-modules/.nvidia_new_installed


Logout > Ctrl-Alt-F1 and switch to a tty


 sudo /etc/init.d/gdm stop

 sudo ln -sf /usr/bin/gcc-4.1 /usr/bin/gcc

 sudo sh NVIDIA-Linux-x86-169.04-pkg1.run

 sudo ln -sf /usr/bin/gcc-4.2 /usr/bin/gcc

 sudo /etc/init.d/gdm start
```
found here: [http://ubuntuforums.org/showpost.php?p=3883182&postcount=6](http://ubuntuforums.org/showpost.php?p=3883182&postcount=6)

following the initial steps then switching to tty, stopping gdm and proceeding to reinstall the nvidia beta drivers... my life becomes hell.

The new nvidia driver couldn't compile a new kernel module for my kernel because removing nvidia-kernel-common also removed a lot of ther kernel files...

So, after roughly 2 hours of trying to figure out how to fix this problem (I'm still rather new to *nix so solving problems via tty is umm, hard lol) from a command line, I finally get things up and running again with the new beta drivers.

Except now, I cannot remove nvidia-glx, through synaptic or through the terminal. I get the following error (I've tried apt-get remove and purge... mark for removal and mark for complete removal):

```
keldek@System-X:~$ sudo apt-get remove nvidia-glx
[sudo] password for keldek: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  nvidia-glx
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 22.4MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 173686 files and directories currently installed.)
Removing nvidia-glx ...
dpkg-divert: rename involves overwriting `/usr/lib/xorg/modules/libwfb.so' with
  different file `/usr/lib/nvidia/libwfb.so.xserver-xorg-core', not allowed
dpkg: error processing nvidia-glx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 nvidia-glx
E: Sub-process /usr/bin/dpkg returned an error code (1)
keldek@System-X:~$ 

```

I don't know if this will cause me trouble down the line, or if it's safe to ignore (though I would really rather NOT ignore it heh).

Has anyone experienced this problem before? If so, how did you go about resolving the issue?

Thanks in advance for any help

Edit: Well, this doesn't seem to be an issue I can just ignore, as I am unable to install or remove any other packages until I can resolve this problem. apt-get and synaptic attempt to remove nvidia-glx before doing anything else, and when it fails nothing else completes. Again, any and all help on this matter is greatly appreciated.

---

