---
title: "Installing Envy to get Nvidia drivers working"
date: 2007-06-03
forum: Multimedia &amp; Video
---

### Post by jme on 2007-06-03
Hi all.

For the last few days I have been trying to get my 8800GTS 320MB card working with Feisty to no avail.  I have read many of the posts here and tried a lot of the ideas.  I have now found the Envy program by Alberto but I'm having problems installing it.  When I use sudo dpkg -i from the command line. 

Here is the output:

```

sudo dpkg -i envy_0.9.4-0ubuntu6_all.deb
Password:
Selecting previously deselected package envy.
(Reading database ... 105003 files and directories currently installed.)
Unpacking envy (from envy_0.9.4-0ubuntu6_all.deb) ...
dpkg: dependency problems prevent configuration of envy:
 envy depends on build-essential; however:
  Package build-essential is not installed.
 envy depends on xserver-xorg-dev; however:
  Package xserver-xorg-dev is not installed.
 envy depends on build-essential; however:
  Package build-essential is not installed.
 envy depends on fakeroot; however:
  Package fakeroot is not installed.
 envy depends on dh-make; however:
  Package dh-make is not installed.
 envy depends on debhelper; however:
  Package debhelper is not installed.
 envy depends on dpkg-dev; however:
  Package dpkg-dev is not installed.
 envy depends on dpatch; however:
  Package dpatch is not installed.
dpkg: error processing envy (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 envy

```

This is a fresh install of Ubuntu and I can't see what's going wrong.

Any help appreciated.  :)

---

### Post by cantormath on 2007-06-03
> dpkg: error processing envy (--install):
 dependency problems - leaving unconfigured
You need to enable the universe and multiverse repos to install envy to get the dependencies it requires.  You can do this in synaptic or by editing the /etc/apt/sources.list use ```
sudo gedit /etc/apt/sources.list
``` in the terminal.
Those > envy depends on.....etc means that it is uable to access the packages from the repos you have set.......so just add the universe and multiverse.  After you save the sources.list file, you have to ```
sudo apt-get update
``` in terminal



I would just download the drivers from the nvidia website, there is a script for the cards, based on the series and you can download and run that, it then asks some easy questions and sets up the drivers perfectly.

---

