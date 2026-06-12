---
title: "q10air netbook - need help with WLAN"
date: 2011-07-21
forum: Networking &amp; Wireless
---

### Post by thyriel on 2011-07-21
Hi,

im trying to get linux running on a Q10air Netbook, so far it works fine, except the WLAN im pretty stuck getting it running.

Ive tried the installation procedure from ubuntu wiki and id tried windows drivers, but cant get it to work :/

Chipset should be Realtek 8187SE

Main Problem is, the wifi seems to work in linux, but it doesnt find any networks, also manual connection doesnt work. In Windows i have around 15 networks in range, my own running in n+g+b mode.

Output of some commands:
> 
iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wlan0 802.11b/g Mode:Managed Frequency=2.422 GHz 
Access Point: Not-Associated Bit Rate:11 Mb/s 
Retry:on RTS thr:off Fragment thr:off
Power Management:off
Link Quality=0/100 Signal level=0 dBm Noise level=0 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0


lspci
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)


lsmod
Module Size Used by
binfmt_misc 13213 1 
parport_pc 32111 0 
dm_crypt 22463 0 
ppdev 12849 0 
joydev 17322 0 
snd_hda_codec_realtek 255820 1 
snd_hda_intel 24140 2 
snd_hda_codec 90901 2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep 13274 1 snd_hda_codec
snd_pcm 80244 2 snd_hda_intel,snd_hda_codec
snd_seq_midi 13132 0 
snd_rawmidi 25269 1 snd_seq_midi
snd_seq_midi_event 14475 1 snd_seq_midi
snd_seq 51291 2 snd_seq_midi,snd_seq_midi_event
snd_timer 28659 2 snd_pcm,snd_seq
snd_seq_device 14110 3 snd_seq_midi,snd_rawmidi,snd_seq
snd 55295 13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse 73312 0 
r8187se 156904 0 
serio_raw 12990 0 
soundcore 12600 1 snd
eeprom_93cx6 12653 1 r8187se
snd_page_alloc 14073 2 snd_hda_intel,snd_pcm
lp 13349 0 
parport 36746 3 parport_pc,ppdev,lp
dm_raid45 88410 0 
xor 21860 1 dm_raid45
btrfs 527341 0 
zlib_deflate 26594 1 btrfs
libcrc32c 12543 1 btrfs
i915 450944 3 
drm_kms_helper 40745 1 i915
drm 180037 4 i915,drm_kms_helper
i2c_algo_bit 13184 1 i915
usb_storage 43946 0 
uas 17676 0 
r8169 42534 0 
video 18951 1 i915


cat /etc/network/interfaces

auto lo
iface lo inet loopback

sudo iwlist scan

lo Interface doesn't support scanning.


eth0 Interface doesn't support scanning.

wlan0 No scan results


rfkill list
dmesg | egrep 'r8|rtl'
[ 2.003982] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[ 2.005589] r8169 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 2.005666] r8169 0000:01:00.0: setting latency timer to 64
[ 2.005771] r8169 0000:01:00.0: irq 42 for MSI/MSI-X
[ 2.007473] r8169 0000:01:00.0: eth0: RTL8102e at 0xf8016000, 00:03:0d:af:33:91, XID 14a00000 IRQ 42
[ 13.820843] r8169 0000:01:00.0: eth0: link down
[ 14.109272] r8187se: module is from the staging directory, the quality is unknown, you have been warned.
[ 14.291443] r8180: Initializing module
[ 14.291450] r8180: Wireless extensions version 22
[ 14.291455] r8180: Initializing proc filesystem
[ 14.291532] r8180: Configuring chip resources
[ 14.291565] r8180 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 14.291582] r8180 0000:02:00.0: setting latency timer to 64
[ 14.318234] r8180: Channel plan is 2
[ 14.318256] r8180: MAC controller is a RTL8187SE b/g
[ 14.320453] r8180: usValue is 0xf00
[ 14.364182] r8180: EEPROM version 104
[ 14.368545] r8180: WW:**PLEASE** REPORT SUCCESSFUL/UNSUCCESSFUL TO Realtek!
[ 14.388715] r8180: IRQ 17
[ 14.447361] r8180: Driver probe completed
[ 15.557489] r8180: Bringing up iface
[ 15.756180] r8180: Card successfully reset
[ 16.495519] r8180: WIRELESS_MODE_G


(rfkill list gives nothing back)

Especially the lines:
 r8187se: module is from the staging directory, the quality is unknown, you have been warned.
[ 14.291443] r8180: Initializing module

look strange to me, does that mean for some reason he doesnt like the r8187se driver and loads r8180 that doesnt work ?

Linux Versions ive tried in hope one works:
- linux mint 11
- xubuntu 11.04
- xubuntu 10.04
- xubuntu 8.04 -> cant even install that via USB (aborts as it finds no cdrom)

---

### Post by thyriel on 2011-07-22
anyone?

---

### Post by wildmanne39 on 2011-07-22
Hi, run this command in a terminal
```
lsmod | grep rt2
```
and post the results here.
Thank you

---

