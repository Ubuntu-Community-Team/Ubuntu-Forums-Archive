---
title: "Cannot connect to university wireless"
date: 2011-10-27
forum: Networking &amp; Wireless
---

### Post by Ian Zaretsky on 2011-10-27
Hello kind people,

I am using Xubuntu 11.10 on my Acer Aspire One 721-3574. Everything seems to work out-of-the-box, including the wireless card. I have no troubles connecting to my WPA network at home. However, I cannot connect to an "eduroam" university wireless using network-manager. My friend in the same office also uses Ubuntu 11.10 on his Dell laptop and can connect to it successfully. Could you help me resolve this? I did some googling which made me believe that people somehow solve similar issues with wpa_supplicant but figuring it out on my own is way beyond my level of expertise...

A quote from my uni website about our wireless:
The eduroam wireless service at Heriot Watt University uses the IEEE 802.1x authentication standard with PEAP (Protected Extensible Authentication Protocol) and MSCHAPv2. Once authenticated WPA/WPA2 (Wi-Fi Protected Access) Enterprise mode and AES/TKIP encryption protects traffic on the network.

---

### Post by kurt18947 on 2011-10-27
I'm no expert but are you using Network Manager? If so, when you are attempting to connect, are you using "WPA and WPA2 enterprise" as opposed to "WPA and WPA2 Personal"? That would be easy to try. If that doesn't work, I'll defer to somebody who knows what they're talking about :tongue:

---

### Post by Ian Zaretsky on 2011-10-27
Hi :-) Yeah, sure! In fact, I followed the instructions provided on our website:

[http://www.hw.ac.uk/it/wifi_instructions/Configuring_UBUNTU_10_04_for_eduroam.pdf](http://www.hw.ac.uk/it/wifi_instructions/Configuring_UBUNTU_10_04_for_eduroam.pdf)

but to no avail...

---

### Post by varunendra on 2011-10-27
That guide of your university is pretty good in details :). So did you try the helpdesk it referred to? Does the network appear in the available networks list? Does it even try to connect (then fails)? You may try wicd to see if it lets you connect.

If you want to try some troubleshooting with NM first, we can start with following outputs:
```
sudo lshw -C network
lsmod
```
and the following when you are trying to connect to your university's network:
```
iwconfig
```

---

### Post by Ian Zaretsky on 2011-10-27
Yeah, our help desk said that they are unfamiliar with new Ubuntu. I.e. "we do not care". :-) 

I can see the network, but it does not accept my credentials, meaning that an authentication window keeps popping out.

I'd like to try debugging with NM first, I'll run those commands tomorrow when I'm back to the uni. Thank you for your help!

---

### Post by Ian Zaretsky on 2011-10-28
Here is what I got:

```

ianic@ianic-Aspire-One-721:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: AR8151 v1.0 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: 00:26:2d:af:15:65
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:d0200000-d023ffff ioport:a000(size=128)
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: c4:46:19:15:21:66
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.0.0-12-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d0300000-d030ffff

```

```

ianic@ianic-Aspire-One-721:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55577  1 vfat
rfcomm                 38408  4 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
uvcvideo               67271  0 
joydev                 17393  0 
videodev               85626  1 uvcvideo
acer_wmi               23302  0 
snd_hda_codec_hdmi     31426  1 
sparse_keymap          13658  1 acer_wmi
snd_hda_codec_realtek   254125  1 
arc4                   12473  2 
snd_seq_midi           13132  0 
snd_hda_intel          24262  4 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_rawmidi            25241  1 snd_seq_midi
psmouse                73673  0 
snd_seq_midi_event     14475  1 snd_seq_midi
fglrx                2595570  36 
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
sp5100_tco             13495  0 
k10temp                12990  0 
serio_raw              12990  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
i2c_piix4              13093  0 
ath9k                 112711  0 
snd_timer              28932  2 snd_pcm,snd_seq
mac80211              272785  1 ath9k
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
video                  18908  0 
ath9k_common           13599  1 ath9k
ath9k_hw              293893  2 ath9k,ath9k_common
snd                    55902  18 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
ath                    19387  2 ath9k,ath9k_hw
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
wmi                    18744  1 acer_wmi
cfg80211              172392  3 ath9k,mac80211,ath
shpchp                 32356  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ums_realtek            13096  0 
usb_storage            44173  1 ums_realtek
uas                    17699  0 
ahci                   21634  3 
libahci                25727  1 ahci
atl1c                  36638  0 
pata_atiixp            12967  0 

```

```

ianic@ianic-Aspire-One-721:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

---

### Post by varunendra on 2011-10-28
You didn't say anything about whether you are able to see their network in the "Available Networks" list or not. If it appears there, does NM even try to connect when you click on it?

There are many threads ongoing about problems with ath9k and NM combination in 11.10. A few have solved their problem by replacing NM with wicd. But since you are already able to connect to your home network, I think disabling 'Hardware encryption' on your card may help:
When you are trying to connect to your university network, please do the following:
```
sudo rmmod ath9k
sudo modprobe ath9k nohwcrypt=1
```
(after executing *rmmod*, use *lsmod* command to make sure the ath9k driver has actually been removed. If it still appears in the list, you may have to use -f option with rmmod, that is : *sudo rmmod -f ath9k*)

See if this helps to get connected. If not, please post the output of (when it _tries_ to connect then fails):
```
dmesg | grep ath
```

---

### Post by Ian Zaretsky on 2011-10-28
Hi varunendra, you overlooked my previous message: "I can see the network, but it does not accept my credentials, meaning that an authentication window keeps popping out." :-) So the answer is yes, I see it and yes, NM tries to connect but cannot get past the authentication stage.

Disabling hardware encryption did not work - the situation is exactly the same as before... And there is no output relevant to the connection process in "dmesg | grep ath". No new messages are generated during the connection attempt. Is this bad? :-)

---

### Post by varunendra on 2011-10-28
Ah, sorry, totally missed it :redface:
But if it tries to connect and fails, there must be demsg messages about it. Maybe 'ath' is a wrong pattern to grep. So try this instead to see if any relevant messages are found:

As soon as it fails to connect, run
```
dmesg | tail -25
```

---

### Post by Ian Zaretsky on 2011-10-28
I tried to set "nohwcrypt=0" the same way, now my wireless card does not work at all, and the wireless led light is off...

---

### Post by Ian Zaretsky on 2011-10-28
And "rfkill list" shows that 

```
6: phy0: Wireless LAN
      Soft blocked: no
      Hard blocked: yes
```

---

### Post by varunendra on 2011-10-28
Try-
```
sudo rmmod ath9k
sudo modprobe ath9k nohwcrypt=1
sudo rfkill unblock all
```
and post-
```
rfkill list all
```

---

### Post by Ian Zaretsky on 2011-10-28
```

1: acer-wireless: Wireless LAN
      Soft blocked: no
      Hard blocked: no
2: phy1: Wireless LAN
      Soft blocked: no
      Hard blocked: yes

```

---

### Post by varunendra on 2011-10-28
> **Ian Zaretsky said:**
> ```

2: phy1: Wireless LAN
      Soft blocked: no
      Hard blocked: yes

```
Usually this means the interface is switched off by a physical switch. Double-check your physical switch for it (if any) and the function key combination to turn it on/off. Although it doesn't make sense, but also check in BIOS to make sure it is not disabled there.

---

