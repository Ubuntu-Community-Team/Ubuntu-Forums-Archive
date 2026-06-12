---
title: "HOW-TO: Installing the latest release of Gtk-Gnutella in Gutsy (7.10)"
date: 2008-11-13
forum: Multimedia Software
---

### Post by Warren Watts on 2008-11-13
I am still running Gutsy on my hardware, basically because I have older, slower hardware with limited RAM and processor clock speeds.

When I tried to install Gtk-Gnutella from the repositories, the version that installed (0.95.4) refused to connect to any peers over the network.  I decided to download the newest release from SourceForge and compile it from source.  I expected to spend HOURS resolving dependancies, but the Authors made it quite easy for me!  There was a README.Debian file that outlined all the steps!  I accomplished the compilation and .deb install in less than 15 minutes!

Here's a HOW-To:


Download the latest Gtk-Gnutella snapshot from sourceforge.net, saving the tarball archive to the Desktop

Source:
[http://sourceforge.net/project/showfiles.php?group_id=4467](http://sourceforge.net/project/showfiles.php?group_id=4467)

Double-click the tarball and extract the folder to the Deskop.

Satisfy any dependancies by installing the following packages:

```
sudo apt-get install fakeroot debhelper gcc make zlib1g-dev libxml2-dev libgnutls-dev gettext libglib2.0-dev libgtk2.0-dev libdbus-1-dev
```

Open the terminal and navigate to the extracted folder:

```
cd Desktop/gtk-gnutella-snapshot
```

Build the .deb:

```
sudo fakeroot debian/rules binary
```

After a few minutes of compiling, a new .deb will be build for you, appearing on the Desktop.

Double-click the .deb and install Gtk-Gnutella. (You may get a warning that the version to be installed being newer than the one available thru the repositories; INSTALL AT YOUR OWN RISK!  I installed the latest release with no problems at all)

Enjoy!

---

