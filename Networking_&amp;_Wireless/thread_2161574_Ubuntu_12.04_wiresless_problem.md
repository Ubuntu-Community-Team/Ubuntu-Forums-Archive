---
title: "Ubuntu 12.04 wiresless problem"
date: 2013-07-11
forum: Networking &amp; Wireless
---

### Post by Kirminas on 2013-07-11
Hello , I have some isues with wireless. It nearly always asks for password and signal is very bad. I have tried compiling rt3090sta driver but got problems on [COLOR=#ff0000]make instal. [/COLOR]When I dropped it and tried to change to rt2860sta it installed correctly but when i blacklisted rt2800pci rt2x00 and 2 other, I enlisted in /etc/modules rt2860sta so it would start module on boot. But then I boot my card is unclaimed. I really dont know what to do I have read loads of topics but only now I think I need help.  I have 2 Antennas but I think it shouldnt be a problem. 
     Thanks in advance.

[B]
lshw -class Network[/B]

 *-network
       description: Wireless interface
       product: RT3091 Wireless 802.11n 1T/2R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan3
       version: 00
       serial: 1c:4b:d6:25:b4:03
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.2.0-23-generic-pae firmware=0.34 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:febf0000-febfffff

**lsmod**

Module                  Size  Used by
snd_hda_codec_hdmi     31775  4 
dm_multipath           22710  0 
psmouse                72846  0 
serio_raw              13027  0 
snd_usb_audio         101566  1 
snd_usbmidi_lib        24603  1 snd_usb_audio
snd_seq_midi           13132  0 
arc4                   12473  2 
snd_rawmidi            25424  2 snd_usbmidi_lib,snd_seq_midi
rt2800pci              18340  0 
snd_hda_codec_realtek   174055  1 
rt2800lib              53264  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
cdc_acm                22306  0 
rt2x00lib              48858  3 rt2800pci,rt2800lib,rt2x00pci
snd_seq_midi_event     14475  1 snd_seq_midi
snd_hda_intel          32765  5 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
mac80211              436455  3 rt2800lib,rt2x00pci,rt2x00lib
snd_hwdep              13276  2 snd_usb_audio,snd_hda_codec
snd_pcm                80845  4 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
cfg80211              178679  2 rt2x00lib,mac80211
eeprom_93cx6           12653  1 rt2800pci
bnep                   17830  2 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
rfcomm                 38139  0 
parport_pc             32114  0 
bluetooth             158438  10 bnep,rfcomm
ppdev                  12849  0 
mac_hid                13077  0 
snd                    62064  24 snd_hda_codec_hdmi,snd_usb_audio,snd_usbmidi_lib,snd_rawmidi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
usbhid                 41906  0 
hid                    77367  1 usbhid
nouveau               712294  3 
ttm                    65344  1 nouveau
drm_kms_helper         45466  1 nouveau
drm                   197692  5 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13199  1 nouveau
mxm_wmi                12859  1 nouveau
wmi                    18744  1 mxm_wmi
video                  19068  1 nouveau
r8169                  56321  0 
zram                   18193  1 


**ls /lib/firmware**

3.2.0-23-generic-pae          matrox
3com                          mrvl
acenic                        mts_cdma.fw
adaptec                       mts_edge.fw
advansys                      mts_gsm.fw
agere_ap_fw.bin               mts_mt9234mu.fw
agere_sta_fw.bin              mts_mt9234zba.fw
aic94xx-seq.fw                mwl8335_duplex.fw
amd-ucode                     mwl8k
ar3k                          myri10ge_ethp_z8e.dat
ar7010_1_1.fw                 myri10ge_eth_z8e.dat
ar7010.fw                     myri10ge_rss_ethp_z8e.dat
ar9170-1.fw                   myri10ge_rss_eth_z8e.dat
ar9170-2.fw                   myricom
ar9170.fw                       NPE-B
ar9271.fw                        NPE-C
asihpi                              ositech
ath3k-1.fw                      phanfw.bin
ath6k                              ql2100_fw.bin
atmel_at76c502_3com.bin      ql2200_fw.bin
atmel_at76c502.bin          ql2300_fw.bin
atmel_at76c502d.bin         ql2322_fw.bin
atmel_at76c502e.bin        ql2400_fw.bin
atmel_at76c504_2958.bin      ql2500_fw.bin
atmel_at76c504a_2958.bin     qlogic
atmel_at76c504.bin          r128
atmel_at76c506.bin         radeon
atmsar11.fw                   rt2561.bin
av7110                           rt2561s.bin
bnx2                              rt2661.bin
bnx2x                            rt2860.bin
brcm                              rt2870.bin
carl9                              170-1.fw                rt3070.bin
cis                                 rt3071.bin
cpia2                              rt3090.bin
cxgb3                             rt3290.bin
cxgb4                             rt73.bin
dabusb                           RTL8192E
dsp56k                        RTL8192SE
dvb-fe-xc5000-1.6.114.fw      rtl_nic
dvb-usb-dib0700-1.20.fw       rtlwifi
dvb-usb-terratec-h5-drxk.fw  s2250.fw
e100                          s2250_loader.fw
ea                            sb16
edgeport                      scripts
emi26                         slicoss
emi62                         sun
ene-ub6250                    sxg
ess                           TDA7706_OM_v2.5.1_boot.txt
f2255usb.bin                  TDA7706_OM_v3.0.2_boot.txt
GPL-3                         tehuti
hp                              ti_3410.fw
htc_7010.fw                   ti_5052.fw
htc_9271.fw                   ti-connectivity
i2400m-fw-usb-1.4.sbcf        tigon
i2400m-fw-usb-1.5.sbcf         tlg2300_firmware.bin
i6050-fw-usb-1.5.sbcf         tr_smctr.bin
intelliport2.bin              ttusb-budget
ipw2100-1.3.fw                ueagle-atm
ipw2100-1.3-i.fw              usbdux
ipw2100-1.3-p.fw              usbduxfast_firmware.bin
ipw2200-bss.fw                usbdux_firmware.bin
ipw2200-ibss.fw               usbduxsigma_firmware.bin
ipw2200-sniffer.fw            v4l-cx231xx-avcore-01.fw
isci                          v4l-cx23418-apu.fw
iwlwifi-1000-5.ucode          v4l-cx23418-cpu.fw
iwlwifi-100-5.ucode           v4l-cx23418-dig.fw
iwlwifi-105-6.ucode           v4l-cx2341x-dec.fw
iwlwifi-135-6.ucode           v4l-cx2341x-enc.fw
iwlwifi-2000-6.ucode          v4l-cx2341x-init.mpg
iwlwifi-2030-6.ucode          v4l-cx23885-avcore-01.fw
iwlwifi-3945-2.ucode          v4l-cx23885-enc.fw
iwlwifi-4965-2.ucode          v4l-cx25840.fw
iwlwifi-5000-5.ucode          v4l-pvrusb2-24xxx-01.fw
iwlwifi-5150-2.ucode          v4l-pvrusb2-29xxx-01.fw
iwlwifi-6000-4.ucode          vicam
iwlwifi-6000g2a-5.ucode       vntwusb.fw
iwlwifi-6000g2a-6.ucode       vxge
iwlwifi-6000g2b-6.ucode       WHENCE.ubuntu
iwlwifi-6050-5.ucode          whiteheat.fw
kaweth                        whiteheat_loader.fw
keyspan                       yam
keyspan_pda                   yamaha
korg                          zd1201-ap.fw
lbtf_usb.bin                   zd1201.fw
lgs8g75.fw                    zd1211
libertas

** rfkill list all**
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


**iwconfig**


eth3      no wireless extensions.


lo        no wireless extensions.


wlan3     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

---

### Post by kc1di on 2013-07-11
You should try building the rt3090sta again you may need to add these packages to get it to work :
build-essentials, devscripts and cdbs 

then try again.

---

### Post by Kirminas on 2013-07-11
I done as you said when do **make **it makes some errors


/home/turapp/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.c:2062:2: error: too few arguments to function &#8216;ieee80211_channel_to_frequency&#8217;
include/net/cfg80211.h:2224:12: note: declared here
/home/turapp/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.c: In function &#8216;CFG80211_SupBandInit&#8217;:
/home/turapp/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.c:2622:3: error: too few arguments to function &#8216;ieee80211_channel_to_frequency&#8217;
include/net/cfg80211.h:2224:12: note: declared here
make[2]: *** [/home/turapp/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.o]** Error 1**
make[1]: *** [_module_/home/turapp/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux] **Error 2**
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-23-generic-pae'
make: *** [LINUX] **Error 2**
turapp@turapp-inne-2:~/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO$ sudo make install
make -C /home/turapp/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/turapp/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA


, then I try to execute **make instal ** I have error. Iwill not copy/paste all but if you see he tries to find this file which doesnt exists. Any ideas???? 

install: cannot stat `rt3090sta.ko': No such file or directory
make[1]: *** [install] Error 1

When I make compiling do I have to specify which card I am using or other stuff coz I have never done this thing. Explanations would be appreciated.ty

---

### Post by kc1di on 2013-07-11
go to a terminal and type the following:
```
sudo rm /etc/wireless
```

Then try the build again.

---

### Post by praseodym on 2013-07-11
Try this one with dkms:

[http://forum.ubuntuusers.de/topic/nach-update-kein-wlan-mehr-433/2/#post-5641297](http://forum.ubuntuusers.de/topic/nach-update-kein-wlan-mehr-433/2/#post-5641297)

---

