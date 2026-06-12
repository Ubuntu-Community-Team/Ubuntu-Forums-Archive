---
title: "Broadcom BCM4312 drivers installing on ubuntu server 13.04"
date: 2013-06-17
forum: Networking &amp; Wireless
---

### Post by diavol on 2013-06-17
Hi,
I am trying to install drivers for my bcm4312 wireles card on ubuntu server 13.04. I have followed instructions on [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt) and tried to both compile source and using apt-get [COLOR=#000000]install bcmwl-kernel-source. 
[/COLOR]
First, compiling:

```
diavol@MusicServer:~/broadcom$ make
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-25-generic'
Wireless Extension is the only possible API for this kernel version
Using Wireless Extension API
  CC [M]  /home/diavol/broadcom/src/wl/sys/wl_linux.o
/home/diavol/broadcom/src/wl/sys/wl_linux.c:43:24: fatal error: asm/system.h: No such file or directory
compilation terminated.
make[2]: *** [/home/diavol/broadcom/src/wl/sys/wl_linux.o] Error 1
make[1]: *** [_module_/home/diavol/broadcom] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-25-generic'
make: *** [all] Error 2



```
and I do not understand why it would not compile, can some one please explain?



Second, using apt-get [COLOR=#000000]install bcmwl-kernel-source:[/COLOR]
[COLOR=#000000]Well, it was no problem to install but after i rebooted ifconfig still not showing some wlan0 interface. In all guide that I found on google i have to go to Driver Manager and enable the driver but i do not have some X, it is a server and well, how can i do it in a terminal?[/COLOR]



[COLOR=#000000]Thankful for help, I have tried to search fo the problem but did not found something that have work for me. I have only used ubuntu with GUI or Arch linux before, so see this post like a ubuntunewbe post.[/COLOR]

[COLOR=#000000]\\diavol[/COLOR]

---

### Post by Hadaka on 2013-06-17
Hi,Let's see what dirver will work best for you..
please copy and paste the following commands.
```
lspci - nn | egrep '0200|0280'
lsmod
rfkill list all
```
please post the output.
thanks.

---

### Post by diavol on 2013-06-17
```

diavol@MusicServer:~/broadcom$ lspci -nn | grep '0200|0280'
diavol@MusicServer:~/broadcom$
diavol@MusicServer:~/broadcom$ lspci -nn
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8132 Fast Ethernet [1969:1062] (rev c0)
diavol@MusicServer:~/broadcom$ lsmod
Module                  Size  Used by
wl                   2902185  0
cfg80211              436177  1 wl
snd_hda_codec_realtek    63791  1
snd_hda_intel          38307  0
snd_hda_codec         117580  2 snd_hda_codec_realtek,snd_hda_intel
coretemp               13131  0
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80890  2 snd_hda_codec,snd_hda_intel
acer_wmi               27592  0
lib80211_crypt_tkip    17160  0
joydev                 17097  0
sparse_keymap          13658  1 acer_wmi
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25114  1 snd_seq_midi
uvcvideo               71279  0
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
lib80211               14040  2 wl,lib80211_crypt_tkip
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24411  2 snd_pcm,snd_seq
videobuf2_vmalloc      12920  1 uvcvideo
videobuf2_memops       13042  1 videobuf2_vmalloc
snd                    56485  9 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
microcode              18286  0
videobuf2_core         39161  1 uvcvideo
lpc_ich                16925  0
soundcore              12600  1 snd
videodev               95806  2 uvcvideo,videobuf2_core
psmouse                81038  0
serio_raw              13031  0
ext2                   63166  1
lp                     13299  0
mac_hid                13037  0
parport                40753  1 lp
xts                    12749  1
gf128mul               14503  1 xts
dm_crypt               22321  2
i915                  535544  1
i2c_algo_bit           13197  1 i915
atl1c                  36175  0
drm_kms_helper         47545  1 i915
drm                   228489  2 i915,drm_kms_helper
ahci                   25507  2
libahci                26108  1 ahci
wmi                    18590  1 acer_wmi
video                  18894  2 i915,acer_wmi
diavol@MusicServer:~/broadcom$ rfkill list all
2: acer-wireless: Wireless LAN
        Soft blocked: no
        Hard blocked: no
3: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
4: brcmwl-0: Wireless LAN
        Soft blocked: no
        Hard blocked: no




```

---

### Post by Hadaka on 2013-06-17
Hi, your wireless card..

Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] <- This number determines the card

does not use the broadcom-kernel-source dirver

please Copy and paste the following commands..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
remove your wired connection,,boot
and your wireless should work

---

### Post by diavol on 2013-06-17
Well, it did not help, at least still no wlan interface in ifconfig output. 
Is it something else that I could do?

post output for 

```
lspci -nn | egrep '0200|0280'
lsmod
rfkill list all
```
again: 

```
diavol@MusicServer:~$ lspci -nn | egrep '0200|0280'
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8132 Fast Ethernet [1969:1062] (rev c0)
diavol@MusicServer:~$ lsmod
Module                  Size  Used by
coretemp               13131  0
joydev                 17097  0
acer_wmi               27592  0
sparse_keymap          13658  1 acer_wmi
snd_hda_codec_realtek    63791  1
snd_hda_intel          38307  0
snd_hda_codec         117580  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80890  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
microcode              18286  0
snd_seq_midi           13132  0
uvcvideo               71279  0
videobuf2_vmalloc      12920  1 uvcvideo
snd_seq_midi_event     14475  1 snd_seq_midi
videobuf2_memops       13042  1 videobuf2_vmalloc
snd_rawmidi            25114  1 snd_seq_midi
videobuf2_core         39161  1 uvcvideo
psmouse                81038  0
lpc_ich                16925  0
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
serio_raw              13031  0
videodev               95806  2 uvcvideo,videobuf2_core
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24411  2 snd_pcm,snd_seq
snd                    56485  9 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              12600  1 snd
mac_hid                13037  0
lp                     13299  0
parport                40753  1 lp
ext2                   63166  1
xts                    12749  1
gf128mul               14503  1 xts
dm_crypt               22321  2
i915                  535544  1
ahci                   25507  2
libahci                26108  1 ahci
atl1c                  36175  0
i2c_algo_bit           13197  1 i915
drm_kms_helper         47545  1 i915
wmi                    18590  1 acer_wmi
drm                   228489  2 i915,drm_kms_helper
video                  18894  2 i915,acer_wmi
diavol@MusicServer:~$ rfkill list all
0: acer-wireless: Wireless LAN
        Soft blocked: yes
        Hard blocked: no

```

---

### Post by Hadaka on 2013-06-17
Hi, yes...please do..
```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
then from a wired connection do..
```
rkill unblock all
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
post any errors
thanks.

---

### Post by diavol on 2013-06-18
Despite of acer_wmi are not i the output of lsmod now, still no wlan interface.

---

### Post by Hadaka on 2013-06-18
ok, lets see if that wireless soft block is still there
please do..
```
sudo rfkill unblock all
sudo rfkill list all
```
you may have to power cycle the computer also.
thanks

---

### Post by diavol on 2013-06-18
No, no soft block anymore, but still not working after reboot.

---

### Post by Hadaka on 2013-06-18
ok, lets do this, i am finding several posts from dr chili
that have this wifi card [14e4:4315] using the wl driver
so my cheat sheet may be in error. 
please do..
```
sudo apt-get update
sudo apt-get upgrade

```
then do..
```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```
and post..
```
lsmod
dmesg | tail -n 20
```
thanks

---

### Post by diavol on 2013-06-18
```
diavol@MusicServer:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
diavol@MusicServer:~$ sudo apt-get install linux-headers-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
linux-headers-generic is already the newest version.
The following package was automatically installed and is no longer required:
  dkms
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
diavol@MusicServer:~$ sudo apt-get install --reinstall bcmwl-kernel-source
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1,303 kB of archives.
After this operation, 3,661 kB of additional disk space will be used.
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 95927 files and directories currently installed.)
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu6_i386.deb) ...
Setting up bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu6) ...
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.8.0-25-generic
Building for architecture i686
Building initial module for 3.8.0-25-generic
Done.


wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.8.0-25-generic/updates/dkms/


depmod..........


DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-25-generic




diavol@MusicServer:~$ sudo modprobe wl
diavol@MusicServer:~$ lsmod
Module                  Size  Used by
lib80211_crypt_tkip    17160  0
wl                   2902185  0
lib80211               14040  2 wl,lib80211_crypt_tkip
mac80211              526519  0
cfg80211              436177  2 wl,mac80211
arc4                   12543  0
joydev                 17097  0
coretemp               13131  0
snd_hda_codec_realtek    63791  1
snd_hda_intel          38307  0
snd_hda_codec         117580  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80890  2 snd_hda_codec,snd_hda_intel
uvcvideo               71279  0
videobuf2_vmalloc      12920  1 uvcvideo
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
microcode              18286  0
videobuf2_memops       13042  1 videobuf2_vmalloc
snd_seq_midi           13132  0
snd_seq_midi_event     14475  1 snd_seq_midi
lpc_ich                16925  0
snd_rawmidi            25114  1 snd_seq_midi
videobuf2_core         39161  1 uvcvideo
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
psmouse                81038  0
videodev               95806  2 uvcvideo,videobuf2_core
serio_raw              13031  0
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24411  2 snd_pcm,snd_seq
snd                    56485  9 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              12600  1 snd
mac_hid                13037  0
lp                     13299  0
parport                40753  1 lp
ext2                   63166  1
xts                    12749  1
gf128mul               14503  1 xts
dm_crypt               22321  2
i915                  535544  1
ahci                   25507  2
libahci                26108  1 ahci
i2c_algo_bit           13197  1 i915
drm_kms_helper         47545  1 i915
atl1c                  36175  0
wmi                    18590  0
drm                   228489  2 i915,drm_kms_helper
video                  18894  1 i915
diavol@MusicServer:~$ dmesg | tail -n 20
[ 1664.331237] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1664.331244] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1664.476137] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[ 1664.520216] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
[ 1664.544502] Broadcom 43xx driver loaded [ Features: PNL ]
[ 1664.551298] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[ 1669.084420] atl1c 0000:03:00.0: irq 45 for MSI/MSI-X
[ 1669.084554] atl1c 0000:03:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[ 1758.511740] atl1c 0000:03:00.0: irq 45 for MSI/MSI-X
[ 1758.511876] atl1c 0000:03:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[ 2946.600463] atl1c 0000:03:00.0: irq 45 for MSI/MSI-X
[ 2946.600608] atl1c 0000:03:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[ 4131.276394] lib80211: common routines for IEEE802.11 drivers
[ 4131.276406] lib80211_crypt: registered algorithm 'NULL'
[ 4131.294647] wl: module license 'MIXED/Proprietary' taints kernel.
[ 4131.320289] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[ 4131.355454] lib80211_crypt: registered algorithm 'TKIP'
[ 4131.561408] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)
[ 4313.205609] atl1c 0000:03:00.0: irq 45 for MSI/MSI-X
[ 4313.205744] atl1c 0000:03:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
diavol@MusicServer:~$ sudo rfkill list all
2: phy1: Wireless LAN
        Soft blocked: no
        Hard blocked: no
3: brcmwl-0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

```

---

### Post by Hadaka on 2013-06-18
k, looks like the module loaded, thats a good thing.
please post the output of..
```
sudo apt-get autoremove
cat /etc/modules
cat /etc/network/interfaces
cat /etc/modprobe.d/blacklist.conf | grep blacklist
```
Its the wee hours of the morning here, I'll look at this tomorrow
thanks.

---

### Post by diavol on 2013-06-18
```

diavol@MusicServer:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


diavol@MusicServer:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.


loop
lp


diavol@MusicServer:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet dhcp


diavol@MusicServer:~$ cat /etc/modprobe.d/blacklist.conf | grep blacklist
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist acer_wmi
diavol@MusicServer:~$

```

---

### Post by Hadaka on 2013-06-18
Let's see if we can get some different info.
please do..
```
sudo modprobe -rf b43 ssb wl brcmfmac brcmsmac bcma
sudo modprobe wl
dmesg | tail -n 20
```
thanks.

---

### Post by chili555 on 2013-06-18
If I may be excused for stepping in, I suggest you hook up the ethernet temporarily and do:```
sudo apt-get remove --purge bcmwl-kernel source
sudo apt-get install firmware-b43-[COLOR="#FF0000"]lpphy[/COLOR]-installer
```...Because you have:> Broadcom Corporation BCM4312 802.11b/g [COLOR="#FF0000"]LP-PHY[/COLOR] [14e4:4315]Then detach the ethernet, reboot and show us:```
iwconfig
dmesg | grep b43
```

---

### Post by diavol on 2013-06-18
Now it works!
Will just add little how i did:

I run the code you gave me and on [COLOR=#000000][FONT=Ubuntu Mono]dmesg | tail -n 20[/FONT][/COLOR] I noticed that:
```

[35959.848284] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)

```

When I used ifconfig, i still was not able to see something except the eth0 (wired connection) and lo, but ifconfig eth1 and iwconfig eth1 gave me the right output. Then:
```
sudo ifconfig eth1 down
sudo iwconfig eth1 mode monitor
```

After that I was able to get the corect output by ifconfig. And with little editing in /etc/network/interfaces i was able to connect to AP.

Thank you wery much for help!
\\diavol

---

