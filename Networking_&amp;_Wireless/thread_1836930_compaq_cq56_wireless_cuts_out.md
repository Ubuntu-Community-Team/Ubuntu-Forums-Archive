---
title: "compaq cq56 wireless cuts out"
date: 2011-08-31
forum: Networking &amp; Wireless
---

### Post by TJFT on 2011-08-31
Hi guys, this was my first post but I posted it in the wrong area, so now im here.

I have been having a problem with my internet, im running ubuntu 11.04, the internet always has full or almost full bars, but when i go to view a webpage it cuts out halfway though and I then have to deactivate and reactivate the internet, I viewed a couple other forums and saw no help because the links they suggested no longer excised.

Thanks for any help,
TJFT

---

### Post by wildmanne39 on 2011-09-01
HI, please run these commands and post the results here:
```
sudo lshw -C network
```
```
nm-tool
```
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by TJFT on 2011-09-01
*-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 5c:ac:4c:a5:f8:06
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-11-generic firmware=N/A ip=192.168.0.10 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d0100000-d010ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 60:eb:69:36:c0:fe
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:d0010000-d0010fff memory:d0000000-d000ffff memory:d0020000-d002ffff




NetworkManager Tool

State: connected

- Device: wlan0  [Auto 91cadi] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        5C:AC:4C:A5:F8:06

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *91cadi:         Infra, 00:26:F3:22:40:29, Freq 2457 MHz, Rate 54 Mb/s, Strength 62 WPA

  IPv4 Settings:
    Address:         192.168.0.10
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        60:EB:69:36:C0:FE

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off



lspci -nn | grep 0280
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)


lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"91cadi"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:26:F3:22:40:29   
          Bit Rate=54 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=46/70  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:28   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"91cadi"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:26:F3:22:40:29   
          Bit Rate=54 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=46/70  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:28   Missed beacon:0

tjft@tjft-Presario-CQ56-Notebook-PC:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39571  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255882  1 
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
arc4                   12473  2 
snd_hwdep              13274  1 snd_hda_codec
joydev                 17322  0 
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
radeon                900494  3 
snd_seq_midi_event     14475  1 snd_seq_midi
ath9k                 103633  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
mac80211              257001  1 ath9k
ttm                    65184  1 radeon
ath9k_common           13611  1 ath9k
drm_kms_helper         40745  1 radeon
ath9k_hw              300328  2 ath9k,ath9k_common
uvcvideo               66851  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   184164  5 radeon,ttm,drm_kms_helper
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
i2c_algo_bit           13184  1 radeon
ath                    19141  2 ath9k,ath9k_hw
psmouse                73312  0 
videodev               75143  1 uvcvideo
cfg80211              156212  3 ath9k,mac80211,ath
hp_wmi                 13418  0 
shpchp                 32345  0 
lp                     13349  0 
sp5100_tco             13456  0 
parport                36746  3 parport_pc,ppdev,lp
video                  18951  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
sparse_keymap          13666  1 hp_wmi
serio_raw              12990  0 
k10temp                12951  0 
i2c_piix4              13095  0 
ahci                   21591  3 
r8169                  42534  0 
libahci                25548  1 ahci

---

### Post by wildmanne39 on 2011-09-01
Hi, that happens a lot with this card two things to try first:

Hi, Is your network set to WPA and WPA2 mixed mode? That is often troublesome. If you can, try WPA2 only. You might also try:
Code:
```
sudo ifconfig wlan0 down
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
sudo ifconfig wlan0 up
```
if you run this command and it works then we will need to make it persistent.

Do not restart your computer this is a one time only method for testing purposes.
Thank you

---

### Post by TJFT on 2011-09-01
From what I can tell its mixed wpa/wpa2 and I put in the code, not sure if it works yet.

Thank you for your help
TJFT.

---

### Post by wildmanne39 on 2011-09-01
Hi, change mixed to just wpa2, with the commands I gave you it should fix the problem.
You can make it persistent like this.
```
sudo gedit /etc/modprobe.d/ath9k.conf
```
Add one line:
Code:
```
options ath9k nohwcrypt=1
```
Proofread, save and close gedit and you should be all set.
Thank you

---

### Post by TJFT on 2011-09-01
Thank you again for all your help, if it doesn´t cut out after an hour ile know it worked.

---

### Post by wildmanne39 on 2011-09-01
Hi, if it continues to work would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

