---
title: "no wireless network"
date: 2012-09-26
forum: Networking &amp; Wireless
---

### Post by shoaibm65 on 2012-09-26
until yesterday my wired network was working, but not the wireless network. I followed bunch of instructions from this forum because my problems seem the same. Now I do not even have wired network. I am using a no-name self configured desktop running ubuntu 12.04 64 bit.

results of the query commands as follows:


shoaib@shoaib-pc:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
Linux shoaib-pc 3.2.0-31-generic #50-Ubuntu SMP Fri Sep 7 16:16:45 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
shoaib@shoaib-pc:~$ lspci -nnk | grep -ia2 net
	Subsystem: HaSoTec GmbH Device [0e55:2928]
	Kernel driver in use: ehci_hcd
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 01)
	Subsystem: Biostar Microtech Int'l Corp Device [1565:2305]
	Kernel driver in use: r8169
shoaib@shoaib-pc:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 13b1:003a Linksys AE2500 802.11abgn Wireless Adapter [Broadcom BCM43236]
Bus 004 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
shoaib@shoaib-pc:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

shoaib@shoaib-pc:~$ rfkill list all
shoaib@shoaib-pc:~$ lsmod
Module                  Size  Used by
nls_utf8               12557  1
isofs                  40257  1
vesafb                 13844  1
snd_hda_codec_realtek   224173  1
rfcomm                 47604  0
bnep                   18281  2
bluetooth             180104  10 rfcomm,bnep
joydev                 17693  0
usbhid                 47199  0
hid                    99559  1 usbhid
nvidia               8107594  34
snd_hda_intel          33773  3
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
ppdev                  17113  0
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0
snd_rawmidi            30748  1 snd_seq_midi
wmi                    19256  0
parport_pc             32866  1
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13253  0
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_nforce2            13058  0
serio_raw              13211  0
lp                     17799  0
parport                46562  3 ppdev,parport_pc,lp
r8169                  62099  0
floppy                 70365  0
pata_amd               14118  1
shoaib@shoaib-pc:~$

any help please

---

### Post by shoaibm65 on 2012-09-26
I just followed some instructions to start my network, and it got the wired network started, but not the wireless. And when I reboot the system, the wired network is gone again.

I need help please

---

### Post by shoaibm65 on 2012-09-26
So, I finally got the wired network starting at the boot by changing the interface file. I remembered deleting the word inet in the second line after seeing it in some instructions. I started having the problem right after I changed it. I originally changed it to, which I should not have:

auto lo
iface lo loopback

The correct way is:
auto lo
iface lo inet loopback

Now that my ethernet(wired) network is working again, I need to fix the wireless network. Somebody, please help.

---

### Post by shoaibm65 on 2012-09-26
please someone, I need some help

---

