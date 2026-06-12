---
title: "[SOLVED] VLC unable to download"
date: 2009-01-04
forum: Multimedia Software
---

### Post by Schok on 2009-01-04
Is it just me? I cant seem to be downloading vlc thru add/remove, synaptics or even thru the terminal. i have tried changing the server from the System>Admin>sofware sources

any suggestions?

running Ubuntu 8.10

---

### Post by tuxxy on 2009-01-04
It should be downloaded using the following command in terminal,

```
sudo apt-get install vlc
```

also if it fails what does it say when you type in 

```
vlc

```

---

### Post by Schok on 2009-01-04
I tried this command when i went thru the Comprehensive Media & HowTo guide

sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4 vlc

And this is what it shows on the terminal:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread3 is already the newest version.
libdvdread3 set to manually installed.
libdvdnav4 is already the newest version.
libdvdnav4 set to manually installed.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libass1 libdca0 libdvbpsi4 libebml0 libiso9660-5 liblua5.1-0 libmatroska0
  libmodplug0c2 libqt4-dbus libqt4-designer libqt4-network libqt4-qt3support
  libqt4-script libqt4-sql libqt4-sql-mysql libqt4-xml libqtcore4 libqtgui4
  libsdl-image1.2 libtar libtwolame0 libvcdinfo0 libvlc2 libvlccore0
  qt4-qtconfig vlc-data vlc-nox
Suggested packages:
  libqt4-dev mozilla-plugin-vlc videolan-doc
The following NEW packages will be installed:
  libass1 libdca0 libdvbpsi4 libdvdcss2 libebml0 libiso9660-5 liblua5.1-0
  libmatroska0 libmodplug0c2 libqt4-dbus libqt4-designer libqt4-network
  libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-xml
  libqtcore4 libqtgui4 libsdl-image1.2 libtar libtwolame0 libvcdinfo0 libvlc2
  libvlccore0 qt4-qtconfig vlc vlc-data vlc-nox
0 upgraded, 29 newly installed, 0 to remove and 0 not upgraded.
Need to get 40.2kB/22.1MB of archives.
After this operation, 58.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
0% [Waiting for headers]                            


It will wait for headers a few minutes and then this will show:

Err [http://ubuntu-ashisuto.ubuntulinux.jp](http://ubuntu-ashisuto.ubuntulinux.jp) intrepid/universe libass1 0.9.5-0ubuntu2
  Connection failed
Failed to fetch [http://ubuntu-ashisuto.ubuntulinux.jp/ubuntu/pool/universe/liba/libass/libass1_0.9.5-0ubuntu2_i386.deb](http://ubuntu-ashisuto.ubuntulinux.jp/ubuntu/pool/universe/liba/libass/libass1_0.9.5-0ubuntu2_i386.deb)  Connection failed
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

thanks

---

### Post by rushikesh988 on 2009-01-04
try downloading and installing from its source codes .. which are avilable on 

[http://videolan.org](http://videolan.org)

---

### Post by Schok on 2009-01-04
Yup did that, didnt work too..

---

### Post by mc4man on 2009-01-04
Maybe try again or go to System -> Admin... -> Software Sources and change your "Download from" to a different mirror.

See if this completes ```
sudo apt-get update
```

---

### Post by Schok on 2009-01-04
Yeah, tried the best server, main server, any other servers nearby the region..doesnt seem to be downloading..yup updated everytime i change the server

---

### Post by rushikesh988 on 2009-01-04
maybe ur Isp server is down

---

### Post by mc4man on 2009-01-04
libass1 only has a few dependencies (unlike vlc), maybe try installing that manually and see if vlc will then install

[http://packages.ubuntu.com/intrepid/libass1](http://packages.ubuntu.com/intrepid/libass1)

though your orig. mirror seems to be open (....?

[http://ubuntu-ashisuto.ubuntulinux.jp/ubuntu/pool/universe/liba/libass/](http://ubuntu-ashisuto.ubuntulinux.jp/ubuntu/pool/universe/liba/libass/)

---

### Post by mishmosh1970 on 2009-01-05
I'm an Ubuntu newbie, and I was trying to install the Mozilla VLC plugin last night, but kept getting 404 Not found.  I tried it through Synaptics Package Manager and through command line, but no go.  What gives?

---

### Post by Schok on 2009-01-08
Hey it seems to be working now. Downloaded through terminal..weird..oh well, was using totem before i cud dl vlc and i kinda like it. For those who cant dl vlc, just try out totem its quite good too.

---

