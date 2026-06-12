---
title: "Using Tenda Wireless"
date: 2012-02-18
forum: Networking &amp; Wireless
---

### Post by Twon10 on 2012-02-18
I am having trouble setting up the Tenda 11n Wireless usb adapter. I am also new to linux. Can someone give me step by step on how to make this thing work please?:D

---

### Post by praseodym on 2012-02-18
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these 5 commands:

```
uname -a
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by Twon10 on 2012-02-18
This what i got:

antoine@Oran-Toine:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:5370 Ralink Technology, Corp. 
antoine@Oran-Toine:~$ lsmod
Module                  Size  Used by
snd_seq_dummy          12686  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
binfmt_misc            17292  1 
i915                  509519  2 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  4 
snd_hda_codec          91859  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
drm_kms_helper         32889  1 i915
snd_pcm                80435  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  3 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
drm                   192194  3 i915,drm_kms_helper
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73673  0 
serio_raw              12990  0 
ppdev                  12849  0 
parport_pc             32114  1 
soundcore              12600  1 snd
i2c_algo_bit           13199  1 i915
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
atl2                   27979  0 
floppy                 60310  0 
antoine@Oran-Toine:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by praseodym on 2012-02-19
Try this driver:
```
sudo apt-get install linux-headers-generic build-essential
wget http://media.cdn.ubuntu-de.org/forum/attachments/16/16/2831641-angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO.tar.gz
tar xvf 2831641-angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO.tar.gz
cd angepa*
sudo make
sudo make install
```
Reboot. Check after that:

```
iwconfig
lsmod
sudo iwlist scan
dmesg | grep rt5
```

---

### Post by Twon10 on 2012-02-19
I did what praseodym told me to do 
 
                                  ```
antoine@Oran-Toine:~$ sudo apt-get install linux-headers-generic build-essentialReading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 linux-headers-generic is already the newest version.  
 The following extra packages will be installed:  
   dpkg-dev fakeroot g++ g++-4.6 libalgorithm-diff-perl  
   libalgorithm-diff-xs-perl libalgorithm-merge-perl libdpkg-perl  
   libstdc++6-4.6-dev patch  
 Suggested packages:  
   debian-keyring g++-multilib g++-4.6-multilib gcc-4.6-doc libstdc++6-4.6-dbg  
   libstdc++6-4.6-doc diffutils-doc  
 The following NEW packages will be installed:  
   build-essential dpkg-dev fakeroot g++ g++-4.6 libalgorithm-diff-perl  
   libalgorithm-diff-xs-perl libalgorithm-merge-perl libdpkg-perl  
   libstdc++6-4.6-dev patch  
 0 upgraded, 11 newly installed, 0 to remove and 0 not upgraded.  
 Need to get 8,673 kB of archives.  
 After this operation, 28.7 MB of additional disk space will be used.  
 Do you want to continue [Y/n]? y  
 Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libstdc++6-4.6-dev i386 4.6.1-9ubuntu3 [1,589 kB]  
 Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main g++-4.6 i386 4.6.1-9ubuntu3 [6,187 kB]  
 Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main g++ i386 4:4.6.1-2ubuntu5 [1,434 B]  
 Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libdpkg-perl all 1.16.0.3ubuntu5 [171 kB]  
 Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main patch i386 2.6.1-2 [86.5 kB]  
 Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main dpkg-dev all 1.16.0.3ubuntu5 [473 kB]  
 Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main build-essential i386 11.5ubuntu1 [5,920 B]  
 Get:8 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main fakeroot i386 1.17-1 [81.6 kB]  
 Get:9 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libalgorithm-diff-perl all 1.19.02-2 [50.7 kB]  
 Get:10 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libalgorithm-diff-xs-perl i386 0.04-1build1 [13.8 kB]  
 Get:11 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libalgorithm-merge-perl all 0.08-2 [12.7 kB]  
 Fetched 8,673 kB in 6s (1,321 kB/s)                                             
 Selecting previously deselected package libstdc++6-4.6-dev.  
 (Reading database ... 158766 files and directories currently installed.)  
 Unpacking libstdc++6-4.6-dev (from .../libstdc++6-4.6-dev_4.6.1-9ubuntu3_i386.deb) ...  
 Selecting previously deselected package g++-4.6.  
 Unpacking g++-4.6 (from .../g++-4.6_4.6.1-9ubuntu3_i386.deb) ...  
 Selecting previously deselected package g++.  
 Unpacking g++ (from .../g++_4%3a4.6.1-2ubuntu5_i386.deb) ...  
 Selecting previously deselected package libdpkg-perl.  
 Unpacking libdpkg-perl (from .../libdpkg-perl_1.16.0.3ubuntu5_all.deb) ...  
 Selecting previously deselected package patch.  
 Unpacking patch (from .../patch_2.6.1-2_i386.deb) ...  
 Selecting previously deselected package dpkg-dev.  
 Unpacking dpkg-dev (from .../dpkg-dev_1.16.0.3ubuntu5_all.deb) ...  
 Selecting previously deselected package build-essential.  
 Unpacking build-essential (from .../build-essential_11.5ubuntu1_i386.deb) ...  
 Selecting previously deselected package fakeroot.  
 Unpacking fakeroot (from .../fakeroot_1.17-1_i386.deb) ...  
 Selecting previously deselected package libalgorithm-diff-perl.  
 Unpacking libalgorithm-diff-perl (from .../libalgorithm-diff-perl_1.19.02-2_all.deb) ...  
 Selecting previously deselected package libalgorithm-diff-xs-perl.  
 Unpacking libalgorithm-diff-xs-perl (from .../libalgorithm-diff-xs-perl_0.04-1build1_i386.deb) ...  
 Selecting previously deselected package libalgorithm-merge-perl.  
 Unpacking libalgorithm-merge-perl (from .../libalgorithm-merge-perl_0.08-2_all.deb) ...  
 Processing triggers for man-db ...  
 Setting up libdpkg-perl (1.16.0.3ubuntu5) ...  
 Setting up patch (2.6.1-2) ...  
 Setting up dpkg-dev (1.16.0.3ubuntu5) ...  
 Setting up fakeroot (1.17-1) ...  
 update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.  
 Setting up libalgorithm-diff-perl (1.19.02-2) ...  
 Setting up libalgorithm-diff-xs-perl (0.04-1build1) ...  
 Setting up libalgorithm-merge-perl (0.08-2) ...  
 Setting up libstdc++6-4.6-dev (4.6.1-9ubuntu3) ...  
 Setting up g++-4.6 (4.6.1-9ubuntu3) ... 
 Setting up g++ (4:4.6.1-2ubuntu5) ...  
 update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode.  
 Setting up build-essential (11.5ubuntu1) ...  
 antoine@Oran-Toine:~$ wget [http://media.cdn.ubuntu-de.org/forum/attachments/16/16/2831641-angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/16/16/2831641-angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO.tar.gz) 
 --2012-02-19 07:35:56--  [http://media.cdn.ubuntu-de.org/forum/attachments/16/16/2831641-angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/16/16/2831641-angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO.tar.gz) 
 Resolving media.cdn.ubuntu-de.org... 213.95.41.13  
 Connecting to media.cdn.ubuntu-de.org|213.95.41.13|:80... connected.  
 HTTP request sent, awaiting response... 200 OK  
 Length: 925955 (904K) [application/octet-stream]  
 Saving to: `2831641-angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO.tar.gz' 
 

 100%[======================================>] 925,955      640K/s   in 1.4s     
 

 2012-02-19 07:35:58 (640 KB/s) - `2831641-angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO.tar.gz' saved [925955/925955]  
 

 antoine@Oran-Toine:~$ tar xvf 2831641-angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO.tar.gz 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/ 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/ 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/ 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/sta/ 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/chips/ 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/ 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/tools/ 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/iface/ 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/os/ 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/chip/ 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/ 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/Makefile 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/iwpriv_usage.txt 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/sta_ate_iwpriv_usage.txt 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/README_STA_usb 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/RT2870STA.dat 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/RT2870STACard.dat 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/cmm_txbf.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/cmm_wpa.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/frq_cal.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/cmm_wep.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/misc.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/cmm_data_usb.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/rtmp_init.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/rt_channel.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/cmm_sync.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/crypt_md5.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/mlme.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/crypt_arc4.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/spectrum.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/rtmp_mcu.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/dfs.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/ee_prom.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/rtmp_timer.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/crypt_aes.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/cmm_sanity.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/cmm_cmd.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/cmm_asic.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/cmm_info.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/rtusb_io.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/ba_action.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/cmm_video.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/cmm_tkip.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/netif_block.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/cmm_profile.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/client_wds.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/rtmp_init_inf.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/cmm_cfg.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/rtusb_data.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/rt2870.bin 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/rtusb_dev_id.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/ee_efuse.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/action.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/rt_ate.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/rt_os_util.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/cmm_data.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/rt_rf.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/rt_led.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/rtusb_bulk.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/crypt_sha2.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/eeprom.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/cmm_mac_usb.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/cmm_aes.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/common/crypt_hmac.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/video.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/firmware.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/rtmp_os.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/crypt_hmac.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/dfs.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/sta_cfg.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/ap.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/crypt_arc4.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/misc.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/rtmp_cmd.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/br_ftph.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/wfa_p2p.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/spectrum_def.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/rtmp_iface.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/rtmp_comm.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/action.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/netif_block.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/dot11i_wpa.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/vr_ikans.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/rtmp_def.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/crypt_aes.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/spectrum.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/misc_cmm.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/client_wds_cmm.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/eeprom.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/ap_diversity.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/rtmp_osabl.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/crypt_sha2.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/crypt_md5.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/rt_led.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/mlme.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/rt_ate.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/rtmp_chip.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/rtmp_dot11.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/rt_os_util.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/wsc.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/chlist.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/rtmp_mcu.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/rtmp_timer.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/client_wds.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/rt_config.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/oid.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/wpa.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/wpa_cmm.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/cfg80211extr.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/cfg80211.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/rtmp.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/rtmp_type.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/ags.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/rtusb_io.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/link_list.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/frq_cal.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/rt_os_net.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/sta/sync.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/sta/sanity.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/sta/rtmp_ckipmic.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/sta/connect.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/sta/auth.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/sta/assoc.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/sta/auth_rsp.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/sta/sta_cfg.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/sta/dls.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/sta/wpa.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/sta/rtmp_data.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/sta/ags.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/chips/rt30xx.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/chips/rt3070.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/chips/rt3370.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/chips/rt33xx.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/chips/rtmp_chip.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/chips/rt5390.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/chips/rt28xx.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/tools/bin2h.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/tools/Makefile 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/tools/bin2h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/iface/iface_util.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/iface/rtmp_usb.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/os/rt_linux_cmm.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/os/rt_linux.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/os/rt_os.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/os/rt_drv.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/chip/rt5390.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/chip/chip_id.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/chip/rt3070.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/chip/rtmp_mac.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/chip/rt28xx.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/chip/rtmp_phy.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/chip/rt33xx.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/chip/rt30xx.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/chip/rt3370.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/chip/mac_usb.h 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/config.mk 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/rt_proc.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/sta_ioctl.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/rt_linux_symb.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/rt_symb.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/Makefile.clean 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/rt_usb_util.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/Makefile.libautoprovision.6 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/cfg80211.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/usb_main_dev.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/vr_ikans.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/vr_bdlt.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/Makefile.6.util 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/rt_linux.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/Makefile.4.netif 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/Makefile.6.netif 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/cfg80211drv.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/rt_profile.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/rt_main_dev.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/Makefile.4 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/Makefile.6 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/rt_usb.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/Makefile.4.util 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/rt_rbus_pci_drv.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/inf_ppa.c 
 angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/br_ftph.c 
 antoine@Oran-Toine:~$ cd angepa*  
 antoine@Oran-Toine:~/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO$ sudo makemake -C tools  
 make[1]: Entering directory `/home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/tools' 
 gcc -g bin2h.c -o bin2h  
 make[1]: Leaving directory `/home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/tools' 
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/tools/bin2h 
 cp -f os/linux/Makefile.6 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/Makefile 
 make -C /lib/modules/3.0.0-16-generic/build SUBDIRS=/home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux modules  
 make[1]: Entering directory `/usr/src/linux-headers-3.0.0-16-generic'  
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/crypt_md5.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/crypt_sha2.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/crypt_hmac.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/crypt_aes.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/crypt_arc4.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/mlme.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_wep.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/action.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_data.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/rtmp_init.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/rtmp_init_inf.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_tkip.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_aes.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_sync.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/eeprom.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_sanity.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_info.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_cfg.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_wpa.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/dfs.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/spectrum.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/rtmp_timer.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/rt_channel.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_profile.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_asic.o 
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_asic.c: In function &#8216;AsicGetAutoAgcOffset&#8217;:  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_asic.c:878:10: warning: unused variable &#8216;bTempSuccess&#8217; [-Wunused-variable]  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_asic.c:877:6: warning: unused variable &#8216;LookupTableIndex&#8217; [-Wunused-variable]  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_asic.c:876:6: warning: unused variable &#8216;CurrentTemp&#8217; [-Wunused-variable]  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_asic.c:875:8: warning: unused variable &#8216;BbpValue&#8217; [-Wunused-variable]  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_asic.c:874:32: warning: unused variable &#8216;pTxPowerTuningEntry2&#8217; [-Wunused-variable]  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_asic.c:871:8: warning: unused variable &#8216;RFValue&#8217; [-Wunused-variable]  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_asic.c:870:32: warning: unused variable &#8216;pTxPowerTuningEntry&#8217; [-Wunused-variable]  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_asic.c: In function &#8216;AsicAdjustTxPower&#8217;:  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_asic.c:1524:20: warning: unused variable &#8216;pFinalTxPwr&#8217; [-Wunused-variable]  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_asic.c:1522:11: warning: unused variable &#8216;bAutoTxAgc&#8217; [-Wunused-variable]  
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_cmd.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../os/linux/rt_profile.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../chips/rtmp_chip.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../sta/assoc.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../sta/auth.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../sta/auth_rsp.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../sta/sync.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../sta/sanity.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../sta/rtmp_data.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../sta/connect.o 
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../sta/connect.c: In function &#8216;LinkUp&#8217;:  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../sta/connect.c:1481:35: warning: unused variable &#8216;pCurrEntry&#8217; [-Wunused-variable]  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../sta/connect.c:1480:28: warning: unused variable &#8216;HashIdx&#8217; [-Wunused-variable]  
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../sta/wpa.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../sta/ags.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../sta/sta_cfg.o 
 In file included from /usr/src/linux-headers-3.0.0-16-generic/arch/x86/include/asm/uaccess.h:570:0, 
                  from /usr/src/linux-headers-3.0.0-16-generic/arch/x86/include/asm/sections.h:5, 
                  from /usr/src/linux-headers-3.0.0-16-generic/arch/x86/include/asm/hw_irq.h:26, 
                  from include/linux/irq.h:351,  
                  from /usr/src/linux-headers-3.0.0-16-generic/arch/x86/include/asm/hardirq.h:5, 
                  from include/linux/hardirq.h:7,  
                  from include/linux/interrupt.h:12,  
                  from /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/os/rt_linux.h:40, 
                  from /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/rtmp_os.h:44, 
                  from /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/rtmp_comm.h:60, 
                  from /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/include/rt_config.h:33, 
                  from /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../sta/sta_cfg.c:28: 
 In function &#8216;copy_from_user&#8217;,  
     inlined from &#8216;RTMPSetInformation&#8217; at /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../sta/sta_cfg.c:1709:28: 
 /usr/src/linux-headers-3.0.0-16-generic/arch/x86/include/asm/uaccess_32.h:211:26: warning: call to &#8216;copy_from_user_overflow&#8217; declared with attribute warning: copy_from_user() buffer size is not provably correct [enabled by default]  
 In function &#8216;copy_from_user&#8217;,  
     inlined from &#8216;RTMPSetInformation&#8217; at /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../sta/sta_cfg.c:2198:28: 
 /usr/src/linux-headers-3.0.0-16-generic/arch/x86/include/asm/uaccess_32.h:211:26: warning: call to &#8216;copy_from_user_overflow&#8217; declared with attribute warning: copy_from_user() buffer size is not provably correct [enabled by default]  
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/rt_os_util.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../os/linux/sta_ioctl.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../os/linux/rt_linux.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../os/linux/rt_main_dev.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/ba_action.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/rt_led.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_mac_usb.o 
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_mac_usb.c: In function &#8216;RTMPFreeTxRxRingMemory&#8217;:  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_mac_usb.c:235:9: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type [enabled by default]  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_mac_usb.c:62:20: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_mac_usb.c:242:9: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type [enabled by default]  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_mac_usb.c:62:20: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_mac_usb.c:280:11: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type [enabled by default]  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_mac_usb.c:62:20: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __HTTX_BUFFER **&#8217;  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_mac_usb.c: In function &#8216;NICInitTransmit&#8217;:  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_mac_usb.c:509:12: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type [enabled by default]  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_mac_usb.c:62:20: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_mac_usb.c: In function &#8216;RTMPAllocTxRxRingMemory&#8217;:  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_mac_usb.c:568:13: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type [enabled by default]  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_mac_usb.c:34:20: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __HTTX_BUFFER **&#8217;  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_mac_usb.c:598:12: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type [enabled by default]  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_mac_usb.c:34:20: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_mac_usb.c:612:12: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type [enabled by default]  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_mac_usb.c:34:20: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_mac_usb.c:630:13: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type [enabled by default]  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_mac_usb.c:34:20: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;UCHAR **&#8217;  
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/rtusb_io.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/rtusb_data.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/cmm_data_usb.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/rtusb_bulk.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/ee_prom.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/ee_efuse.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/rtmp_mcu.o 
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/rtmp_mcu.c: In function &#8216;RtmpAsicSendCommandToMcu&#8217;:  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/rtmp_mcu.c:416:8: warning: unused variable &#8216;IrqFlags&#8217; [-Wunused-variable]  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/rtmp_mcu.c:415:13: warning: unused variable &#8216;pObj&#8217; [-Wunused-variable]  
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/rt_rf.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../os/linux/rt_usb.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/frq_cal.o 
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/frq_cal.c: In function &#8216;FrequencyCalibration&#8217;:  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/frq_cal.c:202:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/frq_cal.c:215:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/frq_cal.c:230:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/frq_cal.c:252:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/frq_cal.c:265:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/frq_cal.c:280:18: warning: comparison of distinct pointer types lacks a cast [enabled by default]  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/frq_cal.c:136:10: warning: unused variable &#8216;bUpdateRFR&#8217; [-Wunused-variable]  
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../chips/rt3070.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../chips/rt30xx.o 
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../chips/rt30xx.c: In function &#8216;RT30xx_ChipSwitchChannel&#8217;:  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../chips/rt30xx.c:633:17: warning: unused variable &#8216;BbpR109&#8217; [-Wunused-variable]  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../chips/rt30xx.c:632:30: warning: unused variable &#8216;Tx1FinePowerCtrl&#8217; [-Wunused-variable]  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../chips/rt30xx.c:632:8: warning: unused variable &#8216;Tx0FinePowerCtrl&#8217; [-Wunused-variable]  
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../chips/rt33xx.o 
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../chips/rt33xx.c: In function &#8216;RT33xxSetRxAnt&#8217;:  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../chips/rt33xx.c:95:9: warning: unused variable &#8216;x&#8217; [-Wunused-variable]  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../chips/rt33xx.c: In function &#8216;RT33xx_ChipSwitchChannel&#8217;:  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../chips/rt33xx.c:337:17: warning: unused variable &#8216;BbpR109&#8217; [-Wunused-variable]  
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../chips/rt3370.o 
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../chips/rt3370.c: In function &#8216;NICInitRT3370RFRegisters&#8217;:  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../chips/rt3370.c:51:7: warning: unused variable &#8216;bbpreg&#8217; [-Wunused-variable]  
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../chips/rt5390.o 
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../chips/rt5390.c: In function &#8216;RT5390_Init&#8217;:  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../chips/rt5390.c:490:25: warning: assignment makes integer from pointer without a cast [enabled by default]  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../chips/rt5390.c: In function &#8216;RT5390LoadRFSleepModeSetup&#8217;:  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../chips/rt5390.c:873:8: warning: unused variable &#8216;RFValue&#8217; [-Wunused-variable]  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../chips/rt5390.c: In function &#8216;RT5390ReverseRFSleepModeSetup&#8217;:  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../chips/rt5390.c:949:8: warning: unused variable &#8216;RFValue&#8217; [-Wunused-variable]  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../chips/rt5390.c: In function &#8216;RT5390_ChipSwitchChannel&#8217;:  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../chips/rt5390.c:1475:17: warning: unused variable &#8216;BbpR110&#8217; [-Wunused-variable]  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../chips/rt5390.c:1474:23: warning: unused variable &#8216;BbpR109&#8217; [-Wunused-variable]  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../chips/rt5390.c: In function &#8216;GetDesiredTssiAndCurrentTssi&#8217;:  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../chips/rt5390.c:3046:2: warning: missing braces around initializer [-Wmissing-braces]  
 /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../chips/rt5390.c:3046:2: warning: (near initialization for &#8216;htTssiInfo.PartA.field&#8217;) [-Wmissing-braces]  
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../common/rtusb_dev_id.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../os/linux/rt_usb_util.o 
   CC [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/../../os/linux/usb_main_dev.o 
   LD [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/rt5370sta.o 
   Building modules, stage 2.  
   MODPOST 1 modules  
 WARNING: modpost: missing MODULE_LICENSE() in /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/rt5370sta.o 
 see include/linux/module.h for more information  
   CC      /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/rt5370sta.mod.o 
   LD [M]  /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/rt5370sta.ko 
 make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-16-generic'  
 cp -f /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/rt5370sta.ko /tftpboot  
 antoine@Oran-Toine:~/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO$ sudo make install  
 make -C /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux -f Makefile.6 install  
 make[1]: Entering directory `/home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux' 
 rm -rf /etc/Wireless/RT2870STA  
 mkdir /etc/Wireless/RT2870STA  
 cp /home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/RT2870STA.dat /etc/Wireless/RT2870STA/.  
 install -d /lib/modules/3.0.0-16-generic/kernel/drivers/net/wireless/  
 install -m 644 -c rt5370sta.ko /lib/modules/3.0.0-16-generic/kernel/drivers/net/wireless/  
 /sbin/depmod -a 3.0.0-16-generic  
 make[1]: Leaving directory `/home/antoine/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux' 
 antoine@Oran-Toine:~/angepasster_2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO$ 

```
After the reboot:

```

Code:
antoine@Oran-Toine:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

antoine@Oran-Toine:~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
ppdev                  12849  0 
snd_hda_codec_realtek   254125  1 
psmouse                73673  0 
serio_raw              12990  0 
parport_pc             32114  1 
binfmt_misc            17292  1 
snd_hda_intel          24262  4 
snd_hda_codec          91859  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  509519  3 
snd                    55902  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
soundcore              12600  1 snd
video                  18908  1 i915
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
floppy                 60310  0 
atl2                   27979  0 
antoine@Oran-Toine:~$ sudo iwlist scan
[sudo] password for antoine: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

antoine@Oran-Toine:~$ 
antoine@Oran-Toine:~$ dmesg | grep rt5
[   27.164116] rt5370sta: module license 'unspecified' taints kernel.
[   27.165525] rt5370sta: Unknown symbol usb_alloc_urb (err 0)
[   27.165543] rt5370sta: Unknown symbol usb_free_urb (err 0)
[   27.165569] rt5370sta: Unknown symbol usb_alloc_coherent (err 0)
[   27.165601] rt5370sta: Unknown symbol usb_register_driver (err 0)
[   27.165656] rt5370sta: Unknown symbol usb_put_dev (err 0)
[   27.165673] rt5370sta: Unknown symbol usb_get_dev (err 0)
[   27.165691] rt5370sta: Unknown symbol usb_submit_urb (err 0)
[   27.165718] rt5370sta: Unknown symbol usb_free_coherent (err 0)
[   27.165746] rt5370sta: Unknown symbol usb_control_msg (err 0)
[   27.165779] rt5370sta: Unknown symbol usb_deregister (err 0)
[   27.165828] rt5370sta: Unknown symbol usb_kill_urb (err 0)
```

---

### Post by praseodym on 2012-02-19
So it does not work. Uninstall it via:

```
sudo make uninstall
sudo depmod -a
```
and try to add the device ID to the driver rt2800usb (this is one line, you better copy/paste it):

```
echo 'install rt2800usb modprobe --ignore-install rt2800usb ; /bin/echo "148f 5370" > /sys/bus/usb/drivers/rt2800usb/new_id' | sudo tee /etc/modprobe.d/rt2800usb.conf
```
(Re)load the driver

```
sudo modprobe -v rt2800usb
```
and replug the stick. Check:
```
lsmod
iwconfig
sudo iwlist scan
dmesg | grep rt28
```

---

### Post by oldfred on 2012-02-19
Please use code tags to make any long listing easier to read. You can highlight and click on the # in the edit panel above you post or advanced mode if editing.

---

### Post by Twon10 on 2012-02-19
[URL="http://ubuntuforums.org/member.php?u=1411497"]praseodym Thanks it worked that time! _:popcorn::D_
[/URL]

---

### Post by CrusaderAD on 2012-05-07
> **praseodym said:**
> 
add the device ID to the driver rt2800usb (this is one line, you better copy/paste it):

```
echo 'install rt2800usb modprobe --ignore-install rt2800usb ; /bin/echo "148f 5370" > /sys/bus/usb/drivers/rt2800usb/new_id' | sudo tee /etc/modprobe.d/rt2800usb.conf
```
(Re)load the driver

```
sudo modprobe -v rt2800usb
```
and replug the stick. Check:
```
lsmod
iwconfig
sudo iwlist scan
dmesg | grep rt28
```

This worked for me without any other configuration. Thanks!

---

