---
title: "After upgrading to 11.04 cannot start wireless broadcom card"
date: 2012-03-04
forum: Networking &amp; Wireless
---

### Post by ddesanti on 2012-03-04
Need help on in resolving my wireless card problem. I was using version 10.10 on my Dell Latitude D620 laptop and all network connectivity was working fine. After upgrading to 11.04 my wireless card is not working. It seems it disabled somehow and cannot find a way to turn it back on. Tried reinstalling the Broadcom STA driver but no luck. 

if I run _rfkill list_ it shows me:
dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

Here is information that could help solving my problem:

dds@dds-Latitude-D620:~$ lspci -nnk | grep -iA2 net
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express [14e4:1600] (rev 02)
	Subsystem: Dell Latitude D620 [1028:01c2]
	Kernel driver in use: tg3
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
	Kernel modules: wl, ssb
dds@dds-Latitude-D620:~$ 

dds@dds-Latitude-D620:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

dds@dds-Latitude-D620:~$ 

dds@dds-Latitude-D620:~$ lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_idt      60537  1 
binfmt_misc            13213  1 
joydev                 17322  0 
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
pcmcia                 39671  0 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
i915                  451053  3 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
dell_wmi               12601  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
sparse_keymap          13666  1 dell_wmi
wl                   2642531  0 
dell_laptop            13515  0 
yenta_socket           27230  0 
drm_kms_helper         40971  1 i915
pcmcia_rsrc            18292  1 yenta_socket
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dcdbas                 14054  1 dell_laptop
drm                   184164  4 i915,drm_kms_helper
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
psmouse                73312  0 
soundcore              12600  1 snd
serio_raw              12990  0 
i2c_algo_bit           13184  1 i915
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lib80211               14570  1 wl
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
tg3                   131476  0 
dds@dds-Latitude-D620:~$ 

dds@dds-Latitude-D620:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:efdfc000-efdfffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:18:8b:bb:98:7b
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 firmware=5752-v3.19 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:efcf0000-efcfffff
dds@dds-Latitude-D620:~$

---

### Post by bkratz on 2012-03-04
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
	Kernel modules:[COLOR=Red] wl[/COLOR], ssb
dds@dds-Latitude-D620:~$ 

Here are the things you need to know. The STA driver (wl)  should be replaced with the B43 driver in 11.04. See this page for details.

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)

---

### Post by ddesanti on 2012-03-05
Thanks **bkratz**, this information was very helpful, got my card working again. :D

---

