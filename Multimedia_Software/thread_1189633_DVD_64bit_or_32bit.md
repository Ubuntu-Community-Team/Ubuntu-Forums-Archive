---
title: "DVD 64bit or 32bit?"
date: 2009-06-16
forum: Multimedia Software
---

### Post by sandman3838 on 2009-06-16
Hello
I would like to get my DVD player working here on Ubuntu 904.
I found this:  (witch one?)
Thanks  guys


Multimedia Applications

Multimedia applications include music and video playback, CD and DVD playback and recording, and Internet TV as well as "terrestrial" (i.e. broadcast, satellite, and cable) TV viewing on your computer. Here is a nice review of some of the applications that enables conversion and handling of these types of files.

[edit]
CDs and DVDs
[edit]
DVD Playback Capability

To play encrypted DVDs, the libdvdcss2 package is essential. libdvdcss2 is a simple library designed for accessing DVDs like a block device without having to bother about the decryption. More information about this package can be found at VideoLAN.

    * You can install libdvdcss2 as a 64-bit .deb package without installing the Medibuntu repositories: 

wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_amd64.deb)
sudo dpkg -i libdvdcss2_1.2.10-0.2medibuntu1_amd64.deb

    or a 32-bit .deb package: 

wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb)
sudo dpkg -i libdvdcss2_1.2.10-0.2medibuntu1_i386.deb

---

### Post by sandman3838 on 2009-06-17
I did some more looking around and this did it for me:

[http://ubuntuforums.org/showpost.php?p=7197110&postcount=5](http://ubuntuforums.org/showpost.php?p=7197110&postcount=5)

Thanks

---

