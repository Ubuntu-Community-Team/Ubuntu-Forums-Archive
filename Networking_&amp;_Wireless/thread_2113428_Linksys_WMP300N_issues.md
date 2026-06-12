---
title: "Linksys WMP300N issues"
date: 2013-02-07
forum: Networking &amp; Wireless
---

### Post by MourningsEnd on 2013-02-07
I have, as stated in the title, a Linksys WMP300N PCI wireless adapter.  

I am on Xubuntu 12.10.

I have the drivers installed through "Additional Drivers".  (Broadcom STA wireless driver)

When I go to connect to a wireless network none show up.  None of them are hiding their SSID, so what could be the problem?  I am currently connecting wired at this moment.

Any help is appreciated.

---

### Post by praseodym on 2013-02-07
Please show the chipset info:
```

lspci -nnk | grep -iA2 net
iwconfig
rfkill list
lsmod
```

---

### Post by MourningsEnd on 2013-02-08
> **praseodym said:**
> Please show the chipset info:
```

lspci -nnk | grep -iA2 net
iwconfig
rfkill list
lsmod
```

Sorry for such a late reply.

```

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
	Subsystem: Realtek Semiconductor Co., Ltd. TEG-ECTX Gigabit PCI-E Adapter [Trendnet] [10ec:8168]
	Kernel driver in use: r8169
	Kernel modules: r8169
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
	Subsystem: Realtek Semiconductor Co., Ltd. TEG-ECTX Gigabit PCI-E Adapter [Trendnet] [10ec:8168]
	Kernel driver in use: r8169
	Kernel modules: r8169
09:01.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11b/g/n [14e4:4329] (rev 01)
	Subsystem: Linksys Device [1737:0060]
	Kernel driver in use: wl


```

```

eth0      no wireless extensions.

eth1      no wireless extensions.

eth3      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

```

```

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


```

```

Module                  Size  Used by
bnep                   18141  2 
rfcomm                 46620  4 
bluetooth             209249  10 bnep,rfcomm
parport_pc             32689  0 
ppdev                  17074  0 
nvidia              11257760  40 
snd_hda_codec_realtek    78048  1 
snd_hda_intel          33492  4 
snd_hda_codec         134213  2 snd_hda_codec_realtek,snd_hda_intel
lib80211_crypt_tkip    17380  0 
wl                   3074773  0 
snd_hwdep              17699  1 snd_hda_codec
snd_pcm                96668  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0 
snd_rawmidi            30513  1 snd_seq_midi
coretemp               13401  0 
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29426  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
kvm                   414071  0 
snd                    78921  17 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              206797  1 wl
soundcore              15048  1 snd
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
lib80211               14382  2 lib80211_crypt_tkip,wl
microcode              22804  0 
mxm_wmi                13022  0 
i7core_edac            23572  0 
mac_hid                13206  0 
edac_core              52452  3 i7core_edac
lpc_ich                17062  0 
wmi                    19071  1 mxm_wmi
serio_raw              13216  0 
lp                     17760  0 
parport                46346  3 parport_pc,ppdev,lp
hid_generic            12541  0 
firewire_ohci          40402  0 
usbhid                 46987  0 
firewire_core          64369  1 firewire_ohci
hid                   100411  2 hid_generic,usbhid
crc_itu_t              12708  1 firewire_core
r8169                  61651  0 
pata_jmicron           12748  0 


```


I would like to state that I just upgraded to 12.10 yesterday.

---

### Post by praseodym on 2013-02-09
Try pure WPA2-AES encryption, if possible. Blacklist the following driver:

```
echo "blacklist brcm80211" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot. Check:
```

dmesg | grep wl
rfkill list
iwlist chan
iwconfig
route -n
cat /etc/resolv.conf
sudo iwlist scan
```
Maybe there is (still?) a driver bug, and it works only on channels 1-11, see the output of "iwlist chan"

---

### Post by MourningsEnd on 2013-02-11
I was using WPA2 AES already.

```

[    6.956254] INFO @wl_cfg80211_attach : Registered CFG80211 phy

```

```

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

```

eth0      no frequency information.

eth1      no frequency information.

eth3      32 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz
          Channel 32 : 5.16 GHz
          Channel 34 : 5.17 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 50 : 5.25 GHz
          Channel 52 : 5.26 GHz
          Channel 54 : 5.27 GHz
          Channel 56 : 5.28 GHz
          Channel 58 : 5.29 GHz
          Channel 60 : 5.3 GHz
          Channel 62 : 5.31 GHz
          Channel 64 : 5.32 GHz
          Channel 66 : 5.33 GHz
lo        no frequency information.

```

```

eth0      no wireless extensions.

eth1      no wireless extensions.

eth3      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

```

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.22.1    0.0.0.0         UG    0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
192.168.22.0    0.0.0.0         255.255.255.0   U     1      0        0 eth1

```

```

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search wcpschools.wcpss.local

```

```

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth3      No scan results

lo        Interface doesn't support scanning.

```

---

### Post by praseodym on 2013-02-12
Maybe its only working properly in the 2,4 GHz region? Try to adjust the router settings (if it is yours).

---

### Post by MourningsEnd on 2013-02-12
> **praseodym said:**
> Maybe its only working properly in the 2,4 GHz region? Try to adjust the router settings (if it is yours).

It is on the 2.4 GHz setting.  :s  I can edit the settings on the router.

---

### Post by praseodym on 2013-02-12
"iwlist chan" also shows the 5 GHz setting. Please show
```

sudo iwlist scan
iwconfig
```
Maybe deactivating a-mode?!

---

### Post by MourningsEnd on 2013-02-13
> **praseodym said:**
> "iwlist chan" also shows the 5 GHz setting. Please show
```

sudo iwlist scan
iwconfig
```
Maybe deactivating a-mode?!

```

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth3      No scan results

lo        Interface doesn't support scanning.

```


```

eth0      no wireless extensions.

eth1      no wireless extensions.

eth3      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

```

What do you mean deactiviting a mode?

---

### Post by praseodym on 2013-02-13
I mean deactivating the 5 GHz region in your router.

---

### Post by MourningsEnd on 2013-02-13
> **praseodym said:**
> I mean deactivating the 5 GHz region in your router.

I am pretty sure it is not enabled.

[IMG]http://i.imgur.com/cVlW1qe.png[/IMG]

---

### Post by praseodym on 2013-02-13
Strange, look at the output of "iwlist chan" and
```

eth3      IEEE 802.11[COLOR="Red"]a[/COLOR]bg  ESSID:off/any  
```
Can you show the picture of "advanced wireless settings"?

---

### Post by MourningsEnd on 2013-02-13
[IMG]http://i.imgur.com/zFRzSrF.png[/IMG]

---

