---
title: "Wireless card in Lenono s10"
date: 2011-10-05
forum: Networking &amp; Wireless
---

### Post by Odense on 2011-10-05
I had to clear my old Lenovo s10 netbook and do a reinstall.
When I boot it up the wifi is not started and it says that it needs a driver or something like that.

I remember that I could fix it (in earlier versions of Ubuntu) by plugging in the network cable and getting the proprietary Broadcom driver online.

At the moment I do not have easy access to wired internet  - so is there a way I can download the driver with another PC and save it to a USB stick and install  it on the netbook that way ? It has to be relatively simple or I better drop it until I somehow can get a wired connection

---

### Post by praseodym on 2011-10-05
Hi,

the packages **dkms**, **patch**, **fakeroot**, and **bcmwl-kernel-source** are on the installation medium. Installation by double clicking. After that

```
sudo depmod -a
```

and you can activate the driver.

---

### Post by Odense on 2011-10-05
Thanks - but unfortunately not "for dummies" enough for me.
I was hopeful when I found the dkms package and really could install it by doubleclicking but I cannot find  **patch**, **fakeroot** or **bcmwl-kernel-source **when I search my USB stick - what do I need to do to locate the files ?

---

### Post by praseodym on 2011-10-06
```
~pool/main/p/patch
~pool/main/f/fakeroot
~pool/main/restricted/bcmwl-...
```
I never used a stick for that, can you add the stick to your software sources, when plugged in?

---

### Post by Odense on 2011-10-06
It is a "persistant Ubuntu Stick" so that some (ideally all - but that is not happening) of my changes can be preserved. It worked OK for installing - but it seems your suspicion is correct - when I try to add another volume it only accept a CD - and there is not built in CD/DVD drive - it is too small for that.

I am sure it must be possible somehow to add the stick though - but it might be beyond my skills :)

~pool/main/p/patch ~pool/main/f/fakeroot ~pool/main/restricted/bcmwl-...How do you get the ~ - when I try typing that in my netbook is does not show in the terminal window ?
And does the ~ replace something or I should just use the ~ ?

---

### Post by praseodym on 2011-10-06
~ is the main folder of the CD

Do you have another stick? These packages can also be downloaded from [http://packages.ubuntu.com](http://packages.ubuntu.com)

for 32/64 bit for you Ubuntu version

---

### Post by Odense on 2011-10-06
Thanks - that worked - this is posted from the netbook via wifi internet.

However - some of the packages was already installed and I even think the "patch" package required to uninstall some other packages  - which I accepted. And now when I try to run the "Update Manager" it crashes - with the following message:

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/th.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

Any ideas on how I get this working again ?

---

### Post by Odense on 2011-10-08
Luckily I did get some help:

[http://ubuntuforums.org/showthread.php?p=11320883#post11320883](http://ubuntuforums.org/showthread.php?p=11320883#post11320883)

---

