---
title: "Intrepid strange problem with apt-get installing ati x550 drivers"
date: 2009-02-07
forum: Multimedia Software
---

### Post by yeremiya on 2009-02-07
I got a strange problem when I try to install ati drivers on my Intrepid. I am trying to follow the instructions provided here:

[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

I have downloaded ati-driver-installer-9-1-x86.x86_64.run and I am trying to execute the following:

```
root@leka-desktop:/home/leka/Desktop# sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++5 dkms
```

When I do that, it produces the following output:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
debconf is already the newest version.
libstdc++5 is already the newest version.
The following packages were automatically installed and are no longer required:
  libopenal1 ispell ibritish libmtp7 libopenal0a libavutil1d python-pexpect
  libdc1394-13 python-twisted-web python-pycurl libopenexr2ldbl libdns35
  libcamel1.2-11 libpostproc1d libtotem-plparser10 libgtkhtml3.16-cil
  libsmbios1 libexiv2-2 libisccc30 libavformat1d libalut0 liblwres30
  bluez-audio linux-restricted-modules-2.6.20-15-generic libpoppler2
  linux-restricted-modules-2.6.22-16-generic libbind9-30 libisccfg30
  libavcodec1d python-smartpm libisc35 iamerican libltdl3 libpoppler-glib2
  o3read libntfs-3g23
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  autoconf automake1.7 autotools-dev dpkg-dev fdupes g++ g++-4.3 gettext
  html2text intltool intltool-debian libcompress-raw-zlib-perl
  libcompress-zlib-perl libio-compress-base-perl libio-compress-zlib-perl
  libmail-sendmail-perl libstdc++6-4.3-dev libsys-hostname-long-perl
  libtimedate-perl m4 po-debconf
Suggested packages:
  autoconf2.13 autobook autoconf-archive gnu-standards autoconf-doc libtool
  devscripts debian-keyring g++-multilib g++-4.3-multilib gcc-4.3-doc
  libstdc++6-4.3-dbg cvs gettext-doc libstdc++6-4.3-doc libmail-box-perl
Recommended packages:
  automake automaken
The following NEW packages will be installed:
  autoconf automake1.7 autotools-dev build-essential cdbs debhelper dh-make
  dkms dpkg-dev fakeroot fdupes g++ g++-4.3 gettext html2text intltool
  intltool-debian libcompress-raw-zlib-perl libcompress-zlib-perl
  libio-compress-base-perl libio-compress-zlib-perl libmail-sendmail-perl
  libstdc++6-4.3-dev libsys-hostname-long-perl libtimedate-perl m4 po-debconf
0 upgraded, 27 newly installed, 0 to remove and 0 not upgraded.
Need to get 7533kB/11.8MB of archives.
After this operation, 39.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081028)'
in the drive '/cdrom/' and press enter

```

When I try inserting Ubuntu 8.10 CD (either normal or alternate versions), nothing happens! :(

After that, i did apt-get autoremove, and it happens again. I've tried restarting the root terminal, but it just happens again, only without the "The following packages were automatically installed and are no longer required..." part.

I must say that I have tried installing the driver automatically, by enabling the restricted driver, but after I click "Activate" (or something) it just stays on "Downloading and installing", at 0 percent, and without any network activity.

I am totally confused! Help?

---

### Post by yeremiya on 2009-02-07
I have figured out how to continue instalation! It's so simple I'm embarassed now... :oops: I just unticked the CD-ROM update option in Software Sources and apt-get started downloading!

Still, I think the fact that it searches for the CD and not recognizing it is some kind of a bug.

---

