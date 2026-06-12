---
title: "ASUS Laptop. Can not detect or connect to the wireless network"
date: 2010-03-29
forum: Networking &amp; Wireless
---

### Post by badRobat on 2010-03-29
Hello!
 
 
I have ASUS Laptop A6Rseries was running XP untill I installed Linux 9.10. Now i am having problem connecting to my wireless network. I am using Belkin router what works fine with XP, Vista and Windovs 7. Here is some information what I found
 
 
lspci 
00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01) 
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge 
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) 
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) 
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) 
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82) 
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80) 
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01) 
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80) 
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) 
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M] 
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 
02:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3) 
02:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17) 
02:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08) 
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) 
 
 
ifconfig 
eth0 Link encap:Ethernet HWaddr 00:18:f3:38:dc:af 
UP BROADCAST MULTICAST MTU:1500 Metric:1 
RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B) 
Interrupt:20 Base address:0xb800 
 
 
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0 
inet6 addr: ::1/128 Scope:Host 
UP LOOPBACK RUNNING MTU:16436 Metric:1 
RX packets:4 errors:0 dropped:0 overruns:0 frame:0 
TX packets:4 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:0 
RX bytes:240 (240.0 B) TX bytes:240 (240.0 B)
 
 
iwconfig 
lo no wireless extensions. 
 
 
eth0 no wireless extensions. 
 
 
lsmod 
Module Size Used by 
nls_iso8859_1 3740 0 
nls_cp437 5372 0 
vfat 10716 0 
fat 51452 1 vfat 
usb_storage 52544 0 
isofs 31620 1 
udf 80900 0 
crc_itu_t 1852 1 udf 
binfmt_misc 8356 1 
snd_atiixp_modem 11940 0 
snd_via82xx_modem 11204 0 
snd_intel8x0m 13896 0 
snd_hda_codec_si3054 4636 1 
snd_hda_codec_realtek 203328 1 
snd_hda_intel 26920 2 
snd_hda_codec 75708 3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel 
snd_ac97_codec 101216 3 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m 
ac97_bus 1532 1 snd_ac97_codec 
snd_hwdep 7200 1 snd_hda_codec 
snd_pcm_oss 37920 0 
snd_mixer_oss 16028 1 snd_pcm_oss 
snd_pcm 75296 8 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_ac97_codec,snd_pcm_oss 
snd_seq_dummy 2656 0 
snd_seq_oss 28576 0 
snd_seq_midi 6432 0 
snd_rawmidi 22208 1 snd_seq_midi 
snd_seq_midi_event 6940 2 snd_seq_oss,snd_seq_midi 
pcmcia 36808 0 
sdhci_pci 7100 0 
sdhci 17472 1 sdhci_pci 
snd_seq 50224 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
asus_laptop 17400 0 
yenta_socket 24200 1 
rsrc_nonstatic 11644 1 yenta_socket 
joydev 10272 0 
snd_timer 22276 2 snd_pcm,snd_seq 
pcmcia_core 35792 3 pcmcia,yenta_socket,rsrc_nonstatic 
lp 8964 0 
ppdev 6688 0 
parport_pc 31940 1 
parport 35340 3 lp,ppdev,parport_pc 
led_class 4096 2 sdhci,asus_laptop 
stkwebcam 20928 0 
snd_seq_device 6920 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
shpchp 32272 0 
videodev 36736 1 stkwebcam 
psmouse 56180 0 
v4l1_compat 14496 1 videodev 
serio_raw 5280 0 
snd 59204 21 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_ac97_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
i2c_piix4 9932 0 
iptable_filter 3100 0 
soundcore 7264 1 snd 
snd_page_alloc 9156 5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_hda_intel,snd_pcm 
ip_tables 11692 1 iptable_filter 
x_tables 16544 1 ip_tables 
8139too 22620 0 
8139cp 19260 0 
mii 5212 2 8139too,8139cp 
radeon 636000 2 
ttm 36212 1 radeon 
drm 159584 4 radeon,ttm 
i2c_algo_bit 5760 1 radeon 
video 19380 0 
output 2780 1 video 
ati_agp 6760 0 
agpgart 34988 3 ttm,drm,ati_agp 
 
 
sudo lshv -C network 
sudo: lshv: command not found 
 
 
iwlist scan 
lo Interface doesn't support scanning. 
 
 
eth0 Interface doesn
 
 
lsb_release -d 
Description: Ubuntu 9.10 
 
 
uname -mr 
2.6.31-14-generic i686 
 
 
sudo /etc/init.d/networking restart 
* Reconfiguring network interfaces... 
 
 
here i am having a problem! I am new with Linux so i dont know much about it but I do know when it is hard to connect to the wireless network! Could anyboday help me and explain how to fix it and connect to the wireless network? Thank you!

---

### Post by bkratz on 2010-03-29
See this page

[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)

pay particular attention to the section labeled Ubuntu/Debian

---

### Post by badRobat on 2010-03-30
I typed in 
 
sudo apt-get install b43-fwcutter
 
Reading package lists... Done 
Building dependency tree 
Reading state information... Done 
b43-fwcutter is already the newest version. 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
1 not fully installed or removed. 
After this operation, 0B of additional disk space will be used. 
Setting up b43-fwcutter (1:012-1) ... 
--2007-01-23 15:53:47-- [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o) 
Resolving downloads.openwrt.org... failed: Name or service not known. 
wget: unable to resolve host address `downloads.openwrt.org' 
dpkg: error processing b43-fwcutter (--configure): 
subprocess installed post-installation script returned error exit status 1 
Errors were encountered while processing: 
b43-fwcutter 
E: Sub-process /usr/bin/dpkg returned an error code (1) 
 
I did got this download from [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o) on my XP. When i copy to Linux I can't run it. When I try to run it it says Could not display "/media/name/wl_apsta3.130.20.0.o".

---

