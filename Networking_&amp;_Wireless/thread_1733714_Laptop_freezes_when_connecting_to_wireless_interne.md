---
title: "Laptop freezes when connecting to wireless internet"
date: 2011-04-19
forum: Networking &amp; Wireless
---

### Post by wildbill8989 on 2011-04-19
[FONT=Times New Roman][SIZE=3]Hi, [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]I’ve been having some serious problems connecting to Internet recently on ubuntu. It connects with no problems to all wireless networks, except the one at my home. If the PC is booted up without the Internet turned on it runs fine, however when it attempts to connect to my wireless network, the icon on the top tool bar begins to load, and after three or four seconds the computer completely freezes. I’ve read through all the threads and found no answer, short of buying new equipment, which I would rather avoid. As you have probably guess, I am not the most tech savvy person out there and any help you could give me in solving this issue would be greatly appreciated. [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Many thanks for your time.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Laptop – Acer Aspire 5532[/SIZE][/FONT]

[FONT=Times New Roman][SIZE=3]Ubuntu 10.10[/SIZE][/FONT]
 
 
[FONT=Times New Roman]Router- D-link Dir-635 [/FONT]


[FONT=Times New Roman]PS- It has managed previously to connect to the internet here, so on some level it must work, I just need to find out what I'm doing wrong[/FONT]

[FONT=Times New Roman]Again many thanks [/FONT]

---

### Post by josephmills on 2011-04-19
hi there could you show us a ```
lshw -C network
``` thanks

---

### Post by wildbill8989 on 2011-04-19
Warning: you should run this program as super-user
pci (sysfs)
*-network DISABLED
Descriptio: wireless interface
Products: AR928X Wireless Network Adapter (PCI-express)
Vendor: Atheros communications IC.
Physical id: 0
Bus infor: [EMAIL="pci@0000:02:00.0"]pci@0000:02:00.0[/EMAIL]
logical name: Wlan0
Versio: 01
Serial: 70:1a:04:b8:36:f3
Width: 64bits
clock33mhz
Capabilities: bus_master cap_list ethernet physical wireless
Configuration: broadcast=yes driver=ath9k driverversion=2. 6. 35-25-generic firmware=N/A latency = 0 multicast=yes wireless=IEEE 802. 11bgn
resources: irq: 16 memory: d1100000-d110ffff
 
I have had to turn the wireless adapter off, so as to not crash the computer, any help?

---

### Post by josephmills on 2011-04-19
could we please see a ```
dmesg | grep ath9k
``` thanks again

---

### Post by wildbill8989 on 2011-04-19
[       19. 109997] ath9k 0000: 02: 00.0: PCI INT A  -> GSI 16 (level, low) -> IRQ 16
[       19. 110010] ath9k 0000: 02: 00.0: setting latency timer to 64
[       20. 162782] phy0: selected rate control algorithm 'ath9k_rate_control'
[       20. 163663] registered led device: ath9k-phy0:: radio
[       20. 163690] registered led device: ath9k-phy0:: assoc
[       20. 163716] registered led device: ath9k-phy0:: tx
[       20. 163742] registered led device: ath9k-phy0:: rx
 
NB- All the ath9k are in orange. 
 
your a saint for this mate

---

### Post by josephmills on 2011-04-19
how about a ```
lsmod
``` Thanks again

---

### Post by wildbill8989 on 2011-04-19
[FONT=Times New Roman][SIZE=3]Module                  Size  Used by[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]aes_i586                7280  375 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]aes_generic            26875  1 aes_i586[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]binfmt_misc             6599  1 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]joydev                  8767  0 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]parport_pc             26058  0 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ppdev                   5556  0 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]dm_crypt               11385  0 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]arc4                    1165  2 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]snd_hda_codec_realtek   218492  1 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]snd_hda_intel          22203  2 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]snd_hwdep               5040  1 snd_hda_codec[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ath9k                  88756  0 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]snd_pcm                71475  2 snd_hda_intel,snd_hda_codec[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ath9k_common            5982  1 ath9k[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]snd_seq_midi            4588  0 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ath9k_hw              292297  2 ath9k,ath9k_common[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]snd_rawmidi            17783  1 snd_seq_midi[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ath                     8153  2 ath9k,ath9k_hw[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]snd_seq_midi_event      6047  1 snd_seq_midi[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]mac80211              231959  2 ath9k,ath9k_common[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]snd_seq                47174  3 snd_seq_midi,snd_seq_midi_event[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]snd_timer              19067  2 snd_pcm,snd_seq[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]cfg80211              144694  4 ath9k,ath9k_common,ath,mac80211[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]snd                    49038  14 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]psmouse                59033  0 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]shpchp                 29886  0 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]soundcore                880  1 snd[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]i2c_piix4               8635  0 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]led_class               2633  1 ath9k[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]snd_page_alloc          7120  2 snd_hda_intel,snd_pcm[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]k8temp                  3228  0 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]serio_raw               4022  0 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]lp                      7342  0 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]parport                31492  3 parport_pc,ppdev,lp[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]radeon                829447  3 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ttm                    56633  1 radeon[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]drm_kms_helper         30200  1 radeon[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]drm                   168092  5 radeon,ttm,drm_kms_helper[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ahci                   19198  2 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]atl1c                  29949  0 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]libahci                21728  1 ahci[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]agpgart                32011  2 ttm,drm[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]i2c_algo_bit            5168  1 radeon[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]video                  18712  0 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]output                  1883  1 video[/SIZE][/FONT]

---

### Post by josephmills on 2011-04-19
this is just a thought but I see alot of drivers there ```

ath9k 88756 0
ath9k_common 5982 1 ath9k
ath9k_hw 292297 2 ath9k,ath9k_common
ath 8153 2 ath9k,ath9k_hw
mac80211 231959 2 ath9k,ath9k_common
cfg80211 144694 4 ath9k,ath9k_common,ath,mac80211
led_class 2633 1 ath9k
```
Iwould say get rid of ```
ath9k_common 5982 1 ath9k
ath9k_hw 292297 2 ath9k,ath9k_common
```


before removing them if you have a Ethernet cable then go for it. but if you are just using wireless, then maybe wait for someone with more experience then me. but I would get rid of them. 


to delete them do ```
rm ath9k_common 5982 1 ath9k
```then
```
rm ath9k_hw 292297 2 ath9k,ath9k_common
```then do a reboot and see if it happens still. let us know

---

