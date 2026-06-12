---
title: "Unable to Connect to Wirless Network"
date: 2012-06-19
forum: Networking &amp; Wireless
---

### Post by DigitalSR on 2012-06-19
Hello,
 
After changing from Windows 7 I am unable to connect to my router wirelessly, however I can connect fine with a wired connection. After trying to connect I am asked every several minutes for wireless authentication. Any help is greatly appreciated.

lspci

```

 00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09) 
 00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) 
 00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04) 
 00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05) 
 00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05) 
 00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5) 
 00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5) 
 00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5) 
 00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5) 
 00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05) 
 00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05) 
 00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05) 
 00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05) 
 02:00.0 Network controller: Intel Corporation Centrino Wireless-N + WiMAX 6150 (rev 67) 
 03:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller 
 04:00.0 Ethernet controller: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet (rev c0) 
    
```iwconfig

```

                                  wlan0     IEEE 802.11bg  ESSID:off/any   
           Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off 
           Power Management:off 
            
 eth0      no wireless extensions. 
  
```lsmod

```

                                  Module                  Size  Used by 
 parport_pc             32866  0  
 ppdev                  17113  0  
 lp                     17799  0  
 parport                46562  3 parport_pc,ppdev,lp 
 rfcomm                 47604  0  
 bnep                   18281  2  
 bluetooth             180104  10 rfcomm,bnep 
 snd_hda_codec_hdmi     32474  1  
 snd_hda_codec_realtek   223867  1  
 joydev                 17693  0  
 i915                  468651  3  
 drm_kms_helper         46978  1 i915 
 drm                   242038  4 i915,drm_kms_helper 
 arc4                   12529  2  
 asus_nb_wmi            12710  0  
 asus_wmi               24456  1 asus_nb_wmi 
 sparse_keymap          13890  1 asus_wmi 
 snd_hda_intel          33773  3  
 snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel 
 snd_hwdep              13668  1 snd_hda_codec 
 snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec 
 i2c_algo_bit           13423  1 i915 
 snd_seq_midi           13324  0  
 uvcvideo               72627  0  
 videodev               98259  1 uvcvideo 
 v4l2_compat_ioctl32    17128  1 videodev 
 snd_rawmidi            30748  1 snd_seq_midi 
 snd_seq_midi_event     14899  1 snd_seq_midi 
 snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event 
 snd_timer              29990  2 snd_pcm,snd_seq 
 snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq 
 video                  19596  1 i915 
 wmi                    19256  1 asus_wmi 
 mac_hid                13253  0  
 iwlwifi               328352  0  
 snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 mac80211              506816  1 iwlwifi 
 psmouse                87603  0  
 serio_raw              13211  0  
 mei                    41616  0  
 cfg80211              205544  2 iwlwifi,mac80211 
 soundcore              15091  1 snd 
 snd_page_alloc         18529  2 snd_hda_intel,snd_pcm 
 atl1c                  41717  0  
 
```sudo lshw -c network


```

                                   
                                   
 description: Wireless interface 
        product: Centrino Wireless-N + WiMAX 6150 
        vendor: Intel Corporation 
        physical id: 0 
        bus info: pci@0000:02:00.0 
        logical name: wlan0 
        version: 67 
        serial: 40:25:c2:51:9f:cc 
        width: 64 bits 
        clock: 33MHz 
        capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
        configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-23-generic firmware=41.28.5.1 build 33926 latency=0 link=no multicast=yes wireless=IEEE 802.11bg 
        resources: irq:51 memory:de800000-de801fff 
   *-network 
        description: Ethernet interface 
        product: AR8151 v2.0 Gigabit Ethernet 
        vendor: Atheros Communications Inc. 
        physical id: 0 
        bus info: pci@0000:04:00.0 
        logical name: eth0 
        version: c0 
        serial: 14:da:e9:50:a8:b1 
        size: 1Gbit/s 
        capacity: 1Gbit/s 
        width: 64 bits 
        clock: 33MHz 
        capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation 
        configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.0.18 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s 
        resources: irq:54 memory:dd400000-dd43ffff ioport:a000(size=128) 


```Thank you.

---

### Post by wildmanne39 on 2012-06-23
Hi, please do:
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
if that does not help post the output of:
```
nm-tool
```
```
sudo cat /var/log/syslog | grep -e iwl -e firmware -e wpa -e wlan -e etork | tail -n75
```
Thanks

---

