---
title: "No Internet Connection on MacBook Pro 2009"
date: 2013-03-19
forum: Networking &amp; Wireless
---

### Post by Braundmeier on 2013-03-19
[INDENT]I recently installed Ubuntu 12.10 on my 2009 Macbook Pro and everything is working properly except Wi-Fi. The wireless settings show that I am using a wired connection, and when I try to manually add a network (SSID, BSID, etc.) nothing happens after I save it. When I boot up into OS X, Wi-Fi is working just fine. Can anyone provide some feedback on what I can do to get the wireless working? Thanks :smile: [/INDENT]

---

### Post by Hadaka on 2013-03-19
Hi please post the output of..
```
lspci -n | egrep '0200|0280'
```
thanks.

---

### Post by Braundmeier on 2013-03-19
00:0a.0 0200: 10de:0ab0 (rev b1)
03:00.0 0280: 14e4:432b (rev 01)

---

### Post by Hadaka on 2013-03-20
Hi please do..

```
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```
thanks.

---

### Post by Braundmeier on 2013-03-20
```
aaron@aaron-MacBookPro:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package bcmwl-kernel-source
aaron@aaron-MacBookPro:~$ sudo modprobe wl
FATAL: Module wl not found
```

:(

---

### Post by Hadaka on 2013-03-20
Hi,were you connected to the internet when you
ran that command? also please do..
```
lsmod
```
post the results
thanks.

---

### Post by Braundmeier on 2013-03-20
I was not connected to the internet when I ran that command - do I need to be? I can probably find an Ethernet cord around here somewhere...I'll be able to get back to my laptop here in awhile, I'll post the results.

---

### Post by Braundmeier on 2013-03-20
```
aaron@aaron-MacBookPro:~$ lsmod
Module                  Size  Used by
cdc_acm                26935  0 
snd_hda_codec_cirrus    23806  1 
coretemp               13400  0 
kvm_intel             132759  0 
kvm                   414070  1 kvm_intel
joydev                 17457  0 
parport_pc             32688  0 
ppdev                  17073  0 
rfcomm                 46619  12 
bnep                   18140  2 
applesmc               19314  0 
input_polldev          13896  1 applesmc
snd_hda_intel          33491  3 
snd_hda_codec         134212  2 snd_hda_codec_cirrus,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
microcode              22803  0 
snd_pcm                96580  2 snd_hda_intel,snd_hda_codec
b43                   369753  0 
mac80211              539908  1 b43
nouveau               895609  3 
ttm                    83595  1 nouveau
drm_kms_helper         46784  1 nouveau
drm                   275528  5 nouveau,ttm,drm_kms_helper
uvcvideo               76749  0 
videobuf2_core         32851  1 uvcvideo
videodev              120309  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12860  1 uvcvideo
videobuf2_memops       13368  1 videobuf2_vmalloc
btusb                  18334  0 
i2c_algo_bit           13413  1 nouveau
mxm_wmi                12979  1 nouveau
video                  19335  1 nouveau
wmi                    19070  2 nouveau,mxm_wmi
snd_seq_midi           13324  0 
bcm5974                17315  0 
bluetooth             209199  22 rfcomm,bnep,btusb
snd_rawmidi            30512  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
cfg80211              206566  2 b43,mac80211
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
bcma                   35656  1 b43
shpchp                 37108  0 
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78734  15 snd_hda_codec_cirrus,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15047  1 snd
i2c_nforce2            13013  0 
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
apple_bl               13673  0 
mac_hid                13205  0 
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
hid_generic            12493  0 
hid_apple              13237  0 
usbhid                 46947  0 
hid                   100366  3 hid_generic,hid_apple,usbhid
usb_storage            48838  0 
uas                    17844  0 
firewire_ohci          40401  0 
firewire_core          64368  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
ssb                    52036  1 b43
forcedeth              67156  0 
aaron@aaron-MacBookPro:~$ 

```

---

### Post by Hadaka on 2013-03-20
Hi,yes please run that command from a 
wired connection . The wired side of your
ubuntu works?..correct, but not the wireless.
thats what i get from your first post. so please do,,
```
 sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```
thanks.

---

### Post by Braundmeier on 2013-03-20
```
aaron@aaron-MacBookPro:~$ sudo apt-get install --reinstall bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package bcmwl-kernel-source
aaron@aaron-MacBookPro:~$ sudo modprobe wl
FATAL: Module wl not found.
aaron@aaron-MacBookPro:~$ 

```

Correct, the wired works when I'm connected to my router with an Ethernet cable, but when I'm unplugged the only connection option I get says "Wired Network" and a message saying I'm disconnected. The code above is the output of those commands while connected to my router.

---

### Post by Hadaka on 2013-03-20
ok, please do..
from a wired connection..
```
sudo apt-get upgrade
sudo apt-get update
```
and then do..
```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl

```
thanks.

---

### Post by Braundmeier on 2013-03-20
Everything went smoothly until the last two commands where I got errors. Here is the output from the last two:

```
aaron@aaron-MacBookPro:~$ sudo apt-get install --reinstall bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dkms fakeroot
Suggested packages:
  dpkg-dev debhelper
The following NEW packages will be installed:
  bcmwl-kernel-source dkms fakeroot
0 upgraded, 3 newly installed, 0 to remove and 1 not upgraded.
Need to get 1,341 kB of archives.
After this operation, 4,277 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ quantal-updates/main dkms all 2.2.0.3-1.1ubuntu1.1 [71.4 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ quantal/restricted bcmwl-kernel-source amd64 5.100.82.112+bdcom-0ubuntu3 [1,181 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ quantal/main fakeroot amd64 1.18.4-2 [88.2 kB]
Fetched 1,341 kB in 1s (749 kB/s)
Selecting previously unselected package dkms.
(Reading database ... 164472 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.2.0.3-1.1ubuntu1.1_all.deb) ...
Selecting previously unselected package bcmwl-kernel-source.
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_amd64.deb) ...
Selecting previously unselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.18.4-2_amd64.deb) ...
Processing triggers for man-db ...
Setting up dkms (2.2.0.3-1.1ubuntu1.1) ...
Setting up bcmwl-kernel-source (5.100.82.112+bdcom-0ubuntu3) ...
Loading new bcmwl-5.100.82.112+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.5.0-17-generic
Building for architecture x86_64
[B][COLOR=#ff0000]Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
ERROR: Module b43legacy does not exist in /proc/modules
ERROR: Module bcm43xx does not exist in /proc/modules
ERROR: Module brcm80211 does not exist in /proc/modules
ERROR: Module brcmfmac does not exist in /proc/modules
ERROR: Module brcmsmac does not exist in /proc/modules[/COLOR]
[COLOR=#ff0000]FATAL: Module wl not found.[/COLOR][/B]
update-initramfs: deferring update (trigger activated)
Setting up fakeroot (1.18.4-2) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-17-generic
aaron@aaron-MacBookPro:~$ sudo modprobe wl
[COLOR=#ff0000]**FATAL: Module wl not found.**[/COLOR]
aaron@aaron-MacBookPro:~$ 

```

---

### Post by Hadaka on 2013-03-20
hi, try this..
```
sudo apt-get install linux-sources linux-headers-3.5.0-17-generic
```
then repeat the last 2 commands
thanks

---

### Post by Braundmeier on 2013-03-20
```
aaron@aaron-MacBookPro:~$ sudo apt-get install linux-sources linux-headers-3.5.0-17-generic
[sudo] password for aaron: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-sources
aaron@aaron-MacBookPro:~$ 

```

:(

---

### Post by Hadaka on 2013-03-20
Hi try this once more please..
```

sudo apt-get install linux-headers-generic 
```
then do..
```

sudo apt-get install --reinstall bcmwl-kernel-source
 sudo modprobe wl 
iwconfig 
```
thanks.

---

### Post by Braundmeier on 2013-03-20
I received the same errors as before, here is the output of all three commands:

```
aaron@aaron-MacBookPro:~$ sudo apt-get install linux-headers-generic
[sudo] password for aaron: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
aaron@aaron-MacBookPro:~$ sudo apt-get install --reinstall bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 1 not upgraded.
Need to get 0 B/1,181 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 164611 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.100.82.112+bdcom-0ubuntu3 (using .../bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Setting up bcmwl-kernel-source (5.100.82.112+bdcom-0ubuntu3) ...
Loading new bcmwl-5.100.82.112+bdcom DKMS files...
Building only for 3.5.0-17-generic
Building for architecture x86_64
[COLOR=#ff0000][B]Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b43legacy does not exist in /proc/modules
ERROR: Module ssb does not exist in /proc/modules
ERROR: Module bcm43xx does not exist in /proc/modules
ERROR: Module brcm80211 does not exist in /proc/modules
ERROR: Module brcmfmac does not exist in /proc/modules
ERROR: Module brcmsmac does not exist in /proc/modules
ERROR: Module bcma does not exist in /proc/modules
FATAL: Module wl not found.[/B][/COLOR]
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-17-generic
aaron@aaron-MacBookPro:~$ sudo modprobe wl
[COLOR=#ff0000]**FATAL: Module wl not found.**[/COLOR]
aaron@aaron-MacBookPro:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

aaron@aaron-MacBookPro:~$ 


```

---

### Post by Hadaka on 2013-03-20
Hi, fun stuff huh? please do..

```
uname -a
```
thanks.

---

### Post by Braundmeier on 2013-03-20
Very fun, lol. I just want some Wi-Fi!   ```
aaron@aaron-MacBookPro:~$ uname -a Linux aaron-MacBookPro 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux 
```

---

### Post by Hadaka on 2013-03-20
Hi, indeed something odd going on here...
lets take a look at a couple more things.
First..boot, in fact do a power cycle on the
computer  and the router, then..
please do..
```
arch
sudo dpkg -s bcmwl-kernel-source
```
thanks.

and thanks to chili555 for looking over my shoulder.

---

### Post by Braundmeier on 2013-03-20
```
 aaron@aaron-MacBookPro:~$ arch x86_64 aaron@aaron-MacBookPro:~$ sudo dpkg -s bcmwl-kernel-source [sudo] password for aaron:  Package: bcmwl-kernel-source Status: install ok installed Priority: optional Section: admin Installed-Size: 3524 Maintainer: Ubuntu Developers  Architecture: amd64 Source: bcmwl Version: 5.100.82.112+bdcom-0ubuntu3 Replaces: bcmwl-modaliases Depends: dkms, linux-libc-dev, libc6-dev, linux-headers-generic | linux-headers Conflicts: bcmwl-modaliases Description: Broadcom 802.11 Linux STA wireless driver source  This package contains Broadcom 802.11 Linux STA wireless driver  for use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,  BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-based  hardware. Modaliases: wl(pci:v000014E4d00000576sv*sd*bc*sc*i*, pci:v000014E4d00004311sv*sd*bc*sc*i*, pci:v000014E4d00004312sv*sd*bc*sc*i*, pci:v000014E4d00004313sv*sd*bc*sc*i*, pci:v000014E4d00004315sv*sd*bc*sc*i*, pci:v000014E4d00004328sv*sd*bc*sc*i*, pci:v000014E4d00004329sv*sd*bc*sc*i*, pci:v000014E4d0000432Asv*sd*bc*sc*i*, pci:v000014E4d0000432Bsv*sd*bc*sc*i*, pci:v000014E4d0000432Csv*sd*bc*sc*i*, pci:v000014E4d0000432Dsv*sd*bc*sc*i*, pci:v000014E4d00004353sv*sd*bc*sc*i*, pci:v000014E4d00004357sv*sd*bc*sc*i*, pci:v000014E4d00004358sv*sd*bc*sc*i*, pci:v000014E4d00004359sv*sd*bc*sc*i*, pci:v000014E4d0000435Asv*sd*bc*sc*i*, pci:v000014E4d00004727sv*sd*bc*sc*i*, pci:v000014E4d0000A99Dsv*sd*bc*sc*i*) Original-Maintainer: Alberto Milone  aaron@aaron-MacBookPro:~$ 
```

---

### Post by Hadaka on 2013-03-20
ok,lets see what happens with the b43 module
since that is what is loaded..
```
sudo modprobe b43
dmesg | grep b43
```
and just out of curiosity..
```
cat /etc/network/interfaces 
```
thanks.

---

### Post by Braundmeier on 2013-03-21
Haven't had a chance to sit down and try those commands yet. I'll be able to tomorrow and I'll post the output. Thanks for all your help by the way!

---

### Post by Hadaka on 2013-03-21
Hi, no problem,I am just now getting
my own machine squared away, I was
messing about with the dd command and
wiped out my entire hard drive. All is well
now.:D

---

### Post by Braundmeier on 2013-03-22
```
 aaron@aaron-MacBookPro:~$ sudo modprobe b43 [sudo] password for aaron:  aaron@aaron-MacBookPro:~$ dmesg | grep b43 [  169.501272] b43-pci-bridge 0000:03:00.0: >power state changed by ACPI to D0 [  169.501280] b43-pci-bridge 0000:03:00.0: >power state changed by ACPI to D0 [  169.797138] b43-phy0: Broadcom 4322 WLAN found (core revision 16) [  169.885148] b43-phy0 ERROR: Firmware file "b43/ucode16_mimo.fw" not found [  169.885153] b43-phy0 ERROR: Firmware file "b43-open/ucode16_mimo.fw" not found [  169.885155] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website. aaron@aaron-MacBookPro:~$ cat /etc/network/interfaces # interfaces(5) file used by ifup(8) and ifdown(8) auto lo iface lo inet loopback aaron@aaron-MacBookPro:~$  
```  Also, I don't know why my code segments aren't formatting correctly when I post them here...

---

### Post by Braundmeier on 2013-03-22
Also, under Additional Drivers it shows that I am using Broadcom Corporation: BCM4332 802.11a/b/g/n Wireless LAN Controller and it's showing it as active...but I still can't get my wireless to scan for networks. I tried rebooting and still nothing.

---

### Post by Hadaka on 2013-03-22
ok, lets unload the b43 and then try
a massaged b43
please do..
```
*sudo apt*-*get* purge *b43*-*fwcutter firmware*-*b43*-[I]installer
sudo modprobe -r b43[/I]
```
then do..
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
dmesg | grep b43
```
thanks.

---

### Post by Braundmeier on 2013-03-22
Aha! I have wireless after those! You are the best!

---

### Post by Hadaka on 2013-03-22
Great,sorry it took so long to get there.
when you loaded 12.10..did you do all the updates?, and have you been
doing the updates from the update manager? Reason i ask is, despite
the fact you now have wireless, it should have loaded the sta driver even
if it was wrong...and didnt...so still a mystery.
anyway...gald its working...do your updates...upgrades
and mark this SOLVED
thanks for the fun !

---

