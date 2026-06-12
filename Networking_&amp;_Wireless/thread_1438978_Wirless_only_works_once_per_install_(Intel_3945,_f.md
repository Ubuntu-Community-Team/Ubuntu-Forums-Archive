---
title: "Wirless only works once per install (Intel 3945, full details)"
date: 2010-03-25
forum: Networking &amp; Wireless
---

### Post by albyr on 2010-03-25
(Full output of lspci, lsmod, dmesg etc below.)

Windows crashed yet again so I thought I'd switch to Ubuntu. Install of 9.10 went flawlessly, everything looked great and worked perfectly. Next day after restart the wireless wouldn't connect. I looked around for solutions and used a wired connection to install wicd and suddenly wireless worked again. But next day after restart wireless wouldn't connect again - I keep getting a popup asking for my WPA key despite the fact that I know the key is entered correctly. I decided to install 10.04, thinking maybe that would help. It didn't look like wireless was working but after a restart it worked and it worked again after another restart! Fantastic! But today, I'm back to square one. Using Windows again.

TL;DR - Wireless won't connect to the network which it can definitely see - repeatedly presents "Enter WPA key" prompt despite key being correct and wireless working flawlessly under Windows.


1. Machine Brand and Model
Dell M65

2. Wireless Brand, Model and Wireless Chipset
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G72GL [Quadro FX 350M] (rev a1)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

3. Interface
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:b5:26:69  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2912 (2.9 KB)  TX bytes:2912 (2.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:de:91:f8:18  
          inet6 addr: fe80::218:deff:fe91:f818/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:810 (810.0 B)  TX bytes:1494 (1.4 KB)

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:";pd$\x11\x9E\x09\xDC\xAA\xD4\xAC\xF2\x1B\x10\xAF;3\xCD\xE3PHG\x15\\xBBo"\x19\xBA\x9B}\xF5"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
pan0      no wireless extensions.

4. Modules
$lsmod
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8901  1 
fat                    47767  1 vfat
usb_storage            39425  1 
rfcomm                 33357  4 
binfmt_misc             6587  1 
ppdev                   5259  0 
sco                     7853  2 
bridge                 45582  0 
stp                     1655  1 bridge
bnep                    9436  2 
l2cap                  30592  16 rfcomm,bnep
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11321  0 
vgastate                8961  1 vga16fb
joydev                  8708  0 
snd_hda_codec_idt      51914  1 
arc4                    1153  2 
snd_hda_intel          21781  2 
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
pcmcia                 33024  0 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
usbhid                 36110  0 
iwl3945                69177  0 
nouveau               466476  2 
iwlcore               106626  1 iwl3945
snd                    54148  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ttm                    49943  1 nouveau
dell_wmi                1793  0 
mac80211              204470  2 iwl3945,iwlcore
drm_kms_helper         29297  1 nouveau
yenta_socket           20408  1 
rsrc_nonstatic         10015  1 yenta_socket
intel_agp              24181  0 
led_class               2864  2 iwl3945,iwlcore
psmouse                62957  0 
serio_raw               3978  0 
btusb                  10925  2 
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
dell_laptop             6688  0 
dcdbas                  5550  1 dell_laptop
hid                    66968  1 usbhid
video                  17375  0 
output                  1871  1 video
drm                   162599  4 nouveau,ttm,drm_kms_helper
i2c_algo_bit            5028  1 nouveau
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
agpgart                31724  3 ttm,intel_agp,drm
soundcore               6620  1 snd
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
cfg80211              126517  3 iwl3945,iwlcore,mac80211
lp                      7028  0 
parport                32635  2 ppdev,lp
ohci1394               27174  0 
ieee1394               81245  1 ohci1394
tg3                   109612  0 

5. Kernel Boot Messages
$dmesg | grep 3945
[   11.773541] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   11.773544] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   11.773664] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.773679] iwl3945 0000:0c:00.0: setting latency timer to 64
[   11.945821] iwl3945 0000:0c:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   11.945826] iwl3945 0000:0c:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   11.946029] iwl3945 0000:0c:00.0: irq 29 for MSI/MSI-X
[   12.002859] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   12.407915] iwl3945 0000:0c:00.0: firmware: requesting iwlwifi-3945-2.ucode
[   12.430029] iwl3945 0000:0c:00.0: loaded firmware version 15.32.2.9

6. Network configuration
$sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 02
       serial: 00:18:de:91:f8:18
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:29 memory:ecfff000-ecffffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:b5:26:69
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 firmware=5752-v3.19 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:30 memory:ecef0000-ecefffff

7. Scan for networks
$iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

8. Ubuntu version - Lucid, but exactly the same problem presented with Karmic.

9. Kernel/Architecture - 2.6.32-17-generic i686

10. Restarting network
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces... [ OK ]

---

### Post by chili555 on 2010-03-25
> ";pd$\x11\x9E\x09\xDC\xAA\xD4\xAC\xF2\x1B\x1 0\xAF;3\xCD\xE3PHG\x15\\xBBo"\x19\xBA\x9B}\xF5" Is this really the name of your network? Please post:```
rfkill list
[COLOR="Red"]sudo[/COLOR] iwlist wlan0 scan
```Thanks.






Hint: *dell_laptop*

---

### Post by albyr on 2010-03-25
Nope, that is definitely not my wireless network's name! It should be "BeBox".

$rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:1D:68:E9:55:67
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"BeBox"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000165c4d89c
                    Extra: Last beacon: 2568ms ago
                    IE: Unknown: 00054265426F78
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180201F0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:24:B2:30:D8:EE
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"SKY81934"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003df6991bf
                    Extra: Last beacon: 2384ms ago
                    IE: Unknown: 0008534B593831393334
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00

---

### Post by chili555 on 2010-03-25
Let's try an experiment. Please do:```
sudo rmmod -f iwl3945
sudo modprobe iwl3945 swcrypto=1
```Does it connect? If so, we will have to tweak a file to make it permanent.

---

### Post by albyr on 2010-03-25
Both commands executed. Still the exact same problem.

---

### Post by chili555 on 2010-03-25
Another trial:```
sudo rmmod -f iwl3945
sudo modprobe iwl3945 swcrypto=0
```How about now?

---

### Post by albyr on 2010-03-26
I reset from Windows into Ubuntu, and the wireless worked! I thought the problem was solved so I did another reset to check and it was back to not working. Whilst it was working I ran iwconfig and it showed the ESSID as "BeBox" and not ";pd$\x11\x9E\x09\..." as it had before on the iwconfig I posted.

I ran the new commands you suggested, rmmod shut down the wireless and modprobe started it back up again, but the problem was still there.

---

