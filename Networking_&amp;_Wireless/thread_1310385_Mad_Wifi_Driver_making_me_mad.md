---
title: "Mad Wifi Driver making me mad"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by larkdarklin on 2009-11-01
Can someone assist in making heads or tails of this info. Trying to get my Atheros ar5211 working under 8.10. I'm getting errors during the install and not sure why. I'm a newbie to Ubuntu so step by step assistance would be greatly appreciated. 

Thanks for your time and knowledge. 

SGM



root@sgm-laptop:~# sudo apt-get -y install build-essential bin86
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@sgm-laptop:~# sudo apt-get -y install build-essential bin86
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-24-generic linux-headers-2.6.24-24
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dpkg-dev g++ g++-4.2 libc6-dev libstdc++6-4.2-dev libtimedate-perl
  linux-libc-dev patch
Suggested packages:
  debian-keyring g++-multilib g++-4.2-multilib gcc-4.2-doc libstdc++6-4.2-dbg
  glibc-doc manpages-dev libstdc++6-4.2-doc diff-doc
The following NEW packages will be installed:
  bin86 build-essential dpkg-dev g++ g++-4.2 libc6-dev libstdc++6-4.2-dev
  libtimedate-perl linux-libc-dev patch
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 8800kB of archives.
After this operation, 34.5MB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main bin86 0.16.17-2ubuntu1 [84.6kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main linux-libc-dev 2.6.24-25.63 [707kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main libc6-dev 2.7-10ubuntu5 [3344kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main libstdc++6-4.2-dev 4.2.4-1ubuntu4 [1187kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main g++-4.2 4.2.4-1ubuntu4 [2784kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main g++ 4:4.2.3-1ubuntu6 [1440B]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libtimedate-perl 1.1600-9 [30.1kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main patch 2.5.9-4 [95.6kB]           
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main dpkg-dev 1.14.16.6ubuntu4 [559kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main build-essential 11.3ubuntu1 [7066B]
Fetched 8800kB in 16s (537kB/s)                                                
Selecting previously deselected package bin86.
(Reading database ... 114257 files and directories currently installed.)
Unpacking bin86 (from .../bin86_0.16.17-2ubuntu1_i386.deb) ...
Selecting previously deselected package linux-libc-dev.
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.24-25.63_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.7-10ubuntu5_i386.deb) ...
Selecting previously deselected package libstdc++6-4.2-dev.
Unpacking libstdc++6-4.2-dev (from .../libstdc++6-4.2-dev_4.2.4-1ubuntu4_i386.deb) ...
Selecting previously deselected package g++-4.2.
Unpacking g++-4.2 (from .../g++-4.2_4.2.4-1ubuntu4_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.2.3-1ubuntu6_i386.deb) ...
Selecting previously deselected package libtimedate-perl.
Unpacking libtimedate-perl (from .../libtimedate-perl_1.1600-9_all.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.5.9-4_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.14.16.6ubuntu4_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3ubuntu1_i386.deb) ...
Setting up bin86 (0.16.17-2ubuntu1) ...
Setting up linux-libc-dev (2.6.24-25.63) ...
Setting up libc6-dev (2.7-10ubuntu5) ...
Setting up libtimedate-perl (1.1600-9) ...
Setting up patch (2.5.9-4) ...
Setting up dpkg-dev (1.14.16.6ubuntu4) ...
Setting up libstdc++6-4.2-dev (4.2.4-1ubuntu4) ...
Setting up g++-4.2 (4.2.4-1ubuntu4) ...
Setting up g++ (4:4.2.3-1ubuntu6) ...

Setting up build-essential (11.3ubuntu1) ...
root@sgm-laptop:~# sub apt-get -y install sharutils
bash: sub: command not found
root@sgm-laptop:~# sudeo apt-get -y install sharutils
bash: sudeo: command not found
root@sgm-laptop:~# sudo apt-get -y install sharutils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-24-generic linux-headers-2.6.24-24
Use 'apt-get autoremove' to remove them.
Suggested packages:
  mailx
The following NEW packages will be installed:
  sharutils
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 108kB of archives.
After this operation, 991kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main sharutils 1:4.6.3-1build1 [108kB]
Fetched 108kB in 1s (73.2kB/s)   
Selecting previously deselected package sharutils.
(Reading database ... 116185 files and directories currently installed.)
Unpacking sharutils (from .../sharutils_1%3a4.6.3-1build1_i386.deb) ...
Setting up sharutils (1:4.6.3-1build1) ...

root@sgm-laptop:~# cd/usr
bash: cd/usr: No such file or directory
root@sgm-laptop:~# cd /usr
root@sgm-laptop:/usr# /src
bash: /src: No such file or directory
root@sgm-laptop:/usr# .src
bash: .src: command not found
root@sgm-laptop:/usr# cd /src
bash: cd: /src: No such file or directory
root@sgm-laptop:/usr# cd /src
bash: cd: /src: No such file or directory
root@sgm-laptop:/usr# cd usr/src/madwifi-0.9.3.2
bash: cd: usr/src/madwifi-0.9.3.2: No such file or directory
root@sgm-laptop:/usr# cd..
bash: cd..: command not found
root@sgm-laptop:/usr# cd /usr/src/madwifi-0.9.3.2
root@sgm-laptop:/usr/src/madwifi-0.9.3.2# sudo make clean
for i in ./ath ./ath_hal ./ath_rate ./net80211; do \
        make -C $i clean; \
    done
make[1]: Entering directory `/usr/src/madwifi-0.9.3.2/ath'
rm -f *~ *.o *.ko *.mod.c .*.cmd
rm -f .depend .version .*.o.flags .*.o.d
rm -rf .tmp_versions
make[1]: Leaving directory `/usr/src/madwifi-0.9.3.2/ath'
make[1]: Entering directory `/usr/src/madwifi-0.9.3.2/ath_hal'
rm -f *~ *.o *.ko *.mod.c uudecode .*.cmd
rm -f .depend .version .*.o.flags .*.o.d
rm -rf .tmp_versions
make[1]: Leaving directory `/usr/src/madwifi-0.9.3.2/ath_hal'
make[1]: Entering directory `/usr/src/madwifi-0.9.3.2/ath_rate'
for i in amrr/ onoe/ sample/; do \
        make -C $i clean; \
    done
make[2]: Entering directory `/usr/src/madwifi-0.9.3.2/ath_rate/amrr'
rm -f *~ *.o *.ko *.mod.c
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/usr/src/madwifi-0.9.3.2/ath_rate/amrr'
make[2]: Entering directory `/usr/src/madwifi-0.9.3.2/ath_rate/onoe'
rm -f *~ *.o *.ko *.mod.c
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/usr/src/madwifi-0.9.3.2/ath_rate/onoe'
make[2]: Entering directory `/usr/src/madwifi-0.9.3.2/ath_rate/sample'
rm -f *~ *.o *.ko *.mod.c
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/usr/src/madwifi-0.9.3.2/ath_rate/sample'
make[1]: Leaving directory `/usr/src/madwifi-0.9.3.2/ath_rate'
make[1]: Entering directory `/usr/src/madwifi-0.9.3.2/net80211'
rm -f *~ *.o *.ko *.mod.c
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[1]: Leaving directory `/usr/src/madwifi-0.9.3.2/net80211'
make -C ./tools  clean
make[1]: Entering directory `/usr/src/madwifi-0.9.3.2/tools'
rm -f athstats 80211stats athkey athchans athctrl athdebug 80211debug wlanconfig core a.out
make[1]: Leaving directory `/usr/src/madwifi-0.9.3.2/tools'
rm -rf .tmp_versions
rm -f *.symvers svnversion.h
root@sgm-laptop:/usr/src/madwifi-0.9.3.2# sudo make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-25-generic/build SUBDIRS=/usr/src/madwifi-0.9.3.2 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-25-generic'
  CC [M]  /usr/src/madwifi-0.9.3.2/ath/if_ath.o
  CC [M]  /usr/src/madwifi-0.9.3.2/ath/if_ath_pci.o
/usr/src/madwifi-0.9.3.2/ath/if_ath_pci.c: In function 'ath_pci_probe':
/usr/src/madwifi-0.9.3.2/ath/if_ath_pci.c:203: error: 'struct net_device' has no member named 'owner'
make[3]: *** [/usr/src/madwifi-0.9.3.2/ath/if_ath_pci.o] Error 1
make[2]: *** [/usr/src/madwifi-0.9.3.2/ath] Error 2
make[1]: *** [_module_/usr/src/madwifi-0.9.3.2] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-25-generic'
make: *** [modules] Error 2
root@sgm-laptop:/usr/src/madwifi-0.9.3.2# sudo make install
sh scripts/find-madwifi-modules.sh 2.6.24-25-generic 

WARNING:
It seems that there are modules left from previous MadWifi installations.
If you are unistalling the MadWifi modules please press "r" to remove them.
If you are installing new MadWifi modules, you should consider removing those
already installed, or else you may experience problems during operation.
Remove old modules?

[l]ist, [r]emove, [i]gnore or e[x]it (l,r,i,[x]) ? 
r
for i in ./ath ./ath_hal ./ath_rate ./net80211; do \
        make -C $i install || exit 1; \
    done
make[1]: Entering directory `/usr/src/madwifi-0.9.3.2/ath'
test -d //lib/modules/2.6.24-25-generic/net || mkdir -p //lib/modules/2.6.24-25-generic/net
install ath_pci.ko //lib/modules/2.6.24-25-generic/net
install: cannot stat `ath_pci.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/usr/src/madwifi-0.9.3.2/ath'
make: *** [install-modules] Error 1
root@sgm-laptop:/usr/src/madwifi-0.9.3.2# sudomodprobe ath_pci
bash: sudomodprobe: command not found
root@sgm-laptop:/usr/src/madwifi-0.9.3.2# sudo probe ath_pci
sudo: probe: command not found
root@sgm-laptop:/usr/src/madwifi-0.9.3.2# sudo modprobie ath_pci
sudo: modprobie: command not found
root@sgm-laptop:/usr/src/madwifi-0.9.3.2# sudo modprobe ath_pci
WARNING: Could not open '/lib/modules/2.6.24-25-generic/volatile/ath_hal.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.24-25-generic/madwifi/wlan.ko': No such file or directory
FATAL: Could not open '/lib/modules/2.6.24-25-generic/madwifi/ath_pci.ko': No such file or directory
root@sgm-laptop:/usr/src/madwifi-0.9.3.2# make clean
for i in ./ath ./ath_hal ./ath_rate ./net80211; do \
        make -C $i clean; \
    done
make[1]: Entering directory `/usr/src/madwifi-0.9.3.2/ath'
rm -f *~ *.o *.ko *.mod.c .*.cmd
rm -f .depend .version .*.o.flags .*.o.d
rm -rf .tmp_versions
make[1]: Leaving directory `/usr/src/madwifi-0.9.3.2/ath'
make[1]: Entering directory `/usr/src/madwifi-0.9.3.2/ath_hal'
rm -f *~ *.o *.ko *.mod.c uudecode .*.cmd
rm -f .depend .version .*.o.flags .*.o.d
rm -rf .tmp_versions
make[1]: Leaving directory `/usr/src/madwifi-0.9.3.2/ath_hal'
make[1]: Entering directory `/usr/src/madwifi-0.9.3.2/ath_rate'
for i in amrr/ onoe/ sample/; do \
        make -C $i clean; \
    done
make[2]: Entering directory `/usr/src/madwifi-0.9.3.2/ath_rate/amrr'
rm -f *~ *.o *.ko *.mod.c
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/usr/src/madwifi-0.9.3.2/ath_rate/amrr'
make[2]: Entering directory `/usr/src/madwifi-0.9.3.2/ath_rate/onoe'
rm -f *~ *.o *.ko *.mod.c
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/usr/src/madwifi-0.9.3.2/ath_rate/onoe'
make[2]: Entering directory `/usr/src/madwifi-0.9.3.2/ath_rate/sample'
rm -f *~ *.o *.ko *.mod.c
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/usr/src/madwifi-0.9.3.2/ath_rate/sample'
make[1]: Leaving directory `/usr/src/madwifi-0.9.3.2/ath_rate'
make[1]: Entering directory `/usr/src/madwifi-0.9.3.2/net80211'
rm -f *~ *.o *.ko *.mod.c
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[1]: Leaving directory `/usr/src/madwifi-0.9.3.2/net80211'
make -C ./tools  clean
make[1]: Entering directory `/usr/src/madwifi-0.9.3.2/tools'
rm -f athstats 80211stats athkey athchans athctrl athdebug 80211debug wlanconfig core a.out
make[1]: Leaving directory `/usr/src/madwifi-0.9.3.2/tools'
rm -rf .tmp_versions
rm -f *.symvers svnversion.h
root@sgm-laptop:/usr/src/madwifi-0.9.3.2# sudo make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-25-generic/build SUBDIRS=/usr/src/madwifi-0.9.3.2 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-25-generic'
  CC [M]  /usr/src/madwifi-0.9.3.2/ath/if_ath.o
  CC [M]  /usr/src/madwifi-0.9.3.2/ath/if_ath_pci.o
/usr/src/madwifi-0.9.3.2/ath/if_ath_pci.c: In function 'ath_pci_probe':
/usr/src/madwifi-0.9.3.2/ath/if_ath_pci.c:203: error: 'struct net_device' has no member named 'owner'
make[3]: *** [/usr/src/madwifi-0.9.3.2/ath/if_ath_pci.o] Error 1
make[2]: *** [/usr/src/madwifi-0.9.3.2/ath] Error 2
make[1]: *** [_module_/usr/src/madwifi-0.9.3.2] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-25-generic'
make: *** [modules] Error 2
root@sgm-laptop:/usr/src/madwifi-0.9.3.2# sudo make install
sh scripts/find-madwifi-modules.sh 2.6.24-25-generic 
for i in ./ath ./ath_hal ./ath_rate ./net80211; do \
        make -C $i install || exit 1; \
    done
make[1]: Entering directory `/usr/src/madwifi-0.9.3.2/ath'
test -d //lib/modules/2.6.24-25-generic/net || mkdir -p //lib/modules/2.6.24-25-generic/net
install ath_pci.ko //lib/modules/2.6.24-25-generic/net
install: cannot stat `ath_pci.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/usr/src/madwifi-0.9.3.2/ath'
make: *** [install-modules] Error 1

---

