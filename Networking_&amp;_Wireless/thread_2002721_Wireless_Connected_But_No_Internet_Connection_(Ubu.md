---
title: "Wireless Connected But No Internet Connection (Ubuntu 12.04)"
date: 2012-06-13
forum: Networking &amp; Wireless
---

### Post by serhancan on 2012-06-13
I am using the same network for 2 days and everything was normal. However, today even though it shows me as connected to the network, I do not have internet connection. If I use ethernet cable instead of wireless, I am still able to connect to the internet. Also my friends are able to connect to the wireless network and they can get internet connection. I did not update or install anything since yesterday. Therefore I do not have any idea why it is happening. Here is some information about my connection:

I will be appreciate to any kind of help. Here is some information about my network properties:

```
root@ghostrider:/etc/resolvconf#     ping 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_req=1 ttl=64 time=0.042 ms
64 bytes from 127.0.0.1: icmp_req=2 ttl=64 time=0.023 ms
64 bytes from 127.0.0.1: icmp_req=3 ttl=64 time=0.036 ms
64 bytes from 127.0.0.1: icmp_req=4 ttl=64 time=0.040 ms
^C
--- 127.0.0.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2998ms
rtt min/avg/max/mdev = 0.023/0.035/0.042/0.008 ms 
root@ghostrider:/etc/resolvconf# ping 192.168.1.3
PING 192.168.1.3 (192.168.1.3) 56(84) bytes of data.
^C
--- 192.168.1.3 ping statistics ---
19 packets transmitted, 0 received, 100% packet loss, time 18143ms

root@ghostrider:/etc/resolvconf# ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
^C
--- 8.8.8.8 ping statistics ---
11 packets transmitted, 0 received, 100% packet loss, time 10079ms



root@ghostrider:/etc/resolvconf# cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux ghostrider 3.2.0-24-generic-pae #39-Ubuntu SMP Mon May 21 18:54:21 UTC 2012 i686     i686 i386 GNU/Linux
root@ghostrider:/etc/resolvconf# lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8131 Gigabit     Ethernet [1969:1063] (rev c0)
Subsystem: Lenovo Device [17aa:3956]
Kernel driver in use: atl1c
--
04:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n         Wireless LAN Controller [14e4:4727] (rev 01)
Subsystem: Broadcom Corporation Device [14e4:0510]
Kernel driver in use: wl
root@ghostrider:/etc/resolvconf# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 007: ID 0489:e00d Foxconn / Hon Hai 
Bus 001 Device 004: ID 1c7a:0801 LighTuning Technology Inc. Fingerprint Reader
Bus 001 Device 005: ID 064e:f219 Suyin Corp. 
Bus 002 Device 010: ID 0424:2412 Standard Microsystems Corp. 
Bus 002 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 011: ID 0403:6010 Future Technology Devices International, Ltd     FT2232C Dual USB-UART/FIFO IC
root@ghostrider:/etc/resolvconf# iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  ESSID:"PoliTekno"  
      Mode:Managed  Frequency:2.462 GHz  Access Point: 00:16:E3:40:C3:E4   
      Bit Rate=54 Mb/s   Tx-Power:24 dBm   
      Retry min limit:7   RTS thr:off   Fragment thr:off
      Power Management:off
      Link Quality=5/5  Signal level=-52 dBm  Noise level=-97 dBm
      Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
      Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

root@ghostrider:/etc/resolvconf# rfkill list all
0: brcmwl-0: Wireless LAN
Soft blocked: no
Hard blocked: no
1: ideapad_wlan: Wireless LAN
Soft blocked: no
Hard blocked: no
2: ideapad_bluetooth: Bluetooth
Soft blocked: no
Hard blocked: no
5: hci0: Bluetooth
Soft blocked: no
Hard blocked: no
root@ghostrider:/etc/resolvconf# lsmod
Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55605  1 vfat
usb_storage            39646  0 
uas                    17828  0 
snd_hda_codec_realtek   174055  1 
rfcomm                 38139  12 
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17830  2 
joydev                 17393  0 
ftdi_sio               35859  1 
usbserial              37173  3 ftdi_sio
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
acer_wmi               23612  0 
hid_logitech_dj        18177  0 
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
uvcvideo               67203  0 
btusb                  17912  2 
snd_seq_midi           13132  0 
videodev               86588  1 uvcvideo
bluetooth             158438  23 rfcomm,bnep,btusb
psmouse                72919  0 
usbhid                 41906  1 hid_logitech_dj
snd_rawmidi            25424  1 snd_seq_midi
intel_ips              17753  0 
serio_raw              13027  0 



    root@ghostrider:/etc/resolvconf#     ping 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_req=1 ttl=64 time=0.042 ms
64 bytes from 127.0.0.1: icmp_req=2 ttl=64 time=0.023 ms
64 bytes from 127.0.0.1: icmp_req=3 ttl=64 time=0.036 ms
64 bytes from 127.0.0.1: icmp_req=4 ttl=64 time=0.040 ms
^C
--- 127.0.0.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2998ms
rtt min/avg/max/mdev = 0.023/0.035/0.042/0.008 ms 
root@ghostrider:/etc/resolvconf# ping 192.168.1.3
PING 192.168.1.3 (192.168.1.3) 56(84) bytes of data.
^C
--- 192.168.1.3 ping statistics ---
19 packets transmitted, 0 received, 100% packet loss, time 18143ms

root@ghostrider:/etc/resolvconf# ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
^C
--- 8.8.8.8 ping statistics ---
11 packets transmitted, 0 received, 100% packet loss, time 10079ms



root@ghostrider:/etc/resolvconf# cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux ghostrider 3.2.0-24-generic-pae #39-Ubuntu SMP Mon May 21 18:54:21 UTC 2012 i686     i686 i386 GNU/Linux
root@ghostrider:/etc/resolvconf# lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8131 Gigabit     Ethernet [1969:1063] (rev c0)
Subsystem: Lenovo Device [17aa:3956]
Kernel driver in use: atl1c
--
04:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n         Wireless LAN Controller [14e4:4727] (rev 01)
Subsystem: Broadcom Corporation Device [14e4:0510]
Kernel driver in use: wl
root@ghostrider:/etc/resolvconf# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 007: ID 0489:e00d Foxconn / Hon Hai 
Bus 001 Device 004: ID 1c7a:0801 LighTuning Technology Inc. Fingerprint Reader
Bus 001 Device 005: ID 064e:f219 Suyin Corp. 
Bus 002 Device 010: ID 0424:2412 Standard Microsystems Corp. 
Bus 002 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 011: ID 0403:6010 Future Technology Devices International, Ltd     FT2232C Dual USB-UART/FIFO IC
root@ghostrider:/etc/resolvconf# iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  ESSID:"PoliTekno"  
      Mode:Managed  Frequency:2.462 GHz  Access Point: 00:16:E3:40:C3:E4   
      Bit Rate=54 Mb/s   Tx-Power:24 dBm   
      Retry min limit:7   RTS thr:off   Fragment thr:off
      Power Management:off
      Link Quality=5/5  Signal level=-52 dBm  Noise level=-97 dBm
      Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
      Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

root@ghostrider:/etc/resolvconf# rfkill list all
0: brcmwl-0: Wireless LAN
Soft blocked: no
Hard blocked: no
1: ideapad_wlan: Wireless LAN
Soft blocked: no
Hard blocked: no
2: ideapad_bluetooth: Bluetooth
Soft blocked: no
Hard blocked: no
5: hci0: Bluetooth
Soft blocked: no
Hard blocked: no
root@ghostrider:/etc/resolvconf# lsmod
Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55605  1 vfat
usb_storage            39646  0 
uas                    17828  0 
snd_hda_codec_realtek   174055  1 
rfcomm                 38139  12 
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17830  2 
joydev                 17393  0 
ftdi_sio               35859  1 
usbserial              37173  3 ftdi_sio
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
acer_wmi               23612  0 
hid_logitech_dj        18177  0 
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
uvcvideo               67203  0 
btusb                  17912  2 
snd_seq_midi           13132  0 
videodev               86588  1 uvcvideo
bluetooth             158438  23 rfcomm,bnep,btusb
psmouse                72919  0 
usbhid                 41906  1 hid_logitech_dj
snd_rawmidi            25424  1 snd_seq_midi
intel_ips              17753  0 
serio_raw              13027  0 
hid                    77367  2 hid_logitech_dj,usbhid
ideapad_laptop         17890  0 
sparse_keymap          13658  2 acer_wmi,ideapad_laptop
lib80211_crypt_tkip    17275  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
wl                   2646601  0 
wmi                    18744  1 acer_wmi
i915                  414672  3 
drm_kms_helper         45466  1 i915
snd_timer              28931  2 snd_pcm,snd_seq
mac_hid                13077  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
lib80211               14040  2 lib80211_crypt_tkip,wl
drm                   197692  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
snd                    62064  15         snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_se    q,snd_timer,snd_seq_device
video                  19068  1 i915
mei                    36570  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
atl1c                  36718  0 
root@ghostrider:/etc/resolvconf# nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth1  [PoliTekno] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        AC:81:12:7F:6B:B2

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    CnDStudios:      Infra, 00:12:BF:3F:0A:8A, Freq 2412 MHz, Rate 54 Mb/s, Strength 85 WPA
    AIR_TIES:        Infra, 00:1C:A8:6E:84:32, Freq 2462 MHz, Rate 54 Mb/s, Strength 72 WPA2
    VKSS:            Infra, 00:E0:4D:01:0D:47, Freq 2452 MHz, Rate 54 Mb/s, Strength 62 WPA2
    PROGEDA:         Infra, 00:1A:2A:60:BF:61, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA
    MobilAtolye:     Infra, 72:2B:C1:65:75:3C, Freq 2422 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    AIRTIES_WAR-141: Infra, 00:1C:A8:AB:AA:48, Freq 2422 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    tilda_biri_yeni: Infra, 54:E6:FC:B0:3C:E9, Freq 2437 MHz, Rate 0 Mb/s, Strength 34 WEP
    *PoliTekno:      Infra, 00:16:E3:40:C3:E4, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2
    AIRTIES_RJY:     Infra, 00:1A:2A:BD:85:16, Freq 2462 MHz, Rate 54 Mb/s, Strength 55 WEP

  IPv4 Settings:
    Address:         0.0.0.0
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        F0:DE:F1:6C:90:65

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off


root@ghostrider:/etc/resolvconf# sudo iwlist scan
lo        Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:16:E3:40:C3:E4
                ESSID:"PoliTekno"
                Mode:Managed
                Frequency:2.462 GHz (Channel 11)
                Quality:5/5  Signal level:-48 dBm  Noise level:-98 dBm
                IE: IEEE 802.11i/WPA2 Version 1
                    Group Cipher : CCMP
                    Pairwise Ciphers (1) : CCMP
                    Authentication Suites (1) : PSK
                Encryption key:on
                Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                          24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                          12 Mb/s; 48 Mb/s
      Cell 02 - Address: 00:E0:4D:01:0D:47
                ESSID:"VKSS"
                Mode:Managed
                Frequency:2.452 GHz (Channel 9)
                Quality:4/5  Signal level:-64 dBm  Noise level:-98 dBm
                IE: IEEE 802.11i/WPA2 Version 1
                    Group Cipher : CCMP
                    Pairwise Ciphers (1) : CCMP
                    Authentication Suites (1) : PSK
                Encryption key:on
                Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                          9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                          48 Mb/s; 54 Mb/s
      Cell 03 - Address: 00:1C:A8:AB:AA:48
                ESSID:"AIRTIES_WAR-141"
                Mode:Managed
                Frequency:2.422 GHz (Channel 3)
                Quality:2/5  Signal level:-77 dBm  Noise level:-95 dBm
                IE: IEEE 802.11i/WPA2 Version 1
                    Group Cipher : TKIP
                    Pairwise Ciphers (2) : CCMP TKIP
                    Authentication Suites (1) : PSK
                IE: Unknown:     DDB20050F204104A0001101049001E007FC5100018DE7CF0D8B70223A62711C18926AC290E30303030303139631044000102103B0001031047001076B31BC241E953CB99C3872554425A28102100194169725469657320576972656C657373204E6574776F726B73102300074169723534343010240008312E322E302E31321042000F4154303939313131383030323832351054000800060050F20400011011000741697235343430100800020084103C000103
                IE: WPA Version 1
                    Group Cipher : TKIP
                    Pairwise Ciphers (2) : CCMP TKIP
                    Authentication Suites (1) : PSK
                Encryption key:on
                Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                          24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                          12 Mb/s; 48 Mb/s
      Cell 04 - Address: 72:2B:C1:65:75:3C
                ESSID:"MobilAtolye"
                Mode:Managed
                Frequency:2.422 GHz (Channel 3)
                Quality:2/5  Signal level:-78 dBm  Noise level:-92 dBm
                IE: IEEE 802.11i/WPA2 Version 1
                    Group Cipher : TKIP
                    Pairwise Ciphers (2) : TKIP CCMP
                    Authentication Suites (1) : PSK
                IE: Unknown: DDA20050F204104A0001101044000102103B00010310470010BC329E001DD811B28601722BC165753C1021001D48756177656920546563686E6F6C6F6769657320436F2E2C204C74642E1023001C48756177656920576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F204000110110009487561776569415053100800020084103C000100
                IE: WPA Version 1
                    Group Cipher : TKIP
                    Pairwise Ciphers (2) : TKIP CCMP
                    Authentication Suites (1) : PSK
                Encryption key:on
                Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                          18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                          24 Mb/s; 48 Mb/s
      Cell 05 - Address: 00:12:BF:3F:0A:8A
                ESSID:"CnDStudios"
                Mode:Managed
                Frequency:2.412 GHz (Channel 1)
                Quality:5/5  Signal level:-47 dBm  Noise level:-95 dBm
                IE: WPA Version 1
                    Group Cipher : TKIP
                    Pairwise Ciphers (1) : TKIP
                    Authentication Suites (1) : PSK
                Encryption key:on
                Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                          6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                          36 Mb/s; 48 Mb/s; 54 Mb/s
      Cell 06 - Address: 00:1C:A8:6E:84:32
                ESSID:"AIR_TIES"
                Mode:Managed
                Frequency:2.462 GHz (Channel 11)
                Quality:5/5  Signal level:-56 dBm  Noise level:-98 dBm
                IE: IEEE 802.11i/WPA2 Version 1
                    Group Cipher : CCMP
                    Pairwise Ciphers (1) : CCMP
                    Authentication Suites (1) : PSK
                Encryption key:on
                Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                          6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                          36 Mb/s; 48 Mb/s; 54 Mb/s
      Cell 07 - Address: 54:E6:FC:B0:3C:E9
                ESSID:"tilda_biri_yeni"
                Mode:Managed
                Frequency:2.437 GHz (Channel 6)
                Quality:1/5  Signal level:-85 dBm  Noise level:-99 dBm
                Encryption key:on
                Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                          12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                          48 Mb/s; 54 Mb/s
      Cell 08 - Address: 18:28:61:16:57:C3
                ESSID:"obilet"
                Mode:Managed
                Frequency:2.437 GHz (Channel 6)
                Quality:1/5  Signal level:-88 dBm  Noise level:-99 dBm
                IE: IEEE 802.11i/WPA2 Version 1
                    Group Cipher : TKIP
                    Pairwise Ciphers (2) : CCMP TKIP
                    Authentication Suites (1) : PSK
                IE: WPA Version 1
                    Group Cipher : TKIP
                    Pairwise Ciphers (2) : CCMP TKIP
                    Authentication Suites (1) : PSK
                Encryption key:on
                Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                          24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                          12 Mb/s; 48 Mb/s
      Cell 09 - Address: 00:1A:2A:60:BF:61
                ESSID:"PROGEDA"
                Mode:Managed
                Frequency:2.462 GHz (Channel 11)
                Quality:2/5  Signal level:-75 dBm  Noise level:-98 dBm
                IE: WPA Version 1
                    Group Cipher : TKIP
                    Pairwise Ciphers (1) : TKIP
                    Authentication Suites (1) : PSK
                Encryption key:on
                Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                          6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                          36 Mb/s; 48 Mb/s; 54 Mb/s

    eth0      Interface doesn't support scanning.
```

Regards

---

### Post by chili555 on 2012-06-13
Would you please try a temporary fix? If it is effective, we'll make it persistent. Please open a terminal and do:```
sudo modprobe -r wl
sudo modprobe brcmsmac
iwconfig
```Do you have a wireless interface wlan0? Does it connect? Does it perform as expected?

---

### Post by serhancan on 2012-06-13
> **chili555 said:**
> Would you please try a temporary fix? If it is effective, we'll make it persistent. Please open a terminal and do:```
sudo modprobe -r wl
sudo modprobe brcmsmac
iwconfig
```Do you have a wireless interface wlan0? Does it connect? Does it perform as expected?

I do not know how it happened (I did not even restart my system or modem) but now I am able to connect to network. But thank you for your help!

---

### Post by chili555 on 2012-06-13
Do you mean you issued the commands I suggested and then it works as expected, or do you mean it just started working all by itself magically?

If it worked after you issued the commands, then we need to take some steps to make it persistent:```
sudo su
apt-get remove --purge bcmwl-kernel-source
gedit /etc/modprobe.d/blacklist.conf
```See if there is any blacklist there for brcmsmac. If so, remove it. Proofread, save and close gedit. Now do:```
echo brcmsmac >> /etc/modules
exit
```Now it ought to work perfectly on reboot.

---

### Post by olinart on 2012-06-14
We may have the same (UNSOLVED!) problem. Check the output of dmesg to see whether your wireless access associates and look at my posts of 3 weeks ago.  
Hopefully, validation from another user will get someone's attention.

---

### Post by chili555 on 2012-06-14
> **olinart said:**
> We may have the same (UNSOLVED!) problem. Check the output of dmesg to see whether your wireless access associates and look at my posts of 3 weeks ago.  
Hopefully, validation from another user will get someone's attention.I've looked at your thread and I fail to see any connection. I think serhancan has the wrong Broadcom driver. I think your case is either a poor Realtek driver or a problem with Network Manager.

You might look for and existing bug or file a new one: [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

Before you do, you might try Wicd instead of Network Manager and the backports wireless suite in Synaptic.

@serhancan--

Let's sort out the correct driver for your device before you do any other steps.

---

### Post by serhancan on 2012-08-02
> **chili555 said:**
> I've looked at your thread and I fail to see any connection. I think serhancan has the wrong Broadcom driver. I think your case is either a poor Realtek driver or a problem with Network Manager.

You might look for and existing bug or file a new one: [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

Before you do, you might try Wicd instead of Network Manager and the backports wireless suite in Synaptic.

@serhancan--

Let's sort out the correct driver for your device before you do any other steps.

I am so sorry that I did not see that your comments. I found a temporary solution to my problem and this is what I have been doing for about 3 weeks: I disable wireless and then re-enable it. With this solution I am able to successfully connect to the wireless network. However it is getting me sick right now. I just want to sit back, relax and wait for it to automatically get connected. Also sometimes this method does not work. Therefore I want to have an exact solution to my problem. Any helps will be appreciated.

---

### Post by chili555 on 2012-08-02
> **serhancan said:**
> I am so sorry that I did not see that your comments. I found a temporary solution to my problem and this is what I have been doing for about 3 weeks: I disable wireless and then re-enable it. With this solution I am able to successfully connect to the wireless network. However it is getting me sick right now. I just want to sit back, relax and wait for it to automatically get connected. Also sometimes this method does not work. Therefore I want to have an exact solution to my problem. Any helps will be appreciated.The next time you boot and the wireless is not working, check to see if the correct driver is loaded:```
lsmod | grep wl
```If it is not loaded, let's load it and see if your wireless comes to life:```
sudo modprobe wl
```If that does it, let's force wl to load in all cases:```
sudo su
echo wl >> /etc/modules
exit
```If that is not the problem, post back and we'll dig deeper.

---

### Post by serhancan on 2012-08-03
> **chili555 said:**
> The next time you boot and the wireless is not working, check to see if the correct driver is loaded:```
lsmod | grep wl
```If it is not loaded, let's load it and see if your wireless comes to life:```
sudo modprobe wl
```If that does it, let's force wl to load in all cases:```
sudo su
echo wl >> /etc/modules
exit
```If that is not the problem, post back and we'll dig deeper.

Today it happened again. Here is the lsmod output:

zero@ghostrider:~$ lsmod | grep wl
wl                   2646601  0 
lib80211               14040  2 lib80211_crypt_tkip,wl

Unfortunately sudo modprobe wl did not solve my problem.

---

### Post by chili555 on 2012-08-03
Let's dig deeper. The next time it boots and isn't connected, let's have a look at dmesg. We'll zip it so you can attach it to your reply using the paperclip tool at the top of the reply box.```
dmesg > serhancan.txt
iwconfig >> serhancan.txt
lsmod >> serhancan.txt
zip serhancan.zip serhancan.txt
```Please look in your user directory, find and attach serhancan.zip to your reply. Thanks.

---

### Post by ChemMeister on 2012-08-03
try the following:

```
sudo echo nameserver 8.8.8.8 > /etc/resolv.conf
```

---

