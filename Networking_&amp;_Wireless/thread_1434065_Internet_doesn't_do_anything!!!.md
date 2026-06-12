---
title: "Internet doesn't do anything!!!"
date: 2010-03-19
forum: Networking &amp; Wireless
---

### Post by volatilepyro on 2010-03-19
So I'm not really sure what it is exactly that I did but my internet just quit working. I can't connect to anything at all. I have an acer aspire 5532. It uses build in wireless but I just tried to connect using an ethernet cable and nothing happened. Still couldn't get on the internet. My wireless monitor won't even show up on the panel and I've tried to readd it and it doesn't work. Any help would be greatly appreciated. I have no need for a computer without internet.

---

### Post by Iowan on 2010-03-19
Check **sudo lshw -C network** (from terminal) to verify interface configuration. **ifconfig -a** *might* be helpful. By "wireless monitor" do you mean Network Manager? Have you checked the System>Preferences>Startup Applications to see if NM checkbox is selected?

---

### Post by volatilepyro on 2010-03-21
Yeah I was talking about the network manager and I tryed to remove and readd it and I can't figure out how to readd it. It wasn't showing up but it was checked and I didn't think it would be problematic but it is. That was after the internet had decided to quit.

---

### Post by volatilepyro on 2010-03-21
I ran sudo lshw -C network and it says that the network is disabled and ifconfig -a just pops up the status of eth0 lo and wlan0. How could I readd the network manager and enable my network???

---

### Post by volatilepyro on 2010-03-22
This is a fairly dire situation for me please help.

---

### Post by volatilepyro on 2010-03-22
If there is a command or anything or like a place in ubuntu to view and work with your hardware settings I haven't found it please tell me.

---

### Post by volatilepyro on 2010-03-24
Help please!!!

---

### Post by Iowan on 2010-03-24
Sorry - didn't mean to leave you hanging...
 If Network Manager is gone, you can try configuring */etc/network/interfaces *  to look like:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```Restart/reboot and see what happens.

---

### Post by mysterian077 on 2010-03-25
If you can't view the network manager, you can try running:
```
nm-applet --sm-disable
```
from a terminal. If it works, the Network manager applet should start up. If it fails, post the output here, and we can help you out some more.

---

### Post by volatilepyro on 2010-03-25
I ran nm-applet-applet --sm-disable.
   Code:The program 'nm-applet' can be found in the following packages:
* network-manager-gnome
* mythbuntu-diskless-client
Try: sudo apt-get install <selected package>
nm-applet: command not found
When I run sudo apt-get install nm-applet:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't fine package nm-applet
I ran sudo apt-get install network-manager-gnome:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
 Linux-headers-2.6.31-14 ;inux-backports-modules-2.6.31-19-generic-pae
 libgtk2-gladexml-perl libgnome2-gconf-perl
 linux-backports-modules-2.6.31-19-generic linux-headers-2.6.31-14-generic
 libnet1 ettercap-common
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  network-manager
The following NEW packages will be installed:
  network-manager network-manager-gnome
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 770kB of archives.
After this operation, 7,086kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic main network-manager 0.8~a~git.20091013t
193206.679d548-0ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.8~a~git.20091013t193206.679d548-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.8~a~git.20091013t193206.679d548-0ubuntu1_i386.deb)
  Could not resolve 'us.archive.ubuntu.com'
 Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.8~a~git.20091013t193206.679d548-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.8~a~git.20091013t193206.679d548-0ubuntu1_i386.deb)
  Could not resolve 'us.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by mysterian077 on 2010-03-25
Go to a computer with an internet connection (e.g. a library or friend's house) and download the following files:

[network-manager-gnome for 32-bit](http://mirrors.kernel.org/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.8~a~git.20091014t134532.4033e62-0ubuntu1_i386.deb) and [network-manager for 32-bit](http://mirrors.kernel.org/ubuntu/pool/main/n/network-manager/network-manager_0.8~a~git.20091013t193206.679d548-0ubuntu1_i386.deb). Just save them to a flash drive, CD-R, etc.

When you get back to your computer, copy the files to your home folder and run, from a terminal:
```
sudo dpkg -i network-manager*.deb
```
which should install network manager. 

Note that the .debs are specific to 32-bit Ubuntu. If you're unsure what type of Ubuntu you have, please run ```
uname -a
``` and post the results here.

---

### Post by volatilepyro on 2010-03-28
I just reinstalled ubuntu and got everything back up to working speed.

---

