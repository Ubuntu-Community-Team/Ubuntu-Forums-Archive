---
title: "My wireless internet connection keeps failing to connect"
date: 2013-05-24
forum: Networking &amp; Wireless
---

### Post by Dadalama on 2013-05-24
I get on the internet and it is fine for a period of time. Eventually the wireless connection will drop. While I can still see the connections it won't allow me to reconnect. I've found by removing the network adapter (belkin n100) and plugging it back in it will connect again. Also restarting the computer had the same effect. Though lately it has a tendency to only stay on for a minute or two. This shorter time periods seem to happen more later in the afternoon and into the night. 

I'm using Ubuntu 12.04

---

### Post by praseodym on 2013-05-24
Please show the terminal outputs of these commands:
```

lsusb
lsmod
ifconfig -a
iwconfig
sudo iwlist scan
```

---

### Post by Dadalama on 2013-05-24
dadalama@dadalama-System-Product-Name:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 050d:945a Belkin Components F7D1101 Basic Wireless USB Adapter v1000 [Realtek RTL8188SU]
Bus 001 Device 003: ID 2080:0001 Barnes & Noble nook
Bus 002 Device 002: ID 046d:0804 Logitech, Inc. Webcam C250
Bus 004 Device 002: ID 046d:c312 Logitech, Inc. DeLuxe 250 Keyboard
Bus 004 Device 003: ID 046d:c044 Logitech, Inc. LX3 Optical Mouse
dadalama@dadalama-System-Product-Name:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
snd_hrtimer            12744  1 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180153  10 rfcomm,bnep
binfmt_misc            17540  1 
snd_hda_codec_via      51474  1 
r8712u                189646  0 
ppdev                  17113  0 
snd_hda_intel          33719  4 
snd_hda_codec         127706  2 snd_hda_codec_via,snd_hda_intel
snd_usb_audio         122982  1 
snd_pcm                97275  4 snd_hda_intel,snd_hda_codec,snd_usb_audio
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_hwdep              17764  2 snd_hda_codec,snd_usb_audio
snd_usbmidi_lib        29476  1 snd_usb_audio
snd_seq_midi           13324  0 
snd_rawmidi            30748  2 snd_usbmidi_lib,snd_seq_midi
usbhid                 47238  0 
hid                    99636  1 usbhid
snd_seq_midi_event     14899  1 snd_seq_midi
edac_core              53746  0 
snd_seq                61929  3 snd_seq_midi,snd_seq_midi_event
k10temp                13166  0 
snd_timer              29990  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
edac_mce_amd           23709  0 
psmouse                97485  0 
snd                    79041  21 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nvidia               9367655  38 
serio_raw              13211  0 
sp5100_tco             13791  0 
soundcore              15091  1 snd
asus_atk0110           18078  0 
parport_pc             32866  1 
i2c_piix4              13301  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mac_hid                13253  0 
wmi                    19256  0 
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
usb_storage            49198  1 
floppy                 70207  0 
pata_atiixp            13204  0 
r8169                  62154  0 
dadalama@dadalama-System-Product-Name:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:24:8c:d1:1c:7e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:52722 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52722 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4110576 (4.1 MB)  TX bytes:4110576 (4.1 MB)

wlan0     Link encap:Ethernet  HWaddr 08:86:3b:23:be:48  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a86:3bff:fe23:be48/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:655 errors:0 dropped:19 overruns:0 frame:0
          TX packets:706 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:463400 (463.4 KB)  TX bytes:121605 (121.6 KB)

dadalama@dadalama-System-Product-Name:~$ iwconfig
lo        no wireless extensions.

wlan0     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

dadalama@dadalama-System-Product-Name:~$ sudo iwlist scan
[sudo] password for dadalama: 
lo        Interface doesn't support scanning.

wlan0     No scan results

eth0      Interface doesn't support scanning.

---

### Post by praseodym on 2013-05-24
Try to update the driver:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/35/41/2844083-rtl8712u-2.6.6.0.2_dkms.tar.gz
sudo tar xvf 2844083-rtl8712u-2.6.6.0.2_dkms.tar.gz -C /usr/src
sudo dkms add -m rtl8712u -v 2.6.6.0.2
sudo dkms build -m rtl8712u -v 2.6.6.0.2
sudo dkms install -m rtl8712u -v 2.6.6.0.2
echo "blacklist r8712u" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Reboot and check:
```

iwconfig
lsmod | egrep 'r81|8712'
 
```

---

### Post by Dadalama on 2013-05-24
dadalama@dadalama-System-Product-Name:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Bradshaw's"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:24:B2:7F:4E:F4   
          Bit Rate:54 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=70/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

dadalama@dadalama-System-Product-Name:~$ lsmod | egrep 'r81|8712'


thanks for the help I'll let you know if it keeps dropping

---

### Post by Dadalama on 2013-05-24
It got worse
It started kicking and forcing me to reinsert the network adapter every few seconds, now it's stable but I don't know for how long...

---

### Post by praseodym on 2013-05-24
Check:
```

lsmod
ifconfig -a
cat /etc/resolv.conf
route -n
sudo iwlist scan
```

---

### Post by Dadalama on 2013-05-24
dadalama@dadalama-System-Product-Name:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
snd_hrtimer            12744  1 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180153  10 rfcomm,bnep
binfmt_misc            17540  1 
snd_hda_codec_via      51474  1 
snd_hda_intel          33719  3 
snd_hda_codec         127706  2 snd_hda_codec_via,snd_hda_intel
snd_usb_audio         122982  1 
snd_pcm                97275  3 snd_hda_intel,snd_hda_codec,snd_usb_audio
ppdev                  17113  0 
snd_hwdep              17764  2 snd_hda_codec,snd_usb_audio
snd_usbmidi_lib        29476  1 snd_usb_audio
r8712u                189646  0 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30748  2 snd_usbmidi_lib,snd_seq_midi
snd_seq                61929  3 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  3 snd_hrtimer,snd_pcm,snd_seq
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
v4l2_compat_ioctl32    17128  1 videodev
snd                    79041  20 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
usbhid                 47238  0 
sp5100_tco             13791  0 
hid                    99636  1 usbhid
psmouse                97485  0 
edac_core              53746  0 
i2c_piix4              13301  0 
soundcore              15091  1 snd
serio_raw              13211  0 
k10temp                13166  0 
edac_mce_amd           23709  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
parport_pc             32866  1 
asus_atk0110           18078  0 
nvidia               9367655  38 
mac_hid                13253  0 
wmi                    19256  0 
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
usb_storage            49198  1 
pata_atiixp            13204  0 
floppy                 70207  0 
r8169                  62154  0 
dadalama@dadalama-System-Product-Name:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:24:8c:d1:1c:7e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1287 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1287 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:92296 (92.2 KB)  TX bytes:92296 (92.2 KB)

wlan0     Link encap:Ethernet  HWaddr 08:86:3b:23:be:48  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a86:3bff:fe23:be48/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5025 errors:0 dropped:96 overruns:0 frame:0
          TX packets:4523 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4685325 (4.6 MB)  TX bytes:890628 (890.6 KB)

dadalama@dadalama-System-Product-Name:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
dadalama@dadalama-System-Product-Name:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
dadalama@dadalama-System-Product-Name:~$ sudo iwlist scan
[sudo] password for dadalama: 
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:24:B2:7F:4E:F4
                    ESSID:"Bradshaw's"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Signal level=100/100  
          Cell 02 - Address: EC:1A:59:49:19:60
                    ESSID:"belkin.960"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD9D0050F204104A00011010440001021041000100103B0001031047001000000000000000010003EC1A594919601021001242656C6B696E20436F72706F726174696F6E1023000946394B31303032763410240007342E30302E30371042000E31323132333947433432383830381054000800060050F20400011011001B42656C6B696E20576972656C65737320526F757465722857464129100800020080
                    Signal level=100/100  
          Cell 03 - Address: 74:44:01:F2:27:76
                    ESSID:"karpowecz"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    Signal level=72/100  
          Cell 04 - Address: E0:91:F5:60:EC:D0
                    ESSID:"fofybrit"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD7C0050F204104A00011010440001021041000100103B0001031047001088A48572B188CF6E7688D36A0FDC68F01021000D4E4554474541522C20496E632E10230009574E5232303030763210240009574E523230303076321042000230311054000800060050F204000110110009574E52323030307632100800020084
                    Signal level=46/100  
          Cell 05 - Address: C4:3D:C7:3A:6F:7B
                    ESSID:"Salas"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Signal level=46/100  

eth0      Interface doesn't support scanning.

dadalama@dadalama-System-Product-Name:~$

---

### Post by praseodym on 2013-05-24
Try WPA2-AES (CCMP) encryption instead of (unsecure) WEP. Did you install the driver?

---

### Post by wildmanne39 on 2013-05-24
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by Dadalama on 2013-05-24
@praseodym: Okay I will, I updated the driver just now but when I first started using ubuntu it loaded up without needing a driver.

Edit:No change after updating the security

@ Wildman: Sorry I will in the future

---

