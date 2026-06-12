---
title: "Atheros AR5006eg"
date: 2006-07-10
forum: Networking &amp; Wireless
---

### Post by johnybot on 2006-07-10
Can someone tell me how to get this card to work on my new laptop, i have found little success going solo

---

### Post by tturrisi on 2006-07-10
For atheros chipset cards:
1. run synaptec
2. enable universe & multiuniverse repositories
3. install restricted modules for kernel used.

---

### Post by johnybot on 2006-07-10
this does nothing?

---

### Post by tturrisi on 2006-07-11
what card?

---

### Post by stupidkid on 2006-07-11
> **tturrisi said:**
> what card?
It's in the title.

You need madwifi drivers. Atheros cards are very easy to install.

In fact, Dapper should support this card natively. Can you post your lsmod and iwconfig?

---

### Post by clyde9999 on 2006-07-11
**[COLOR="DarkGreen"]You and I are having similar problems. If I come up with a fix, you will be the first to know. I will send you links so that you can monitor my progress, which is not good so far. [/COLOR]**

[http://kubuntuforums.net/forums/index.php?topic=6745.0](http://kubuntuforums.net/forums/index.php?topic=6745.0)
[http://www.ubuntuforums.org/showthread.php?p=1241450#post1241450](http://www.ubuntuforums.org/showthread.php?p=1241450#post1241450)

One link is for the same problem in Kubuntu, and the wireless used to work in Kubuntu, now it does not. It all started after my last update. The other link is to the problem I am having with Ubuntu.

---

### Post by clyde9999 on 2006-07-11
Check this out. My problem is solved in Ubunut. Maybe it can help. I do not know for sure.
[http://www.ubuntuforums.org/showthread.php?t=213536](http://www.ubuntuforums.org/showthread.php?t=213536)

---

### Post by johnybot on 2006-07-14
yah tried installing mad wifi drivers iwconfig shows no wireless device

when doing 'make' it says nothing to configure

---

### Post by johnybot on 2006-07-27
my problem still exists and is prevents me from using linux

---

### Post by tturrisi on 2006-07-27
You should not need to use "make" for anything, the drivers are in the restricted-modules package.
Follow stupidkid's instructions and open a terminal & type:
sudo lsmod & post the results here.
Do same w/ command iwconfig.

---

### Post by johnybot on 2006-07-28
output from lsmod 
```
Module                  Size  Used by
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
radeon                116000  0
drm                    73236  1 radeon
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               21904  1 i2c_acpi_ec
ac                      5252  1 acpi_sbs
nls_utf8                2176  1
ntfs                  103536  1
ipv6                  265600  6
dm_mod                 58936  1
md_mod                 72532  0
af_packet              22920  2
sr_mod                 16932  0
sbp2                   24196  0
parport_pc             35780  0
lp                     11844  0
parport                36296  3 ppdev,parport_pc,lp
joydev                 10048  0
pcmcia                 40508  0
serio_raw               7300  0
snd_hda_intel          18964  1
snd_hda_codec         142640  1 snd_hda_intel
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
yenta_socket           28428  1
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
8139cp                 22528  0
8139too                26880  0
mii                     5888  2 8139cp,8139too
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_hda_intel,snd_pcm
new_ath_pci            98340  0
new_ath_rate_sample    14080  1 new_ath_pci
new_wlan              204892  2 new_ath_pci,new_ath_rate_sample
wlan                  144924  0
new_ath_hal           191312  2 new_ath_pci,new_ath_rate_sample
pcspkr                  2180  0
psmouse                36228  0
rtc                    13492  0
ati_agp                 9100  0
agpgart                34888  2 drm,ati_agp
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
tsdev                   8000  0
evdev                   9856  2
sg                     37920  0
ext3                  135688  1
jbd                    58772  1 ext3
usbhid                 38368  0
ide_generic             1536  0
ehci_hcd               32008  0
ohci_hcd               21892  0
usbcore               129668  4 usbhid,ehci_hcd,ohci_hcd
ohci1394               35124  0
ieee1394              299832  2 sbp2,ohci1394
ide_cd                 33028  0
cdrom                  38560  2 sr_mod,ide_cd
atiixp                  6800  1
sd_mod                 19984  4
generic                 5124  0
sata_sil                9348  6
libata                 78992  1 sata_sil
scsi_mod              139496  5 sr_mod,sbp2,sg,sd_mod,libata
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

```

output form iwconfig 
```
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

```

thanks for any help

---

### Post by tturrisi on 2006-07-28
new_ath_pci            98340  0
new_ath_rate_sample    14080  1 new_ath_pci
new_wlan              204892  2 new_ath_pci,new_ath_rate_sample
wlan                  144924  0
new_ath_hal           191312  2 new_ath_pci,new_ath_rate_sample

These are the mad-wifi drivers but they must be the "new" drivers, not the ones that are part of restricted-modules.  I suspect that they could be corrupted incorrectly built.

The lsmod should look like this:

ath_pci                81852  0
ath_rate_sample        17224  1 ath_pci
wlan                  146684  4 wlan_wep,ath_pci,ath_rate_sample
ath_hal               148848  3 ath_pci,ath_rate_sample


run these commands & post results:

sudo lshw -C network

lspci -v | grep Ethernet

---

### Post by johnybot on 2006-07-28
```
  *-network UNCLAIMED
       description: Ethernet controller
       product: Atheros Communications, Inc.
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       resources: iomemory:d0100000-d010ffff irq:233
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@09:06.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:21:76:7a
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=half ip=192.168.0.15 link=yes multicast=yes port=MII speed=10MB/s
       resources: ioport:a000-a0ff iomemory:d0200800-d02008ff irq:209

```

```
0000:02:00.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001c (rev 01)
0000:09:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

---

### Post by urthshu on 2006-12-29
This is my same issue, with a Toshiba Sat m115-s1061. Nearest I can sort out thus far is that I'll have to go with ndiswrapper using the ar5211.sys file from my windows partition. It seems that these cards aren't Linux-friendly somehow. 

I'll be trying it out shortly, let you know how it goes.

---

### Post by abliss26 on 2007-02-04
I had the exact same problem with a new toshiba satellite with ar5006eg wifi card; the solution for me was to download the latest build from madwifi (release this month) compile and install ; before compiling and installing, remove any loaded ath* modules (ath_hal and ath_pci) with modprobe; then run make and then make install ; you'll need linux-headers packages installed ; also the installer will detect that an older version of madwifi drivers are installed, chose option to remove ; hope this helps

---

### Post by Lonthong on 2007-02-05
I just successfully installed madwifi onto fresh installed Edgy 64bit.
My laptop: BenQ P41, Turion X2, Ati X1100, Atheros Ar5006eg.

The driver that works with this card can be found here:
[http://snapshots.madwifi.org/madwifi-ng/](http://snapshots.madwifi.org/madwifi-ng/)
The version that works is r1711 or later (in fact I installed the latest).

On fresh Edgy, restricted-modules is not installed so I just went head & installed  that driver directly.
go to your madwifi folder 
$ cd scripts
$ ./madwifi-unload.bash
$ ./find-madwifi-modules.sh /lib/modules/
$ cd .. 
$ sudo make
$ sudo make install
$ sudo modprobe ath_pci
$sudo modprobe wlan_scan_sta
$ sudo ifconfig ath0 up
System - administration - networking: My wireless device is now listed in here

If you have restricted-modules already installed, you must disable & uninstall it first
$ sudo ifconfig ath0 down 
after $ sudo make above:
$ sudo make uninstall

---

### Post by silentsoul on 2007-02-05
I tried your idea and this is the errors I am getting

computer@Xerses:~/Desktop$ cd madwifi-ng-r1718-20060920/
computer@Xerses:~/Desktop/madwifi-ng-r1718-20060920$ cd scripts computer@Xerses:~/Desktop/madwifi-ng-r1718-20060920/scripts$ ./madwifi-unload.bash
computer@Xerses:~/Desktop/madwifi-ng-r1718-20060920/scripts$ ./find-madwifi-modules.sh /lib/modules
computer@Xerses:~/Desktop/madwifi-ng-r1718-20060920/scripts$ cd .. computer@Xerses:~/Desktop/madwifi-ng-r1718-20060920$ sudo make Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.15-27-386/build SUBDIRS=/home/computer/Desktop/madwifi-ng-r1718-20060920 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-27-386'
  CC [M]  /home/computer/Desktop/madwifi-ng-r1718-20060920/ath/ah_osdep.o
  HOSTCC  /home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:27:19: error: errno.h: No such file or directory
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:29:20: error: string.h: No such file or directory
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c: In function 'uudecode_usage':
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c: At top level:
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:40: error: syntax error before '*' token
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:41: warning: function declaration isn't a prototype
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c: In function 'get_line_from_file':
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:46: warning: implicit declaration of function 'getc'
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:46: error: 'file' undeclared (first use in this function)
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:46: error: (Each undeclared identifier is reported only once
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:46: error: for each function it appears in.)
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:46: error: 'EOF' undeclared (first use in this function)
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:58: warning: implicit declaration of function 'ferror'
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:59: error: 'NULL' undeclared (first use in this function)
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c: At top level:
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:70: error: syntax error before '*' token
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:71: warning: function declaration isn't a prototype
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c: In function 'read_stduu':
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:74: error: 'src_stream' undeclared (first use in this function)
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:74: error: 'NULL' undeclared (first use in this function)
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:78: warning: implicit declaration of function 'strcmp'
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:87: warning: implicit declaration of function 'fprintf'
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:87: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:87: error: 'stderr' undeclared (first use in this function)
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:88: warning: implicit declaration of function 'exit'
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:88: warning: incompatible implicit declaration of built-in function 'exit'
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:93: warning: implicit declaration of function 'strlen'
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:93: warning: incompatible implicit declaration of built-in function 'strlen'
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:94: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:95: warning: incompatible implicit declaration of built-in function 'exit'
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:100: warning: implicit declaration of function 'fputc'
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:100: error: 'dst_stream' undeclared (first use in this function)
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:115: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:116: warning: incompatible implicit declaration of built-in function 'exit'
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c: In function 'main':
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:188: warning: implicit declaration of function 'open'
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/computer/Desktop/madwifi-ng-r1718-20060920/ath/uudecode] Error 1
make[2]: *** [/home/computer/Desktop/madwifi-ng-r1718-20060920/ath] Error 2
make[1]: *** [_module_/home/computer/Desktop/madwifi-ng-r1718-20060920] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-27-386'
make: *** [modules] Error 2
computer@Xerses:~/Desktop/madwifi-ng-r1718-20060920$ sudo make install sh scripts/find-madwifi-modules.sh 2.6.15-27-386
for i in ./ath ath_rate/sample ./net80211; do \
                make -C $i install || exit 1; \
        done
make[1]: Entering directory `/home/computer/Desktop/madwifi-ng-r1718-20060920/ath'
test -d //lib/modules/2.6.15-27-386/net || mkdir -p //lib/modules/2.6.15-27-386/net
cp ath_pci.ko //lib/modules/2.6.15-27-386/net
cp: cannot stat `ath_pci.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/computer/Desktop/madwifi-ng-r1718-20060920/ath'
make: *** [install-modules] Error 1
computer@Xerses:~/Desktop/madwifi-ng-r1718-20060920$ sudo modprobe ath_pci
FATAL: Module ath_pci not found.
computer@Xerses:~/Desktop/madwifi-ng-r1718-20060920$ sudo modprobe wlan_scan_staFATAL: Module wlan_scan_sta not found.
computer@Xerses:~/Desktop/madwifi-ng-r1718-20060920$ sudo ifconfig ath0 up
ath0: ERROR while getting interface flags: No such device
computer@Xerses:~/Desktop/madwifi-ng-r1718-20060920$

---

### Post by barefoot on 2007-02-05
A fresh install of ubuntu doesnt have build-essentials install (afaik kubuntu does though)

```
sudo apt-get install build-essential
```

---

### Post by abliss26 on 2007-02-05
it seems that kernel updates are breaking something with the compiled atheros module; had to re-install after updating the machine (updates included a kernel update); any idea how to prevent future kernle patches from wreaking havok?

---

### Post by tturrisi on 2007-02-05
> **abliss26 said:**
> it seems that kernel updates are breaking something with the compiled atheros module; had to re-install after updating the machine (updates included a kernel update); any idea how to prevent future kernle patches from wreaking havok?
If you build any module you will have to rebuild it when change kernels, always been like that and likely always will be like that.

---

### Post by manfo on 2007-02-26
> **Lonthong said:**
> I just successfully installed madwifi onto fresh installed Edgy 64bit.
My laptop: BenQ P41, Turion X2, Ati X1100, Atheros Ar5006eg.

The driver that works with this card can be found here:
[http://snapshots.madwifi.org/madwifi-ng/](http://snapshots.madwifi.org/madwifi-ng/)
The version that works is r1711 or later (in fact I installed the latest).

On fresh Edgy, restricted-modules is not installed so I just went head & installed  that driver directly.
go to your madwifi folder 
$ cd scripts
$ ./madwifi-unload.bash
$ ./find-madwifi-modules.sh /lib/modules/
$ cd .. 
$ sudo make
$ sudo make install
$ sudo modprobe ath_pci
$sudo modprobe wlan_scan_sta
$ sudo ifconfig ath0 up
System - administration - networking: My wireless device is now listed in here

If you have restricted-modules already installed, you must disable & uninstall it first
$ sudo ifconfig ath0 down 
after $ sudo make above:
$ sudo make uninstall

..thank you, that worked for me too! I'm on a Toshiba A100-063 laptop with an Atheros AR5006EG wireless card...

---

### Post by senab on 2007-03-17
Thanks, that method worked great. Unfortunately I still can't get network-manager-gnome to recognize the card. Not sure why to be honest, it's been setup in 'System' --> 'Administration' --> 'Networking' therefore I was under the impression it should recognize the card. Any ideas?

---

### Post by Watergeus on 2007-03-17
Works here, at least I have a wireless connection in the Network Settings.
Now I still have to configure that.
Will do and if I run in problems I will come back.

For the good order the configuration of this laptop:

Laptop: Toshiba Satellite A135-S2276
Vista preinstalled, dual booting with Edgy, Kubuntu

To see the network settings (and to config them) I go:
System -> Networking (in Kubuntu)

I had installed already some other 'madwifi's' and the:
```

sudo make uninstall

```
worked. I think you have to type 'r' to get rid of the old stuff.


Thanks for the tip! (took me 24 hours to find this right solution)

---

### Post by yammosk on 2007-09-29
I have an Amilo Li 1720 with a built-in AR5006EG chipset and I cannot get it to work under Feisty. I do not know whether this is significant, but the WLAN LED does not lid up after Ubuntu has booted although I did use the BIOS setting "Enable WLAN at boot". I'd be happy to post anything in order to get closer to a solution. Right now, I'm a little bit at a loss. 
I can see different wlan-networks, but I cannot connect. :confused:

EDIT: The following two simple commands solved my problems: 

$ sudo modprobe acerhk autowlan=1
$ echo 1 | sudo tee > /proc/driver/acerhk/wirelessled


Works like a charm now. :)

---

### Post by johnnycordeiro on 2007-09-30
I'am new at this too. I got mine to turn on by:  sudo echo "enabled: 1" > /proc/acpi/acer/wireless 
If that does not work:  sudo echo "1" > /proc/acpi/acer/wireless  if your acpi is different directories may be different. Then: sudo modprobe ath_pci 

Hope this helps

---

### Post by mrmoney on 2007-10-10
Hi guys.

I too have the Atheros AR5006eg card, on an Acer Asipre 3050-1270 laptop.
I am running Ubuntu Gusty, and no wireless card is being recognized in the Network admin.

Eg if I do iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

```

I tried install madwifi-ng-r2732 using:
sudo make install KERNELPATH=/usrc/src/linux-headers-2.6.22-13-generic

and then doing 
sudo modprobe ath_pci

but it says that module does not exist
here is the output of lsmod:

```

Module                  Size  Used by
ipv6                  278916  15 
binfmt_misc            12936  1 
af_packet              24840  2 
rfcomm                 42136  2 
l2cap                  26112  11 rfcomm
bluetooth              56804  4 rfcomm,l2cap
ppdev                  10244  0 
powernow_k8            16832  0 
cpufreq_ondemand        9612  1 
cpufreq_powersave       2688  0 
cpufreq_conservative     8072  0 
cpufreq_stats           7232  0 
cpufreq_userspace       5280  0 
freq_table              5792  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
button                  8976  0 
dock                   10656  0 
container               5504  0 
video                  17932  0 
ac                      6148  0 
sbs                    19592  0 
battery                11012  0 
parport_pc             37668  0 
lp                     12452  0 
parport                37448  3 ppdev,parport_pc,lp
joydev                 11328  0 
snd_hda_intel         263712  1 
snd_pcm_oss            44544  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53104  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcspkr                  4224  0 
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 41260  0 
i2c_piix4               9868  0 
serio_raw               8068  0 
sdhci                  19084  0 
mmc_core               28420  1 sdhci
psmouse                39952  0 
k8temp                  6656  0 
snd                    54532  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
yenta_socket           27532  1 
rsrc_nonstatic         14592  1 yenta_socket
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
i2c_core               26112  1 i2c_piix4
snd_page_alloc         11528  2 snd_hda_intel,snd_pcm
shpchp                 34580  0 
pci_hotplug            32576  1 shpchp
ati_agp                10252  0 
agpgart                35144  1 ati_agp
evdev                  11136  6 
ext3                  133640  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36380  0 
ide_cd                 32416  0 
cdrom                  37408  1 ide_cd
sd_mod                 30336  3 
8139too                27776  0 
usbhid                 29664  0 
hid                    28928  1 usbhid
ata_generic             8580  0 
8139cp                 25344  0 
mii                     6656  2 8139too,8139cp
atiixp                  7056  0 [permanent]
ide_core              116932  2 ide_cd,atiixp
ehci_hcd               36492  0 
ohci_hcd               23556  0 
sata_sil               12296  2 
usbcore               138248  4 usbhid,ehci_hcd,ohci_hcd
libata                125168  2 ata_generic,sata_sil
scsi_mod              146828  3 sg,sd_mod,libata
thermal                14344  0 
processor              32072  2 powernow_k8,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40600  0 
commoncap               8320  1 apparmor


```


I don't really know what I am doing, so any help is GREATLY appreciated.

Thanks

---

### Post by dr_cerebro on 2007-10-22
You have to install acer_acpi first, just read this thread, page 2 and 3:

[http://ubuntuforums.org/showthread.php?t=580672](http://ubuntuforums.org/showthread.php?t=580672)

---

### Post by TuxSinx on 2007-10-24
I have this problem and can't i resolved here post lspci lsmod and iwconfig, excuseme my english but i from venezuela and dont speack english

LSPCI 

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
14:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
1a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
1a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
1a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
1a:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

LSMOD

Module                  Size  Used by
nls_iso8859_1           5120  1 
nls_cp437               6784  2 
isofs                  36412  1 
vfat                   14080  1 
udf                    87204  0 
fat                    54300  1 vfat
ipv6                  273892  17 
af_packet              24840  2 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
powernow_k8            16960  1 
cpufreq_ondemand        9612  1 
cpufreq_conservative     8072  0 
cpufreq_stats           7232  0 
cpufreq_powersave       2688  0 
freq_table              5792  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       5280  0 
button                  8976  0 
video                  18060  0 
sbs                    19592  0 
ac                      6148  0 
dock                   10656  0 
battery                11012  0 
container               5504  0 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
joydev                 11328  0 
pcmcia                 41388  0 
snd_hda_intel         263712  1 
ide_cd                 32672  1 
cdrom                  37536  1 ide_cd
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
tifm_7xx1               8832  0 
tifm_core              11652  1 tifm_7xx1
snd_rawmidi            25728  1 snd_seq_midi
fglrx                 735392  57 
pcspkr                  4224  0 
sdhci                  18828  0 
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                39952  0 
ath_pci                98080  0 
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
k8temp                  6656  0 
serio_raw               8068  0 
i2c_piix4               9740  0 
i2c_core               26112  1 i2c_piix4
mmc_core               28420  1 sdhci
wlan                  206020  1 ath_pci
ath_hal               192720  1 ath_pci
atiixp                  7056  0 [permanent]
ati_agp                10124  0 
agpgart                35016  2 fglrx,ati_agp
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  5 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
usb_storage            73024  1 
ide_core              116804  3 ide_cd,atiixp,usb_storage
libusual               18448  1 usb_storage
sg                     36764  0 
sd_mod                 30336  6 
ata_generic             8452  0 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
r8169                  32260  0 
ehci_hcd               36492  0 
ohci_hcd               22916  0 
usbcore               138632  5 usb_storage,libusual,ehci_hcd,ohci_hcd
ahci                   23300  3 
libata                125168  2 ata_generic,ahci
scsi_mod              147084  5 sbp2,usb_storage,sg,sd_mod,libata
thermal                14344  0 
processor              32072  2 powernow_k8,thermal
fan                     5764  0 
fuse                   47124  3 
apparmor               40728  0 
commoncap               8320  1 apparmor

IWCONFIG

lo        no wireless extensions.

eth0      no wireless extensions.

i have a laptop Toshiba Satellite A215-s4697 please i have 1 month testing and find solution for this problem

---

### Post by Thragon on 2007-10-29
I'm in the same situation. I have a Toshiba Satellite A210 11P machine dual booting into Gutsy but I can't seem to get the wireless card working. It is an Atheros AR5006EG. I've been around the forums, and attempted a few of the solutions, with no success and but as I'm a *complete* 2 day old newbie on Linux, I'm hitting some knowledge walls. I'd be grateful if someone could post a step-by-step solution that takes into account my lack of knowledge. Thanks in advance.

Thragon.

---

### Post by BoardStupid on 2008-02-26
I managed to get wireless working just fine on my Acer Aspire 5051AWXMi, with Atheros AR5006EG integrated wireless. I used  [ndiswrapper]("http://ubuntuforums.org/showthread.php?t=574501&highlight=ndiswrapper") and [WICD](http://wesleybailey.com/blog/2007/11/01/wireless-with-wicd/).
After a couple of days of head banging it finally all clicked into place. The final piece to fall in place was setting the "WPA Supplicant Driver" in the preference tab to 'wext' so I could connect to my WEP secured network.

---

