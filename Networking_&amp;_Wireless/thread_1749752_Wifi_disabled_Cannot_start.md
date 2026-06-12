---
title: "Wifi disabled Cannot start"
date: 2011-05-04
forum: Networking &amp; Wireless
---

### Post by pcsel on 2011-05-04
System: Fujitsu-Siemens Amilo Li 2727 Laptop
Wireless: Atheros Wifi chipset
OS: Ubuntu 11.04

I have a problem with the above where I don't see any Wireless networks. Wireless is enabled from the Network Applet. I have tried to add as much information with my limited knowledge.. hope this helps and someone can assist in finding the problem.

Many Thanks


I have carried out the following tests and the results are as follows:

```

rfkill list all
0: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no

```

I then tried to unblock using:
```

rfkill unblock all
rfkill unblock wifi

```

After running the above commands I get this:
```

rfkill list all
0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

```

I have checked the adapter and found it to be disabled:
```

sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0a:e4:cc:46:49
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:f6000000-f6000fff memory:f0000000-f001ffff
  *-network DISABLED
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 04
       serial: 00:16:44:bc:ce:97
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.38-8-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:fa000000-fa00ffff

```

Other commands I can think of for information that might be useful for anyone that can help are below:

```

sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

```

and..
```

lsmod
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39571  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255820  1 
joydev                 17322  0 
snd_hda_intel          24140  2 
binfmt_misc            13213  1 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
arc4                   12473  2 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
acer_wmi               23123  0 
sparse_keymap          13666  1 acer_wmi
snd_seq_midi_event     14475  1 snd_seq_midi
i915                  450944  3 
ath5k                 144412  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ath                    19141  1 ath5k
mac80211              257001  1 ath5k
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         40745  1 i915
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
drm                   180037  4 i915,drm_kms_helper
cfg80211              156212  3 ath5k,ath,mac80211
serio_raw              12990  0 
soundcore              12600  1 snd
i2c_algo_bit           13184  1 i915
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
ahci                   21591  3 
libahci                25548  1 ahci
r8169                  42534  0 

```

and 
```

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


```

and
```

dmesg | grep ath
[    0.959852] device-mapper: multipath: version 1.2.0 loaded
[    0.959856] device-mapper: multipath round-robin: version 1.0.0 loaded
[   10.997141] ath5k 0000:08:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   10.997158] ath5k 0000:08:00.0: setting latency timer to 64
[   10.997226] ath5k 0000:08:00.0: registered as 'phy0'
[   11.656267] ath: EEPROM regdomain: 0x30
[   11.656271] ath: EEPROM indicates we should expect a direct regpair map
[   11.656275] ath: Country alpha2 being used: AM
[   11.656277] ath: Regpair used: 0x30
[   11.690896] Registered led device: ath5k-phy0::rx
[   11.691019] Registered led device: ath5k-phy0::tx
[   11.691034] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)

```

---

### Post by mtelesha on 2011-05-04
I have the same issue with a Lenovo Ideapad S12. Wireless worked great in 10.04 then won't wake up from sleep in 10.10 and fails in 11.04.

FIXED:

Black Listed acer-wireless
> sudo nano /etc/modprobe.d/blacklist.conf
add line: blacklist acer wmi


Then I had to remove the STA drives and installed the B43
> I removed the STA drive by Additional Driver GUI
Then install: sudo aptitude install b43-fwcutter 
sudo aptitude install firmware-b43-installer
Then I did
> lsmod
look for b43 and mine was not installed
> sudo modprobe b43
then I lsmod to check

REBOOTED

then I lsmod and sure enough it didn't load the b43 so I once again:
> sudo modprobe b43

Wireless working

Fix for sudo modprobe b43
> sudo nano /etc/rc.local
add line: modprobe b43
add the line before end0


Hope this helps someone.

-Marc

PS Ubuntu has been getting worse and worse for my son's idea pad. I use OpenSUSE on my own computer.

---

### Post by Enotsoul on 2011-05-05
Works like a charm! Many thanks:D. I hate it how ubuntu changes everything every time you upgrade.. went throught my 3d upgrade and there are many things that don't work as expected:(

---

