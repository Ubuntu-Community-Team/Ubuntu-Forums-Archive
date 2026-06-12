---
title: "Gadmin-OPENVPN Can not write openvpn server sysinit"
date: 2009-04-20
forum: Networking &amp; Wireless
---

### Post by heavyt on 2009-04-20
I am trying to set up openvpn with gadmin-openvpn but I get this error when I tried to activate the server from the gui. ```
Can not write openvpn server sysinit script here: 
/etc/rc.d/init.d/gadmin-openvpn-server
```

And there isn´t a ***/etc/rc.d*** directory in Ubuntu. Do anyone have workaround or fix for this? Thanks
HeavyT

---

### Post by albinootje on 2009-04-20
> **heavyt said:**
> 
And there isn´t a ***/etc/rc.d*** directory in Ubuntu.

Which Ubuntu release are you using ?
The rpm packages on the Gadmin website are apparently only for "RH and Fedora 7-10".
See here for Ubuntu packages :
[http://packages.ubuntu.com/search?keywords=gadmin](http://packages.ubuntu.com/search?keywords=gadmin)

---

### Post by heavyt on 2009-04-20
> **albinootje said:**
> Which Ubuntu release are you using ?
The rpm packages on the Gadmin website are apparently only for "RH and Fedora 7-10".
See here for Ubuntu packages :
[http://packages.ubuntu.com/search?keywords=gadmin](http://packages.ubuntu.com/search?keywords=gadmin)

I am using Xubuntu 9.04 Release Candidate

---

### Post by albinootje on 2009-04-20
> **heavyt said:**
> I am using Xubuntu 9.04 Release Candidate

Okay, did you install the gadmin-openvpn-server package from Jaunty ?
I just checked the content of that specific package, and I can't find a mention of /etc/rc.d/ in it, so I guess you installed the rpm.
Can you remove the gadmin openvpn server package you have installed now, and then install the gadmin-openvpn-server from Jaunty, and see how that goes ?

---

### Post by heavyt on 2009-04-20
> **albinootje said:**
> Okay, did you install the gadmin-openvpn-server package from Jaunty ?
I just checked the content of that specific package, and I can't find a mention of /etc/rc.d/ in it, so I guess you installed the rpm.
Can you remove the gadmin openvpn server package you have installed now, and then install the gadmin-openvpn-server from Jaunty, and see how that goes ?

I did not use the rpm, I used the deb from synaptic package manager which installed gadmin-openvpn-server from Jaunty. This is the message that is displayed when I try to activate  gadmin-openvpn-server:

> [B]Can not write openvpn server sysinit script here: 
/etc/rc.d/init.d/gadmin-openvpn-server[/B]

```
home-ubuntu:~/Desktop$ sudo apt-get install gadmin-openvpn-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gadmin-openvpn-server is already the newest version.

home-ubuntu:~/Desktop$ dpkg -s  gadmin-openvpn-server
Package: gadmin-openvpn-server
Status: install ok installed
Priority: optional
Section: admin
Installed-Size: 244
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Version: 0.0.7-1
Depends: libatk1.0-0 (>= 1.20.0), libc6 (>= 2.4), libcairo2 (>= 1.2.4), libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.3.5), libglib2.0-0 (>= 2.16.0), libgtk2.0-0 (>= 2.14.0), libpango1.0-0 (>= 1.22.0), zlib1g (>= 1:1.1.4), menu, openvpn
Description: GTK+ configuration tool for openvpn (server)
 gadmin-openvpn-server is a fast and easy to use GTK+ administration tool for
 the OpenVPN server.
Original-Maintainer: Daniel Baumann <daniel@debian.org>
Homepage: http://www.gadmintools.org/
```

---

### Post by albinootje on 2009-04-21
> **heavyt said:**
> 
Can not write openvpn server sysinit script here:
/etc/rc.d/init.d/gadmin-openvpn-server

Okay, this is a bug which needs to be reported to the package maintainer.
Meanwhile you could try again after making a symbolic link :
```

sudo mkdir /etc/rc.d
sudo ln -s /etc/init.d /etc/rc.d

```

---

### Post by heavyt on 2009-04-21
> **albinootje said:**
> Okay, this is a bug which needs to be reported to the package maintainer.
Meanwhile you could try again after making a symbolic link :
```

sudo mkdir /etc/rc.d
sudo ln -s /etc/init.d /etc/rc.d

```
Thanks for your help.

Filed a bug report on launchpad bug #364619. Also did the symbolic link now it complains about > ***/usr/lib/openvpn/plugin/lib/openvpn-auth-pam.so: cannot open shared object file: No such file or directory***. Will work on it later today.

---

### Post by sta1n on 2010-01-13
I have the same Issue and im using ubuntu 9.10. Anyone got a solution?

---

### Post by BlackBird28 on 2010-01-17
> **sta1n said:**
> I have the same Issue and im using ubuntu 9.10. Anyone got a solution?

Here I am...same issue.

---

### Post by haris_led on 2010-01-19
Same problem here with ubuntu :(

---

### Post by nur fadilah on 2010-05-30
same here.. got that problem in ubuntu 10.04 server edition.

---

### Post by mox386 on 2010-08-25
> **albinootje said:**
> ```

sudo mkdir /etc/rc.d
sudo ln -s /etc/init.d /etc/rc.d

```

tried this it simply removes the prompt, still not able to activate the server.

---

