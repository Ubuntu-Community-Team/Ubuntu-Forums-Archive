---
title: "Wifi Appears to be Connected, but Internet Not Working"
date: 2013-02-21
forum: Networking &amp; Wireless
---

### Post by Experimental Manatee on 2013-02-21
Setup::  desktop, Dell Inspiron 530
 

 OS::  Ubuntu 12.04
 

 Wifi::  usb Rosewill RNX-150ube (I think the driver = r8712u)
 

 Problem::  Wifi appears to work (full signal), but cannot connect to internet
 

 Attempted Solutions (that failed):::::   
 sudo gedit /etc/modprobe.d/r8712u.conf
 options r8712u 11n_disable=1
 

 sudo gedit /etc/modprobe.d/iwlwifi.conf
 options iwlwifi 11n_disable=1
 

 Situation::  Wifi has been working for 2 months; went into suspend couple of days ago, and upon returning from suspend, wifi quit working, even after reboot.
 

 Note#1::  (perhaps unrelated) after suspend, I have to unplug and replug my wifi usb; but this no longer is effective; and the fact that wifi doesn't work even after reboot is a completely new problem.
 

 Note#2::  I have two installations of 12.04 on this computer.  The internet still works on the other installation.  So, if it would help, I can provide the terminal output for the installation that doesn't have an internet problem.
 

 Terminal Output::::::::
 .....for iwconfig  
 

 

 lo        no wireless extensions. 
  
 wlan0     IEEE 802.11bgn  ESSID:"Sandwich Log"  Nickname:"rtl_wifi" 
           Mode:Managed  Frequency:2.462 GHz  Access Point: 00:24:01:7B:7D:58    
           Bit Rate:150 Mb/s   Sensitivity:0/0   
           Retry:off   RTS thr:off   Fragment thr:off 
           Power Management:off 
           Link Quality=100/100  Signal level=73/100  Noise level=0/100 
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
  
 eth0      no wireless extensions. 
 

 

 .....for ifconfig
 

 

 eth0      Link encap:Ethernet  HWaddr 00:1d:09:92:56:db   
           inet addr:192.168.0.14  Bcast:192.168.0.255  Mask:255.255.255.0 
           inet6 addr: fe80::21d:9ff:fe92:56db/64 Scope:Link 
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:8091 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:6667 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:7401524 (7.4 MB)  TX bytes:1084224 (1.0 MB) 
           Interrupt:20 Memory:fdfc0000-fdfe0000  
  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0 
           inet6 addr: ::1/128 Scope:Host 
           UP LOOPBACK RUNNING  MTU:16436  Metric:1 
           RX packets:1478 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:1478 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:0  
           RX bytes:219401 (219.4 KB)  TX bytes:219401 (219.4 KB) 
  
 wlan0     Link encap:Ethernet  HWaddr 68:1c:a2:04:07:db   
           inet addr:192.168.0.15  Bcast:192.168.0.255  Mask:255.255.255.0 
           inet6 addr: fe80::6a1c:a2ff:fe04:7db/64 Scope:Link 
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:11 errors:0 dropped:1 overruns:0 frame:0 
           TX packets:43 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:4406 (4.4 KB)  TX bytes:9890 (9.8 KB) 
 

 

 .....for lsmod
 

 

 Module                  Size  Used by 
 e1000e                139997  0  
 btrfs                 638248  0  
 zlib_deflate           26622  1 btrfs 
 libcrc32c              12543  1 btrfs 
 ufs                    78131  0  
 qnx4                   13309  0  
 hfsplus                83544  0  
 hfs                    49479  0  
 minix                  31453  0  
 ntfs                  100206  0  
 vfat                   17308  0  
 msdos                  17132  0  
 fat                    55605  2 vfat,msdos 
 jfs                   175085  0  
 xfs                   747494  0  
 reiserfs              230943  0  
 ext2                   67987  0  
 pci_stub               12550  1  
 vboxpci                22911  0  
 vboxnetadp             13328  0  
 vboxnetflt             27240  0  
 vboxdrv               252188  3 vboxpci,vboxnetadp,vboxnetflt 
 bnep                   17830  2  
 rfcomm                 38139  0  
 bluetooth             158479  10 bnep,rfcomm 
 parport_pc             32114  0  
 ppdev                  12849  0  
 binfmt_misc            17292  1  
 snd_hda_codec_realtek   174313  1  
 joydev                 17393  0  
 snd_hda_intel          32765  2  
 snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel 
 snd_hwdep              13276  1 snd_hda_codec 
 r8712u                163880  0  
 dcdbas                 14098  0  
 snd_pcm                80916  2 snd_hda_intel,snd_hda_codec 
 wacom                  51812  0  
 snd_seq_midi           13132  0  
 snd_rawmidi            25424  1 snd_seq_midi 
 snd_seq_midi_event     14475  1 snd_seq_midi 
 snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event 
 snd_timer              28931  2 snd_pcm,snd_seq 
 snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq 
 snd                    62218  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 psmouse                86520  0  
 serio_raw              13027  0  
 mac_hid                13077  0  
 i915                  419297  3  
 drm_kms_helper         45466  1 i915 
 drm                   197641  4 i915,drm_kms_helper 
 soundcore              14635  1 snd 
 i2c_algo_bit           13199  1 i915 
 snd_page_alloc         14108  2 snd_hda_intel,snd_pcm 
 video                  19068  1 i915 
 lp                     17455  0  
 parport                40930  3 parport_pc,ppdev,lp 
 usbhid                 41937  0  
 hid                    77428  1 usbhid 
 firewire_ohci          40172  0  
 firewire_core          56940  1 firewire_ohci 
 crc_itu_t              12627  1 firewire_core 
 floppy                 60184  0  
 usb_storage            39646  0  
 

 

 .....for nm-tool
 

 

 NetworkManager Tool 
  
 State: connected (global) 
  
 - Device: wlan0  [Sandwich Log] ------------------------------------------------ 
   Type:              802.11 WiFi 
   Driver:            r8712u 
   State:             connected 
   Default:           no 
   HW Address:        68:1C:A2:04:07:DB 
  
   Capabilities: 
     Speed:           150 Mb/s 
  
   Wireless Properties 
     WEP Encryption:  yes 
     WPA Encryption:  yes 
     WPA2 Encryption: yes 
  
   Wireless Access Points (* = current AP) 
     2WIRE439:        Infra, B8:E6:25:19:54:31, Freq 2432 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2 
     2WIRE386:        Infra, B8:E6:25:43:43:51, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2 
     2WIRE473:        Infra, 74:9D:DC:9F:FB:49, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2 
     *Sandwich Log:   Infra, 00:24:01:7B:7D:58, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 
  
   IPv4 Settings: 
     Address:         192.168.0.15 
     Prefix:          24 (255.255.255.0) 
     Gateway:         192.168.0.1 
  
     DNS:             192.168.0.1 
  
  
 - Device: eth0  [Wired connection 1] ------------------------------------------- 
   Type:              Wired 
   Driver:            e1000e 
   State:             connected 
   Default:           yes 
   HW Address:        00:1D:09:92:56:DB 
  
   Capabilities: 
     Carrier Detect:  yes 
     Speed:           100 Mb/s 
  
   Wired Properties 
     Carrier:         on 
  
   IPv4 Settings: 
     Address:         192.168.0.14 
     Prefix:          24 (255.255.255.0) 
     Gateway:         192.168.0.1 
  
     DNS:             192.168.0.1 
 

 

 .....for sudo lshw -C network
 

 

   *-network                
        description: Ethernet interface 
        product: 82562V-2 10/100 Network Connection 
        vendor: Intel Corporation 
        physical id: 19 
        bus info: pci@0000:00:19.0 
        logical name: eth0 
        version: 02 
        serial: 00:1d:09:92:56:db 
        size: 100Mbit/s 
        capacity: 100Mbit/s 
        width: 32 bits 
        clock: 33MHz 
        capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
        configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k duplex=full firmware=1.1-2 ip=192.168.0.14 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s 
        resources: irq:43 memory:fdfc0000-fdfdffff memory:fdfff000-fdffffff ioport:fe00(size=32) 
   *-network 
        description: Wireless interface 
        physical id: 1 
        bus info: usb@1:5.4 
        logical name: wlan0 
        serial: 68:1c:a2:04:07:db 
        capabilities: ethernet physical wireless 
        configuration: broadcast=yes driver=r8712u ip=192.168.0.15 multicast=yes wireless=IEEE 802.11bgn

---

