---
title: "RALink rt2070 card not able to connect"
date: 2012-08-05
forum: Networking &amp; Wireless
---

### Post by Morphic on 2012-08-05
Hey guys, I've recently installed Ubuntu 12.04 LTS and am trying to get my new wireless card to connect to my network. I've read through many solutions here and tried quite a few, however I am still unable to connect to my network, I can confirm I am using the correct SSID and WPA key but instead of connecting nm-applet just cycle's me through endless authentication prompts :/.

My card is:
```

root@HellFire:/etc/Wireless/RT2870STA# lsusb
Bus 001 Device 003: ID 148f:2070 Ralink Technology, Corp. RT2070 Wireless Adapter

```

My system is:
```

root@HellFire:/etc/Wireless/RT2870STA# uname -a
Linux HellFire 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

So far I've blacklisted the existing rt2800usb drivers to prevent conflicts and my blacklist file is as follows:
```

root@HellFire:/etc/Wireless/RT2870STA# cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

[snip]

blacklist rt2800usb

```

I've also rmmod'd the rt* module's to ensure they're not loaded and confirmed via:
```

root@HellFire:/home/josh/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO# lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
uas                    18027  0 
usb_storage            49198  1 
dm_crypt               23125  1 
snd_hda_codec_hdmi     32474  4 
rfcomm                 47604  0 
parport_pc             32866  0 
ppdev                  17113  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
snd_hda_codec_realtek   223867  1 
eeepc_wmi              13109  0 
asus_wmi               24456  1 eeepc_wmi
sparse_keymap          13890  1 asus_wmi
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
psmouse                87603  0 
serio_raw              13211  0 
sb_edac                18127  0 
snd_seq_midi           13324  0 
edac_core              53746  1 sb_edac
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 17693  0 
mac_hid                13253  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41616  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
nouveau               774571  3 
ttm                    76949  1 nouveau
drm_kms_helper         46978  1 nouveau
drm                   242038  5 nouveau,ttm,drm_kms_helper
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
i2c_algo_bit           13423  1 nouveau
mxm_wmi                12979  1 nouveau
video                  19596  1 nouveau
e1000e                156693  0 
wmi                    19256  2 asus_wmi,mxm_wmi

```

I've downloaded drivers from RALink's Linux Support section, untar'd the tarball and I now have this:
```

root@HellFire:/home/josh/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO# ls
chips    iwpriv_usage.txt  README_STA_usb     sta
common   Makefile          RT2870STACard.dat  sta_ate_iwpriv_usage.txt
include  os                RT2870STA.dat      tools

```
I've added my device's ID to common/rtusb_dev_id.c and replaced the call to usb_buffer_alloc/usb_buffer_free with the appropiate usb_alloc_coherent/usb_free_coherent to prevent errors during make. In addition I **have** changed config.mk to use the WPA supplicant:
```

# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

```   

Having compiled the kernel module successfully...
```

root@HellFire:/home/josh/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO# make

make -C tools
make[1]: Entering directory `/home/josh/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/josh/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/tools'
/home/josh/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/tools/bin2h
cp -f os/linux/Makefile.6 /home/josh/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux/Makefile
make -C /lib/modules/3.2.0-23-generic/build SUBDIRS=/home/josh/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-23-generic'
  [snip]  
  #LD [M]  /home/josh/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux/rt5370sta.o
  Building modules, stage 2.
  MODPOST 1 modules
  LD [M]  /home/josh/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux/rt5370sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-23-generic'
cp -f /home/josh/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux/rt5370sta.ko /tftpboot
root@HellFire:/home/josh/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO# 

```
And installed it successfully...
```

root@HellFire:/home/josh/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO# make install
make -C /home/josh/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/josh/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/josh/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/3.2.0-23-generic/kernel/drivers/net/wireless/
install -m 644 -c rt5370sta.ko /lib/modules/3.2.0-23-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 3.2.0-23-generic
make[1]: Leaving directory `/home/josh/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux'

root@HellFire:/home/josh/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO# cd os/linux/
root@HellFire:/home/josh/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux# modprobe rt5370sta

```

...I can see the module is installed and claimed by my wireless card:
```

root@HellFire:/home/josh/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux# lsmod
Module                  Size  Used by
rt5370sta             805299  1 
[snip]

root@HellFire:/home/josh/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux# modinfo rt5370sta
filename:       /lib/modules/3.2.0-23-generic/kernel/drivers/net/wireless/rt5370sta.ko
version:        2.5.0.3
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     48118790AAD878DDDCC052B
[snip]
alias:          usb:v148Fp2070d*dc*dsc*dp*ic*isc*ip*
depends:        
vermagic:       3.2.0-23-generic SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)

```

and I now have a wireless interface:
```

root@HellFire:/home/josh/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux# ifconfig
eth0      Link encap:Ethernet  HWaddr 10:bf:48:e2:a5:51  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Memory:fb700000-fb720000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1864 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1864 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:148208 (148.2 KB)  TX bytes:148208 (148.2 KB)

ra0       Link encap:Ethernet  HWaddr 7c:dd:90:13:92:47  
          inet6 addr: fe80::7edd:90ff:fe13:9247/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:67190 (67.1 KB)  TX bytes:163164 (163.1 KB)

ra0:avahi Link encap:Ethernet  HWaddr 7c:dd:90:13:92:47  
          inet addr:169.254.6.226  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

root@HellFire:/home/josh/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux# iwconfig
lo        no wireless extensions.

ra0       Ralink STA  ESSID:"SKY61133"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.437 GHz  Access Point: 00:24:B2:43:B1:B6   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=97/100  Signal level:-11 dBm  Noise level:-11 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

```

Where SKY61133 is my network's SSID and is as follows:
```

root@HellFire:/home/josh/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux# iwlist ra0 scan
ra0       Scan completed :
          Cell 01 - Address: 00:24:B2:43:B1:B6
                    Protocol:802.11b/g
                    ESSID:"SKY61133"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/100  Signal level=-69 dBm  Noise level=-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

```

Despite all of this, I still cannot connect to my network and I have been trying to correct the issue for some two days, I've tried the rt2870sta driver also, which doesn't allow me to scan or really do anything.

Having ran dmesg after insertion of the wifi card, I can see quite a few errors are given by this driver and thus the driver I have may not be the correct one for this card, the dmesg output is as follows:
```

[ 5067.688198] usb 1-1.6: new high-speed USB device number 5 using ehci_hcd
[ 5067.799796] 
[ 5067.799798] 
[ 5067.799799] === pAd = ffffc90015101000, size = 549784 ===
[ 5067.799800] 
[ 5067.799968] <-- RTMPAllocTxRxRingMemory, Status=0
[ 5067.800063] <-- RTMPAllocAdapterBlock, Status=0
[ 5067.817316] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[ 5068.076099] RTMP_TimerListAdd: add timer obj ffffc9001514a160!
[ 5068.076105] RTMP_TimerListAdd: add timer obj ffffc9001514a1d8!
[ 5068.076108] RTMP_TimerListAdd: add timer obj ffffc9001514a250!
[ 5068.076111] RTMP_TimerListAdd: add timer obj ffffc9001514a0e8!
[ 5068.076115] RTMP_TimerListAdd: add timer obj ffffc90015149f80!
[ 5068.076118] RTMP_TimerListAdd: add timer obj ffffc90015149ff8!
[ 5068.076122] RTMP_TimerListAdd: add timer obj ffffc90015114468!
[ 5068.076125] RTMP_TimerListAdd: add timer obj ffffc90015103668!
[ 5068.076128] RTMP_TimerListAdd: add timer obj ffffc900151036e8!
[ 5068.076131] RTMP_TimerListAdd: add timer obj ffffc900151145f8!
[ 5068.076135] RTMP_TimerListAdd: add timer obj ffffc90015114378!
[ 5068.076139] RTMP_TimerListAdd: add timer obj ffffc90015114578!
[ 5068.077522] -->RTUSBVenderReset
[ 5068.077646] <--RTUSBVenderReset
[ 5068.545837] Key1Str is Invalid key length(0) or Type(0)
[ 5068.545858] Key2Str is Invalid key length(0) or Type(0)
[ 5068.545878] Key3Str is Invalid key length(0) or Type(0)
[ 5068.545898] Key4Str is Invalid key length(0) or Type(0)
[ 5068.546201] 1. Phy Mode = 5
[ 5068.546204] 2. Phy Mode = 5
[ 5068.572650] phy mode> Error! The chip does not support 5G band 5!
[ 5068.572741] RTMPSetPhyMode: channel is out of range, use first channel=1 
[ 5068.576281] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[ 5068.590651] 3. Phy Mode = 9
[ 5068.593152] \x1b[mAntCfgInit: primary/secondary ant 0/1
[ 5068.593154] \x1b[mMCS Set = ff 00 00 00 01
[ 5068.683344] <==== rt28xx_init, Status=0
[ 5068.684901] 0x1300 = 00064300
[ 5068.703766] ERROR!!! RTMPSetTimer failed, Halt in Progress!
[ 5068.960778] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[ 5069.219359] RTMP_TimerListAdd: add timer obj ffffc9001514a160!
[ 5069.219365] RTMP_TimerListAdd: add timer obj ffffc9001514a1d8!
[ 5069.219369] RTMP_TimerListAdd: add timer obj ffffc9001514a250!
[ 5069.219372] RTMP_TimerListAdd: add timer obj ffffc9001514a0e8!
[ 5069.219376] RTMP_TimerListAdd: add timer obj ffffc90015149f80!
[ 5069.219379] RTMP_TimerListAdd: add timer obj ffffc90015149ff8!
[ 5069.219382] RTMP_TimerListAdd: add timer obj ffffc90015114468!
[ 5069.219385] RTMP_TimerListAdd: add timer obj ffffc90015103668!
[ 5069.219388] RTMP_TimerListAdd: add timer obj ffffc900151036e8!
[ 5069.219391] RTMP_TimerListAdd: add timer obj ffffc900151145f8!
[ 5069.219395] RTMP_TimerListAdd: add timer obj ffffc90015114378!
[ 5069.219399] RTMP_TimerListAdd: add timer obj ffffc90015114578!
[ 5069.220775] -->RTUSBVenderReset
[ 5069.220898] <--RTUSBVenderReset
[ 5069.693964] Key1Str is Invalid key length(0) or Type(0)
[ 5069.693984] Key2Str is Invalid key length(0) or Type(0)
[ 5069.694004] Key3Str is Invalid key length(0) or Type(0)
[ 5069.694024] Key4Str is Invalid key length(0) or Type(0)
[ 5069.694329] 1. Phy Mode = 5
[ 5069.694331] 2. Phy Mode = 5
[ 5069.720774] phy mode> Error! The chip does not support 5G band 5!
[ 5069.720863] RTMPSetPhyMode: channel is out of range, use first channel=1 
[ 5069.724409] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[ 5069.738777] 3. Phy Mode = 9
[ 5069.741277] \x1b[mAntCfgInit: primary/secondary ant 0/1
[ 5069.741280] \x1b[mMCS Set = ff 00 00 00 01
[ 5069.829348] <==== rt28xx_init, Status=0
[ 5069.830898] 0x1300 = 00064300
[ 5069.859150] /home/josh/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c:3069 assert KeyIdx < 4failed
[ 5069.859773] /home/josh/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c:3069 assert KeyIdx < 4failed
[ 5072.050432] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 186

```

The config file is as follows:
```

root@HellFire:/home/josh/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux# cat /etc/Wireless/RT2870STA/RT2870STA.dat 
#The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=
ChannelGeography=1
SSID=[my networks SSID]
NetworkType=Infra
WirelessMode=5
Channel=0
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
PktAggregate=0
WmmCapable=1
AckPolicy=0;0;0;0
AuthMode=WPAPSK
EncrypType=TKIP
WPAPSK=[my network's WPA key]
DefaultKeyID=1
Key1Type=0
Key1Str=
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
PSMode=CAM
AutoRoaming=0
RoamThreshold=70
APSDCapable=0
APSDAC=0;0;0;0
HT_RDG=1
HT_EXTCHA=0
HT_OpMode=0
HT_MpduDensity=4
HT_BW=1
HT_BADecline=0
HT_AutoBA=1
HT_AMSDU=0
HT_BAWinSize=64
HT_GI=1
HT_MCS=33
HT_MIMOPSMode=3
HT_DisallowTKIP=1
HT_STBC=0
EthConvertMode=
EthCloneMac=
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0
MeshId=MESH
MeshAutoLink=1
MeshAuthMode=OPEN
MeshEncrypType=NONE
MeshWPAKEY=
MeshDefaultkey=1
MeshWEPKEY=
CarrierDetect=0
AntDiversity=0
BeaconLostTime=4
FtSupport=0
Wapiifname=ra0
WapiPsk=
WapiPskType=
WapiUserCertPath=
WapiAsCertPath=
PSP_XLINK_MODE=0
WscManufacturer=
WscModelName=
WscDeviceName=
WscModelNumber=
WscSerialNumber=
RadioOn=1

```

Sorry for the long post but this is really frustrating me. I'm going to try the other drivers from RALink's site and see if any of them can provide better results, in the meantime any advice would be appreciated.

Regards,

Morphic

Edit: 
I understand the rt2870sta module is merged into the rt2800usb module as of an earlier version of Linux(pre 12.04). I have tried connecting with the rt2800usb module also and made sure the rt2870sta drivers aren't loaded to prevent conflicts. While I am able to see my network, I still cannot connect to it :/

Edit2:
I get the following when trying to connect to my network using the rt2800usb driver:
```

dmesg
[snip]
[ 7966.568725] wlan0: authenticate with 00:24:b2:43:b1:b6 (try 1)
[ 7966.569989] wlan0: authenticated # displayed regardless of whether wpa key is valid
[ 7966.588238] wlan0: associate with 00:24:b2:43:b1:b6 (try 1)
[ 7966.590992] wlan0: RX ReassocResp from 00:24:b2:43:b1:b6 (capab=0x471 status=0 aid=2)
[ 7966.590997] wlan0: associated
[ 7970.590040] wlan0: deauthenticated from 00:24:b2:43:b1:b6 (Reason: 1)
[ 7970.638259] cfg80211: All devices are disconnected, going to restore regulatory settings
[snip]

```
Any idea's?

---

### Post by Morphic on 2012-08-06
I've managed to solve the issue! For those who have a similar problem the following is how to solve it.

Ensure you use the correct drivers for your wireless card, I'm now using the following:
```

DPO_RT3070_LinuxSTA_V2.3.0.4_20100604
$ lsmod
rt3070sta

```

The above driver will **not** compile on Ubuntu 12.04 out of the box, you have to update the reference's of usb_alloc_buffer and usb_free_buffer, as the functions have been renamed in this version of Ubuntu.

Browse to DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/include/os and search for all references to "**usb_alloc_buffer**" and "**usb_free_buffer**" within **rt_linux.h**, there should only be two. Update them to "**usb_alloc_coherent**" and "**usb_free_coherent**".

You may need to add your device ID to **DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/common/rtusb_dev_id.c**. You can find your device's id via:
```

$ lsusb
Bus 001 Device 003: ID 148f:2070 Ralink Technology, Corp. RT2070 Wireless Adapter

```
Add the returned  vendor and product ID to module array, my edited file is as follows for the rt2070 wifi adapter:
```

/* module table */
USB_DEVICE_ID rtusb_dev_id[] = {
#ifdef RT3070
	{USB_DEVICE(0x148F,0x2070)}, /* Ralink 2070 < ADDED MY DEVICE'S ID */
	{USB_DEVICE(0x148F,0x3070)}, /* Ralink 3070 */
[snip]

```

Rename/copy the RT2870STA.dat file to RT3070STA.dat so *make install* locate's and copies the correct file. 

Compile the driver via:
```

sudo make
sudo make install

```

Create a symlink to resolve errors locating the adapter's configuration file.
```

sudo mkdir /etc/Wireless/RT2870STA; sudo ln -s /etc/Wireless/RT3070STA/RT3070STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat

```

You may need to edit this configuration file, mine is as follows, I found the original causes problems.
```

josh@HellFire:~$ cat /etc/Wireless/RT3070STA/RT3070STA.dat
#The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=US
ChannelGeography=1
NetworkType=Infra
WirelessMode=5
Channel=1
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
PktAggregate=0
WmmCapable=1
AckPolicy=0;0;0;0
PSMode=CAM
AutoRoaming=0
RoamThreshold=70
APSDCapable=0
APSDAC=0;0;0;0
HT_RDG=1
HT_EXTCHA=0
HT_OpMode=0
HT_MpduDensity=4
HT_BW=1
HT_BADecline=0
HT_AutoBA=1
HT_AMSDU=0
HT_BAWinSize=64
HT_GI=1
HT_MCS=33
HT_MIMOPSMode=3
HT_DisallowTKIP=1
EthConvertMode=
EthCloneMac=
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0
CarrierDetect=0
AntDiversity=0
BeaconLostTime=4
FtSupport=0
Wapiifname=ra0
WapiPsk=
WapiPskType=
WapiUserCertPath=
WapiAsCertPath=
PSP_XLINK_MODE=0
WscManufacturer=
WscModelName=
WscDeviceName=
WscModelNumber=
WscSerialNumber=

```

Blacklist the default rt2800usb drivers via adding "blacklist rt2800usb" to /etc/modprobe.d/blacklist.conf and remove all rt* drivers that are currently loaded via:
```

sudo rmmod [rt*drivername]

```
You can view all loaded rt* modules via:
```

lsmod

```

Once all rt* module's have been removed, you can start the new driver (from within DPO_RT3070_LinuxSTA_V2.3.0.4_20100604):
```

cd os/linux
sudo modprobe rt3070sta

```
With any luck the module will start up and you'll have a wireless interface, check via iwconfig, you should see **ra0** and output similar to what I have below.
```

josh@HellFire:~$ iwconfig
lo        no wireless extensions.

ra0       Ralink STA  ESSID:"SKY61133"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:24:B2:43:B1:B6   
          Bit Rate=36 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=64/100  Signal level:-77 dBm  Noise level:-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

josh@HellFire:~$ 

```
Reboot and you should be able to see broadcasted SSID's and connect to your router and see within a few attempts!

Hope this helps.

Morphic

---

