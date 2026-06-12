---
title: "wireless isn't working"
date: 2011-01-10
forum: Networking &amp; Wireless
---

### Post by knr10 on 2011-01-10
I was having the same problem described in this thread,
[http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)
so I installed the required package from this website,
[http://packages.debian.org/squeeze/firmware-b43-lpphy-installer](http://packages.debian.org/squeeze/firmware-b43-lpphy-installer)
Now I am getting this error,

kristin@kristin-HP-Mini:~/Downloads$ sudo dpkg -i firmware-b43-lpphy-installer_4.174.64.19-4_all.deb 
(Reading database ... 114219 files and directories currently installed.)
Unpacking firmware-b43-lpphy-installer (from firmware-b43-lpphy-installer_4.174.64.19-4_all.deb) ...
Setting up firmware-b43-lpphy-installer (4.174.64.19-4) ...
--2011-01-09 19:24:40--  [http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2)
Resolving downloads.openwrt.org... failed: Name or service not known.
wget: unable to resolve host address `downloads.openwrt.org'
dpkg: error processing firmware-b43-lpphy-installer (--install):
 subprocess installed post-installation script returned error exit status 4
Errors were encountered while processing:
 firmware-b43-lpphy-installer

I don't have internet access on that machine until I can get the wireless to work so I can't use the software center.

---

### Post by PatchesTheCaveman on 2011-01-10
There's another method that will probably be easier in your situation.

Download this file:  [http://downloads.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)

Transfer it to your computer.  Open a terminal and *cd* to the directory that file is stored in.  Then run these commands:
```
tar xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
sudo b43-fwcutter -w /lib/firmware/ wl_apsta_mimo.o
```

Your wireless should now work.  If not, try restarting the b43 driver:
```
sudo modprobe -r b43
sudo modprobe -r ssb
sudo modprobe b43
```

---

### Post by knr10 on 2011-01-10
Thank you so much!! I've been trying to get this to work for a while and this finally ended up working.

---

