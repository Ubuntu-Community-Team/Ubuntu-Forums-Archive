---
title: "Building Tork (KED application) in Ubuntu 8.10 (Gnome)"
date: 2009-04-05
forum: Networking &amp; Wireless
---

### Post by lotuseclat79 on 2009-04-05
This procedure will allow you to build the latest Tork source code for version 0.31-1.

1 - Make the following changes to /etc/apt/sources.list (as root):

a) uncomment universe and multiverse lines if not already uncommented

b) Ref: [http://wiki.noreply.org/noreply/TheOnionRouter/TorOnDebian](http://wiki.noreply.org/noreply/TheOnionRouter/TorOnDebian)
see above web page entitled Stable versions of tor and add those lines and
also add weasel's signature below it as instructed.

2 - launch Synaptic Package Manager (System>Administration>Synaptic Package Manager) and click on the Reload icon.

3 - Search for tork (should find 0.29-1build1 version) Note: 0.31-1 is latest. 

The next step will download and install both tork and the KDE environment in tork's Depends list of packages documented in the tork package's control file.

4 - Mark tork, click on Mark again, then click on Apply icon, then click
on Apply again.  Note: 66 new packages will be installed, 236 MB of extra
space will be used, and 83.1 MB have to be downloaded

5 - Now, using Synaptic Package Manager, search and add the following
development tools and libraries necessary to configure, compile, and install tork 0.31-1.

a) g++: 3 new packages will be installed, 6 packages will be upgraded,
19.1 MB of extra space will be used, 12.0 MB have to be downloaded

b) automake: 4 new packages will be installed, 4153 kB of extra space will
be used, 1248 kB have to be downloaded

c) libx11-dev: 14 new packages will be installed, 1 package will be upgraded,
6771 kB of extra space will be used, 2861 kB have to be downloaded

d) libxt-dev: 3 new packages will be installed, 1671 kB of extra space will
be used, 563 kB have to be downloaded

e) zlib1g: 1 new package will be re-installed, 75.6 kB have to be downloaded

f) libjpeg62-dev: 1 new package will be installed, 430 kB of extra space
will be used, 188 kB have to be downloaded

g) libpng12-dev: 2 new packages will be installed, 1 package will be upgraded, 999 kB of extra space will be used, 575 kB have to be downloaded

h) libqt3-headers: 34 new packages will be installed, 3 packages will be
upgraded, 26.4 MB of extra space will be used, 7427 kB have to be downloaded

i) kdelibs4-dev: 37 new packages will be installed, 6 packages will be
upgraded, 50.8 MB of extra space will be used, 18.3 MB have to be downloaded

Note: After step 5i) System restart required (To complete the update of your system, please restart it.  click on the notification icon for details.

6) - Download and extract the tork-0.31-1 source code from SourceForge.net:
[http://sourceforge.net/project/showfiles.php?group_id=159836%20Download%20TorK](http://sourceforge.net/project/showfiles.php?group_id=159836%20Download%20TorK)

a) Tork Source Tarball at:
[http://sourceforge.net/project/showfiles.php?group_id=159836&package_id=179627&release_id=658861](http://sourceforge.net/project/showfiles.php?group_id=159836&package_id=179627&release_id=658861) : 
tork-0.31.tar.bz2: Size: 3043835 Architecture: i386
tork-0.31.tar.gz: Size: 3624469 Architecture: i386

b) Tork Source Tarball Signatures at:
[http://sourceforge.net/project/showfiles.php?group_id=159836&package_id=256885&release_id=658862](http://sourceforge.net/project/showfiles.php?group_id=159836&package_id=256885&release_id=658862) :
tork-0.31.tar.bz2.asc: Size: 189 Architecture: i386
tork-0.31.tar.gz.asc: Size: 189 Architecture: i386
Note: Click on link, copy text and save to file: tork-0.31.gpg (189 bytes)

Note: Also, there is a tork-data .deb file for all Debian releases at:
[http://ftp.debian.org/debian/pool/main/t/tork/tork-data_0.31-1_all.deb](http://ftp.debian.org/debian/pool/main/t/tork/tork-data_0.31-1_all.deb) 865K
which is required to be installed prior to installing the tork Debian
package, but may be (?) generated as part of compilation.  It does not contain any dependencies, but tork is dependent on the tork-data package in its control file.

How to configure, compile and install tork on Gnome:

1) Having downloaded tork-0.31.tar.bz2, do these steps prior to configuring tork for compilation (assumes PWD=/home/ubuntu/Desktop):

a) bunzip2 tork-0.31.tar.bz2
b) tar -xf tork-0.31.tar
c) cd tork-0.31

2) Do the following commands to configure tork:

a) ./configure > config.out.0 2>&1
b) echo $?

The echo command above should return: 0

3) Do the following command to compile tork:

a) make > make.out.0 2>& 1
b) echo $?

The echo command above should return: 0

4) Do the following commands to install tork:

a) sudo -i
b) cd ~ubuntu/Desktop/tork-0.31
c) make install > make.install.0 2>&1
d) echo $?

The echo command above should return: 0

If the echo command did not return 0 in any of the above steps, inspect the output file for a description of the errors and fix them, then repeat the step to continue the procedure.

At this point, tork is ready for execution, so it should be able to at least emit it's version information with the command:

$ tork -version
Qt: 3.3.8b
KDE: 3.5.10
Tork: 0.31:

Prior to executing tork, you should download its documentation and find out how to configure its configuration files for execution with tor, and privoxy (optional).  Tork has a First Run Wizard to help out in this regard, which must be selected as it does not automatically detect that situation.

Instead of Privoxy, Tork now uses the small, fast caching proxy, polipo,
for improved performance which can be downloaded and installed using the
Synaptic Package Manager. Polipo does pipelining which privoxy does not.

Also, if you use Firefox, make sure you get the Add-on TorButton 1.2.1.
Note: Version 3.0.8 is the latest version of Firefox at this time.

-- Tom

---

