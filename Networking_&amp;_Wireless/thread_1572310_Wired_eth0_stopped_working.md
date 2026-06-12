---
title: "Wired eth0 stopped working"
date: 2010-09-10
forum: Networking &amp; Wireless
---

### Post by senormoll on 2010-09-10
Hey all, I can't find a solution to this but im hoping its easy and im just not searching properly.  All of a sudden my wired nic is not working anymore.  I've tried booting into older kernels and tried reinstalling my root partition.  Neither of these worked, so im thinking it is a setting of mine that is messing it up, but I don't remember changing anything.  It works fine on windows 7, so its not hardware.  I know this is a vague description but just tell me what output you may need if you can help.  Thanks!

---

### Post by utilitytrack on 2010-09-11
Hello, can you please give here output of these commands:
```

$ lsb_release --all
$ uname -a
$ cat /proc/cmdline
$ lspci -nn | grep -E 'Ethernet|Network'
$ dmesg | grep eth
$ ps -f | grep -E -i 'supplicant|Netwo|nm-app'
# ifconfig -a
# cat /etc/network/interfaces
# ls -l /etc/modprobe.d/*
# route -n
```

---

### Post by senormoll on 2010-09-11
Thanks for the quick reply!  Here's what you requested:

chris@chris-desktop:~$ lsb_release --all
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04 LTS
Release:    10.04
Codename:    lucid

chris@chris-desktop:~$ uname -a
Linux chris-desktop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux

chris@chris-desktop:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=30365eb0-a322-4858-b1ff-4db2f7e4aafd ro quiet splash

chris@chris-desktop:~$ lspci -nn | grep -E 'Ethernet|Network'
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)

chris@chris-desktop:~$ dmesg | grep eth
[    2.023131] eth0: RTL8168d/8111d at 0xffffc90000c72000, 00:24:1d:d2:16:b6, XID 083000c0 IRQ 33
[    8.491835] r8169: eth0: link down
[    8.492330] ADDRCONF(NETDEV_UP): eth0: link is not ready

chris@chris-desktop:~$ ps -f | grep -E -i 'supplicant|Netwo|nm-app'
chris     1815  1750  0 22:35 pts/0    00:00:00 grep --color=auto -E -i supplicant|Netwo|nm-app

chris@chris-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:24:1d:d2:16:b6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1740 (1.7 KB)  TX bytes:0 (0.0 B)
          Interrupt:33 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

chris@chris-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

chris@chris-desktop:~$ ls -l /etc/modprobe.d/*
-rw-r--r-- 1 root root 2386 2010-01-28 19:01 /etc/modprobe.d/alsa-base.conf
-rw-r--r-- 1 root root  325 2010-04-14 00:36 /etc/modprobe.d/blacklist-ath_pci.conf
-rw-r--r-- 1 root root 1603 2010-04-14 00:36 /etc/modprobe.d/blacklist.conf
-rw-r--r-- 1 root root  213 2010-04-14 00:36 /etc/modprobe.d/blacklist-firewire.conf
-rw-r--r-- 1 root root  660 2010-04-14 00:36 /etc/modprobe.d/blacklist-framebuffer.conf
-rw-r--r-- 1 root root  156 2010-01-28 19:01 /etc/modprobe.d/blacklist-modem.conf
lrwxrwxrwx 1 root root   41 2010-09-10 17:32 /etc/modprobe.d/blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r-- 1 root root 1077 2010-04-14 00:36 /etc/modprobe.d/blacklist-watchdog.conf
-rw-r--r-- 1 root root   16 2010-01-06 03:13 /etc/modprobe.d/libpisock9.conf

chris@chris-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

---

### Post by utilitytrack on 2010-09-12
Please write what PC/laptop you use, what is the device that you connected through Ethernet link, and post outputs of [FONT="Courier New"]$ lspci -nn[/FONT] (full output for clarity) and [FONT="Courier New"]# lsmod[/FONT]

On this time it seems that Ethernet interface simply not configured, so no serious troubles.

---

### Post by senormoll on 2010-09-12
I have it connected to an asus rt-n16...it's a custom built desktop so i'm using the onboard NIC for my P55-UD3R.  Thanks again for the help

chris@chris-desktop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DMI [8086:d131] (rev 11)
00:03.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express Root Port 1 [8086:d138] (rev 11)
00:08.0 System peripheral [0880]: Intel Corporation Core Processor System Management Registers [8086:d155] (rev 11)
00:08.1 System peripheral [0880]: Intel Corporation Core Processor Semaphore and Scratchpad Registers [8086:d156] (rev 11)
00:08.2 System peripheral [0880]: Intel Corporation Core Processor System Control and Status Registers [8086:d157] (rev 11)
00:08.3 System peripheral [0880]: Intel Corporation Core Processor Miscellaneous Registers [8086:d158] (rev 11)
00:10.0 System peripheral [0880]: Intel Corporation Core Processor QPI Link [8086:d150] (rev 11)
00:10.1 System peripheral [0880]: Intel Corporation Core Processor QPI Routing and Protocol Registers [8086:d151] (rev 11)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller [8086:3b3b] (rev 05)
00:1a.1 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller [8086:3b3e] (rev 05)
00:1a.2 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller [8086:3b3f] (rev 05)
00:1a.7 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05)
00:1c.3 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 [8086:3b48] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller [8086:3b36] (rev 05)
00:1d.1 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller [8086:3b37] (rev 05)
00:1d.2 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller [8086:3b38] (rev 05)
00:1d.3 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller [8086:3b39] (rev 05)
00:1d.7 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation 5 Series Chipset LPC Interface Controller [8086:3b02] (rev 05)
00:1f.2 IDE interface [0101]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller [8086:3b20] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
00:1f.5 IDE interface [0101]: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller [8086:3b26] (rev 05)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Device [1002:689e]
01:00.1 Audio device [0403]: ATI Technologies Inc Cypress HDMI Audio [Radeon HD 5800 Series] [1002:aa50]
02:00.0 SATA controller [0106]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 02)
02:00.1 IDE interface [0101]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 02)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
04:00.0 SATA controller [0106]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 03)
04:00.1 IDE interface [0101]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 03)
05:05.0 Multimedia audio controller [0401]: Creative Labs CA0106 Soundblaster [1102:0007]

chris@chris-desktop:~$ sudo lsmod
[sudo] password for chris: 
Module                  Size  Used by
nls_iso8859_1           4633  1 
nls_cp437               6351  1 
vfat                   10802  1 
fat                    55350  1 vfat
binfmt_misc             7960  1 
joydev                 11072  0 
snd_hda_codec_atihdmi     3023  1 
snd_hda_codec_realtek   278890  1 
snd_ca0106             38051  2 
snd_ac97_codec        125394  1 snd_ca0106
ac97_bus                1450  1 snd_ac97_codec
snd_hda_intel          25645  2 
snd_hda_codec          85727  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87850  5 snd_ca0106,snd_ac97_codec,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  2 snd_ca0106,snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23553  2 snd_pcm,snd_seq
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   6375  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
parport_pc             29958  1 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
snd                    70978  22 snd_hda_codec_realtek,snd_ca0106,snd_ac97_codec,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
usbhid                 40988  0 
serio_raw               4918  0 
soundcore               8052  1 snd
snd_page_alloc          8500  3 snd_ca0106,snd_hda_intel,snd_pcm
lp                      9336  0 
parport                37160  3 ppdev,parport_pc,lp
hid                    83376  1 usbhid
usb_storage            49833  2 
r8169                  39554  0 
mii                     5237  1 r8169
ahci                   37646  0 
pata_jmicron            2747  0

---

### Post by Iowan on 2010-09-12
A couple of things to check:
Right-click Network Manager icon and verify Networking is enabled.
[http://ubuntuforums.org/showthread.php?t=1484913]("http://ubuntuforums.org/showthread.php?t=1484913")
[http://ubuntuforums.org/showthread.php?t=1537792]("http://ubuntuforums.org/showthread.php?t=1537792")

---

### Post by senormoll on 2010-09-12
I'm going to switch the ubuntu now to check the configuration files mentioned in those threads, but i'm 100% sure networking is enabled in the panel.  I've even tried toggling it to no avail

---

### Post by senormoll on 2010-09-12
I'm sorry, but your post is not very clear.  I'm not sure if what you said is directed toward me, but the asus rt-n16 is a router.  

At any rate, I just booted into Ubuntu, and without doing anything, the eth0 connection is ok (i'm on it right now)...so after a month+ of it not working now all of a sudden it's ok.  I'm not sure if it's something I ran in the terminal that you gave me or just dumb luck.  I'm gonna mark the thread as solved as soon as I can confirm that it stays working.  Thanks for all the help! :D

---

### Post by utilitytrack on 2010-09-13
You are right, it's my mistake. But I glad for you anyway.

---

### Post by kiltedwonder on 2010-09-13
I think the confusion was my fault.  I popped in with a second computer because my issue is so similar to the first one.  Sorry for the confusion.

My ethernet is still not working.  Any chance you could continue to help me here since there was no definitive answer as to what fixed his?

> First, I'm not understand why you need PAE kernel while your machine is x86. You have more than 4GB RAM?

I only have 4 gigs of ram.  This was a standard install.  No idea why it would have the PAE kernal (or even what it was until I googled it).

---

### Post by cheezbergher on 2010-10-05
Does your BIOS have an option to enable "LAN Boot ROM"? try turning that on, reboot and shutdown, then unplug the power supply, and then boot it back up. It should work after that, assuming that theres nothing else wrong with your network configuration.

---

