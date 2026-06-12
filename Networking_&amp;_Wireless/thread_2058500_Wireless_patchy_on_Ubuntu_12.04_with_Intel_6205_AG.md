---
title: "Wireless patchy on Ubuntu 12.04 with Intel 6205 AGN, fine on Windows"
date: 2012-09-15
forum: Networking &amp; Wireless
---

### Post by rainspeaker on 2012-09-15
Hi, 
I got a new Thinkpad X230 about a month and a half ago. I dual-boot ubuntu 12.04 and Windows 7. On the Windows installation, wireless works great, but on the linux side, it's almost unusable. NetworkManager is able to detect the networks, and says that they're at quite a high strength, but when I try to connect, it takes a long time. When the connection finally does work, it works at a decent speed, but after just a few minutes it almost invariably stops working. Chrome usually then tells me not that I am disconnected from the internet, but that it was unable to resolve the DNS request. The other strange thing is that the networkmanager icon, when I am connected (i.e. when I can access websites) generally displays the 'connecting' icon, although once in a very long while it displays a 'connected' icon. And it usually doesn't display the 'disconnected' icon after my access stops working. So while my internet is vaguely usable for browsing wikipedia or forum pages, streaming and video chatting are a no go. 

I'm using an Intel Advanced-N 6205 adapter, built-in. 

I'm not sure what information will be needed, so I'll include some that I've seen asked for/posted on other forum posts. 

From iwconfig:
```
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on

```

```
robbie@thursday:~$ lspci -nnk |grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
	Subsystem: Lenovo Device [17aa:21f3]
	Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [8086:0085] (rev 34)
	Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN [8086:1311]
	Kernel driver in use: iwlwifi

```

```
robbie@thursday:~$ lsmod
Module                  Size  Used by
bnep                   18190  2 
parport_pc             32734  0 
rfcomm                 47012  0 
bluetooth             206685  10 bnep,rfcomm
ppdev                  17180  0 
snd_hda_codec_hdmi     32111  1 
binfmt_misc            17498  1 
snd_hda_codec_realtek    77948  1 
snd_hda_intel          33332  3 
snd_hda_codec         123847  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
uvcvideo               72690  0 
snd_hwdep              13652  1 snd_hda_codec
videobuf2_core         32801  1 uvcvideo
snd_pcm                97231  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
videodev              111615  1 uvcvideo
thinkpad_acpi          81197  0 
i915                  484383  3 
videobuf2_vmalloc      12860  1 uvcvideo
videobuf2_memops       13368  1 videobuf2_vmalloc
hid_logitech_dj        18432  0 
snd_seq_midi           13324  0 
snd_rawmidi            30655  1 snd_seq_midi
arc4                   12529  2 
joydev                 17597  0 
snd_seq_midi_event     14899  1 snd_seq_midi
drm_kms_helper         46958  1 i915
drm                   265069  4 i915,drm_kms_helper
iwlwifi               411182  0 
snd_seq                61538  2 snd_seq_midi,snd_seq_midi_event
coretemp               13602  0 
ghash_clmulni_intel    13180  0 
mac_hid                13205  0 
mei                    40904  0 
i2c_algo_bit           13509  1 i915
snd_timer              29708  2 snd_pcm,snd_seq
snd_seq_device         14490  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              519398  1 iwlwifi
aesni_intel            51530  0 
cfg80211              202006  2 iwlwifi,mac80211
snd                    79086  17 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cryptd                 20396  2 ghash_clmulni_intel,aesni_intel
snd_page_alloc         18572  2 snd_hda_intel,snd_pcm
aes_x86_64             17208  1 aesni_intel
psmouse                87589  0 
serio_raw              13211  0 
video                  19280  1 i915
soundcore              14996  1 snd
tpm_tis                18678  0 
nvram                  14363  1 thinkpad_acpi
microcode              22945  0 
wmi                    19141  0 
lp                     17789  0 
parport                46360  3 parport_pc,ppdev,lp
usbhid                 46836  1 hid_logitech_dj
hid                    99833  2 hid_logitech_dj,usbhid
sdhci_pci              18680  0 
sdhci                  32460  1 sdhci_pci
e1000e                162863  0 

```
```

robbie@thursday:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 3c:97:0e:19:3a:79  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f2500000-f2520000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4702 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4702 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:423009 (423.0 KB)  TX bytes:423009 (423.0 KB)

wlan0     Link encap:Ethernet  HWaddr 8c:70:5a:f5:6f:2c  
          inet addr:10.251.149.55  Bcast:10.251.159.255  Mask:255.255.240.0
          inet6 addr: fe80::8e70:5aff:fef5:6f2c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13846 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10298 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5956490 (5.9 MB)  TX bytes:2147901 (2.1 MB)

```

I would seriously appreciate any help you guys can give me. 
Thanks, Robbie

---

### Post by steeldriver on 2012-09-15
Hi, the usual problem with these intel cards is that they don't play well with wireless N mode - you can see if that's the issue by temporarily disabling it

```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```

If that helps, you can make it persistent by creating a module conf file as described here

[http://ubuntuforums.org/showpost.php?p=11970349&postcount=5](http://ubuntuforums.org/showpost.php?p=11970349&postcount=5)

---

### Post by rainspeaker on 2012-09-16
I tried what you suggested, but as soon as I entered the first of the two commands you suggested, my kernel panicked and I had to hard-reboot the computer. I've actually tried to fix the problem using this method before, and it always panics.

EDIT: I guess I should have mentioned this before.

---

### Post by varunendra on 2012-09-16
> **rainspeaker said:**
> 
From iwconfig:
```
....
wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          **Power Management:[COLOR=Red]on[/COLOR]**

```
Your description of the problem seems to me more related with what I highlighted above (but I am no expert..!). Please try:
```
sudo iwconfig power off
```
It'll turn off the power management which tries to save power on the adapter when it 'thinks' it is idle.

Only if it does not help:
you can try another parameter to the iwlwifi driver that looks interesting - "fw_restart"(: restart firmware in case of error):
```
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi fw_restart=1
```

Even more, you can also try both parameters at once:
```
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi fw_restart=1 11n_disable=1
```

Try these three blind shots from a non-expert, and do tell us if any of these work for you.

---

