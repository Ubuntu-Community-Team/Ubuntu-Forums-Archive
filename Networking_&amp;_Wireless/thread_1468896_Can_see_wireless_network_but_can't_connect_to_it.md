---
title: "Can see wireless network but can't connect to it"
date: 2010-05-01
forum: Networking &amp; Wireless
---

### Post by Didjee on 2010-05-01
Hi,

I have installed Lucid yesterday on my computer but I can't get connected to the wireless network. I have tried many things included installing wicd, using ndiswrapper to get the driver on Windows (computer is on dual-boot).
Now, it still doesn't work and I'm getting quite desperate.

Here is my log as required to get help:

1) Code:

PC desktop
Processor Pentimu Dual-core E5200 @ 2.5GHz
Memory:  3.9 GiB
Release 10.4 (Lucid)
Kernel Linux 2.6.32-21
Gnome 2.30.0

2) Edimax Ew-7717Un USB

Code: 

$ lspci

00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03) 
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03) 
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4 
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5 
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6 
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller 
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1 
00:1c.3 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 4 
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5 
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6 
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1 
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2 
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3 
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90) 
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller 
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1 
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller 
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2 
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8500 GT] (rev a1) 
02:00.0 Ethernet controller: Atheros Communications Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0) 
03:00.0 SATA controller: JMicron Technology Corp. JMB361 AHCI/IDE (rev 02) 
03:00.1 IDE interface: JMicron Technology Corp. JMB361 AHCI/IDE (rev 02) 
04:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. Device 3403 

code:

$ lsusb

Bus 008 Device 002: ID 046d:c509 Logitech, Inc. Cordless Keyboard & Mouse 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 002: ID 099a:7202 Zippy Technology Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 002: ID 148f:2770 Ralink Technology, Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 

3) code:

$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:26:18:90:d6:86  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:14 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:29 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:6080 (6.0 KB)  TX bytes:6080 (6.0 KB) 

$ iwconfig

lo        no wireless extensions. 

eth0      no wireless extensions. 

wlan0     RTxx70 Wireless  ESSID:""  Nickname:"RT3070STA" 
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off 
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

4) Code:

$ lsmod

Module                  Size  Used by 
ndiswrapper           244768  0 
binfmt_misc             7960  1 
ppdev                   6375  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon 
font                    8053  1 fbcon 
bitblit                 5811  1 fbcon 
softcursor              1565  1 bitblit 
vga16fb                12757  0 
vgastate                9857  1 vga16fb 
snd_hda_codec_via      33207  1 
snd_hda_intel          25645  2 
snd_hda_codec          85727  2 snd_hda_codec_via,snd_hda_intel 
snd_hwdep               6924  1 snd_hda_codec 
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss 
snd_pcm                87850  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss 
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  1 snd_seq_midi 
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi 
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
nouveau               515131  2 
snd_timer              23553  2 snd_pcm,snd_seq 
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
ttm                    60815  1 nouveau 
rt2870sta             525366  0 
asus_atk0110           10033  0 
drm_kms_helper         30742  1 nouveau 
joydev                 11072  0 
psmouse                64608  0 
serio_raw               4918  0 
snd                    70978  15 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
ohci1394               30260  0 
drm                   198770  4 nouveau,ttm,drm_kms_helper 
i2c_algo_bit            6024  1 nouveau 
intel_agp              29225  0 
soundcore               8052  1 snd 
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm 
lp                      9336  0 
parport                37160  2 ppdev,lp 
usbhid                 40988  0 
hid                    83376  1 usbhid 
usb_storage            49833  0 
atl1e                  33233  0 
ieee1394               94675  1 ohci1394 
pata_jmicron            2747  0 
ahci                   37646  0 

$ lsmod | grep rt2870

rt2870sta             525366  0 

5) Code:

$ dmesg

[  213.270034] # 
[  213.280034] # 
[  213.300159] # 
[  213.310035] # 
[  213.330035] # 
[  213.340035] # 
[  213.350034] # 
[  213.360035] # 
[  213.370035] # 
[  213.380035] # 
[  213.419922] <-- RTMPAllocTxRxRingMemory, Status=0 
[  213.421536] -->RTUSBVenderReset 
[  213.421660] <--RTUSBVenderReset 
[  213.430036] # 
[  213.440035] # 
[  213.450036] # 
[  213.460162] # 
[  213.470036] # 
[  213.480036] # 
[  213.490036] # 
[  213.500037] # 
[  213.510037] # 
[  213.520037] # 
[  213.530038] # 
[  213.550036] # 
[  213.560037] # 
[  213.570037] # 
[  213.580038] # 
[  213.590038] # 
[  213.600038] # 
[  213.610038] # 
[  213.620038] # 
[  213.630038] # 
[  213.640038] # 
[  213.650039] # 
[  213.660039] # 
[  213.670039] # 
[  213.680040] # 
[  213.690038] # 
[  213.700039] # 
[  213.710039] # 
[  213.720039] # 
[  213.730039] # 
[  213.740040] # 
[  213.750040] # 
[  213.760039] # 
[  213.770040] # 
[  213.780040] # 
[  213.790166] # 
[  213.800041] # 
[  213.810041] # 
[  213.820041] # 
[  213.830040] # 
[  213.840041] # 
[  213.850041] # 
[  213.860041] # 
[  213.870042] # 
[  213.880041] # 
[  213.890042] # 
[  213.900041] # 
[  213.910041] # 
[  213.920042] # 
[  213.930042] # 
[  213.940042] # 
[  213.950043] # 
[  213.960043] # 
[  213.968928] --> Error 2 opening /etc/Wireless/RT3070STA/RT3070STA.dat 
[  213.968932] 1. Phy Mode = 0 
[  213.968935] 2. Phy Mode = 0 
[  213.970170] # 
[  213.980169] # 
[  213.990170] # 
[  214.000044] # 
[  214.010171] # 
[  214.020169] # 
[  214.030044] # 
[  214.038669] 3. Phy Mode = 0 
[  214.042919] MCS Set = 00 00 00 00 00 
[  214.050043] # 
[  214.057173] <==== RTMPInitialize, Status=0 
[  214.058668] 0x1300 = 000a4300 
[  214.336470] usb 1-5: USB disconnect, address 2 
[  216.143550] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1) 
[  216.190068] # 
[  216.210067] # 
[  216.220069] # 
[  216.230069] # 
[  216.250076] # 
[  216.250079] # 
[  216.260070] # 
[  216.270068] # 
[  216.280069] # 
[  216.284870] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 756 
[  216.285051] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1) 
[  216.290069] # 
[  216.300069] # 
[  216.310071] # 
[  216.320071] # 
[  216.330070] # 
[  216.340070] # 
[  216.350071] # 
[  216.360070] # 
[  216.370070] # 
[  217.220079] # 
[  219.061289] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 756 
[  219.220102] # 
[  219.230103] # 
[  220.220113] # 
[  224.970009] wlan0: no IPv6 routers present 
[  226.287890] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 756 
[  226.288015] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1) 
[  226.290059] # 
[  226.300055] # 
[  230.220102] # 
[  231.290114] # 
[  236.295852] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 565 
[  236.295968] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1) 
[  236.300046] # 
[  236.310169] # 
[  238.220068] # 
[  240.220089] # 
[  240.230090] # 
[  246.300518] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 565 
[  246.300642] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1) 
[  246.310033] # 
[  248.230055] # 
[  250.230078] # 
[  254.670264] Terminate the TimerQThr_pid=2397! 
[  254.670286] Terminate the MLMEThr_pid=2395! 
[  254.670295] Terminate the RTUSBCmdThr_pid=2396! 
[  254.676629] ---> RTMPFreeTxRxRingMemory 
[  254.676656] <--- ReleaseAdapter 
[  254.690128] # 
[  254.954124] <-- RTMPAllocTxRxRingMemory, Status=0 
[  254.955630] -->RTUSBVenderReset 
[  254.955755] <--RTUSBVenderReset 
[  255.231147] --> Error 2 opening /etc/Wireless/RT3070STA/RT3070STA.dat 
[  255.231151] 1. Phy Mode = 0 
[  255.231154] 2. Phy Mode = 0 
[  255.260135] # 
[  255.266635] 3. Phy Mode = 0 
[  255.270886] MCS Set = 00 00 00 00 00 
[  255.280140] <==== RTMPInitialize, Status=0 
[  255.281635] 0x1300 = 000a4200 
[  255.890275] Terminate the TimerQThr_pid=2463! 
[  255.890296] Terminate the MLMEThr_pid=2461! 
[  255.890306] Terminate the RTUSBCmdThr_pid=2462! 
[  255.896642] ---> RTMPFreeTxRxRingMemory 
[  255.896666] <--- ReleaseAdapter 
[  255.976887] ATL1E 0000:02:00.0: irq 29 for MSI/MSI-X 
[  255.977849] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[  409.010124] # 
[  409.020125] # 
[  409.030123] # 
[  409.040125] # 
[  409.050125] # 
[  409.080123] # 
[  409.090126] # 
[  409.311728] <-- RTMPAllocTxRxRingMemory, Status=0 
[  409.313251] -->RTUSBVenderReset 
[  409.313379] <--RTUSBVenderReset 
[  409.320131] # 
[  409.593889] --> Error 2 opening /etc/Wireless/RT3070STA/RT3070STA.dat 
[  409.593893] 1. Phy Mode = 0 
[  409.593896] 2. Phy Mode = 0 
[  409.610131] # 
[  409.620133] # 
[  409.635131] 3. Phy Mode = 0 
[  409.639381] MCS Set = 00 00 00 00 00 
[  409.648635] <==== RTMPInitialize, Status=0 
[  409.650134] 0x1300 = 000a4200 
[  411.508173] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 374 
[  420.260009] wlan0: no IPv6 routers present 
[  458.981625] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 565 
[  513.990061] # 
[  518.982363] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 382 
[  573.980118] # 
[  574.260118] # 
[  575.171377] # 
[  578.986187] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 382 
[  614.001322] # 
[  615.953417] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 565 
[  616.621349] Terminate the TimerQThr_pid=2538! 
[  616.621375] Terminate the MLMEThr_pid=2536! 
[  616.621387] Terminate the RTUSBCmdThr_pid=2537! 
[  616.627720] ---> RTMPFreeTxRxRingMemory 
[  616.627746] <--- ReleaseAdapter 
[  616.903411] <-- RTMPAllocTxRxRingMemory, Status=0 
[  616.904971] -->RTUSBVenderReset 
[  616.905097] <--RTUSBVenderReset 
[  617.180858] --> Error 2 opening /etc/Wireless/RT3070STA/RT3070STA.dat 
[  617.180861] 1. Phy Mode = 0 
[  617.180862] 2. Phy Mode = 0 
[  617.209225] 3. Phy Mode = 0 
[  617.213476] MCS Set = 00 00 00 00 00 
[  617.222477] <==== RTMPInitialize, Status=0 
[  617.223975] 0x1300 = 000a4200 
[  617.385837] ATL1E 0000:02:00.0: irq 29 for MSI/MSI-X 
[  617.386373] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[  617.971369] Terminate the TimerQThr_pid=2731! 
[  617.971391] Terminate the MLMEThr_pid=2729! 
[  617.971401] Terminate the RTUSBCmdThr_pid=2730! 
[  617.977735] ---> RTMPFreeTxRxRingMemory 
[  617.977818] <--- ReleaseAdapter 
[  618.293800] <-- RTMPAllocTxRxRingMemory, Status=0 
[  618.295362] -->RTUSBVenderReset 
[  618.295487] <--RTUSBVenderReset 
[  618.510116] # 
[  618.579749] --> Error 2 opening /etc/Wireless/RT3070STA/RT3070STA.dat 
[  618.579751] 1. Phy Mode = 0 
[  618.579752] 2. Phy Mode = 0 
[  618.607367] 3. Phy Mode = 0 
[  618.611617] MCS Set = 00 00 00 00 00 
[  618.620618] <==== RTMPInitialize, Status=0 
[  618.622117] 0x1300 = 000a4200 
[  620.705971] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1) 
[  625.794005] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 565 
[  625.794153] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1) 
[  629.271253] wlan0: no IPv6 routers present 
[  638.981418] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 565 
[  647.800014] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 565 
[  647.800109] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1) 
[  657.806617] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 565 
[  657.806714] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1) 
[  659.681588] Terminate the TimerQThr_pid=2744! 
[  659.681611] Terminate the MLMEThr_pid=2742! 
[  659.681621] Terminate the RTUSBCmdThr_pid=2743! 
[  659.687956] ---> RTMPFreeTxRxRingMemory 
[  659.687984] <--- ReleaseAdapter 
[  659.964886] <-- RTMPAllocTxRxRingMemory, Status=0 
[  659.966459] -->RTUSBVenderReset 
[  659.966583] <--RTUSBVenderReset 
[  660.263473] --> Error 2 opening /etc/Wireless/RT3070STA/RT3070STA.dat 
[  660.263476] 1. Phy Mode = 0 
[  660.263477] 2. Phy Mode = 0 
[  660.290088] 3. Phy Mode = 0 
[  660.294338] MCS Set = 00 00 00 00 00 
[  660.303339] <==== RTMPInitialize, Status=0 
[  660.304838] 0x1300 = 000a4200 
[  660.943483] Terminate the TimerQThr_pid=2810! 
[  660.943507] Terminate the MLMEThr_pid=2808! 
[  660.943518] Terminate the RTUSBCmdThr_pid=2809! 
[  660.949846] ---> RTMPFreeTxRxRingMemory 
[  660.952056] <--- ReleaseAdapter 
[  661.035802] ATL1E 0000:02:00.0: irq 29 for MSI/MSI-X 
[  661.036412] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[  819.268450] <-- RTMPAllocTxRxRingMemory, Status=0 
[  819.270011] -->RTUSBVenderReset 
[  819.270135] <--RTUSBVenderReset 
[  819.545520] --> Error 2 opening /etc/Wireless/RT3070STA/RT3070STA.dat 
[  819.545522] 1. Phy Mode = 0 
[  819.545523] 2. Phy Mode = 0 
[  819.572264] 3. Phy Mode = 0 
[  819.576515] MCS Set = 00 00 00 00 00 
[  819.585517] <==== RTMPInitialize, Status=0 
[  819.587015] 0x1300 = 000a4200 
[  821.643197] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 374 
[  821.824597] Terminate the TimerQThr_pid=2889! 
[  821.824620] Terminate the MLMEThr_pid=2887! 
[  821.824630] Terminate the RTUSBCmdThr_pid=2888! 
[  821.831041] ---> RTMPFreeTxRxRingMemory 
[  821.831068] <--- ReleaseAdapter 
[  822.104859] <-- RTMPAllocTxRxRingMemory, Status=0 
[  822.106418] -->RTUSBVenderReset 
[  822.106542] <--RTUSBVenderReset 
[  822.382680] --> Error 2 opening /etc/Wireless/RT3070STA/RT3070STA.dat 
[  822.382682] 1. Phy Mode = 0 
[  822.382683] 2. Phy Mode = 0 
[  822.409421] 3. Phy Mode = 0 
[  822.413672] MCS Set = 00 00 00 00 00 
[  822.422673] <==== RTMPInitialize, Status=0 
[  822.424172] 0x1300 = 000a4200 
[  822.595886] ATL1E 0000:02:00.0: irq 29 for MSI/MSI-X 
[  822.596456] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[  823.191439] Terminate the TimerQThr_pid=2900! 
[  823.191461] Terminate the MLMEThr_pid=2898! 
[  823.191471] Terminate the RTUSBCmdThr_pid=2899! 
[  823.197806] ---> RTMPFreeTxRxRingMemory 
[  823.197830] <--- ReleaseAdapter 
[  823.504124] <-- RTMPAllocTxRxRingMemory, Status=0 
[  823.505683] -->RTUSBVenderReset 
[  823.505808] <--RTUSBVenderReset 
[  823.790195] --> Error 2 opening /etc/Wireless/RT3070STA/RT3070STA.dat 
[  823.790198] 1. Phy Mode = 0 
[  823.790200] 2. Phy Mode = 0 
[  823.817063] 3. Phy Mode = 0 
[  823.821314] MCS Set = 00 00 00 00 00 
[  823.830314] <==== RTMPInitialize, Status=0 
[  823.831813] 0x1300 = 000a4200 
[  825.896218] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1) 
[  830.983946] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 565 
[  830.984084] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1) 
[  834.121254] wlan0: no IPv6 routers present 
[  840.986792] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 191 
[  840.986865] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1) 
[  850.991280] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 565 
[  850.991375] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1) 
[  860.995779] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 565 
[  860.995871] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1) 
[  864.681408] Terminate the TimerQThr_pid=2913! 
[  864.681430] Terminate the MLMEThr_pid=2911! 
[  864.681440] Terminate the RTUSBCmdThr_pid=2912! 
[  864.687775] ---> RTMPFreeTxRxRingMemory 
[  864.687804] <--- ReleaseAdapter 
[  864.960978] <-- RTMPAllocTxRxRingMemory, Status=0 
[  864.962527] -->RTUSBVenderReset 
[  864.962652] <--RTUSBVenderReset 
[  865.255790] --> Error 2 opening /etc/Wireless/RT3070STA/RT3070STA.dat 
[  865.255793] 1. Phy Mode = 0 
[  865.255794] 2. Phy Mode = 0 
[  865.282657] 3. Phy Mode = 0 
[  865.286907] MCS Set = 00 00 00 00 00 
[  865.295909] <==== RTMPInitialize, Status=0 
[  865.297407] 0x1300 = 000a4200 
[  865.931421] Terminate the TimerQThr_pid=2998! 
[  865.931444] Terminate the MLMEThr_pid=2996! 
[  865.931455] Terminate the RTUSBCmdThr_pid=2997! 
[  865.937789] ---> RTMPFreeTxRxRingMemory 
[  865.937817] <--- ReleaseAdapter 
[  866.035826] ATL1E 0000:02:00.0: irq 29 for MSI/MSI-X 
[  866.036583] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[ 1024.275778] <-- RTMPAllocTxRxRingMemory, Status=0 
[ 1024.277328] -->RTUSBVenderReset 
[ 1024.277453] <--RTUSBVenderReset 
[ 1024.311332] # 
[ 1024.351332] # 
[ 1024.570588] --> Error 2 opening /etc/Wireless/RT3070STA/RT3070STA.dat 
[ 1024.570590] 1. Phy Mode = 0 
[ 1024.570592] 2. Phy Mode = 0 
[ 1024.598583] 3. Phy Mode = 0 
[ 1024.602833] MCS Set = 00 00 00 00 00 
[ 1024.611835] <==== RTMPInitialize, Status=0 
[ 1024.613333] 0x1300 = 000a4200 
[ 1024.621336] # 
[ 1025.981475] # 
[ 1025.991350] # 
[ 1026.669563] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 382 
[ 1027.380122] Terminate the TimerQThr_pid=3079! 
[ 1027.380146] Terminate the MLMEThr_pid=3077! 
[ 1027.380155] Terminate the RTUSBCmdThr_pid=3078! 
[ 1027.386490] ---> RTMPFreeTxRxRingMemory 
[ 1027.386516] <--- ReleaseAdapter 
[ 1027.660189] <-- RTMPAllocTxRxRingMemory, Status=0 
[ 1027.661742] -->RTUSBVenderReset 
[ 1027.661866] <--RTUSBVenderReset 
[ 1027.681369] # 
[ 1027.950252] --> Error 2 opening /etc/Wireless/RT3070STA/RT3070STA.dat 
[ 1027.950254] 1. Phy Mode = 0 
[ 1027.950256] 2. Phy Mode = 0 
[ 1027.961372] # 
[ 1027.971371] # 
[ 1027.981371] # 
[ 1027.991372] # 
[ 1028.001371] # 
[ 1028.006748] 3. Phy Mode = 0 
[ 1028.010997] MCS Set = 00 00 00 00 00 
[ 1028.011373] # 
[ 1028.021373] # 
[ 1028.030374] <==== RTMPInitialize, Status=0 
[ 1028.031373] # 
[ 1028.037122] 0x1300 = 000a4200 
[ 1028.175477] ATL1E 0000:02:00.0: irq 29 for MSI/MSI-X 
[ 1028.176012] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[ 1028.273306] Terminate the TimerQThr_pid=3090! 
[ 1028.273316] Terminate the MLMEThr_pid=3088! 
[ 1028.273333] Terminate the RTUSBCmdThr_pid=3089! 
[ 1028.279750] ---> RTMPFreeTxRxRingMemory 
[ 1028.279777] <--- ReleaseAdapter 
[ 1028.581715] <-- RTMPAllocTxRxRingMemory, Status=0 
[ 1028.583252] -->RTUSBVenderReset 
[ 1028.583377] <--RTUSBVenderReset 
[ 1028.859764] --> Error 2 opening /etc/Wireless/RT3070STA/RT3070STA.dat 
[ 1028.859766] 1. Phy Mode = 0 
[ 1028.859768] 2. Phy Mode = 0 
[ 1028.886756] 3. Phy Mode = 0 
[ 1028.891007] MCS Set = 00 00 00 00 00 
[ 1028.900010] <==== RTMPInitialize, Status=0 
[ 1028.901631] 0x1300 = 000a4200 
[ 1030.985933] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1) 
[ 1031.001406] # 
[ 1031.981295] # 
[ 1036.072789] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 382 
[ 1036.072948] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1) 
[ 1036.081340] # 
[ 1038.902329] wlan0: no IPv6 routers present 
[ 1046.075607] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 565 
[ 1046.075684] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1) 
[ 1046.081329] # 
[ 1056.080283] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 565 
[ 1056.080377] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1) 
[ 1066.084735] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 565 
[ 1066.084826] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1) 
[ 1069.681350] Terminate the TimerQThr_pid=3103! 
[ 1069.681371] Terminate the MLMEThr_pid=3101! 
[ 1069.681381] Terminate the RTUSBCmdThr_pid=3102! 
[ 1069.687720] ---> RTMPFreeTxRxRingMemory 
[ 1069.687752] <--- ReleaseAdapter 
[ 1069.960664] <-- RTMPAllocTxRxRingMemory, Status=0 
[ 1069.962221] -->RTUSBVenderReset 
[ 1069.962346] <--RTUSBVenderReset 
[ 1070.238481] --> Error 2 opening /etc/Wireless/RT3070STA/RT3070STA.dat 
[ 1070.238484] 1. Phy Mode = 0 
[ 1070.238485] 2. Phy Mode = 0 
[ 1070.266851] 3. Phy Mode = 0 
[ 1070.271100] MCS Set = 00 00 00 00 00 
[ 1070.280102] <==== RTMPInitialize, Status=0 
[ 1070.281601] 0x1300 = 000a4200 
[ 1070.940239] Terminate the TimerQThr_pid=3169! 
[ 1070.940252] Terminate the MLMEThr_pid=3167! 
[ 1070.940269] Terminate the RTUSBCmdThr_pid=3168! 
[ 1070.946608] ---> RTMPFreeTxRxRingMemory 
[ 1070.946633] <--- ReleaseAdapter 
[ 1071.024571] ATL1E 0000:02:00.0: irq 29 for MSI/MSI-X 
[ 1071.025181] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[ 1229.051397] # 
[ 1229.274855] <-- RTMPAllocTxRxRingMemory, Status=0 
[ 1229.276397] -->RTUSBVenderReset 
[ 1229.276522] <--RTUSBVenderReset 
[ 1229.553282] --> Error 2 opening /etc/Wireless/RT3070STA/RT3070STA.dat 
[ 1229.553285] 1. Phy Mode = 0 
[ 1229.553286] 2. Phy Mode = 0 
[ 1229.571278] # 
[ 1229.581401] # 
[ 1229.591278] # 
[ 1229.603026] 3. Phy Mode = 0 
[ 1229.607277] MCS Set = 00 00 00 00 00 
[ 1229.616278] <==== RTMPInitialize, Status=0 
[ 1229.617776] 0x1300 = 000a4200 
[ 1231.674048] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 382 
[ 1232.390690] Terminate the TimerQThr_pid=3285! 
[ 1232.390713] Terminate the MLMEThr_pid=3283! 
[ 1232.390723] Terminate the RTUSBCmdThr_pid=3284! 
[ 1232.397059] ---> RTMPFreeTxRxRingMemory 
[ 1232.397088] <--- ReleaseAdapter 
[ 1232.681852] <-- RTMPAllocTxRxRingMemory, Status=0 
[ 1232.683311] -->RTUSBVenderReset 
[ 1232.683435] <--RTUSBVenderReset 
[ 1232.691314] # 
[ 1232.881317] # 
[ 1232.901316] # 
[ 1232.921315] # 
[ 1232.941316] # 
[ 1233.008323] --> Error 2 opening /etc/Wireless/RT3070STA/RT3070STA.dat 
[ 1233.008326] 1. Phy Mode = 0 
[ 1233.008327] 2. Phy Mode = 0 
[ 1233.034941] 3. Phy Mode = 0 
[ 1233.039191] MCS Set = 00 00 00 00 00 
[ 1233.048192] <==== RTMPInitialize, Status=0 
[ 1233.049690] 0x1300 = 000a4200 
[ 1233.215341] ATL1E 0000:02:00.0: irq 29 for MSI/MSI-X 
[ 1233.215992] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[ 1233.820204] Terminate the TimerQThr_pid=3295! 
[ 1233.820226] Terminate the MLMEThr_pid=3293! 
[ 1233.820236] Terminate the RTUSBCmdThr_pid=3294! 
[ 1233.826576] ---> RTMPFreeTxRxRingMemory 
[ 1233.826602] <--- ReleaseAdapter 
[ 1233.981328] # 
[ 1234.001328] # 
[ 1234.071329] # 
[ 1234.180254] <-- RTMPAllocTxRxRingMemory, Status=0 
[ 1234.181828] -->RTUSBVenderReset 
[ 1234.181953] <--RTUSBVenderReset 
[ 1234.251333] # 
[ 1234.271331] # 
[ 1234.482463] --> Error 2 opening /etc/Wireless/RT3070STA/RT3070STA.dat 
[ 1234.482466] 1. Phy Mode = 0 
[ 1234.482467] 2. Phy Mode = 0 
[ 1234.491333] # 
[ 1234.517832] 3. Phy Mode = 0 
[ 1234.522083] MCS Set = 00 00 00 00 00 
[ 1234.531085] <==== RTMPInitialize, Status=0 
[ 1234.532582] 0x1300 = 000a4200 
[ 1234.541338] # 
[ 1236.616152] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1) 
[ 1236.621361] # 
[ 1236.631359] # 
[ 1236.641358] # 
[ 1236.651358] # 
[ 1236.661358] # 
[ 1236.702609] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 565 
[ 1236.702758] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1) 
[ 1236.710109] # 
[ 1244.990010] wlan0: no IPv6 routers present 
[ 1246.705379] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 756 
[ 1246.705456] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1) 
[ 1256.708121] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 756 
[ 1256.708200] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1) 
[ 1266.712781] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 756 
[ 1266.712871] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1) 
[ 1275.681683] Terminate the TimerQThr_pid=3308! 
[ 1275.681706] Terminate the MLMEThr_pid=3306! 
[ 1275.681716] Terminate the RTUSBCmdThr_pid=3307! 
[ 1275.688050] ---> RTMPFreeTxRxRingMemory 
[ 1275.688079] <--- ReleaseAdapter 
[ 1275.968096] <-- RTMPAllocTxRxRingMemory, Status=0 
[ 1275.969676] -->RTUSBVenderReset 
[ 1275.969801] <--RTUSBVenderReset 
[ 1276.246436] --> Error 2 opening /etc/Wireless/RT3070STA/RT3070STA.dat 
[ 1276.246439] 1. Phy Mode = 0 
[ 1276.246440] 2. Phy Mode = 0 
[ 1276.273430] 3. Phy Mode = 0 
[ 1276.281059] MCS Set = 00 00 00 00 00 
[ 1276.290058] <==== RTMPInitialize, Status=0 
[ 1276.291555] 0x1300 = 000a4200 
[ 1276.921696] Terminate the TimerQThr_pid=3374! 
[ 1276.921718] Terminate the MLMEThr_pid=3372! 
[ 1276.921729] Terminate the RTUSBCmdThr_pid=3373! 
[ 1276.928063] ---> RTMPFreeTxRxRingMemory 
[ 1276.928089] <--- ReleaseAdapter 
[ 1277.005666] ATL1E 0000:02:00.0: irq 29 for MSI/MSI-X 
[ 1277.006274] ADDRCONF(NETDEV_UP): eth0: link is not ready 

6) Code:

$ sudo lshw -C network

 *-network               
       description: Ethernet interface 
       product: Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller 
       vendor: Atheros Communications 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: b0 
       serial: 00:26:18:90:d6:86 
       capacity: 1GB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no multicast=yes port=twisted pair 
       resources: irq:29 memory:fe9c0000-fe9fffff ioport:cc00(size=128) 
  *-network DISABLED 
       description: Wireless interface 
       physical id: 1 
       logical name: wlan0 
       serial: 00:1f:1f:2a:72:87 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=RTxx70 Wireless 

7) Code:

$ iwlist scan 

lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 

wlan0     No scan results 

8) Code:

$ lsb_release -d

Description:    Ubuntu 10.04 LTS

9) code:

$ uname -mr

2.6.32-21-generic x86_64

10) Code:

$ sudo /etc/init.d/networking restart

* Reconfiguring network interfaces... 


Any help would be greatly appreciated,

thanks

---

### Post by Didjee on 2010-05-01
Why nobody is interested by my post?? I'm new here and I just did my best to post a clear text. And I have just spent my day trying to solve the problem so it would be nice if somebody was answering...

---

### Post by chili555 on 2010-05-01
Only a few people here know what to do and sometimes he's answering other posts, eating dinner or watching NASCAR.

This is the problem:> Error 2 opening /etc/Wireless/RT3070STA/RT3070STA.dat You may not have the right file in the right place. 

Please see here: [http://ubuntuforums.org/showpost.php?p=9195852&postcount=23](http://ubuntuforums.org/showpost.php?p=9195852&postcount=23)

---

### Post by Didjee on 2010-05-01
Hi Chill,

Thanks for your answer. I tried to create /etc/Wireless/RT3070STA and had the answer "no such file or directory"

---

### Post by Didjee on 2010-05-01
Sorry, I forgot to say that know my wireless network has totally disappeared.
If I tape in:

Code: iwconfig

lo          no wireless extension.

eth0      no wireless extension

and in ifconfig I don't have anymore the Wlan0

---

### Post by chili555 on 2010-05-01
> I tried to create /etc/Wireless/RT3070STA and had the answer "no such file or directory"You did:```
sudo mkdir /etc/Wireless/RT3070STA
```??

Please try again and let me know the exact response.

Did you do the prior step?```
ls /etc/Wireless
```What was the result?

---

### Post by Didjee on 2010-05-01
When enter the code:

ls /etc/Wireless

I have:

ls: cannot access /etc/Wireless: No such file or directory

---

### Post by Didjee on 2010-05-01
Since having installed ndiswrapper earlier on (before your answer) and installed the Windows driver for the wireless device , I lost all Wlan after rebooting my computer.
I removed the Windows driver but I don't have Wlan anymore

---

### Post by chili555 on 2010-05-01
Please do:```
cat /etc/modprobe.d/blacklist.conf
cat /etc/modprobe.d/blacklist
```Are rt2870sta, rt2800usb or any other rt2xx drivers blacklisted?> I removed the Windows driver but I don't have Wlan anymore Did you do this just a while ago? It will be hard for me to help you fix your wireless if you are making random changes I don't know about.

---

### Post by Didjee on 2010-05-01
Sorry, maybe I am unclear. After I contacted you, I rebooted m computer and realised I had lost the Wlan. So, effectively I uninstalled the Windows driver and ndiswrapper to reverse the process. Unfortunately, it seems it doesn't work that way. 

	 	 Code:
 

 cat /etc/modprobe.d/blacklist.conf
 

 # This file lists those modules which we don't want to be loaded by  
 # alias expansion, usually so some other driver will be loaded for the  
 # device instead.  
 

 # evbug is a debug tool that should be loaded explicitly  
 blacklist evbug  
 

 # these drivers are very simple, the HID drivers are usually preferred  
 blacklist usbmouse  
 blacklist usbkbd  
 

 # replaced by e100  
 blacklist eepro100  
 

 # replaced by tulip  
 blacklist de4x5  
 

 # causes no end of confusion by creating unexpected network interfaces  
 blacklist eth1394  
 

 # snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much  
 # hardware on its own (Ubuntu bug #2011, #6810)  
 blacklist snd_intel8x0m  
 

 # Conflicts with dvb driver (which is better for handling this device)  
 blacklist snd_aw2  
 

 # causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)  
 blacklist i2c_i801  
 

 # replaced by p54pci  
 blacklist prism54  
 

 # replaced by b43 and ssb.  
 blacklist bcm43xx  
 

 # most apps now use garmin usb driver directly (Ubuntu: #114565)  
 blacklist garmin_gps  
 

 # replaced by asus-laptop (Ubuntu: #184721)  
 blacklist asus_acpi  
 

 # low-quality, just noise when being used for sound playback, causes  
 # hangs at desktop session start (Ubuntu: #246969)  
 blacklist snd_pcsp  
 

 # ugly and loud noise, getting on everyone's nerves; this should be done by a  
 # nice pulseaudio bing (Ubuntu: #77010) 
 blacklist pcspkr  
 

 # EDAC driver for amd76x clashes with the agp driver preventing the aperture  
 # from being initialised (Ubuntu: #297750). Blacklist so that the driver  
 # continues to build and is installable for the few cases where its  
 # really needed.  
 blacklist amd76x_edac  
 blacklist ndiswrapper 



I blacklisted ndiswrapper because I tried loading the module rt2870sta using the command sudo modprobe. This worked, however, when I was rebooting ndiswrapper was coming back and rt2870sta was disappearing again. 

So, I thought that by putting ndiswrapper on blacklist, rt2870sta would stay but unfortunately it doesn't.

---

### Post by chili555 on 2010-05-01
Let's try a few things:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add three lines:```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread, save and close gedit. Now do:```
sudo gedit /etc/modules
```Add a new line:```
rt2870sta
```Proofread, save and close gedit. Reboot and report your progress.

---

### Post by Didjee on 2010-05-01
Okay, nice :), I have now the Wlan connection and I am back at where I was when I posted this post. 
Wicd detects my wifi network but I can't connect to it. I get the error message:
Bad password

Do you want to see lsmod, iwconfig?

Thanks

---

### Post by Didjee on 2010-05-01
Actually, i'm going to do what you suggested on your first post

---

### Post by Didjee on 2010-05-01
Ok, now if I do:

Code: 

ls /etc/Wireless

I have as answer:

ls: cannot access /etc/Wireless: No such file or directory

---

### Post by chili555 on 2010-05-01
> Bad passwordI think it doesn't agree with your WPA or WEP password. If you have a wireless interface and it tries to connect, there is no need to worry about RT3070STA.dat.

---

### Post by Didjee on 2010-05-01
Ok, is there nothing more I can do?

It looks like I will have to wait until my USB wireless device is supported. Thanks for help and patience.

---

### Post by chili555 on 2010-05-01
> Ok, is there nothing more I can do?Certainly there is! Check the WPA or WEP password in the router carefully against what you are inputting in Wicd. Make sure it's the correct format and the correct key. Your card is supported just fine if you use the correct password.

---

### Post by Didjee on 2010-05-01
Well, I have tried again the passphrase associated with my router. I have tried with WEP, WPA and all the options availaible really. The passphrase is pretty simple so I am sure it is the right one.  I select the right network too. All I can say is that everytime, it is stopping when validating authentication.

---

### Post by chili555 on 2010-05-02
Please let us see:```
dmesg | grep rt2
sudo cat /var/log/syslog | grep -i network > syslog.txt
```The latter command is likely to be quite long, so we will zip it so you can post it as an attachment in your reply.```
zip syslog.zip syslog.txt
```You will find the syslog.zip file in your home directory.

---

### Post by Antonimo89 on 2010-05-30
have same problem, same device, installed ralink driver for rt2870. EW-7717Un

on 64 bit Wep works fine, on 128bit - cant connect.

---

