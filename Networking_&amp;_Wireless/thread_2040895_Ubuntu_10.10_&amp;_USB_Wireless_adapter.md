---
title: "Ubuntu 10.10 &amp; USB Wireless adapter"
date: 2012-08-11
forum: Networking &amp; Wireless
---

### Post by pauliusj on 2012-08-11
Hello, I have installed ubuntu 10.10 on my 32-bit laptop that has wireless switch broken. On windows I used a usb wireless adapter to connect to wifi. The problem is, ubuntu automatically tries to connect to wifi through the internal wireless card and I don't know how to change that so that i would connect to wifi through usb wireless adapter. If im not wrong, the ubuntu has no problem making that usb wireless adapter working(it shows up in the list of connections), the problem is that it tries to connect through the internal one. I would be very greatful if someone would help me on this. If you need more info, just say because I don't know what kind of information you might need to help me.

Btw, sorry for my broken english :)

---

### Post by praseodym on 2012-08-11
Hi,

several things:

1. Ubuntu 10.10 is outdated. Therefore I recommend installing 12.04 Long-Term-Support (Upgrading via 11.04 _and_ 11.10 takes too long)

2. Which hardware is in use? 

Please show the outputs of
```

lsusb
lspci -nnk | grep -iA2 net
lsmod
```
3. Check this thread: Unload the pci-driver when the stick is in use via udev-rule:

[http://ubuntuforums.org/showpost.php?p=11247931&postcount=13](http://ubuntuforums.org/showpost.php?p=11247931&postcount=13)

---

### Post by pauliusj on 2012-08-12
Hi praseodym and thanks for helping me!

I am using ubuntu 10.10, because this laptop is not very good in specs(512 ram, 1.5GHz cpu) and I'm afraid the latest version of ubuntu would not run so well(ubuntu 10.10 runs very fast, the speed is uncomparible with sluggish winXP). And the only method I can install an OS now is through usb flash drive, but I have a problem with it([http://ubuntuforums.org/showthread.php?t=2038772](http://ubuntuforums.org/showthread.php?t=2038772)). Currently I don't have a computer that could burn iso's into disks. Besides, I only need few programs on ubuntu. To be exact it's eclipse ide, android sdk, text editor, website browser, dropbox.

The console output I got from those commands is:

```
paulius@ubuntu:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c062 Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bda:8171 Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
paulius@ubuntu:~$ lspci -nnk | grep -iA2 net
02:01.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413 802.11bg NIC [168c:001a] (rev 01)
    Subsystem: Atheros Communications Inc. Compex Wireless 802.11 b/g  MiniPCI Adapter, Rev A1 [WLM54G] [168c:2052]
    Kernel driver in use: ath5k
--
02:0d.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Fujitsu Technology Solutions Device [1734:1098]
    Kernel driver in use: b44
paulius@ubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
arc4                    1165  2 
snd_atiixp_modem        9147  0 
snd_atiixp             12426  2 
radeon                825934  2 
snd_ac97_codec         99227  2 snd_atiixp_modem,snd_atiixp
ac97_bus                1014  1 snd_ac97_codec
ath5k                 130051  0 
snd_pcm                71475  3 snd_atiixp_modem,snd_atiixp,snd_ac97_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
mac80211              231541  1 ath5k
ttm                    56633  1 radeon
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         30200  1 radeon
snd_timer              19067  2 snd_pcm,snd_seq
ath                     8153  1 ath5k
drm                   168054  4 radeon,ttm,drm_kms_helper
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 35973  0 
r8192s_usb            287340  0 
joydev                  8735  0 
cfg80211              144470  3 ath5k,mac80211,ath
snd                    49006  12 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit            5168  1 radeon
i2c_piix4               8635  0 
tifm_7xx1               3766  0 
yenta_socket           21518  0 
soundcore                880  1 snd
ati_agp                 5202  0 
psmouse                59033  0 
tifm_core               6089  1 tifm_7xx1
pcmcia_rsrc            10566  1 yenta_socket
snd_page_alloc          7120  3 snd_atiixp_modem,snd_atiixp,snd_pcm
agpgart                32011  3 ttm,drm,ati_agp
shpchp                 29886  0 
eeprom_93cx6            1345  1 r8192s_usb
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw               4022  0 
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usbhid                 36882  0 
b44                    26253  0 
sdhci_pci               6339  0 
firewire_ohci          21106  0 
sdhci                  15890  1 sdhci_pci
hid                    67742  1 usbhid
firewire_core          46643  1 firewire_ohci
ssb                    39288  1 b44
mii                     4425  1 b44
pata_atiixp             3288  1 
crc_itu_t               1383  1 firewire_core
led_class               2633  2 ath5k,sdhci

```I tried the udev-rule and it didn't work. It still tries to connect to wifi through the internal wireless card(at least it shows me that). And after some time of trying to connect it asks me for password again(the password is good, i checked it alot of times).

---

### Post by mörgæs on 2012-08-12
If Ubuntu is slow then Lubuntu or Xubuntu 12.04 are good candidates.

---

### Post by praseodym on 2012-08-12
You need to replace "b43" in that rule **twice** with "ath5k".

---

### Post by praseodym on 2012-08-12
Additionally, you need to copy the firmware to the right place in 10.10:

```
sudo mkdir /lib/firmware/RTL8192SU
sudo cp /lib/firmware/RTL8192SE/rtl8192sfw.bin /lib/firmware/RTL8192SU/ 
```
Reload the USB-driver:

```
sudo modprobe -rf r8192s_usb
sudo modprobe r8192s_usb 
```
The stick should work now with the channels 1-11

---

### Post by pauliusj on 2012-08-12
Thanks! i did what you said, and it now tries to connect to wifi through my usb wireless adapter, though it still shows me that it is trying to connect and asks for password again after some time :(

---

### Post by pauliusj on 2012-08-12
> **mörgæs said:**
> If Ubuntu is slow then Lubuntu or Xubuntu 12.04 are good candidates.

I had lubuntu 12.04 installed, but there was the same problem with wireless and when I uninstalled it I can't boot from usb no more([http://ubuntuforums.org/showthread.php?t=2038772](http://ubuntuforums.org/showthread.php?t=2038772)). I had ubuntu 10.10 on cd so I installed it instead.

---

### Post by pauliusj on 2012-08-12
I tried to use a different wireless adapter and it works now! thanks for your help! :)

---

