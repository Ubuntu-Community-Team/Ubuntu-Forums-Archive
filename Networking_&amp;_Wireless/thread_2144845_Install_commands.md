---
title: "Install commands"
date: 2013-05-13
forum: Networking &amp; Wireless
---

### Post by Podimore on 2013-05-13
I am in the process of installing a new wireless card driver after upgrading to 12.04. I have lost the thread with the advice given. i have downloaded it, extracted the file and used sudo make command. Its now ready to install but i dont know the install command. sudo install is not being accepted. any help appreciated

---

### Post by praseodym on 2013-05-13
With

```
sudo make install
```
it should work. What driver is it? Please show:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by Podimore on 2013-05-13
hi
result is liz@liz-N220:~$ ```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions
```

i have recently upgraded to 12.04 and my wireless is no longer working . got advice from forum and downloaded new driver but its still not working

liz@liz-N220:~$ ```
lspci -nnk | grep -iA2 net
05:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192E/RTL8192SE Wireless LAN Controller [10ec:8192] (rev 01)
    Subsystem: Askey Computer Corp. Device [144f:7160]
    Kernel modules: r8192e_pci, rtl8192se
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354]
    Subsystem: Samsung Electronics Co Ltd Device [144d:c072]
    Kernel driver in use: sky2
liz@liz-N220:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0ac8:c33f Z-Star Microelectronics Corp. Webcam
Bus 004 Device 002: ID 0a5c:219b Broadcom Corp. Bluetooth 2.1 Device
liz@liz-N220:~$ lsmod
Module                  Size  Used by
joydev                 17393  0 
samsung_backlight      13487  0 
samsung_laptop         13386  0 
snd_hda_codec_realtek   174313  1 
snd_hda_intel          32719  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
snd_seq_midi_event     14475  1 snd_seq_midi
psmouse                96718  0 
btusb                  17948  2 
serio_raw              13027  0 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  423529  3 
snd                    62218  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         45466  1 i915
drm                   197641  4 i915,drm_kms_helper
rfcomm                 38139  12 
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
mac_hid                13077  0 
video                  19115  1 i915
bnep                   17830  2 
parport_pc             32114  0 
bluetooth             158479  23 btusb,rfcomm,bnep
ppdev                  12849  0 
binfmt_misc            17292  1 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
sky2                   49545  0 
liz@liz-N220:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.



liz@liz-N220:~$ sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential
[sudo] password for liz: 
Sorry, try again.
[sudo] password for liz: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libunity6
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/985 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 183092 files and directories currently installed.)
Preparing to replace build-essential 11.5ubuntu2.1 (using .../build-essential_11.5ubuntu2.1_i386.deb) ...
Unpacking replacement build-essential ...
Preparing to replace linux-headers-3.2.0-41-generic 3.2.0-41.66 (using .../linux-headers-3.2.0-41-generic_3.2.0-41.66_i386.deb) ...
Unpacking replacement linux-headers-3.2.0-41-generic ...
Setting up build-essential (11.5ubuntu2.1) ...
Setting up linux-headers-3.2.0-41-generic (3.2.0-41.66) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-41-generic /boot/vmlinuz-3.2.0-41-generic
Error! Bad return status for module build on kernel: 3.2.0-41-generic (i686)
Consult /var/lib/dkms/samsung_wireless/0015.1013.2010/build/make.log for more information.
liz@liz-N220:~$
```

---

### Post by praseodym on 2013-05-13
Which driver? Which device? Please show the other outputs.

---

### Post by Podimore on 2013-05-13
have included in post

---

### Post by praseodym on 2013-05-13
Install this driver:

[http://forum.ubuntuusers.de/topic/mein-wlan-stick-150n-von-sitecom-spinnt/#rtl8192de-ce-se-Kombipaket](http://forum.ubuntuusers.de/topic/mein-wlan-stick-150n-von-sitecom-spinnt/#rtl8192de-ce-se-Kombipaket)

"Version 0005.1230.2011 für Ubuntu 12.04"

Driver download is included.

---

### Post by Podimore on 2013-05-13
thank you  i am a complete novice im afraid. could you please give me instructions about how to do it. thanks again

---

### Post by praseodym on 2013-05-13
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential
wget http://media.cdn.ubuntu-de.org/forum/attachments/43/33/2844083-rtl_92ce_92se_92de_0005.1230.2011.tar.gz
tar xvf 2844083-rtl_92ce_92se_92de_0005.1230.2011.tar.gz
cd rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011
make
sudo make install
sudo cp -r firmware/* /lib/firmware 
```
Just copy/paste these lines one by one into the terminal while connected via cable.

---

### Post by Podimore on 2013-05-15
i get error message after the first command line  see edited post

---

### Post by praseodym on 2013-05-15
Is there still the Samsung-wireless PPA active? Check:
```

cat /etc/apt/sources.list
dpkg -l linux-headers-3.2.0-41-generic
dpkg -l build-essential
```

---

### Post by Podimore on 2013-05-15
liz@liz-N220:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
liz@liz-N220:~$ dpkg -l linux-headers-3.2.0-41-generic
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  linux-headers- 3.2.0-41.66    Linux kernel headers for version 3.2.0 on 32
liz@liz-N220:~$ dpkg -l build-essential
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  build-essentia 11.5ubuntu2.1  Informational list of build-essential packag
liz@liz-N220:~$

---

### Post by Podimore on 2013-05-15
see next page

---

### Post by praseodym on 2013-05-15
Is "dkms" installed?
```
sudo apt-get install --reinstall dkms
```

---

### Post by Podimore on 2013-05-15
liz@liz-N220:~$ sudo apt-get install --reinstall dkms
[sudo] password for liz: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libunity6
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/73.2 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 183092 files and directories currently installed.)
Preparing to replace dkms 2.2.0.3-1ubuntu3.1 (using .../dkms_2.2.0.3-1ubuntu3.1_all.deb) ...
Unpacking replacement dkms ...
Processing triggers for man-db ...
Setting up dkms (2.2.0.3-1ubuntu3.1) ...
liz@liz-N220:~$

---

### Post by praseodym on 2013-05-15
Ok, now start the regular installation of the driver.

---

### Post by Podimore on 2013-05-15
i  build-essentia 11.5ubuntu2.1  Informational list of build-essential packag
liz@liz-N220:~$ sudo apt-get install --reinstall dkms
[sudo] password for liz: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libunity6
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/73.2 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 183092 files and directories currently installed.)
Preparing to replace dkms 2.2.0.3-1ubuntu3.1 (using .../dkms_2.2.0.3-1ubuntu3.1_all.deb) ...
Unpacking replacement dkms ...
Processing triggers for man-db ...
Setting up dkms (2.2.0.3-1ubuntu3.1) ...
liz@liz-N220:~$ sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential
[sudo] password for liz: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libunity6
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/985 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 183092 files and directories currently installed.)
Preparing to replace build-essential 11.5ubuntu2.1 (using .../build-essential_11.5ubuntu2.1_i386.deb) ...
Unpacking replacement build-essential ...
Preparing to replace linux-headers-3.2.0-41-generic 3.2.0-41.66 (using .../linux-headers-3.2.0-41-generic_3.2.0-41.66_i386.deb) ...
Unpacking replacement linux-headers-3.2.0-41-generic ...
Setting up build-essential (11.5ubuntu2.1) ...
Setting up linux-headers-3.2.0-41-generic (3.2.0-41.66) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-41-generic /boot/vmlinuz-3.2.0-41-generic
Error! Bad return status for module build on kernel: 3.2.0-41-generic (i686)
Consult /var/lib/dkms/samsung_wireless/0015.1013.2010/build/make.log for more information.

---

### Post by praseodym on 2013-05-15
Continue with the "wget"-command

---

### Post by Podimore on 2013-05-17
have completed all commands and restarted but still no wifi. also now showing an error message that cannot be reported because ubuntu does not supprt samsung. says problems with samsung wireless???

---

### Post by praseodym on 2013-05-17
Did you install "samsung-wireless" in the earlier Ubuntuversion?
```

dpkg -l samsung-wireless
```
```

sudo add-apt-repository ppa:voria/ppa
sudo apt-get update
sudo apt-get install --reinstall samsung-wireless
```

[https://launchpad.net/~voria/%2Barchive/ppa](https://launchpad.net/~voria/%2Barchive/ppa)

---

### Post by Podimore on 2013-05-17
have completed all commands and restarted but still no wifi. also now showing an error message that cannot be reported because ubuntu does not supprt samsung. says problems with samsung wireless???

---

### Post by Podimore on 2013-05-17
liz@liz-N220:~$ dpkg -l samsung-wireless
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  samsung-wirele 0015.1013.2010 Realtek 8192E wireless driver in DKMS format
liz@liz-N220:~$

---

### Post by Podimore on 2013-05-17
should i proceed with your final commands

---

### Post by praseodym on 2013-05-17
This device is known to cause problems.

Check:

```
grep r8 /etc/modprobe.d/*
```

---

### Post by Podimore on 2013-05-17
liz@liz-N220:~$ grep r8 /etc/modprobe.d/*
liz@liz-N220:~$ 


????????

---

### Post by praseodym on 2013-05-17
```
echo "blacklist r8192e_pci" | sudo tee -a /etc/modprobe.d/blacklist.conf && echo "blacklist r8192se_pci" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
and load the "samsung" driver:
```

sudo modprobe -v r8192e_pci_realtek
```

---

### Post by Podimore on 2013-05-17
iz@liz-N220:~$ grep r8 /etc/modprobe.d/*
liz@liz-N220:~$ echo "blacklist r8192e_pci" | sudo tee -a /etc/modprobe.d/blacklist.conf && echo "blacklist r8192se_pci" | sudo tee -a /etc/modprobe.d/blacklist.conf
[sudo] password for liz: 
blacklist r8192e_pci
blacklist r8192se_pci
liz@liz-N220:~$ sudo modprobe -v r8192e_pci_realtek
FATAL: Module r8192e_pci_realtek not found.
liz@liz-N220:~$

---

### Post by praseodym on 2013-05-17
Please show the file /var/lib/dkms/samsung_wireless/0015.1013.2010/build/make.log

Obviously the driver has not been compiled.

---

### Post by Podimore on 2013-05-19
get this

liz@liz-N220:~$  /var/lib/dkms/samsung_wireless/0015.1013.2010/build/make.log
bash: /var/lib/dkms/samsung_wireless/0015.1013.2010/build/make.log: Permission denied
liz@liz-N220:~$

---

### Post by praseodym on 2013-05-19
Just open the file manager and copy the file.

---

### Post by Podimore on 2013-05-19
where is file manager

---

### Post by praseodym on 2013-05-19
Open your /home-folder and change the folder to /var/lib/dkms/samsung_wireless/0015.1013.2010/build/ and show the file make.log

---

### Post by Podimore on 2013-05-19
im really sorry about this. maybe i should drop this until i can find someone to help me???? i have opened my home folder but how do i change to the different folder

---

### Post by praseodym on 2013-05-19
Check:

```
cat /var/lib/dkms/samsung_wireless/0015.1013.2010/build/make.log >> ~/wireless.txt
```
Now there should be a file named wireless.txt in your /home folder.

---

### Post by Podimore on 2013-05-19
home folder file shows this

DKMS make.log for samsung_wireless-0015.1013.2010 for kernel 3.2.0-41-generic (i686)
Wed May 15 21:39:57 BST 2013
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-41-generic'
gcc: error: /lib/modules/3.2.0-41-generic/build/include/linux/autoconf.h: No such file or directory
gcc: fatal error: no input files
compilation terminated.
scripts/Makefile.build:49: *** CFLAGS was changed in "/var/lib/dkms/samsung_wireless/0015.1013.2010/build/HAL/rtl8192/Makefile". Fix it to use ccflags-y. Stop.
make[1]: *** [_module_/var/lib/dkms/samsung_wireless/0015.1013.2010/build/HAL/rtl8192] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-41-generic'
make: *** [all] Error 2

---

### Post by praseodym on 2013-05-19
Please show:

```
cat /var/lib/dkms/samsung_wireless/0015.1013.2010/build/HAL/rtl8192/Makefile >> makefile.txt
```
Maybe this solution works:

[http://lkml.indiana.edu/hypermail/linux/kernel/0709.3/2581.html](http://lkml.indiana.edu/hypermail/linux/kernel/0709.3/2581.html)

to add the following line:
```
 + ccflags-y += -I$(obj)
```

According to this [http://ubuntuforums.org/showthread.php?t=2091449&p=12389249#post12389249](http://ubuntuforums.org/showthread.php?t=2091449&p=12389249#post12389249) the driver version is too old.

Please show:
```

locate dkms.conf | grep var
```
Maybe we can install the new version but we need to remove all old files before. A clean fresh installation with the same problem helped here:

[http://forum.ubuntuusers.de/post/4313892/](http://forum.ubuntuusers.de/post/4313892/)

I will re-open that thread to get new information about kernel upgrades.

---

### Post by wildmanne39 on 2013-05-19
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

