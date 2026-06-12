---
title: "Wireless not working on my Compaq 6910P laptop with Intel 4965AGN!!"
date: 2011-11-29
forum: Networking &amp; Wireless
---

### Post by rdhddad on 2011-11-29
Wireless not working on my Compaq 6910P laptop. Running Ocelot. Controller on laptop is Intel 4965AGN. 'Wireless is disabled by hardware switch' is grayed out. New to this but willing to work the issue. Please advise!

---

### Post by praseodym on 2011-11-29
Hi,

please show the terminal outputs of:

```
lsmod
rfkill list
dmesg | grep iwl
iwconfig
```

---

### Post by rdhddad on 2011-11-30
lsmod

Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282739  4 vboxpci,vboxnetadp,vboxnetflt
binfmt_misc            17540  1 
dm_crypt               23199  1 
snd_hda_codec_analog    93522  1 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
arc4                   12529  2 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
pata_pcmcia            17074  1 
iwl4965               132375  0 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17693  0 
iwl_legacy             83487  1 iwl4965
pcmcia                 49378  1 pata_pcmcia
tpm_infineon           17536  0 
hp_wmi                 18092  0 
mac80211              462092  2 iwl4965,iwl_legacy
yenta_socket           28084  0 
pcmcia_rsrc            18430  1 yenta_socket
pcmcia_core            22614  3 pcmcia,yenta_socket,pcmcia_rsrc
snd                    68266  13 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73882  0 
mei                    41480  0 
hp_accel               21880  0 
soundcore              12680  1 snd
irda                  201273  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
cfg80211              199587  3 iwl4965,iwl_legacy,mac80211
sparse_keymap          13890  1 hp_wmi
lis3lv02d              19888  1 hp_accel
serio_raw              13166  0 
ppdev                  17113  0 
tpm_tis                18546  0 
parport_pc             36962  1 
crc_ccitt              12667  1 irda
input_polldev          13896  1 lis3lv02d
lm63                   14398  0 
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
ahci                   26002  2 
firewire_ohci          40722  0 
libahci                26861  1 ahci
firewire_core          63626  1 firewire_ohci
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
crc_itu_t              12707  1 firewire_core
video                  19412  0 
radeon               1016085  3 
wmi                    19256  1 hp_wmi
e1000e                160582  0 
ttm                    76805  1 radeon
drm_kms_helper         42558  1 radeon
drm                   236330  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13423  1 radeon


rfkill list

0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: yes
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

dmesg | grep iwl

[   17.545025] iwl4965: Intel(R) Wireless WiFi 4965 driver for Linux, in-tree:
[   17.545028] iwl4965: Copyright(c) 2003-2011 Intel Corporation
[   17.545114] iwl4965 0000:10:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.545124] iwl4965 0000:10:00.0: setting latency timer to 64
[   17.545158] iwl4965 0000:10:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[   17.583566] iwl4965 0000:10:00.0: device EEPROM VER=0x36, CALIB=0x5
[   17.584149] iwl4965 0000:10:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   17.584237] iwl4965 0000:10:00.0: irq 47 for MSI/MSI-X
[   18.288050] iwl4965 0000:10:00.0: loaded firmware version 228.61.2.24
[   18.729419] ieee80211 phy0: Selected rate control algorithm 'iwl-4965-rs'

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

---

### Post by praseodym on 2011-11-30
Any button/key/switch or key combination (e.g. Fn+F2) to press, even pressing repeatedly during boot-up? Checked the BIOS settings if wireless can be activated there?

Also try:

```
sudo rfkill unblock all
rfkill list           #control
```

---

### Post by rdhddad on 2011-11-30
No key combo at all that i know of. I've looked at the BIOS and there is nothing there. All references to wireless state 'ENABLED'.

Here's the output you requested after running 'rfkill unblock all'...

rfkill list           #control
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: yes
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

---

