---
title: "No sound card found (Ubuntu 10.04 )"
date: 2012-06-18
forum: Multimedia Software
---

### Post by harshal22 on 2012-06-18
Hi ,

I am new to linux. I have installed Ubuntu 10.04 on my sony vaio laptop.
First problem I faced is of screen resolution . That is fixed with installation of latest stable nVidia driver that I downloaded from nVidia website. (No proprietary drivers are in use this system)

After that I found that sound is not coming. In sound menu input tab is disable. Output  tab is showing dummy output. There is no hardware listed under hardware tab.

With some search on this forum I ran this

harshal@ubuntu:~$ aplay -l
aplay: device_list:223: no soundcards found...

harshal@ubuntu:~$ cd /proc/asound
bash: cd: /proc/asound: No such file or directory

harshal@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Device 0104 (rev 09)
00:01.0 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 04)
**00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 04)**
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b4)
00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b4)
00:1c.5 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 6 (rev b4)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Device 1c49 (rev 04)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation Device 1055 (rev a1)
**01:00.1 Audio device: nVidia Corporation Device 0e08 (rev a1)**
07:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
0d:00.0 Class ff00: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)
13:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

I have installed alsa and pulseaudio both .

Note : I have installed ubuntu under windows .Does it causing this problem???

---

