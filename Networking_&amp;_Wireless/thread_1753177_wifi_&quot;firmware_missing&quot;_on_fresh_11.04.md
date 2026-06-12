---
title: "wifi &quot;firmware missing&quot; on fresh 11.04"
date: 2011-05-08
forum: Networking &amp; Wireless
---

### Post by wlraider70 on 2011-05-08
I just did a fresh install on an old laptop it says that my built in wifi card is "missing firmware" though it is detected. 

I'm using a usb wifi card that's working as a temp
I think my card is a boradcom, but im not sure how to find out.


thanks.

---

### Post by wlraider70 on 2011-05-09
apparently mu post was not detected either.
I will use this usb *bump* as a temp. substitute.

---

### Post by josephmills on 2011-05-09
ok first lets see what kind of card you have ```
lspci -nn 
``` if it is a usb wifi lets see ```
lsusb
``` lets make sure that nothing is being bocked also ```
rfkill list 
``` lets also see what mods/drivers are loaded ```
lsmod
``` once we figure out what kind of card it is we will see about the firmware. **edit bump **
joseph

---

### Post by wlraider70 on 2011-05-10
lspci

```

luke@sempron:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 01)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374]
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375]
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373]
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 11)
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376]
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377]
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371]
00:14.5 Multimedia audio controller [0401]: ATI Technologies Inc IXP SB400 AC'97 Audio Controller [1002:4370] (rev 02)
00:14.6 Modem [0703]: ATI Technologies Inc SB400 AC'97 Modem Controller [1002:4378] (rev 02)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE) [1002:5955]
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
05:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
05:09.0 CardBus bridge [0607]: Texas Instruments PCIxx21/x515 Cardbus Controller [104c:8031]
luke@sempron:~$


```

rfkill list

```

luke@sempron:~$ rfkill list
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: phy2: Wireless LAN
	Soft blocked: no
	Hard blocked: no


```

ldmod

```

luke@sempron:~$ lsmod
Module                  Size  Used by
snd_atiixp_modem       18624  5 
snd_via82xx_modem      18305  0 
snd_intel8x0m          18493  0 
cryptd                 19801  0 
aes_i586               16956  1 
aes_generic            38023  1 aes_i586
parport_pc             32111  0 
ppdev                  12849  0 
radeon                896428  3 
binfmt_misc            13213  1 
arc4                   12473  4 
snd_atiixp             19400  2 
b43                   296610  0 
rtl8187                56206  0 
snd_seq_midi           13132  0 
mac80211              257001  2 b43,rtl8187
snd_rawmidi            25269  1 snd_seq_midi
ttm                    65184  1 radeon
joydev                 17322  0 
snd_seq_midi_event     14475  1 snd_seq_midi
hp_wmi                 13418  0 
drm_kms_helper         40745  1 radeon
sparse_keymap          13666  1 hp_wmi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_ac97_codec        105614  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_atiixp
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  7 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_atiixp,snd_ac97_codec
pcmcia                 39671  0 
snd_timer              28659  2 snd_pcm,snd_seq
drm                   180037  5 radeon,ttm,drm_kms_helper
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              156212  3 rtl8187,b43,mac80211
yenta_socket           27230  0 
psmouse                73312  0 
snd                    55295  22 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_atiixp,snd_rawmidi,snd_ac97_codec,snd_pcm,snd_seq,snd_timer,snd_seq_device
pcmcia_rsrc            18292  1 yenta_socket
eeprom_93cx6           12653  1 rtl8187
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
k8temp                 12872  0 
serio_raw              12990  0 
soundcore              12600  1 snd
i2c_algo_bit           13184  1 radeon
video                  18951  0 
snd_page_alloc         14073  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_atiixp,snd_pcm
i2c_piix4              13095  0 
ati_agp                13202  0 
shpchp                 32345  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
8139too                23208  0 
8139cp                 22497  0 
ssb                    45942  1 b43
pata_atiixp            12968  2 
luke@sempron:~$ 


```

---

### Post by josephmills on 2011-05-10
please see post number 44 thanks [http://ubuntuforums.org/showthread.php?t=1748245&page=5](http://ubuntuforums.org/showthread.php?t=1748245&page=5)
hope that this helps

---

### Post by wlraider70 on 2011-05-10
thanks friends, it works great.

---

### Post by josephmills on 2011-05-10
glad you got it working  happy wireless

---

