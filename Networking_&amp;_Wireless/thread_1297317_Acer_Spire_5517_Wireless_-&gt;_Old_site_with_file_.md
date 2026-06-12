---
title: "Acer Spire 5517 Wireless -&gt; Old site with file no longer up"
date: 2009-10-21
forum: Networking &amp; Wireless
---

### Post by PaulTR on 2009-10-21
I have an Acer Aspire 5517 that I recently purchased and have put Ubuntu on as one of the partitions. After the installation I wasn't getting any internet connection, but I found a tutorial on how to get the eth0 running and so now I'm on with the ethernet cord plugged in, but I don't have the wireless working. I was going to go through the steps at [http://ubuntuforums.org/showthread.php?t=224350&highlight=3680-2682+wireless+card](http://ubuntuforums.org/showthread.php?t=224350&highlight=3680-2682+wireless+card) but the website that has the acer_acpi-0.3.tar.gz file is no longer there. Does anyone else have a link where I could find that file, or another tutorial so I can get my wireless up and running? Thanks!

---

### Post by PaulTR on 2009-10-21
Alright I've looked around for a few other tutorials, and still nothing's working. Anyone have any helpful advise for getting the wireless working? Under system>admin>network tools I'm seeing pan0 as unknown interface. On my other partition I have the wireless working fine under Vista. Is there any way to download the driver from the site and install it under Ubuntu?

---

### Post by chili555 on 2009-10-21
I am not sure but I think acer_acpi has been superceded with acerhk-source. (I have a crazed friend that says acerhk is a cure for everything; including a toothache!) Please try:```
sudo apt-get install acerhk-source
```Post back and let us know.

---

### Post by PaulTR on 2009-10-21
```

paul@paul-laptop:~$ sudo apt-get install acerhk-source
[sudo] password for paul: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  build-essential debhelper dpkg-dev g++ g++-4.3 gettext html2text
  intltool-debian libmail-sendmail-perl libstdc++6-4.3-dev
  libsys-hostname-long-perl module-assistant patch po-debconf
Suggested packages:
  dh-make debian-keyring g++-multilib g++-4.3-multilib gcc-4.3-doc
  libstdc++6-4.3-dbg cvs gettext-doc libstdc++6-4.3-doc diff-doc
  libmail-box-perl
The following NEW packages will be installed:
  acerhk-source build-essential debhelper dpkg-dev g++ g++-4.3 gettext
  html2text intltool-debian libmail-sendmail-perl libstdc++6-4.3-dev
  libsys-hostname-long-perl module-assistant patch po-debconf
0 upgraded, 15 newly installed, 0 to remove and 0 not upgraded.
Need to get 9267kB of archives.
After this operation, 32.2MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com jaunty/universe module-assistant 0.10.11ubuntu1 [100kB]
Get:2 http://us.archive.ubuntu.com jaunty/main patch 2.5.9-5 [100kB]
Get:3 http://us.archive.ubuntu.com jaunty/main dpkg-dev 1.14.24ubuntu1 [643kB]
Get:4 http://us.archive.ubuntu.com jaunty/main html2text 1.3.2a-5 [91.9kB]
Get:5 http://us.archive.ubuntu.com jaunty/main gettext 0.17-6ubuntu2 [1910kB]
Get:6 http://us.archive.ubuntu.com jaunty/main intltool-debian 0.35.0+20060710.1 [31.6kB]
Get:7 http://us.archive.ubuntu.com jaunty/main po-debconf 1.0.15ubuntu1 [237kB]
Get:8 http://us.archive.ubuntu.com jaunty/main debhelper 7.0.17ubuntu4 [549kB]
Get:9 http://us.archive.ubuntu.com jaunty/universe acerhk-source 0.5.35-4 [38.8kB]
Get:10 http://us.archive.ubuntu.com jaunty/main libstdc++6-4.3-dev 4.3.3-5ubuntu4 [1356kB]
Get:11 http://us.archive.ubuntu.com jaunty/main g++-4.3 4.3.3-5ubuntu4 [4162kB]
Get:12 http://us.archive.ubuntu.com jaunty/main g++ 4:4.3.3-1ubuntu1 [1438B]   
Get:13 http://us.archive.ubuntu.com jaunty/main build-essential 11.4 [7172B]   
Get:14 http://us.archive.ubuntu.com jaunty/main libsys-hostname-long-perl 1.4-2 [11.4kB]
Get:15 http://us.archive.ubuntu.com jaunty/main libmail-sendmail-perl 0.79.16-1 [26.5kB]
Fetched 9267kB in 7s (1266kB/s)                                                
Selecting previously deselected package module-assistant.
(Reading database ... 105691 files and directories currently installed.)
Unpacking module-assistant (from .../module-assistant_0.10.11ubuntu1_all.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.5.9-5_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.14.24ubuntu1_all.deb) ...
Selecting previously deselected package html2text.
Unpacking html2text (from .../html2text_1.3.2a-5_i386.deb) ...
Selecting previously deselected package gettext.
Unpacking gettext (from .../gettext_0.17-6ubuntu2_i386.deb) ...
Selecting previously deselected package intltool-debian.
Unpacking intltool-debian (from .../intltool-debian_0.35.0+20060710.1_all.deb) ...
Selecting previously deselected package po-debconf.
Unpacking po-debconf (from .../po-debconf_1.0.15ubuntu1_all.deb) ...
Selecting previously deselected package debhelper.
Unpacking debhelper (from .../debhelper_7.0.17ubuntu4_all.deb) ...
Selecting previously deselected package acerhk-source.
Unpacking acerhk-source (from .../acerhk-source_0.5.35-4_all.deb) ...
Selecting previously deselected package libstdc++6-4.3-dev.
Unpacking libstdc++6-4.3-dev (from .../libstdc++6-4.3-dev_4.3.3-5ubuntu4_i386.deb) ...
Selecting previously deselected package g++-4.3.
Unpacking g++-4.3 (from .../g++-4.3_4.3.3-5ubuntu4_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.3.3-1ubuntu1_i386.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.4_i386.deb) ...
Selecting previously deselected package libsys-hostname-long-perl.
Unpacking libsys-hostname-long-perl (from .../libsys-hostname-long-perl_1.4-2_all.deb) ...
Selecting previously deselected package libmail-sendmail-perl.
Unpacking libmail-sendmail-perl (from .../libmail-sendmail-perl_0.79.16-1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Setting up module-assistant (0.10.11ubuntu1) ...
Setting up patch (2.5.9-5) ...
Setting up dpkg-dev (1.14.24ubuntu1) ...
Setting up html2text (1.3.2a-5) ...

Setting up gettext (0.17-6ubuntu2) ...

Setting up intltool-debian (0.35.0+20060710.1) ...
Setting up po-debconf (1.0.15ubuntu1) ...

Setting up debhelper (7.0.17ubuntu4) ...

Setting up acerhk-source (0.5.35-4) ...
Setting up libsys-hostname-long-perl (1.4-2) ...
Setting up libmail-sendmail-perl (0.79.16-1) ...
Setting up g++-4.3 (4.3.3-5ubuntu4) ...
Setting up libstdc++6-4.3-dev (4.3.3-5ubuntu4) ...
Setting up g++ (4:4.3.3-1ubuntu1) ...

Setting up build-essential (11.4) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
paul@paul-laptop:~$ 

```

There's the output from that, but the wireless still isn't showing in the icon in the upper right corner, nor in system>admin>network tools.

---

### Post by chili555 on 2009-10-21
Please do:```
sudo modprobe acerhk
ifconfig
```Please let us see the output. When you manipulate the wireless key on your Acer, does the LED light up? Flicker? Anything? Thanks.

---

### Post by PaulTR on 2009-10-21
```

paul@paul-laptop:~$ sudo modprobe acerhk
[sudo] password for paul: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
paul@paul-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:22:1f:9f:ab  
          inet addr:192.168.1.117  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:22ff:fe1f:9fab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1748 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1464 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:1955675 (1.9 MB)  TX bytes:298366 (298.3 KB)
          Interrupt:251 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

paul@paul-laptop:~$ 

```

Nope, no flickering whatsoever from the LED.

---

### Post by calrogman on 2009-10-22
> **chili555 said:**
> I am not sure but I think acer_acpi has been superceded with acerhk-source. (I have a crazed friend that says acerhk is a cure for everything; including a toothache!) Please try:```
sudo apt-get install acerhk-source
```Post back and let us know.

First, I never claimed acerhk solved toothache.
Second, apt-getting the source for acerhk doesn't compile it.
Third, I only recommended using it in one case, where there was substantial evidence that it would work.
Fourth, acerhk is installed in Ubuntu 9.04 by default.
Fifth, loading the acerhk module is not enough, you need to `echo on | sudo tee /proc/driver/acerhk/wirelessled`.

That is all.

---

### Post by chili555 on 2009-10-22
I hope calrogman and the forum realize I was just having a little fun! I suggest that PaulTR do as suggested:```
sudo su
echo on | sudo tee /proc/driver/acerhk/wirelessled
```Any change in behavior?

---

