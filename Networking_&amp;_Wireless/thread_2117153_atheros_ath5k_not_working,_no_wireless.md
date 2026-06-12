---
title: "atheros ath5k not working, no wireless"
date: 2013-02-17
forum: Networking &amp; Wireless
---

### Post by anotherone33 on 2013-02-17
Hello.
Suddendly my wireless not working.  Anyone can help me?

------------------My System:::
:~$ uname -r
3.5.0-24-generic
:~$ cat /etc/issue
Ubuntu 12.10
:~$ uname -a
Linux xxx 3.5.0-24-generic #37-Ubuntu SMP Thu Feb 7 01:50:30 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

:~$ lspci -nn | grep Ath
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. Attansic L1 Gigabit Ethernet [1969:1048] (rev b0)

:~$ iwconfig
eth0      no wireless extensions.

eth1      no wireless extensions.

lo        no wireless extensions.


-------------The problems
:~$ dmesg | grep -e ath5 -e wlan

[   16.399257] ath5k 0000:01:00.0: registered as 'phy0'
[   16.465812] ath5k: phy0: POST Failed !!!
[   16.465854] ath5k: probe of 0000:01:00.0 failed with error -11
[  176.973774] ath5k 0000:01:00.0: registered as 'phy0'
[  176.977840] ath5k: phy0: Invalid max custom EEPROM size: 173384858 (0xa55a49a) max expected: 2496 (0x09c0)
[  176.977845] ath5k: phy0: unable to init EEPROM
[  176.977881] ath5k: probe of 0000:01:00.0 failed with error -5
[ 1610.489311] ath5k: phy0: unable to read address from EEPROM
[ 1610.489370] ath5k: probe of 0000:01:00.0 failed with error -5
[ 1685.920054] ath5k 0000:01:00.0: Refused to change power state, currently in D3
[ 1685.920134] ath5k 0000:01:00.0: registered as 'phy0'
[ 1685.936425] ath5k: phy0: failed to wakeup the MAC Chip
[ 1685.936466] ath5k: probe of 0000:01:00.0 failed with error -5


:~$ lshw -C network
-----------gives:
*-network UNCLAIMED
...


------------- Trying using this commands : enabling network before and then 
:~$ sudo modprobe -r -f ath5k
  or
:~$ sudo rmmod  ath5k


:~$ sudo modprobe ath5k




Tryed now: 
sudo apt-get install linux-backports-modules-hv-3.5.0-24-generic

And rebooting. This not solves it.

-----------------Then also:
:~$ sudo su
:~$ echo ath9k >> /etc/modules
:~$ exit




More documenting:
 more /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
ath9k

:~$ lsmod
Module                  Size  Used by
ath5k                 150269  0 
rfcomm                 46620  0 
bnep                   18141  2 
bluetooth             209249  10 rfcomm,bnep
binfmt_misc            17501  1 
coretemp               13401  0 
kvm_intel             132760  0 
kvm                   414071  1 kvm_intel
snd_hda_codec_realtek    78147  1 
ppdev                  17074  0 
gpio_ich               13384  0 
microcode              22804  0 
serio_raw              13216  0 
joydev                 17458  0 
parport_pc             32689  1 
asus_atk0110           17647  0 
snd_hda_intel          33492  3 
snd_hda_codec         134213  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17699  1 snd_hda_codec
snd_pcm                96668  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0 
snd_rawmidi            30513  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29426  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  520615  4 
ath9k                 131355  0 
snd                    78921  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lpc_ich                17062  0 
mac_hid                13206  0 
mac80211              540032  2 ath5k,ath9k
ath9k_common           14056  1 ath9k
drm_kms_helper         49113  1 i915
drm                   288721  5 i915,drm_kms_helper
ath9k_hw              395307  2 ath9k,ath9k_common
soundcore              15048  1 snd
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13414  1 i915
video                  19391  1 i915
ath                    23828  4 ath5k,ath9k,ath9k_common,ath9k_hw
cfg80211              206797  4 ath5k,ath9k,mac80211,ath
lp                     17760  0 
parport                46346  3 ppdev,parport_pc,lp
hid_logitech           26586  0 
ff_memless             13014  1 hid_logitech
usbhid                 46987  1 hid_logitech
hid                   100411  2 hid_logitech,usbhid
floppy                 69453  1 
8139too                31918  0 
8139cp                 27235  0 
atl1                   40382  0

---

### Post by anotherone33 on 2013-02-18
Anyone can or want help me?

In the last days my wireless suddedly go down and my edit connection can see the stamp that wireless connection was working two days ago. 

I looked on forums and I learn some commands. I tryed solutions.

Yesterday for a moment I could have again wireless appear. But I cannot reproduce the exact combination to have ath5 and wireless working again.

Just booting.

:~$ dmesg | grep  ath 
```
[   15.287837] ath5k 0000:01:00.0: registered as 'phy0'
[   15.316315] ath5k: phy0: POST Failed !!!
[   15.316361] ath5k: probe of 0000:01:00.0 failed with error -11

```

here the network UNCLAIMED:

:~$ sudo lshw -class network
[sudo] password for xx: 
 ```
 *-network               
       description: Ethernet interface
       product: Attansic L1 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: b0
       serial: 00:1a:92:62:39:d8
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1 driverversion=2.1.3 duplex=full ip=192.168.1.6 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:48 memory:fe9c0000-fe9fffff memory:fe9a0000-fe9bffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
       resources: memory:fe8f0000-fe8fffff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 10
       serial: 00:50:22:e7:7f:65
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:19 ioport:e800(size=256) memory:febffc00-febffcff memory:febe0000-febeffff
```

:~$ sudo apt-get install linux-backports-modules-cw-3.6-3.5.0-24-generic

:~$ sudo apt-get install linux-backports-modules-hv-3.6-3.5.0-24-generic

:~$ sudo apt-get install linux-headers-lbm-3.5.0-24-generic

It seems worst situation:

```
:~$ dmesg | grep  ath 
[   15.287837] ath5k 0000:01:00.0: registered as 'phy0'
[   15.316315] ath5k: phy0: POST Failed !!!
[   15.316361] ath5k: probe of 0000:01:00.0 failed with error -11
[ 1115.180899] ath5k 0000:01:00.0: registered as 'phy0'
[ 1115.184979] ath5k: phy0: unable to init EEPROM
[ 1115.185021] ath5k: probe of 0000:01:00.0 failed with error -5
[13901.843200] ath5k: disagrees about version of symbol ath_hw_keyreset
[13901.843204] ath5k: Unknown symbol ath_hw_keyreset (err -22)
[13901.843213] ath5k: disagrees about version of symbol ath_key_config
[13901.843214] ath5k: Unknown symbol ath_key_config (err -22)
[13901.843227] ath5k: disagrees about version of symbol ieee80211_free_hw
[13901.843228] ath5k: Unknown symbol ieee80211_free_hw (err -22)
[13901.843235] ath5k: disagrees about version of symbol ath_rxbuf_alloc
[13901.843237] ath5k: Unknown symbol ath_rxbuf_alloc (err -22)
[13901.843240] ath5k: disagrees about version of symbol ieee80211_alloc_hw
[13901.843242] ath5k: Unknown symbol ieee80211_alloc_hw (err -22)
[13901.843248] ath5k: disagrees about version of symbol regulatory_hint
[13901.843249] ath5k: Unknown symbol regulatory_hint (err -22)
[13901.843257] ath5k: disagrees about version of symbol ieee80211_register_hw
[13901.843259] ath5k: Unknown symbol ieee80211_register_hw (err -22)
[13901.843266] ath5k: disagrees about version of symbol ieee80211_ctstoself_duration
[13901.843268] ath5k: Unknown symbol ieee80211_ctstoself_duration (err -22)
[13901.843274] ath5k: disagrees about version of symbol ieee80211_get_hdrlen_from_skb
[13901.843276] ath5k: Unknown symbol ieee80211_get_hdrlen_from_skb (err -22)
[13901.843279] ath5k: disagrees about version of symbol ieee80211_generic_frame_duration
[13901.843281] ath5k: Unknown symbol ieee80211_generic_frame_duration (err -22)
[13901.843285] ath5k: disagrees about version of symbol ieee80211_wake_queue
[13901.843287] ath5k: Unknown symbol ieee80211_wake_queue (err -22)
[13901.843293] ath5k: disagrees about version of symbol ath_hw_setbssidmask
[13901.843294] ath5k: Unknown symbol ath_hw_setbssidmask (err -22)
[13901.843304] ath5k: disagrees about version of symbol __ieee80211_get_tx_led_name
[13901.843306] ath5k: Unknown symbol __ieee80211_get_tx_led_name (err -22)
[13901.843309] ath5k: disagrees about version of symbol ieee80211_get_buffered_bc
[13901.843311] ath5k: Unknown symbol ieee80211_get_buffered_bc (err -22)
[13901.843315] ath5k: disagrees about version of symbol ath_hw_cycle_counters_update
[13901.843317] ath5k: Unknown symbol ath_hw_cycle_counters_update (err -22)
[13901.843325] ath5k: disagrees about version of symbol wiphy_rfkill_set_hw_state
[13901.843326] ath5k: Unknown symbol wiphy_rfkill_set_hw_state (err -22)
[13901.843334] ath5k: disagrees about version of symbol ath_regd_get_band_ctl
[13901.843336] ath5k: Unknown symbol ath_regd_get_band_ctl (err -22)
[13901.843339] ath5k: disagrees about version of symbol __ieee80211_get_rx_led_name
[13901.843341] ath5k: Unknown symbol __ieee80211_get_rx_led_name (err -22)
[13901.843344] ath5k: disagrees about version of symbol ath_hw_get_listen_time
[13901.843346] ath5k: Unknown symbol ath_hw_get_listen_time (err -22)
[13901.843355] ath5k: disagrees about version of symbol wiphy_to_ieee80211_hw
[13901.843357] ath5k: Unknown symbol wiphy_to_ieee80211_hw (err -22)
[13901.843360] ath5k: disagrees about version of symbol ath_reg_notifier_apply
[13901.843362] ath5k: Unknown symbol ath_reg_notifier_apply (err -22)
[13901.843368] ath5k: disagrees about version of symbol ieee80211_queue_delayed_work
[13901.843370] ath5k: Unknown symbol ieee80211_queue_delayed_work (err -22)
[13901.843378] ath5k: disagrees about version of symbol ieee80211_rx
[13901.843380] ath5k: Unknown symbol ieee80211_rx (err -22)
[13901.843389] ath5k: disagrees about version of symbol ieee80211_wake_queues
[13901.843391] ath5k: Unknown symbol ieee80211_wake_queues (err -22)
[13901.843402] ath5k: disagrees about version of symbol ieee80211_tx_status
[13901.843404] ath5k: Unknown symbol ieee80211_tx_status (err -22)
[13901.843406] ath5k: disagrees about version of symbol ieee80211_stop_queue
[13901.843408] ath5k: Unknown symbol ieee80211_stop_queue (err -22)
[13901.843411] ath5k: disagrees about version of symbol ieee80211_stop_queues
[13901.843413] ath5k: Unknown symbol ieee80211_stop_queues (err -22)
[13901.843418] ath5k: disagrees about version of symbol ieee80211_iterate_active_interfaces_atomic
[13901.843420] ath5k: Unknown symbol ieee80211_iterate_active_interfaces_atomic (err -22)
[13901.843429] ath5k: disagrees about version of symbol ieee80211_channel_to_frequency
[13901.843431] ath5k: Unknown symbol ieee80211_channel_to_frequency (err -22)
[13901.843434] ath5k: disagrees about version of symbol ieee80211_unregister_hw
[13901.843436] ath5k: Unknown symbol ieee80211_unregister_hw (err -22)
[13901.843439] ath5k: disagrees about version of symbol ath_regd_init
[13901.843440] ath5k: Unknown symbol ath_regd_init (err -22)
[13901.843443] ath5k: disagrees about version of symbol ieee80211_beacon_get_tim
[13901.843445] ath5k: Unknown symbol ieee80211_beacon_get_tim (err -22)
[13901.843451] ath5k: disagrees about version of symbol ath_key_delete
[13901.843452] ath5k: Unknown symbol ath_key_delete (err -22)
[13901.843462] ath5k: disagrees about version of symbol ieee80211_queue_work
[13901.843464] ath5k: Unknown symbol ieee80211_queue_work (err -22)
[13901.843469] ath5k: disagrees about version of symbol ieee80211_rts_duration
[13901.843471] ath5k: Unknown symbol ieee80211_rts_duration (err -22)
[13914.292182] ath5k: disagrees about version of symbol ath_hw_keyreset
[13914.292188] ath5k: Unknown symbol ath_hw_keyreset (err -22)
[13914.292201] ath5k: disagrees about version of symbol ath_key_config
[13914.292204] ath5k: Unknown symbol ath_key_config (err -22)
[13914.292220] ath5k: disagrees about version of symbol ieee80211_free_hw
[13914.292223] ath5k: Unknown symbol ieee80211_free_hw (err -22)
[13914.292232] ath5k: disagrees about version of symbol ath_rxbuf_alloc
[13914.292234] ath5k: Unknown symbol ath_rxbuf_alloc (err -22)
[13914.292240] ath5k: disagrees about version of symbol ieee80211_alloc_hw
[13914.292242] ath5k: Unknown symbol ieee80211_alloc_hw (err -22)
[13914.292250] ath5k: disagrees about version of symbol regulatory_hint
[13914.292253] ath5k: Unknown symbol regulatory_hint (err -22)
[13914.292263] ath5k: disagrees about version of symbol ieee80211_register_hw
[13914.292265] ath5k: Unknown symbol ieee80211_register_hw (err -22)
[13914.292276] ath5k: disagrees about version of symbol ieee80211_ctstoself_duration
[13914.292278] ath5k: Unknown symbol ieee80211_ctstoself_duration (err -22)
[13914.292287] ath5k: disagrees about version of symbol ieee80211_get_hdrlen_from_skb
[13914.292290] ath5k: Unknown symbol ieee80211_get_hdrlen_from_skb (err -22)
[13914.292295] ath5k: disagrees about version of symbol ieee80211_generic_frame_duration
[13914.292297] ath5k: Unknown symbol ieee80211_generic_frame_duration (err -22)
[13914.292304] ath5k: disagrees about version of symbol ieee80211_wake_queue
[13914.292307] ath5k: Unknown symbol ieee80211_wake_queue (err -22)
[13914.292315] ath5k: disagrees about version of symbol ath_hw_setbssidmask
[13914.292317] ath5k: Unknown symbol ath_hw_setbssidmask (err -22)
[13914.292331] ath5k: disagrees about version of symbol __ieee80211_get_tx_led_name
[13914.292333] ath5k: Unknown symbol __ieee80211_get_tx_led_name (err -22)
[13914.292338] ath5k: disagrees about version of symbol ieee80211_get_buffered_bc
[13914.292341] ath5k: Unknown symbol ieee80211_get_buffered_bc (err -22)
[13914.292347] ath5k: disagrees about version of symbol ath_hw_cycle_counters_update
[13914.292349] ath5k: Unknown symbol ath_hw_cycle_counters_update (err -22)
[13914.292360] ath5k: disagrees about version of symbol wiphy_rfkill_set_hw_state
[13914.292363] ath5k: Unknown symbol wiphy_rfkill_set_hw_state (err -22)
[13914.292374] ath5k: disagrees about version of symbol ath_regd_get_band_ctl
[13914.292376] ath5k: Unknown symbol ath_regd_get_band_ctl (err -22)
[13914.292381] ath5k: disagrees about version of symbol __ieee80211_get_rx_led_name
[13914.292383] ath5k: Unknown symbol __ieee80211_get_rx_led_name (err -22)
[13914.292388] ath5k: disagrees about version of symbol ath_hw_get_listen_time
[13914.292391] ath5k: Unknown symbol ath_hw_get_listen_time (err -22)
[13914.292403] ath5k: disagrees about version of symbol wiphy_to_ieee80211_hw
[13914.292406] ath5k: Unknown symbol wiphy_to_ieee80211_hw (err -22)
[13914.292411] ath5k: disagrees about version of symbol ath_reg_notifier_apply
[13914.292413] ath5k: Unknown symbol ath_reg_notifier_apply (err -22)
[13914.292422] ath5k: disagrees about version of symbol ieee80211_queue_delayed_work
[13914.292425] ath5k: Unknown symbol ieee80211_queue_delayed_work (err -22)
[13914.292437] ath5k: disagrees about version of symbol ieee80211_rx
[13914.292439] ath5k: Unknown symbol ieee80211_rx (err -22)
[13914.292453] ath5k: disagrees about version of symbol ieee80211_wake_queues
[13914.292455] ath5k: Unknown symbol ieee80211_wake_queues (err -22)
[13914.292471] ath5k: disagrees about version of symbol ieee80211_tx_status
[13914.292473] ath5k: Unknown symbol ieee80211_tx_status (err -22)
[13914.292478] ath5k: disagrees about version of symbol ieee80211_stop_queue
[13914.292480] ath5k: Unknown symbol ieee80211_stop_queue (err -22)
[13914.292485] ath5k: disagrees about version of symbol ieee80211_stop_queues
[13914.292487] ath5k: Unknown symbol ieee80211_stop_queues (err -22)
[13914.292495] ath5k: disagrees about version of symbol ieee80211_iterate_active_interfaces_atomic
[13914.292498] ath5k: Unknown symbol ieee80211_iterate_active_interfaces_atomic (err -22)
[13914.292512] ath5k: disagrees about version of symbol ieee80211_channel_to_frequency
[13914.292514] ath5k: Unknown symbol ieee80211_channel_to_frequency (err -22)
[13914.292518] ath5k: disagrees about version of symbol ieee80211_unregister_hw
[13914.292521] ath5k: Unknown symbol ieee80211_unregister_hw (err -22)
[13914.292525] ath5k: disagrees about version of symbol ath_regd_init
[13914.292528] ath5k: Unknown symbol ath_regd_init (err -22)
[13914.292532] ath5k: disagrees about version of symbol ieee80211_beacon_get_tim
[13914.292534] ath5k: Unknown symbol ieee80211_beacon_get_tim (err -22)
[13914.292545] ath5k: disagrees about version of symbol ath_key_delete
[13914.292548] ath5k: Unknown symbol ath_key_delete (err -22)
[13914.292562] ath5k: disagrees about version of symbol ieee80211_queue_work
[13914.292565] ath5k: Unknown symbol ieee80211_queue_work (err -22)
[13914.292572] ath5k: disagrees about version of symbol ieee80211_rts_duration
[13914.292575] ath5k: Unknown symbol ieee80211_rts_duration (err -22)
[14320.871723] ath5k: disagrees about version of symbol ath_hw_keyreset
[14320.871729] ath5k: Unknown symbol ath_hw_keyreset (err -22)
[14320.871742] ath5k: disagrees about version of symbol ath_key_config
[14320.871746] ath5k: Unknown symbol ath_key_config (err -22)
[14320.871762] ath5k: disagrees about version of symbol ieee80211_free_hw
[14320.871764] ath5k: Unknown symbol ieee80211_free_hw (err -22)
[14320.871773] ath5k: disagrees about version of symbol ath_rxbuf_alloc
[14320.871775] ath5k: Unknown symbol ath_rxbuf_alloc (err -22)
[14320.871781] ath5k: disagrees about version of symbol ieee80211_alloc_hw
[14320.871783] ath5k: Unknown symbol ieee80211_alloc_hw (err -22)
[14320.871792] ath5k: disagrees about version of symbol regulatory_hint
[14320.871794] ath5k: Unknown symbol regulatory_hint (err -22)
[14320.871804] ath5k: disagrees about version of symbol ieee80211_register_hw
[14320.871806] ath5k: Unknown symbol ieee80211_register_hw (err -22)
[14320.871817] ath5k: disagrees about version of symbol ieee80211_ctstoself_duration
[14320.871819] ath5k: Unknown symbol ieee80211_ctstoself_duration (err -22)
[14320.871828] ath5k: disagrees about version of symbol ieee80211_get_hdrlen_from_skb
[14320.871830] ath5k: Unknown symbol ieee80211_get_hdrlen_from_skb (err -22)
[14320.871836] ath5k: disagrees about version of symbol ieee80211_generic_frame_duration
[14320.871838] ath5k: Unknown symbol ieee80211_generic_frame_duration (err -22)
[14320.871845] ath5k: disagrees about version of symbol ieee80211_wake_queue
[14320.871847] ath5k: Unknown symbol ieee80211_wake_queue (err -22)
[14320.871855] ath5k: disagrees about version of symbol ath_hw_setbssidmask
[14320.871858] ath5k: Unknown symbol ath_hw_setbssidmask (err -22)
[14320.871871] ath5k: disagrees about version of symbol __ieee80211_get_tx_led_name
[14320.871874] ath5k: Unknown symbol __ieee80211_get_tx_led_name (err -22)
[14320.871879] ath5k: disagrees about version of symbol ieee80211_get_buffered_bc
[14320.871882] ath5k: Unknown symbol ieee80211_get_buffered_bc (err -22)
[14320.871887] ath5k: disagrees about version of symbol ath_hw_cycle_counters_update
[14320.871890] ath5k: Unknown symbol ath_hw_cycle_counters_update (err -22)
[14320.871901] ath5k: disagrees about version of symbol wiphy_rfkill_set_hw_state
[14320.871904] ath5k: Unknown symbol wiphy_rfkill_set_hw_state (err -22)
[14320.871914] ath5k: disagrees about version of symbol ath_regd_get_band_ctl
[14320.871917] ath5k: Unknown symbol ath_regd_get_band_ctl (err -22)
[14320.871921] ath5k: disagrees about version of symbol __ieee80211_get_rx_led_name
[14320.871924] ath5k: Unknown symbol __ieee80211_get_rx_led_name (err -22)
[14320.871928] ath5k: disagrees about version of symbol ath_hw_get_listen_time
[14320.871931] ath5k: Unknown symbol ath_hw_get_listen_time (err -22)
[14320.871943] ath5k: disagrees about version of symbol wiphy_to_ieee80211_hw
[14320.871946] ath5k: Unknown symbol wiphy_to_ieee80211_hw (err -22)
[14320.871951] ath5k: disagrees about version of symbol ath_reg_notifier_apply
[14320.871954] ath5k: Unknown symbol ath_reg_notifier_apply (err -22)
[14320.871963] ath5k: disagrees about version of symbol ieee80211_queue_delayed_work
[14320.871965] ath5k: Unknown symbol ieee80211_queue_delayed_work (err -22)
[14320.871978] ath5k: disagrees about version of symbol ieee80211_rx
[14320.871980] ath5k: Unknown symbol ieee80211_rx (err -22)
[14320.872024] ath5k: disagrees about version of symbol ieee80211_wake_queues
[14320.872027] ath5k: Unknown symbol ieee80211_wake_queues (err -22)
[14320.872044] ath5k: disagrees about version of symbol ieee80211_tx_status
[14320.872053] ath5k: Unknown symbol ieee80211_tx_status (err -22)
[14320.872063] ath5k: disagrees about version of symbol ieee80211_stop_queue
[14320.872072] ath5k: Unknown symbol ieee80211_stop_queue (err -22)
[14320.872083] ath5k: disagrees about version of symbol ieee80211_stop_queues
[14320.872092] ath5k: Unknown symbol ieee80211_stop_queues (err -22)
[14320.872106] ath5k: disagrees about version of symbol ieee80211_iterate_active_interfaces_atomic
[14320.872114] ath5k: Unknown symbol ieee80211_iterate_active_interfaces_atomic (err -22)
[14320.872134] ath5k: disagrees about version of symbol ieee80211_channel_to_frequency
[14320.872137] ath5k: Unknown symbol ieee80211_channel_to_frequency (err -22)
[14320.872141] ath5k: disagrees about version of symbol ieee80211_unregister_hw
[14320.872144] ath5k: Unknown symbol ieee80211_unregister_hw (err -22)
[14320.872149] ath5k: disagrees about version of symbol ath_regd_init
[14320.872151] ath5k: Unknown symbol ath_regd_init (err -22)
[14320.872155] ath5k: disagrees about version of symbol ieee80211_beacon_get_tim
[14320.872158] ath5k: Unknown symbol ieee80211_beacon_get_tim (err -22)
[14320.872167] ath5k: disagrees about version of symbol ath_key_delete
[14320.872170] ath5k: Unknown symbol ath_key_delete (err -22)
[14320.872184] ath5k: disagrees about version of symbol ieee80211_queue_work
[14320.872187] ath5k: Unknown symbol ieee80211_queue_work (err -22)
[14320.872195] ath5k: disagrees about version of symbol ieee80211_rts_duration
[14320.872197] ath5k: Unknown symbol ieee80211_rts_duration (err -22)
[14332.237985] ath5k: disagrees about version of symbol ath_hw_keyreset
[14332.237989] ath5k: Unknown symbol ath_hw_keyreset (err -22)
[14332.238002] ath5k: disagrees about version of symbol ath_key_config
[14332.238005] ath5k: Unknown symbol ath_key_config (err -22)
[14332.238022] ath5k: disagrees about version of symbol ieee80211_free_hw
[14332.238024] ath5k: Unknown symbol ieee80211_free_hw (err -22)
[14332.238033] ath5k: disagrees about version of symbol ath_rxbuf_alloc
[14332.238035] ath5k: Unknown symbol ath_rxbuf_alloc (err -22)
[14332.238041] ath5k: disagrees about version of symbol ieee80211_alloc_hw
[14332.238043] ath5k: Unknown symbol ieee80211_alloc_hw (err -22)
[14332.238051] ath5k: disagrees about version of symbol regulatory_hint
[14332.238054] ath5k: Unknown symbol regulatory_hint (err -22)
[14332.238063] ath5k: disagrees about version of symbol ieee80211_register_hw
[14332.238066] ath5k: Unknown symbol ieee80211_register_hw (err -22)
[14332.238076] ath5k: disagrees about version of symbol ieee80211_ctstoself_duration
[14332.238078] ath5k: Unknown symbol ieee80211_ctstoself_duration (err -22)
[14332.238087] ath5k: disagrees about version of symbol ieee80211_get_hdrlen_from_skb
[14332.238090] ath5k: Unknown symbol ieee80211_get_hdrlen_from_skb (err -22)
[14332.238095] ath5k: disagrees about version of symbol ieee80211_generic_frame_duration
[14332.238097] ath5k: Unknown symbol ieee80211_generic_frame_duration (err -22)
[14332.238104] ath5k: disagrees about version of symbol ieee80211_wake_queue
[14332.238106] ath5k: Unknown symbol ieee80211_wake_queue (err -22)
[14332.238115] ath5k: disagrees about version of symbol ath_hw_setbssidmask
[14332.238117] ath5k: Unknown symbol ath_hw_setbssidmask (err -22)
[14332.238131] ath5k: disagrees about version of symbol __ieee80211_get_tx_led_name
[14332.238134] ath5k: Unknown symbol __ieee80211_get_tx_led_name (err -22)
[14332.238139] ath5k: disagrees about version of symbol ieee80211_get_buffered_bc
[14332.238142] ath5k: Unknown symbol ieee80211_get_buffered_bc (err -22)
[14332.238147] ath5k: disagrees about version of symbol ath_hw_cycle_counters_update
[14332.238150] ath5k: Unknown symbol ath_hw_cycle_counters_update (err -22)
[14332.238161] ath5k: disagrees about version of symbol wiphy_rfkill_set_hw_state
[14332.238163] ath5k: Unknown symbol wiphy_rfkill_set_hw_state (err -22)
[14332.238174] ath5k: disagrees about version of symbol ath_regd_get_band_ctl
[14332.238176] ath5k: Unknown symbol ath_regd_get_band_ctl (err -22)
[14332.238180] ath5k: disagrees about version of symbol __ieee80211_get_rx_led_name
[14332.238183] ath5k: Unknown symbol __ieee80211_get_rx_led_name (err -22)
[14332.238188] ath5k: disagrees about version of symbol ath_hw_get_listen_time
[14332.238191] ath5k: Unknown symbol ath_hw_get_listen_time (err -22)
[14332.238204] ath5k: disagrees about version of symbol wiphy_to_ieee80211_hw
[14332.238206] ath5k: Unknown symbol wiphy_to_ieee80211_hw (err -22)
[14332.238211] ath5k: disagrees about version of symbol ath_reg_notifier_apply
[14332.238214] ath5k: Unknown symbol ath_reg_notifier_apply (err -22)
[14332.238223] ath5k: disagrees about version of symbol ieee80211_queue_delayed_work
[14332.238225] ath5k: Unknown symbol ieee80211_queue_delayed_work (err -22)
[14332.238237] ath5k: disagrees about version of symbol ieee80211_rx
[14332.238240] ath5k: Unknown symbol ieee80211_rx (err -22)
[14332.238253] ath5k: disagrees about version of symbol ieee80211_wake_queues
[14332.238256] ath5k: Unknown symbol ieee80211_wake_queues (err -22)
[14332.238271] ath5k: disagrees about version of symbol ieee80211_tx_status
[14332.238274] ath5k: Unknown symbol ieee80211_tx_status (err -22)
[14332.238278] ath5k: disagrees about version of symbol ieee80211_stop_queue
[14332.238281] ath5k: Unknown symbol ieee80211_stop_queue (err -22)
[14332.238285] ath5k: disagrees about version of symbol ieee80211_stop_queues
[14332.238287] ath5k: Unknown symbol ieee80211_stop_queues (err -22)
[14332.238295] ath5k: disagrees about version of symbol ieee80211_iterate_active_interfaces_atomic
[14332.238298] ath5k: Unknown symbol ieee80211_iterate_active_interfaces_atomic (err -22)
[14332.238311] ath5k: disagrees about version of symbol ieee80211_channel_to_frequency
[14332.238314] ath5k: Unknown symbol ieee80211_channel_to_frequency (err -22)
[14332.238318] ath5k: disagrees about version of symbol ieee80211_unregister_hw
[14332.238320] ath5k: Unknown symbol ieee80211_unregister_hw (err -22)
[14332.238325] ath5k: disagrees about version of symbol ath_regd_init
[14332.238327] ath5k: Unknown symbol ath_regd_init (err -22)
[14332.238331] ath5k: disagrees about version of symbol ieee80211_beacon_get_tim
[14332.238334] ath5k: Unknown symbol ieee80211_beacon_get_tim (err -22)
[14332.238343] ath5k: disagrees about version of symbol ath_key_delete
[14332.238346] ath5k: Unknown symbol ath_key_delete (err -22)
[14332.238360] ath5k: disagrees about version of symbol ieee80211_queue_work
[14332.238363] ath5k: Unknown symbol ieee80211_queue_work (err -22)
[14332.238370] ath5k: disagrees about version of symbol ieee80211_rts_duration
[14332.238373] ath5k: Unknown symbol ieee80211_rts_duration (err -22)

```

:~$ sudo -s
:~$ echo blacklist ath_pci >> /etc/modprobe.d/blacklist


[14638.544213] ath9k: ath9k: Driver unloaded
[14681.824721] ath5k 0000:01:00.0: registered as 'phy0'
[14681.888946] ath5k: phy0: failed to resume the MAC Chip
[14681.888998] ath5k: probe of 0000:01:00.0 failed with error -5
...

---

### Post by anotherone33 on 2013-02-19
Hello,
anyone can help me?

what's happen?
:~$ dmesg | grep ath
[    6.927778] ath5k 0000:01:00.0: registered as 'phy0'
[    6.992562] ath5k: phy0: failed to resume the MAC Chip
[    6.992588] ath5k: probe of 0000:01:00.0 failed with error -5
[   15.470244] type=1400 audit(1361274885.541:22): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=967 comm="apparmor_parser"

---

### Post by anotherone33 on 2013-02-19
Is there someone who can help me to get back my wireless working ?

Thank, you

---

### Post by steeldriver on 2013-02-19
your original problem sounds like it might be some kind of power management issue? like the device is not waking up from sleep / hibernate

---

### Post by anotherone33 on 2013-02-20
Thank you, I appreciate very much you help steeldriver.
Do you know any direct way I can wake up my wireless from sleep/hibernate? I tryed $ ifup -a . No success.

Can you help me to remove any damn I can have done in my tries and leave a virgin situation where possibly apply the wake up procedure?

Sincerely I also have no procedure to recognize if the wireless simply suddendly broken. If it is so, probably not responding at all? (and this is not the case, real?).

In my searches I found something about a driver not associated with the wireless, and this because "network UNCLAIMED". But sincerely I haven't found an exact procedure resolve the unclaimed, or for some reason the procedure with me doesn't solve.

---

### Post by steeldriver on 2013-02-20
These things can be hard to fix - chili555 has previously posted a possible solution

[http://ubuntuforums.org/showthread.php?t=2004690&highlight=sleep](http://ubuntuforums.org/showthread.php?t=2004690&highlight=sleep)

You will need to change the module name from iwlwifi to ath5k

IIRC there's also a condition where Windows can leave some wireless hardware in a state that Linux can't wake it from - that's only if you dual boot of course, and I don't know if it applies to the Atheros chipset(s)

You may want to remove the backports package as well, since that seems to have made things worse

---

### Post by anotherone33 on 2013-02-20
Hi,
everybody.
Unfortunately may be I solved.

This is my output now:
**$ lspci -nn | grep Ath**
```
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. Attansic L1 Gigabit Ethernet [1969:1048] (rev b0)
```

May be this is the solution to the question: how can I recognize if my controller suddendly breaks?
(may be)Answer: because no response in **lspci -nn** , and no module response in **dmesg | grep -e ath -e wlan**


If no news from you, bad news, and so have I to buy a wireless-usb-pen or a new controller?  Can you confirm?

Thanks for you attention...

I read your answer now, below... I'll remove backports, thanks.

---

### Post by anotherone33 on 2013-02-23
Hey ! wireless not broken! It seems back again!!!

[SIZE="3"]If you can again give me an help ... welcoming ;)[/SIZE]

:~$ **sudo lshw -class network**
[sudo] password for mu: 
```
  *-network               
       description: Ethernet interface
       product: Attansic L1 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: b0
       serial: 00:1a:92:62:39:d8
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1 driverversion=2.1.3 duplex=full ip=192.168.1.6 latency=0 link=yes multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:48 memory:fe9c0000-fe9fffff memory:fe9a0000-fe9bffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
       resources: memory:fe8f0000-fe8fffff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 10
       serial: 00:50:22:e7:7f:65
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:19 ioport:e800(size=256) memory:febffc00-febffcff memory:febe0000-febeffff
```
[again unclaimed]

:~$ **dmesg | grep  ath **
[```
   15.674958] ath5k 0000:01:00.0: registered as 'phy0'
[   15.678022] ath5k: phy0: POST Failed !!!
[   15.684015] ath5k: probe of 0000:01:00.0 failed with error -11
```

:~$ **sudo modprobe ath5k**
```
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release
```.

:~$ **sudo more /etc/modprobe.d/blacklist**
blacklist ath_pci

:~$ **sudo rm /etc/modprobe.d/blacklist**
:~$ **sudo more /etc/modprobe.d/blacklist**
/etc/modprobe.d/blacklist: File o directory non esistente

[...removing old patch tries]

(deactivating net) (needs?)

:~$ **sudo rmmod ath5k**

(reactivating net) (needs?)

:~$ **sudo modprobe ath5k**
:~$ **dmesg | grep  ath** 
```
[   15.674958] ath5k 0000:01:00.0: registered as 'phy0'
[   15.678022] ath5k: phy0: POST Failed !!!
[   15.684015] ath5k: probe of 0000:01:00.0 failed with error -11
[ 1615.339908] ath5k 0000:01:00.0: registered as 'phy1'
[ 1615.404440] ath5k: phy1: failed to resume the MAC Chip
[ 1615.404479] ath5k: probe of 0000:01:00.0 failed with error -5
```

Here again, failed to wake up/freeze the wireless. Was it a secondary effect from a suspended session?

---

### Post by anotherone33 on 2013-02-23
From a different point of view:


:~$** dmesg ath | grep ath5**
```
[   27.090811] ath5k 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   27.090822] ath5k 0000:01:00.0: setting latency timer to 64
[   27.090855] ath5k 0000:01:00.0: registered as 'phy0'
[   27.094112] ath5k phy0: unable to init EEPROM
[   27.094153] ath5k 0000:01:00.0: PCI INT A disabled
[   27.094159] ath5k: probe of 0000:01:00.0 failed with error -5

```


:~$** lsb_release -a**
```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.3 LTS
Release:	10.04
Codename:	lucid
```

:~$** uname -mr**
2.6.32-38-generic x86_64

Again tryed, with abled or with disabled net :
[B]rmmod -f ath5k
rfkill unblock all
modprobe ath5k[/B]
Result:
```
[   27.090811] ath5k 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   27.090822] ath5k 0000:01:00.0: setting latency timer to 64
[   27.090855] ath5k 0000:01:00.0: registered as 'phy0'
[   27.094112] ath5k phy0: unable to init EEPROM
[   27.094153] ath5k 0000:01:00.0: PCI INT A disabled
[   27.094159] ath5k: probe of 0000:01:00.0 failed with error -5
[  966.563872] ath5k 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  966.563887] ath5k 0000:01:00.0: setting latency timer to 64
[  966.563965] ath5k 0000:01:00.0: registered as 'phy1'
[  966.567245] ath5k phy1: unable to init EEPROM
[  966.567271] ath5k 0000:01:00.0: PCI INT A disabled
[  966.567283] ath5k: probe of 0000:01:00.0 failed with error -5
[ 1038.246810] ath5k 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 1038.246826] ath5k 0000:01:00.0: setting latency timer to 64
[ 1038.247359] ath5k 0000:01:00.0: registered as 'phy2'
[ 1038.249457] ath5k phy2: POST Failed !!!
[ 1038.249474] ath5k 0000:01:00.0: PCI INT A disabled
[ 1038.249483] ath5k: probe of 0000:01:00.0 failed with error -11
[ 1079.695386] ath5k 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 1079.695400] ath5k 0000:01:00.0: setting latency timer to 64
[ 1079.695451] ath5k 0000:01:00.0: registered as 'phy3'
[ 1079.698653] ath5k phy3: unable to init EEPROM
[ 1079.698671] ath5k 0000:01:00.0: PCI INT A disabled
[ 1079.698679] ath5k: probe of 0000:01:00.0 failed with error -5

```

:~$ **lspci -nn | grep  Ath**
```
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
02:00.0 Ethernet controller [0200]: Atheros Communications L1 Gigabit Ethernet Adapter [1969:1048] (rev b0)
```


from another forum thread, again some infoes:

:~$ **lspci -nnk | grep -iA2 net**
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
	Kernel modules: ath5k
02:00.0 Ethernet controller [0200]: Atheros Communications L1 Gigabit Ethernet Adapter [1969:1048] (rev b0)
	Kernel driver in use: atl1
	Kernel modules: atl1
--
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Kernel driver in use: 8139too
	Kernel modules: 8139too, 8139cp

:~$ **iwconfig**
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

```

:~$ **lsmod | grep ath**
```
ath5k                 134405  0 
mac80211              238928  1 ath5k
ath                     9723  1 ath5k
cfg80211              148725  3 ath5k,mac80211,ath
led_class               3764  1 ath5k
```

---

### Post by anotherone33 on 2013-02-23
some more complete informations, again from 
Description:	Ubuntu 10.04.3 LTS
Release:	10.04
Codename:	lucid
point of view.


:~$ **more /etc/modprobe.d/blacklist.conf **
```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# modified mauro cumin 10 6 2010
blacklist floppy

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

```


:~$ **lsmod**
```
Module                  Size  Used by
ath5k                 134405  0 
binfmt_misc             7960  1 
snd_hda_codec_realtek   279072  1 
snd_hda_intel          25805  2 
snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
snd_mixer_oss          16299  1 snd_pcm_oss
vga16fb                12757  0 
vgastate                9857  1 vga16fb
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
mac80211              238928  1 ath5k
snd_seq_dummy           1782  0 
i915                  326140  4 
drm_kms_helper         30742  1 i915
ath                     9723  1 ath5k
snd_seq_oss            31191  0 
drm                   200384  5 i915,drm_kms_helper
snd_seq_midi            5829  0 
ppdev                   6375  0 
snd_rawmidi            23420  1 snd_seq_midi
parport_pc             29958  1 
lp                      9336  0 
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
parport                37160  3 ppdev,parport_pc,lp
i2c_algo_bit            6024  1 i915
snd_seq                57481  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
cfg80211              148725  3 ath5k,mac80211,ath
intel_agp              29319  2 i915
serio_raw               4918  0 
xhci                   42775  0 
led_class               3764  1 ath5k
joydev                 11104  0 
snd_timer              23681  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
video                  20623  1 i915
output                  2503  1 video
asus_atk0110           10033  0 
snd                    71283  17 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
hid_logitech            8820  0 
ff_memless              5109  1 hid_logitech
usbhid                 41116  1 hid_logitech
hid                    83888  2 hid_logitech,usbhid
8139too                22245  0 
8139cp                 19541  0 
atl1                   33145  0 
mii                     5237  3 8139too,8139cp,atl1

```

From wicd, preferences:
Advanced settings, wpa supplicant: wext

---

### Post by anotherone33 on 2013-02-23
Some more complete informations, again from 
Description:	Ubuntu 10.04.3 LTS
Release:	10.04
Codename:	lucid
point of view.

:~$ **sudo lspci -vvv**

```
01:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
	Subsystem: Device 1a3b:1034
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at fe8f0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
		Address: 00000000  Data: 0000
	Capabilities: [60] Express (v1) Legacy Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr- UncorrErr+ FatalErr- UnsuppReq+ AuxPwr- TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <64us
			ClockPM- Suprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; RCB 128 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
		Vector table: BAR=0 offset=00000000
		PBA: BAR=0 offset=00000000
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Kernel modules: ath5k

```

---

