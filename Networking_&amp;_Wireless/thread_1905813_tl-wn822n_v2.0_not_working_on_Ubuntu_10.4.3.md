---
title: "tl-wn822n v2.0 not working on Ubuntu 10.4.3"
date: 2012-01-07
forum: Networking &amp; Wireless
---

### Post by justinwright on 2012-01-07
Hello all, 

I'm new to Ubuntu and just installed 10.4.3 on a custom desktop machine. (Gigabyte a75m-s2v motherboard, amd a6 3650 processor). I haven't done anything since installation except try to get the wireless working.

I chose the lt-wn822n wireless usb adapter because it is supposed to work right out of the box, but it doesn't for me. I can see it in lsusb, but nowhere else. I've tried almost every usb port on the machine, all with the same lack of results. Wired network works fine (but seems a little slow...). Please see data below and thanks in advance for your help! 

```
cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"
Linux FeelGoodInc 2.6.32-37-generic #81-Ubuntu SMP Fri Dec 2 20:32:42 UTC 2011 x86_64 GNU/Linux

lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Kernel driver in use: r8169
    Kernel modules: r8169

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

rfkill list all
#no response!

lsmod
Module                  Size  Used by
nls_utf8                1421  1 
isofs                  33399  1 
binfmt_misc             7960  1 
ppdev                   6375  0 
usbhid                 41116  0 
hid                    83888  1 usbhid
snd_hda_codec_realtek   279104  1 
snd_hda_intel          25805  2 
snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23681  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    71283  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
i2c_piix4               9639  0 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
xhci                   42775  0 
lp                      9336  0 
parport                37160  2 ppdev,lp
ahci                   38350  3 
r8169                  39714  0 
mii                     5237  1 r8169
pata_atiixp             4209  0 

lsusb
Bus 007 Device 002: ID 045e:00d1 Microsoft Corp. Optical Mouse with Tilt Wheel
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0cf3:7015 Atheros Communications, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by justinwright on 2012-01-08
Ok, just found out this wireless adapter works plug-and-play on Ubuntu 11.10. Doesn't really help me though, because I can't get 11.10 to work with my motherboard's onboard graphics (black screen prior to login prompt). 

It's always something...

---

### Post by apflanigan on 2012-02-20
I had the same problem you did with my TL-WN822N V2 adapter.  I also had to keep Ubuntu 10.04 on my laptop because I had sound issues with the later versions.  Here is how I got my adapter to work.
1.  Download the latest driver from the TP-link web site and unzip the contents to a familiar location on your PC.
2.  Make sure the adapter is disconnected from your PC.
3. Use either Ubuntu Software Center or Synaptic Package Manager application to install "Windows Wireless Drivers" program.
4. Open Windows Wireless Drivers program from the System -> Administration pull down menu.  You may need to type in your password to access the program.
5. Click the "Install New Driver" button
6. Select the inf file by selecting the folder icon button and navigating to the familiar location on your PC. The Windows XP 32 bit driver worked on my laptop.
7. There should be a "netathuw" driver listed on the left side of the window.
8. Plug in the adapter and wait for the PC to recognize the hardware.  It took less than a minute for my laptop to recognize the adapter.  If your PC does not see the adapter, try restarting computer.  
9. Close the Windows Wireless Drivers window.

Hope this is useful.

---

### Post by flash63 on 2012-02-21
Hello,
you don't need ndiswrapper

TL-WN822N v1 Atheros AR-9170 ID 0CF3:1002 - modul carl9170
TL-WN822N v2 Atheros HTC ID:0cf3:7015 - modul ath9k_htc 

Driver from [http://www.linuxwireless.org/](http://www.linuxwireless.org/) (prepared older package for Ubuntu 10.04 from my Homepage)

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential 
wget http://elektronenblitz63.de/downloads/compat-wireless-2011-10-29_patched_ubuntu.tar.gz
tar xvf compat-wireless-2011-10-29_patched_ubuntu.tar.gz 
cd compat-wireless-2011-10-29_patched_ubuntu
make
sudo make install  
```

Install the latest firmware package 1.60 from
[http://nl.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.60_all.deb](http://nl.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.60_all.deb)

Finaly load the modul
```
sudo modprobe ath9k_htc
iwconfig
```

References (German)
[http://wiki.ubuntuusers.de/WLAN/Karten/TP-Link](http://wiki.ubuntuusers.de/WLAN/Karten/TP-Link)
[http://forum.ubuntuusers.de/post/2767012/](http://forum.ubuntuusers.de/post/2767012/)

---

### Post by salinmooch on 2012-05-02
Flash63 instructions worked perfectly!  Thanks!

I had to reboot to get the firmware recognised but it seems to work fine after that.  Should hold me over till I upgrade from 10.04 to 12.04  when I get the chance.

Cheers!

---

### Post by digiPixel on 2012-06-21
By all means you should. Since you are used to using LTS releases if I were you I would stick to those releases for stability/reliability reasons.

Only go for an unstable release (non LTS) if a particular piece of hardware isn't already supported in the latest LTS release.

---

### Post by justinwright on 2012-12-01
Thanks for the help, everyone. These methods seemed to work. Also, the tl-wn822n "just works" on 12.04, so I'm good to go. SOLVED!

---

