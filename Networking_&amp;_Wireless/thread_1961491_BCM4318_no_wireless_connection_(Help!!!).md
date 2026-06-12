---
title: "BCM4318 no wireless connection (Help!!!)"
date: 2012-04-19
forum: Networking &amp; Wireless
---

### Post by Debian1989 on 2012-04-19
Hi everyone I'm completely new to linux.[IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG]  i installed ubuntu two days ago  and have been able to get the wireless to work, my ethernet port works fine. At first it would show  the wireless connection in option but wouldn't pick up any networks. :confused: Now  the wireless option is gone all-together. [IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG] I really need help with this,  ive been trying for two days to do it on my own by reading forums but  i'm willing to admit defeat and ask for her. Can someone with some  experience please help me [IMG]http://ubuntuforums.org/images/icons/icon14.gif[/IMG]

---

### Post by josephmills on 2012-04-19
> **Debian1989 said:**
> Hi everyone I'm completely new to linux.[IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG]  i installed ubuntu two days ago  and have been able to get the wireless to work, my ethernet port works fine. At first it would show  the wireless connection in option but wouldn't pick up any networks. :confused: Now  the wireless option is gone all-together. [IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG] I really need help with this,  ive been trying for two days to do it on my own by reading forums but  i'm willing to admit defeat and ask for her. Can someone with some  experience please help me [IMG]http://ubuntuforums.org/images/icons/icon14.gif[/IMG]

Please open termina (ctrl+alt+t) and put in 
```
lspci -nn && lsmod && rfkill list all
```
then paste here thanks

---

### Post by Debian1989 on 2012-04-19
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)
02:01.0 CardBus bridge [0607]: Texas Instruments PCI1510 PC card Cardbus Controller [104c:ac56]
02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
02:08.0 Ethernet controller [0200]: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile [8086:1068] (rev 03)
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
dm_crypt               22565  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  8 bnep,rfcomm
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80468  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
joydev                 17393  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
dell_laptop            13519  0 
pcmcia                 39822  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
dcdbas                 14098  1 dell_laptop
yenta_socket           27428  0 
snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_rsrc            18367  1 yenta_socket
psmouse                73673  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
binfmt_misc            17292  1 
squashfs               36095  1 
overlayfs              27481  1 
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622589  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
usb_storage            44173  1 
uas                    17699  0 
i915                  505108  3 
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
e100                   36289  0 
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
zram                   18007  1

---

### Post by josephmills on 2012-04-19
> **Debian1989 said:**
> 00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)
02:01.0 CardBus bridge [0607]: Texas Instruments PCI1510 PC card Cardbus Controller [104c:ac56]
02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [COLOR="Red"][AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318][/COLOR] (rev 02)
02:08.0 Ethernet controller [0200]: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile [8086:1068] (rev 03)
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
dm_crypt               22565  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  8 bnep,rfcomm
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80468  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
joydev                 17393  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
dell_laptop            13519  0 
pcmcia                 39822  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
dcdbas                 14098  1 dell_laptop
yenta_socket           27428  0 
snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_rsrc            18367  1 yenta_socket
psmouse                73673  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
binfmt_misc            17292  1 
squashfs               36095  1 
overlayfs              27481  1 
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622589  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
usb_storage            44173  1 
uas                    17699  0 
i915                  505108  3 
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
e100                   36289  0 
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
zram                   18007  1

in terminal 

```
sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-installer 
```
then 
```
sudo modprobe b43
```

Do you have wireless if not please post 
```
lsmod && rfkill list all 
```

thanks

---

### Post by Debian1989 on 2012-04-19
I've been trying this first step and i always get this error message:

ubuntu@ubuntu:~$ sudo apt-get install b43 && sudo apt-get install firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package b43

---

### Post by Debian1989 on 2012-04-19
I followed the other steps and this is the result:

00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)
02:01.0 CardBus bridge [0607]: Texas Instruments PCI1510 PC card Cardbus Controller [104c:ac56]
02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
02:08.0 Ethernet controller [0200]: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile [8086:1068] (rev 03)
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
dm_crypt               22565  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  8 bnep,rfcomm
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80468  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
joydev                 17393  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
dell_laptop            13519  0 
pcmcia                 39822  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
dcdbas                 14098  1 dell_laptop
yenta_socket           27428  0 
snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_rsrc            18367  1 yenta_socket
psmouse                73673  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
binfmt_misc            17292  1 
squashfs               36095  1 
overlayfs              27481  1 
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622589  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
usb_storage            44173  1 
uas                    17699  0 
i915                  505108  3 
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
e100                   36289  0 
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
zram                   18007  1 
ubuntu@ubuntu:~$ sudo apt-get install b43 && sudo apt-get install firmware-b43-install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package b43
ubuntu@ubuntu:~$ sudo apt-get install b43 && sudo apt-get install firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package b43
ubuntu@ubuntu:~$ sudo modprobe b43
ubuntu@ubuntu:~$ lsmod && rfkill list all
Module                  Size  Used by
arc4                   12473  2 
b43                   318816  0 
ssb                    50682  1 b43
mac80211              272785  1 b43
cfg80211              172392  2 b43,mac80211
parport_pc             32114  0 
ppdev                  12849  0 
dm_crypt               22565  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  8 bnep,rfcomm
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80468  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
joydev                 17393  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
dell_laptop            13519  0 
pcmcia                 39822  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
dcdbas                 14098  1 dell_laptop
yenta_socket           27428  0 
snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_rsrc            18367  1 yenta_socket
psmouse                73673  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
binfmt_misc            17292  1 
squashfs               36095  1 
overlayfs              27481  1 
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622589  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
usb_storage            44173  1 
uas                    17699  0 
i915                  505108  3 
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
e100                   36289  0 
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
zram                   18007  1 
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by Debian1989 on 2012-04-19
wireless option is now back in network. :D but still says missing firmware

---

### Post by josephmills on 2012-04-19
ahh 

lets see 



```
dmesg | grep b43 
```

thanks

---

### Post by josephmills on 2012-04-19
> **Debian1989 said:**
> I followed the other steps and this is the result:


ubuntu@ubuntu:~$ sudo apt-get install b43 && sudo apt-get install firmware-b43-install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package b43
ubuntu@ubuntu:~$ sudo apt-get install b43 && sudo apt-get install firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package b43


also it is 

```
sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-installer
```

---

### Post by Debian1989 on 2012-04-19
This is the first command results:

ubuntu@ubuntu:~$ dmesg | grep b43
[ 5871.642021] b43-pci-bridge 0000:02:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 5871.743210] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[ 5872.109465] Registered led device: b43-phy0::tx
[ 5872.109502] Registered led device: b43-phy0::rx
[ 5872.109529] Registered led device: b43-phy0::radio
[ 5872.747258] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[ 5872.747268] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[ 5872.747275] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.

---

### Post by Debian1989 on 2012-04-19
This is for the second command:

ubuntu@ubuntu:~$ sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 415 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up initramfs-tools (0.99ubuntu7) ...
update-initramfs: deferring update (trigger activated)
lzma: Cannot allocate memory
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Setting up bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu4) ...
Removing old bcmwl-5.100.82.38+bdcom DKMS files...

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 5.100.82.38+bdcom
Kernel:  3.0.0-12-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.0.0-12-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod.........

DKMS: uninstall Completed.

------------------------------
Deleting module version: 5.100.82.38+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-5.100.82.38+bdcom DKMS files...
Building only for 3.0.0-12-generic
Building for architecture i686
Building initial module for 3.0.0-12-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-12-generic/updates/dkms/

depmod...........

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
lzma: Cannot allocate memory
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 initramfs-tools
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

