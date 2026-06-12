---
title: "Very slow wifi connection"
date: 2012-05-27
forum: Networking &amp; Wireless
---

### Post by michouthefirst on 2012-05-27
I have a very slow wifi connection (around 20K/s downloads) on a laptop that used to have windows on it with very fast wifi downloads.

Here is the output from iwconfig:

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Jidarc-2GHZ"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 58:6D:8F:03:13:3F   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:721  Invalid misc:205   Missed beacon:0

eth0      no wireless extensions.

The laptop is a Asus G53JW.

I have tried different things like the followig:

sudo iwconfig wlan0 rate 55M power off

and others, to no avail. Please, I would like a real working solution for this, as I am about to go back to Windows, but I'd rather not. The Kubuntu installation is 12.04.

This is a real show stopper.

---

### Post by wildmanne39 on 2012-05-27
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by lisati on 2012-05-27
*Thread moved to **Networking & Wireless**.*

---

### Post by michouthefirst on 2012-05-28
cat /etc/lsb-release; uname -a
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux jidarc-ubuntu-5 3.2.0-23-generic-pae #36-Ubuntu SMP Tue Apr 10 22:19:09 UTC 2012 i686 i686 i386 GNU/Linux
```lspci -nnk | grep -iA2 net
```
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
        Subsystem: AzureWave AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card [1a3b:1089]
        Kernel driver in use: ath9k
--
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
        Subsystem: ASUSTeK Computer Inc. U6V/U31J laptop [1043:16d5]
        Kernel driver in use: r8169
```lsusb
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 04f2:b1bb Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 0b05:1788 ASUSTek Computer, Inc. 
Bus 002 Device 003: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
```iwconfig
```
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Jidarc-2GHZ"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 58:6D:8F:03:13:3F   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:648  Invalid misc:190   Missed beacon:0

eth0      no wireless extensions.
```rfkill list all
```
0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
```lsmod
```
Module                  Size  Used by
snd_hda_codec_hdmi     31775  4 
bnep                   17830  2 
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 38139  16 
binfmt_misc            17292  1 
snd_hda_codec_realtek   174055  1 
nvidia              10962290  44 
snd_hda_intel          32765  5 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
arc4                   12473  2 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
ath9k                 117326  0 
mac80211              436455  1 ath9k
psmouse                72846  0 
serio_raw              13027  0 
i7core_edac            23382  0 
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
edac_core              46858  1 i7core_edac
joydev                 17393  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
btusb                  17912  1 
bluetooth             158438  23 bnep,rfcomm,btusb
ath9k_common           13781  1 ath9k
ath9k_hw              391523  2 ath9k,ath9k_common
rts_pstor             353215  0 
ath                    19387  3 ath9k,ath9k_common,ath9k_hw
cfg80211              178679  3 ath9k,mac80211,ath
snd                    62064  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mei                    36570  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
asus_laptop            23693  0 
sparse_keymap          13658  1 asus_laptop
input_polldev          13648  1 asus_laptop
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77367  1 usbhid
r8169                  56321  0 
video                  19068  0
```

Thanks for the welcome and your help, really appreciated.

---

### Post by wildmanne39 on 2012-05-28
Hi, please do:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Thanks

---

### Post by michouthefirst on 2012-05-28
Here is the output:

```
michel@jidarc-ubuntu-5:~$ echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
[sudo] password for michel: 
options ath9k nohwcrypt=1
michel@jidarc-ubuntu-5:~$ sudo modprobe -rfv ath9k
rmmod /lib/modules/3.2.0-23-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
rmmod /lib/modules/3.2.0-23-generic-pae/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.2.0-23-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
rmmod /lib/modules/3.2.0-23-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
rmmod /lib/modules/3.2.0-23-generic-pae/kernel/drivers/net/wireless/ath/ath.ko
rmmod /lib/modules/3.2.0-23-generic-pae/kernel/net/wireless/cfg80211.ko
michel@jidarc-ubuntu-5:~$ sudo modprobe -v ath9k
insmod /lib/modules/3.2.0-23-generic-pae/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.2.0-23-generic-pae/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.2.0-23-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko 
insmod /lib/modules/3.2.0-23-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko 
insmod /lib/modules/3.2.0-23-generic-pae/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.2.0-23-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko nohwcrypt=1 nohwcrypt=1

```I still have a slow connection.

---

### Post by michouthefirst on 2012-05-28
Should I reboot?

---

### Post by wildmanne39 on 2012-05-28
Hi, yes reboot and please show:
```
nm-tool
```
```
gksudo gedit /etc/modprobe.d/ath9k.conf
```
Please set your wireless settings in network manager to match the screenshots.
Thanks

---

### Post by michouthefirst on 2012-05-28
Here we go:

```
michel@jidarc-ubuntu-5:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        20:CF:30:7A:F8:71

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [Jidarc-2GHZ] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        48:5D:60:5B:CE:70

  Capabilities:
    Speed:           58 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    belkin54g:       Infra, 00:17:3F:E5:2F:A1, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    ALmaison:        Infra, 00:1D:7E:2E:8B:62, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA
    linksys_SES_50643: Infra, 00:14:BF:20:C7:96, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA
    daves network QC:Infra, 00:1D:6A:8A:A7:37, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WEP
    *Jidarc-2GHZ:    Infra, 58:6D:8F:03:13:3F, Freq 2437 MHz, Rate 54 Mb/s, Strength 63 WPA WPA2
    Gatineau:        Infra, 00:0C:42:FC:2E:8F, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    BELL888:         Infra, 00:1D:5A:DC:C8:31, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA
    Maison:          Infra, 94:44:52:4E:EC:94, Freq 2457 MHz, Rate 54 Mb/s, Strength 27 WPA
    NETGEAR:         Infra, 00:09:5B:ED:17:B4, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WEP
    zorro:           Infra, 00:18:D1:68:F5:A9, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WEP
    Etudes:          Infra, 00:26:5A:FD:DB:EA, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    BELL499:         Infra, 00:26:50:73:31:99, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WEP
    linksys:         Infra, 00:12:17:E2:C9:E0, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA
    Claude L:        Infra, 68:7F:74:E0:B8:B8, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    Cisco19822:      Infra, 58:6D:8F:41:5C:5F, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    VIDEOTRON7855:   Infra, 00:18:E7:DB:D6:A7, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    BELL123:         Infra, 34:EF:44:1C:90:71, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WEP
    venetiazanella:  Infra, 00:22:6B:63:84:B0, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    BELL493:         Infra, 00:1B:5B:E1:BC:F1, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA
    gspot:           Infra, 00:24:01:73:E9:3B, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    Arbaces:         Infra, 00:1B:11:CC:69:30, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA2
    BELL384:         Infra, 34:EF:44:5F:1E:41, Freq 2462 MHz, Rate 54 Mb/s, Strength 15 WEP

  IPv4 Settings:
    Address:         192.168.1.138
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             24.200.241.37
    DNS:             24.202.72.13
    DNS:             24.200.0.1

```For the contents of the file:
```
options ath9k nohwcrypt=1
```Also, my wifi configuration does not look like yours: Here are screenshots:

---

### Post by michouthefirst on 2012-05-28
I noticed my connection has improved a little I can now go up to 100KB/sec. When this laptop was configured with Windows, I could reach speeds as fast as 1.5MB/sec.

---

### Post by wildmanne39 on 2012-05-28
Hi, it is ok that you use a different manager, just make sure the settings are the same in the two screenshots.

Also in your router make sure if possible that the encryption setting is set to wpa2 only not mixed mode or wpa or wep.
Thanks

---

### Post by wildmanne39 on 2012-05-28
Hi, also you have many networks in your area that is hard for network manager, try changing your channel to 11 in the router.
Thanks

---

### Post by michouthefirst on 2012-05-29
The 2.4GHz band is pretty crowded here, on all channels. My router is dual-band and used to use a 5GHz dongle to play WoW at the time. I may try it, and I hope it works with Ubuntu. That may solve my problem.

Thanks for the time you took to help me, really appreciated.

---

