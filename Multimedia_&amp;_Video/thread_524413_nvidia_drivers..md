---
title: "nvidia drivers."
date: 2007-08-13
forum: Multimedia &amp; Video
---

### Post by damansandhu on 2007-08-13
i am new in kubuntu and i have downloaded nvidia drivers 100.14.11 , but dont know how to install them . i have evga 7600gs.
when type sudo sh nvidia-linux-x86-100.14.11-pkg1.run
it says some x servers are running , plz somebody help me.

---

### Post by ZipoTe on 2007-08-13
You can do 2 things:

1st (aka being a man :-P it's a joke):
- cntrl+alt+F1 this will bring you to the terminal
- type: /etc/init.d/gdm stop, with that, your X server will stop running

then try again: sudo sh nvidia-linux-x86-100.14.11-pkg1.run

when finished: /etc/init.d/gdm start

2nd:

install [envy]("http://albertomilone.com/nvidia_scripts1.html") and enjoy you nvidia card :)

**EDIT**

control+alt+F7 will bring you back to your X session

---

### Post by damansandhu on 2007-08-13
ok when i tried this command "/etc/init.d/gdm stop" it said no such file in the directory

---

### Post by tseliot on 2007-08-13
Follow only one of the 2 methods. Mixing them is not an option.

---

### Post by tseliot on 2007-08-13
> **damansandhu said:**
> ok when i tried this command "/etc/init.d/gdm stop" it said no such file in the directory
You don't have to install the Nvidia driver from Nvidia's website, especially if you're not experienced (no offence, I'm just trying to help you). You will lack certain dependencies and will have to follow additional steps...

Have a look at this thread instead:
[http://ubuntuforums.org/showthread.php?t=301499](http://ubuntuforums.org/showthread.php?t=301499)

---

### Post by ZipoTe on 2007-08-13
I explained wrong, what i meant was 1st **or** 2nd, as tseliot said, mixing them is not a good idea :-P

---

### Post by ZipoTe on 2007-08-13
By the way, you have to type:**_sudo_** /etc/init.d/gdm stop

---

### Post by damansandhu on 2007-08-13
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.20-16-generic_2.6.20-16.29_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
daman@Ultimate:~$ sudo apt-get install nvidia-glx-new
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  linux-restricted-modules-2.6.20-16-generic: Depends: linux-image-2.6.20-16-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).



can you help me now??

---

### Post by tseliot on 2007-08-13
type:
```
sudo apt-get update
```

```
sudo apt-get install -f
```

and post the output of the 2nd command.

---

### Post by damansandhu on 2007-08-13
```
daman@Ultimate:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-image-2.6.20-16-generic
Suggested packages:
  linux-doc-2.6.20 linux-source-2.6.20
The following NEW packages will be installed:
  linux-image-2.6.20-16-generic
0 upgraded, 1 newly installed, 0 to remove and 102 not upgraded.
5 not fully installed or removed.
Need to get 0B/23.8MB of archives.
After unpacking 71.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 91597 files and directories currently installed.)
Unpacking linux-image-2.6.20-16-generic (from .../linux-image-2.6.20-16-generic_2.6.20-16.29_i386.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.20-16-generic_2.6.20-16.29_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Running postrm hook script /sbin/update-grub.
You shouldn't call /sbin/update-grub. Please call /usr/sbin/update-grub instead!

Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.20-15-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.20-16-generic_2.6.20-16.29_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
daman@Ultimate:~$ sudo apt-get install linux-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
linux-generic is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  linux-restricted-modules-2.6.20-16-generic: Depends: linux-image-2.6.20-16-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
daman@Ultimate:~$ sudo apt-get install nvidia-glx-new
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  linux-restricted-modules-2.6.20-16-generic: Depends: linux-image-2.6.20-16-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
daman@Ultimate:~$  
```

still same

---

### Post by tseliot on 2007-08-13
Is synaptic, Update manager (or any other application that has to do with packages) open while you're typing the commands?

---

### Post by damansandhu on 2007-08-13
nothing was running , except adept updater was notifying me some downloads.

---

### Post by damansandhu on 2007-08-13
ok , i am going to reinstall kubuntu, then i guess i will be able to install drivers

---

### Post by tseliot on 2007-08-13
> **damansandhu said:**
> ok , i am going to reinstall kubuntu, then i guess i will be able to install drivers

no, you shouldn't.

Open adept-updater and let it update the system.

---

### Post by damansandhu on 2007-08-13
i got drivers installed from method 1 after reinstalling

---

### Post by ZipoTe on 2007-08-14
great!! glad the first method helped ^^

---

