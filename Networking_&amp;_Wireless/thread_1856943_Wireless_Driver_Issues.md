---
title: "Wireless Driver Issues"
date: 2011-10-09
forum: Networking &amp; Wireless
---

### Post by kakashi_12 on 2011-10-09
Just formatted the system and now I can't get the Wireless to work.

It won't see the Wireless driver when I go to System > Administration > Hardware Drivers

I tried rebooting. That didn't work.

Tried switching the device on by using the Fn (function) key + Wireless. But I doubt Ubuntu recognizes Functions.

I also tried some command
sudo lshw -C network
That showed my wireless device and showed it as Enabled.

I also gave my self permissions/rights to connect to wireless.

The last thing that I have done is after doing some research, I have installed NDIS Wrapper. Took me awhile to figure out how to even install it. And then I opened it up and installed my wireless driver (.inf file). But that still did not work.. It still won't see/detect any wireless networks. Is there one more step I have to do after installing the windows driver in NDIS Wrapper?

A little help here please:confused:

---

### Post by kakashi_12 on 2011-10-09
Now went to System > Administration > Hardware Drivers

Now it sees the driver and I have Activated it. But I still can not detect wireless networks.

I took out my external wireless card and re-inserted it and now it detects wireless networks. Problem Solved.

However, I'm still confused as to whether I'm actually using the linux driver or the NDIS. When I activated, it said open source and Broadcom. Did I finish the steps to use NDIS properly, or did my linux drivers finally kick in? Which driver am i using?

---

### Post by praseodym on 2011-10-09
Hi,

please show:

```
lspci -nnk | grep -iA2 net
iwconfig
rfkill list
lsmod
```

---

### Post by kakashi_12 on 2011-10-09
Do I run those all in one command? or each line separately?

---

### Post by kakashi_12 on 2011-10-09
note: this time when booting up, I'm back at square one. The dang wireless card won't detect networks again! Grrrr.

lspci -nnk | grep -iA2 net
01:0c.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Kernel driver in use: 8139too
    Kernel modules: 8139cp, 8139too
02:00.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
    Kernel modules: ssb

 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

rfkill list
bash: rfkill: command not found

 lsmod
Module                  Size  Used by
ndiswrapper           196380  0 
ipv6                  263972  8 
binfmt_misc            16904  1 
i915                   38144  2 
drm                    86056  3 i915
af_packet              25728  2 
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
ppdev                  15620  0 
acpi_cpufreq           15500  0 
cpufreq_powersave       9856  0 
cpufreq_stats          13188  0 
cpufreq_userspace      11396  0 
cpufreq_ondemand       14988  1 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative    14600  0 
pci_slot               12552  0 
container              11520  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
wmi                    14504  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
pcmcia                 43052  0 
snd_intel8x0           37532  3 
snd_ac97_codec        111652  1 snd_intel8x0
evdev                  17696  10 
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10884  0 
psmouse                45200  0 
serio_raw              13444  0 
yenta_socket           31756  2 
rsrc_nonstatic         19072  1 yenta_socket
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcspkr                 10624  0 
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
video                  25104  0 
output                 11008  1 video
battery                18436  0 
ac                     12292  0 
button                 14224  0 
intel_agp              33724  1 
agpgart                42184  3 drm,intel_agp
ext3                  133256  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_piix               24580  2 
ata_generic            12932  0 
8139too                31616  0 
pata_acpi              12160  0 
ohci1394               37936  0 
libata                177312  3 ata_piix,ata_generic,pata_acpi
8139cp                 27520  0 
mii                    13440  2 8139too,8139cp
ieee1394               96324  2 sbp2,ohci1394
scsi_mod              155212  5 sbp2,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
uhci_hcd               30736  0 
ehci_hcd               43276  0 
usbcore               148848  4 ndiswrapper,uhci_hcd,ehci_hcd
thermal                23708  0 
processor              42156  3 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3

---

### Post by praseodym on 2011-10-09
Uninstall ndiswrapper and install the needed firmware:

```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
sudo update-initramfs -u -k all
sudo apt-get install --reinstall b43-fwcutter
```
If you are using 11.04 the last line has to be:
```
sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer
```
Reboot.

---

### Post by kakashi_12 on 2011-10-09
So if I follow these steps, I'll be using the Linux driver and not the Nis Wrapper?
It seems like NIS Wrapper would be more convenient and easier once I get it working. Am I wrong?

---

### Post by praseodym on 2011-10-09
The Linux driver b43 is already part of the kernel, you only need the proprietary firmware being installed.

---

### Post by kakashi_12 on 2011-10-09
doing that now. Just a side note though, I'm having other issues now. When trying to run updates, I get an error and can not receive updates. Yes, I am running an old version of Ubuntu, but would like to on this old pc. Getting the updates would be nice too. Here is the error.

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.171 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz)  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.171 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz)  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz)  404 Not Found [IP: 91.189.92.171 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.92.171 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.171 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz)  404 Not Found [IP: 91.189.92.171 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.171 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.92.171 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz)  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz)  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.92.170 80]
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by praseodym on 2011-10-09
Please show:

```
lsb_release -a
cat /etc/apt/sources.list
```

---

### Post by kakashi_12 on 2011-10-09
Ok. I finished the code above for uninstall Wrapper and re-installing the linux wireless driver. Now what do I do to get it working again?

 lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 8.10
Release:    8.10
Codename:    intrepid



cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

---

### Post by bkratz on 2011-10-09
Intrepid is no longer supported, you will have to change your software sources like in this link

[http://ubuntuforums.org/showpost.php?p=6653548&postcount=4](http://ubuntuforums.org/showpost.php?p=6653548&postcount=4)

Of course changing the name to intrepid from feisty.

---

### Post by kakashi_12 on 2011-10-09
Well, that sorta worked. I was able to get one update. But then I still got the same error.

What about my wireless?

---

### Post by praseodym on 2011-10-09
Firmware archive attached. Save it on your Desktop and install it via:

```
sudo tar xvf ~/Desktop/Broadcom_Firmware.tar.gz -C /lib/firmware/ 
sudo modprobe -v b43
```
Check:
```
dmesg | grep b43
iwconfig
lsmod
```
I recommend a clean new installtion of at least 10.04 because 8.10 is way too old. An Upgrade via 9.04->9.10->10.04 will cause trouble and too much time.

---

### Post by kakashi_12 on 2011-10-09
That seemed to work at first, but as before when I rebooted I lost it again. I can't see any wireless networks now again.

---

### Post by praseodym on 2011-10-09
Force the driver to load at boot-up:

```
sudo modprobe -v b43
sudo depmod -a
sudo update-initramfs -u
echo b43 | sudo tee -a /etc/modules
```

---

### Post by kakashi_12 on 2011-10-09
awesome. thanks.

---

