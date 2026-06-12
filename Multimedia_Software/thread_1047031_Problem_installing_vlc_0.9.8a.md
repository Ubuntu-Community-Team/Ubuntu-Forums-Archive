---
title: "Problem installing vlc 0.9.8a"
date: 2009-01-22
forum: Multimedia Software
---

### Post by kubunut on 2009-01-22
I'm new to K-ubuntu been using mainly PCLinuxOS and SuSE.

I tried adding the repos for VLC and managed to upgrade to KDE 4.1.4.
and the DVD lib and flash, etc...

But Synaptic and Apt Manager can't see vlc, I added the c-Korn repo.
But I keep getting 0.9.4.

I tried to install manually using dpkg -i .deb of the vlc_0.9.8a packages but some dep errors.

Now even when I try to just install 0.9.4 again I get some errors, I need help ???

I would be happy with either 0.9.8a or 0.9.4.

Running: sudo apt-get -f install gives me

> # /usr/lib$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libvlc2 libvlccore0
The following NEW packages will be installed:
  libvlc2 libvlccore0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
29 not fully installed or removed.
Need to get 0B/439kB of archives.
After this operation, 1053kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 118891 files and directories currently installed.)
Unpacking libvlccore0 (from .../libvlccore0_0.9.4-1ubuntu3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libvlccore0_0.9.4-1ubuntu3_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libvlccore.so.0.0.2', which is also in package libvlc0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking libvlc2 (from .../libvlc2_0.9.4-1ubuntu3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libvlc2_0.9.4-1ubuntu3_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libvlc.so.2.0.2', which is also in package libvlc0
Errors were encountered while processing:
 /var/cache/apt/archives/libvlccore0_0.9.4-1ubuntu3_i386.deb
 /var/cache/apt/archives/libvlc2_0.9.4-1ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Running sudo apt-get check gives me.

> #/usr/lib$ sudo apt-get check
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  vlc: Depends: libvlccore0 (>= 0.9.1) but it is not installed
  vlc-nox: Depends: libvlc2 (>= 0.9.1) but it is not installed
           Depends: libvlccore0 (>= 0.9.1) but it is not installed
E: Unmet dependencies. Try using -f.

Help me.

I tried removing the cached packages I tried removing the libvlc* manually nothing works.


Kubunut

---

### Post by kubunut on 2009-01-22
I somehow found the libvlc through Synapti,c that was installed with 0.9.8a removed it along with everything vlc related. Then reinstalled vlc 0.9.4.

It works now. But why can't I just upgrade to 0.9.8a through c-korn, weird ???


Kubunut

---

### Post by x33a on 2009-01-22
first uninstall vlc and it's dependencies through apt or synaptic

then download vlc and other required debs from here:

[http://archive.getdeb.net/dump/intrepid/vlc/](http://archive.getdeb.net/dump/intrepid/vlc/)

install them with dpkg and everything will run fine.

---

