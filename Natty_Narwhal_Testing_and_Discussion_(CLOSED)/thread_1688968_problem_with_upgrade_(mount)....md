---
title: "problem with upgrade (mount)..."
date: 2011-02-16
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by zika on 2011-02-16
```
Resolving dependencies...                
The following NEW packages will be installed:
  libunity3{a} 
The following packages will be upgraded:
  bsdutils chromium-browser chromium-browser-inspector computer-janitor computer-janitor-gtk cpp-4.4 empathy empathy-common gcc-4.4 gcc-4.4-base jockey-common jockey-gtk libblkid1 libcap2 libgudev-1.0-0 libperl5.10 libraw1394-11 libsdl1.2debian libsdl1.2debian-pulseaudio libsensors4 
  libsgutils2-2 libtextcat-data-utf8 libudev0 libuuid1 mount nautilus-sendto-empathy network-manager-gnome passwd perl perl-base perl-modules software-center udev util-linux uuid-runtime 
The following packages are RECOMMENDED but will NOT be installed:
  chromium-browser-l10n 
35 packages upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0 B/38.5 MB of archives. After unpacking 463 kB will be used.
Do you want to continue? [Y/n/?] 
Extracting templates from packages: 100% 
Preconfiguring packages ...
(Reading database ... 168475 files and directories currently installed.)
Preparing to replace mount 2.17.2-3.3ubuntu4 (using .../mount_2.17.2-9.1ubuntu1_amd64.deb) ...
/var/lib/dpkg/tmp.ci/preinst: 49: dpkg-vendor: not found
dpkg: error processing /var/cache/apt/archives/mount_2.17.2-9.1ubuntu1_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/mount_2.17.2-9.1ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:                                         
:~$ 
```

---

### Post by myrryr on 2011-02-16
yeah, there is a bug in I think the cups upgrade, you need dpkg-vendor...

which is in dpkg-dev

so install that package with 

apt-get install dpkg-dev

then you will be able to run your upgrade.

---

### Post by zika on 2011-02-16
> **myrryr said:**
> yeah, there is a bug in I think the cups upgrade, you need dpkg-vendor...

which is in dpkg-dev

so install that package with 

apt-get install dpkg-dev

then you will be able to run your upgrade.
```
:~$ sudo apt-get install dpkg-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  build-essential fakeroot g++ g++-4.5 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libdpkg-perl
  libstdc++6-4.5-dev patch
Suggested packages:
  debian-keyring g++-multilib g++-4.5-multilib gcc-4.5-doc libstdc++6-4.5-dbg
  libstdc++6-4.5-doc diffutils-doc
The following NEW packages will be installed:
  build-essential dpkg-dev fakeroot g++ g++-4.5 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libdpkg-perl
  libstdc++6-4.5-dev patch
0 upgraded, 11 newly installed, 0 to remove and 2 not upgraded.
Need to get 9,046 kB of archives.
After this operation, 29.5 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
```
That might be a patch but that doesn't look like solution...

---

### Post by MadCow108 on 2011-02-16
[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/719754](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/719754)

be patient, it will get fixed properly soon

---

### Post by myrryr on 2011-02-16
oh hell yes, that is not the long term fix :)

I think a bug has been raised against the offending package already. So it shouldn't take long for that to be fixed.

If you are interested in upgrading right now, then using the dev package will get you there. 

Otherwise, its waiting time, or fix the package, in which case you will need the dev package anyway. :)

---

### Post by zika on 2011-02-16
> **myrryr said:**
> oh hell yes, that is not the long term fix :)

I think a bug has been raised against the offending package already. So it shouldn't take long for that to be fixed.

If you are interested in upgrading right now, then using the dev package will get you there. 

Otherwise, its waiting time, or fix the package, in which case you will need the dev package anyway. :)I'll wait. All other packages are, already, upgraded...
Thank You...

---

### Post by zika on 2011-02-16
> **MadCow108 said:**
> [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/719754](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/719754)

be patient, it will get fixed properly soonI do not think that any of us testing could be called patient, but... :)
I'll be patient as much as it is possible... :)

---

### Post by MadCow108 on 2011-02-16
see it as an test of the dpkg-dev dependencies ;)

---

### Post by zika on 2011-02-16
> **MadCow108 said:**
> see it as an test of the dpkg-dev dependencies ;)[img]http://www.burningblood.it/forum/emoticon-ok.gif[/img]

---

### Post by Harry33 on 2011-02-16
> **zika said:**
> [img]http://www.burningblood.it/forum/emoticon-ok.gif[/img]

Now this bug has been fixed, a new version is available: 2.17.2-9.1ububntu2
Here: [https://launchpad.net/ubuntu/natty/+source/util-linux/2.17.2-9.1ubuntu2](https://launchpad.net/ubuntu/natty/+source/util-linux/2.17.2-9.1ubuntu2)

---

### Post by zika on 2011-02-16
> **Harry33 said:**
> Now this bug has been fixed, a new version is available: 2.17.2-9.1ububntu2
Here: [https://launchpad.net/ubuntu/natty/+source/util-linux/2.17.2-9.1ubuntu2](https://launchpad.net/ubuntu/natty/+source/util-linux/2.17.2-9.1ubuntu2)
[img]http://www.burningblood.it/forum/emoticon-ok.gif[/img]
Marking „solved“...

---

