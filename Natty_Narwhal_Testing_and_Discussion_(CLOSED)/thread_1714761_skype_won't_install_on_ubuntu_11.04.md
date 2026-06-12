---
title: "skype won't install on ubuntu 11.04"
date: 2011-03-25
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by &lt;(-.-)&gt; on 2011-03-25
I'm trying to install skype on ubuntu 11.04 but when i try both the  32-bit and 64-bit versions but neither will work.  when i try 64-bit it  says wrong architecture and when i try 32-bit it says "The package is of  bad quality, The installation of a package which violates the quality  standards isn't allowed. This could cause serious problems on your  computer. Please contact the person or organisation who provided this  package file and include the details beneath."  and under details it  says "Lintian check results for  /tmp/skype-ubuntu-intrepid_2.1.0.81-1_i386.deb:
E: skype: description-starts-with-package-name 
W: skype: extended-description-line-too-long 
W: skype: extended-description-line-too-long 
W: skype: possible-unindented-list-in-extended-description 
W: skype: new-package-should-close-itp-bug 
W: skype: binary-without-manpage usr/bin/skype"

---

### Post by VMC on 2011-03-25
Have a look [_**here**_]("http://ubuntuforums.org/showthread.php?t=1714414") on the same subject.

---

### Post by &lt;(-.-)&gt; on 2011-03-25
i tried the dpkg commands but it still is not being installed
error being
cannot access archive: No such file or directory
Errors were encountered while processing:
 skype-ubunru-intrepid_2.1.0.81-1_i386.deb
i tried even putting the directory and sill came up with the same error

---

### Post by cariboo on 2011-03-25
The skype package is located here:

[http://archive.canonical.com/ubuntu/pool/partner/s/skype/](http://archive.canonical.com/ubuntu/pool/partner/s/skype/)

It isn't a Natty specific package, but it will work. Just download it and use the usual methods to install it.

---

### Post by rajeev1204 on 2011-03-26
:popcorn:off topic.

How do you get a username like that ?  Its a diagram.I thought characters were not allowed.

Really cool stuff.

---

### Post by kuvanito on 2011-03-26
Open a terminal and type these commands one at a time according to your version 32 or 64 bit

32 bit
wget [http://www.skype.com/go/getskype-linux-beta-ubuntu-32](http://www.skype.com/go/getskype-linux-beta-ubuntu-32)
sudo apt-get install libqt4-dbus libqt4-network libqt4-xml libasound2
sudo dpkg -i getskype-linux-beta-ubuntu-32
sudo apt-get -f install



64 bit
wget [http://www.skype.com/go/getskype-linux-beta-ubuntu-64](http://www.skype.com/go/getskype-linux-beta-ubuntu-64)
sudo apt-get install libqt4-dbus libqt4-network libqt4-xml libasound2
sudo dpkg -i getskype-linux-beta-ubuntu-64
sudo apt-get -f install

---

