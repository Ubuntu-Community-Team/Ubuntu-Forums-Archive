---
title: "Wicd - No wireless networks found"
date: 2011-08-08
forum: Networking &amp; Wireless
---

### Post by Nazaf on 2011-08-08
Hello,
I am getting "No wireless networks found" using Wicd manager. Below is some info that might help:

**iwconfig**
```

 root@root:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

```**ifconfig-a**
```
eth0      Link encap:Ethernet  HWaddr 00:0b:db:72:0e:2a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:211 errors:0 dropped:0 overruns:0 frame:0
          TX packets:211 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28125 (28.1 KB)  TX bytes:28125 (28.1 KB)

wlan0     Link encap:Ethernet  HWaddr f0:7d:68:fb:d7:fa  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```**lspci**
```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:0a.0 Network controller: RaLink Device 3060
01:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
```

Thanks!!

---

### Post by wildmanne39 on 2011-08-08
Hi, run these commands please:
```
sudo lshw -C network
```
```
lspci -nn | grep 0280
```
```
rfkill list all
```
```
lsmod
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by lkjoel on 2011-08-09
You need a driver for that.

Download the attachment into your home directory, open up a Terminal window, and type in it:
```
cd ~
mv DPO_DRIVER.tar.gz DPO_DRIVER.tar.lzma
tar -xf DPO_DRIVER.tar.gz
cd DPO_*
sudo make
sudo make install

```Reboot and see if you can connect.

---

### Post by Nazaf on 2011-08-09
> **wildmanne39 said:**
> Hi, run these commands please:
```
sudo lshw -C network
``````
lspci -nn | grep 0280
``````
rfkill list all
``````
lsmod
```and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

Here it is:

```

root@root:~# sudo lshw -C network
  *-network:0             
       description: Wireless interface
       product: RaLink
       vendor: RaLink
       physical id: a
       bus info: pci@0000:01:0a.0
       logical name: wlan0
       version: 00
       serial: f0:7d:68:fb:d7:fa
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.38 firmware=0.34 latency=64 link=no maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:fead0000-feadffff
  *-network:1
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: c
       bus info: pci@0000:01:0c.0
       logical name: eth0
       version: 02
       serial: 00:0b:db:72:0e:2a
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI firmware=N/A latency=64 link=no mingnt=255 multicast=yes port=twisted pair
       resources: irq:18 memory:feae0000-feafffff ioport:df40(size=64)
root@root:~# lspci -nn | grep 0280
01:0a.0 Network controller [0280]: RaLink Device [1814:3060]
root@root:~# rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
root@root:~# lsmod
Module                  Size  Used by
dm_crypt               14560  0 
snd_intel8x0           25295  0 
snd_ac97_codec        101425  1 snd_intel8x0
ac97_bus                 982  1 snd_ac97_codec
snd_pcm_oss            36427  0 
snd_mixer_oss          13581  1 snd_pcm_oss
snd_pcm                68875  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1358  0 
arc4                    1141  2 
snd_seq_oss            26216  0 
snd_seq_midi            4460  0 
rt2800pci               7938  0 
snd_rawmidi            18745  1 snd_seq_midi
rt2800lib              33048  1 rt2800pci
crc_ccitt               1281  1 rt2800lib
rt2x00pci               5178  1 rt2800pci
rt2x00lib              33002  3 rt2800pci,rt2800lib,rt2x00pci
snd_seq_midi_event      5720  2 snd_seq_oss,snd_seq_midi
mac80211              248838  3 rt2800lib,rt2x00pci,rt2x00lib
snd_seq                45875  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              17835  2 snd_pcm,snd_seq
snd_seq_device          5281  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              152934  2 rt2x00lib,mac80211
gspca_stv06xx          23600  0 
ppdev                   5096  0 
snd                    50345  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
gspca_main             22422  1 gspca_stv06xx
dcdbas                  5557  0 
rfkill                 14987  1 cfg80211
eeprom_93cx6            1292  1 rt2800pci
videodev               64006  1 gspca_main
soundcore               6016  1 snd
parport_pc             26079  1 
shpchp                 24986  0 
snd_page_alloc          6769  2 snd_intel8x0,snd_pcm
mac_hid                 3029  0 
lp                      7373  0 
parport                29468  3 ppdev,parport_pc,lp
squashfs               24620  1 
aufs                  151288  2867 
nls_iso8859_1           3301  1 
nls_cp437               4971  1 
vfat                    8810  1 
fat                    49021  1 vfat
i915                  458129  2 
drm_kms_helper         30726  1 i915
drm                   171919  3 i915,drm_kms_helper
usbhid                 35213  0 
intel_agp               9614  1 i915
hid                    67599  1 usbhid
usb_storage            40486  1 
i2c_algo_bit            4852  1 i915
e1000                  96161  0 
uas                     7524  0 
intel_gtt              13296  3 i915,intel_agp
video                  10930  1 i915
agpgart                27382  3 drm,intel_agp,intel_gtt
root@root:~# 



```

---

### Post by wildmanne39 on 2011-08-09
Hi, lkjoel is correct you need the driver he gave you in his post.

If you need more directions you can use this link post #20 tells you step by step how to do it.
[http://ubuntuforums.org/showthread.php?t=1780136&highlight=1814%3A3060](http://ubuntuforums.org/showthread.php?t=1780136&highlight=1814%3A3060)

I just compiled that driver yesterday to help someone so the directions are correct.
Thank you

---

### Post by Nazaf on 2011-08-09
> **lkjoel said:**
> You need a driver for that.

Download the attachment into your home directory, open up a Terminal window, and type in it:
```
cd ~
mv DPO_DRIVER.tar.gz DPO_DRIVER.tar.lzma
tar -xf DPO_DRIVER.tar.gz
cd DPO_*
sudo make
sudo make install

```Reboot and see if you can connect.

When I type tar -xf DPO_DRIVER.tar.gz I get an error:
tar: DPO_DRIVER.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

---

### Post by Nazaf on 2011-08-09
I installed the driver. However, it's not working.

By the way, I am using a Live USB drive.

---

### Post by lkjoel on 2011-08-09
Could you give me the output of the commands?

---

### Post by Nazaf on 2011-08-09
```

root@root:~# sudo lshw -C network
  *-network:0             
       description: Wireless interface
       product: RaLink
       vendor: RaLink
       physical id: a
       bus info: pci@0000:01:0a.0
       logical name: wlan0
       version: 00
       serial: f0:7d:68:fb:d7:fa
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.38 firmware=0.34 latency=64 link=no maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:fead0000-feadffff
  *-network:1
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: c
       bus info: pci@0000:01:0c.0
       logical name: eth0
       version: 02
       serial: 00:0b:db:72:0e:2a
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI firmware=N/A latency=64 link=no mingnt=255 multicast=yes port=twisted pair
       resources: irq:18 memory:feae0000-feafffff ioport:df40(size=64)
root@root:~# lspci -nn | grep 0280
01:0a.0 Network controller [0280]: RaLink Device [1814:3060]
root@root:~# rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
root@root:~# lsmod
Module                  Size  Used by
dm_crypt               14560  0 
snd_intel8x0           25295  0 
snd_ac97_codec        101425  1 snd_intel8x0
ac97_bus                 982  1 snd_ac97_codec
snd_pcm_oss            36427  0 
snd_mixer_oss          13581  1 snd_pcm_oss
snd_pcm                68875  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1358  0 
arc4                    1141  2 
snd_seq_oss            26216  0 
rt2800pci               7938  0 
snd_seq_midi            4460  0 
rt2800lib              33048  1 rt2800pci
snd_rawmidi            18745  1 snd_seq_midi
crc_ccitt               1281  1 rt2800lib
rt2x00pci               5178  1 rt2800pci
rt2x00lib              33002  3 rt2800pci,rt2800lib,rt2x00pci
snd_seq_midi_event      5720  2 snd_seq_oss,snd_seq_midi
snd_seq                45875  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
mac80211              248838  3 rt2800lib,rt2x00pci,rt2x00lib
snd_timer              17835  2 snd_pcm,snd_seq
snd_seq_device          5281  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              152934  2 rt2x00lib,mac80211
ppdev                   5096  0 
snd                    50345  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
gspca_stv06xx          23600  0 
gspca_main             22422  1 gspca_stv06xx
rfkill                 14987  1 cfg80211
dcdbas                  5557  0 
eeprom_93cx6            1292  1 rt2800pci
soundcore               6016  1 snd
videodev               64006  1 gspca_main
parport_pc             26079  1 
shpchp                 24986  0 
snd_page_alloc          6769  2 snd_intel8x0,snd_pcm
mac_hid                 3029  0 
lp                      7373  0 
parport                29468  3 ppdev,parport_pc,lp
squashfs               24620  1 
aufs                  151288  2866 
nls_iso8859_1           3301  1 
nls_cp437               4971  1 
vfat                    8810  1 
fat                    49021  1 vfat
i915                  458129  2 
drm_kms_helper         30726  1 i915
drm                   171919  3 i915,drm_kms_helper
usbhid                 35213  0 
usb_storage            40486  1 
intel_agp               9614  1 i915
hid                    67599  1 usbhid
i2c_algo_bit            4852  1 i915
e1000                  96161  0 
intel_gtt              13296  3 i915,intel_agp
uas                     7524  0 
video                  10930  1 i915
agpgart                27382  3 drm,intel_agp,intel_gtt



```

---

### Post by lkjoel on 2011-08-09
Sorry, I mean the output of the commands you used to install the driver.

---

### Post by Nazaf on 2011-08-09
> **lkjoel said:**
> Sorry, I mean the output of the commands you used to install the driver.

* I extracted the file as a folder to the Desktop since the commands didn't work for me.

```

root@root:~/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217# sudo make
make -C tools
make[1]: Entering directory `/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools/bin2h
cp -f os/linux/Makefile.6 /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/Makefile
make -C /lib/modules/2.6.38/build SUBDIRS=/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux modules
make[1]: Entering directory `/usr/src/linux-source-2.6.38'

  WARNING: Symbol version dump /usr/src/linux-source-2.6.38/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_md5.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_sha2.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_hmac.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_aes.o
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_aes.c: In function ‘AES_GTK_KEY_WRAP’:
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_aes.c:2265: warning: the frame size of 1096 bytes is larger than 1024 bytes
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_aes.c: In function ‘WscDecryptData’:
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_aes.c:1592: warning: the frame size of 1372 bytes is larger than 1024 bytes
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_aes.c: In function ‘WscEncryptData’:
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_aes.c:1522: warning: the frame size of 1372 bytes is larger than 1024 bytes
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_arc4.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/mlme.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_wep.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/action.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_data.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rtmp_init.o
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rtmp_init.c: In function ‘NICInitAsicFromEEPROM’:
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rtmp_init.c:1391: warning: format ‘%x’ expects type ‘unsigned int’, but argument 3 has type ‘ULONG’
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_tkip.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_aes.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_sync.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/eeprom.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_sanity.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_info.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_cfg.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_wpa.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/dfs.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/spectrum.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rtmp_timer.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rt_channel.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_profile.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_asic.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_cmd.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/assoc.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/auth.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/auth_rsp.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/sync.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/sanity.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/rtmp_data.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/connect.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/wpa.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/ags.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../sta/sta_cfg.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_profile.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/sta_ioctl.o
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_iwaplist’:
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/sta_ioctl.c:596: warning: the frame size of 1288 bytes is larger than 1024 bytes
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlE2PROM’:
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/sta_ioctl.c:6043: warning: the frame size of 1352 bytes is larger than 1024 bytes
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlMAC’:
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/sta_ioctl.c:5844: warning: the frame size of 1360 bytes is larger than 1024 bytes
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_linux.o
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevDetach’:
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_linux.c:1699: warning: initialization discards qualifiers from pointer target type
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_linux.c:1736: warning: initialization discards qualifiers from pointer target type
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_main_dev.o
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_main_dev.c: In function ‘MainVirtualIF_close’:
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_main_dev.c:118: warning: unused variable ‘Cancelled’
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_main_dev.c: In function ‘WriteDatThread’:
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_main_dev.c:1250: warning: ‘return’ with no value, in function returning non-void
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/ba_action.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.o
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c: In function ‘RTMPResetTxRxRingMemory’:
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:36: warning: unused variable ‘num’
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c: In function ‘RTMPFreeTxRxRingMemory’:
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:119: warning: unused variable ‘IrqFlags’
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:118: warning: unused variable ‘pPacket’
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:117: warning: unused variable ‘pTxD’
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:116: warning: unused variable ‘pTxRing’
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:115: warning: unused variable ‘j’
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:115: warning: unused variable ‘index’
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c: In function ‘RTMPAllocTxRxRingMemory’:
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:447: warning: unused variable ‘BufBaseVa’
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:446: warning: unused variable ‘BufBasePaLow’
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:445: warning: unused variable ‘BufBasePaHigh’
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:432: warning: unused variable ‘pPacket’
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:431: warning: unused variable ‘pDmaBuf’
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:430: warning: unused variable ‘pTxRing’
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:428: warning: unused variable ‘pRxD’
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:427: warning: unused variable ‘pTxD’
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:425: warning: unused variable ‘RingBaseVa’
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:424: warning: unused variable ‘RingBasePaLow’
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:423: warning: unused variable ‘RingBasePaHigh’
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_mac_pci.c:489: warning: ‘index’ may be used uninitialized in this function
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_data_pci.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rtmp_mcu.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/ee_prom.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/ee_efuse.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rt_rf.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../chips/rt30xx.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../chips/rt35xx.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_pci_rbus.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/rt_rbus_pci_util.o
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/pci_main_dev.o
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/pci_main_dev.c: In function ‘rt2860_probe’:
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../os/linux/pci_main_dev.c:320: warning: assignment discards qualifiers from pointer target type
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/misc.o
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/misc.c: In function ‘RTMPHwCoexSwitch’:
/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/misc.c:963: warning: format ‘%x’ expects type ‘unsigned int’, but argument 6 has type ‘ULONG’
  CC [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../chips/rt3592cb.o
  LD [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/rt3562sta.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/rt3562sta.o
see include/linux/module.h for more information
  CC      /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/rt3562sta.mod.o
  LD [M]  /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/rt3562sta.ko
make[1]: Leaving directory `/usr/src/linux-source-2.6.38'
cp -f /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/rt3562sta.ko /tftpboot
root@root:~/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217# sudo make install
make -C /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux -f Makefile.6 install
make[1]: Entering directory `/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/2.6.38/kernel/drivers/net/wireless/
install -m 644 -c rt3562sta.ko /lib/modules/2.6.38/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.38
make[1]: Leaving directory `/root/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux'




```

---

### Post by lkjoel on 2011-08-10
Did you reboot?

---

### Post by Nazaf on 2011-08-10
> **lkjoel said:**
> Did you reboot?

Yes, I did and many times.

---

### Post by lkjoel on 2011-08-10
Could you give me the output of these Terminal commands?
```
uname -a
lsb_release -a

```

---

### Post by Nazaf on 2011-08-10
```


**root@root:~# uname -a**
Linux root 2.6.38 #1 SMP Thu Mar 17 20:52:18 EDT 2011 i686 GNU/Linux
[B]
root@root:~# lsb_release -a[/B]
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.2 LTS
Release:    10.04
Codename:    lucid
root@root:~# 




```

---

### Post by lkjoel on 2011-08-10
Try this:
```
sudo apt-get install aptitude
sudo aptitude update
sudo aptitude full-upgrade

```
Reboot, reinstall the driver, and reboot again.

---

### Post by Nazaf on 2011-08-11
```

root@root:~# sudo apt-get install aptitude
Reading package lists... Done
Building dependency tree       
Reading state information... Done
aptitude is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@root:~# sudo aptitude update
Writing extended state information... Done
Err http://source.repository.backtrack-linux.org revolution Release.gpg
  Could not resolve 'source.repository.backtrack-linux.org'
Err http://32.repository.backtrack-linux.org revolution Release.gpg             
  Could not resolve '32.repository.backtrack-linux.org'
Err http://source.repository.backtrack-linux.org/ revolution/main Translation-en_US
  Could not resolve 'source.repository.backtrack-linux.org'
Err http://source.repository.backtrack-linux.org/ revolution/microverse Translation-en_US
  Could not resolve 'source.repository.backtrack-linux.org'
Err http://32.repository.backtrack-linux.org/ revolution/main Translation-en_US 
  Could not resolve '32.repository.backtrack-linux.org'
Err http://source.repository.backtrack-linux.org/ revolution/non-free Translation-en_US
  Could not resolve 'source.repository.backtrack-linux.org'
Err http://source.repository.backtrack-linux.org/ revolution/testing Translation-en_US
  Could not resolve 'source.repository.backtrack-linux.org'
Err http://32.repository.backtrack-linux.org/ revolution/microverse Translation-en_US
  Could not resolve '32.repository.backtrack-linux.org'
Err http://32.repository.backtrack-linux.org/ revolution/non-free Translation-en_US
  Could not resolve '32.repository.backtrack-linux.org'
Err http://32.repository.backtrack-linux.org/ revolution/testing Translation-en_US
  Could not resolve '32.repository.backtrack-linux.org'
Err http://all.repository.backtrack-linux.org revolution Release.gpg
  Could not resolve 'all.repository.backtrack-linux.org'
Err http://all.repository.backtrack-linux.org/ revolution/main Translation-en_US
  Could not resolve 'all.repository.backtrack-linux.org'
Err http://all.repository.backtrack-linux.org/ revolution/microverse Translation-en_US
  Could not resolve 'all.repository.backtrack-linux.org'
Err http://all.repository.backtrack-linux.org/ revolution/non-free Translation-en_US
  Could not resolve 'all.repository.backtrack-linux.org'
Err http://all.repository.backtrack-linux.org/ revolution/testing Translation-en_US
  Could not resolve 'all.repository.backtrack-linux.org'
Reading package lists... Done             

root@root:~# sudo aptitude full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done



```

---

### Post by lkjoel on 2011-08-11
Can you connect to wired networks?

---

### Post by Nazaf on 2011-08-11
> **lkjoel said:**
> Can you connect to wired networks?

No, but I can download files from another PC.

---

### Post by lkjoel on 2011-08-11
Download this file: [http://dl.dropbox.com/u/21016209/wireless/aptitude](http://dl.dropbox.com/u/21016209/wireless/aptitude)
Transfer it to the other PC's home directory, and type in a Terminal window:
```
cd ~
chmod +x aptitude
./aptitude

```

---

### Post by Nazaf on 2011-08-11
It's not working. Now I get this error message "Could not connect to wicd's D-Bus interface. Check the wicd log for error messages."

**Here is the output:**
```

root@root:~# cd ~
root@root:~# chmod +x aptitude
root@root:~# /aptitude
bash: /aptitude: No such file or directory
root@root:~# ./aptitude
Verifying archive integrity... All good.
Uncompressing aptitude......................................
(Reading database ... 212476 files and directories currently installed.)
Preparing to replace debconf 1.5.28ubuntu4 (using .../debconf_1.5.36ubuntu4_i386.deb) ...
Unpacking replacement debconf ...
Selecting previously deselected package debconf-english.
dpkg: regarding .../debconf-english_1.5.36ubuntu4_all.deb containing debconf-english:
 debconf-english conflicts with debconf-i18n
  debconf-i18n (version 1.5.28ubuntu4) is present and installed.
dpkg: error processing packages/debconf-english_1.5.36ubuntu4_all.deb (--install):
 conflicting packages - not installing debconf-english
Preparing to replace debconf-i18n 1.5.28ubuntu4 (using .../debconf-i18n_1.5.36ubuntu4_all.deb) ...
Unpacking replacement debconf-i18n ...
Preparing to replace debianutils 3.2.2 (using .../debianutils_3.4.3ubuntu1_i386.deb) ...
Unpacking replacement debianutils ...
Selecting previously deselected package gcc-4.5-base.
Unpacking gcc-4.5-base (from .../gcc-4.5-base_4.5.2-8ubuntu4_i386.deb) ...
dpkg: regarding .../libattr1_1%3a2.4.44-2ubuntu3_i386.deb containing libattr1, pre-dependency problem:
 libattr1 pre-depends on multiarch-support
  multiarch-support is not installed.
dpkg: error processing packages/libattr1_1%3a2.4.44-2ubuntu3_i386.deb (--install):
 pre-dependency problem - not installing libattr1
Selecting previously deselected package libboost-iostreams1.42.0.
Unpacking libboost-iostreams1.42.0 (from .../libboost-iostreams1.42.0_1.42.0-4ubuntu2_i386.deb) ...
Preparing to replace libbz2-1.0 1.0.5-4ubuntu0.1 (using .../libbz2-1.0_1.0.5-6ubuntu1_i386.deb) ...
Unpacking replacement libbz2-1.0 ...
dpkg: regarding .../libc6_2.13-0ubuntu13_i386.deb containing libc6:
 libc6 conflicts with libc6-i686
  libc6-i686 (version 2.11.1-0ubuntu7.8) is present and installed.
dpkg: error processing packages/libc6_2.13-0ubuntu13_i386.deb (--install):
 conflicting packages - not installing libc6
Preparing to replace libc-bin 2.11.1-0ubuntu7.8 (using .../libc-bin_2.13-0ubuntu13_i386.deb) ...
Unpacking replacement libc-bin ...
Preparing to replace libcwidget3 0.5.13-1ubuntu1 (using .../libcwidget3_0.5.16-3ubuntu2_i386.deb) ...
Unpacking replacement libcwidget3 ...
Selecting previously deselected package libept1.
Unpacking libept1 (from .../libept1_1.0.4_i386.deb) ...
dpkg: regarding .../libgcc1_1%3a4.5.2-8ubuntu4_i386.deb containing libgcc1, pre-dependency problem:
 libgcc1 pre-depends on multiarch-support
  multiarch-support is not installed.
dpkg: error processing packages/libgcc1_1%3a4.5.2-8ubuntu4_i386.deb (--install):
 pre-dependency problem - not installing libgcc1
Preparing to replace liblocale-gettext-perl 1.05-6 (using .../liblocale-gettext-perl_1.05-6_i386.deb) ...
Unpacking replacement liblocale-gettext-perl ...
Selecting previously deselected package liblzma2.
Unpacking liblzma2 (from .../liblzma2_5.0.0-2_i386.deb) ...
Preparing to replace libncursesw5 5.7+20090803-2ubuntu3 (using .../libncursesw5_5.7+20101128-1_i386.deb) ...
Unpacking replacement libncursesw5 ...
dpkg: regarding .../libpam0g_1.1.2-2ubuntu8.3_i386.deb containing libpam0g, pre-dependency problem:
 libpam0g pre-depends on multiarch-support
  multiarch-support is not installed.
dpkg: error processing packages/libpam0g_1.1.2-2ubuntu8.3_i386.deb (--install):
 pre-dependency problem - not installing libpam0g
dpkg: regarding .../libpam-modules_1.1.2-2ubuntu8.3_i386.deb containing libpam-modules, pre-dependency problem:
 libpam-modules pre-depends on libpam0g (>= 1.1.2-2ubuntu4)
  libpam0g is installed, but is version 1.1.1-2ubuntu5.1.
dpkg: error processing packages/libpam-modules_1.1.2-2ubuntu8.3_i386.deb (--install):
 pre-dependency problem - not installing libpam-modules
dpkg: regarding .../libselinux1_2.0.96-1ubuntu2_i386.deb containing libselinux1, pre-dependency problem:
 libselinux1 pre-depends on multiarch-support
  multiarch-support is not installed.
dpkg: error processing packages/libselinux1_2.0.96-1ubuntu2_i386.deb (--install):
 pre-dependency problem - not installing libselinux1
Preparing to replace libsigc++-2.0-0c2a 2.2.4.2-1 (using .../libsigc++-2.0-0c2a_2.2.4.2-1ubuntu1_i386.deb) ...
Unpacking replacement libsigc++-2.0-0c2a ...
dpkg: regarding .../libsqlite3-0_3.7.4-2ubuntu5_i386.deb containing libsqlite3-0, pre-dependency problem:
 libsqlite3-0 pre-depends on multiarch-support
  multiarch-support is not installed.
dpkg: error processing packages/libsqlite3-0_3.7.4-2ubuntu5_i386.deb (--install):
 pre-dependency problem - not installing libsqlite3-0
dpkg: regarding .../libstdc++6_4.5.2-8ubuntu4_i386.deb containing libstdc++6, pre-dependency problem:
 libstdc++6 pre-depends on multiarch-support
  multiarch-support is not installed.
dpkg: error processing packages/libstdc++6_4.5.2-8ubuntu4_i386.deb (--install):
 pre-dependency problem - not installing libstdc++6
Preparing to replace libtext-charwidth-perl 0.04-6 (using .../libtext-charwidth-perl_0.04-6_i386.deb) ...
Unpacking replacement libtext-charwidth-perl ...
Preparing to replace libtext-iconv-perl 1.7-2 (using .../libtext-iconv-perl_1.7-2_i386.deb) ...
Unpacking replacement libtext-iconv-perl ...
Preparing to replace libtext-wrapi18n-perl 0.06-7 (using .../libtext-wrapi18n-perl_0.06-7_all.deb) ...
Unpacking replacement libtext-wrapi18n-perl ...
dpkg: regarding .../libuuid1_2.17.2-9.1ubuntu4_i386.deb containing libuuid1, pre-dependency problem:
 libuuid1 pre-depends on multiarch-support
  multiarch-support is not installed.
dpkg: error processing packages/libuuid1_2.17.2-9.1ubuntu4_i386.deb (--install):
 pre-dependency problem - not installing libuuid1
Selecting previously deselected package libxapian22.
Unpacking libxapian22 (from .../libxapian22_1.2.4-1_i386.deb) ...
Preparing to replace passwd 1:4.1.4.2-1ubuntu2.2 (using .../passwd_1%3a4.1.4.2+svn3283-3ubuntu1_i386.deb) ...
Unpacking replacement passwd ...
Preparing to replace perl-base 5.10.1-8ubuntu2.1 (using .../perl-base_5.10.1-17ubuntu4.1_i386.deb) ...
Unpacking replacement perl-base ...
Replacing files in old package perl ...
Preparing to replace sensible-utils 0.0.1ubuntu3 (using .../sensible-utils_0.0.6ubuntu2_all.deb) ...
Unpacking replacement sensible-utils ...
Preparing to replace tzdata 2011g-0ubuntu0.10.04 (using .../tzdata_2011g-0ubuntu0.11.04_i386.deb) ...
Unpacking replacement tzdata ...
dpkg: regarding .../zlib1g_1%3a1.2.3.4.dfsg-3ubuntu3_i386.deb containing zlib1g, pre-dependency problem:
 zlib1g pre-depends on multiarch-support
  multiarch-support is not installed.
dpkg: error processing packages/zlib1g_1%3a1.2.3.4.dfsg-3ubuntu3_i386.deb (--install):
 pre-dependency problem - not installing zlib1g
Setting up gcc-4.5-base (4.5.2-8ubuntu4) ...
Setting up libbz2-1.0 (1.0.5-6ubuntu1) ...

Setting up libc-bin (2.13-0ubuntu13) ...
Installing new version of config file /etc/gai.conf ...

dpkg: dependency problems prevent configuration of libcwidget3:
 libcwidget3 depends on libstdc++6 (>= 4.5); however:
  Version of libstdc++6 on system is 4.4.3-4ubuntu5.
dpkg: error processing libcwidget3 (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libept1:
 libept1 depends on libapt-pkg4.10; however:
  Package libapt-pkg4.10 is not installed.
dpkg: error processing libept1 (--install):
 dependency problems - leaving unconfigured
Setting up liblzma2 (5.0.0-2) ...

Setting up libncursesw5 (5.7+20101128-1) ...

dpkg: dependency problems prevent configuration of libsigc++-2.0-0c2a:
 libsigc++-2.0-0c2a depends on libstdc++6 (>= 4.5); however:
  Version of libstdc++6 on system is 4.4.3-4ubuntu5.
dpkg: error processing libsigc++-2.0-0c2a (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxapian22:
 libxapian22 depends on libstdc++6 (>= 4.5); however:
  Version of libstdc++6 on system is 4.4.3-4ubuntu5.
dpkg: error processing libxapian22 (--install):
 dependency problems - leaving unconfigured
Setting up perl-base (5.10.1-17ubuntu4.1) ...
Setting up sensible-utils (0.0.6ubuntu2) ...

Setting up libboost-iostreams1.42.0 (1.42.0-4ubuntu2) ...

Processing triggers for man-db ...
Setting up libtext-iconv-perl (1.7-2) ...
Setting up debianutils (3.4.3ubuntu1) ...

Setting up liblocale-gettext-perl (1.05-6) ...
Setting up libtext-charwidth-perl (0.04-6) ...
Setting up libtext-wrapi18n-perl (0.06-7) ...
Setting up passwd (1:4.1.4.2+svn3283-3ubuntu1) ...

Setting up debconf-i18n (1.5.36ubuntu4) ...
Setting up debconf (1.5.36ubuntu4) ...

Setting up tzdata (2011g-0ubuntu0.11.04) ...

User defined time zone, leaving /etc/localtime unchanged.
Local time is now:      Thu Aug 11 11:06:16 EDT 2011.
Universal Time is now:  Thu Aug 11 15:06:16 UTC 2011.
Run 'dpkg-reconfigure tzdata' if you wish to change it.


Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 packages/debconf-english_1.5.36ubuntu4_all.deb
 packages/libattr1_1%3a2.4.44-2ubuntu3_i386.deb
 packages/libc6_2.13-0ubuntu13_i386.deb
 packages/libgcc1_1%3a4.5.2-8ubuntu4_i386.deb
 packages/libpam0g_1.1.2-2ubuntu8.3_i386.deb
 packages/libpam-modules_1.1.2-2ubuntu8.3_i386.deb
 packages/libselinux1_2.0.96-1ubuntu2_i386.deb
 packages/libsqlite3-0_3.7.4-2ubuntu5_i386.deb
 packages/libstdc++6_4.5.2-8ubuntu4_i386.deb
 packages/libuuid1_2.17.2-9.1ubuntu4_i386.deb
 packages/zlib1g_1%3a1.2.3.4.dfsg-3ubuntu3_i386.deb
 libcwidget3
 libept1
 libsigc++-2.0-0c2a
 libxapian22



```
**Wicd Log file:**
```

root@root:/var/log/wicd# cat wicd.log
2011/08/11 11:10:19 :: ---------------------------
2011/08/11 11:10:19 :: wicd initializing...
2011/08/11 11:10:19 :: ---------------------------
2011/08/11 11:10:19 :: wicd is version 1.7.0 552
2011/08/11 11:10:19 :: did not find backend in configuration, setting default external
2011/08/11 11:10:19 :: setting backend to external
2011/08/11 11:10:19 :: trying to load backend external
2011/08/11 11:10:19 :: successfully loaded backend external
2011/08/11 11:10:19 :: trying to load backend external
2011/08/11 11:10:19 :: successfully loaded backend external
2011/08/11 11:10:19 :: Automatically detected wireless interface wlan0
2011/08/11 11:10:19 :: did not find wireless_interface in configuration, setting default wlan0
2011/08/11 11:10:19 :: setting wireless interface wlan0
2011/08/11 11:10:19 :: automatically detected wired interface eth0
2011/08/11 11:10:19 :: did not find wired_interface in configuration, setting default eth0
2011/08/11 11:10:19 :: setting wired interface eth0
2011/08/11 11:10:19 :: did not find wpa_driver in configuration, setting default wext
2011/08/11 11:10:19 :: setting wpa driver wext
2011/08/11 11:10:19 :: did not find always_show_wired_interface in configuration, setting default False
2011/08/11 11:10:19 :: did not find use_global_dns in configuration, setting default False
2011/08/11 11:10:19 :: setting use global dns to False
2011/08/11 11:10:19 :: did not find global_dns_1 in configuration, setting default None
2011/08/11 11:10:19 :: did not find global_dns_2 in configuration, setting default None
2011/08/11 11:10:19 :: did not find global_dns_3 in configuration, setting default None
2011/08/11 11:10:19 :: did not find global_dns_dom in configuration, setting default None
2011/08/11 11:10:19 :: did not find global_search_dom in configuration, setting default None
2011/08/11 11:10:19 :: setting global dns
2011/08/11 11:10:19 :: global dns servers are None None None
2011/08/11 11:10:19 :: domain is None
2011/08/11 11:10:19 :: search domain is None
2011/08/11 11:10:19 :: did not find auto_reconnect in configuration, setting default True
2011/08/11 11:10:19 :: setting automatically reconnect when connection drops True
2011/08/11 11:10:19 :: did not find debug_mode in configuration, setting default False
2011/08/11 11:10:19 :: did not find wired_connect_mode in configuration, setting default 1
2011/08/11 11:10:19 :: did not find signal_display_type in configuration, setting default 0
2011/08/11 11:10:19 :: did not find should_verify_ap in configuration, setting default 1
2011/08/11 11:10:19 :: did not find dhcp_client in configuration, setting default 0
2011/08/11 11:10:19 :: Setting dhcp client to 0
2011/08/11 11:10:19 :: did not find link_detect_tool in configuration, setting default 0
2011/08/11 11:10:19 :: did not find flush_tool in configuration, setting default 0
2011/08/11 11:10:19 :: did not find sudo_app in configuration, setting default 0
2011/08/11 11:10:19 :: did not find prefer_wired in configuration, setting default False
2011/08/11 11:10:19 :: Wireless configuration file not found, creating...
2011/08/11 11:10:19 :: Wired configuration file not found, creating a default...
2011/08/11 11:10:19 :: Creating wired profile for wired-default
2011/08/11 11:10:19 :: dhclient.conf.template not found, copying...
2011/08/11 11:10:19 :: chmoding configuration files 0600...
2011/08/11 11:10:19 :: chowning configuration files root:root...
2011/08/11 11:10:19 :: Using wireless interface...wlan0
2011/08/11 11:10:19 :: Using wired interface...eth0
2011/08/11 11:10:25 :: Autoconnecting...
2011/08/11 11:10:25 :: No wired connection present, attempting to autoconnect to wireless network
2011/08/11 11:10:26 :: Unable to autoconnect, you'll have to manually connect
2011/08/11 11:10:30 :: Autoconnecting...
2011/08/11 11:10:30 :: No wired connection present, attempting to autoconnect to wireless network
2011/08/11 11:10:31 :: Unable to autoconnect, you'll have to manually connect
2011/08/11 11:10:35 :: Autoconnecting...
2011/08/11 11:10:35 :: No wired connection present, attempting to autoconnect to wireless network
2011/08/11 11:10:36 :: Unable to autoconnect, you'll have to manually connect
2011/08/11 11:10:40 :: Autoconnecting...
2011/08/11 11:10:40 :: No wired connection present, attempting to autoconnect to wireless network
2011/08/11 11:10:41 :: Unable to autoconnect, you'll have to manually connect
2011/08/11 11:11:18 :: did not find main_width in configuration, setting default -1
2011/08/11 11:11:18 :: did not find main_height in configuration, setting default -1



```

---

### Post by lkjoel on 2011-08-11
Could you give me the output of this Terminal command?
```
sudo lspci -vvnn

```

---

### Post by temporos on 2011-08-11
Hey, guys.  I'm having the same issues detecting wireless networks after upgrading to 10.04.3 x64.  My system shows the same symptoms as the OP's, but I was able to fully update *aptitude*.  I also successfully compiled and installed the driver **lkjoel** provided, but I still can't detect any wireless networks after a restart.

I'm on an Everex XT5300T, if that helps.

---

### Post by lkjoel on 2011-08-11
> **temporos said:**
> Hey, guys.  I'm having the same issues detecting wireless networks after upgrading to 10.04.3 x64.  My system shows the same symptoms as the OP's, but I was able to fully update *aptitude*.  I also successfully compiled and installed the driver **lkjoel** provided, but I still can't detect any wireless networks after a restart.

I'm on an Everex XT5300T, if that helps.
Could you give me the output of these Terminal commands?
```
sudo lspci -vvnn
sudo nm-tool
sudo ifconfig
iwconfig
uname -a
lsb_release -a
sudo rfkill list all
sudo lshw -C Network

```

---

### Post by temporos on 2011-08-12
Here are the results. The first spit out a *looooong* report, so I've included only the part relevant to wireless networking.

**sudo lspci -vvnn**
```
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
    Subsystem: Atheros Communications Inc. Device [168c:3065]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at c0400000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Address: 00000000  Data: 0000
    Capabilities: [60] Express (v1) Legacy Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <128ns, L1 <2us
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr+ UncorrErr+ FatalErr- UnsuppReq+ AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <64us
            ClockPM- Suprise- LLActRep- BwNot-
        LnkCtl:    ASPM L0s Enabled; RCB 128 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
    Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
        Vector table: BAR=0 offset=00000000
        PBA: BAR=0 offset=00000000
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Virtual Channel <?>
    Kernel driver in use: ath5k
    Kernel modules: ath5k
```**sudo nm-tool**
```
NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             connected
  Default:           yes
  HW Address:        00:14:0B:3C:C3:8A

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.0.1.9
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.1.1

    DNS:             10.0.1.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        00:16:44:15:A1:87

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points
```**sudo ifconfig**
```
eth0      Link encap:Ethernet  HWaddr 00:14:0b:3c:c3:8a  
          inet addr:10.0.1.9  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:bff:fe3c:c38a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1874 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1432 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2225778 (2.2 MB)  TX bytes:222251 (222.2 KB)
          Interrupt:20 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:16:44:15:a1:87  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```**iwconfig**
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```**uname -a**
```
Linux bekkers 2.6.32-33-generic #72-Ubuntu SMP Fri Jul 29 21:07:13 UTC 2011 x86_64 GNU/Linux
```**lsb_release -a**
```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.3 LTS
Release:    10.04
Codename:    lucid
```**sudo rfkill list all**
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```**sudo lshw -C network**
```
  *-network               
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:16:44:15:a1:87
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:c0400000-c040ffff
```

---

### Post by lkjoel on 2011-08-12
Hmm... Could you give me the output of these Terminal commands?
```
cat /etc/network/interfaces
sudo iwlist scan

```

---

### Post by temporos on 2011-08-12
```
bek@bekkers:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

bek@bekkers:~$ sudo iwlist scan
[sudo] password for bek: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Resource temporarily unavailable

```

---

### Post by Nazaf on 2011-08-12
> **lkjoel said:**
> Could you give me the output of this Terminal command?
```
sudo lspci -vvnn

```

```
root@root:~# sudo lspci -vvnn
00:00.0 Host bridge [0600]: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570] (rev 02)
    Subsystem: Dell Device [1028:0151]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
    Latency: 0
    Region 0: Memory at f0000000 (32-bit, prefetchable) [size=128M]
    Capabilities: [e4] Vendor Specific Information <?>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller [0300]: Intel Corporation 82865G Integrated Graphics Controller [8086:2572] (rev 02)
    Subsystem: Dell Device [1028:0151]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx+
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at e8000000 (32-bit, prefetchable) [size=128M]
    Region 1: Memory at feb80000 (32-bit, non-prefetchable) [size=512K]
    Region 2: I/O ports at ed98 [size=8]
    Capabilities: [d0] Power Management version 1
        Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: i915
    Kernel modules: intelfb, i915

00:06.0 System peripheral [0880]: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface [8086:2576] (rev 02)
    Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Region 0: Memory at fecf0000 (32-bit, non-prefetchable) [size=4K]

00:1d.0 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 [8086:24d2] (rev 02)
    Subsystem: Dell Device [1028:0151]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 4: I/O ports at ff80 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 [8086:24d4] (rev 02)
    Subsystem: Dell Device [1028:0151]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 19
    Region 4: I/O ports at ff60 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 [8086:24d7] (rev 02)
    Subsystem: Dell Device [1028:0151]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin C routed to IRQ 18
    Region 4: I/O ports at ff40 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 [8086:24de] (rev 02)
    Subsystem: Dell Device [1028:0151]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 4: I/O ports at ff20 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [8086:24dd] (rev 02) (prog-if 20)
    Subsystem: Dell Device [1028:0151]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin D routed to IRQ 23
    Region 0: Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fea00000-feafffff
    Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Kernel modules: shpchp

00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02)
    Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller [8086:24db] (rev 02) (prog-if 8a [Master SecP PriP])
    Subsystem: Dell Device [1028:0151]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 18
    Region 0: I/O ports at 01f0 [size=8]
    Region 1: I/O ports at 03f4 [size=1]
    Region 2: I/O ports at 0170 [size=8]
    Region 3: I/O ports at 0374 [size=1]
    Region 4: I/O ports at ffa0 [size=16]
    Region 5: Memory at feb7fc00 (32-bit, non-prefetchable) [size=1K]
    Kernel driver in use: ata_piix

00:1f.2 IDE interface [0101]: Intel Corporation 82801EB (ICH5) SATA Controller [8086:24d1] (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Dell Device [1028:0151]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 18
    Region 0: I/O ports at fe00 [size=8]
    Region 1: I/O ports at fe10 [size=4]
    Region 2: I/O ports at fe20 [size=8]
    Region 3: I/O ports at fe30 [size=4]
    Region 4: I/O ports at fea0 [size=16]
    Kernel driver in use: ata_piix

00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller [8086:24d3] (rev 02)
    Subsystem: Dell Device [1028:0151]
    Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin B routed to IRQ 3
    Region 4: I/O ports at eda0 [size=32]
    Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller [8086:24d5] (rev 02)
    Subsystem: Dell Device [1028:0151]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 17
    Region 0: I/O ports at ee00 [size=256]
    Region 1: I/O ports at edc0 [size=64]
    Region 2: Memory at feb7fa00 (32-bit, non-prefetchable) [size=512]
    Region 3: Memory at feb7f900 (32-bit, non-prefetchable) [size=256]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

01:0a.0 Network controller [0280]: RaLink Device [1814:3060]
    Subsystem: D-Link System Inc Device [1186:3c04]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (500ns min, 1000ns max), Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at fead0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: rt2800pci
    Kernel modules: rt2800pci

01:0c.0 Ethernet controller [0200]: Intel Corporation 82540EM Gigabit Ethernet Controller [8086:100e] (rev 02)
    Subsystem: Dell Device [1028:0151]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (63750ns min), Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 18
    Region 0: Memory at feae0000 (32-bit, non-prefetchable) [size=128K]
    Region 2: I/O ports at df40 [size=64]
    Capabilities: [dc] Power Management version 2
        Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=1 PME-
    Capabilities: [e4] PCI-X non-bridge device
        Command: DPERE- ERO+ RBC=512 OST=1
        Status: Dev=00:00.0 64bit- 133MHz- SCD- USC- DC=simple DMMRBC=2048 DMOST=1 DMCRS=16 RSCEM- 266MHz- 533MHz-
    Capabilities: [f0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Address: 0000000000000000  Data: 0000
    Kernel driver in use: e1000
    Kernel modules: e1000


```

---

### Post by Ih4cktEch on 2013-02-14
Firstly Hi, great forum, saved me a headache so many times! :)  Secondly, I had this problem for the last 2 days. (I know it is an old post but just encase someone may have this issue in the future).  I resolved it by opening Wcid program, clicking preferences, then entering wlan0 in the wireless interface box. The signal wasn't great though until a reboot.   Finally I can move away from my router and enjoy wireless again! :)

---

