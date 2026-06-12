---
title: "ubuntu 12.04 - how to install wireless driver for BCM43228"
date: 2012-07-06
forum: Networking &amp; Wireless
---

### Post by dilipmeena on 2012-07-06
Hi,
i am new to ubuntu, and i tried to install my wireless driver through "additional driver" but could not succeed, please help me to install following driver.

lspci -vv

02:00.0 Network controller: Broadcom Corporation BCM43228 802.11a/b/g/n
    Subsystem: Dell Wireless 1530 Half-size Mini PCIe Card

---

### Post by wildmanne39 on 2012-07-06
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
nm-tool
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by dilipmeena on 2012-07-06
Thanks for responding.......Please see below output

dilipmeena@ubuntu:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux ubuntu 3.2.0-030200-generic-pae #201201042035 SMP Thu Jan 5 01:52:43 UTC 2012 i686 i686 i386 GNU/Linux
dilipmeena@ubuntu:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
    Subsystem: Dell Wireless 1530 Half-size Mini PCIe Card [1028:0011]
    Kernel driver in use: wl
--
0a:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5761 Gigabit Ethernet PCIe [14e4:1681] (rev 10)
    Subsystem: Dell Device [1028:049b]
    Kernel driver in use: tg3
dilipmeena@ubuntu:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [G03] ---------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        38:59:F9:C0:22:4B

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    MGMNT:           Infra, 00:25:5E:1B:83:29, Freq 2412 MHz, Rate 54 Mb/s, Strength 49 WEP
    sudichats:       Infra, 00:25:5E:1B:83:28, Freq 2412 MHz, Rate 54 Mb/s, Strength 49 WEP
    Bravern:         Infra, 00:14:D1:42:91:F0, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WEP
    Aditya:          Infra, 00:25:5E:40:39:A0, Freq 2412 MHz, Rate 54 Mb/s, Strength 49 WPA
    Airtel202:       Infra, 00:19:36:10:48:CC, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WEP
    RT2561_3:        Infra, 00:19:36:10:48:CE, Freq 2437 MHz, Rate 54 Mb/s, Strength 37
    RT2561_2:        Infra, 00:19:36:10:48:CD, Freq 2437 MHz, Rate 54 Mb/s, Strength 30
    RT2561_4:        Infra, 00:19:36:10:48:CF, Freq 2437 MHz, Rate 54 Mb/s, Strength 37
    Broadcom:        Infra, 00:08:5C:EF:0A:C6, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WEP
    *G03:            Infra, 00:1B:57:EC:0A:03, Freq 2437 MHz, Rate 54 Mb/s, Strength 80 WEP
    HomeNet:         Infra, 00:25:5E:3C:E9:C8, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA2
    G303:            Infra, 00:25:5E:BB:6C:00, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WEP
    helix:           Infra, 00:1E:58:B8:BA:6D, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    Shadows:         Infra, 00:25:5E:17:98:8C, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WEP

  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: ttyUSB0 --------------------------------------------------------------
  Type:              Mobile Broadband (CDMA)
  Driver:            option1
  State:             disconnected
  Default:           no

  Capabilities:


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        D0:67:E5:36:D3:48

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


dilipmeena@ubuntu:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11  Access Point: Not-Associated   
          Link Quality:4  Signal level:196  Noise level:168
          Rx invalid nwid:0  invalid crypt:1  invalid misc:0

eth0      no wireless extensions.

dilipmeena@ubuntu:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
dilipmeena@ubuntu:~$ lsmod
Module                  Size  Used by
ndiswrapper           196722  0 [permanent]
lib80211_crypt_tkip    17175  0 
wl                   2646601  0 [permanent]
lib80211               14040  2 lib80211_crypt_tkip,wl
ppp_deflate            12828  0 
zlib_deflate           26506  1 ppp_deflate
bsd_comp               12803  0 
ppp_async              17254  1 
crc_ccitt              12595  1 ppp_async
snd_hda_codec_hdmi     31547  1 
snd_hda_codec_idt      59932  1 
bnep                   17749  2 
rfcomm                 37611  12 
snd_hda_intel          32396  2 
b43                   341426  0 
snd_hda_codec          99529  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
i915                  403610  3 
snd_pcm                76379  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
mac80211              425736  1 b43
snd_seq_midi           13132  0 
snd_rawmidi            25103  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
cfg80211              169219  2 b43,mac80211
snd_seq                51256  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         36749  1 i915
snd_timer              24609  2 snd_pcm,snd_seq
drm                   197086  4 i915,drm_kms_helper
snd_seq_device         14130  3 snd_seq_midi,snd_rawmidi,snd_seq
bcma                   25387  1 b43
snd                    55724  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia                 39578  0 
option                 25580  3 
ssb                    46176  1 b43
soundcore              12600  1 snd
usb_wwan               19682  1 option
uvcvideo               66495  0 
dell_wmi               12601  0 
psmouse                67491  0 
yenta_socket           27140  0 
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13152  1 i915
dell_laptop            13592  0 
usbserial              37116  8 option,usb_wwan
mei                    36087  0 
btusb                  17979  2 
sparse_keymap          13658  1 dell_wmi
pcmcia_rsrc            18292  1 yenta_socket
dcdbas                 14054  1 dell_laptop
videodev               86260  1 uvcvideo
wmi                    18645  1 dell_wmi
pcmcia_core            21506  3 pcmcia,yenta_socket,pcmcia_rsrc
ppdev                  12900  0 
lp                     13349  0 
bluetooth             153157  23 bnep,rfcomm,btusb
serio_raw              13027  0 
parport_pc             32006  0 
video                  18792  1 i915
joydev                 17313  0 
parport                36664  3 ppdev,lp,parport_pc
usbhid                 45614  0 
hid                    81147  1 usbhid
usb_storage            43811  0 
uas                    17587  0 
firewire_ohci          39598  0 
sdhci_pci              18264  0 
firewire_core          56694  1 firewire_ohci
sdhci                  27687  1 sdhci_pci
tg3                   140230  0 
crc_itu_t              12627  1 firewire_core
dilipmeena@ubuntu:~$

---

### Post by dilipmeena on 2012-07-06
some how i m able to connect but my chipset showing unknown

dilipmeena@ubuntu:~$ sudo airmon-ng start wlan0


Found 4 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!
-e 
PID    Name
952    NetworkManager
988    avahi-daemon
989    avahi-daemon
2355    wpa_supplicant


Interface    Chipset        Driver

wlan0        Unknown         wl (monitor mode enabled)

dilipmeena@ubuntu:~$

---

### Post by wildmanne39 on 2012-07-06
Hi, please copy and paste all commands one line at a time:
```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
```

I would change encryption to just wpa2 in your router and change it to wpa/wpa2 in network manager.

Also I do not know if monitor mode will work with the wl driver so please take it off monitor mode.
Thanks

---

