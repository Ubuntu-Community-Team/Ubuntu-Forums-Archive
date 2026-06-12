---
title: "wifi connection bad in ubuntu, good in windows"
date: 2011-12-23
forum: Networking &amp; Wireless
---

### Post by liatodua on 2011-12-23
Hi,

I have dual boot (ubuntu 11.10 and windows 7) on a new Lenovo G470. wifi connection works just fine in windows. But in ubuntu it behaves strangely - connection is established but opening of sites takes terribly long. But if I reconnect - the sites open easily for some 2-3 minutes and then it slows down again.

Any suggestions?

And here is lshw information:

description: Wireless interface
                product: BCM4313 802.11b/g/n Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: wlan0
                version: 01
                serial: 60:d8:19:2a:d2:c4
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=brcmsmac driverversion=3.0.0-14-generic firmware=N/A ip=192.168.100.9 latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:e0400000-e0403fff
        *-usb:1

---

### Post by praseodym on 2011-12-23
Hi,

activate the Broadcom-STA driver and blacklist the modules **brcmsmac**, **bcma**, and **brcm80211**. Reboot after that and check:

```
ifconfig -a
iwconfig
rfkill list
lsmod
sudo iwlist scan
dmesg | egrep 'wl|country'
```

---

### Post by liatodua on 2011-12-24
I activated Broadcom-STA driver right after the installation of Ubuntu.

No idea how to blacklist the modules.

---

### Post by praseodym on 2011-12-25
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
Add the following new lines:

```
blacklist brcmsmac
blacklist bcma
blacklist brcm80211
```
save, close the editor, and reboot.

---

### Post by liatodua on 2011-12-25
Done. Connection seems to be much better.

Thank you!

And here are results of checking:

lia@lia-Lenovo-G470:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr b8:70:f4:4a:bb:56  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 

eth1      Link encap:Ethernet  HWaddr 60:d8:19:2a:d2:c4  
          inet addr:192.168.100.8  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::62d8:19ff:fe2a:d2c4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1395 errors:0 dropped:0 overruns:0 frame:374
          TX packets:762 errors:18 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:777665 (777.6 KB)  TX bytes:147108 (147.1 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lia@lia-Lenovo-G470:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:202  Noise level:161
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

lia@lia-Lenovo-G470:~$ rfkill list
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
lia@lia-Lenovo-G470:~$ lsmod
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  8 
parport_pc             36962  0 
ppdev                  17113  0 
joydev                 17693  0 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_conexant    62197  1 
lib80211_crypt_tkip    17390  0 
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
rts5139               351143  0 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
snd_seq_midi_event     14899  1 snd_seq_midi
v4l2_compat_ioctl32    17083  1 videodev
btusb                  18600  2 
bluetooth             166112  23 bnep,rfcomm,btusb
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
wl                   2568210  0 
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fglrx                2928969  0 
psmouse                73882  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i915                  566827  2 
serio_raw              13166  0 
lib80211               14991  2 lib80211_crypt_tkip,wl
mei                    41480  0 
drm_kms_helper         42558  1 i915
drm                   236290  3 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
ideapad_laptop         13871  0 
sparse_keymap          13890  1 ideapad_laptop
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
ahci                   26002  3 
libahci                26861  1 ahci
atl1c                  41643  0 
lia@lia-Lenovo-G470:~$ sudo iwlist scan
[sudo] password for lia: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:24:36:AC:EC:63
                    ESSID:"Anna"
                    Mode:Managed
                    Frequency=2.452 GHz (Channel 9)
                    Quality:3/5  Signal level:-68 dBm  Noise level:-98 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 34:08:04:BB:73:F4
                    ESSID:"dlink"
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:1/5  Signal level:-87 dBm  Noise level:-98 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD750050F204104A00011010440001021041000100103B00010310470010F29A13D1F77CAF78049D340804BB73F410210006442D4C696E6B102300074449522D333030102400074449522D3330301042000830303030303030301054000800060050F2040001101100074449522D333030100800020086
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
          Cell 03 - Address: 28:6E:D4:72:2D:D3
                    ESSID:"U.T.G"
                    Mode:Managed
                    Frequency=2.417 GHz (Channel 2)
                    Quality:2/5  Signal level:-72 dBm  Noise level:-98 dBm
                    IE: Unknown: DDAB0050F204104A0001101044000102103B0001031047001000000000000010000000286ED4722DD31021000C4D6667724E616D65486572651023000D4D6F64656C4E616D65486572651024000F4D6F64656C4E756D626572486572651042001053657269616C4E756D626572486572651054000800060050F2040001101100094578616D706C654150100800020086103C000103104900140024E26002000101600000020001600100020001
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 04 - Address: 28:6E:D4:72:31:11
                    ESSID:""
                    Mode:Managed
                    Frequency=2.437 GHz (Channel 6)
                    Quality:5/5  Signal level:-53 dBm  Noise level:-96 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

lia@lia-Lenovo-G470:~$ dmesg | egrep 'wl|country'
[   15.982822] wl 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.982834] wl 0000:08:00.0: setting latency timer to 64

Seems to be OK, no?

---

### Post by pjcdawkins on 2012-01-11
That fix worked for me too, many thanks.

---

