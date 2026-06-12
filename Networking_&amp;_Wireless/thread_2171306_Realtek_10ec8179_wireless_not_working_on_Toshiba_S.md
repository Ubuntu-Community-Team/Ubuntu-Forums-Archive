---
title: "Realtek 10ec:8179 wireless not working on Toshiba Satellite C40D"
date: 2013-08-30
forum: Networking &amp; Wireless
---

### Post by DistroHopper on 2013-08-30
Just bought a new Toshiba Satellite C40D and there is no wireless card found on Mint 15/Ubuntu 13.04. After I bunch of searches I found Chilli555's instructions here: [http://askubuntu.com/questions/337785/wireless-not-working-on-toshiba-satellite-c55-a5281](http://askubuntu.com/questions/337785/wireless-not-working-on-toshiba-satellite-c55-a5281) I realize that thy had a different toshiba but it has the same wireless card from what I can tell. 
My card comes up as [QUOTE="lspci -nn"]05:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8179] (rev 01)[/QUOTE]

Anyway I followed all those instructions and end up with FATAL: Module rtl8188ee not found and no wireless. I don't know if I did anything wrong but here's the details of everything I did:
```
tim@tim-Satellite-C40D-A ~ $ sudo apt-get update
[sudo] password for tim: 
Get:1 [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia Release.gpg [197 B]                 
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring Release.gpg [933 B]                     
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release.gpg [933 B] 
Get:4 [http://archive.canonical.com](http://archive.canonical.com) raring Release.gpg [933 B]                  
Get:5 [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia Release [17.7 kB]                   
Get:6 [http://archive.canonical.com](http://archive.canonical.com) raring Release [5,919 B]                    
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release [40.8 kB]             
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates Release.gpg [933 B]             
Get:9 [http://archive.canonical.com](http://archive.canonical.com) raring/partner amd64 Packages [3,100 B]     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring Release                                   
Get:10 [http://archive.canonical.com](http://archive.canonical.com) raring/partner i386 Packages [4,283 B]     
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates Release [40.8 kB]              
Get:12 [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia/main amd64 Packages [23.9 kB]      
Get:13 [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia/upstream amd64 Packages [9,108 B]  
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main amd64 Packages [96.9 kB]
Get:15 [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia/import amd64 Packages [39.0 kB]    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main amd64 Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted amd64 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe amd64 Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse amd64 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main i386 Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted i386 Packages                  
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted amd64 Packages [14 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe i386 Packages                    
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en_CA              
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe amd64 Packages [33.3 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse i386 Packages                  
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en                 
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main Translation-en_CA [8,055 B]       
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse amd64 Packages [3,702 B]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main i386 Packages [96.2 kB] 
Get:21 [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia/main i386 Packages [24.0 kB]       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main Translation-en                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse Translation-en                 
Get:22 [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia/upstream i386 Packages [9,093 B]   
Get:23 [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia/import i386 Packages [39.9 kB]     
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted i386 Packages [14 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted Translation-en                 
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe i386 Packages [33.9 kB]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe Translation-en_CA [663 B]     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe Translation-en                   
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main amd64 Packages [160 kB]   
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse i386 Packages [3,871 B]
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en [50.4 kB]
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en [1,826 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en       
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en [21.4 kB]
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted amd64 Packages [14 B]
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe amd64 Packages [141 kB]
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse amd64 Packages [3,702 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en_CA          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en_CA    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en_CA    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en_CA      
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia/import Translation-en_CA              
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia/import Translation-en                 
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia/main Translation-en_CA                
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main i386 Packages [158 kB]    
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia/main Translation-en                   
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia/upstream Translation-en_CA            
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia/upstream Translation-en               
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted i386 Packages [14 B]
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe i386 Packages [142 kB]
Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse i386 Packages [3,871 B]
Get:39 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main Translation-en [76.5 kB]  
Get:40 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse Translation-en [1,826 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted Translation-en         
Get:41 [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe Translation-en [74.3 kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse Translation-en_CA              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted Translation-en_CA              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe Translation-en_CA
Fetched 1,372 kB in 2min 44s (8,337 B/s)
Reading package lists... Done
tim@tim-Satellite-C40D-A ~ $ sudo apt-get install linux-headers-generic build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev g++ g++-4.7 libalgorithm-diff-perl libalgorithm-diff-xs-perl
  libalgorithm-merge-perl libstdc++6-4.7-dev linux-generic
  linux-headers-3.8.0-29 linux-headers-3.8.0-29-generic
  linux-image-3.8.0-29-generic linux-image-extra-3.8.0-29-generic
  linux-image-generic
Suggested packages:
  debian-keyring g++-multilib g++-4.7-multilib gcc-4.7-doc libstdc++6-4.7-dbg
  libstdc++6-4.7-doc fdutils linux-doc-3.8.0 linux-source-3.8.0 linux-tools
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.7 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libstdc++6-4.7-dev
  linux-headers-3.8.0-29 linux-headers-3.8.0-29-generic
  linux-image-3.8.0-29-generic linux-image-extra-3.8.0-29-generic
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic
3 upgraded, 12 newly installed, 0 to remove and 195 not upgraded.
Need to get 0 B/67.0 MB of archives.
After this operation, 265 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously unselected package linux-image-3.8.0-29-generic.
(Reading database ... 141074 files and directories currently installed.)
Unpacking linux-image-3.8.0-29-generic (from .../linux-image-3.8.0-29-generic_3.8.0-29.42_amd64.deb) ...
Done.
Selecting previously unselected package libstdc++6-4.7-dev:amd64.
Unpacking libstdc++6-4.7-dev:amd64 (from .../libstdc++6-4.7-dev_4.7.3-1ubuntu1_amd64.deb) ...
Selecting previously unselected package g++-4.7.
Unpacking g++-4.7 (from .../g++-4.7_4.7.3-1ubuntu1_amd64.deb) ...
Selecting previously unselected package g++.
Unpacking g++ (from .../g++_4%3a4.7.3-1ubuntu10_amd64.deb) ...
Selecting previously unselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.16.10ubuntu1_all.deb) ...
Selecting previously unselected package build-essential.
Unpacking build-essential (from .../build-essential_11.6ubuntu4_amd64.deb) ...
Selecting previously unselected package libalgorithm-diff-perl.
Unpacking libalgorithm-diff-perl (from .../libalgorithm-diff-perl_1.19.02-3_all.deb) ...
Selecting previously unselected package libalgorithm-diff-xs-perl.
Unpacking libalgorithm-diff-xs-perl (from .../libalgorithm-diff-xs-perl_0.04-2build3_amd64.deb) ...
Selecting previously unselected package libalgorithm-merge-perl.
Unpacking libalgorithm-merge-perl (from .../libalgorithm-merge-perl_0.08-2_all.deb) ...
Selecting previously unselected package linux-image-extra-3.8.0-29-generic.
Unpacking linux-image-extra-3.8.0-29-generic (from .../linux-image-extra-3.8.0-29-generic_3.8.0-29.42_amd64.deb) ...
Preparing to replace linux-generic 3.8.0.19.35 (using .../linux-generic_3.8.0.29.47_amd64.deb) ...
Unpacking replacement linux-generic ...
Preparing to replace linux-image-generic 3.8.0.19.35 (using .../linux-image-generic_3.8.0.29.47_amd64.deb) ...
Unpacking replacement linux-image-generic ...
Selecting previously unselected package linux-headers-3.8.0-29.
Unpacking linux-headers-3.8.0-29 (from .../linux-headers-3.8.0-29_3.8.0-29.42_all.deb) ...
Selecting previously unselected package linux-headers-3.8.0-29-generic.
Unpacking linux-headers-3.8.0-29-generic (from .../linux-headers-3.8.0-29-generic_3.8.0-29.42_amd64.deb) ...
Preparing to replace linux-headers-generic 3.8.0.19.35 (using .../linux-headers-generic_3.8.0.29.47_amd64.deb) ...
Unpacking replacement linux-headers-generic ...
Processing triggers for man-db ...
Setting up linux-image-3.8.0-29-generic (3.8.0-29.42) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-29-generic
Warning: No support for locale: en_CA.utf8
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found initrd image: /boot/initrd.img-3.8.0-19-generic
Found memtest86+ image: /boot/memtest86+.bin
  No volume groups found
done
Setting up libstdc++6-4.7-dev:amd64 (4.7.3-1ubuntu1) ...
Setting up g++-4.7 (4.7.3-1ubuntu1) ...
Setting up g++ (4:4.7.3-1ubuntu10) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode
Setting up dpkg-dev (1.16.10ubuntu1) ...
Setting up build-essential (11.6ubuntu4) ...
Setting up libalgorithm-diff-perl (1.19.02-3) ...
Setting up libalgorithm-diff-xs-perl (0.04-2build3) ...
Setting up libalgorithm-merge-perl (0.08-2) ...
Setting up linux-image-extra-3.8.0-29-generic (3.8.0-29.42) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-29-generic
Warning: No support for locale: en_CA.utf8
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found initrd image: /boot/initrd.img-3.8.0-19-generic
Found memtest86+ image: /boot/memtest86+.bin
  No volume groups found
done
Setting up linux-image-generic (3.8.0.29.47) ...
Setting up linux-headers-3.8.0-29 (3.8.0-29.42) ...
Setting up linux-headers-3.8.0-29-generic (3.8.0-29.42) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
Setting up linux-headers-generic (3.8.0.29.47) ...
Setting up linux-generic (3.8.0.29.47) ...
tim@tim-Satellite-C40D-A ~ $ cd Desktop
tim@tim-Satellite-C40D-A ~/Desktop $ make defconfig-rtlwifi
make: *** No rule to make target `defconfig-rtlwifi'.  Stop.
tim@tim-Satellite-C40D-A ~/Desktop $ cd b
tim@tim-Satellite-C40D-A ~/Desktop/b $ make defconfig-rtlwifi
Generating local configuration database from kernel ... done.
cc -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer   -c -o conf.o conf.c
cc -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer   -c -o zconf.tab.o zconf.tab.c
cc   conf.o zconf.tab.o   -o conf
#
# configuration written to .config
#
tim@tim-Satellite-C40D-A ~/Desktop/b $ make
make[5]: `conf' is up to date.
#
# configuration written to .config
#
Building backport-include/backport/autoconf.h ... done.
  CC [M]  /home/tim/Desktop/b/compat/main.o
  CC [M]  /home/tim/Desktop/b/compat/compat-3.9.o
  CC [M]  /home/tim/Desktop/b/compat/backport-3.10.o
  CC [M]  /home/tim/Desktop/b/compat/backport-3.11.o
  LD [M]  /home/tim/Desktop/b/compat/compat.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/base.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/cam.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/core.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/debug.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/efuse.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/ps.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rc.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/regd.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/stats.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/pci.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/usb.o
  LD [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtlwifi.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8188ee/dm.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8188ee/fw.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8188ee/hw.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8188ee/led.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8188ee/phy.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8188ee/pwrseq.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8188ee/pwrseqcmd.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8188ee/rf.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8188ee/sw.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8188ee/table.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8188ee/trx.o
  LD [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192c/main.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192c/dm_common.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192c/fw_common.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192c/phy_common.o
  LD [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192ce/dm.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192ce/hw.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192ce/led.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192ce/phy.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192ce/rf.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192ce/sw.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192ce/table.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192ce/trx.o
  LD [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192cu/dm.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192cu/hw.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192cu/led.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192cu/mac.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192cu/phy.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192cu/rf.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192cu/sw.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192cu/table.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192cu/trx.o
  LD [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192de/dm.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192de/fw.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192de/hw.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192de/led.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192de/phy.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192de/rf.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192de/sw.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192de/table.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192de/trx.o
  LD [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192de/rtl8192de.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192se/dm.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192se/fw.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192se/hw.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192se/led.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192se/phy.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192se/rf.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192se/sw.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192se/table.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192se/trx.o
  LD [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8723ae/dm.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8723ae/fw.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8723ae/hal_btc.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8723ae/hal_bt_coexist.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8723ae/hw.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8723ae/led.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8723ae/phy.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8723ae/pwrseq.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8723ae/pwrseqcmd.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8723ae/rf.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8723ae/sw.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8723ae/table.o
  CC [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8723ae/trx.o
  LD [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.o
  CC [M]  /home/tim/Desktop/b/net/mac80211/main.o
  CC [M]  /home/tim/Desktop/b/net/mac80211/status.o
  CC [M]  /home/tim/Desktop/b/net/mac80211/sta_info.o
  CC [M]  /home/tim/Desktop/b/net/mac80211/wep.o
  CC [M]  /home/tim/Desktop/b/net/mac80211/wpa.o
  CC [M]  /home/tim/Desktop/b/net/mac80211/scan.o
  CC [M]  /home/tim/Desktop/b/net/mac80211/offchannel.o
  CC [M]  /home/tim/Desktop/b/net/mac80211/ht.o
  CC [M]  /home/tim/Desktop/b/net/mac80211/agg-tx.o
  CC [M]  /home/tim/Desktop/b/net/mac80211/agg-rx.o
  CC [M]  /home/tim/Desktop/b/net/mac80211/vht.o
  CC [M]  /home/tim/Desktop/b/net/mac80211/ibss.o
  CC [M]  /home/tim/Desktop/b/net/mac80211/iface.o
  CC [M]  /home/tim/Desktop/b/net/mac80211/rate.o
  CC [M]  /home/tim/Desktop/b/net/mac80211/michael.o
  CC [M]  /home/tim/Desktop/b/net/mac80211/tkip.o
  CC [M]  /home/tim/Desktop/b/net/mac80211/aes_ccm.o
  CC [M]  /home/tim/Desktop/b/net/mac80211/aes_cmac.o
  CC [M]  /home/tim/Desktop/b/net/mac80211/cfg.o
  CC [M]  /home/tim/Desktop/b/net/mac80211/rx.o
  CC [M]  /home/tim/Desktop/b/net/mac80211/spectmgmt.o
  CC [M]  /home/tim/Desktop/b/net/mac80211/tx.o
  CC [M]  /home/tim/Desktop/b/net/mac80211/key.o
  CC [M]  /home/tim/Desktop/b/net/mac80211/util.o
  CC [M]  /home/tim/Desktop/b/net/mac80211/wme.o
  CC [M]  /home/tim/Desktop/b/net/mac80211/event.o
  CC [M]  /home/tim/Desktop/b/net/mac80211/chan.o
  CC [M]  /home/tim/Desktop/b/net/mac80211/trace.o
  CC [M]  /home/tim/Desktop/b/net/mac80211/mlme.o
  CC [M]  /home/tim/Desktop/b/net/mac80211/debugfs.o
  CC [M]  /home/tim/Desktop/b/net/mac80211/debugfs_sta.o
  CC [M]  /home/tim/Desktop/b/net/mac80211/debugfs_netdev.o
  CC [M]  /home/tim/Desktop/b/net/mac80211/debugfs_key.o
  CC [M]  /home/tim/Desktop/b/net/mac80211/pm.o
  LD [M]  /home/tim/Desktop/b/net/mac80211/mac80211.o
  CC [M]  /home/tim/Desktop/b/net/wireless/core.o
  CC [M]  /home/tim/Desktop/b/net/wireless/sysfs.o
  CC [M]  /home/tim/Desktop/b/net/wireless/radiotap.o
  CC [M]  /home/tim/Desktop/b/net/wireless/util.o
  CC [M]  /home/tim/Desktop/b/net/wireless/reg.o
  CC [M]  /home/tim/Desktop/b/net/wireless/scan.o
  CC [M]  /home/tim/Desktop/b/net/wireless/nl80211.o
  CC [M]  /home/tim/Desktop/b/net/wireless/mlme.o
  CC [M]  /home/tim/Desktop/b/net/wireless/ibss.o
  CC [M]  /home/tim/Desktop/b/net/wireless/sme.o
  CC [M]  /home/tim/Desktop/b/net/wireless/chan.o
  CC [M]  /home/tim/Desktop/b/net/wireless/ethtool.o
  CC [M]  /home/tim/Desktop/b/net/wireless/mesh.o
  CC [M]  /home/tim/Desktop/b/net/wireless/ap.o
  CC [M]  /home/tim/Desktop/b/net/wireless/trace.o
  CC [M]  /home/tim/Desktop/b/net/wireless/debugfs.o
  CC [M]  /home/tim/Desktop/b/net/wireless/wext-compat.o
  CC [M]  /home/tim/Desktop/b/net/wireless/wext-sme.o
  LD [M]  /home/tim/Desktop/b/net/wireless/cfg80211.o
  Building modules, stage 2.
  MODPOST 11 modules
  CC      /home/tim/Desktop/b/compat/compat.mod.o
  LD [M]  /home/tim/Desktop/b/compat/compat.ko
  CC      /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.mod.o
  LD [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
  CC      /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.mod.o
  LD [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
  CC      /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.mod.o
  LD [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
  CC      /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.mod.o
  LD [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
  CC      /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192de/rtl8192de.mod.o
  LD [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192de/rtl8192de.ko
  CC      /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.mod.o
  LD [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
  CC      /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.mod.o
  LD [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.ko
  CC      /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtlwifi.mod.o
  LD [M]  /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtlwifi.ko
  CC      /home/tim/Desktop/b/net/mac80211/mac80211.mod.o
  LD [M]  /home/tim/Desktop/b/net/mac80211/mac80211.ko
  CC      /home/tim/Desktop/b/net/wireless/cfg80211.mod.o
  LD [M]  /home/tim/Desktop/b/net/wireless/cfg80211.ko
tim@tim-Satellite-C40D-A ~/Desktop/b $ sudo make install
[sudo] password for tim: 
  Building modules, stage 2.
  MODPOST 11 modules
  INSTALL /home/tim/Desktop/b/compat/compat.ko
Can't read private key
  INSTALL /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
Can't read private key
  INSTALL /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
Can't read private key
  INSTALL /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
Can't read private key
  INSTALL /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
Can't read private key
  INSTALL /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192de/rtl8192de.ko
Can't read private key
  INSTALL /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
Can't read private key
  INSTALL /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.ko
Can't read private key
  INSTALL /home/tim/Desktop/b/drivers/net/wireless/rtlwifi/rtlwifi.ko
Can't read private key
  INSTALL /home/tim/Desktop/b/net/mac80211/mac80211.ko
Can't read private key
  INSTALL /home/tim/Desktop/b/net/wireless/cfg80211.ko
Can't read private key
  DEPMOD  3.8.0-19-generic
depmod will prefer updates/ over kernel/ -- OK!
Note:
You may or may not need to update your initramfs, you should if
any of the modules installed are part of your initramfs. To add
support for your distribution to do this automatically send a
patch against "update-initramfs.sh". If your distribution does not
require this send a patch with the '/usr/bin/lsb_release -i -s'
("Ubuntu") tag for your distribution to avoid this warning.

Your backported driver modules should be installed now.
Reboot.

tim@tim-Satellite-C40D-A ~/Desktop/b $ 
```

And then I after I rebooted:
```
tim@tim-Satellite-C40D-A ~/Desktop/b $ sudo modprobe rtl8188ee
[sudo] password for tim: 
FATAL: Module rtl8188ee not found.
```

Did I do anything wrong or does anyone know how to get my wireless working?

---

### Post by chili555 on 2013-08-30
Whew! You had me sweating and doubting myself! I hate when that happens!!!> Did I do anything wrong or does anyone know how to get my wireless working? Yes, I can. You compiled the driver for 3.8.0-19:> DEPMOD  3.8.0-[COLOR="#FF0000"]19[/COLOR]-genericHowever, one of the updates you installed was a later kernel version:> Setting up linux-image-generic (3.8.0[COLOR="#FF0000"].29.47[/COLOR]) ...
Setting up linux-headers-3.8.0-29 (3.8.0-29.42) ...
Setting up linux-headers-3.8.0-29-generic (3.8.0-29.42) ...When you rebooted, it was into -29.42 and not -19. You simply need to re-compile for the newer kernel version:```
cd Desktop/b
make clean
make defconfig-rtlwifi
make
sudo make install
```Reboot and let us hear your report.

The re-compile process was covered in my askubuntu post:> Your wireless should now be working. You will have compiled the driver for your currently running kernel only. When Update Manager installs a later linux-image, after reboot, re-compile:Now I can sleep again!

EDIT: I believe the 'Can't read private key' is harmless because the install doesn't end in an error and because I built my driver, iwlwifi, with the same package, had the same comment and the driver loads and drives my device perfectly.

---

### Post by DistroHopper on 2013-09-02
> **chili555 said:**
> You compiled the driver for 3.8.0-19:However, one of the updates you installed was a later kernel version:When you rebooted, it was into -29.42 and not -19. 
Ahhh I see what happened! When I installed [FONT=Ubuntu Mono]linux-headers-generic build-essential[/FONT] it updated the kernel and I didn't reboot.

I followed your instructions and the wifi now works! :D Thank you so so much! (if you could give reputation on here I would you give you some) 
Now I just need to get it to dual-boot with Win8, for my brother.

---

