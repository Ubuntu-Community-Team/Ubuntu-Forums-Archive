---
title: "Wifi problem with Dell Inspiron 1520"
date: 2011-01-09
forum: Networking &amp; Wireless
---

### Post by sross01986 on 2011-01-09
To begin I have a Dell Inspiron 1520. I am dual booting Windows 7 and Ubuntu 10.10. My wireless card is built into the computer. The card is an Intel Pro wireless 3945 ABG. Currently wireless is work on Win 7 but not Ubuntu. The other day when I started Ubuntu wifi was working great but now when I right click on the networks icon the "enable wireless" option is listed in dark grey. I cannot add a wireless network manually. So far I have looked up some information from terminal. I am posting it for some more background information. I am very new to Ubuntu and Linux so any help would be great.

srr@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 02
       serial: 00:1b:77:d8:fa:a2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:27 memory:fe8ff000-fe8fffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:a2:a0:1f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=10.0.0.8 latency=64 multicast=yes
       resources: irq:17 memory:fe5fe000-fe5fffff

srr@ubuntu:~$ rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: yes
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by noelvh on 2011-01-09
I bet you have updated your ubuntu system. I have seen a bunch off wifi issues lately with the latest kernel version. Try on boot up to select you older kernel and see if that helps you.

Noel

---

### Post by sross01986 on 2011-01-09
I installed Ubuntu 10.10 yesterday morning. I was working with a Mac4lin appearance package and then later that day I no longer had the option of enabling wireless. How would I be able to go back to the original kernal?

---

### Post by PatchesTheCaveman on 2011-01-09
You can follow the instructions I provided in this post to see if you have the known broken kernel and fix it:
[http://ubuntuforums.org/showpost.php?p=10312711&postcount=5](http://ubuntuforums.org/showpost.php?p=10312711&postcount=5)

---

### Post by sross01986 on 2011-01-09
Unfortunately that did not work I  followed the instructions and got this kernel instead

srr@ubuntu:~$ uname -r
2.6.32-27-generic

---

### Post by PatchesTheCaveman on 2011-01-10
You must be running 10.04 Lucid Lynx (LTS), as only that version has the series of kernel versions.  The broken kernel is only a problem for 10.10 Maverick Meerkat.

Your *rfkill* output indicates your wireless is hard-blocked.  Have you tried flipping your wireless switch?  It might be a physical switch, a discrete button, or a Fn key combination.

---

### Post by BigYellowDog on 2011-01-10
I'm having the same issue I have an Insprion 1464, running kubuntu 10.04 (LTS)

> 
[rob] ~ $ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: c4:17:fe:76:9d:50
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f0400000-f0403fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:26:b9:24:11:28
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.6 latency=0 multicast=yes
       resources: irq:32 ioport:2000(size=256) memory:f0810000-f0810fff(prefetchable) memory:f0800000-f080ffff(prefetchable) memory:f0820000-f083ffff(prefetchable)
[rob] ~ $ 
I get no output from *rfkill list*

---

### Post by PatchesTheCaveman on 2011-01-11
BigYellowDog:  what model laptop do you have?

Also, please copy/paste the output of:
```
lsmod
```

---

### Post by BigYellowDog on 2011-01-11
I have a Dell Inspiron 1464 which is similar to theOP's laptop.  If need be I can start a new thread.

```

Module                  Size  Used by                                                                                                                                                           
ppdev                   6375  0                                                                                                                                                                 
snd_hda_codec_intelhdmi    13090  1                                                                                                                                                             
snd_hda_codec_realtek   279008  1                                                                                                                                                               
snd_hda_intel          25741  2                                                                                                                                                                 
snd_hda_codec          85759  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel                                                                                                     
snd_hwdep               6924  1 snd_hda_codec                                                                                                                                                   
snd_pcm_oss            41394  0                                                                                                                                                                 
snd_mixer_oss          16299  1 snd_pcm_oss                                                                                                                                                     
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss                                                                                                                         
snd_seq_dummy           1782  0                                                                                                                                                                 
snd_seq_oss            31191  0                                                                                                                                                                 
snd_seq_midi            5829  0                                                                                                                                                                 
fbcon                  39270  71 
tileblit                2487  1 fbcon
snd_rawmidi            23420  1 snd_seq_midi
font                    8053  1 fbcon
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
vga16fb                12757  0 
dell_wmi                2177  0 
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
lib80211_crypt_tkip     8676  0 
uvcvideo               62595  0 
videodev               40518  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
psmouse                64576  0 
snd                    71251  17 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8052  1 snd
dell_laptop             7941  0 
vgastate                9857  1 vga16fb
joydev                 11104  0 
wl                   1964968  0 
v4l2_compat_ioctl32    11892  1 videodev
i915                  323510  2 
lib80211                6151  2 lib80211_crypt_tkip,wl
drm_kms_helper         30742  1 i915
drm                   198948  3 i915,drm_kms_helper
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
i2c_algo_bit            6024  1 i915
usbhid                 41116  0 
serio_raw               4918  0 
intel_agp              29319  2 i915
dcdbas                  6886  1 dell_laptop
video                  20623  1 i915
hid                    83472  1 usbhid
output                  2503  1 video
lp                      9336  0 
parport                37160  2 ppdev,lp
r8169                  39714  0 
ahci                   37870  5 
mii                     5237  1 r8169

```

---

### Post by sross01986 on 2011-01-11
BigYellowDog I would appreciate it if you were to make a new thread for your wifi problem. 

PatchestheCaveman I appreciate all of your insight and advice. I have tried my wifi switch it does not work with ubuntu. Here is what I have been doing the last couple of days. I uninstalled 10.04 from my computer, I then reinstalled it. When 10.04 is untouched wifi works and I have no problem with it. I then downloaded an appearance package to change the look of Ubuntu. That is where I went wrong. I restarted the computer to make the installation complete and I lost my ability to enable wifi. just for fun here is some more info.

srr@ubuntu:~$ lshw-C network
lshw-C: command not found
srr@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 02
       serial: 00:1b:77:d8:fa:a2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:28 memory:fe8ff000-fe8fffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:a2:a0:1f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=10.0.0.8 latency=64 multicast=yes
       resources: irq:17 memory:fe5fe000-fe5fffff

srr@ubuntu:~$ rfkill list
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: yes
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
7: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

srr@ubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc             7960  1 
rfcomm                 40393  4 
ppdev                   6375  0 
sco                     9617  2 
bridge                 53184  0 
stp                     2171  1 bridge
bnep                   11884  2 
l2cap                  34806  16 rfcomm,bnep
snd_hda_codec_idt      61450  1 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
joydev                 11072  0 
snd_hda_intel          25677  2 
snd_hda_codec          85759  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87882  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
arc4                    1473  2 
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iwl3945                79436  0 
iwlcore               124955  1 iwl3945
snd                    71106  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dell_wmi                2177  0 
mac80211              238448  2 iwl3945,iwlcore
i915                  321160  3 
drm_kms_helper         30742  1 i915
dell_laptop             7941  0 
dcdbas                  6886  1 dell_laptop
btusb                  12969  2 
bluetooth              58685  9 rfcomm,sco,bnep,l2cap,btusb
ricoh_mmc               3416  0 
sdhci_pci               6700  0 
sdhci                  17928  1 sdhci_pci
led_class               3764  3 iwl3945,iwlcore,sdhci
cfg80211              148546  3 iwl3945,iwlcore,mac80211
psmouse                64576  0 
soundcore               8052  1 snd
serio_raw               4918  0 
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
drm                   199204  4 i915,drm_kms_helper
i2c_algo_bit            6024  1 i915
intel_agp              29095  2 i915
video                  20623  1 i915
output                  2503  1 video
lp                      9336  0 
parport                37160  2 ppdev,lp
ohci1394               30260  0 
ieee1394               94771  1 ohci1394
b44                    30687  0 
ssb                    45092  1 b44
mii                     5237  1 b44
usbhid                 41084  0 
hid                    83440  1 usbhid
srr@ubuntu:~$ 
Any help or advice would be greatly appreciated.

---

### Post by PatchesTheCaveman on 2011-01-12
sross01986:  Please copy/paste the output of:
```
dmesg | grep -i iwl
```

BigYellowDog:  I don't see a wireless driver in there at all.  Not good.  Please run a full suite of diagnostics as instructed in the following post and copy/paste the output into a new thread:
[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by sross01986 on 2011-01-12
Here is the output of the code

srr@MAC OS X:~$ dmesg | grep -i iwl
[   12.947560] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   12.947565] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   12.947702] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.947718] iwl3945 0000:0c:00.0: setting latency timer to 64
[   13.094600] iwl3945 0000:0c:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   13.094606] iwl3945 0000:0c:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   13.094768] iwl3945 0000:0c:00.0: irq 28 for MSI/MSI-X
[   13.154669] phy0: Selected rate control algorithm 'iwl-3945-rs'
[  938.323958] iwl3945 0000:0c:00.0: firmware: requesting iwlwifi-3945-2.ucode
[  938.328064] iwl3945 0000:0c:00.0: loaded firmware version 15.32.2.9
[  938.328277] iwl3945 0000:0c:00.0: Radio disabled by HW RF Kill switch
[  967.901092] iwl3945 0000:0c:00.0: Radio disabled by HW RF Kill switch
[  980.495466] iwl3945 0000:0c:00.0: Radio disabled by HW RF Kill switch
[ 2578.463927] iwl3945 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 2578.463997] iwl3945 0000:0c:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xfe8ff000)
[ 2578.464011] iwl3945 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 2578.464031] iwl3945 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100506)
[ 9686.040200] iwl3945 0000:0c:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x080003C8
[ 9686.040200] iwl3945 0000:0c:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x080003C8
[ 9686.040200] iwl3945 0000:0c:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x080003C8
[ 9686.040200] iwl3945 0000:0c:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x080003C8
[ 9686.040200] iwl3945 0000:0c:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x080003C8
[ 9686.040200] iwl3945 0000:0c:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x080003C8
[ 9686.040200] iwl3945 0000:0c:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x080003C8
[ 9686.040200] iwl3945 0000:0c:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x080003C8
[ 9686.040200] iwl3945 0000:0c:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x080003C8
[ 9686.040200] iwl3945 0000:0c:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x080003C8
[ 9686.272000] iwl3945 0000:0c:00.0: Hardware error detected.  Restarting.
[ 9686.290273] PM: suspend of drv:iwl3945 dev:0000:0c:00.0 complete after 260.040 msecs
[ 9687.003973] iwl3945 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 9687.004044] iwl3945 0000:0c:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xfe8ff000)
[ 9687.004058] iwl3945 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 9687.004078] iwl3945 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100506)

Thanks

---

### Post by Castarmax on 2011-01-12
> **BigYellowDog said:**
> I'm having the same issue I have an Insprion 1464, running kubuntu 10.04 (LTS)

I get no output from *rfkill list*


Couldnt find another thread started. Sorry 

On 10.04 and both 10.10 you need to use the propriety drivers for that card. Broadcom also has them posted on their website.
Try System-Administration-Hardware Drivers

---

### Post by PatchesTheCaveman on 2011-01-12
@Castarmax:  he has an Intel wireless card.  The Broadcom device is his wired Ethernet card, which has open source drivers included in the Linux kernel.

---

### Post by akhilsn on 2011-01-18
This may be because of your wifi card.



u try this out.

take command prompt .type

   sudo rmmod wl

then 

 sudo modprobe wl


your wifi will restart in seconds.. watch out your problem may be solved..:D

else 

see this post[http://akhilsnaik.blogspot.com/2010/12/problem-with-wifi-in-ubuntu.html](http://akhilsnaik.blogspot.com/2010/12/problem-with-wifi-in-ubuntu.html)

---

### Post by sross01986 on 2011-01-18
Well I would like to thank everyone that tried to help with my problem. In the end I stopped using Macbuntu. It was great except that the wifi was turned off when I rebooted the appearance program. When I am running a regular 10.04 LTS on my Dell Inspiron 1520 I have no problems. So it is something with the appearance package and the wifi switch. It was a great experiment that did not yield the best results but I learned a lot.

One more thing, there needs to be better nettiqutte. I have a Dell Inspiron 1520 that is still running a Core Duo processor from almost 3 years ago. I wanted to dual boot Macbuntu and Windows 7. I was very upset when someone with a much newer Dell Inspiron and different components took the thread and used it to their advantage. Now I have people helping with the newer Dell while ignoring my problem. I was very disappointed. I thought forums were for helping people out and communicating good ideas. While some like PatchestheCaveman are willing to help others ruin the idea of forums.

---

