---
title: "AR93XX Wireless LAN problems"
date: 2012-12-11
forum: Networking &amp; Wireless
---

### Post by skimwpi on 2012-12-11
I am having problems with my wireless connection on my desktop pc. It says it is connected to my router but I cannot make any internet connections. The machine is dual-boot w/ Windows XP and ubuntu 12.10. On Windows XP, I have no problems connecting and browsing wirelessly so I know that it's not a problem with my wireless PCI card. On ubuntu 12.10, I can connect to the internet with a wired connection but when I switch over to wireless, it says it is connected to my router but I cannot make any internet connections. Below I have printed some debug statements.

```

skim@YukGaiJung:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"
Linux YukGaiJung 3.5.0-19-generic #30-Ubuntu SMP Tue Nov 13 17:49:53 UTC 2012 i686 i686 i686 GNU/Linux
skim@YukGaiJung:~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. Attansic L1 Gigabit Ethernet [1969:1048] (rev b0)
	Subsystem: ASUSTeK Computer Inc. P5KPL-VM Motherboard [1043:8226]
	Kernel driver in use: atl1
--
04:00.0 Network controller [0280]: Atheros Communications Inc. AR9300 Wireless LAN adaptor [168c:0030] (rev 01)
	Subsystem: Atheros Communications Inc. Device [168c:3112]
	Kernel driver in use: ath9k
skim@YukGaiJung:~$ iwconfig
wlan0     IEEE 802.11abgn  ESSID:"kimchiJigae"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:D4:29:58:D0   
          Bit Rate=117 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:11  Invalid misc:6   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

skim@YukGaiJung:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
skim@YukGaiJung:~$ lsmod
Module                  Size  Used by
dm_crypt               22402  1 
coretemp               13168  0 
kvm_intel             126745  0 
kvm                   357806  1 kvm_intel
gpio_ich               13159  0 
snd_hda_codec_analog    75059  1 
snd_emu10k1_synth      12963  0 
snd_emux_synth         33483  1 snd_emu10k1_synth
snd_seq_virmidi        13220  1 snd_emux_synth
snd_seq_midi_emul      13443  1 snd_emux_synth
microcode              18209  0 
snd_emu10k1           132517  3 snd_emu10k1_synth
arc4                   12473  2 
psmouse                84843  0 
serio_raw              13031  0 
snd_ac97_codec        105616  1 snd_emu10k1
snd_usb_audio         105028  2 
ath9k                 116549  0 
snd_usbmidi_lib        24225  1 snd_usb_audio
mac80211              461161  1 ath9k
snd_hda_intel          32515  2 
snd_hda_codec         111547  2 snd_hda_codec_analog,snd_hda_intel
ac97_bus               12670  1 snd_ac97_codec
snd_util_mem           13786  2 snd_emux_synth,snd_emu10k1
snd_hwdep              13272  4 snd_emux_synth,snd_emu10k1,snd_usb_audio,snd_hda_codec
snd_pcm                80163  5 snd_emu10k1,snd_usb_audio,snd_hda_intel,snd_ac97_codec,snd_hda_codec
emu10k1_gp             12541  0 
gameport               15016  2 emu10k1_gp
snd_seq_midi           13132  0 
snd_rawmidi            25382  4 snd_seq_virmidi,snd_emu10k1,snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14475  2 snd_seq_virmidi,snd_seq_midi
ath9k_common           13783  1 ath9k
ath9k_hw              376155  2 ath9k,ath9k_common
ath                    19187  3 ath9k,ath9k_common,ath9k_hw
lpc_ich                16925  0 
snd_seq                51255  5 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi,snd_seq_midi_event
rfcomm                 37276  0 
asus_atk0110           17390  0 
bnep                   17707  2 
bluetooth             183228  10 rfcomm,bnep
ppdev                  12817  0 
parport_pc             31968  1 
snd_timer              24411  3 snd_emu10k1,snd_pcm,snd_seq
cfg80211              175375  3 ath9k,mac80211,ath
snd_seq_device         14137  5 snd_emu10k1_synth,snd_emu10k1,snd_seq_midi,snd_rawmidi,snd_seq
snd                    61991  27 snd_hda_codec_analog,snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_ac97_codec,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13037  0 
soundcore              14599  1 snd
snd_page_alloc         14036  3 snd_emu10k1,snd_hda_intel,snd_pcm
lp                     13299  0 
parport                40753  3 ppdev,parport_pc,lp
hid_generic            12445  0 
firewire_ohci          35521  0 
usbhid                 41702  0 
hid                    82142  2 hid_generic,usbhid
nouveau               823577  4 
firewire_core          57492  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
floppy                 55444  0 
ttm                    75534  1 nouveau
drm_kms_helper         45271  1 nouveau
drm                   230463  6 nouveau,ttm,drm_kms_helper
atl1                   35516  0 
pata_jmicron           12651  0 
i2c_algo_bit           13197  1 nouveau
mxm_wmi                12859  1 nouveau
video                  18847  1 nouveau
wmi                    18590  2 nouveau,mxm_wmi

```

I would greatly appreciate any help on resolving this issue. Thank you.

---

### Post by skimwpi on 2012-12-17
hmmm...I could really use help here. No replies to my post. Please let me know if more info is required.

Is anyone out there having any problems w/ ubuntu 12.10 and AR9300 Atheros chipset using ath9k?

---

### Post by skimwpi on 2012-12-26
For those who might encounter the same problems as I did, I was able to resolve my connectivity issues with the installation of compat-wireless aka linux-backports-modules-cw that matches with my kernel from ubuntu repository. Alternatively, can install by building and loading the compat-wireless drivers from, [http://linuxwireless.org/en/users/Download/stable/]("http://linuxwireless.org/en/users/Download/stable/")

---

