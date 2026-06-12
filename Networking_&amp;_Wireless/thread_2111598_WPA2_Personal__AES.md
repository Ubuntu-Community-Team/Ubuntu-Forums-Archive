---
title: "WPA2 Personal / AES"
date: 2013-02-02
forum: Networking &amp; Wireless
---

### Post by brett- on 2013-02-02
A couple of months ago I ditched 10.04 and installed Ubuntu Server on my notebook along with plasma-desktop, in order to avoid a bunch of apps that I did not require.  As things progressed I tossed in bits and pieces to get things running smoothly.

The other day I tried to connect to a hidden wireless network that I had used many times before with the previous 10.04 install.   No luck.  Authentication is WPA2 Personal and AES encryption.  NetworkManager does not display the connection (phone and desktop pick it up with no trouble).

I have had no trouble connecting to WEP protected networks with the current install.  This is the first WPA2 network that I have tried.

I must be missing some packages but do not know where to begin (searching has turned up nothing except discussions specific to particular routers).  I know this is not a router problem because, as mentioned earlier, no trouble w/ other devices or 10.04.

Any ideas of what is  missing would be appreciated.

---

### Post by praseodym on 2013-02-02
Server network config is done in system files. KDE works with the network-manager, which can not handle manual configs per default. Please check:
```
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
```

---

### Post by brett- on 2013-02-03
> **praseodym said:**
> Server network config is done in system files. KDE works with the network-manager, which can not handle manual configs per default. Please check:
```
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
```

The only thing not hashed out is "auto lo" and "iface lo inet loopback"

Do I need to add wpq-ssid and wpa-aes or wpa-psk?

---

### Post by praseodym on 2013-02-03
No, normally not. Check:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
iwlist chan
sudo iwlist scan
```

---

### Post by brett- on 2013-02-03
> **praseodym said:**
> No, normally not. Check:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
iwlist chan
sudo iwlist scan
```

Can't post output now due to connection (will post later)

The ESSID of the network I am trying to connect to does not show up with the iwlist scan because it does not broadcast.

I did boot from a KUbuntu live disk and still could not connect to the WPA2-AES hidden network.  Other WEP and WPA2-PSK networks show up in the network manager applet.

Also ... Typing thid response from a handheld connected to the same network!

---

### Post by praseodym on 2013-02-03
Why is the network hidden? This is _not_ improving security!

---

### Post by brett- on 2013-02-03
> **praseodym said:**
> Why is the network hidden? This is _not_ improving security!

Don't know, not my network.  Sure is keeping KDE out.

Does AES work in KDE?

---

### Post by praseodym on 2013-02-03
Yes, it does. You may try **Wicd** instead of the NM.

---

### Post by brett- on 2013-02-03
> **praseodym said:**
> No, normally not. Check:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
iwlist chan
sudo iwlist scan
```

Here is the output from all but the last command.

bhl@hp2530p:~$ lspci -nnk | grep -iA2 net

00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM Gigabit Network Connection [8086:10f5] (rev 03)
        Subsystem: Hewlett-Packard Company Device [103c:30e1]
        Kernel driver in use: e1000e
--
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection [8086:4237]
        Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1211]
        Kernel driver in use: iwlwifi

bhl@hp2530p:~$ lsusb

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 03f0:201d Hewlett-Packard un2400 Gobi Wireless Modem (QDL mode)
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard Bluetooth 2.0 Interface [Broadcom BCM2045]
Bus 008 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305

bhl@hp2530p:~$ lsmod

Module                  Size  Used by
snd_hda_codec_analog    75395  1 
tpm_infineon           17296  0 
snd_hda_intel          32765  2 
snd_hda_codec         109562  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
arc4                   12473  2                                                                                          
snd_rawmidi            25424  1 snd_seq_midi                                                                                 
hp_wmi                 13652  0                                                                                                  
sparse_keymap          13658  1 hp_wmi                                                                                                
joydev                 17393  0                                                                                                       
snd_seq_midi_event     14475  1 snd_seq_midi                                                                                              
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event                                                                                      
snd_timer              28931  2 snd_pcm,snd_seq                                                                                                      
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq                                                                                           
usbhid                 41937  0                                                                                                                                 
hid                    77428  1 usbhid                                                                                                                          
iwlwifi               366524  0                                                                                                                                      
tpm_tis                18308  0                                                                                                                                      
psmouse                86520  0                                                                                                                                          
snd                    62218  13 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device                             
serio_raw              13027  0                                                                                                                                              
btusb                  17948  0                                                                                                                                                  
qcserial               12702  0 
usb_wwan               19779  1 qcserial
mac80211              436493  1 iwlwifi
bluetooth             158479  1 btusb
usbserial              37173  2 qcserial,usb_wwan
cfg80211              178877  2 iwlwifi,mac80211
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
i915                  419361  3 
mac_hid                13077  0 
hp_accel               25728  0 
lis3lv02d              19268  1 hp_accel
wmi                    18744  1 hp_wmi
drm_kms_helper         45466  1 i915
drm                   197641  4 i915,drm_kms_helper
input_polldev          13648  1 lis3lv02d
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
mei                    36570  0 
lp                     17455  0 
parport                40930  1 lp
firewire_ohci          40172  0 
firewire_core          56940  1 firewire_ohci
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
e1000e                140131  0 

bhl@hp2530p:~$ iwconfig

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: on
          
eth0      no wireless extensions.

bhl@hp2530p:~$ rfkill list

0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
2: hp-wifi: Wireless LAN
        Soft blocked: no
        Hard blocked: no
3: hp-bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no
4: hp-wwan: Wireless WAN
        Soft blocked: no
        Hard blocked: no

bhl@hp2530p:~$ iwlist chan

lo        no frequency information.

wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
eth0      no frequency information.

---

### Post by brett- on 2013-02-03
> **praseodym said:**
> Yes, it does. You may try **Wicd** instead of the NM.

Ironic because that is what I had initially and switched to NM because of nice interface.  I hesitate to try and roll back.  Can both exist together for testing?

---

### Post by praseodym on 2013-02-03
Yes, try it on the fly after installing:
```

sudo service network-manager stop
sudo killall wpa_supplicant 
sudo service wicd restart
```
If it works deactivate the NM in autostart

---

### Post by brett- on 2013-02-05
> **praseodym said:**
> Yes, try it on the fly after installing:
```

sudo service network-manager stop
sudo killall wpa_supplicant 
sudo service wicd restart
```If it works deactivate the NM in autostart
  
I installed python-wicd and wicd-daemon and not wicd-kde.  Retained the panel widget "Network Management" by [EMAIL="wstephenson@kde.org"]wstephenson-at-kde.org[/EMAIL] because it offers quick access to vpn connections.

Did not remove network-manager because plasma-widget-networkmanager depends on network-manager and I don't know if it will impact the widget "Network Management" and I could not figure out how to access vpn through widget wicd-kde.

I will test removal of network-manager later when I have access to  an ethernet connection.

Bottom line is connection to the WPA2-AES was successful thanks to your suggestion of installing WICD.  Thank you.

Is this a KDE bug?

---

### Post by Karmovorotin on 2013-11-17
Hi guys,

I have installed WICD on my kubuntu 12.04 PC because I couldn't connect to my home network
The networks is WPA2 protected with AES encryption. Thing is, Network Manager didn't even let me choose a WPA2 network, that's why I chose to install WICD. But even on WICD I can only choose LEAP or PEAP. I am quite lost and don't know what to do, since I am quite new to Ubuntu.

Thanks for your help.

---

