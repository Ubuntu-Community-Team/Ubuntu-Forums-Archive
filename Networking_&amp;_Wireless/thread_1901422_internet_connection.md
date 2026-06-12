---
title: "internet connection"
date: 2011-12-28
forum: Networking &amp; Wireless
---

### Post by Pat910art on 2011-12-28
I am running Ubuntu 11.10 on my Acer netbook.  As soon as I log in it connects to my wireless network, but more often than not when I try to go online [I am using Chromium] I get an error message saying 'This web page is not available'.

Why can't I go online even though it is clearly connected OK?

Can anyone help please?

---

### Post by wildmanne39 on 2011-12-28
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Flash__Gordon on 2011-12-29
I too have been having same/similar issues

david@david-asus:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux david-asus 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
david@david-asus:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
	Subsystem: AzureWave Device [1a3b:1139]
	Kernel driver in use: rtl8192ce
--
04:00.0 Ethernet controller [0200]: Atheros Communications AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1851]
	Kernel driver in use: atl1c
david@david-asus:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Gordon"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:21:29:B2:F1:57   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

david@david-asus:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
david@david-asus:~$ lsmod
Module                  Size  Used by
usbhid                 47198  0 
hid                    95463  1 usbhid
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282739  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
joydev                 17693  0 
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
arc4                   12529  2 
asus_nb_wmi            12517  0 
asus_wmi               20035  1 asus_nb_wmi
sparse_keymap          13890  1 asus_wmi
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
wmi                    19256  1 asus_wmi
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73882  0 
rtl8192ce              84775  0 
rtl8192c_common        75767  1 rtl8192ce
i915                  566827  3 
soundcore              12680  1 snd
rtlwifi               110972  1 rtl8192ce
drm_kms_helper         42558  1 i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mac80211              462092  3 rtl8192ce,rtl8192c_common,rtlwifi
serio_raw              13166  0 
drm                   236290  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
cfg80211              199587  2 rtlwifi,mac80211
mei                    41480  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ahci                   26002  2 
libahci                26861  1 ahci
atl1c                  41643  0 
xhci_hcd               82820  0 
david@david-asus:~$

---

### Post by wildmanne39 on 2011-12-29
Hi Flash__Gordon, please post:
```
nm-tool
```
```
sudo iwlist scan
```
```
ndiswrapper -l
```
```
sudo cat /var/log/syslog | grep -e rtl -e firmware -e wlan -e wpa -e etork | tail -n75
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Pat910art on 2011-12-30
pat@ACE:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux ACE 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux
pat@ACE:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Acer Incorporated [ALI] Device [1025:0590]
	Kernel driver in use: r8169
--
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: Foxconn International, Inc. Device [105b:e016]
	Kernel driver in use: ath9k
pat@ACE:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Pats_Wireless"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1B:9E:E0:87:E1   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:88   Missed beacon:0

pat@ACE:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
pat@ACE:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55577  1 vfat
usb_storage            44173  0 
uas                    17699  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
joydev                 17393  0 
sparse_keymap          13658  0 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
arc4                   12473  2 
uvcvideo               67271  0 
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
videodev               85626  1 uvcvideo
psmouse                73673  0 
snd_seq_midi           13132  0 
serio_raw              12990  0 
rts_pstor             353227  0 
ath9k                 112711  0 
snd_rawmidi            25241  1 snd_seq_midi
mac80211              393459  1 ath9k
snd_seq_midi_event     14475  1 snd_seq_midi
ath9k_common           13599  1 ath9k
ath9k_hw              293933  2 ath9k,ath9k_common
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ath                    19387  2 ath9k,ath9k_hw
cfg80211              172392  3 ath9k,mac80211,ath
snd_timer              28932  2 snd_pcm,snd_seq
wmi                    18744  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  505159  4 
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         32889  1 i915
drm                   192194  5 i915,drm_kms_helper
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  43104  0 
pat@ACE:~$ 

This is what I got in terminal but at the moment it's connecting to the web OK.

Pat

---

### Post by Flash__Gordon on 2011-12-30
#david@david-asus:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Gordon] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           yes
  HW Address:        E0:B9:A5:A8:5F:D9

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *Gordon:         Infra, 00:21:29:B2:F1:57, Freq 2442 MHz, Rate 54 Mb/s, Strength 91 WEP

  IPv4 Settings:
    Address:         192.168.0.122
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        54:04:A6:03:C2:82

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


david@david-asus:~$ sudo iwlist scan
[sudo] password for david: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:21:29:B2:F1:57
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"Gordon"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002ee46dd0d7
                    Extra: Last beacon: 84ms ago
                    IE: Unknown: 0006476F72646F6E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180202F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

david@david-asus:~$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
david@david-asus:~$ sudo cat /var/log/syslog | grep -e rtl -e firmware -e wlan -e wpa -e etork | tail -n75
Dec 30 17:17:52 david-asus wpa_supplicant[1295]: Trying to authenticate with 00:21:29:b2:f1:57 (SSID='Gordon' freq=2442 MHz)
Dec 30 17:17:52 david-asus NetworkManager[1132]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Dec 30 17:17:52 david-asus kernel: [  193.723707] wlan0: authenticate with 00:21:29:b2:f1:57 (try 1)
Dec 30 17:17:52 david-asus kernel: [  193.725368] wlan0: authenticated
Dec 30 17:17:52 david-asus wpa_supplicant[1295]: Trying to associate with 00:21:29:b2:f1:57 (SSID='Gordon' freq=2442 MHz)
Dec 30 17:17:52 david-asus wpa_supplicant[1295]: Associated with 00:21:29:b2:f1:57
Dec 30 17:17:52 david-asus kernel: [  193.725720] wlan0: associate with 00:21:29:b2:f1:57 (try 1)
Dec 30 17:17:52 david-asus kernel: [  193.728159] wlan0: RX ReassocResp from 00:21:29:b2:f1:57 (capab=0x411 status=0 aid=2)
Dec 30 17:17:52 david-asus kernel: [  193.728171] wlan0: associated
Dec 30 17:17:52 david-asus wpa_supplicant[1295]: CTRL-EVENT-CONNECTED - Connection to 00:21:29:b2:f1:57 completed (reauth) [id=0 id_str=]
Dec 30 17:17:52 david-asus NetworkManager[1132]: <info> (wlan0): supplicant interface state: authenticating -> completed
Dec 30 17:17:55 david-asus kernel: [  196.858284] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
Dec 30 17:17:55 david-asus kernel: [  196.858301] wlan0: Connection to AP 00:21:29:b2:f1:57 lost.
Dec 30 17:17:55 david-asus wpa_supplicant[1295]: CTRL-EVENT-DISCONNECTED bssid=00:21:29:b2:f1:57 reason=4
Dec 30 17:17:55 david-asus NetworkManager[1132]: <info> (wlan0): supplicant interface state: completed -> disconnected
Dec 30 17:17:55 david-asus NetworkManager[1132]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Dec 30 17:17:56 david-asus wpa_supplicant[1295]: Trying to authenticate with 00:21:29:b2:f1:57 (SSID='Gordon' freq=2442 MHz)
Dec 30 17:17:56 david-asus NetworkManager[1132]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Dec 30 17:17:56 david-asus kernel: [  198.175585] wlan0: authenticate with 00:21:29:b2:f1:57 (try 1)
Dec 30 17:17:56 david-asus wpa_supplicant[1295]: Trying to associate with 00:21:29:b2:f1:57 (SSID='Gordon' freq=2442 MHz)
Dec 30 17:17:56 david-asus wpa_supplicant[1295]: Associated with 00:21:29:b2:f1:57
Dec 30 17:17:56 david-asus wpa_supplicant[1295]: CTRL-EVENT-CONNECTED - Connection to 00:21:29:b2:f1:57 completed (reauth) [id=0 id_str=]
Dec 30 17:17:56 david-asus kernel: [  198.177148] wlan0: authenticated
Dec 30 17:17:56 david-asus kernel: [  198.177402] wlan0: associate with 00:21:29:b2:f1:57 (try 1)
Dec 30 17:17:56 david-asus kernel: [  198.179587] wlan0: RX ReassocResp from 00:21:29:b2:f1:57 (capab=0x411 status=0 aid=2)
Dec 30 17:17:56 david-asus kernel: [  198.179590] wlan0: associated
Dec 30 17:17:56 david-asus NetworkManager[1132]: <info> (wlan0): supplicant interface state: authenticating -> completed
Dec 30 17:17:59 david-asus kernel: [  201.233964] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
Dec 30 17:17:59 david-asus kernel: [  201.233974] wlan0: Connection to AP 00:21:29:b2:f1:57 lost.
Dec 30 17:17:59 david-asus wpa_supplicant[1295]: CTRL-EVENT-DISCONNECTED bssid=00:21:29:b2:f1:57 reason=4
Dec 30 17:17:59 david-asus NetworkManager[1132]: <info> (wlan0): supplicant interface state: completed -> disconnected
Dec 30 17:18:00 david-asus NetworkManager[1132]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Dec 30 17:18:01 david-asus wpa_supplicant[1295]: Trying to authenticate with 00:21:29:b2:f1:57 (SSID='Gordon' freq=2442 MHz)
Dec 30 17:18:01 david-asus NetworkManager[1132]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Dec 30 17:18:01 david-asus kernel: [  202.598891] wlan0: authenticate with 00:21:29:b2:f1:57 (try 1)
Dec 30 17:18:01 david-asus kernel: [  202.600487] wlan0: authenticated
Dec 30 17:18:01 david-asus wpa_supplicant[1295]: Trying to associate with 00:21:29:b2:f1:57 (SSID='Gordon' freq=2442 MHz)
Dec 30 17:18:01 david-asus wpa_supplicant[1295]: Associated with 00:21:29:b2:f1:57
Dec 30 17:18:01 david-asus wpa_supplicant[1295]: CTRL-EVENT-CONNECTED - Connection to 00:21:29:b2:f1:57 completed (reauth) [id=0 id_str=]
Dec 30 17:18:01 david-asus kernel: [  202.600826] wlan0: associate with 00:21:29:b2:f1:57 (try 1)
Dec 30 17:18:01 david-asus kernel: [  202.603138] wlan0: RX ReassocResp from 00:21:29:b2:f1:57 (capab=0x411 status=0 aid=2)
Dec 30 17:18:01 david-asus kernel: [  202.603147] wlan0: associated
Dec 30 17:18:01 david-asus NetworkManager[1132]: <info> (wlan0): supplicant interface state: authenticating -> completed
Dec 30 17:18:04 david-asus kernel: [  205.729570] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
Dec 30 17:18:04 david-asus kernel: [  205.729603] wlan0: Connection to AP 00:21:29:b2:f1:57 lost.
Dec 30 17:18:04 david-asus wpa_supplicant[1295]: CTRL-EVENT-DISCONNECTED bssid=00:21:29:b2:f1:57 reason=4
Dec 30 17:18:04 david-asus NetworkManager[1132]: <info> (wlan0): supplicant interface state: completed -> disconnected
Dec 30 17:18:04 david-asus NetworkManager[1132]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Dec 30 17:18:05 david-asus wpa_supplicant[1295]: Trying to authenticate with 00:21:29:b2:f1:57 (SSID='Gordon' freq=2442 MHz)
Dec 30 17:18:05 david-asus NetworkManager[1132]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Dec 30 17:18:05 david-asus kernel: [  207.038516] wlan0: authenticate with 00:21:29:b2:f1:57 (try 1)
Dec 30 17:18:05 david-asus wpa_supplicant[1295]: Trying to associate with 00:21:29:b2:f1:57 (SSID='Gordon' freq=2442 MHz)
Dec 30 17:18:05 david-asus wpa_supplicant[1295]: Associated with 00:21:29:b2:f1:57
Dec 30 17:18:05 david-asus wpa_supplicant[1295]: CTRL-EVENT-CONNECTED - Connection to 00:21:29:b2:f1:57 completed (reauth) [id=0 id_str=]
Dec 30 17:18:05 david-asus kernel: [  207.040184] wlan0: authenticated
Dec 30 17:18:05 david-asus kernel: [  207.040314] wlan0: associate with 00:21:29:b2:f1:57 (try 1)
Dec 30 17:18:05 david-asus kernel: [  207.042627] wlan0: RX ReassocResp from 00:21:29:b2:f1:57 (capab=0x411 status=0 aid=2)
Dec 30 17:18:05 david-asus kernel: [  207.042635] wlan0: associated
Dec 30 17:18:05 david-asus NetworkManager[1132]: <info> (wlan0): supplicant interface state: authenticating -> completed
Dec 30 17:18:10 david-asus kernel: [  212.283719] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
Dec 30 17:18:10 david-asus kernel: [  212.283755] wlan0: Connection to AP 00:21:29:b2:f1:57 lost.
Dec 30 17:18:10 david-asus wpa_supplicant[1295]: CTRL-EVENT-DISCONNECTED bssid=00:21:29:b2:f1:57 reason=4
Dec 30 17:18:10 david-asus NetworkManager[1132]: <info> (wlan0): supplicant interface state: completed -> disconnected
Dec 30 17:18:11 david-asus NetworkManager[1132]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Dec 30 17:18:12 david-asus wpa_supplicant[1295]: Trying to authenticate with 00:21:29:b2:f1:57 (SSID='Gordon' freq=2442 MHz)
Dec 30 17:18:12 david-asus NetworkManager[1132]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Dec 30 17:18:12 david-asus kernel: [  213.592300] wlan0: authenticate with 00:21:29:b2:f1:57 (try 1)
Dec 30 17:18:12 david-asus wpa_supplicant[1295]: Trying to associate with 00:21:29:b2:f1:57 (SSID='Gordon' freq=2442 MHz)
Dec 30 17:18:12 david-asus kernel: [  213.593961] wlan0: authenticated
Dec 30 17:18:12 david-asus kernel: [  213.594355] wlan0: associate with 00:21:29:b2:f1:57 (try 1)
Dec 30 17:18:12 david-asus kernel: [  213.596669] wlan0: RX ReassocResp from 00:21:29:b2:f1:57 (capab=0x411 status=0 aid=2)
Dec 30 17:18:12 david-asus kernel: [  213.596678] wlan0: associated
Dec 30 17:18:12 david-asus wpa_supplicant[1295]: Associated with 00:21:29:b2:f1:57
Dec 30 17:18:12 david-asus wpa_supplicant[1295]: CTRL-EVENT-CONNECTED - Connection to 00:21:29:b2:f1:57 completed (reauth) [id=0 id_str=]
Dec 30 17:18:12 david-asus NetworkManager[1132]: <info> (wlan0): supplicant interface state: authenticating -> completed
david@david-asus:~$ 


I installed the latest drivers from Realtek last night but it still says kernel driver in use so not sure how to correct this. Driver I used was "rtl_92ce_92se_92de_linux_mac80211_0004.0816.2011"

Sorry for the delayed reply - had to work today and used other laptop to avoid the issues. 

Flash

---

### Post by wildmanne39 on 2011-12-30
Hi Pat910art, please do this:
```
gksudo gedit /etc/modprobe.d/ath9k.conf
```
Add a single line:
```
options ath9k nohwcrypt=1
```
Proofread carefully, save and close gedit. Reboot.
Thanks

---

### Post by wildmanne39 on 2011-12-30
Hi, Flash__Gordon, can you connect to the internet at all?

You should set your encryption to wpa2 in your router if you can and see if that helps, also you might consider turning encryption off a few minutes just to see if it will connect then.
Thanks

---

### Post by Flash__Gordon on 2011-12-30
> **wildmanne39 said:**
> Hi, Flash__Gordon, can you connect to the internet at all?

You should set your encryption to wpa2 in your router if you can and see if that helps, also you might consider turning encryption off a few minutes just to see if it will connect then.
Thanks

Hi, Yes I can connect to internet. It will just gradually slow down and hang on web pages or stop downloading or fail at checking email. Works fine "wired" and works fine on 2 of my other laptops (10.04.3 with Broadcom chips) Only having issues with the Asus (RTL8188CE) and HP with RTL81** (can't recall at this moment - daughters laptop). While sometimes I can 
disable wireless with FN-F2 key wait a moment and re-enable then will be able to browse web or check mail again for a bit, other times must reboot. During the "issue" I can easily and happily surf with any of the other two laptops wirelessly. I understand the added security of wpa2 but I don't think that is suddenly an issue as I have had this network setup for years. I live in the bush so I am not too worried about anyone 'stealing' my wireless. (a Moose maybe or bear in summer LOL)
 It always connects to network effortlessly it is just like card is napping or something. Really *issing me off. I've been using Ubuntu for 5+ years now and generally have not had any real issues. Is there anyway to ensure that I am using the recently downloaded drivers instead of built in kernel drivers?

Flash

---

### Post by wildmanne39 on 2011-12-30
Hi Flash__Gordon run this command then see if it works better. ```
echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf . /dev/null
```

My understanding if you install updated drivers from an outside source they will automatically be used, but know every time you have an update to your kernel you will have to run make clean and make install again.
Thanks

---

### Post by Flash__Gordon on 2011-12-30
> **wildmanne39 said:**
> Hi Flash__Gordon run this command then see if it works better. ```
echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf . /dev/null
```

My understanding if you install updated drivers from an outside source they will automatically be used, but know every time you have an update to your kernel you will have to run make clean and make install again.
Thanks

 I already have my router using google dns servers. (that was one of the first things I did) I realize that I will have to reinstall drivers with every kernel update but small price to pay for stable wireless. I have searched over the internet in the last week or so for solutions and noticed that there are a lot of people with this chip or variation of it with same issue. I think I will install 9.10 on an external and see if issues are there,then maybe 10.04.3. I think this has been since Ver.3 or late 2. Not 100% on that. 

Flash

Really appreciate the assistance in this matter.

---

### Post by wildmanne39 on 2011-12-30
Hi, is this how you got the new driver if not do this, it is a driver for 11.04 and 11.10 only. 
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential
wget http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl_92ce_92se_92de_Ubuntu_11.x_mac80211_0004.0816.2011.tar.gz
tar xvf rtl_92ce_92se_92de_Ubuntu_11.x_mac80211_0004.0816.2011.tar.gz
cd rtl_92ce_92se_92de_Ubuntu_11.x_mac80211_0004.0816.2011
make
sudo make install
sudo cp -r firmware/* /lib/firmware
```

Be sure to install kernel-headers suitable to you kernel architecture, too (e.g. linux-headers-generic, linux-headers-generic-pae, etc).
Then reboot.

Also you could try 10.04 but I would not try 9.10 since it is not supported.
Thanks

---

### Post by Flash__Gordon on 2011-12-30
> **wildmanne39 said:**
> Hi, is this how you got the new driver if not do this, it is a driver for 11.04 and 11.10 only. 
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential
wget http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl_92ce_92se_92de_Ubuntu_11.x_mac80211_0004.0816.2011.tar.gz
tar xvf rtl_92ce_92se_92de_Ubuntu_11.x_mac80211_0004.0816.2011.tar.gz
cd rtl_92ce_92se_92de_Ubuntu_11.x_mac80211_0004.0816.2011
make
sudo make install
sudo cp -r firmware/* /lib/firmware
```

Be sure to install the metapackage of your kernel-headers suitable to you kernel architecture, too (e.g. linux-headers-generic, linux-headers-generic-pae, etc).
Then reboot.

Also you could try 10.04 but I would not try 9.10 since it is not supported.
Thanks

I will try this. I downloaded the driver from realtek website. How do I ensure I have the metapackages? I am running 64bit if that helps. Can I copy the whole code and run or seperately?

---

### Post by wildmanne39 on 2011-12-30
Hi, just copy the commands one line at a time and watch for errors and you should be fine.

The first line of code will install kernel-header and build- essentials which is being referred to here as metapackage.
Thanks

---

### Post by Flash__Gordon on 2011-12-30
> **wildmanne39 said:**
> Hi, just copy the commands one line at a time and watch for errors and you should be fine.

The first line of code will install kernel-header and build- essentials which is being referred to here as metapackage.
Thanks

Ok. I have already run the code just going to reboot now. Did not see any errors. Will let you know.

Thanks again,
Flash

---

### Post by Flash__Gordon on 2011-12-30
Ok wildmanne39, I seem to be ok but too soon to tell for certain. Here's hoping. Question - Will it be necessary to redo this with each update as when I used the drivers from the realtek website? 

Flash

---

### Post by wildmanne39 on 2011-12-30
Hi, I do not know for sure but I do not think so as long as you had dkms package installed before you installed the driver but I am not sure about that.

I know there are times when the dkms is included in the first line of the code with the headers and then for sure it does not have to be reinstalled.
Thanks

---

### Post by Flash__Gordon on 2011-12-30
> **wildmanne39 said:**
> Hi, I do not know for sure but I do not think so as long as you had dkms package installed before you installed the driver but I am not sure about that.

I know there are times when the dkms is included in the first line of the code with the headers and then for sure it does not have to be reinstalled.
Thanks

Ok. I do have dkms installed so I guess I'll find out on next update. Seems to be still working, hasn't came up with "unable to load page" or email failure, but sometimes it would work for 20 or 30 min before getting weird. It seemed to be dependent on load but couldn't proof it conclusively. I will keep you posted. If it works, maybe it will help someone else too. 

Flash

---

### Post by wildmanne39 on 2011-12-30
Hi, yes please keep me posted, if it does not work I have no more idea's though.
Thanks

---

### Post by Flash__Gordon on 2011-12-30
> **wildmanne39 said:**
> Hi, yes please keep me posted, if it does not work I have no more idea's though.
Thanks

That's ok, I don't have any more either! That's why I was on here. LOL 

Thanks again.

---

### Post by wildmanne39 on 2011-12-30
Hi, your welcome!

---

### Post by Pat910art on 2011-12-31
Hi wildmanne39

I have done as you suggested.  Strangely enough, even prior to doing this my netbook was connecting OK.  As I said in the first place, it was only intermittent.  Now, if I connect to any website I want to I presume it is working OK as a result of your suggestions.  So thanks in advance.  Will let you know if I have any further problems.

---

### Post by Flash__Gordon on 2011-12-31
Hi wildmanne39,

It is a little better. I don't have to shut off/on wireless to re-establish with outside world, but still have to wait for it (at least my email program isn't "failing to establish connection") . I ran a new Cat6 cable to use when the wireless starts to *iss me off at home (doesn't help much for on the road though). I hope this does get resolved in future kernels/versions of Ubuntu though. Thanks again for your time. 

Flash

---

### Post by wildmanne39 on 2011-12-31
Hi Pat910art, glad to hear it, I think it will continue to work if it does, would you please go to the top of the page and mark this thread solved by clicking on thread tools. 
Thank you

---

### Post by wildmanne39 on 2011-12-31
Hi Flash__Gordon, I have looked for more answers the only thing that I have found is again and I think I suggested this already is that linux connects better to wpa2 only mode usually instead of wep, you could also install wicd then uninstall network manager and see if that helps because wicd handles encryption better.

If you try wicd you need to know that it does not put an icon in the notification area and you must install wicd before uninstall network manager.
Thanks

---

### Post by Flash__Gordon on 2011-12-31
> **wildmanne39 said:**
> Hi Flash__Gordon, I have looked for more answers the only thing that I have found is again and I think I suggested this already is that linux connects better to wpa2 only mode usually instead of wep, you could also install wicd then uninstall network manager and see if that helps because wicd handles encryption better.

If you try wicd you need to know that it does not put an icon in the notification area and you must install wicd before uninstall network manager.
Thanks

  I understand what you are saying, however it does not explain the other laptops without Realtek chip do not have this concern. But I may give this a try if 12.04 LTS doesn't resolve it. I can wait until then. 

Thanks,
Flash

---

### Post by wildmanne39 on 2011-12-31
Hi, that is the point it all depends on how well the driver handles encryption and some drivers handle it better and different then others in linux.
Thanks

---

### Post by Flash__Gordon on 2011-12-31
> **wildmanne39 said:**
> Hi, that is the point it all depends on how well the driver handles encryption and some drivers handle it better and different then others in linux.
Thanks

  Ah! I see what you are saying. Ok, well tomorrow while recuperating from New Years Eve I will go into router and change that.  If that doesn't do it then I may get a wireless PCI-E card from [https://www.thinkpenguin.com/](https://www.thinkpenguin.com/) 

Thanks,
Flash

---

### Post by wowie on 2011-12-31
Hi, I too am new to ubuntu. I too was having problems with intermittant internet connection problems, until I could no longer connect at all. I went thru all the fixes that I could find on the internet, and nothing worked. I am now just trying to get the word out on how I fixed my problem. (Well, my sister fixed it in about 5 minutes, she is the Linux wizard in the family) Here's what worked for me.
Go to System, Preferences, Network Proxy. Under Network Proxy Preferences window, click on the Ignored Hosts tab. In the next window, see if you have this listed: (*.local) (no parentheses) If this is listed in the ignored hosts list, highlight it, then click on remove. After I did this, everything has worked just fine, no more problem, even after a cold boot. I just wanted to help if I can. (I have no idea how this got into my ignore hosts list) Good Luck.

---

### Post by d3v1150m471c on 2011-12-31
> **wildmanne39 said:**
> Hi Flash__Gordon run this command then see if it works better. ```
echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf . /dev/null
```
Thanks

[http://cr.yp.to/djbdns/run-cache.html](http://cr.yp.to/djbdns/run-cache.html)

---

### Post by Pat910art on 2012-01-12
Hi everyone who might be able to help.

I am still having intermittent connection problems on my Netbook.  It finds and connects to the wireless network no problem but when I actually try to get anything on the internet it says "This web page is not available" because the DNS look-up failed.  What does that mean?  Can I rectify it?  Other times it simply connects no problem.

---

### Post by wildmanne39 on 2012-01-12
Hi Pat910art, make your connection looks like the screenshots except leave auto connect checked.

Especially make sure to set the DNS server like the screenshot.
Thanks

---

### Post by dreamquartz on 2012-01-12
I have the same problem.
I hope I gathered all the info for my netbook.
Hope someone can help.
It's really frustrating.

Dream

```
**lspci -nnk | grep -iA2 net**
01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1629]
    Kernel driver in use: rtl8192ce
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:1584]
    Kernel driver in use: r8169

**lsmod**
Module                  Size  Used by
twofish_generic        16579  0 
twofish_i586           12503  0 
twofish_common         20823  2 twofish_generic,twofish_i586
serpent                29029  0 
xts                    12644  0 
gf128mul               14503  1 xts
dm_crypt               22565  0 
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
joydev                 17393  0 
binfmt_misc            17292  1 
arc4                   12473  2 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
ip6t_LOG               16846  4 
xt_hl                  12465  6 
ip6t_rt                12473  3 
snd_hda_codec_idt      60049  1 
nf_conntrack_ipv6      13581  7 
nf_defrag_ipv6         13139  1 nf_conntrack_ipv6
ipt_REJECT             12512  1 
ipt_LOG                12783  5 
xt_limit               12541  12 
uvcvideo               67271  0 
xt_tcpudp              12531  18 
videodev               85626  1 uvcvideo
xt_addrtype            12596  4 
xt_state               12514  14 
snd_hda_intel          24262  2 
snd_hda_codec          91859  2 snd_hda_codec_idt,snd_hda_intel
ip6table_filter        12711  1 
snd_hwdep              13276  1 snd_hda_codec
ip6_tables             22528  3 ip6t_LOG,ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12585  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
psmouse                73673  0 
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
serio_raw              12990  0 
nf_nat_ftp             12595  0 
nf_nat                 24958  1 nf_nat_ftp
nf_conntrack_ipv4      19084  9 nf_nat
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
nf_conntrack_ftp       13183  1 nf_nat_ftp
nf_conntrack           70103  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12706  1 
snd_seq_midi           13132  0 
ip_tables              18106  1 iptable_filter
x_tables               21975  13 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
i915                  509487  3 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
rtl8192ce              75448  0 
rtl8192c_common        69519  1 rtl8192ce
rtlwifi                95614  1 rtl8192ce
wmi                    18744  1 hp_wmi
mac80211              393459  3 rtl8192ce,rtl8192c_common,rtlwifi
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
snd                    55902  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              172427  2 rtlwifi,mac80211
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            44173  1 
uas                    17699  0 
ahci                   21634  2 
libahci                25727  1 ahci
r8169                  43104  0

**sudo ifconfig wlan0 down**

**sudo rmmod -f ath9k**
ERROR: Removing 'ath9k': No such file or directory

**sudo modprobe ath9k nohwcrypt=1**

**sudo ifconfig wlan0 up**

**cat /etc/lsb-release; uname -a**
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux *** 3.0.0-15-generic #25-Ubuntu SMP Mon Jan 2 17:45:26 UTC 2012 i686 i686 i386 GNU/Linux

**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"***"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: **:**:**:**:**:**   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

**rfkill list all**
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

**lsusb**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 003: ID 5986:0313 Acer, Inc 
[B]
sudo iwlist scan[/B]
[sudo] password for ***: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: **:**:**:**:**:**
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"***"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000f5bdc2674a
                    Extra: Last beacon: 84ms ago
                    IE: Unknown: 0003426550
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1606051700000000000000000000000000000000000000
                    IE: Unknown: DD7A0050F204104A00011010440001021041000100103B0001031047001059D2CAD626E79B61D57F0D55FE78BA48102100104C696E6B73797320627920436973636F102300075752543631304E1024000876322E30302E30301042000234321054000800060050F2040001101100075752543631304E100800020084
                    IE: Unknown: DD090010180207F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406051700000000000000000000000000000000000000
          Cell 02 - Address: **:**:**:**:**:**
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:off
                    ESSID:"hpsetup"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 560ms ago
                    IE: Unknown: 000768707365747570
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 06020000
```

---

### Post by peace012 on 2012-01-13
Hi,

I have problem in configuring internet connectivity over my ubuntu machine.
I have network of : 192.168.1.0, IP addr: 192.168.1.33, and my gateway is 112.115.87.63 . When dhcp is enabled i cannot connect to outside world, again i tried for static ip and started the network then it gives me error:
 SIOCADDRT: no process found
I tried to add route manually then also it gives the same error.

I hve configured the same network settings in my other disto of linux like Fedora,suse,CentoOS and Redhat . It works smoothly.

Please help me to get me out from this.

Thanks!

---

### Post by wildmanne39 on 2012-01-13
Hi dreamquartz, try everything that was listed for Flash__Gordon to try in this thread, it may help it may not.
Thanks

---

### Post by wildmanne39 on 2012-01-13
> **peace012 said:**
> Hi,

I have problem in configuring internet connectivity over my ubuntu machine.
I have network of : 192.168.1.0, IP addr: 192.168.1.33, and my gateway is 112.115.87.63 . When dhcp is enabled i cannot connect to outside world, again i tried for static ip and started the network then it gives me error:
 SIOCADDRT: no process found
I tried to add route manually then also it gives the same error.

I hve configured the same network settings in my other disto of linux like Fedora,suse,CentoOS and Redhat . It works smoothly.

Please help me to get me out from this.

Thanks!Hi peace012, you do not have to manually configure you settings in ubuntu unless you are user a server, this thread it about getting wireless connection working so if it is your wireless then post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod

``` 
here by clicking on new reply and click # and paste the information between the brackets.

Also remove the connection you created and let network manager find the connection.
Thank you

---

### Post by dreamquartz on 2012-01-13
> **wildmanne39 said:**
> Hi dreamquartz, try everything that was listed for Flash__Gordon to try in this thread, it may help it may not.
Thanks

I listed the 1st part you asked Flash_Gordon to list.

Thx,

Dream

```

[SIZE=3]**nm-tool**[/SIZE]
 [SIZE=3]NetworkManager Tool[/SIZE]
 

 [SIZE=3]State: connected (global)[/SIZE]
 

 [SIZE=3]- Device: wlan0  [***] ---------------------------------------------------------[/SIZE]
   [SIZE=3]Type:              802.11 WiFi[/SIZE]
   [SIZE=3]Driver:            rtl8192ce[/SIZE]
   [SIZE=3]State:             connected[/SIZE]
   [SIZE=3]Default:           yes[/SIZE]
   [SIZE=3]HW Address:        68:A3:C4:BA:E5:EB[/SIZE]
 

   [SIZE=3]Capabilities:[/SIZE]
     [SIZE=3]Speed:           150 Mb/s[/SIZE]
 

   [SIZE=3]Wireless Properties[/SIZE]
     [SIZE=3]WEP Encryption:  yes[/SIZE]
     [SIZE=3]WPA Encryption:  yes[/SIZE]
     [SIZE=3]WPA2 Encryption: yes[/SIZE]
 

   [SIZE=3]Wireless Access Points (* = current AP)[/SIZE]
     [SIZE=3]****:            Infra, 68:7F:74:18:7D:84, Freq 2437 MHz, Rate 54 Mb/s, Strength 88 WPA WPA2[/SIZE]
     [SIZE=3]hpsetup:         Ad-Hoc, DA:CE:46:0F:41:FA, Freq 2437 MHz, Rate 54 Mb/s, Strength 92[/SIZE]
 

   [SIZE=3]IPv4 Settings:[/SIZE]
     [SIZE=3]Address:         192.168.1.110[/SIZE]
     [SIZE=3]Prefix:          24 (255.255.255.0)[/SIZE]
     [SIZE=3]Gateway:         192.168.1.1[/SIZE]
 

     [SIZE=3]DNS:             192.168.1.1[/SIZE]
     [SIZE=3]DNS:             64.59.144.18[/SIZE]
     [SIZE=3]DNS:             64.59.144.19[/SIZE]
 

   [SIZE=3]IPv6 Settings:[/SIZE]
     [SIZE=3]Address:         2002:b841:4ef9:0:6aa3:c4ff:feba:e5eb[/SIZE]
     [SIZE=3]Prefix:          64[/SIZE]
     [SIZE=3]Gateway:         fe80::6a7f:74ff:fe18:7d82[/SIZE]
 

     [SIZE=3]Address:         fe80::6aa3:c4ff:feba:e5eb[/SIZE]
     [SIZE=3]Prefix:          64[/SIZE]
     [SIZE=3]Gateway:         fe80::6a7f:74ff:fe18:7d82[/SIZE]
 

 

 

 [SIZE=3]- Device: eth0 -----------------------------------------------------------------[/SIZE]
   [SIZE=3]Type:              Wired[/SIZE]
   [SIZE=3]Driver:            r8169[/SIZE]
   [SIZE=3]State:             unavailable[/SIZE]
   [SIZE=3]Default:           no[/SIZE]
   [SIZE=3]HW Address:        2C:27:D7:0B:BD:E3[/SIZE]
 

   [SIZE=3]Capabilities:[/SIZE]
     [SIZE=3]Carrier Detect:  yes[/SIZE]
     [SIZE=3]Speed:           10 Mb/s[/SIZE]
 

   [SIZE=3]Wired Properties[/SIZE]
     [SIZE=3]Carrier:         off[/SIZE]
 

 [SIZE=3]**sudo iwlist scan**[/SIZE]
 [SIZE=3]lo        Interface doesn't support scanning.[/SIZE]
 

 [SIZE=3]eth0      Interface doesn't support scanning.[/SIZE]
 

 [SIZE=3]wlan0     Scan completed :[/SIZE]
           [SIZE=3]Cell 01 - Address: 68:7F:74:18:7D:84[/SIZE]
                     [SIZE=3]Channel:6[/SIZE]
                     [SIZE=3]Frequency:2.437 GHz (Channel 6)[/SIZE]
                     [SIZE=3]Quality=63/70  Signal level=-47 dBm  [/SIZE] 
                     [SIZE=3]Encryption key:on[/SIZE]
                     [SIZE=3]ESSID:"***"[/SIZE]
                     [SIZE=3]Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s[/SIZE]
                               [SIZE=3]24 Mb/s; 36 Mb/s; 54 Mb/s[/SIZE]
                     [SIZE=3]Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s[/SIZE]
                     [SIZE=3]Mode:Master[/SIZE]
                     [SIZE=3]Extra:tsf=0000000c0c877236[/SIZE]
                     [SIZE=3]Extra: Last beacon: 84ms ago[/SIZE]
                     [SIZE=3]IE: Unknown: 0003426550[/SIZE]
                     [SIZE=3]IE: Unknown: 010882848B962430486C[/SIZE]
                     [SIZE=3]IE: Unknown: 030106[/SIZE]
                     [SIZE=3]IE: Unknown: 2A0104[/SIZE]
                     [SIZE=3]IE: Unknown: 2F0104[/SIZE]
                     [SIZE=3]IE: IEEE 802.11i/WPA2 Version 1[/SIZE]
                         [SIZE=3]Group Cipher : TKIP[/SIZE]
                         [SIZE=3]Pairwise Ciphers (2) : CCMP TKIP[/SIZE]
                         [SIZE=3]Authentication Suites (1) : PSK[/SIZE]
                     [SIZE=3]IE: Unknown: 32040C121860[/SIZE]
                     [SIZE=3]IE: Unknown: 2D1A7E181BFFFF000001000000000000000000000000000000000000[/SIZE]
                     [SIZE=3]IE: Unknown: 3D16060D1600000000000000000000000000000000000000[/SIZE]
                     [SIZE=3]IE: Unknown: DD7A0050F204104A00011010440001021041000100103B0001031047001059D2CAD626E79B61D57F0D55FE78BA48102100104C696E6B73797320627920436973636F102300075752543631304E1024000876322E30302E30301042000234321054000800060050F2040001101100075752543631304E100800020084[/SIZE]
                     [SIZE=3]IE: Unknown: DD090010180205F0050000[/SIZE]
                     [SIZE=3]IE: WPA Version 1[/SIZE]
                         [SIZE=3]Group Cipher : TKIP[/SIZE]
                         [SIZE=3]Pairwise Ciphers (2) : CCMP TKIP[/SIZE]
                         [SIZE=3]Authentication Suites (1) : PSK[/SIZE]
                     [SIZE=3]IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00[/SIZE]
                     [SIZE=3]IE: Unknown: DD1E00904C337E181BFFFF000001000000000000000000000000000000000000[/SIZE]
                     [SIZE=3]IE: Unknown: DD1A00904C34060D1600000000000000000000000000000000000000[/SIZE]
           [SIZE=3]Cell 02 - Address: DA:CE:46:0F:41:FA[/SIZE]
                     [SIZE=3]Channel:6[/SIZE]
                     [SIZE=3]Frequency:2.437 GHz (Channel 6)[/SIZE]
                     [SIZE=3]Quality=63/70  Signal level=-47 dBm  [/SIZE] 
                     [SIZE=3]Encryption key:off[/SIZE]
                     [SIZE=3]ESSID:"*****"[/SIZE]
                     [SIZE=3]Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s[/SIZE]
                     [SIZE=3]Mode:Ad-Hoc[/SIZE]
                     [SIZE=3]Extra:tsf=0000000000000000[/SIZE]
                     [SIZE=3]Extra: Last beacon: 564ms ago[/SIZE]
                     [SIZE=3]IE: Unknown: 000768707365747570[/SIZE]
                     [SIZE=3]IE: Unknown: 010482848B96[/SIZE]
                     [SIZE=3]IE: Unknown: 030106[/SIZE]
                     [SIZE=3]IE: Unknown: 06020000[/SIZE]
 

 [SIZE=3]**ndiswrapper -l**[/SIZE]
 [SIZE=3]The program 'ndiswrapper' is currently not installed.  You can install it by typing:[/SIZE]
 [SIZE=3]sudo apt-get install ndiswrapper-common[/SIZE]
 

 [SIZE=3]**sudo cat /var/log/syslog | grep -e rtl -e firmware -e wlan -e wpa -e etork | tail -n7**5[/SIZE]
 [SIZE=3]Jan 13 14:19:32 #### kernel: [ 4274.273437] wlan0: deauthenticating from 68:7f:74:18:7d:84 by local choice (reason=3)[/SIZE]
 [SIZE=3]Jan 13 14:19:32 #### wpa_supplicant[1094]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3[/SIZE]
 [SIZE=3]Jan 13 14:19:32 #### NetworkManager[876]: <info> (wlan0): supplicant interface state: completed -> disconnected[/SIZE]
 [SIZE=3]Jan 13 14:19:35 #### NetworkManager[876]: <info> Activation (wlan0) starting connection '***'[/SIZE]
 [SIZE=3]Jan 13 14:19:35 #### NetworkManager[876]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0][/SIZE]
 [SIZE=3]Jan 13 14:19:35 #### NetworkManager[876]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...[/SIZE]
 [SIZE=3]Jan 13 14:19:35 #### NetworkManager[876]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...[/SIZE]
 [SIZE=3]Jan 13 14:19:35 #### NetworkManager[876]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...[/SIZE]
 [SIZE=3]Jan 13 14:19:35 #### NetworkManager[876]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.[/SIZE]
 [SIZE=3]Jan 13 14:19:35 #### NetworkManager[876]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...[/SIZE]
 [SIZE=3]Jan 13 14:19:35 #### NetworkManager[876]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0][/SIZE]
 [SIZE=3]Jan 13 14:19:35 #### NetworkManager[876]: <info> Activation (wlan0/wireless): access point '***' has security, but secrets are required.[/SIZE]
 [SIZE=3]Jan 13 14:19:35 #### NetworkManager[876]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0][/SIZE]
 [SIZE=3]Jan 13 14:19:35 #### NetworkManager[876]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.[/SIZE]
 [SIZE=3]Jan 13 14:19:35 #### NetworkManager[876]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...[/SIZE]
 [SIZE=3]Jan 13 14:19:35 #### NetworkManager[876]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...[/SIZE]
 [SIZE=3]Jan 13 14:19:35 #### NetworkManager[876]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0][/SIZE]
 [SIZE=3]Jan 13 14:19:35 #### NetworkManager[876]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...[/SIZE]
 [SIZE=3]Jan 13 14:19:35 #### NetworkManager[876]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.[/SIZE]
 [SIZE=3]Jan 13 14:19:35 #### NetworkManager[876]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...[/SIZE]
 [SIZE=3]Jan 13 14:19:35 #### NetworkManager[876]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0][/SIZE]
 [SIZE=3]Jan 13 14:19:35 #### NetworkManager[876]: <info> Activation (wlan0/wireless): connection '***' has security, and secrets exist.  No new secrets needed.[/SIZE]
 [SIZE=3]Jan 13 14:19:35 #### NetworkManager[876]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.[/SIZE]
 [SIZE=3]Jan 13 14:19:35 #### kernel: [ 4277.174485] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin[/SIZE]
 [SIZE=3]Jan 13 14:19:35 #### NetworkManager[876]: <info> (wlan0): supplicant interface state: disconnected -> scanning[/SIZE]
 [SIZE=3]Jan 13 14:19:36 #### wpa_supplicant[1094]: Trying to authenticate with 68:7f:74:18:7d:84 (SSID='***' freq=2437 MHz)[/SIZE]
 [SIZE=3]Jan 13 14:19:36 #### kernel: [ 4278.374763] wlan0: authenticate with 68:7f:74:18:7d:84 (try 1)[/SIZE]
 [SIZE=3]Jan 13 14:19:36 #### wpa_supplicant[1094]: Trying to associate with 68:7f:74:18:7d:84 (SSID='***' freq=2437 MHz)[/SIZE]
 [SIZE=3]Jan 13 14:19:36 #### NetworkManager[876]: <info> (wlan0): supplicant interface state: scanning -> authenticating[/SIZE]
 [SIZE=3]Jan 13 14:19:36 #### kernel: [ 4278.376740] wlan0: authenticated[/SIZE]
 [SIZE=3]Jan 13 14:19:36 #### kernel: [ 4278.377316] wlan0: associate with 68:7f:74:18:7d:84 (try 1)[/SIZE]
 [SIZE=3]Jan 13 14:19:36 #### kernel: [ 4278.382104] wlan0: RX ReassocResp from 68:7f:74:18:7d:84 (capab=0x411 status=0 aid=5)[/SIZE]
 [SIZE=3]Jan 13 14:19:36 #### kernel: [ 4278.382114] wlan0: associated[/SIZE]
 [SIZE=3]Jan 13 14:19:36 #### NetworkManager[876]: <info> (wlan0): supplicant interface state: authenticating -> associating[/SIZE]
 [SIZE=3]Jan 13 14:19:36 #### wpa_supplicant[1094]: Associated with 68:7f:74:18:7d:84[/SIZE]
 [SIZE=3]Jan 13 14:19:36 #### NetworkManager[876]: <info> (wlan0): supplicant interface state: associating -> 4-way handshake[/SIZE]
 [SIZE=3]Jan 13 14:19:36 #### wpa_supplicant[1094]: WPA: Key negotiation completed with 68:7f:74:18:7d:84 [PTK=CCMP GTK=TKIP][/SIZE]
 [SIZE=3]Jan 13 14:19:36 #### wpa_supplicant[1094]: CTRL-EVENT-CONNECTED - Connection to 68:7f:74:18:7d:84 completed (reauth) [id=0 id_str=][/SIZE]
 [SIZE=3]Jan 13 14:19:36 #### NetworkManager[876]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed[/SIZE]
 [SIZE=3]Jan 13 14:19:36 #### NetworkManager[876]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network '***'.[/SIZE]
 [SIZE=3]Jan 13 14:19:36 #### NetworkManager[876]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.[/SIZE]
 [SIZE=3]Jan 13 14:19:36 #### NetworkManager[876]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...[/SIZE]
 [SIZE=3]Jan 13 14:19:36 #### NetworkManager[876]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0][/SIZE]
 [SIZE=3]Jan 13 14:19:36 #### NetworkManager[876]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)[/SIZE]
 [SIZE=3]Jan 13 14:19:36 #### NetworkManager[876]: <info> Activation (wlan0) Beginning IP6 addrconf.[/SIZE]
 [SIZE=3]Jan 13 14:19:36 #### avahi-daemon[872]: Withdrawing address record for fe80::6aa3:c4ff:feba:e5eb on wlan0.[/SIZE]
 [SIZE=3]Jan 13 14:19:36 #### avahi-daemon[872]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::6aa3:c4ff:feba:e5eb.[/SIZE]
 [SIZE=3]Jan 13 14:19:36 #### avahi-daemon[872]: Interface wlan0.IPv6 no longer relevant for mDNS.[/SIZE]
 [SIZE=3]Jan 13 14:19:36 #### NetworkManager[876]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.[/SIZE]
 [SIZE=3]Jan 13 14:19:36 #### NetworkManager[876]: <info> (wlan0): DHCPv4 state changed nbi -> preinit[/SIZE]
 [SIZE=3]Jan 13 14:19:36 #### dhclient: Listening on LPF/wlan0/68:a3:c4:ba:e5:eb[/SIZE]
 [SIZE=3]Jan 13 14:19:36 #### dhclient: Sending on   LPF/wlan0/68:a3:c4:ba:e5:eb[/SIZE]
 [SIZE=3]Jan 13 14:19:36 #### dhclient: DHCPREQUEST of 192.168.1.110 on wlan0 to 255.255.255.255 port 67[/SIZE]
 [SIZE=3]Jan 13 14:19:38 #### avahi-daemon[872]: Joining mDNS multicast group on interface wlan0.IPv6 with address 2002:b841:4ef9:0:6aa3:c4ff:feba:e5eb.[/SIZE]
 [SIZE=3]Jan 13 14:19:38 #### avahi-daemon[872]: New relevant interface wlan0.IPv6 for mDNS.[/SIZE]
 [SIZE=3]Jan 13 14:19:38 #### avahi-daemon[872]: Registering new address record for 2002:b841:4ef9:0:6aa3:c4ff:feba:e5eb on wlan0.*.[/SIZE]
 [SIZE=3]Jan 13 14:19:38 #### NetworkManager[876]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...[/SIZE]
 [SIZE=3]Jan 13 14:19:38 #### NetworkManager[876]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...[/SIZE]
 [SIZE=3]Jan 13 14:19:38 #### NetworkManager[876]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...[/SIZE]
 [SIZE=3]Jan 13 14:19:38 #### dhclient: DHCPREQUEST of 192.168.1.110 on wlan0 to 255.255.255.255 port 67[/SIZE]
 [SIZE=3]Jan 13 14:19:39 #### NetworkManager[876]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0][/SIZE]
 [SIZE=3]Jan 13 14:19:39 #### NetworkManager[876]: <info> Policy set '***' (wlan0) as default for IPv6 routing and DNS.[/SIZE]
 [SIZE=3]Jan 13 14:19:39 #### NetworkManager[876]: <info> Activation (wlan0) successful, device activated.[/SIZE]
 [SIZE=3]Jan 13 14:19:39 #### NetworkManager[876]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.[/SIZE]
 [SIZE=3]Jan 13 14:19:39 #### NetworkManager[876]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.[/SIZE]
 [SIZE=3]Jan 13 14:19:39 #### NetworkManager[876]: <info> (wlan0): DHCPv4 state changed preinit -> reboot[/SIZE]
 [SIZE=3]Jan 13 14:19:39 #### avahi-daemon[872]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.110.[/SIZE]
 [SIZE=3]Jan 13 14:19:39 #### avahi-daemon[872]: New relevant interface wlan0.IPv4 for mDNS.[/SIZE]
 [SIZE=3]Jan 13 14:19:39 #### avahi-daemon[872]: Registering new address record for 192.168.1.110 on wlan0.IPv4.[/SIZE]
 [SIZE=3]Jan 13 14:19:40 #### NetworkManager[876]: <info> Policy set '***' (wlan0) as default for IPv4 routing and DNS.[/SIZE]
 [SIZE=3]Jan 13 14:19:40 #### NetworkManager[876]: <info> Policy set '***' (wlan0) as default for IPv6 routing and DNS.[/SIZE]
 [SIZE=3]Jan 13 14:20:00 #### avahi-daemon[872]: Registering new address record for fe80::6aa3:c4ff:feba:e5eb on wlan0.*.[/SIZE]
 [SIZE=3]Jan 13 14:20:01 #### avahi-daemon[872]: Withdrawing address record for fe80::6aa3:c4ff:feba:e5eb on wlan0.[/SIZE]
 [SIZE=3]Jan 13 14:20:07 #### kernel: [ 4308.543788] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:68:7f:74:18:7d:82:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 [/SIZE] 
 [SIZE=3]Jan 13 14:20:21 #### avahi-daemon[872]: Registering new address record for fe80::6aa3:c4ff:feba:e5eb on wlan0.*.[/SIZE]
 

  

```

---

### Post by wildmanne39 on 2012-01-13
Hi, what I meant was to try everything that I told Flash_Gordon to try to fix his issue not post the results of the commands, but I do see that it says your firewall is blocking in coming and out going traffic.
Thanks

---

### Post by NGR on 2012-06-28
I have the same problem and i can't find any solution for a long time.
Can someone look into this issue or help.
I gathered system information that might be helpful.

Thanks

**Notebook**
```
HP ProBook 4530s
```

**cat /etc/lsb-release; uname -a**
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux zoo 3.2.0-25-generic #40-Ubuntu SMP Wed May 23 20:30:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

**lspci -nnk | grep -iA2 net**
```

25:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:169f]
	Kernel driver in use: rtl8192ce
--
26:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Hewlett-Packard Company Device [103c:167c]
	Kernel driver in use: r8169

```

**iwconfig**
```

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"ab2"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 20:CF:30:E4:E8:2A   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:609   Missed beacon:0

eth0      no wireless extensions.

tun0      no wireless extensions.

```

**rfkill list all**
```

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no

```

**lsmod**
```

Module                  Size  Used by
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
arc4                   12529  2 
rtl8192ce             137448  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
joydev                 17693  0 
radeon                804372  0 
ttm                    76949  1 radeon
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
rtlwifi               118718  1 rtl8192ce
jmb38x_ms              17646  0 
snd_rawmidi            30748  1 snd_seq_midi
memstick               16569  1 jmb38x_ms
psmouse                87692  0 
snd_seq_midi_event     14899  1 snd_seq_midi
serio_raw              13211  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              506816  2 rtl8192ce,rtlwifi
hid_logitech_dj        18593  0 
cfg80211              205544  2 rtlwifi,mac80211
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
hp_accel               25976  0 
lis3lv02d              19876  1 hp_accel
input_polldev          13896  1 lis3lv02d
i915                  468745  4 
wmi                    19256  1 hp_wmi
mei                    41616  0 
drm_kms_helper         46978  2 radeon,i915
drm                   242038  7 radeon,ttm,i915,drm_kms_helper
mac_hid                13253  0 
lp                     17799  0 
i2c_algo_bit           13423  2 radeon,i915
soundcore              15091  1 snd
parport                46562  3 parport_pc,ppdev,lp
video                  19596  1 i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
usbhid                 47199  1 hid_logitech_dj
hid                    99559  2 hid_logitech_dj,usbhid
r8169                  62099  0 
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci

```

**nm-tool**
```

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        E4:11:5B:2C:45:08

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [ab2] ---------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           yes
  HW Address:        20:10:7A:FA:0A:BE

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Homelan:         Infra, 00:1E:58:C6:B3:7D, Freq 2417 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    genya:           Infra, FC:75:16:41:F9:74, Freq 2412 MHz, Rate 54 Mb/s, Strength 77 WPA2
    Vadim K:         Infra, B8:A3:86:BC:9C:66, Freq 2462 MHz, Rate 54 Mb/s, Strength 16 WPA WPA2
    *ab2:            Infra, 20:CF:30:E4:E8:2A, Freq 2462 MHz, Rate 54 Mb/s, Strength 58 WPA2
    GL2:             Infra, 00:15:6D:A6:D1:01, Freq 2442 MHz, Rate 11 Mb/s, Strength 16
    TeNeT-WiFi:      Infra, 06:15:6D:A6:D1:01, Freq 2442 MHz, Rate 11 Mb/s, Strength 64
    Asus G-32:       Infra, 20:CF:30:98:ED:80, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2

  IPv4 Settings:
    Address:         192.168.1.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1
    DNS:             8.8.8.8
    DNS:             8.8.4.4
    DNS:             79.142.192.4


- VPN:  [dev-vpn-gb] -----------------------------------------------------------
  State:             connected
  Default:           no

  Message:

```

**sudo iwlist scan**
```

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 20:CF:30:E4:E8:2A
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=14 dBm  
                    Encryption key:on
                    ESSID:"ab2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000001537418e
                    Extra: Last beacon: 84ms ago
                    IE: Unknown: 0003616232
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001300000000000000000000000000000000000000
                    IE: Unknown: DD090010180205F0280000
          Cell 02 - Address: FC:75:16:41:F9:74
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"genya"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000013734efeb54
                    Extra: Last beacon: 4024ms ago
                    IE: Unknown: 000567656E7961
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000008127A
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706554120010E10
          Cell 03 - Address: 00:1E:58:C6:B3:7D
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=70/70  Signal level=18 dBm  
                    Encryption key:on
                    ESSID:"Homelan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000dabc31181
                    Extra: Last beacon: 3044ms ago
                    IE: Unknown: 0007486F6D656C616E
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101830002A3400027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010060FF7F
          Cell 04 - Address: B8:A3:86:BC:9C:66
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=20 dBm  
                    Encryption key:on
                    ESSID:"Vadim K"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000193f642148
                    Extra: Last beacon: 388ms ago
                    IE: Unknown: 0007566164696D204B
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706554120010E14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101034003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000029127A
                    IE: Unknown: DD07000C4307000000

eth0      Interface doesn't support scanning.

tun0      Interface doesn't support scanning.

```

---

### Post by wildmanne39 on 2012-06-28
Hi NGR, start here:
[http://ubuntuforums.org/showpost.php?p=11788913&postcount=22](http://ubuntuforums.org/showpost.php?p=11788913&postcount=22)
Thanks

---

### Post by NGR on 2012-06-28
I have tried software encryption and seems there is no changes: 
still have random disconnect, that looks like 100% package loss
but NM show "connected" and there are no records in dmesg and syslog

ll try to build driver from sources, but had no luck with this before

If you know, how to investigate, please help with this

---

### Post by wildmanne39 on 2012-06-29
Hi, please keep the settings from the link that I gave you and change your wireless settings in network manager to match the screenshots then if you still cannot connect post the output of:
```
sudo cat /var/log/syslog | grep -e 819 -e firmware -e wpa -e wlan -e etork | tail -n55
``` 
Thanks

---

### Post by NGR on 2012-06-30
> change your wireless settings in network manager to match the screenshots

already done

**sudo cat /var/log/syslog | grep -e 819 -e firmware -e wpa -e wlan -e etork | tail -n55**

```

Jun 29 23:01:34 zoo NetworkManager[998]: <info> (wlan0): taking down device.
Jun 30 22:05:08 zoo kernel: [63733.781905] PM: suspend of drv:sd dev:0:0:0:0 complete after 382.442 msecs
Jun 30 22:05:08 zoo kernel: [63733.781949] PM: suspend of drv:scsi dev:target0:0:0 complete after 382.468 msecs
Jun 30 22:05:08 zoo kernel: [63733.781983] PM: suspend of drv:scsi dev:host0 complete after 329.304 msecs
Jun 30 22:05:08 zoo kernel: [63733.819076] PM: suspend of drv: dev:pci0000:00 complete after 364.940 msecs
Jun 30 22:05:08 zoo kernel: [63733.819088] PM: suspend of devices complete after 419.852 msecs
Jun 30 22:05:08 zoo kernel: [63733.819091] PM: suspend devices took 0.420 seconds
Jun 30 22:05:08 zoo kernel: [63733.819267] xhci_hcd 0000:27:00.0: PME# enabled
Jun 30 22:05:08 zoo kernel: [63733.819277] pcieport 0000:00:1c.7: wake-up capability enabled by ACPI
Jun 30 22:05:08 zoo kernel: [63734.508521] rtl8192ce 0000:25:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x10a)
Jun 30 22:05:08 zoo kernel: [63734.508547] rtl8192ce 0000:25:00.0: restoring config space at offset 0x6 (was 0x4, writing 0xd4700004)
Jun 30 22:05:08 zoo kernel: [63734.508556] rtl8192ce 0000:25:00.0: restoring config space at offset 0x4 (was 0x1, writing 0x3001)
Jun 30 22:05:08 zoo kernel: [63734.508562] rtl8192ce 0000:25:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
Jun 30 22:05:08 zoo kernel: [63734.508571] rtl8192ce 0000:25:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
Jun 30 22:05:08 zoo kernel: [63734.528191] snd_hda_intel 0000:00:1b.0: power state changed by ACPI to D0
Jun 30 22:05:08 zoo kernel: [63734.528197] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jun 30 22:05:09 zoo NetworkManager[998]: <info> (wlan0): now managed
Jun 30 22:05:09 zoo NetworkManager[998]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 30 22:05:09 zoo NetworkManager[998]: <info> (wlan0): bringing up device.
Jun 30 22:05:09 zoo kernel: [63738.484974] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
Jun 30 22:05:09 zoo NetworkManager[998]: <info> (wlan0): preparing device.
Jun 30 22:05:09 zoo NetworkManager[998]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jun 30 22:05:09 zoo kernel: [63738.828302] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 30 22:05:09 zoo NetworkManager[998]: <info> (wlan0): supplicant interface state: starting -> ready
Jun 30 22:05:09 zoo NetworkManager[998]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jun 30 22:05:09 zoo NetworkManager[998]: <info> (wlan0): supplicant interface state: ready -> inactive
Jun 30 22:05:11 zoo NetworkManager[998]: <info> Activation (wlan0) starting connection 'ab2'
Jun 30 22:05:11 zoo NetworkManager[998]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun 30 22:05:11 zoo NetworkManager[998]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 30 22:05:11 zoo NetworkManager[998]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 30 22:05:11 zoo NetworkManager[998]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 30 22:05:11 zoo NetworkManager[998]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 30 22:05:11 zoo NetworkManager[998]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 30 22:05:11 zoo NetworkManager[998]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 30 22:05:11 zoo NetworkManager[998]: <info> Activation (wlan0/wireless): access point 'ab2' has security, but secrets are required.
Jun 30 22:05:11 zoo NetworkManager[998]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jun 30 22:05:11 zoo NetworkManager[998]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 30 22:05:11 zoo NetworkManager[998]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 30 22:05:11 zoo NetworkManager[998]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 30 22:05:11 zoo NetworkManager[998]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Jun 30 22:05:11 zoo NetworkManager[998]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 30 22:05:11 zoo NetworkManager[998]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 30 22:05:11 zoo NetworkManager[998]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 30 22:05:11 zoo NetworkManager[998]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 30 22:05:11 zoo NetworkManager[998]: <info> Activation (wlan0/wireless): connection 'ab2' has security, and secrets exist.  No new secrets needed.
Jun 30 22:05:11 zoo NetworkManager[998]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 30 22:05:11 zoo NetworkManager[998]: <info> (wlan0): supplicant interface state: inactive -> scanning
Jun 30 22:05:12 zoo wpa_supplicant[1047]: Trying to authenticate with 20:cf:30:e4:e8:2a (SSID='ab2' freq=2462 MHz)
Jun 30 22:05:12 zoo NetworkManager[998]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jun 30 22:05:12 zoo kernel: [63741.586306] wlan0: authenticate with 20:cf:30:e4:e8:2a (try 1)
Jun 30 22:05:12 zoo wpa_supplicant[1047]: Trying to associate with 20:cf:30:e4:e8:2a (SSID='ab2' freq=2462 MHz)
Jun 30 22:05:12 zoo kernel: [63741.588284] wlan0: authenticated
Jun 30 22:05:12 zoo kernel: [63741.588610] wlan0: associate with 20:cf:30:e4:e8:2a (try 1)
Jun 30 22:05:12 zoo kernel: [63741.590668] wlan0: RX AssocResp from 20:cf:30:e4:e8:2a (capab=0x411 status=0 aid=5)
Jun 30 22:05:12 zoo kernel: [63741.590677] wlan0: associated
Jun 30 22:05:12 zoo wpa_supplicant[1047]: Associated with 20:cf:30:e4:e8:2a
Jun 30 22:05:12 zoo NetworkManager[998]: <info> (wlan0): supplicant interface state: authenticating -> 4-way handshake
Jun 30 22:05:12 zoo kernel: [63741.592304] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jun 30 22:05:12 zoo wpa_supplicant[1047]: WPA: Key negotiation completed with 20:cf:30:e4:e8:2a [PTK=CCMP GTK=TKIP]
Jun 30 22:05:12 zoo wpa_supplicant[1047]: CTRL-EVENT-CONNECTED - Connection to 20:cf:30:e4:e8:2a completed (auth) [id=0 id_str=]
Jun 30 22:05:12 zoo NetworkManager[998]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Jun 30 22:05:12 zoo NetworkManager[998]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'ab2'.
Jun 30 22:05:12 zoo NetworkManager[998]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun 30 22:05:12 zoo NetworkManager[998]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jun 30 22:05:12 zoo NetworkManager[998]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jun 30 22:05:12 zoo NetworkManager[998]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun 30 22:05:12 zoo NetworkManager[998]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jun 30 22:05:12 zoo NetworkManager[998]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jun 30 22:05:12 zoo dhclient: Listening on LPF/wlan0/20:10:7a:fa:0a:be
Jun 30 22:05:12 zoo dhclient: Sending on   LPF/wlan0/20:10:7a:fa:0a:be
Jun 30 22:05:12 zoo dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jun 30 22:05:13 zoo avahi-daemon[993]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::2210:7aff:fefa:abe.
Jun 30 22:05:13 zoo avahi-daemon[993]: New relevant interface wlan0.IPv6 for mDNS.
Jun 30 22:05:13 zoo avahi-daemon[993]: Registering new address record for fe80::2210:7aff:fefa:abe on wlan0.*.
Jun 30 22:05:15 zoo dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Jun 30 22:05:20 zoo dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Jun 30 22:05:22 zoo kernel: [63752.092404] wlan0: no IPv6 routers present
Jun 30 22:05:34 zoo dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Jun 30 22:05:39 zoo dhclient: DHCPREQUEST of 192.168.1.105 on wlan0 to 255.255.255.255 port 67
Jun 30 22:05:39 zoo NetworkManager[998]: <info> (wlan0): DHCPv4 state changed preinit -> bound
Jun 30 22:05:39 zoo NetworkManager[998]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jun 30 22:05:39 zoo NetworkManager[998]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Jun 30 22:05:39 zoo avahi-daemon[993]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.105.
Jun 30 22:05:39 zoo avahi-daemon[993]: New relevant interface wlan0.IPv4 for mDNS.
Jun 30 22:05:39 zoo avahi-daemon[993]: Registering new address record for 192.168.1.105 on wlan0.IPv4.
Jun 30 22:05:40 zoo NetworkManager[998]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Jun 30 22:05:40 zoo NetworkManager[998]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jun 30 22:05:40 zoo NetworkManager[998]: <info> Policy set 'ab2' (wlan0) as default for IPv4 routing and DNS.
Jun 30 22:05:40 zoo NetworkManager[998]: <info> Activation (wlan0) successful, device activated.
Jun 30 22:05:40 zoo NetworkManager[998]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.

```

As you can see there are no records about drop connection, but it does happens

---

### Post by wildmanne39 on 2012-06-30
Hi, I believe you are having an issue with network manager, please do [COLOR="Red"]in the following order[/COLOR]:
```
sudo apt-get install wicd
```
Then:
```
sudo apt-get purge network-manager network-manager-gnome
```

I believe dhcp has to be set to dhclient.
Then reboot.
Thanks

---

### Post by dreamquartz on 2012-07-07
> **wildmanne39 said:**
> Hi, what I meant was to try everything that I told Flash_Gordon to try to fix his issue not post the results of the commands, but I do see that it says your firewall is blocking in coming and out going traffic.
Thanks

Sorry for the belayed response on this issue.
updated to 12.04, and no problems what so ever.

Thx,

Dream

---

