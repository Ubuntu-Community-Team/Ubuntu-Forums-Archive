---
title: "Software Center, Synaptic Package Manager and Update Manager will not download."
date: 2011-12-07
forum: Networking &amp; Wireless
---

### Post by geebob on 2011-12-07
I am running Ubuntu 11.04 on a Dell INspiron 1501.  From SC, I get a message that says the packages failed to download and that I should check my internet connection, which is working since I am posting this.  From SPM I am told the packages are unverified (also UM says same thing).

I don't know if this has anything to do with Dansguardian that I tried unsuccesfully to use on this computer.

From another thread on a similar problem, I followed the advice to change my source in software center to the "best source".  This did not help and resulted in software options disappearing from SC and SPM.





I recieved this from SPM

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/html2text/html2text_1.3.2a-15_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/html2text/html2text_1.3.2a-15_i386.deb)
  Could not connect to 10.0.0.2:8080 (10.0.0.2). - connect (113: No route to host)


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/po-debconf/po-debconf_1.0.16+nmu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/po-debconf/po-debconf_1.0.16+nmu1_all.deb)
  Unable to connect to 10.0.0.2:8080:


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/d/debhelper/debhelper_8.1.2ubuntu4_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/d/debhelper/debhelper_8.1.2ubuntu4_all.deb)
  Unable to connect to 10.0.0.2:8080:


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsys-hostname-long-perl/libsys-hostname-long-perl_1.4-2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsys-hostname-long-perl/libsys-hostname-long-perl_1.4-2_all.deb)
  Unable to connect to 10.0.0.2:8080:


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libm/libmail-sendmail-perl/libmail-sendmail-perl_0.79.16-1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libm/libmail-sendmail-perl/libmail-sendmail-perl_0.79.16-1_all.deb)
  Unable to connect to 10.0.0.2:8080:


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/m/module-assistant/module-assistant_0.11.3ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/m/module-assistant/module-assistant_0.11.3ubuntu1_all.deb)
  Unable to connect to 10.0.0.2:8080:


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.56+r2729-1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.56+r2729-1_all.deb)
  Unable to connect to 10.0.0.2:8080:


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-source_1.56+r2729-1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-source_1.56+r2729-1_all.deb)
  Unable to connect to 10.0.0.2:8080:


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.56+r2729-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.56+r2729-1_i386.deb)
  Unable to connect to 10.0.0.2:8080:

---

### Post by geebob on 2011-12-07
I have tried to download a variety of software, it is not limited to just a few types of packages.

---

### Post by BC59 on 2011-12-07
Try to change your sources.list maybe is corrupted.

---

### Post by BC59 on 2011-12-07
Could you please post your sources.list?


```
sudo gedit /etc/apt/sources.list
```

---

### Post by geebob on 2011-12-07
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security multiverse

---

### Post by BC59 on 2011-12-07
I would comment with hash (#) in front of the repositories 

deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main

because are for developers and maybe they are creating issues.

Then update and try to see if it's working. The problem is that some unstable packages are already installed.

---

### Post by geebob on 2011-12-07
It didn't work.  Update manager rejected the updates as untrusted packages from x.org x server.

I don't even think that I am getting updates from canonical.

Just so the slate remains clean, I undid the hashes.

---

### Post by BC59 on 2011-12-07
As a last resource try to these

```
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get -f upgrade
sudo apt-get dist-upgrade --fix-missing
```

---

### Post by matt_symes on 2011-12-07
Hi

> I don't know if this has anything to do with Dansguardian that I tried unsuccessfully to use on this computer.> Could not connect to **10.0.0.2:8080** (10.0.0.2). - connect (113: No route to host)Dansguardian uses a proxy ? (Never used it). It's trying to connect to a private IP range address.

What's the IP address of your PC ? From the terminal

```
ifconfig
```Post back results here.

Kind regards

---

### Post by geebob on 2011-12-07
Matt Symes, here is the response I got.

eth0      Link encap:Ethernet  HWaddr 00:1d:09:b7:07:a1  
          inet addr:10.0.0.3  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:feb7:7a1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23377 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21417 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23439711 (23.4 MB)  TX bytes:3099542 (3.0 MB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:46 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3600 (3.6 KB)  TX bytes:3600 (3.6 KB)


I removed Dansgaurdian a day or two ago and I thought I removed tinyproxy, but I'm not sure I managed to remove all the packages that I used for Dansguardian.


BC59:  Here is the response I got:


Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  clamav clamav-freshclam clamav-base libclamav6 dhcp3-server libtommath0
  isc-dhcp-server
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
rob@friend:~$ sudo apt-get -f upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  xserver-xorg-video-intel
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 224 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Abort.


I still have the same issue after trying SC


This is all I have time for today.  Thank you gentlemen for your assistance thus far.

---

### Post by matt_symes on 2011-12-07
Hi

apt is trying to route through an IP address on your local subnet by the looks of it. 

This may have been due to Dansguardian trying to route through a proxy. Did you completely remove Dansguardian ? Did you install a proxy ?

I have never used Dansguardian so this is all supposition. 

Did you follow a tutorial to configure it ? 

If you did then please post a link to the tutorial. If not then please explain how you installed and configured it.

Kind regards

---

