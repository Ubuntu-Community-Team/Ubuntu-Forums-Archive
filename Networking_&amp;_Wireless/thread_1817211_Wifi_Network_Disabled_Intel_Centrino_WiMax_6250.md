---
title: "Wifi Network Disabled Intel Centrino WiMax 6250"
date: 2011-08-03
forum: Networking &amp; Wireless
---

### Post by audio1 on 2011-08-03
I am running a dual boot Windows 7 / Ubuntu 11.04 on a Lenovo V560 laptop. I tried to load 10.04 and spent hours trying to get the wifi to work. I have loaded 11.04 and this seems to like my system better as touchpad works, but network seems disabled.

I can see the softblocks are on and have tried rfkill unblock all but this doesn't remove the softblocks. I would love it if someone could help me.

Here is some information on my system:

matthew@matthew-Lenovo-V560:~$ lspci -nn | grep 0280
04:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N + WiMAX 6250 [8086:0089] (rev 5f)
matthew@matthew-Lenovo-V560:~$ lsmod
Module                  Size  Used by
sha256_generic         20911  2 
cryptd                 19801  0 
aes_i586               16956  150 
aes_generic            38023  1 aes_i586
parport_pc             32111  0 
ppdev                  12849  0 
dm_crypt               22463  1 
binfmt_misc            13213  1 
joydev                 17322  0 
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  2 
arc4                   12473  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
i2400m_usb             35677  0 
i2400m                101216  1 i2400m_usb
iwlagn                284569  0 
snd_seq_midi_event     14475  1 snd_seq_midi
acer_wmi               23123  0 
wimax                  33488  1 i2400m
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               66851  0 
iwlcore               148965  1 iwlagn
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              257001  2 iwlagn,iwlcore
videodev               75143  1 uvcvideo
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              156212  3 iwlagn,iwlcore,mac80211
psmouse                73312  0 
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
intel_ips              17769  0 
ideapad_laptop         13262  0 
sparse_keymap          13666  2 acer_wmi,ideapad_laptop
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
i915                  450944  8 
atl1c                  36237  0 
drm_kms_helper         40745  1 i915
ahci                   21591  2 
drm                   180037  4 i915,drm_kms_helper
libahci                25548  1 ahci
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
matthew@matthew-Lenovo-V560:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
wmx0      no wireless extensions.

matthew@matthew-Lenovo-V560:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
3: i2400m-usb:2-1.4:1.0: WiMAX
	Soft blocked: yes
	Hard blocked: no
matthew@matthew-Lenovo-V560:~$

---

### Post by josephmills on 2011-08-03
> **audio1 said:**
> I am running a dual boot Windows 7 / Ubuntu 11.04 on a Lenovo V560 laptop. I tried to load 10.04 and spent hours trying to get the wifi to work. I have loaded 11.04 and this seems to like my system better as touchpad works, but network seems disabled.

I can see the softblocks are on and have tried rfkill unblock all but this doesn't remove the softblocks. I would love it if someone could help me.

Here is some information on my system:

matthew@matthew-Lenovo-V560:~$ lspci -nn | grep 0280
04:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N + WiMAX 6250 [8086:0089] (rev 5f)
matthew@matthew-Lenovo-V560:~$ lsmod
Module                  Size  Used by
sha256_generic         20911  2 
cryptd                 19801  0 
aes_i586               16956  150 
aes_generic            38023  1 aes_i586
parport_pc             32111  0 
ppdev                  12849  0 
dm_crypt               22463  1 
binfmt_misc            13213  1 
joydev                 17322  0 
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  2 
arc4                   12473  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
[COLOR="red"]i2400m_usb             35677  0 
i2400m                101216  1 i2400m_usb
iwlagn                284569  0 [/COLOR]
snd_seq_midi_event     14475  1 snd_seq_midi
[COLOR="Red"]acer_wmi               23123  0 [/COLOR]
wimax                  33488  1 i2400m
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               66851  0 
[COLOR="red"]iwlcore               148965  1 iwlagn[/COLOR]
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
[COLOR="red"]mac80211              257001  2 iwlagn,iwlcore[/COLOR]
videodev               75143  1 uvcvideo
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
[COLOR="red"]cfg80211              156212  3 iwlagn,iwlcore,mac80211[/COLOR]
psmouse                73312  0 
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
intel_ips              17769  0 
ideapad_laptop         13262  0 
sparse_keymap          13666  2 acer_wmi,ideapad_laptop
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
i915                  450944  8 
atl1c                  36237  0 
drm_kms_helper         40745  1 i915
ahci                   21591  2 
drm                   180037  4 i915,drm_kms_helper
libahci                25548  1 ahci
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
matthew@matthew-Lenovo-V560:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
wmx0      no wireless extensions.

matthew@matthew-Lenovo-V560:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
	[COLOR="red"]Soft blocked: yes[/COLOR]
	Hard blocked: no
1: acer-wireless: Wireless LAN
	[COLOR="red"]Soft blocked: yes[/COLOR]
	Hard blocked: no
2: phy0: Wireless LAN
	[COLOR="red"]Soft blocked: yes
	Hard blocked: yes[/COLOR]
3: i2400m-usb:2-1.4:1.0: WiMAX
	[COLOR="red"]Soft blocked: yes[/COLOR]
	Hard blocked: no
matthew@matthew-Lenovo-V560:~$


Hi there there are a couple things that I see wrong first there are two driver are there two wireless cards? could we please see a ```
lspci -nn
``` next I see that the  hard block is YES this is caused by the external wifi switch being turned off. next if you have tried rfkill unblock all wifi wlan0 and what not then it is usually cause by the wmi switch which is the mod that controls the switch for the wifi. so try and blacklist that. but I think that having two drivers installed is not a good thing. But I could be wrong I am all the time

---

### Post by audio1 on 2011-08-04
Thankyou very much for your reply. Here is what you requested. I also managed to remove the hardblock from the phy0. I did this by going back into windows 7 and turning wifi on then toggling switch.

I do not know how to remove the drivers or do the mod switch thing I am totally new to linux and Ubuntu and would need somebody to show me how.

All help appreciated.

Thankyou.



matthew@matthew-Lenovo-V560:~$ rfkill list
0: ideapad_wlan: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
3: i2400m-usb:2-1.4:1.0: WiMAX
	Soft blocked: yes
	Hard blocked: no
matthew@matthew-Lenovo-V560:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05)
00:1c.3 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 [8086:3b48] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 05)
03:00.0 Ethernet controller [0200]: Atheros Communications AR8131 Gigabit Ethernet [1969:1063] (rev c0)
04:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N + WiMAX 6250 [8086:0089] (rev 5f)
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)

---

### Post by bkratz on 2011-08-04
See posts 2 and 4 of this thread

[http://ubuntuforums.org/showthread.php?t=1790646&highlight=acer-wmi](http://ubuntuforums.org/showthread.php?t=1790646&highlight=acer-wmi)

---

### Post by audio1 on 2011-08-05
Thankyou to everyone involved who replied. The problem is solved, even on restart. I have just been surfing the web on my new beautiful and now connected Lenovo with Ubuntu 11.04.

The solution was to blacklist the acer-wmi module.

---

### Post by big_mick on 2011-11-15
Blacklisting the acer-wmi module also fixed my wireless issue on my Lenovo V560.  This after 8 hours over 3 days of searching and trying multiple things.  The first thing I wanted to do with my connection was post a very heartfelt thank you to those who monitor and reply on these forums.  Even the threads that didn't address my problem were informative and very helpful.

---

