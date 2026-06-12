---
title: "DVD will not play; medibuntu AWOL?"
date: 2013-10-10
forum: Multimedia Software
---

### Post by sks24 on 2013-10-10
Having trouble getting dvds to play in a new 12.04/32 bit installation on a Dell xps m1530 laptop.  

I've tried a number of things.  I think the problem may be that the servers for medibuntu are down  (see below) 

I ended up here, and the software center shows that all of the following are installed: 
libdvdnav4, libdvdread4, gstreamer0.10-plugins-bad, and gstreamer0.10-plugins-ugly.

But I run into the 404 error when I run this: sudo /usr/share/doc/libdvdread4/install-css.sh

```
home@home-XPS-M1530:~$ sudo /usr/share/doc/libdvdread4/install-css.sh
[sudo] password for home: 
--2013-10-10 22:25:54--  http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages
Resolving packages.medibuntu.org (packages.medibuntu.org)... 88.191.127.22
Connecting to packages.medibuntu.org (packages.medibuntu.org)|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2013-10-10 22:25:55 ERROR 404: Not Found.

Dynamic fetch failed; Falling back to static fetch
--2013-10-10 22:25:55--  http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb
Resolving packages.medibuntu.org (packages.medibuntu.org)... 88.191.127.22
Connecting to packages.medibuntu.org (packages.medibuntu.org)|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2013-10-10 22:25:56 ERROR 404: Not Found.

home@home-XPS-M1530:~$ ^C
home@home-XPS-M1530:~$ 

```

The home menu on the dvd does appear - I can pick scenes and so forth - but the movie itself will not play.  

Soooo, I dunno.

---

### Post by oldfred on 2013-10-10
Thread above yours as I am just now looking at threads.
 Medibuntu repositories closing

[http://ubuntuforums.org/showthread.php?t=2174110](http://ubuntuforums.org/showthread.php?t=2174110)

Script has only been updated in new 13.10.
       Media howto: 
[http://ubuntuforums.org/showthread.php?t=2179777](http://ubuntuforums.org/showthread.php?t=2179777)
Older Ubuntu versions may not have new install-css.sh
[https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/)
(make sure to install/upgrade the libdvdread4 package first)
sudo apt-get install libdvdread4
new libdvdread 4 is already in 13.10
The new libdvdread4 has an updated install-css.sh that will install libdvdcss2 from a videolan repo
[https://launchpad.net/ubuntu/+source/libdvdread](https://launchpad.net/ubuntu/+source/libdvdread)
Medibuntu discontinured April 2013
[https://launchpad.net/medibuntu/+announcement/11219](https://launchpad.net/medibuntu/+announcement/11219)
[http://gauvain.pocentek.net/node/61](http://gauvain.pocentek.net/node/61)

---

### Post by sks24 on 2014-02-24
Thank you oldfred.  :^)

---

