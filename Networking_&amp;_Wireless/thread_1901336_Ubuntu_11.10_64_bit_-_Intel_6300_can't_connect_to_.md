---
title: "Ubuntu 11.10 64 bit - Intel 6300 can't connect to WPA"
date: 2011-12-28
forum: Networking &amp; Wireless
---

### Post by Gelupah on 2011-12-28
Hi,

I have issues with my laptop connecting to some WPA networks. More precisely, it connects to TKIP but not AES (either that or the opposite, need to check when I can). It  works flawlessly with WEP and the other type of WPA. Strangely,I had the same problem with the previous Realtek card I had in the laptop, and thought that was the issue... 

(filtered outputs)

1
Laptop: Clevo 3101 Slim
3.0.0-14-generic x86_64
Wireless AP works fine,I have another laptop connected to it with a USB wifi Atheros Dongle.

2
lspci:
```
03:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 2c)
```

3
ifconfig
```
wlan1     Link encap:Ethernet  HWaddr 00:15:00:xx:xx:xx  
          inet6 addr: fe80::215:ff:fexx:xxxx/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:78 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8814 (8.8 KB)  TX bytes:12090 (12.0 KB)
```

iwconfig
```
wlan1     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```


4
lsmod
```
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61475  1 vfat
usb_storage            57901  1 
uas                    18027  0 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282548  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             36962  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
joydev                 17693  0 
binfmt_misc            17540  1 
arc4                   12529  2 
snd_hda_intel          33390  4 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
iwlagn                314213  0 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  566827  8 
mac80211              462092  1 iwlagn
drm_kms_helper         42558  1 i915
snd                    68266  17 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73882  0 
drm                   236290  4 i915,drm_kms_helper
serio_raw              13166  0 
intel_ips              18089  0 
cfg80211              199587  2 iwlagn,mac80211
i2c_algo_bit           13423  1 i915
wmi                    19256  0 
jmb38x_ms              17646  0 
memstick               16569  1 jmb38x_ms
mei                    41480  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
jme                    41301  0 
ahci                   26002  3 
libahci                26861  1 ahci

```

5
dmesg
```
 861.522307] wlan1: authenticate with 38:22:9d:f9:a6:5c (try 1)
[  861.720796] wlan1: authenticate with 38:22:9d:f9:a6:5c (try 2)
[  861.723233] wlan1: authenticated
[  861.723793] wlan1: associate with 38:22:9d:f9:a6:5c (try 1)
[  861.726428] wlan1: RX ReassocResp from 38:22:9d:f9:a6:5c (capab=0x11 status=0 aid=2)
[  861.726437] wlan1: associated
[  861.732795] cfg80211: Calling CRDA for country: IT
[  861.741203] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  861.741215] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  861.741223] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  861.741231] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  861.741238] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  861.741246] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  861.741252] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  861.741260] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  861.741266] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  861.741274] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  861.741281] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  861.741289] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  861.741295] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  861.741303] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  861.741309] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  861.741317] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  861.741323] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  861.741332] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  861.741338] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  861.741346] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  861.741352] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  861.741360] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  861.741366] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  861.741374] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  861.741381] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  861.741389] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  861.741395] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[  861.741403] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  861.741409] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[  861.741418] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  861.741424] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[  861.741432] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  861.741438] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[  861.741446] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  861.741452] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule:
[  861.741461] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  861.741467] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule:
[  861.741475] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  861.741481] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule:
[  861.741489] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  861.741495] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule:
[  861.741503] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  861.741510] cfg80211: Updating information on frequency 5500 MHz for a 20 MHz width channel with regulatory rule:
[  861.741518] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
[  861.741524] cfg80211: Updating information on frequency 5520 MHz for a 20 MHz width channel with regulatory rule:
[  861.741532] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
[  861.741539] cfg80211: Updating information on frequency 5540 MHz for a 20 MHz width channel with regulatory rule:
[  861.741547] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
[  861.741553] cfg80211: Updating information on frequency 5560 MHz for a 20 MHz width channel with regulatory rule:
[  861.741561] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
[  861.741567] cfg80211: Updating information on frequency 5580 MHz for a 20 MHz width channel with regulatory rule:
[  861.741575] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
[  861.741581] cfg80211: Updating information on frequency 5600 MHz for a 20 MHz width channel with regulatory rule:
[  861.741590] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
[  861.741596] cfg80211: Updating information on frequency 5620 MHz for a 20 MHz width channel with regulatory rule:
[  861.741604] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
[  861.741610] cfg80211: Updating information on frequency 5640 MHz for a 20 MHz width channel with regulatory rule:
[  861.741618] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
[  861.741624] cfg80211: Updating information on frequency 5660 MHz for a 20 MHz width channel with regulatory rule:
[  861.741632] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
[  861.741639] cfg80211: Updating information on frequency 5680 MHz for a 20 MHz width channel with regulatory rule:
[  861.741647] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
[  861.741653] cfg80211: Updating information on frequency 5700 MHz for a 20 MHz width channel with regulatory rule:
[  861.741661] cfg80211: 5490000 KHz - 5710000 KHz @  KHz), (N/A mBi, 2700 mBm)
[  861.741667] cfg80211: Disabling freq 5745 MHz
[  861.741671] cfg80211: Disabling freq 5765 MHz
[  861.741676] cfg80211: Disabling freq 5785 MHz
[  861.741680] cfg80211: Disabling freq 5805 MHz
[  861.741685] cfg80211: Disabling freq 5825 MHz
[  861.741697] cfg80211: Regulatory domain changed to country: IT
[  861.741702] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  861.741709] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  861.741716] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  861.741723] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  861.741730] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[  870.046111] wlan1: deauthenticated from 38:22:9d:f9:a6:5c (Reason: 1)
[  870.053549] cfg80211: All devices are disconnected, going to restore regulatory settings
[  870.053564] cfg80211: Restoring regulatory settings
[  870.053575] cfg80211: Calling CRDA to update world regulatory domain
[  870.064858] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[  870.064870] cfg80211: World regulatory domain updated:
[  870.064875] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  870.064884] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  870.064892] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  870.064900] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  870.064908] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  870.064915] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
```

6
sudo lshw -C network
```
*-network               
       description: Wireless interface
       product: Centrino Ultimate-N 6300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan1
       version: 2c
       serial: 00:15:00:xx:xx:xx
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-14-generic firmware=9.221.4.1 build 25532 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:41 memory:f0500000-f0501fff
```


Any ideas how to fix this?

Many thanks,

Tony

---

### Post by Gelupah on 2011-12-29
I've tried installing wicd, and removing network manager. When I try connecting using wicd it returns a "bad password" messages; I am sure my WPA code is correct though, I triple checked it...

What could be causing this?

Thanks

---

### Post by lz1dsb on 2012-01-06
I'm not sure I'm experiencing this too. I have installed 11.10 recently on my Dell 1555 and from time to time while I'm connected to my wireless router (using WPA encryption) I get an error message saying that my password is wrong even though I have been connected for hours before that... Is it the same problem? Are you able to connect at all to a WPA wireless network?
My laptop uses the BCM4312 wireless controller chip... But I'm not quite sure still if this is really related to the driver.

---

### Post by Gelupah on 2012-01-27
Well, apologies for not looking throught he forum thoroughly enough apparently. The following post worked a treat for me:

[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

Downside is that I can't use VPN, since by configuring the settings manually I disable network manager. Let's hope this issue with network manager is fixed soon...

---

