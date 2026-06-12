---
title: "Don't see home network"
date: 2012-02-02
forum: Networking &amp; Wireless
---

### Post by wesley9 on 2012-02-02
Network adapter sees neighbors internet connections, but I don't see my network on the list.  I have researching this for a while now typing various things in the terminal to no avail.  I am very new to linux, and just updated to 11.10 from 11.04 live disk.  I was on my network fine with 11.04.  I lost my internet connection during the update the first time and i am wondering if that caused this issue.  Anyway would greatly appreciate your help.

kellyrb@ace:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
kellyrb@ace:~$ rfkill list all
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
kellyrb@ace:~$ lsmod
Module                  Size  Used by
ath9k                 112612  0 
ath5k                 145100  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
joydev                 17393  0 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_conexant    52418  1 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_hda_intel          28358  2 
snd_hda_codec          91859  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
psmouse                63474  0 
serio_raw              12990  0 
intel_ips              17753  0 
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
arc4                   12473  2 
asus_laptop            19050  0 
mac80211              393459  2 ath9k,ath5k
sparse_keymap          13658  1 asus_laptop
jmb38x_ms              17406  0 
ath9k_common           13599  1 ath9k
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath9k_hw              293933  2 ath9k,ath9k_common
memstick               15857  1 jmb38x_ms
ath                    19387  3 ath9k,ath5k,ath9k_hw
i915                  509522  8 
mei                    36466  0 
cfg80211              172427  4 ath9k,ath5k,mac80211,ath
drm_kms_helper         32889  1 i915
drm                   196290  4 i915,drm_kms_helper
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   21634  2 
libahci                25761  1 ahci
jme                    40330  0 
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
kellyrb@ace:~$ sudo lshw -C network
[sudo] password for kellyrb: 
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 48:5d:60:e4:8b:07
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.0.0-15-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d2c00000-d2c0ffff
  *-network
       description: Ethernet interface
       product: JMC250 PCI Express Gigabit Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0.5
       bus info: pci@0000:04:00.5
       logical name: eth0
       version: 03
       serial: bc:ae:c5:d0:87:82
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.8 duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:47 memory:d0400000-d0403fff ioport:a100(size=128) ioport:a000(size=256)
kellyrb@ace:~$

---

