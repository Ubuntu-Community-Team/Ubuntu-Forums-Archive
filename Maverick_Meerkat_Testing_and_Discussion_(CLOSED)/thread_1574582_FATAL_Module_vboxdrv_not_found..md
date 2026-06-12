---
title: "FATAL: Module vboxdrv not found."
date: 2010-09-14
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by coolman98 on 2010-09-14
I upgraded to 10.10 and when I try to boot up my virtualbox vm I get error: Failed to open a session for the virtual machine xp.
 The virtual machine 'xp' has terminated unexpectedly during startup with exit code 1

 and then: please install the virtualbox-ose-dkms package and execute 'modprobe vboxdrv' as root.
please help.

---

### Post by philinux on 2010-09-14
Moved to Maverick Testing.

---

### Post by coolman98 on 2010-09-14
sigh..........

---

### Post by Longinus00 on 2010-09-14
Did you even try to do the commands it told you to run? It sounds like it didn't compile the virtualbox module when you upgraded to 10.10, something which dkms would have taken care of.

---

### Post by coolman98 on 2010-09-14
I did it said :virtualbox-ose-dkms is already the newest version.
The following packages were automatically installed and are no longer required:
  libktnef4 librpmbuild0 libavutil49 libqt4-assistant libkpimtextedit4
  libkimproxy4 libboost-program-options1.40.0 kdelibs5 libkxmlrpcclient4
  librpmio0 librpm0 libsysfs-dev libdirectfb-extra libdvbpsi5 libkde3support4
  libdirectfb-dev libx264-85 install-package libqgpgme1 libqt4-webkit
  libqtassistantclient4 libxcb-render-util0-dev libkpimidentities4
  libjpeg62-dev libkblog4 libmagick++2 gdebi-kde kdepimlibs5 libkholidays4
  libsox1a virtuoso-nepomuk libsyndication4 libebml0 libmpcdec3 libmatroska0
  libgpgme++2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 128 not upgraded.

---

### Post by coolman98 on 2010-09-14
bump.

---

### Post by cariboo on 2010-09-14
I just got the same error, time to file a bug.

---

### Post by coolman98 on 2010-09-14
will you do it.

---

### Post by cariboo on 2010-09-14
I can't, as I just installed the puel version on this system. If you are running a testing version, you should be willing to report bugs. If you have a [Launchpad aacount]("https://launchpad.net/") , all you have to do is press Alt-F2 and type:

```
ubuntu-bug VirtualBox
```

and follow the prompts.

---

### Post by coolman98 on 2010-09-14
I dont like bug report> ughh

---

### Post by cariboo on 2010-09-14
If the devs don't know there is a problem, how can the fix it?

---

### Post by coolman98 on 2010-09-19
you do it

---

### Post by caryb on 2010-09-19
try this it might fix your problem

```
sudo /etc/init.d/vboxdrv setup
```


Cary

---

### Post by andymorton on 2010-09-22
I'm having the same problem myself. I've filed a bug report

andy

---

### Post by Noz3001 on 2010-09-22
Did you modprobe it and then try again? I don't like the module starting at boot so I have to do this purposefully

---

### Post by andymorton on 2010-09-22
> **Noz3001 said:**
> Did you modprobe it and then try again? I don't like the module starting at boot so I have to do this purposefully

I've tried it a few times and get the same result.

---

### Post by SeijiSensei on 2010-09-22
Maybe you don't have the gcc compiler installed so VB can't build the module to match your kernel.

Try running 'sudo apt-get build-essential'.  Does apt-get tell you it's already installed, or does it install a bunch of new packages?  If the latter, try installing VB again.

Out of the box, Ubuntu doesn't come with the programs and libraries needed to build software from source.  However VB needs to build and install a new kernel module each time it encounters a new kernel versopm.  (The vboxdrv module is stored in /lib/modules/[kernel-version-number]/updates/dkms; there's a subdirectory in /lib/modules for each kernel and a separate, compatible copy of the vboxdrv module in each one.)

---

### Post by andymorton on 2010-09-22
> **SeijiSensei said:**
> Maybe you don't have the gcc compiler installed so VB can't build the module to match your kernel.

Try running 'sudo apt-get build-essential'.  Does apt-get tell you it's already installed, or does it install a bunch of new packages?  If the latter, try installing VB again.

Out of the box, Ubuntu doesn't come with the programs and libraries needed to build software from source.  However VB needs to build and install a new kernel module each time it encounters a new kernel versopm.  (The vboxdrv module is stored in /lib/modules/[kernel-version-number]/updates/dkms; there's a subdirectory in /lib/modules for each kernel and a separate, compatible copy of the vboxdrv module in each one.)

It says ''E: invalid operation build-essential''

andy

---

### Post by SeijiSensei on 2010-09-22
Sorry, andy, I forgot the key word "install" as in "apt-get *install* build-essential".

---

### Post by andymorton on 2010-09-22
No problem. Thanks! :)

andy

---

### Post by andymorton on 2010-09-22
> **SeijiSensei said:**
> Sorry, andy, I forgot the key word "install" as in "apt-get *install* build-essential".

Ok, I've just ran the command and it's already installed.

---

### Post by coolman98 on 2010-10-05
the bug was fixed.

---

