---
title: "AcidRip won't rip any Dvds"
date: 2009-10-29
forum: Multimedia Software
---

### Post by Gogeden on 2009-10-29
So I tried to rip a DVD with AcidRip and it obviously won't rip. Everytime I try to preview the chapter, AcidRip locks up and when I try to start the ripping process, nothing happens... It detects DVDs but it won't rip! Help! :lolflag:

---

### Post by Aemaeth on 2009-10-29
may be a foolish question but do you have libdvdcss2 installed? what about the windows codecs? 

You need to add the following lines to /etc/apt/sources.list file or you need to make sure you have enabled Universe and multiverse repositories Using GUI.

sudo gedit /etc/apt/sources.list

Make sure you have the following two lines save and exit your file

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty universe multiverse

Now you need to run the following command to update the source list

    sudo apt-get update

I trimmed this from another forum:

Install libdvdcss2 and w32 video codecs in Ubuntu 9.04 (Jaunty)

Support for WMV, RealMedia and other formats has been bundled into the w32codecs package. This package is not available from the Ubuntu repositories due to licensing and legal restrictions.To play encrypted DVDs, the libdvdcss2 package is essential.

For Ubuntu 9.04 (Jaunty) Users use the following procedures

sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

Then, add the GPG Key using the following commands

sudo apt-get update

sudo apt-get install medibuntu-keyring

sudo apt-get update

For i386 Users install Codecs using the following command

    sudo apt-get install w32codecs libdvdcss2

For amd64 Users install Codecs using the following command

    sudo apt-get install w64codecs libdvdcss2

Using above download locations you can install most of the mutimedia codecs for ubuntu.

---

### Post by Gogeden on 2009-10-29
The problem has been solved! Thanks! Man! Kudos! ^_^

---

