---
title: "LXDE removed network-manager"
date: 2009-10-10
forum: Networking &amp; Wireless
---

### Post by xarhelios on 2009-10-10
I recently installed LXDE in an Ubuntu Virtual Machine, and It replaced network-manager with lxnm, but this "lxnm" cannot connect to my "wired" network for the VM to get internet, so I know I need to mount and boot into a liveCD to install the packages I need, but what are these? I want wicd, but are there dependancies?

and how do I install to my OS from a Live OS?

Thanks in advance, Xarhelios.

---

### Post by xarhelios on 2009-10-10
I was in kind of a rush at the time of writing this, so i will clarify a few details.

I want to know how to install network-manager or wicd FROM a live CD INTO my main Ubuntu OS.

I would like to say that I am using Virtualbox 3.0.8 in Windows 7 host, build 7100, Release Candidate (RC).  Maybe this is a question better suited for the virtualization board? Move if you find it to be more relevant elsewhere, mods.

The guest has 1GB ram, 150GB Hard Drive, and 256MB video memory. all of these specs can be delivered at any given time, so problems will not come from there. 

I tried running apt-get install wicd as root from the Live CD, but it output "cannot find selected packages." However, apt-get install network-manager said I already have the package, I am guessing this is because the LiveOS DOES have the package. 

Thanks in advance, Xarhelios

---

### Post by kevdog on 2009-10-10
You probably want wicd, but this isn't included on the live CD.  You need to add the repository to your /etc/apt/sources.list, then do a sudo aptitude update and then sudo aptitude install wicd.

The instructions are here:
[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by xarhelios on 2009-10-10
I grabbed the wicd .deb from 
[http://packages.ubuntu.com/jaunty/all/wicd/download](http://packages.ubuntu.com/jaunty/all/wicd/download)
and it all works fine now. 

thanks

---

