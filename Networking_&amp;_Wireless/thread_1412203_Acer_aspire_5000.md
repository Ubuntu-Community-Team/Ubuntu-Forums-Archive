---
title: "Acer aspire 5000"
date: 2010-02-20
forum: Networking &amp; Wireless
---

### Post by traum313 on 2010-02-20
I can't get my wireless card to work. I downloaded a broadcom driver for it and i do believe its the right one, but its not helped. If some one wouldnt mind helping me out with it a little bit it would be much appreciated.
I'm running mint 8. 
The information on my internal wireless card i got using the terminal is:
lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

---

### Post by northd_tech on 2010-02-20
That's a Broadcom 4318 wireless, and I believe that the proprietary "b43" wireless driver was the best solution for those (my Broadcom "4328" wireless prefers the Broadcom STA driver).  Did you download that from Broadcom's website, or was it from one of the ubuntu repositories, or using Synaptic Package Manager (if Mint has that), or ??

If you search this forum for "broadcom 4318" you should find several threads:

[http://ubuntuforums.org/tags.php?tag=broadcom+4318](http://ubuntuforums.org/tags.php?tag=broadcom+4318)

You also might want to watch/post on this recent thread:

[http://ubuntuforums.org/showthread.php?t=1412151](http://ubuntuforums.org/showthread.php?t=1412151)

edit:  You will want to remember that Linux Mint is a derivative of Ubuntu, not ubuntu *per se* (and Mint 8 is the newest one), so the solutions might be somewhat different for yours.  I and a relative gave up on wireless under Mint 6 (but his wireless still isn't working under Ubuntu Karmic Koala 9.10 either- it's a real %$&# of a 64-bit wireless card).

---

### Post by DaRCNoob on 2010-04-05
Well I'm a Linux / Ubuntu newbie using Ubuntu Karmic.  I've tried the B43* solution and the Ndiswrapper solution - but can't work out what's missing from the puzzle to get it working.   I'm running it dual partitioned with windoze - on win the wifi works which is how I can post here so I can use it to download things to the USB drive and then load them into the Ubuntu partition. I'm not sure where to go next....

Here's the output from various commands:
	 	 
 darc@ubuntu:~$ lsmod  
 Module                  Size  Used by  
 nls_utf8                1568  1  
 isofs                  31620  1  
 binfmt_misc             8356  1  
 ppdev                   6688  0  
 snd_intel8x0           30168  2  
 snd_ac97_codec        101216  1 snd_intel8x0  
 ac97_bus                1532  1 snd_ac97_codec  
 snd_pcm_oss            37920  0  
 iptable_filter          3100  0  
 snd_mixer_oss          16028  1 snd_pcm_oss  
 ip_tables              11692  1 iptable_filter  
 snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss  
 x_tables               16544  1 ip_tables  
 snd_seq_dummy           2656  0  
 snd_seq_oss            28576  0  
 snd_seq_midi            6432  0  
 snd_rawmidi            22208  1 snd_seq_midi  
 snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi  
 snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event  
 joydev                 10272  0  
 ndiswrapper           185404  0  
 snd_timer              22276  2 snd_pcm,snd_seq  
 pcmcia                 36808  0  
 snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq  
 psmouse                56180  0  
 lp                      8964  0  
 yenta_socket           24200  1  
 snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 rsrc_nonstatic         11644  1 yenta_socket  
 soundcore               7264  1 snd  
 led_class               4096  0  
 i2c_sis96x              3904  0  
 serio_raw               5280  0  
 k8temp                  4188  0  
 pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic  
 shpchp                 32272  0  
 parport                35340  2 ppdev,lp  
 snd_page_alloc          9156  2 snd_intel8x0,snd_pcm  
 nls_iso8859_1           3740  2  
 nls_cp437               5372  2  
 vfat                   10716  2  
 fat                    51452  1 vfat  
 usb_storage            52544  2  
 sis_agp                 6972  0  
 sis900                 19932  0  
 mii                     5212  1 sis900  
 ssb                    35300  0  
 amd64_agp               9796  1  
 agpgart                34988  2 sis_agp,amd64_agp  
 darc@ubuntu:~$ sudo lshw -C network  
   *-network:0              
        description: Ethernet interface  
        product: SiS900 PCI Fast Ethernet  
        vendor: Silicon Integrated Systems [SiS]  
        physical id: 4  
        bus info: pci@0000:00:04.0  
        logical name: eth0  
        version: 91  
        serial: 00:16:36:47:d3:72  
        size: 10MB/s  
        capacity: 100MB/s  
        width: 32 bits  
        clock: 33MHz  
        capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=173 link=no maxlatency=11 mingnt=52 multicast=yes port=MII speed=10MB/s  
        resources: irq:19 ioport:1800(size=256) memory:e2005000-e2005fff memory:28000000-2801ffff(prefetchable)  
   *-network:1  
        description: Network controller  
        product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller  
        vendor: Broadcom Corporation  
        physical id: b  
        bus info: pci@0000:00:0b.0  
        version: 02  
        width: 32 bits  
        clock: 33MHz  
        capabilities: bus_master  
        configuration: driver=b43-pci-bridge latency=64  
        resources: irq:17 memory:e2000000-e2001fff  
 darc@ubuntu:~$ ifconfig 
 eth0      Link encap:Ethernet  HWaddr 00:16:36:47:d3:72   
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:19 Base address:0x1800  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
 

 darc@ubuntu:~$ iwconfig 
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 darc@ubuntu:~$ sudo iwlist scan  
 lo        Interface doesn't support scanning.  
 

 eth0      Interface doesn't support scanning.  
 

 darc@ubuntu:~$ sudo cat /var/log/messages | grep firm  
 Apr  3 15:25:32 ubuntu kernel: [   27.744041] b43 ssb0:0: firmware: requesting b43/ucode5.fw 
 Apr  3 15:25:32 ubuntu firmware.sh[1069]: Cannot find  firmware file 'b43/ucode5.fw'  
 Apr  3 15:25:32 ubuntu kernel: [   27.784068] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw  
 Apr  3 15:25:32 ubuntu firmware.sh[1075]: Cannot find  firmware file 'b43-open/ucode5.fw'  
 Apr  3 15:25:33 ubuntu firmware.sh[1095]: Cannot find  firmware file 'b43/ucode5.fw'  
 Apr  3 15:25:33 ubuntu kernel: [   28.400038] b43 ssb0:0: firmware: requesting b43/ucode5.fw 
 Apr  3 15:25:33 ubuntu kernel: [   28.406637] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw  
 Apr  3 15:25:33 ubuntu firmware.sh[1105]: Cannot find  firmware file 'b43-open/ucode5.fw'  
 Apr  3 15:50:03 ubuntu kernel: [   15.516103] b43 ssb0:0: firmware: requesting b43/ucode5.fw 
 Apr  3 15:50:03 ubuntu kernel: [   15.652880] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw  
 Apr  3 15:50:03 ubuntu firmware.sh[901]: Cannot find  firmware file 'b43/ucode5.fw'  
 Apr  3 15:50:03 ubuntu firmware.sh[984]: Cannot find  firmware file 'b43-open/ucode5.fw'  
 Apr  3 15:50:05 ubuntu kernel: [   17.558130] b43 ssb0:0: firmware: requesting b43/ucode5.fw 
 Apr  3 15:50:05 ubuntu firmware.sh[1131]: Cannot find  firmware file 'b43/ucode5.fw'  
 Apr  3 15:50:05 ubuntu kernel: [   17.562650] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw  
 Apr  3 15:50:05 ubuntu firmware.sh[1137]: Cannot find  firmware file 'b43-open/ucode5.fw'  
 Apr  3 18:20:07 ubuntu kernel: [   20.788071] b43 ssb0:0: firmware: requesting b43/ucode5.fw 
 Apr  3 18:20:07 ubuntu kernel: [   20.791966] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw  
 Apr  3 18:20:08 ubuntu firmware.sh[1116]: Cannot find  firmware file 'b43/ucode5.fw'  
 Apr  3 18:20:08 ubuntu firmware.sh[1122]: Cannot find  firmware file 'b43-open/ucode5.fw'  
 Apr  3 18:20:08 ubuntu firmware.sh[1148]: Cannot find  firmware file 'b43/ucode5.fw'  
 Apr  3 18:20:08 ubuntu kernel: [   21.352040] b43 ssb0:0: firmware: requesting b43/ucode5.fw 
 Apr  3 18:20:08 ubuntu firmware.sh[1154]: Cannot find  firmware file 'b43-open/ucode5.fw'  
 Apr  3 18:20:08 ubuntu kernel: [   21.357349] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw  
 Apr  3 18:43:25 ubuntu kernel: [   18.161399] b43 ssb0:0: firmware: requesting b43/ucode5.fw 
 Apr  3 18:43:25 ubuntu kernel: [   18.216711] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw  
 Apr  3 18:43:25 ubuntu firmware.sh[1154]: Cannot find  firmware file 'b43/ucode5.fw'  
 Apr  3 18:43:25 ubuntu firmware.sh[1160]: Cannot find  firmware file 'b43-open/ucode5.fw'  
 Apr  3 18:43:26 ubuntu kernel: [   18.880081] b43 ssb0:0: firmware: requesting b43/ucode5.fw 
 Apr  3 18:43:26 ubuntu firmware.sh[1181]: Cannot find  firmware file 'b43/ucode5.fw'  
 Apr  3 18:43:26 ubuntu kernel: [   18.884276] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw  
 Apr  3 18:43:26 ubuntu firmware.sh[1188]: Cannot find  firmware file 'b43-open/ucode5.fw'  
 darc@ubuntu:~$ dmesg | grep firm  
 darc@ubuntu:~$ ls -al /lib/firmware  
 total 9824  
 drwxr-xr-x  7 root root    4096 2010-04-04 11:03 .  
 drwxr-xr-x 18 root root   12288 2010-04-03 15:23 ..  
 drwxr-xr-x 29 root root    4096 2009-10-28 20:57 2.6.31-14-generic  
 drwxr-xr-x 13 root root    4096 2009-10-28 20:59 acx  
 -rw-r--r--  1 root root   22622 2009-10-17 23:55 aic94xx-seq.fw  
 -rw-r--r--  1 root root   83968 2009-10-17 23:55 ar9170-1.fw  
 -rw-r--r--  1 root root    3508 2009-10-17 23:55 ar9170-2.fw  
 -rw-r--r--  1 root root   15960 2009-10-17 23:55 ar9170.fw  
 -rw-r--r--  1 root root   30348 2009-10-17 23:55 atmel_at76c502_3com.bin  
 -rw-r--r--  1 root root   35184 2009-10-17 23:55 atmel_at76c502_3com-wpa.bin  
 -rw-r--r--  1 root root   31764 2009-10-17 23:55 atmel_at76c502.bin  
 -rw-r--r--  1 root root   31764 2009-10-17 23:55 atmel_at76c502d.bin  
 -rw-r--r--  1 root root   35276 2009-10-17 23:55 atmel_at76c502d-wpa.bin  
 -rw-r--r--  1 root root   31776 2009-10-17 23:55 atmel_at76c502e.bin  
 -rw-r--r--  1 root root   35272 2009-10-17 23:55 atmel_at76c502e-wpa.bin  
 -rw-r--r--  1 root root   35276 2009-10-17 23:55 atmel_at76c502-wpa.bin  
 -rw-r--r--  1 root root   28156 2009-10-17 23:55 atmel_at76c503-i3861.bin  
 -rw-r--r--  1 root root   28032 2009-10-17 23:55 atmel_at76c503-i3863.bin  
 -rw-r--r--  1 root root   35372 2009-10-17 23:55 atmel_at76c503-rfmd-0.90.2-140.bin  
 -rw-r--r--  1 root root   37800 2009-10-17 23:55 atmel_at76c503-rfmd-acc.bin  
 -rw-r--r--  1 root root   37956 2009-10-17 23:55 atmel_at76c503-rfmd.bin  
 -rw-r--r--  1 root root   35180 2009-10-17 23:55 atmel_at76c504_2958-wpa.bin  
 -rw-r--r--  1 root root   39928 2009-10-17 23:55 atmel_at76c504a_2958-wpa.bin  
 -rw-r--r--  1 root root   31748 2009-10-17 23:55 atmel_at76c504.bin  
 -rw-r--r--  1 root root   35196 2009-10-17 23:55 atmel_at76c504c-wpa.bin  
 -rw-r--r--  1 root root   37005 2009-10-17 23:55 atmel_at76c505a-rfmd2958.bin  
 -rw-r--r--  1 root root   36992 2009-10-17 23:55 atmel_at76c505-rfmd2958.bin  
 -rw-r--r--  1 root root   35528 2009-10-17 23:55 atmel_at76c505-rfmd.bin  
 -rw-r--r--  1 root root   31824 2009-10-17 23:55 atmel_at76c506.bin  
 -rw-r--r--  1 root root   35228 2009-10-17 23:55 atmel_at76c506-wpa.bin  
 drwxrwxrwx  2 root root    4096 2010-04-04 11:03 b43  
 drwxrwxrwx  2 root root    4096 2010-04-03 19:55 b43legacy  
 -rw-r--r--  1 root root  114688 2009-10-17 23:55 BCM2033-FW.BIN  
 -rw-r--r--  1 root root    3245 2009-10-17 23:55 BCM2033-MD.BIN  
 -rw-r--r--  1 root root   12401 2009-10-17 23:55 dvb-fe-xc5000-1.6.114.fw  
 -rw-r--r--  1 root root   33768 2009-10-17 23:55 dvb-usb-dib0700-1.20.fw  
 -rw-r--r--  1 root root 1142480 2009-10-17 23:55 i2400m-fw-usb-1.3.sbcf  
 -rw-r--r--  1 root root 1251036 2009-10-17 23:55 i2400m-fw-usb-1.4.sbcf  
 -rw-r--r--  1 root root  209190 2009-10-17 23:55 ipw2100-1.3.fw  
 -rw-r--r--  1 root root  201138 2009-10-17 23:55 ipw2100-1.3-i.fw  
 -rw-r--r--  1 root root  196458 2009-10-17 23:55 ipw2100-1.3-p.fw  
 -rw-r--r--  1 root root  191154 2009-10-17 23:55 ipw2200-bss.fw  
 -rw-r--r--  1 root root  185428 2009-10-17 23:55 ipw2200-ibss.fw  
 -rw-r--r--  1 root root  187836 2009-10-17 23:55 ipw2200-sniffer.fw  
 -rw-r--r--  1 root root  112128 2009-10-17 23:55 isl3877  
 -rw-r--r--  1 root root   29036 2009-10-17 23:55 isl3886pci  
 -rw-r--r--  1 root root   29500 2009-10-17 23:55 isl3886usb  
 -rw-r--r--  1 root root   29736 2009-10-17 23:55 isl3887usb  
 -rw-r--r--  1 root root   93996 2009-10-17 23:55 isl3890  
 -rw-r--r--  1 root root  335056 2009-10-17 23:55 iwlwifi-1000-3.ucode  
 -rw-r--r--  1 root root  149652 2009-10-17 23:55 iwlwifi-3945-1.ucode  
 -rwxr-xr-x  1 root root  150100 2009-10-17 23:55 iwlwifi-3945-2.ucode  
 -rw-r--r--  1 root root  187608 2009-10-17 23:55 iwlwifi-4965-1.ucode  
 -rwxr-xr-x  1 root root  187972 2009-10-17 23:55 iwlwifi-4965-2.ucode  
 -rw-r--r--  1 root root  345008 2009-10-17 23:55 iwlwifi-5000-1.ucode  
 -rw-r--r--  1 root root  353240 2009-10-17 23:55 iwlwifi-5000-2.ucode  
 -rw-r--r--  1 root root  337400 2009-10-17 23:55 iwlwifi-5150-2.ucode  
 -rw-r--r--  1 root root  459992 2009-10-17 23:55 iwlwifi-6000-4.ucode  
 -rw-r--r--  1 root root  118884 2009-10-17 23:55 lbtf_usb.bin  
 lrwxrwxrwx  1 root root      14 2010-04-03 15:13 NPE-B -> NPE-B.01020201  
 -rw-r--r--  1 root root   15664 2009-10-13 20:41 NPE-B.01020201  
 lrwxrwxrwx  1 root root      14 2010-04-03 15:13 NPE-C -> NPE-C.02020201  
 -rw-r--r--  1 root root   15664 2009-10-13 20:41 NPE-C.02020201  
 -rw-r--r--  1 root root   76802 2009-10-17 23:55 ql2100_fw.bin  
 -rw-r--r--  1 root root   84566 2009-10-17 23:55 ql2200_fw.bin  
 -rw-r--r--  1 root root  123170 2009-10-17 23:55 ql2300_fw.bin  
 -rw-r--r--  1 root root  132978 2009-10-17 23:55 ql2322_fw.bin  
 -rw-r--r--  1 root root  206500 2009-10-17 23:55 ql2400_fw.bin  
 -rw-r--r--  1 root root    8192 2009-10-17 23:55 rt2561.bin  
 -rw-r--r--  1 root root    8192 2009-10-17 23:55 rt2561s.bin  
 -rw-r--r--  1 root root    8192 2009-10-17 23:55 rt2661.bin  
 -rw-r--r--  1 root root    8192 2009-10-17 23:55 rt2860.bin  
 -rw-r--r--  1 root root    4096 2009-10-17 23:55 rt2870.bin  
 -rw-r--r--  1 root root    2048 2009-10-17 23:55 rt73.bin  
 -rw-r--r--  1 root root  141200 2009-10-17 23:55 v4l-cx23418-apu.fw  
 -rw-r--r--  1 root root  158332 2009-10-17 23:55 v4l-cx23418-cpu.fw  
 -rw-r--r--  1 root root   16382 2009-10-17 23:55 v4l-cx23418-dig.fw  
 -rw-r--r--  1 root root  262144 2009-10-17 23:55 v4l-cx2341x-dec.fw  
 -rw-r--r--  1 root root  376836 2009-10-17 23:55 v4l-cx2341x-enc.fw  
 -rw-r--r--  1 root root  155648 2009-10-17 23:55 v4l-cx2341x-init.mpg  
 -rw-r--r--  1 root root   16382 2009-10-17 23:55 v4l-cx23885-avcore-01.fw  
 -rw-r--r--  1 root root  376836 2009-10-17 23:55 v4l-cx23885-enc.fw  
 -rw-r--r--  1 root root   16382 2009-10-17 23:55 v4l-cx25840.fw  
 -rw-r--r--  1 root root    8192 2009-10-17 23:55 v4l-pvrusb2-24xxx-01.fw  
 -rw-r--r--  1 root root    8192 2009-10-17 23:55 v4l-pvrusb2-29xxx-01.fw  
 -rw-r--r--  1 root root   62484 2009-10-17 23:55 zd1201-ap.fw  
 -rw-r--r--  1 root root   70612 2009-10-17 23:55 zd1201.fw  
 drwxr-xr-x  2 root root    4096 2009-10-28 20:59 zd1211  
 darc@ubuntu:~$ cat /etc/network/interfaces  
 auto lo  
 iface lo inet loopback  
 

 darc@ubuntu:~$

---

