---
title: "Toshiba NB 510 WLAN difficulties installing Ubuntu 12.04: connects then disconnects"
date: 2012-10-17
forum: Networking &amp; Wireless
---

### Post by Jshickm1 on 2012-10-17
Hey all,
Was forced to buy a PC in Spain, and windows 7 came installed in Spanish, so I downloaded Ubuntu 12.04 desktop. I have been booting it from a USB, and want to have an Internet connection when installing so that drivers/ect. install properly. Initially my WLAN prompts me for my password, then when entered it connects, but only for 3 to 5 minutes. Afterwards it continues trying to connect but to no avail, and continually prompts me for my password. Not sure if this is common and I should simply buy an ethernet to install while connected so that wireless drivers all install, or if I should be able to be connected instantly.

I'm not particularly computer savvy, but will be more than happy to copy and paste terminal output if anybody can guide me to what I should be entering in. Have checked troubleshoots and FAQs but have difficulty understanding when problems discussed are relevant to my own.

Thanks for the help.

---

### Post by Jshickm1 on 2012-10-18
Have now installed 12.04 onto the hard drive, but with no internet connection. I plan to download updates manually once I get connected, however, I have now tried an unencrypted wireless network along with booting while connected to my router with an ethernet cable; none stay connected for more than 5 minutes.

Will post ifconfig, iwconfig, ect. terminal output later on today, but since I cannot connect I have to painstakingly type it in all by hand to another computer, which is why I was reluctant to do so initially. Help will be greatly, greatly appreciated once I do so.

Thanks again

---

### Post by Jshickm1 on 2012-10-18
Ok I got some terminal outputs, also I downloaded all of the Ubuntu software updates but still cannot stay connected to wireless. Not sure if I formatted these correctly but here goes:

lspci

```


  	 	 	 	 	 	   00:00.0 Host bridge: Intel Corporation Atom Processor D2xxx/N2xxx DRAM Controller (rev 03)  
 00:02.0 VGA compatible controller: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller (rev 09)  
 00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)  
 00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)  
 00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)  
 00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)  
 00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)  
 00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)  
 00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)  
 00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)  
 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)  
 00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)  
 00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA Controller [AHCI mode] (rev 02)  
 00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)  
 01:00.0 Ethernet controller: Atheros Communications Inc. AR8162 Fast Ethernet (rev 10)  
 02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)  
  

```

iwconfig

```


  	 	 	 	 	 	   lo        no wireless extensions.  
 

 wlan0     IEEE 802.11bgn  ESSID:"WLAN_0E"   
           Mode:Managed  Frequency:2.452 GHz  Access Point: 40:4A:03:C0:62:35    
           Bit Rate=54 Mb/s   Tx-Power=20 dBm    
           Retry  long limit:7   RTS thr=2347 B   Fragment thr:off  
           Power Management:off  
           Link Quality=63/70  Signal level=-47 dBm   
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0  
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0  
 

 
```


lsmod


```



   	 	 	 	 	 	   
Module                  Size  Used by  
 joydev                 17393  0  
 rfcomm                 38139  0  
 bnep                   17830  2  
 parport_pc             32114  0  
 bluetooth             158438  10 rfcomm,bnep  
 ppdev                  12849  0  
 arc4                   12473  2  
 cedarview_gfx         381322  2  
 snd_hda_codec_realtek   174222  1  
 snd_hda_codec_hdmi     31775  1  
 rtl8192ce              75491  0  
 rtl8192c_common        69519  1 rtl8192ce  
 uvcvideo               67203  0  
 rtlwifi                95804  1 rtl8192ce  
 snd_hda_intel          32765  3  
 mac80211              436455  3 rtl8192ce,rtl8192c_common,rtlwifi  
 videodev               86588  1 uvcvideo  
 snd_hda_codec         109562  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel  
 ttm                    64734  1 cedarview_gfx  
 snd_hwdep              13276  1 snd_hda_codec  
 snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec  
 drm_kms_helper         32561  1 cedarview_gfx  
 psmouse                72919  0  
 serio_raw              13027  0  
 snd_seq_midi           13132  0  
 cfg80211              178679  2 rtlwifi,mac80211  
 snd_rawmidi            25424  1 snd_seq_midi  
 drm                   196349  3 cedarview_gfx,ttm,drm_kms_helper  
 snd_seq_midi_event     14475  1 snd_seq_midi  
 i2c_algo_bit           13199  1 cedarview_gfx  
 snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event  
 snd_timer              28931  2 snd_pcm,snd_seq  
 snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq  
 video                  19068  1 cedarview_gfx  
 snd                    62064  16 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 soundcore              14635  1 snd  
 mac_hid                13077  0  
 snd_page_alloc         14108  2 snd_hda_intel,snd_pcm  
 lp                     17455  0  
 parport                40930  3 parport_pc,ppdev,lp  
 ums_realtek            17920  0  
 uas                    17828  0  
 usb_storage            39646  1 ums_realtek 




```


sudo lshw -C network


```



   	 	 	 	 	 	   
  *-network UNCLAIMED      
        description: Ethernet controller 
        product: AR8162 Fast Ethernet  
        vendor: Atheros Communications Inc.  
        physical id: 0  
        bus info: pci@0000:01:00.0  
        version: 10  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm pciexpress msi msix bus_master cap_list  
        configuration: latency=0  
        resources: memory:43000000-4303ffff ioport:3000(size=128)  
   *-network  
        description: Wireless interface  
        product: RTL8188CE 802.11b/g/n WiFi Adapter  
        vendor: Realtek Semiconductor Co., Ltd.  
        physical id: 0  
        bus info: pci@0000:02:00.0  
        logical name: wlan0  
        version: 01  
        serial: 44:6d:57:fd:81:59  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi bus_master cap_list ethernet physical wireless  
        configuration: broadcast=yes driver=rtl8192ce driverversion=3.2.0-29-generic-pae firmware=N/A ip=192.168.1.38 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn  
        resources: irq:17 ioport:2000(size=256) memory:42000000-42003fff 




```


iwlist scan


```



   	 	 	 	 	 	   
lo        Interface doesn't support scanning.  
 

 wlan0     Scan completed :  
           Cell 01 - Address: 40:4A:03:C0:62:35  
                     Channel:9  
                     Frequency:2.452 GHz (Channel 9)  
                     Quality=63/70  Signal level=-47 dBm   
                     Encryption key:on  
                     ESSID:"WLAN_0E" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s  
                     Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s  
                               36 Mb/s; 48 Mb/s; 54 Mb/s  
                     Mode:Master  
                     Extra:tsf=000000678f8ab1c3  
                     Extra: Last beacon: 135832ms ago  
                     IE: Unknown: 0007574C414E5F3045  
                     IE: Unknown: 010582848B962C  
                     IE: Unknown: 030109 
                     IE: Unknown: 2A0100 
                     IE: Unknown: 32080C1218243048606C  
 

  
```

---

