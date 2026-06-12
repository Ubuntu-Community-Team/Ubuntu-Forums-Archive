---
title: "Installing Slimserver on Desktop 7.04 i386"
date: 2007-05-07
forum: Multimedia &amp; Video
---

### Post by ImpelGD on 2007-05-07
I've followed the instructions at [http://wiki.slimdevices.com/index.cgi?DebianPackage](http://wiki.slimdevices.com/index.cgi?DebianPackage) but get the following:

```

~$ sudo apt-get update
~$ sudo apt-get install slimserver
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libconvert-binhex-perl libclass-dbi-plugin-perl libsoap-lite-perl libclass-dbi-plugin-retrieveall-perl libneon26 vorbis-tools libcrypt-ssleay-perl libxml-namespacesupport-perl libapr1
  subversion libclass-dbi-pager-perl libsvn1 libxml-sax-perl libmime-perl libmime-lite-perl libfcgi-perl libdbd-sqlite3-perl libimlib2 libaprutil1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libclass-data-accessor-perl libclass-inspector-perl libdbix-class-perl
Recommended packages:
  libdatetime-format-mysql-perl libdatetime-format-db2-perl libdatetime-format-pg-perl
The following NEW packages will be installed
  libclass-data-accessor-perl libclass-inspector-perl libdbix-class-perl slimserver
0 upgraded, 4 newly installed, 0 to remove and 1 not upgraded.
Need to get 27.7kB/10.7MB of archives.
After unpacking 24.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  slimserver
Install these packages without verification [y/N]? y
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe libclass-data-accessor-perl 0.03-1 [10.7kB]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe libclass-inspector-perl 1.16-1 [17.0kB]
Fetched 28.4kB in 0s (66.5kB/s)           
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/universe/libc/libclass-data-accessor-perl/libclass-data-accessor-perl_0.03-1_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/universe/libc/libclass-data-accessor-perl/libclass-data-accessor-perl_0.03-1_all.deb)  Size mismatch
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/universe/libc/libclass-inspector-perl/libclass-inspector-perl_1.16-1_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/universe/libc/libclass-inspector-perl/libclass-inspector-perl_1.16-1_all.deb)  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

Have tried the stable, testing and unstable versions. I don't want to use the older version (although it works) from the Synapse Package Manager for other reasons.

Also can't seem to install the relevant archives using the 'Size mismatch error' section of the wiki page mentioned above.

I'm really stuck on this one. Have tried searching for clues but can only find [this thread]("http://forums.slimdevices.com/showthread.php?t=34742") which hasn't received an answer.

Thanks.

---

### Post by ninjaPants on 2007-05-13
I think the quickest workaround would probably to go to the Ubuntu Package Search, download those packages with the "size mismatch" and install them with dpkg or gdebi.
Package search is a default search engine on firefox, but if you've removed it, [here's a link.]("http://packages.ubuntu.com")
Hope this helps.
Andrew

---

### Post by ImpelGD on 2007-05-13
Yeah, thanks for replying ninjaPants (nice name!). I actually got it working by following [this reply]("http://forums.slimdevices.com/showpost.php?p=200237&postcount=9").

---

### Post by Raymond Day on 2007-07-15
I had to type this to get it installed. It would just come back with size mismatch on these two libclass files. Here are the commands I did and it worked.

wget [http://mirror.internode.on.net/pub/ubuntu/ubuntu/pool/universe/libc/libclass-data-accessor-perl/libclass-data-accessor-perl_0.03-1_all.deb](http://mirror.internode.on.net/pub/ubuntu/ubuntu/pool/universe/libc/libclass-data-accessor-perl/libclass-data-accessor-perl_0.03-1_all.deb)
dpkg -i libclass-data-accessor-perl_0.03-1_all.deb
wget [http://mirror.internode.on.net/pub/ubuntu/ubuntu/pool/universe/libc/libclass-inspector-perl/libclass-inspector-perl_1.16-1_all.deb](http://mirror.internode.on.net/pub/ubuntu/ubuntu/pool/universe/libc/libclass-inspector-perl/libclass-inspector-perl_1.16-1_all.deb)
dpkg -i libclass-inspector-perl_1.16-1_all.deb
apt-get install slimserver

I can then go to port 9000 and set up slimserver.

They should fix this size mismatch!

-Raymond Day

---

