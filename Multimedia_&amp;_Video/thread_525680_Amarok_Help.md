---
title: "Amarok Help"
date: 2007-08-14
forum: Multimedia &amp; Video
---

### Post by churchill614 on 2007-08-14
I am trying to install Amarok through Synaptic Package Manager.  When selecting Amarok for installation, it says other packages need to be installed.  It then tells me that Python-qt3 must be installed but that it is not going to be.  As such, I select this for installation but get a further error message that the package requires python (<2.5) but that 2.5.1-0ubuntu3 is to be installed.

Having looked, python 2.5, 2.4 and below are installed, but removing 2.5 would mean loosing a lot of other packages from my system.

I am running Feisty with Gnome, on a MacBook. I know Amarok is designed for KDE, but how do I get it to work and install into Gnome. If I can't get this to work, I will have to go back to OSX as I have lost my MP3 and iPod ability, and Banshee installs, starts to open, shows on the taskbar then disappears, so that doesn't work either.

Please help.

Thanks.

---

### Post by churchill614 on 2007-08-14
Okay, I did a prtial upgrade and that fixed most of my problems. I have removed amarok as I don't like it. Now, I am attempting Banshee, and when I type the following:

```
sudo apt-get build-dep banshee
```

the following error appears:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_dapper_free_source_Sources - open (2 No such file or directory)

```

I have no idea what this means, please can somebody help me.

---

