---
title: "rt3072 assistance needed please"
date: 2012-11-07
forum: Networking &amp; Wireless
---

### Post by dwb814 on 2012-11-07
I just bought a etekcity high power 802.11 adapter. I sees the router and everyone's network around the block but I can't connect. I put in my password and the prompt comes back again?

Here is my information:

dan@dan-desktop:~$ sudo /etc/init.d/networking restart
[sudo] password for dan: 
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ]


dan@dan-desktop:~$ sudo lspci
00:00.0 RAM memory: NVIDIA Corporation MCP61 Host Bridge (rev a1)
00:01.0 ISA bridge: NVIDIA Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: NVIDIA Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB controller: NVIDIA Corporation MCP61 USB 1.1 Controller (rev a3)
00:02.1 USB controller: NVIDIA Corporation MCP61 USB 2.0 Controller (rev a3)
00:04.0 PCI bridge: NVIDIA Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: NVIDIA Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: NVIDIA Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: NVIDIA Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: NVIDIA Corporation C61 [GeForce 7025 / nForce 630a] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:0a.0 USB controller: NEC Corporation USB (rev 43)
01:0a.1 USB controller: NEC Corporation USB (rev 43)
01:0a.2 USB controller: NEC Corporation USB 2.0 (rev 04)


dan@dan-desktop:~$ sudo lspci | grep -i wireless
dan@dan-desktop:~$ 

dan@dan-desktop:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
Linux dan-desktop 3.2.0-32-generic-pae #51-Ubuntu SMP Wed Sep 26 21:54:23 UTC 2012 i686 athlon i386 GNU/Linux

dan@dan-desktop:~$ lspci -nnk | grep -iA2 net
00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
    Subsystem: ASRock Incorporation 939NF6G-VSTA Board [1849:03ef]
    Kernel driver in use: forcedeth

dan@dan-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05e3:0607 Genesys Logic, Inc. Logitech G110 Hub
Bus 002 Device 003: ID 148f:3072 Ralink Technology, Corp. RT3072 Wireless Adapter
Bus 003 Device 002: ID 0461:4d03 Primax Electronics, Ltd Kensington Mouse-in-a-box

dan@dan-desktop:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

dan@dan-desktop:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

dan@dan-desktop:~$ lsmod
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39553  1 
vesafb                 13516  1 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
snd_hda_codec_via      46138  1 
arc4                   12473  2 
nvidia              10235966  30 
snd_hda_intel          32765  4 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_intel,snd_hda_codec
rt2800usb              22373  0 
rt2800lib              53264  1 rt2800usb
crc_ccitt              12595  1 rt2800lib
rt2x00usb              20061  1 rt2800usb
rt2x00lib              48836  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              436455  3 rt2800lib,rt2x00usb,rt2x00lib
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
ppdev                  12849  0 
cfg80211              178679  2 rt2x00lib,mac80211
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
parport_pc             32114  1 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  16 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
serio_raw              13027  0 
k10temp                12990  0 
mac_hid                13077  0 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
i2c_nforce2            12906  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
sata_nv                23360  3 
forcedeth              58096  0 
pata_amd               13750  0 

dan@dan-desktop:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             connected
  Default:           yes
  HW Address:        BC:5F:F4:42:9C:B4

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.141
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             75.75.76.76
    DNS:             75.75.75.75


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             disconnected
  Default:           no
  HW Address:        00:0F:12:56:06:F3

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    HOME-25C8:       Infra, B8:9B:C9:CF:25:C8, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    GodsHouse:       Infra, C0:C1:C0:82:E7:AA, Freq 2412 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2


dan@dan-desktop:~$ lsmod | grep rt
rt2800usb              22373  0 
rt2800lib              53264  1 rt2800usb
crc_ccitt              12595  1 rt2800lib
rt2x00usb              20061  1 rt2800usb
rt2x00lib              48836  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              436455  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              178679  2 rt2x00lib,mac80211
parport_pc             32114  1 
parport                40930  3 ppdev,parport_pc,lp
dan@dan-desktop:~$ 


dan@dan-desktop:~$ dmesg | egrep 'rtl|firm|wpa|etork|wlan0'
[   12.845357] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.845632] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.597036] wlan0: authenticate with c0:c1:c0:82:e7:aa (try 1)
[   16.598547] wlan0: c0:c1:c0:82:e7:aa denied authentication (status 1)
[  496.344629] wlan0: authenticate with c0:c1:c0:82:e7:aa (try 1)
[  496.346144] wlan0: c0:c1:c0:82:e7:aa denied authentication (status 1)
[  976.330366] wlan0: authenticate with c0:c1:c0:82:e7:aa (try 1)
[  976.331883] wlan0: c0:c1:c0:82:e7:aa denied authentication (status 1)
[ 1339.318388] wlan0: authenticate with c0:c1:c0:82:e7:aa (try 1)
[ 1339.319898] wlan0: c0:c1:c0:82:e7:aa denied authentication (status 1)
[ 3214.365273] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3217.708073] wlan0: authenticate with c0:c1:c0:82:e7:aa (try 1)
[ 3217.709590] wlan0: c0:c1:c0:82:e7:aa denied authentication (status 1)
[ 3288.154426] wlan0: authenticate with c0:c1:c0:82:e7:aa (try 1)
[ 3288.157816] wlan0: c0:c1:c0:82:e7:aa denied authentication (status 1)
[ 3768.326017] wlan0: authenticate with c0:c1:c0:82:e7:aa (try 1)
[ 3768.328092] wlan0: c0:c1:c0:82:e7:aa denied authentication (status 1)
dan@dan-desktop:~$ 


I can't get it to accept my password, if it can do that I should get on. Please help!!

---

### Post by dwb814 on 2012-11-07
Tried to install the driver and I'm getting errors on the first step -Make

```
dan@dan-desktop:~/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO (2)$ sudo su
[sudo] password for dan: 
root@dan-desktop:/home/dan/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO (2)# make
make -C tools
make[1]: Entering directory `/home/dan/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO (2)/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/dan/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO (2)/tools'
/home/dan/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO (2)/tools/bin2h
/bin/sh: 1: Syntax error: word unexpected (expecting ")")
make: *** [build_tools] Error 2
root@dan-desktop:/home/dan/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO (2)# 

```I saw where it said 

```
make -C tools
```so I put that in, 

```
root@dan-desktop:/home/dan/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO (2)# make -C tools
make: Entering directory `/home/dan/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO (2)/tools'
gcc -g bin2h.c -o bin2h
make: Leaving directory `/home/dan/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO (2)/tools'
root@dan-desktop:/home/dan/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO (2)# 

```That worked but, the next step "make install" errors out, now I'm stuck at:

```
root@dan-desktop:/home/dan/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO (2)# make install
make -C /home/dan/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO (2)/os/linux -f Makefile.6 install
/bin/sh: 1: Syntax error: "(" unexpected
make: *** [install] Error 2
root@dan-desktop:/home/dan/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO (2)# 

```

Got it, never mind

---

### Post by flash63 on 2012-11-08
Hello,
use these instructions to install the driver with DKMS over Ethernet:

[http://forum.ubuntuusers.de/topic/d-link-dwa-140-wird-nicht-erkannt-komme-nicht-/#post-4365112](http://forum.ubuntuusers.de/topic/d-link-dwa-140-wird-nicht-erkannt-komme-nicht-/#post-4365112)

Summary:
```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget media.cdn.ubuntu-de.org/forum/attachments/42/20/4365112-Ralink_5370sta-2.5.0.3_dkms.tar.gz
sudo tar xvf 4365112-Ralink_5370sta-2.5.0.3_dkms.tar.gz -C /usr/src
sudo dkms add -m Ralink_5370sta -v 2.5.0.3
sudo dkms build -m Ralink_5370sta -v 2.5.0.3
sudo dkms install -m Ralink_5370sta -v 2.5.0.3 
```

install the prepared RT2870STA.dat configuration file:
```
sudo mkdir -p /etc/Wireless/RT2870STA
sudo cp /usr/src/Ralink_5370sta-2.5.0.3/src/RT2870STA.dat /etc/Wireless/RT2870STA 
```
blacklist rt2800usb:
```
echo "blacklist rt2800usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Restart

---

### Post by dwb814 on 2012-11-08
Thank you [flash63]("http://ubuntuforums.org/member.php?u=815324") I'll copy these instructions down for the next time. Thanks again!  :)

---

### Post by dwb814 on 2012-11-12
flash63,
I want to thank you for your advise on installing the other drive for my wireless connection.

My connection was getting intermittent, but after following your instruction, my connection is rock solid now. 

Thank you very much for your kind assistance.
Dan :)

---

### Post by flash63 on 2012-11-14
> My connection was getting intermittent, but after following your instruction, my connection is rock solid now.

You're welcome and  thanks for your reply.

---

