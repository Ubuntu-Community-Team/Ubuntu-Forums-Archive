---
title: "LENOVO 3000 G410: Couldn't connet to wireless network (Ubuntu 12.04 LTS)"
date: 2013-04-02
forum: Networking &amp; Wireless
---

### Post by servnsps on 2013-04-02
Hi... im new to ubuntu. i have installed Ubuntu 12.04LTS in my 16GB pendrive and it worked.  But then i had some problems in detecting the wireless network. After  searching through several post regarding wireless networks i couldn't  get a solution. Atlast Mr.Chili555 helped and solved this. Now that my  laptop is detecting wirless network i couldn't connect to the  wireless network. It keeps on asking for authentication again and again.  When checked with my collegues laptop HP/compaq (windows XP) who is using wireless internet from the same network i found  out that the wireless authentication is as mentioned below. Since this  is a office network i can't make changes in router... pls suggest wat  should i do to connect to internet???
Im able to connect to internet using wired connection.

My Laptop Model: LENOVO 3000 G410

These are the commands i used to correct the problem "not detecting the wireless connection"

>  

sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree

Detach the ethernet and reboot. 

the Windows wireless connection properties are as below

Network authentication: WPA-PSK

Data Encryption: TKIP

Below are the output of certain commands

>  paul@renato-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:38:a2:86:f0  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fea2:86f0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3858 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3499 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4147184 (4.1 MB)  TX bytes:579064 (579.0 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:312 errors:0 dropped:0 overruns:0 frame:0
          TX packets:312 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27300 (27.3 KB)  TX bytes:27300 (27.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:00:19:9c:7e  
          inet6 addr: fe80::221:ff:fe19:9c7e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:226 (226.0 B)  TX bytes:310 (310.0 B)

paul@renato-laptop:~$ iwconfig
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

eth0      no wireless extensions.

paul@renato-laptop:~$ lsmod
Module                  Size  Used by
btusb                  17952  0 
rfcomm                 38104  0 
bnep                   17791  2 
bluetooth             189585  14 btusb,rfcomm,bnep
joydev                 17394  0 
parport_pc             32115  0 
ppdev                  12850  0 
snd_hda_codec_si3054    12865  1 
snd_hda_codec_realtek    64959  1 
arc4                   12474  2 
snd_hda_intel          32983  3 
b43                   351542  0 
snd_hda_codec         116477  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13277  1 snd_hda_codec
snd_pcm                81124  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
coretemp               13362  0 
snd_rawmidi            25426  1 snd_seq_midi
mac80211              475546  1 b43
snd_seq_midi_event     14476  1 snd_seq_midi
i915                  474913  3 
snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              181041  2 b43,mac80211
snd                    62675  16 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         47459  1 i915
drm                   240232  4 i915,drm_kms_helper
psmouse                91022  0 
bcma                   34573  1 b43
soundcore              14636  1 snd
ssb_hcd                12782  0 
snd_page_alloc         14109  2 snd_hda_intel,snd_pcm
microcode              18396  0 
serio_raw              13032  0 
ideapad_laptop         17891  0 
wmi                    18745  0 
sparse_keymap          13659  1 ideapad_laptop
lpc_ich                16993  0 
i2c_algo_bit           13317  1 i915
mac_hid                13078  0 
video                  19117  1 i915
lp                     17456  0 
parport                40931  3 parport_pc,ppdev,lp
hid_generic            12485  0 
usbhid                 46054  0 
hid                    82511  2 hid_generic,usbhid
ums_realtek            17929  0 
usb_storage            39757  3 ums_realtek
tg3                   141761  0 
ssb                    50757  2 b43,ssb_hcd
paul@renato-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 03)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [IDE mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
06:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
paul@renato-laptop:~$ 

  

Hope this will be helpful to you all... thanks.... :) !!

---

### Post by chili555 on 2013-04-02
Let's try a driver parameter:```
gksudo gedit /etc/modprobe.d/b43.conf
```A new empty file will open.Add a single line:```
options b43 hwtkip=1 
```Proofread carefully, save and close gedit. Detach the ethernet, reboot and let us hear your report.

---

### Post by servnsps on 2013-04-03
Hi... thanks a lot. Actually i must say sorry beause the network guy changed the wireless password and through some best sources i found out the new password. Its working perfectly and i can use the internet. Thanks a lot once again.

pls tell me whether i should be careful while doing regular updates through update manager... due to which my current working configuration might get lost ??

What i shouldn't do... cause im using this only for mails & chatting.

Thanks !!

---

### Post by servnsps on 2013-04-03
Sorry i forgot to mention this....  i did not do the steps in this thread !! It was already working the first time after you told me set those settings. 

Thanks ....!!

---

### Post by chili555 on 2013-04-03
> pls tell me whether i should be careful while doing regular updates through update manager...Not at all. The driver b43 is present in the linux-image by default and will be updated in correctly. The needed firmware probably will never change. You are safe!

I'm glad it's working by whatever means. Have fun!

---

### Post by servnsps on 2013-04-04
Thanks.... :)!!

---

