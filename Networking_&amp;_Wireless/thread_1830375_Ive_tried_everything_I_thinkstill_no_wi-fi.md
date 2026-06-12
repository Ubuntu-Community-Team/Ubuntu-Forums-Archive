---
title: "Ive tried everything I think/still no wi-fi"
date: 2011-08-21
forum: Networking &amp; Wireless
---

### Post by ruseriousb511 on 2011-08-21
alright guys I have been reading Ubuntu forums posts and google search rsult pages for about 36 hours now and I still cannot get my wi-fi to work. Ethernet works just fine but no option to enable wireless and it says "wireless disabled by hardware switch".

I have an HP Compaq Presario X6000 with wireless card BCM 4306 802.11 b/g 14e4 : 4320 (rev 03 ). 

I have read a few other posts where guys have had the same card or even the same notebook and card, they got theirs to work so I followed their steps and I still sould not get mine to work in the same manner. :(

It was working just fine in Ubuntu 10.04 Lucid ( never had a problem ). 

Any info you may need to help me out just give me the command and I will paste it for you if it'll help you help me.

Please get me going on my wireless and I would be willing to send you a few bucks through pay-pal even, I just need it working. 

Please help me and I would be forever grateful. Thanks guys !! 

I'm stumped :-k

---

### Post by praseodym on 2011-08-21
Please show:

```
lspci -nnk | grep -iA2 net
lsmod
rfkill list
iwconfig
dmesg | egrep 'b43|wl'
```

---

### Post by ruseriousb511 on 2011-08-21
here it is :

ruseriousb5@ruseriousb5-Presario-x6000-PK249AV-ABA:~$ lspci -nnk | grep -iA2 net0b:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:3082]
    Kernel driver in use: 8139too
--
0b:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
    Subsystem: Hewlett-Packard Company Broadcom 802.11b/g WLAN [103c:12f8]
    Kernel driver in use: b43-pci-bridge
ruseriousb5@ruseriousb5-Presario-x6000-PK249AV-ABA:~$ lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
radeon                900494  3 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
binfmt_misc            13213  1 
arc4                   12473  2 
ttm                    65184  1 radeon
hp_wmi                 13418  0 
b43                   296610  0 
sparse_keymap          13666  1 hp_wmi
drm_kms_helper         40745  1 radeon
snd_timer              28659  2 snd_pcm,snd_seq
mac80211              257001  1 b43
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 39671  0 
drm                   184164  5 radeon,ttm,drm_kms_helper
cfg80211              156212  2 b43,mac80211
tifm_7xx1              12898  0 
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 17322  0 
video                  18951  0 
tifm_core              15040  1 tifm_7xx1
yenta_socket           27230  0 
psmouse                73312  0 
pcmcia_rsrc            18292  1 yenta_socket
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
i2c_algo_bit           13184  1 radeon
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
8139too                23208  0 
ssb                    45942  1 b43
8139cp                 22497  0 
sdhci_pci              13623  0 
sdhci                  22720  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
ruseriousb5@ruseriousb5-Presario-x6000-PK249AV-ABA:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
ruseriousb5@ruseriousb5-Presario-x6000-PK249AV-ABA:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
ruseriousb5@ruseriousb5-Presario-x6000-PK249AV-ABA:~$ dmesg | egrep 'b43|wl'
[    0.000000] DMI: Hewlett-Packard Presario x6000 (PK249AV#ABA)      /3082, BIOS F.22      02/23/2005
[    1.604123] b43-pci-bridge 0000:0b:03.0: enabling device (0000 -> 0002)
[    1.604138] b43-pci-bridge 0000:0b:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.410433] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   15.521534] Registered led device: b43-phy0::tx
[   15.521694] Registered led device: b43-phy0::rx
[   15.521838] Registered led device: b43-phy0::radio
ruseriousb5@ruseriousb5-Presario-x6000-PK249AV-ABA:~$

---

### Post by praseodym on 2011-08-21
> Tx-Power=off

means that there is a switch/etc. Try the following:

```
echo "options hp_wmi wireless=1" | sudo tee /etc/modprobe.d/hp_wmi.conf
```
Reboot and:

```
sudo rfkill unblock all
```
Tests:

```
rfkill list
iwconfig
sudo iwlist scan
dmesg | egrep 'b43|wmi'
```

---

### Post by ruseriousb511 on 2011-08-21
just did that EXACT thing and here are the results :

ruseriousb5@ruseriousb5-Presario-x6000-PK249AV-ABA:~$ sudo rfkill unblock all
[sudo] password for ruseriousb5: 
ruseriousb5@ruseriousb5-Presario-x6000-PK249AV-ABA:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
ruseriousb5@ruseriousb5-Presario-x6000-PK249AV-ABA:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
ruseriousb5@ruseriousb5-Presario-x6000-PK249AV-ABA:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

ruseriousb5@ruseriousb5-Presario-x6000-PK249AV-ABA:~$ dmesg | grep wmi
[    0.248816] wmi: Mapper loaded
[   15.062788] hp_wmi: Unknown parameter `wireless'
ruseriousb5@ruseriousb5-Presario-x6000-PK249AV-ABA:~$

---

### Post by ruseriousb511 on 2011-08-21
That did the trick wi-fi is officially on and working 

THANK YOU !!!!!!

:p:D:):P

---

