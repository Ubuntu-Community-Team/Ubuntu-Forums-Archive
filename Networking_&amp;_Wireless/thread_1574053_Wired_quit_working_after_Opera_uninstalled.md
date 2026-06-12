---
title: "Wired quit working after Opera uninstalled"
date: 2010-09-12
forum: Networking &amp; Wireless
---

### Post by kiltedwonder on 2010-09-12
I'm having a [similar issue]("http://ubuntuforums.org/showthread.php?t=1572310") on a custom machine with an MSI 785GT-E63 motherboard and a Belkin gigabit/N+ router (exact model unknown).  My internet stopped working after I uninstalled Opera.  I went ahead and ran all the commands Utilitytrack requested:

evan@evan-desktop:~$ lsb_release --all
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.1 LTS
Release:	10.04
Codename:	lucid

evan@evan-desktop:~$ uname -a
Linux evan-desktop 2.6.32-24-generic-pae #42-Ubuntu SMP Fri Aug 20 15:37:22 UTC 2010 i686 GNU/Linux

evan@evan-desktop:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic-pae root=UUID=015e4a56-ea3b-4486-8940-32bdde6cb046 ro quiet splash

evan@evan-desktop:~$ lspci -nn | grep -E 'Ethernet|Network'
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)

evan@evan-desktop:~$ dmesg | grep eth
[    0.173607] ACPI Error (psparse-0537): Method parse/execution failed [\] (Node c0923024), AE_NOT_FOUND
[    0.180678] ACPI Error (psparse-0537): Method parse/execution failed [\PRID.P_D0._STA] (Node f742b858), AE_NOT_EXIST
[    0.180695] ACPI Error (uteval-0250): Method execution failed [\PRID.P_D0._STA] (Node f742b858), AE_NOT_EXIST
[    0.180711] ACPI Error (psparse-0537): Method parse/execution failed [\PRID.P_D1._STA] (Node f742b900), AE_NOT_EXIST
[    0.180728] ACPI Error (uteval-0250): Method execution failed [\PRID.P_D1._STA] (Node f742b900), AE_NOT_EXIST
[    0.180744] ACPI Error (psparse-0537): Method parse/execution failed [\SECD.S_D0._STA] (Node f742ba68), AE_NOT_EXIST
[    0.180761] ACPI Error (uteval-0250): Method execution failed [\SECD.S_D0._STA] (Node f742ba68), AE_NOT_EXIST
[    0.180776] ACPI Error (psparse-0537): Method parse/execution failed [\SECD.S_D1._STA] (Node f742bb10), AE_NOT_EXIST
[    0.180793] ACPI Error (uteval-0250): Method execution failed [\SECD.S_D1._STA] (Node f742bb10), AE_NOT_EXIST
[    0.186279] ACPI Error (psparse-0537): Method parse/execution failed [\PRID.P_D0._STA] (Node f742b858), AE_NOT_EXIST
[    0.186309] ACPI Error (psparse-0537): Method parse/execution failed [\PRID.P_D1._STA] (Node f742b900), AE_NOT_EXIST
[    0.186353] ACPI Error (psparse-0537): Method parse/execution failed [\SECD.S_D0._STA] (Node f742ba68), AE_NOT_EXIST
[    0.186383] ACPI Error (psparse-0537): Method parse/execution failed [\SECD.S_D1._STA] (Node f742bb10), AE_NOT_EXIST
[    0.195343] ACPI Error (psparse-0537): Method parse/execution failed [\PRID.P_D0._STA] (Node f742b858), AE_NOT_EXIST
[    0.195343] ACPI Error (uteval-0250): Method execution failed [\PRID.P_D0._STA] (Node f742b858), AE_NOT_EXIST
[    0.195343] ACPI Error (psparse-0537): Method parse/execution failed [\PRID.P_D1._STA] (Node f742b900), AE_NOT_EXIST
[    0.195343] ACPI Error (uteval-0250): Method execution failed [\PRID.P_D1._STA] (Node f742b900), AE_NOT_EXIST
[    0.195343] ACPI Error (psparse-0537): Method parse/execution failed [\SECD.S_D0._STA] (Node f742ba68), AE_NOT_EXIST
[    0.195343] ACPI Error (uteval-0250): Method execution failed [\SECD.S_D0._STA] (Node f742ba68), AE_NOT_EXIST
[    0.195343] ACPI Error (psparse-0537): Method parse/execution failed [\SECD.S_D1._STA] (Node f742bb10), AE_NOT_EXIST
[    0.195343] ACPI Error (uteval-0250): Method execution failed [\SECD.S_D1._STA] (Node f742bb10), AE_NOT_EXIST
[    0.422106] ACPI Error (psparse-0537): Method parse/execution failed [\PRID.P_D0._STA] (Node f742b858), AE_NOT_EXIST
[    0.422124] ACPI Error (uteval-0250): Method execution failed [\PRID.P_D0._STA] (Node f742b858), AE_NOT_EXIST
[    0.422143] ACPI Error (psparse-0537): Method parse/execution failed [\PRID.P_D1._STA] (Node f742b900), AE_NOT_EXIST
[    0.422160] ACPI Error (uteval-0250): Method execution failed [\PRID.P_D1._STA] (Node f742b900), AE_NOT_EXIST
[    0.422184] ACPI Error (psparse-0537): Method parse/execution failed [\SECD.S_D0._STA] (Node f742ba68), AE_NOT_EXIST
[    0.422201] ACPI Error (uteval-0250): Method execution failed [\SECD.S_D0._STA] (Node f742ba68), AE_NOT_EXIST
[    0.422219] ACPI Error (psparse-0537): Method parse/execution failed [\SECD.S_D1._STA] (Node f742bb10), AE_NOT_EXIST
[    0.422236] ACPI Error (uteval-0250): Method execution failed [\SECD.S_D1._STA] (Node f742bb10), AE_NOT_EXIST
[    0.837078] eth0: RTL8168d/8111d at 0xf82a6000, 40:61:86:be:7d:70, XID 081000c0 IRQ 26
[   21.079035] r8169: eth0: link down
[   21.079175] ADDRCONF(NETDEV_UP): eth0: link is not ready

evan@evan-desktop:~$ ps -f | grep -E -i 'supplicant|Netwo|nm-app'
evan      1853  1822  0 16:02 pts/0    00:00:00 grep --color=auto -E -i supplicant|Netwo|nm-app

evan@evan-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 40:61:86:be:7d:70  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:26 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

evan@evan-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

evan@evan-desktop:~$ ls -l /etc/modprobe.d/*
-rw-r--r-- 1 root root 2386 2010-01-28 19:01 /etc/modprobe.d/alsa-base.conf
-rw-r--r-- 1 root root  325 2009-09-15 17:46 /etc/modprobe.d/blacklist-ath_pci.conf
-rw-r--r-- 1 root root 1603 2009-09-15 17:46 /etc/modprobe.d/blacklist.conf
-rw-r--r-- 1 root root  213 2009-09-15 17:46 /etc/modprobe.d/blacklist-firewire.conf
-rw-r--r-- 1 root root  660 2010-04-14 00:26 /etc/modprobe.d/blacklist-framebuffer.conf
-rw-r--r-- 1 root root  156 2009-10-11 18:07 /etc/modprobe.d/blacklist-modem.conf
lrwxrwxrwx 1 root root   41 2010-05-07 13:53 /etc/modprobe.d/blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r-- 1 root root 1077 2009-09-15 17:46 /etc/modprobe.d/blacklist-watchdog.conf
-rw-r--r-- 1 root root   16 2009-08-26 05:49 /etc/modprobe.d/libpisock9.conf

evan@evan-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

evan@evan-desktop:~$ lspci -nn
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate [1022:9601]
00:01.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx) [1022:9602]
00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) [1022:9605]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] [1002:4390]
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:12.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 3c)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB700/SB800 IDE Controller [1002:439c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:14.5 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller [1002:4399]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control [1022:1203]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control [1022:1204]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS880 [Radeon HD 4200] [1002:9710]
01:05.1 Audio device [0403]: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200] [1002:970f]
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)

evan@evan-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_atihdmi     2367  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_codec_realtek   203312  1 
snd_hda_intel          22037  2 
snd_hda_codec          74201  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70886  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
radeon                695210  2 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ttm                    50071  1 radeon
drm_kms_helper         29297  1 radeon
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   163098  4 radeon,ttm,drm_kms_helper
psmouse                63245  0 
lp                      7028  0 
serio_raw               3978  0 
soundcore               6620  1 snd
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
i2c_piix4               8527  0 
agpgart                31788  2 ttm,drm
i2c_algo_bit            5028  1 radeon
parport                32635  2 ppdev,lp
shpchp                 28884  0 
usbhid                 36174  0 
usb_storage            39457  1 
hid                    67032  1 usbhid
r8169                  34300  0 
mii                     4381  1 r8169
pata_atiixp             3148  2 
ahci                   32232  0

---

### Post by utilitytrack on 2010-09-12
```
evan@evan-desktop:~$ uname -a
Linux evan-desktop 2.6.32-24-generic-pae #42-Ubuntu SMP Fri Aug 20 15:37:22 UTC 2010 i686 GNU/Linux

```

First, I'm not understand why you need PAE kernel while your machine is x86. You have more than 4GB RAM?

> 
I'm having a similar issue on a custom machine with an MSI 785GT-E63 motherboard and a Belkin gigabit/N+ router 

> I have it connected to an asus rt-n16...

Second, let's will be solve troubles for somehow one machine, ok?
In other case it's simply not possible to understand the situation.

Please definitely say, which machine is faulty and to which of them belong outputs in your second post.

---

### Post by utilitytrack on 2010-09-13
> At any rate, I just booted into Ubuntu, and without doing anything, the eth0 connection is ok 

Hmm...

> My ethernet is still not working.

You wrote this about the same machine?

> Any chance you could continue to help me here since there was no definitive answer as to what fixed his?

Yes, if you will exactly answer on my questions.

> I only have 4 gigs of ram.  This was a standard install. 


First, definitely say what PC/laptop has problems with network.
Next post output of following commands (**run it ONLY on the machine that has network problems**)
```
$ free -m
$ uname -a
$ cat /proc/cmdline
$ lspci -nn
$ cat /etc/network/interfaces
$ ps -f | grep -E -i 'supplicant|network|nm-app|wicd'
$ ifconfig -a
# lshw -C network
```

---

### Post by kiltedwonder on 2010-09-13
> **utilitytrack said:**
> Hmm...



You wrote this about the same machine?

No.  

I accidentally confused you.  **I am not the original poster**, but I am having a very similar problem to the original poster.  I apologize for the confusion and thanks for your willingness to help.  The original poster's problem seems to have resolved itself.  Mine has not.

Here is my info (once again, **NOT the original machine**):


> evan@evan-desktop:~$ lsb_release --all
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.1 LTS
Release:	10.04
Codename:	lucid

evan@evan-desktop:~$ uname -a
Linux evan-desktop 2.6.32-24-generic-pae #42-Ubuntu SMP Fri Aug 20 15:37:22 UTC 2010 i686 GNU/Linux

evan@evan-desktop:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic-pae root=UUID=015e4a56-ea3b-4486-8940-32bdde6cb046 ro quiet splash

evan@evan-desktop:~$ lspci -nn | grep -E 'Ethernet|Network'
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)

evan@evan-desktop:~$ dmesg | grep eth
[    0.173607] ACPI Error (psparse-0537): Method parse/execution failed [\] (Node c0923024), AE_NOT_FOUND
[    0.180678] ACPI Error (psparse-0537): Method parse/execution failed [\PRID.P_D0._STA] (Node f742b858), AE_NOT_EXIST
[    0.180695] ACPI Error (uteval-0250): Method execution failed [\PRID.P_D0._STA] (Node f742b858), AE_NOT_EXIST
[    0.180711] ACPI Error (psparse-0537): Method parse/execution failed [\PRID.P_D1._STA] (Node f742b900), AE_NOT_EXIST
[    0.180728] ACPI Error (uteval-0250): Method execution failed [\PRID.P_D1._STA] (Node f742b900), AE_NOT_EXIST
[    0.180744] ACPI Error (psparse-0537): Method parse/execution failed [\SECD.S_D0._STA] (Node f742ba68), AE_NOT_EXIST
[    0.180761] ACPI Error (uteval-0250): Method execution failed [\SECD.S_D0._STA] (Node f742ba68), AE_NOT_EXIST
[    0.180776] ACPI Error (psparse-0537): Method parse/execution failed [\SECD.S_D1._STA] (Node f742bb10), AE_NOT_EXIST
[    0.180793] ACPI Error (uteval-0250): Method execution failed [\SECD.S_D1._STA] (Node f742bb10), AE_NOT_EXIST
[    0.186279] ACPI Error (psparse-0537): Method parse/execution failed [\PRID.P_D0._STA] (Node f742b858), AE_NOT_EXIST
[    0.186309] ACPI Error (psparse-0537): Method parse/execution failed [\PRID.P_D1._STA] (Node f742b900), AE_NOT_EXIST
[    0.186353] ACPI Error (psparse-0537): Method parse/execution failed [\SECD.S_D0._STA] (Node f742ba68), AE_NOT_EXIST
[    0.186383] ACPI Error (psparse-0537): Method parse/execution failed [\SECD.S_D1._STA] (Node f742bb10), AE_NOT_EXIST
[    0.195343] ACPI Error (psparse-0537): Method parse/execution failed [\PRID.P_D0._STA] (Node f742b858), AE_NOT_EXIST
[    0.195343] ACPI Error (uteval-0250): Method execution failed [\PRID.P_D0._STA] (Node f742b858), AE_NOT_EXIST
[    0.195343] ACPI Error (psparse-0537): Method parse/execution failed [\PRID.P_D1._STA] (Node f742b900), AE_NOT_EXIST
[    0.195343] ACPI Error (uteval-0250): Method execution failed [\PRID.P_D1._STA] (Node f742b900), AE_NOT_EXIST
[    0.195343] ACPI Error (psparse-0537): Method parse/execution failed [\SECD.S_D0._STA] (Node f742ba68), AE_NOT_EXIST
[    0.195343] ACPI Error (uteval-0250): Method execution failed [\SECD.S_D0._STA] (Node f742ba68), AE_NOT_EXIST
[    0.195343] ACPI Error (psparse-0537): Method parse/execution failed [\SECD.S_D1._STA] (Node f742bb10), AE_NOT_EXIST
[    0.195343] ACPI Error (uteval-0250): Method execution failed [\SECD.S_D1._STA] (Node f742bb10), AE_NOT_EXIST
[    0.422106] ACPI Error (psparse-0537): Method parse/execution failed [\PRID.P_D0._STA] (Node f742b858), AE_NOT_EXIST
[    0.422124] ACPI Error (uteval-0250): Method execution failed [\PRID.P_D0._STA] (Node f742b858), AE_NOT_EXIST
[    0.422143] ACPI Error (psparse-0537): Method parse/execution failed [\PRID.P_D1._STA] (Node f742b900), AE_NOT_EXIST
[    0.422160] ACPI Error (uteval-0250): Method execution failed [\PRID.P_D1._STA] (Node f742b900), AE_NOT_EXIST
[    0.422184] ACPI Error (psparse-0537): Method parse/execution failed [\SECD.S_D0._STA] (Node f742ba68), AE_NOT_EXIST
[    0.422201] ACPI Error (uteval-0250): Method execution failed [\SECD.S_D0._STA] (Node f742ba68), AE_NOT_EXIST
[    0.422219] ACPI Error (psparse-0537): Method parse/execution failed [\SECD.S_D1._STA] (Node f742bb10), AE_NOT_EXIST
[    0.422236] ACPI Error (uteval-0250): Method execution failed [\SECD.S_D1._STA] (Node f742bb10), AE_NOT_EXIST
[    0.837078] eth0: RTL8168d/8111d at 0xf82a6000, 40:61:86:be:7d:70, XID 081000c0 IRQ 26
[   21.079035] r8169: eth0: link down
[   21.079175] ADDRCONF(NETDEV_UP): eth0: link is not ready

evan@evan-desktop:~$ ps -f | grep -E -i 'supplicant|Netwo|nm-app'
evan      1853  1822  0 16:02 pts/0    00:00:00 grep --color=auto -E -i supplicant|Netwo|nm-app

evan@evan-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 40:61:86:be:7d:70  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:26 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

evan@evan-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

evan@evan-desktop:~$ ls -l /etc/modprobe.d/*
-rw-r--r-- 1 root root 2386 2010-01-28 19:01 /etc/modprobe.d/alsa-base.conf
-rw-r--r-- 1 root root  325 2009-09-15 17:46 /etc/modprobe.d/blacklist-ath_pci.conf
-rw-r--r-- 1 root root 1603 2009-09-15 17:46 /etc/modprobe.d/blacklist.conf
-rw-r--r-- 1 root root  213 2009-09-15 17:46 /etc/modprobe.d/blacklist-firewire.conf
-rw-r--r-- 1 root root  660 2010-04-14 00:26 /etc/modprobe.d/blacklist-framebuffer.conf
-rw-r--r-- 1 root root  156 2009-10-11 18:07 /etc/modprobe.d/blacklist-modem.conf
lrwxrwxrwx 1 root root   41 2010-05-07 13:53 /etc/modprobe.d/blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r-- 1 root root 1077 2009-09-15 17:46 /etc/modprobe.d/blacklist-watchdog.conf
-rw-r--r-- 1 root root   16 2009-08-26 05:49 /etc/modprobe.d/libpisock9.conf

evan@evan-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

evan@evan-desktop:~$ lspci -nn
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate [1022:9601]
00:01.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx) [1022:9602]
00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) [1022:9605]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] [1002:4390]
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:12.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 3c)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB700/SB800 IDE Controller [1002:439c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:14.5 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller [1002:4399]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control [1022:1203]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control [1022:1204]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS880 [Radeon HD 4200] [1002:9710]
01:05.1 Audio device [0403]: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200] [1002:970f]
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)

evan@evan-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_atihdmi     2367  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_codec_realtek   203312  1 
snd_hda_intel          22037  2 
snd_hda_codec          74201  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70886  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
radeon                695210  2 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ttm                    50071  1 radeon
drm_kms_helper         29297  1 radeon
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   163098  4 radeon,ttm,drm_kms_helper
psmouse                63245  0 
lp                      7028  0 
serio_raw               3978  0 
soundcore               6620  1 snd
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
i2c_piix4               8527  0 
agpgart                31788  2 ttm,drm
i2c_algo_bit            5028  1 radeon
parport                32635  2 ppdev,lp
shpchp                 28884  0 
usbhid                 36174  0 
usb_storage            39457  1 
hid                    67032  1 usbhid
r8169                  34300  0 
mii                     4381  1 r8169
pata_atiixp             3148  2 
ahci                   32232  0 

---

### Post by utilitytrack on 2010-09-13
> **kiltedwonder said:**
> No. I accidentally confused you.  **I am not the original poster**


Yes?!?!... Really... OMG, I just now noticed it, thanks :))

:))))))

---

### Post by Iowan on 2010-09-13
Moved to separate thread.
Having two tracks in the same thread usually causes confusion. That's why it's ordinarily better to start your own thread - link to the similar one, if necessary. Seldom are two problems identical, and a separate thread lets troubleshooters tailor their responses to YOUR problem... plus, you can mark your own thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") - if/when it is.

---

### Post by utilitytrack on 2010-09-13
Thank you, Iowan

---

