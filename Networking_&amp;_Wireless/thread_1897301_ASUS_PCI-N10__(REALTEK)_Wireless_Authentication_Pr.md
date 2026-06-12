---
title: "ASUS PCI-N10  (REALTEK) Wireless Authentication Problems"
date: 2011-12-19
forum: Networking &amp; Wireless
---

### Post by jackbusch on 2011-12-19
I bought a cheap (actually free) ASUS PCI-N10 wireless card off of Newegg and it worked beautifully under 10.10 using the drivers off of the Realtek website (made for Linux kernal 2.6.x). But when I upgraded to 11.10, things started getting funny. On the plus side, the wireless card was detected immediately and started trying to connect to my router. The bad news is that it would try and try and try and fail until it brought ALL my wireless connections in my house down.

Unfortunately, you cannot install the official Realtek wireless driver in 11.10 (something to do with autoconf.h being moved). But I did some more fiddling and found out that if I disabled my wireless security, it worked. Turns out that the problem is that Ubuntu can't seem to figure out what kind of authentication is needed. I had WPA and it was trying lord knows what. Then I switched to WPA2 and it thought it was WEP. Finally, I made a connection manually, telling Ubuntu what kind of authentication there was, and then connected to it as if it were a hidden network. That worked.

I'm foreseeing further inconvenience with the state of things. Is there a known fix for this? Or a way to get the Realtek drivers to install?

Thanks

---

### Post by praseodym on 2011-12-19
Hi,

please show:

```
lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
sudo iwlist scan
iwlist chan
dmesg | egrep 'rtl8|r8|country'
```

---

### Post by jackbusch on 2011-12-19
This is what it looks like at the moment, though right now I am successfully connected to wireless.

```
jack@jack-tower:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device [1043:84b5]
	Kernel driver in use: rtl8192ce
--
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
	Subsystem: Elitegroup Computer Systems Device [1019:8d48]
	Kernel driver in use: r8169
jack@jack-tower:~$ lsmod
Module                  Size  Used by
usbhid                 47198  0 
hid                    95463  1 usbhid
parport_pc             36962  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     32040  4 
rfcomm                 47946  0 
bnep                   18436  0 
bluetooth             166112  4 rfcomm,bnep
binfmt_misc            17540  1 
snd_hda_codec_realtek   330769  1 
arc4                   12529  2 
snd_hda_intel          33390  5 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  19 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nouveau               728662  3 
k10temp                13166  0 
edac_core              53746  0 
edac_mce_amd           23709  0 
psmouse                73882  0 
serio_raw              13166  0 
rtl8192ce              84775  0 
sp5100_tco             13791  0 
rtl8192c_common        75767  1 rtl8192ce
rtlwifi               110972  1 rtl8192ce
ttm                    76805  1 nouveau
mac80211              310872  3 rtl8192ce,rtl8192c_common,rtlwifi
drm_kms_helper         42558  1 nouveau
drm                   236330  5 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13423  1 nouveau
mxm_wmi                12979  1 nouveau
wmi                    19256  1 mxm_wmi
video                  19412  1 nouveau
i2c_piix4              13301  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
cfg80211              199587  2 rtlwifi,mac80211
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
pata_atiixp            13164  2 
r8169                  52788  0 
ahci                   26002  0 
libahci                26861  1 ahci
jack@jack-tower:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Slamson"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1E:2A:50:4A:12   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:341   Missed beacon:0

jack@jack-tower:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
jack@jack-tower:~$ sudo iwlist scan
[sudo] password for jack: 
Sorry, try again.
[sudo] password for jack: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1E:2A:50:4A:12
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"Slamson"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000011354135ff
                    Extra: Last beacon: 68ms ago
                    IE: Unknown: 0007536C616D736F6E
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0900037F0101001DFF7F
                    IE: Unknown: DD0C00037F0201010B0002A44000
                    IE: Unknown: DD1A00037F0301000000001E2A504A12021E2A504A1264002C011D08
          Cell 02 - Address: 00:13:46:1B:CC:40
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"angie wireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000005aeae454555
                    Extra: Last beacon: 228ms ago
                    IE: Unknown: 000E616E67696520776972656C657373
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
 

```

---

### Post by praseodym on 2011-12-20
Try to change the encryption to WPA2-AES, mixed WPA/WPA2 causes problems

---

### Post by jackbusch on 2011-12-21
I did that and it works a LITTLE bit better. Still kind of unreliable, though. About 1 out of 5 times I end up having to go into my basement to restart my router.

---

### Post by praseodym on 2011-12-22
Hi,


you can update the driver [COLOR="Red"](this driver version works only for 11.04 and 11.10)[/COLOR]:
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential
wget http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl_92ce_92se_92de_Ubuntu_11.x_mac80211_0004.0816.2011.tar.gz
tar xvf rtl_92ce_92se_92de_Ubuntu_11.x_mac80211_0004.0816.2011.tar.gz
cd rtl_92ce_92se_92de_Ubuntu_11.x_mac80211_0004.0816.2011
make
sudo make install
sudo cp -r firmware/* /lib/firmware 
```
Reboot. Be sure to install the metapackage of your kernel-headers suitable to you kernel architecture, too (e.g. linux-headers-generic, linux-headers-generic-pae, whatever).

---

