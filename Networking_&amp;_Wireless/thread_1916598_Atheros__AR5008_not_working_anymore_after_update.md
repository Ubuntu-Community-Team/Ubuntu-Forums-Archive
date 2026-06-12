---
title: "Atheros  AR5008 not working anymore after update"
date: 2012-01-28
forum: Networking &amp; Wireless
---

### Post by lucipacurar on 2012-01-28
Hi guys,

I've installed Ubuntu 11.10 and then updated the system using update manager. After restarting my wireless pci card won't connect to my WLAN anymore.

Here's my card:
```
04:02.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
```

and here's some dmesg output:
```

[   73.872559] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   73.872561] cfg80211: Disabling freq 2484 MHz
[   73.872563] cfg80211: World regulatory domain updated:
[   73.872564] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   73.872566] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   73.872568] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   73.872570] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   73.872572] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   73.872574] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   74.733788] wlan0: authenticate with f0:7d:68:9c:20:ec (try 1)
[   74.735786] wlan0: authenticated
[   74.739597] wlan0: associate with f0:7d:68:9c:20:ec (try 1)
[   74.743546] wlan0: RX ReassocResp from f0:7d:68:9c:20:ec (capab=0xc31 status=0 aid=1)
[   74.743550] wlan0: associated
[   74.746268] cfg80211: Calling CRDA for country: GB
[   74.749802] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   74.749806] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   74.749809] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   74.749812] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   74.749815] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   74.749818] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   74.749820] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   74.749823] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   74.749826] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   74.749829] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   74.749831] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   74.749834] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   74.749837] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   74.749840] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   74.749842] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   74.749845] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   74.749848] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   74.749851] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   74.749853] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   74.749857] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   74.749859] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   74.749862] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   74.749865] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   74.749868] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   74.749870] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   74.749873] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   74.749876] cfg80211: Disabling freq 2484 MHz
[   74.749879] cfg80211: Regulatory domain changed to country: GB
[   74.749881] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   74.749884] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   74.749887] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   74.749889] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   74.749892] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[   76.004604] wlan0: deauthenticating from f0:7d:68:9c:20:ec by local choice (reason=3)
[   76.021972] cfg80211: All devices are disconnected, going to restore regulatory settings
[   76.021977] cfg80211: Restoring regulatory settings
[   76.021994] cfg80211: Calling CRDA to update world regulatory domain
[   76.025497] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   76.025501] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   76.025504] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   76.025507] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   76.025510] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   76.025513] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   76.025516] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   76.025519] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   76.025521] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   76.025524] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   76.025527] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   76.025530] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   76.025533] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   76.025536] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   76.025538] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   76.025541] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   76.025544] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   76.025547] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   76.025549] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   76.025552] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   76.025555] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   76.025558] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   76.025561] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   76.025564] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   76.025566] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   76.025569] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   76.025571] cfg80211: Disabling freq 2484 MHz
[   76.025574] cfg80211: World regulatory domain updated:
[   76.025577] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   76.025580] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   76.025583] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   76.025586] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   76.025589] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   76.025592] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
```

Does anybody have an idea on how to get it working again? The card works like a charm in OS X 10.7.2, and Win 7.

Thanks!

---

### Post by lucipacurar on 2012-01-31
It seems it works from time to time. But it's dead slow when it does work.

---

### Post by varunendra on 2012-02-01
As a very quick shot (that may or may not work), please try:
```
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k nohwcrypt=1
```

Just copy-paste the commands to avoid typing mistake. Do not restart after issuing these commands, just wait till the wireless becomes active again, then retry to connect.

---

### Post by lucipacurar on 2012-03-10
The driver for my card is ath9k. I've tried those commands in the terminal but the card still won't connect.

---

### Post by varunendra on 2012-03-11
> **lucipacurar said:**
> The driver for my card is ath9k..
Should have been ath5k. Please post the outputs of:
```
lspci -nnk | grep -iA2 net
lsmod
```

If the first one shows ath9k in use, then also try:
```
sudo modprobe -rfv ath9k
sudo modprobe -v ath5k
```
then try to connect and post back the results (along with outputs I asked above).

---

### Post by manvvip on 2012-03-13
Ath9k is the correct driver for the Atheros AR5008 

[http://linuxwireless.org/en/users/Drivers/ath9k](http://linuxwireless.org/en/users/Drivers/ath9k)

The following comments are not suitable for the Atheros AR5008 and are off topic.

---

### Post by Naturally-Simple on 2012-03-21
I had a problem in the past with earlier Ubuntu releases and my ath5k driver, which was solved by following the expert advice of people on this thread:  [http://ubuntuforums.org/showthread.php?t=1776004](http://ubuntuforums.org/showthread.php?t=1776004)

However, the problem has arisen again after updating just yesterday or two days ago. I tried what you suggested, varunendra, and here is my outputs from those commands:

```
kevin@deep-thought:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
        Subsystem: Hewlett-Packard Company Device [103c:360b]
        Kernel driver in use: r8169
--
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
        Subsystem: Hewlett-Packard Company AR5BXB63 (Foxconn) 802.11bg Mini PCIe NIC [103c:137a]
        Kernel driver in use: ath5k

```Then with lsmod (which I couldn't see all of in my terminal, but this is the last part):
```

binfmt_misc            17292  1 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_conexant    52460  1 
joydev                 17393  0 
snd_hda_intel          24262  4 
snd_hda_codec          91859  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
sparse_keymap          13658  1 hp_wmi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
arc4                   12473  2 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  17 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  509519  3 
drm_kms_helper         32889  1 i915
psmouse                73673  0 
serio_raw              12990  0 
soundcore              12600  1 snd
drm                   192194  4 i915,drm_kms_helper
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
wmi                    18744  1 hp_wmi
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ums_realtek            13096  0 
usb_storage            44173  1 ums_realtek
uas                    17699  0 
ahci                   21634  3 
libahci                25727  1 ahci
r8169                  43104  0

```I also did the other commands: 
sudo modprobe -rfv ath5k sudo modprobe -v ath5k nohwcrypt=1
but they did not work to activate my wireless.

This is now what I get with rfkill list all, and the physical toggle switch does nothing, nor does it work to type "rfkill unblock all"

```

kevin@deep-thought:~$ rfkill list all
2: hp-wifi: Wireless LAN
        Soft blocked: yes
        Hard blocked: yes
3: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

```Also, for your consideration, here's iwconfig and ifconfig outputs:

```

kevin@deep-thought:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
kevin@deep-thought:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:16:d6:21:06  
          inet addr:192.168.1.143  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:16ff:fed6:2106/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27384 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25673 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32009822 (32.0 MB)  TX bytes:3291466 (3.2 MB)
          Interrupt:42 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19776 (19.7 KB)  TX bytes:19776 (19.7 KB)

```So like I wrote above, my wireless was working after I initially upgraded to 11.10 by following the steps from the previous thread I posted above, but then just in the last few days, the wireless stopped working again.

Any help is much appreciated.
Thanks!

---

### Post by wildmanne39 on 2012-03-21
Hi Kevin-dell1100, you have a soft and a hard block, please try:
```
sudo rmmod -f hp_wmi
```
also you may have to toggle your physical switch for the hard block.
Thanks

---

### Post by Naturally-Simple on 2012-03-21
Thanks for the suggestion. I tried it, but all that did was remove my other listing on the rfkill list. So now I get this:

```

kevin@deep-thought:~$ sudo rmmod -f hp_wmi
[sudo] password for kevin: 
kevin@deep-thought:~$ rfkill list all
3: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes
kevin@deep-thought:~$ rfkill list all
3: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes

```

and when I toggle my physical switch, nothing changes like it once did, way back when I first encountered this problem.

Any other ideas?

---

### Post by wildmanne39 on 2012-03-21
Hi, please post the output of:
```
cat /var/lib/NetworkManager/NetworkManager.state
dmesg | egrep 'ath|firm|radio|switch|wlan0|etwork'
```
can you post all of ```
lsmod
```it is not showing the driver.
Thanks

---

### Post by Naturally-Simple on 2012-03-21
Ok, here is that first and second code:

```

kevin@deep-thought:~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
kevin@deep-thought:~$ dmesg | egrep 'ath|firm|radio|switch|wlan0|etwork'
[   16.551726] type=1400 audit(1332364285.043:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=513 comm="apparmor_parser"
[   16.565010] ath5k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.565025] ath5k 0000:02:00.0: setting latency timer to 64
[   16.565080] ath5k 0000:02:00.0: registered as 'phy0'
[   17.073778] ath: EEPROM regdomain: 0x64
[   17.073780] ath: EEPROM indicates we should expect a direct regpair map
[   17.073784] ath: Country alpha2 being used: 00
[   17.073786] ath: Regpair used: 0x64
[   17.115786] Registered led device: ath5k-phy0::rx
[   17.115840] Registered led device: ath5k-phy0::tx
[   17.115852] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   17.952657] Console: switching to colour frame buffer device 170x48
[   21.612103] type=1400 audit(1332364290.107:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=860 comm="apparmor_parser"
[   21.642873] type=1400 audit(1332364290.135:13): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=878 comm="apparmor_parser"
[ 4969.185848] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6735.748331] ath5k 0000:02:00.0: PCI INT A disabled
[ 6798.016993] ath5k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 6798.017012] ath5k 0000:02:00.0: setting latency timer to 64
[ 6798.017068] ath5k 0000:02:00.0: registered as 'phy0'
[ 6798.518056] ath: EEPROM regdomain: 0x64
[ 6798.518061] ath: EEPROM indicates we should expect a direct regpair map
[ 6798.518066] ath: Country alpha2 being used: 00
[ 6798.518069] ath: Regpair used: 0x64
[ 6798.526842] Registered led device: ath5k-phy0::rx
[ 6798.526907] Registered led device: ath5k-phy0::tx
[ 6798.526923] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[13723.576081] ADDRCONF(NETDEV_UP): wlan0: link is not ready
kevin@deep-thought:~$ 

```

...and here is lsmod:

```

kevin@deep-thought:~$ lsmod
Module                  Size  Used by
ath5k                 145100  0
ath                    19387  1 ath5k
mac80211              393421  1 ath5k
cfg80211              172427  3 ath5k,ath,mac80211
bnep                   17923  2
rfcomm                 38408  0
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0
ppdev                  12849  0
binfmt_misc            17292  1
snd_hda_codec_hdmi     31426  1
snd_hda_codec_conexant    52460  1
joydev                 17393  0
snd_hda_intel          24262  6
snd_hda_codec          91859  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0
snd_rawmidi            25241  1 snd_seq_midi
sparse_keymap          13658  0
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               67271  0
videodev               85626  1 uvcvideo
arc4                   12473  2
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  21 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  509519  3
drm_kms_helper         32889  1 i915
psmouse                73673  0
serio_raw              12990  0
soundcore              12600  1 snd
drm                   192194  4 i915,drm_kms_helper
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
wmi                    18744  0
lp                     17455  0
parport                40930  3 parport_pc,ppdev,lp
ums_realtek            13096  0
usb_storage            44173  1 ums_realtek
uas                    17699  0
ahci                   21634  3
libahci                25727  1 ahci
r8169                  43104  0

```

does this help you in diagnosing my problem?

---

### Post by wildmanne39 on 2012-03-21
Hi, please try:
```
sudo ifconfig wlan0 down
sudo rfkill unblock all
sudo ifconfig wlan0 up
```
Thanks

---

### Post by Naturally-Simple on 2012-03-21
ok, here's those outputs:
```

kevin@deep-thought:~$ sudo ifconfig wlan0 down
[sudo] password for kevin: 
kevin@deep-thought:~$ sudo rfkill unblock all
kevin@deep-thought:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Operation not possible due to RF-kill
kevin@deep-thought:~$ 

```

doing rfkill list all shows me this again:

```

kevin@deep-thought:~$ rfkill list all
3: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes

```
and when I toggle the physical switch, still no change.

---

### Post by wildmanne39 on 2012-03-22
Hi, this should take care of the hardblock.
```
gksudo gedit /etc/rc.local
```
```
rmmod -r ath5k
rfkill unblock all
modprobe ath5k
```
Then reboot if it does not come on run the ```
rkkill list all
```command again to see if the blocks are gone.
Thanks

---

### Post by Naturally-Simple on 2012-03-22
I just need a bit of clarification. You want me to type this:

 	Code:
 	rmmod -r ath5k rfkill unblock all modprobe ath5k 
and type it into the rc.local file, or just in the terminal?

In any case, when I did this:
gksudo gedit /etc/rc.localit opened up rc.local, and this is what the file looks like this. Keep in mind, that the bottom part was added by me from the last time I was having a wireless issue:

```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
rfkill unblock wifi
exit 0

```

I didn't know what else you'd like me to do with this file. So I just typed your next coding in the terminal and got this:
```

kevin@deep-thought:~$ rmmod -r ath5k
rmmod: invalid option -- 'r'
Usage: rmmod [-fhswvV] modulename ...
 -f (or --force) forces a module unload, and may crash your
    machine.  This requires the Forced Module Removal option
    when the kernel was compiled.
 -h (or --help) prints this help text
 -s (or --syslog) says use syslog, not stderr
 -v (or --verbose) enables more messages
 -V (or --version) prints the version code
 -w (or --wait) begins a module removal even if it is used
    and will stop new users from accessing the module (so it
    should eventually fall to zero).

```

is there a different option I should be using instead of "-r"? Or is this just a case of me misunderstanding that I should actually put this coding into my rc.local file?
Thanks!

---

### Post by wildmanne39 on 2012-03-22
Hi, yes put it into your rc.local file, but remove the line you put in there before.

Put each command on its own line just before the exit o and in the order I listed them.
Thanks

---

### Post by Naturally-Simple on 2012-03-22
Okay, I edited my rc.local file with those changes. I rebooted it, and it didn't change much. Prior to making your changes, I had noticed that when I reboot, the wireless actually connects, but as soon as I unplug my cable, the wireless takes over for maybe a second and then it completely disappears and no wireless option is available. And now, with the changes to rc.local, the same thing happened.

Rfkill gives me this:
```

kevin@deep-thought:~$ rfkill list all
0: hp-wifi: Wireless LAN
        Soft blocked: no
        Hard blocked: yes
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

```and it makes no difference if I toggle the physical wireless button on my laptop, which is so odd, considering that back a year ago this made a difference.

Where do we go from here? I really appreciate you putting in the effort to help me, by the way.

---

### Post by wildmanne39 on 2012-03-22
Hi if you have windows boot windows and turn the wireless off then back on, then boot ubuntu.
Thanks

---

### Post by Naturally-Simple on 2012-03-22
Unfortunately (or fortunately, depending on how you look at it), I do not dual-boot with Windows. 100% Ubuntu here.

---

### Post by wildmanne39 on 2012-03-23
Hi, please open this file and post the output let's make sure the changes stayed after saving them.
```
gksudo gedit /etc/rc.local
```
Also post:
```
cat /etc/resolv.conf
```
```
cat /var/lib/NetworkManager/NetworkManager.state
```
Thanks

---

### Post by Naturally-Simple on 2012-03-23
Ok, here is my rc.local file:
```

  	 	 	 	 	 	   #!/bin/sh -e
 #
 # rc.local
 #
 # This script is executed at the end of each multiuser runlevel.
 # Make sure that the script will "exit 0" on success or any other
 # value on error.
 #
 # In order to enable or disable this script just change the execution
 # bits.
 #
 # By default this script does nothing.
 rmmod -r ath5k
 rfkill unblock all
 modprobe ath5k
 exit 0
  
```

and here are the other two you asked me to show you:
```

kevin@deep-thought:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 142.161.2.155
nameserver 142.161.130.155
kevin@deep-thought:~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
kevin@deep-thought:~$

```
Get this, though: When I typed "rfkill list all" this time after booting up, this is what it showed me this time:
```

kevin@deep-thought:~$ rfkill list all
0: hp-wifi: Wireless LAN
        Soft blocked: yes
        Hard blocked: yes
1: phy0: Wireless LAN
        Soft blocked: yes
        Hard blocked: no
kevin@deep-thought:~$ 

```

...so I did "rfkill unblock all" and it gave me this:
```

kevin@deep-thought:~$ rfkill unblock all
kevin@deep-thought:~$ rfkill list all
0: hp-wifi: Wireless LAN
        Soft blocked: yes
        Hard blocked: yes
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

```
...so it got rid of the soft block, but toggling the switch still didn't do anything. I wonder why it showed a soft block this time when before it wasn't?

Maybe this is unrelated to my problem?

---

### Post by wildmanne39 on 2012-03-23
Hi, another thing we should do is disable power management.
```
gksudo gedit /etc/pm/power.d/wireless
```
then add:
```
#!/bin/sh

/sbin/iwconfig wlan0 power off

```
above exit0, then save gedit, close and reboot.
Thanks

---

### Post by Naturally-Simple on 2012-03-23
When I type this:
```

gksudo gedit /etc/pm/power.d/wireless

```
it gives me a blank file. Is it supposed to be blank? In other words, do you want me to create a file that has only these lines:

```

#!/bin/sh

/sbin/iwconfig wlan0 power off

exit0

```

I'll do that if that's what you meant. But if that file is already supposed to have an "exit0" or anything else, I'm just letting you know that it's completely blank.

Let me know.

---

### Post by wildmanne39 on 2012-03-23
Hi, yes that is fine some people have may have one some do not so just create it.
Thanks

---

### Post by Naturally-Simple on 2012-03-23
ok, I've created the file and I've rebooted. No wireless coming up. Out of curiousity, just now looked at "rfkill list all" again and it showed me this:

```

kevin@deep-thought:~$ rfkill list all
0: phy0: Wireless LAN
        Soft blocked: yes
        Hard blocked: no
1: hp-wifi: Wireless LAN
        Soft blocked: yes
        Hard blocked: yes

```

What other codes should I show you next to see if what we did changed some stuff?

---

### Post by wildmanne39 on 2012-03-23
Hi, now try this one more time:
```
sudo rmmod -f hp_wmi
```
thanks

---

### Post by Naturally-Simple on 2012-03-23
Hmm... very interesting. So I typed that last code, and then I noticed that when I click on my connections icon in the taskbar, I had the option of "enable wireless" whereas before I didn't. However, even though that is now enabled, I don't have any wireless networks to connect to. "rfkill list all" now gives me this:

```

kevin@deep-thought:~$ rfkill list all
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

```

Seems very strange to me, but then, I don't know what exactly is going on. What do you think?

---

### Post by wildmanne39 on 2012-03-23
Hi, let's run some more tests while it looks like you wireless is on but do not reboot.

Post the output of:
```
nm-tool
sudo iwlist scan

```
```
sudo cat /var/log/syslog | grep -e ath -e firmware -e wlan -e wpa -e etork | tail -n75
```
Thanks

---

### Post by Naturally-Simple on 2012-03-23
Ok, here's "nm-tool":
```

kevin@deep-thought:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:1F:16:D6:21:06

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.143
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             142.161.2.155
    DNS:             142.161.130.155


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        00:24:2C:52:F9:5E

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points

```

here's iwlist scan:
```

kevin@deep-thought:~$ sudo iwlist scan
[sudo] password for kevin: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

```

and finally, here's that last long one:
```

kevin@deep-thought:~$ sudo cat /var/log/syslog | grep -e ath -e firmware -e wlan -e wpa -e etork | tail -n75
Mar 23 16:11:53 deep-thought kernel: [   16.697856] ath5k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Mar 23 16:11:53 deep-thought kernel: [   16.697871] ath5k 0000:02:00.0: setting latency timer to 64
Mar 23 16:11:53 deep-thought kernel: [   16.697924] ath5k 0000:02:00.0: registered as 'phy0'
Mar 23 16:11:53 deep-thought kernel: [   17.206236] ath: EEPROM regdomain: 0x64
Mar 23 16:11:53 deep-thought kernel: [   17.206239] ath: EEPROM indicates we should expect a direct regpair map
Mar 23 16:11:53 deep-thought kernel: [   17.206242] ath: Country alpha2 being used: 00
Mar 23 16:11:53 deep-thought kernel: [   17.206244] ath: Regpair used: 0x64
Mar 23 16:11:53 deep-thought kernel: [   17.235989] Registered led device: ath5k-phy0::rx
Mar 23 16:11:53 deep-thought kernel: [   17.236091] Registered led device: ath5k-phy0::tx
Mar 23 16:11:53 deep-thought kernel: [   17.236102] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
Mar 23 16:11:53 deep-thought kernel: [   21.599280] type=1400 audit(1332537113.091:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=874 comm="apparmor_parser"
Mar 23 16:11:53 deep-thought NetworkManager[843]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/eth0, iface: eth0)
Mar 23 16:11:53 deep-thought NetworkManager[843]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Mar 23 16:11:53 deep-thought NetworkManager[843]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0)
Mar 23 16:11:53 deep-thought NetworkManager[843]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Mar 23 16:11:53 deep-thought NetworkManager[843]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Mar 23 16:11:53 deep-thought NetworkManager[843]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Mar 23 16:11:53 deep-thought NetworkManager[843]: <info> monitoring kernel firmware directory '/lib/firmware'.
Mar 23 16:11:53 deep-thought NetworkManager[843]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Mar 23 16:11:53 deep-thought NetworkManager[843]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath5k' ifindex: 3)
Mar 23 16:11:53 deep-thought NetworkManager[843]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Mar 23 16:11:53 deep-thought NetworkManager[843]: <info> (wlan0): now managed
Mar 23 16:11:53 deep-thought NetworkManager[843]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Mar 23 16:11:53 deep-thought NetworkManager[843]: <info> (wlan0): bringing up device.
Mar 23 16:11:53 deep-thought NetworkManager[843]: <info> (wlan0): deactivating device (reason 'managed') [2]
Mar 23 17:09:39 deep-thought kernel: [   16.673734] ath5k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Mar 23 17:09:39 deep-thought kernel: [   16.673750] ath5k 0000:02:00.0: setting latency timer to 64
Mar 23 17:09:39 deep-thought kernel: [   16.673881] ath5k 0000:02:00.0: registered as 'phy0'
Mar 23 17:09:39 deep-thought kernel: [   17.181830] ath: EEPROM regdomain: 0x64
Mar 23 17:09:39 deep-thought kernel: [   17.181834] ath: EEPROM indicates we should expect a direct regpair map
Mar 23 17:09:39 deep-thought kernel: [   17.181838] ath: Country alpha2 being used: 00
Mar 23 17:09:39 deep-thought kernel: [   17.181840] ath: Regpair used: 0x64
Mar 23 17:09:39 deep-thought kernel: [   17.198879] Registered led device: ath5k-phy0::rx
Mar 23 17:09:39 deep-thought kernel: [   17.198901] Registered led device: ath5k-phy0::tx
Mar 23 17:09:39 deep-thought kernel: [   17.198911] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
Mar 23 17:09:39 deep-thought NetworkManager[849]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/eth0, iface: eth0)
Mar 23 17:09:39 deep-thought NetworkManager[849]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Mar 23 17:09:39 deep-thought NetworkManager[849]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0)
Mar 23 17:09:39 deep-thought NetworkManager[849]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Mar 23 17:09:39 deep-thought NetworkManager[849]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Mar 23 17:09:39 deep-thought NetworkManager[849]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Mar 23 17:09:39 deep-thought NetworkManager[849]: <info> monitoring kernel firmware directory '/lib/firmware'.
Mar 23 17:09:39 deep-thought NetworkManager[849]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Mar 23 17:09:39 deep-thought NetworkManager[849]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath5k' ifindex: 3)
Mar 23 17:09:39 deep-thought NetworkManager[849]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Mar 23 17:09:39 deep-thought NetworkManager[849]: <info> (wlan0): now managed
Mar 23 17:09:39 deep-thought NetworkManager[849]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Mar 23 17:09:39 deep-thought NetworkManager[849]: <info> (wlan0): bringing up device.
Mar 23 17:09:39 deep-thought NetworkManager[849]: <info> (wlan0): deactivating device (reason 'managed') [2]
Mar 23 17:18:28 deep-thought NetworkManager[849]: <info> (wlan0): bringing up device.
Mar 23 17:18:28 deep-thought NetworkManager[849]: <info> (wlan0): bringing up device.
Mar 23 17:18:28 deep-thought kernel: [  550.127777] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 23 17:18:28 deep-thought dbus[834]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Mar 23 17:18:28 deep-thought dbus[834]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Mar 23 17:18:28 deep-thought NetworkManager[849]: <info> wpa_supplicant started
Mar 23 17:18:28 deep-thought NetworkManager[849]: <info> (wlan0): supplicant interface state: starting -> ready
Mar 23 17:18:28 deep-thought NetworkManager[849]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Mar 23 17:18:28 deep-thought NetworkManager[849]: <info> (wlan0): supplicant interface state: ready -> inactive

```

thanks

---

### Post by Naturally-Simple on 2012-03-23
I'm stepping out for a while, so whenever you reply, I'll probably only apply your suggestions tomorrow. Thanks so far for all of the help you've provided! Looking forward to solving this conundrum.

---

### Post by wildmanne39 on 2012-03-23
Hi, I asked the resident expert to come help us out.
Thanks

---

### Post by chili555 on 2012-03-23
First, verify the state of rfkill:```
rfkill list all
```Verify that hp-wmi is *NOT* loaded:```
lsmod | grep wmi
```Once we see where we are now, we can move to the next steps.

---

### Post by Naturally-Simple on 2012-03-24
Ah, hello once again, chili555! I appreciated your help last time. Funny how it's come back full circle.

Here is rfkill:
```

kevin@deep-thought:~$ rfkill list all
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

```

and here is lsmod:
```

kevin@deep-thought:~$ lsmod | grep wmi
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    18744  0 

```

It's about bedtime for me, but I'm wondering whether things will change when I shut down my computer, so I'm not sure I should shut it off. Maybe I'll suspend it for the night.

---

### Post by chili555 on 2012-03-24
Please do reboot and let us see:```
dmesg | grep -e ath5 -e wlan
```Your readings look pretty solid so far.

---

### Post by Naturally-Simple on 2012-03-24
k, here's that output:
```

kevin@deep-thought:~$ dmesg | grep -e ath5 -e wlan
[   16.606498] ath5k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.606514] ath5k 0000:02:00.0: setting latency timer to 64
[   16.606570] ath5k 0000:02:00.0: registered as 'phy0'
[   17.122539] Registered led device: ath5k-phy0::rx
[   17.122561] Registered led device: ath5k-phy0::tx
[   17.122570] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)

```and in case you want or need it again, here's rfkill once more after this reboot I just did:
```

kevin@deep-thought:~$ rfkill list all
0: hp-wifi: Wireless LAN
        Soft blocked: yes
        Hard blocked: yes
1: phy0: Wireless LAN
        Soft blocked: yes
        Hard blocked: no

```
oh, and I just edited this to add that when I click on my network connections icon in the task bar, "enable wireless" is all greyed out, and there's a greyed out note that says "wireless is disabled by hardware switch". I haven't tried toggling the physical switch yet, nor have I tried doing "rfkill unblock all". I'm just now going out for a couple hours and will check in again then.
thanks!

---

### Post by chili555 on 2012-03-24
Dr. Chili is not one to curse, but...

We need to blacklist hp-wmi so it doesn't hard-block the wireless radio. Please do:```
sudo su
echo hp-wmi >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and let me see those readings again and include:```
sudo iwlist wlan0 scan
```

---

### Post by Naturally-Simple on 2012-03-24
ha, just got yer message before stepping out. Here's what you asked for:
```

kevin@deep-thought:~$ dmesg | grep -e ath5 -e wlan
[   16.794417] ath5k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.794431] ath5k 0000:02:00.0: setting latency timer to 64
[   16.794487] ath5k 0000:02:00.0: registered as 'phy0'
[   17.326645] Registered led device: ath5k-phy0::rx
[   17.326694] Registered led device: ath5k-phy0::tx
[   17.326704] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
kevin@deep-thought:~$ rfkill list all
0: hp-wifi: Wireless LAN
        Soft blocked: yes
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: yes
        Hard blocked: no

```
and here's iwlist:
```

kevin@deep-thought:~$ sudo iwlist wlan0 scan
[sudo] password for kevin: 
wlan0     Interface doesn't support scanning : Network is down

```
and I should mention that now on the network icon in the taskbar, I can choose to click "enable wireless" and the message below "wireless networks" now says "wireless is disabled"

Thanks for your help. I'll check in again in a couple hours. Putting the computer to sleep in the mean time.

---

### Post by chili555 on 2012-03-24
> 0: [COLOR="Red"]hp-wifi: Wireless LAN
        Soft blocked: yes[/COLOR]
        Hard blocked: noObviously, hp-wmi or some similar is *NOT* blacklisted. Curses. I made a mistake and I'm sorry. I forgot the word blacklist. 

Please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Is hp-wmi listed there? Please add the word blacklist so the end of the file looks like this:```
# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
**blacklist hp-wmi**
```Proofread carefully, save and close gedit. Reboot and let us see:```
rfkill list all
```

---

### Post by Naturally-Simple on 2012-03-24
Before I make changes to my blacklist.conf file, this is how it looks (well, the last part of it, anyway):
```

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
#blacklist hp-wmi

#Remove To Install MadWIFI Drivers
#blacklist ath5k

#Remove To Install MadWIFI Drivers
#blacklist ath9k
#blacklist ath5k
hp-wmi

```

...so based off of your instructions, you want me to remove the "#" which will blacklist hp-wmi, but what about that last hp-wmi? Should I remove that as well?

Also, an interesting thing has happened since we've been doing this tweaking: when I suspend my computer, which I've done three times now since making these changes, my display doesn't come up, I can't get to a terminal screen, and no key combinations or anything works resulting in me having to do a hard restart. Is this related to the things we've been changing?

Thanks

---

### Post by Naturally-Simple on 2012-03-24
Never mind my question about hp-wmi. I'm just going to remove it, because even though I may not be a very technical user, it seems pretty obvious to me that the first hp-wmi needs to be blacklisted and the second one just plain removed.

I'll do this, then reboot, then post my rfkill list all to you in a few minutes.

---

### Post by Naturally-Simple on 2012-03-24
ok, so I've rebooted, and I see that my "enable wireless" is checked off, which is good. But no wireless connections because under Wireless Networks it states: "disconnected".

Here are the outputs you asked for from the last diagnosis:
```

kevin@deep-thought:~$ rfkill list all
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
kevin@deep-thought:~$ dmesg | grep -e ath5 -e wlan
[   16.662385] ath5k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.662402] ath5k 0000:02:00.0: setting latency timer to 64
[   16.662452] ath5k 0000:02:00.0: registered as 'phy0'
[   17.185806] Registered led device: ath5k-phy0::rx
[   17.185901] Registered led device: ath5k-phy0::tx
[   17.185914] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   21.768288] ADDRCONF(NETDEV_UP): wlan0: link is not ready
kevin@deep-thought:~$ sudo iwlist wlan0 scan
[sudo] password for kevin: 
wlan0     No scan results

```

---

### Post by Naturally-Simple on 2012-03-24
weird. I just suspended, then when I came back, there was no problem, and then my wireless started working.

Here's a couple outputs:
```

kevin@deep-thought:~$ rfkill list all
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
kevin@deep-thought:~$ dmesg | grep -e ath5 -e wlan
[   17.253122] ath5k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.253137] ath5k 0000:02:00.0: setting latency timer to 64
[   17.253187] ath5k 0000:02:00.0: registered as 'phy0'
[   17.762408] Registered led device: ath5k-phy0::rx
[   17.762431] Registered led device: ath5k-phy0::tx
[   17.762441] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   22.512041] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  256.106390] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  259.778704] wlan0: authenticate with 98:fc:11:3e:bc:e2 (try 1)
[  259.784284] wlan0: authenticated
[  259.791107] wlan0: associate with 98:fc:11:3e:bc:e2 (try 1)
[  259.795588] wlan0: RX AssocResp from 98:fc:11:3e:bc:e2 (capab=0x411 status=0 aid=1)
[  259.795593] wlan0: associated
[  259.796381] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  270.064023] wlan0: no IPv6 routers present

```

When I tried the iwconfig scan, a HUGE amount of output comes out, but I can't copy and paste it all. If you tell me how to view all of the output so I can post it here for you, I will.

I will also try rebooting to see if the wireless strangely connects by itself again...

---

### Post by chili555 on 2012-03-24
> and then my wireless started working.That's all I need to see! Does it stick after reboot?

---

### Post by Naturally-Simple on 2012-03-24
Sort of and sort of not.

I've rebooted several times now, and this is how it goes:

I am prompted to enter my wireless network password (which is weird because it used to be automatic), and when I enter the password, it connects. However, as soon as I unplug my cable and try using the internet, the wireless stops working and it prompts me to enter my password, which at that point doesn't work at all to re-connect.

Has a new problem been created?

---

### Post by wildmanne39 on 2012-03-24
Hi, you said in post 39 that this is what the ```
hp-wmi
```looked like in your blacklist file did you change it to 
```
blacklist hp-wmi
```?
Thanks

---

### Post by Naturally-Simple on 2012-03-24
yep, it's blacklisted alright:
```

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist hp-wmi

#Remove To Install MadWIFI Drivers
#blacklist ath5k

#Remove To Install MadWIFI Drivers
#blacklist ath9k
#blacklist ath5k

```

---

### Post by wildmanne39 on 2012-03-24
Deleted

---

### Post by wildmanne39 on 2012-03-24
Hi, please post:
```
lsmod | grep ath
```
```
sudo iwlist scan
```
to copy the whole thing just highlight the text and hold left mouse button down and move the mouse all the way to the bottom of the terminal.
Thanks

---

### Post by Naturally-Simple on 2012-03-24
ok, I did that, and I rebooted, but no difference. How did you see that my driver was blacklisted? I thought the hp-wmi is supposed to be blacklisted. Isn't my ath5k the driver? Should I also be making a change to my blacklist.conf file?

---

### Post by Naturally-Simple on 2012-03-24
here is the output from your last request:
```

kevin@deep-thought:~$ lsmod | grep ath
ath5k                 145100  0 
ath                    19387  1 ath5k
mac80211              393421  1 ath5k
cfg80211              172427  3 ath5k,ath,mac80211
kevin@deep-thought:~$ 

```

---

### Post by wildmanne39 on 2012-03-24
> **Kevin-dell1100 said:**
> here is the output from your last request:
```

kevin@deep-thought:~$ lsmod | grep ath
ath5k                 145100  0 
ath                    19387  1 ath5k
mac80211              393421  1 ath5k
cfg80211              172427  3 ath5k,ath,mac80211
kevin@deep-thought:~$ 

```
Your driver is not blacklist that is why I immediately deleted the text. I also added a second command in  my last post with directions to post it here please do so.
Thanks

---

### Post by chili555 on 2012-03-24
> However, as soon as I unplug my cable and try using the internet, the wireless stops working Does it work correctly if you simply boot with the ethernet cable detached?

---

### Post by Naturally-Simple on 2012-03-24
Well, unlike before, when I had all sorts of output, the iwscan only gives me this now:
```

kevin@deep-thought:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

```
I'll reboot and enter that command again to see what it shows when it actually connects temporarily.

---

### Post by wildmanne39 on 2012-03-24
Hi, you may have hit the nail on the head chili depending what version of ubuntu he is using, I can connect with wireless and wired at the same time from 11.04 on but not before.
thanks

---

### Post by Naturally-Simple on 2012-03-24
Well, I tried rebooting and ran the iwlist scan command, and the wlan0 gave me all sorts of output (again, for some stupid reason I can't highlight and copy/paste it... whenever I choose "select all" it highlights it but then quickly loses the highlight, and using the mouse to drag up and select all of the text also doesn't work...). But I'd expect it to give me that output if it has actually connected, so it seems to work in that situation, but that's only right when I boot up my system. As soon as I click on my firefox, the wireless connection is lost. Same thing happens when I reboot with the ethernet cable unplugged. I'm prompted for my wireless password, I enter it, it connects, but then as soon as I try to use the internet, it disconnects, and I can't get it to connect again with my password.

this is version 11.10

---

### Post by chili555 on 2012-03-24
Wild Man, why don't you take over. Mrs. Chili and I are about to go out for the evening.

I'd be interested in syslog and I'd also try:```
sudo modprobe -r ath5k
sudo modprobe ath5k nohwcrypt=1
```If it works, Wild Man, you know what to do next.

---

### Post by Naturally-Simple on 2012-03-24
I just entered those commands you posted, Chili, and after doing the second one, it prompted me for my wireless password. Took a while, but it connected. I then unplugged my ethernet cable, and it appeared to stay connected, but as soon as I tried opening firefox, it went from a strong healthy signal to lower, then to disconnecting again without showing connecting to any site.

---

### Post by wildmanne39 on 2012-03-24
Thank you chili! we will do that.

Please reboot with your wired connection disconnected then post the output of:
```
sudo tail -n35 /var/log/syslog
```
run the commands this way that chili suggested.
```
sudo ifconfig wlan0 down
sudo rmmod -f ath5k
sudo modprobe ath5k nohwcrypt=1
sudo ifconfig wlan0 up
```
Thanks

---

### Post by Naturally-Simple on 2012-03-24
Ok, I decided to do a few reboots with different configurations with the wired or wireless being connected or disconnected. I ran the syslog command for each one. Here is scenario one, with both wired and wireless being disconnected:
```

  	 	 	 	 	 	   kevin@deep-thought:~$ sudo tail -n35 /var/log/syslog  
 [sudo] password for kevin:  
 Mar 24 16:46:16 deep-thought NetworkManager[855]: <info> (wlan0): deactivating device (reason 'supplicant-timeout') [11]  
 Mar 24 16:46:16 deep-thought NetworkManager[855]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1619  
 Mar 24 16:46:16 deep-thought avahi-daemon[864]: Withdrawing address record for 192.168.1.144 on wlan0.  
 Mar 24 16:46:16 deep-thought avahi-daemon[864]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.144.  
 Mar 24 16:46:16 deep-thought avahi-daemon[864]: Interface wlan0.IPv4 no longer relevant for mDNS.  
 Mar 24 16:46:16 deep-thought NetworkManager[855]: <info> Auto-activating connection 'Homestead'.  
 Mar 24 16:46:16 deep-thought NetworkManager[855]: <info> Activation (wlan0) starting connection 'Homestead'  
 Mar 24 16:46:16 deep-thought NetworkManager[855]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]  
 Mar 24 16:46:16 deep-thought NetworkManager[855]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...  
 Mar 24 16:46:16 deep-thought NetworkManager[855]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...  
 Mar 24 16:46:16 deep-thought NetworkManager[855]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...  
 Mar 24 16:46:16 deep-thought NetworkManager[855]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.  
 Mar 24 16:46:16 deep-thought NetworkManager[855]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...  
 Mar 24 16:46:16 deep-thought NetworkManager[855]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]  
 Mar 24 16:46:16 deep-thought NetworkManager[855]: <info> Activation (wlan0/wireless): access point 'Homestead' has security, but secrets are required.  
 Mar 24 16:46:16 deep-thought NetworkManager[855]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]  
 Mar 24 16:46:16 deep-thought NetworkManager[855]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.  
 Mar 24 16:46:16 deep-thought NetworkManager[855]: <info> (wlan0): supplicant interface state: authenticating -> disconnected  
 Mar 24 16:46:16 deep-thought dbus[828]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)  
 Mar 24 16:46:16 deep-thought NetworkManager[855]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.  
 Mar 24 16:46:16 deep-thought dbus[828]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'  
 Mar 24 16:46:22 deep-thought NetworkManager[855]: <warn> No agents were available for this request.  
 Mar 24 16:46:22 deep-thought NetworkManager[855]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]  
 Mar 24 16:46:22 deep-thought NetworkManager[855]: <warn> Activation (wlan0) failed for access point (Homestead)  
 Mar 24 16:46:22 deep-thought NetworkManager[855]: <info> Marking connection 'Homestead' invalid.  
 Mar 24 16:46:22 deep-thought NetworkManager[855]: <warn> Activation (wlan0) failed.  
 Mar 24 16:46:22 deep-thought NetworkManager[855]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]  
 Mar 24 16:46:22 deep-thought NetworkManager[855]: <info> (wlan0): deactivating device (reason 'none') [0]  
 Mar 24 16:46:33 deep-thought dbus[828]: [system] Activating service name='org.debian.apt' (using servicehelper)  
 Mar 24 16:46:35 deep-thought AptDaemon: INFO: Initializing daemon  
 Mar 24 16:46:35 deep-thought dbus[828]: [system] Successfully activated service 'org.debian.apt'  
 Mar 24 16:46:35 deep-thought AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1  
 Mar 24 16:46:35 deep-thought AptDaemon.Trans: INFO: Simulate was called  
 Mar 24 16:46:35 deep-thought AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/978fc87037d546d0a2b4c019027c1dfc  
 Mar 24 16:46:38 deep-thought AptDaemon.Worker: INFO: Upgrade system with safe mode: 1  
  
```

Here is with wired connected and wireless disconnected:
```

  	 	 	 	 	 	   kevin@deep-thought:~$ sudo tail -n35 /var/log/syslog  
 Mar 24 16:48:16 deep-thought dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1  
 Mar 24 16:48:16 deep-thought dhclient: Copyright 2004-2010 Internet Systems Consortium.  
 Mar 24 16:48:16 deep-thought dhclient: All rights reserved.  
 Mar 24 16:48:16 deep-thought dhclient: For info, please visit https://www.isc.org/software/dhcp/  
 Mar 24 16:48:16 deep-thought dhclient:  
 Mar 24 16:48:16 deep-thought NetworkManager[855]: <info> (eth0): DHCPv4 state changed nbi -> preinit  
 Mar 24 16:48:16 deep-thought dhclient: Listening on LPF/eth0/00:1f:16:d6:21:06  
 Mar 24 16:48:16 deep-thought dhclient: Sending on   LPF/eth0/00:1f:16:d6:21:06  
 Mar 24 16:48:16 deep-thought dhclient: Sending on   Socket/fallback  
 Mar 24 16:48:16 deep-thought dhclient: DHCPREQUEST of 192.168.1.143 on eth0 to 255.255.255.255 port 67  
 Mar 24 16:48:16 deep-thought dhclient: DHCPACK of 192.168.1.143 from 192.168.1.1  
 Mar 24 16:48:16 deep-thought dhclient: bound to 192.168.1.143 -- renewal in 34226 seconds.  
 Mar 24 16:48:16 deep-thought NetworkManager[855]: <info> (eth0): DHCPv4 state changed preinit -> reboot  
 Mar 24 16:48:16 deep-thought NetworkManager[855]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...  
 Mar 24 16:48:16 deep-thought NetworkManager[855]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...  
 Mar 24 16:48:16 deep-thought NetworkManager[855]: <info>   address 192.168.1.143  
 Mar 24 16:48:16 deep-thought NetworkManager[855]: <info>   prefix 24 (255.255.255.0)  
 Mar 24 16:48:16 deep-thought NetworkManager[855]: <info>   gateway 192.168.1.1  
 Mar 24 16:48:16 deep-thought NetworkManager[855]: <info>   nameserver '142.161.2.155'  
 Mar 24 16:48:16 deep-thought NetworkManager[855]: <info>   nameserver '142.161.130.155'  
 Mar 24 16:48:16 deep-thought NetworkManager[855]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...  
 Mar 24 16:48:16 deep-thought avahi-daemon[864]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.143.  
 Mar 24 16:48:16 deep-thought avahi-daemon[864]: New relevant interface eth0.IPv4 for mDNS.  
 Mar 24 16:48:16 deep-thought avahi-daemon[864]: Registering new address record for 192.168.1.143 on eth0.IPv4.  
 Mar 24 16:48:17 deep-thought NetworkManager[855]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]  
 Mar 24 16:48:17 deep-thought NetworkManager[855]: <info> Policy set 'Auto Ethernet' (eth0) as default for IPv4 routing and DNS.  
 Mar 24 16:48:17 deep-thought NetworkManager[855]: <info> Activation (eth0) successful, device activated.  
 Mar 24 16:48:17 deep-thought NetworkManager[855]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.  
 Mar 24 16:48:17 deep-thought NetworkManager[855]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.  
 Mar 24 16:48:17 deep-thought dbus[828]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)  
 Mar 24 16:48:17 deep-thought dbus[828]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'  
 Mar 24 16:48:18 deep-thought avahi-daemon[864]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::21f:16ff:fed6:2106.  
 Mar 24 16:48:18 deep-thought avahi-daemon[864]: New relevant interface eth0.IPv6 for mDNS.  
 Mar 24 16:48:18 deep-thought avahi-daemon[864]: Registering new address record for fe80::21f:16ff:fed6:2106 on eth0.*.  
 Mar 24 16:48:26 deep-thought ntpdate[2305]: adjust time server 91.189.94.4 offset -0.267061 sec  
  
```

and finally, here's with wired disconnected and wireless temporarily "connected":
```

  	 	 	 	 	 	   kevin@deep-thought:~$ sudo tail -n35 /var/log/syslog  
 [sudo] password for kevin:  
 Mar 24 16:51:10 deep-thought NetworkManager[863]: <info>   address 192.168.1.144  
 Mar 24 16:51:10 deep-thought NetworkManager[863]: <info>   prefix 24 (255.255.255.0)  
 Mar 24 16:51:10 deep-thought NetworkManager[863]: <info>   gateway 192.168.1.1  
 Mar 24 16:51:10 deep-thought NetworkManager[863]: <info>   nameserver '142.161.2.155'  
 Mar 24 16:51:10 deep-thought NetworkManager[863]: <info>   nameserver '142.161.130.155'  
 Mar 24 16:51:10 deep-thought NetworkManager[863]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...  
 Mar 24 16:51:11 deep-thought NetworkManager[863]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]  
 Mar 24 16:51:11 deep-thought NetworkManager[863]: <info> Policy set 'Homestead' (wlan0) as default for IPv4 routing and DNS.  
 Mar 24 16:51:11 deep-thought NetworkManager[863]: <info> Activation (wlan0) successful, device activated.  
 Mar 24 16:51:11 deep-thought NetworkManager[863]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.  
 Mar 24 16:51:11 deep-thought NetworkManager[863]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.  
 Mar 24 16:51:11 deep-thought dbus[836]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)  
 Mar 24 16:51:11 deep-thought dbus[836]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'  
 Mar 24 16:51:13 deep-thought wpa_supplicant[929]: CTRL-EVENT-DISCONNECTED bssid=98:fc:11:3e:bc:e2 reason=4  
 Mar 24 16:51:13 deep-thought kernel: [   46.864123] cfg80211: All devices are disconnected, going to restore regulatory settings  
 Mar 24 16:51:13 deep-thought kernel: [   46.864130] cfg80211: Restoring regulatory settings  
 Mar 24 16:51:13 deep-thought kernel: [   46.864170] cfg80211: Calling CRDA to update world regulatory domain  
 Mar 24 16:51:13 deep-thought NetworkManager[863]: <info> (wlan0): supplicant interface state: completed -> disconnected  
 Mar 24 16:51:13 deep-thought kernel: [   46.868368] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain  
 Mar 24 16:51:13 deep-thought kernel: [   46.868373] cfg80211: World regulatory domain updated:  
 Mar 24 16:51:13 deep-thought kernel: [   46.868375] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)  
 Mar 24 16:51:13 deep-thought kernel: [   46.868378] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)  
 Mar 24 16:51:13 deep-thought kernel: [   46.868381] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)  
 Mar 24 16:51:13 deep-thought kernel: [   46.868384] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)  
 Mar 24 16:51:13 deep-thought kernel: [   46.868387] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)  
 Mar 24 16:51:13 deep-thought kernel: [   46.868390] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)  
 Mar 24 16:51:13 deep-thought NetworkManager[863]: <info> (wlan0): supplicant interface state: disconnected -> scanning  
 Mar 24 16:51:14 deep-thought wpa_supplicant[929]: Trying to authenticate with 98:fc:11:3e:bc:e2 (SSID='Homestead' freq=2437 MHz)  
 Mar 24 16:51:14 deep-thought NetworkManager[863]: <info> (wlan0): supplicant interface state: scanning -> authenticating  
 Mar 24 16:51:14 deep-thought kernel: [   47.800477] wlan0: authenticate with 98:fc:11:3e:bc:e2 (try 1)  
 Mar 24 16:51:14 deep-thought kernel: [   48.000036] wlan0: authenticate with 98:fc:11:3e:bc:e2 (try 2)  
 Mar 24 16:51:14 deep-thought kernel: [   48.200045] wlan0: authenticate with 98:fc:11:3e:bc:e2 (try 3)  
 Mar 24 16:51:14 deep-thought kernel: [   48.400034] wlan0: authentication with 98:fc:11:3e:bc:e2 timed out  
 Mar 24 16:51:17 deep-thought kernel: [   50.704033] wlan0: no IPv6 routers present  
 Mar 24 16:51:18 deep-thought NetworkManager[863]: <info> (wlan0): roamed from BSSID 98:FC:11:3E:BC:E2 (Homestead) to (none) ((none))  
  
```

Then I ran these commands:
```

kevin@deep-thought:~$ sudo ifconfig wlan0 down
kevin@deep-thought:~$ sudo rmmod -f ath5k
kevin@deep-thought:~$ sudo modprobe ath5k nohwcrypt=1
kevin@deep-thought:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Operation not possible due to RF-kill

```
so they all seemed to work except that last one.

---

### Post by wildmanne39 on 2012-03-24
Hi,> SIOCSIFFLAGS: Operation not possible due to RF-kill that means that you are hardblocked again or softblocked which you should not be.
Thanks

---

### Post by Naturally-Simple on 2012-03-24
this is what rfkill just gave me:
```

kevin@deep-thought:~$ rfkill list all
1: phy1: Wireless LAN
        Soft blocked: no
        Hard blocked: yes

```
and no changes when I toggle the physical switch. "rfkill unblock all" also does not change the rfkill list all:
```

kevin@deep-thought:~$ rfkill unblock all
kevin@deep-thought:~$ rfkill list all
1: phy1: Wireless LAN
        Soft blocked: no
        Hard blocked: yes

```

---

### Post by wildmanne39 on 2012-03-24
I also see that you are having issues with encryption it looks like but we can not work on that until the hardblock is gone.

I will do more research on the issue.
Thanks

---

### Post by Naturally-Simple on 2012-03-24
Thanks so much! I really appreciate the work you're putting into helping me.

What does it mean that I have encryption issues?

Unfortunately, similar to Chili, I also have evening plans. I may check once more before bed, otherwise I'll run whatever commands and instructions you give me tomorrow morning.

---

### Post by wildmanne39 on 2012-03-24
Hi, it means you are having issues logging into your routers security or it could be that the hardblock keeps coming back before it connects not sure yet .
Thanks

---

### Post by chili555 on 2012-03-25
> and no changes when I toggle the physical switch.Meaning what? The wireless key combination; Fn+F5, for example? Or a physical On-Off switch or slider? What model Dell is it?

---

### Post by Naturally-Simple on 2012-03-25
Ha, I shouldn't have chosen a user name based off of the computer I once owned. I don't have a Dell any more. I use a Compaq HP Presario CQ60, and it has a blue/orange-lighted wireless button next to the power button. The Fn+__ corresponds pretty much exactly as my keys show, so pushing Fn+F5 will put my computer to sleep, Fn+F7 decreases my screen brightness, and so on.

By the way, after this boot up, when I click on my connections, both "Networking" and "wireless" are enabled, but it tells me in a greyed out font that "Wireless Networks disconnected" but I have no networks to choose from to connect to.

When I do rfkill this time, I get something different than I had last evening:
```

kevin@deep-thought:~$ rfkill list all
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

```

---

### Post by chili555 on 2012-03-25
> kevin@deep-thought:~$ rfkill list all
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: noWell, sir! Now we're getting a lot closer. Does it scan now?```
sudo iwlist wlan0 scan
```What if you do:```
sudo modprobe -r ath5k
sudo modprobe ath5k nohwcrypt=1
sudo iwlist wlan0 scan
```No need to post all the cells it sees; just 'Yes' will do.

---

### Post by Naturally-Simple on 2012-03-25
When I first tried the scan, it told me that there were no scan results. Then I went through the three other commands you listed, and when I did the last one again with the scan, it tells me: "Interface doesn't support scanning : Network is down" and then I looked at my connections and saw that yes indeed, the "enable wireless" is no longer checked, and is greyed out. Wireless Networks now states, in greyed out font: "wireless is disabled by hardware switch". And this is what rfkill now gives me:
```

kevin@deep-thought:~$ rfkill list all
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes

```

---

### Post by chili555 on 2012-03-25
> kevin@deep-thought:~$ rfkill list all
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yesIs there any change when you press the wireless button? How about this:```
sudo rfkill unblock all
rfkill list all
```

---

### Post by Naturally-Simple on 2012-03-25
No, that's kind of what this problem was like at the beginning. I push the wireless button, but no change. I try to unblock all, but nothing.
```

kevin@deep-thought:~$ rfkill unblock all
kevin@deep-thought:~$ rfkill list all
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes

```
It was at this point last time when Wild Man suggested using Windows, if I dual boot, to remove the hard block, but I don't dual boot. We had it unblocked there before doing the modprobe commands, right?

---

### Post by chili555 on 2012-03-25
I am reviewing our older threads. Please try this:```
sudo modprobe hp-wmi
```Now press the wireless button. Any changes?```
sudo rfkill unblock all
rfkill list all
```Anything?

---

### Post by Naturally-Simple on 2012-03-25
After modprobe and then pressing my wireless button:
```

kevin@deep-thought:~$ sudo modprobe hp-wmi
[sudo] password for kevin:
kevin@deep-thought:~$ rfkill list all
1: phy0: Wireless LAN
        Soft blocked: yes
        Hard blocked: yes
2: hp-wifi: Wireless LAN
        Soft blocked: yes
        Hard blocked: yes
kevin@deep-thought:~$ rfkill list all
1: phy0: Wireless LAN
        Soft blocked: yes
        Hard blocked: yes
2: hp-wifi: Wireless LAN
        Soft blocked: yes
        Hard blocked: yes

```
And unblock all gives me this:
```

kevin@deep-thought:~$ sudo rfkill unblock all
kevin@deep-thought:~$ rfkill list all
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes
2: hp-wifi: Wireless LAN
        Soft blocked: yes
        Hard blocked: yes

```
I once again tried the wireless button, but no changes.

---

### Post by chili555 on 2012-03-25
Frankly, I am at a loss. It won't work *at all* with hp-wmi loaded. It won't connect *at all* without nohwcrypt=1, but that seems to cause hard blocked.

Unless wildmanne39 has any better ideas, frankly I'd seriously consider downgrading to 11.04 or even 10.10. At least it works.

---

### Post by Naturally-Simple on 2012-03-25
Well, it also worked with 10.04, but then stopped working with 10.10, as I recall, and with 11.04, I didn't care about the wireless because I decided to just use wired all the time. Then after I upgraded to 11.10, I had it working for a few weeks without any problem until just this week.

So, I guess I'll be content with just wired again until 12.04 and we'll see how that goes after I upgrade. The idea is that issues like this are supposed to be worked out as the software/updates catch up with hardware, no?

---

### Post by wildmanne39 on 2012-03-25
Hi, do you have an older kernel you can use to boot with in grub to see if it will work that way?

Also it is very strange that is why I asked chili555 to help because it just bounces back and forth between blocked and unblocked and it still will not scan when it shows unblocked.

I wonder if when you have trouble last october if you made changes to any other files that may be effecting the changes we are doing now?
Thanks

---

### Post by chili555 on 2012-03-25
> The idea is that issues like this are supposed to be worked out as the software/updates catch up with hardware, no?Yes. I suspect the problem is hp-wmi and you may wish to file a bug report: [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

---

### Post by Naturally-Simple on 2012-03-25
Hmm. I really have no idea how to boot with an older kernel. That seems complicated, or isn't it?

Back when my wireless first stopped working, I did a lot of the same sorts of things we've been doing this time, except that last time also involved installing MadWIFI, following instructions given by [drpjkurian]("http://ubuntuforums.org/member.php?u=805294") and then some tweaking by Chili. I honestly don't know what impact those changes may have had on my system.

I'm really quite unknowledgeable with Linux and Ubuntu. I don't know the technical stuff at all, so I mostly just take and try the suggestions and advice of you kind folks who do know a lot.

Perhaps I will file a bug report. There must be others with this same or a similar problem.

---

### Post by wildmanne39 on 2012-03-25
Hi, no it is not hard, reboot and hold down the shift key then you should see a menu with the kernels listed and see if you have more then one kernel to boot from but not the recovery or memtest.
Thanks

---

### Post by Naturally-Simple on 2012-03-25
Thanks for your instructions. I have two older kernels I could use to boot. There is 2.6.38-13-generic and its recovery version, and I also have 2.6.32-25-generic and it's recovery version.

Which should I choose, and what should I do once I choose one?

---

### Post by wildmanne39 on 2012-03-25
Hi, try 2.6.38-13-generic first and if wireless does not work in it try the other one but if it does work and you update your kernel it will most likely break it again.
Thanks

---

### Post by chili555 on 2012-03-25
> **wildmanne39 said:**
> Hi, try 2.6.38-13-generic first and if wireless does not work in it try the other one but if it does work and you update your kernel it will most likely break it again.
ThanksAgreed, but you needn't try the recovery versions. My bet is on 2.6.32. If it works, the Wild Man will show you how to make it default.

---

### Post by Naturally-Simple on 2012-03-25
Interesting tests. I tried both 2.6.38-13-generic and 2.6.32-25-generic, and both had the same results as each other. Just like with the current kernel I'm using now, these two different boots prompted me to enter my wireless password. But what was different from these two older kernels compared to the current one I'm using now, is that the wireless connected, then disconnected, but being prompted to enter my password again, it re-connected, I scanned it with iwlist, and it worked. But of course each time it disconnected, which it kept doing, I couldn't scan.

Here's the part I find particularly interesting, but maybe it means nothing to you two: When I booted into the current kernel I'm using now, and once it connected temporarily, I tried doing the scan as I had done before, but this time it said:
```

kevin@deep-thought:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Device or resource busy

```
which is different than before. If I scan it now, it gives me the same message as before, "no scan results". I wonder why, during these temporary connections, it would give me a different message with this newer kernel as opposed to the older ones, which just seemed to scan normally.

---

### Post by wildmanne39 on 2012-03-25
Hi, will we can run some commands on one of the kernels to see if we can get it to work so I would go with the newest kernel and run these commands:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
nm-tool
```
Also make sure your router is set to wpa2 encryption only if possible.
Thanks

---

### Post by Naturally-Simple on 2012-03-25
Here are the outputs of those commands under kernal 2.6.38-13-generic. And yes, the wireless encryption is WPA & WPA2 (can't do solely wpa2 as far I can tell). Also keep in mind that I ran these commands while the wireless was disconnected. There was a period there where it connected and I was actually able to access a website, but then it disconnected again and prompted me for the password.
```

kevin@deep-thought:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux deep-thought 2.6.38-13-generic #55-Ubuntu SMP Tue Jan 24 14:27:59 UTC 2012 i686 i686 i386 GNU/Linux

kevin@deep-thought:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:360b]
    Kernel driver in use: r8169
--
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Hewlett-Packard Company AR5BXB63 (Foxconn) 802.11bg Mini PCIe NIC [103c:137a]
    Kernel driver in use: ath5k

kevin@deep-thought:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

kevin@deep-thought:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

kevin@deep-thought:~$ lsmod
Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  0 
aes_generic            38023  1 aes_i586
sco                    17827  2 
bnep                   17785  2 
rfcomm                 38125  0 
l2cap                  48656  6 bnep,rfcomm
bluetooth              65493  6 sco,bnep,rfcomm,l2cap
parport_pc             32111  0 
ppdev                  12849  0 
binfmt_misc            13213  1 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_conexant    43782  1 
joydev                 17322  0 
snd_hda_intel          24113  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
arc4                   12473  2 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               66851  0 
ath5k                 144534  0 
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  451053  3 
videodev               75143  1 uvcvideo
ath                    19141  1 ath5k
drm_kms_helper         40971  1 i915
drm                   184164  4 i915,drm_kms_helper
soundcore              12600  1 snd
mac80211              257001  1 ath5k
psmouse                73312  0 
i2c_algo_bit           13184  1 i915
lp                     13349  0 
serio_raw              12990  0 
cfg80211              156212  3 ath5k,ath,mac80211
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  1 i915
parport                36746  3 parport_pc,ppdev,lp
usb_storage            43946  0 
uas                    17676  0 
ahci                   21591  3 
r8169                  42534  0 
libahci                25548  1 ahci

kevin@deep-thought:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:1F:16:D6:21:06

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.143
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             142.161.2.155
    DNS:             142.161.130.155


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        00:24:2C:52:F9:5E

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    71D446:          Infra, 38:60:77:1D:F3:FA, Freq 2452 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    Homestead:       Infra, 98:FC:11:3E:BC:E2, Freq 2437 MHz, Rate 54 Mb/s, Strength 80 WPA WPA2
    canadianpress-guest: Infra, 58:6D:8F:8F:A5:F5, Freq 2412 MHz, Rate 54 Mb/s, Strength 12
    7E0635:          Infra, 38:60:77:8D:0A:8A, Freq 2462 MHz, Rate 54 Mb/s, Strength 5 WPA WPA2
    SENNHEISER:      Infra, 00:24:01:CE:EB:BB, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA
    p@tc4e5:         Infra, 00:15:05:F8:0E:1C, Freq 2452 MHz, Rate 54 Mb/s, Strength 5 WPA WPA2
    2WIRE359:        Infra, 28:16:2E:40:E5:B1, Freq 2417 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    canadianpress:   Infra, 58:6D:8F:8F:A5:F4, Freq 2412 MHz, Rate 54 Mb/s, Strength 10 WPA WPA2
    8DA8AB:          Infra, 38:60:77:DB:B8:CE, Freq 2412 MHz, Rate 54 Mb/s, Strength 12 WPA WPA2
    mhn312:          Infra, 00:24:56:74:D1:C1, Freq 2412 MHz, Rate 54 Mb/s, Strength 5 WPA WPA2
    9056E6:          Infra, 38:60:77:E3:7F:0F, Freq 2412 MHz, Rate 54 Mb/s, Strength 2 WPA WPA2
    716268:          Infra, 38:60:77:2D:07:97, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    2WIRE446:        Infra, 28:16:2E:CC:80:C9, Freq 2432 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    C50915:          Infra, 78:CD:8E:C5:09:19, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    747E0D:          Infra, 78:CD:8E:74:7E:10, Freq 2427 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    2WIRE881:        Infra, 64:0F:28:F8:7F:F9, Freq 2432 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2

```

And here are those same ones while temporarily connected:
```

kevin@deep-thought:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux deep-thought 2.6.38-13-generic #55-Ubuntu SMP Tue Jan 24 14:27:59 UTC 2012 i686 i686 i386 GNU/Linux

kevin@deep-thought:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:360b]
    Kernel driver in use: r8169
--
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Hewlett-Packard Company AR5BXB63 (Foxconn) 802.11bg Mini PCIe NIC [103c:137a]
    Kernel driver in use: ath5k

kevin@deep-thought:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Homestead"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 98:FC:11:3E:BC:E2   
          Bit Rate=5.5 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:15   Missed beacon:0

kevin@deep-thought:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

kevin@deep-thought:~$ lsmod
Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  1 
aes_generic            38023  1 aes_i586
sco                    17827  2 
bnep                   17785  2 
rfcomm                 38125  0 
l2cap                  48656  6 bnep,rfcomm
bluetooth              65493  6 sco,bnep,rfcomm,l2cap
parport_pc             32111  0 
ppdev                  12849  0 
binfmt_misc            13213  1 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_conexant    43782  1 
joydev                 17322  0 
snd_hda_intel          24113  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
arc4                   12473  2 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               66851  0 
ath5k                 144534  0 
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  451053  3 
videodev               75143  1 uvcvideo
ath                    19141  1 ath5k
drm_kms_helper         40971  1 i915
drm                   184164  4 i915,drm_kms_helper
soundcore              12600  1 snd
mac80211              257001  1 ath5k
psmouse                73312  0 
i2c_algo_bit           13184  1 i915
lp                     13349  0 
serio_raw              12990  0 
cfg80211              156212  3 ath5k,ath,mac80211
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  1 i915
parport                36746  3 parport_pc,ppdev,lp
usb_storage            43946  0 
uas                    17676  0 
ahci                   21591  3 
r8169                  42534  0 
libahci                25548  1 ahci

kevin@deep-thought:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:1F:16:D6:21:06

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.143
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             142.161.2.155
    DNS:             142.161.130.155


- Device: wlan0  [Homestead] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             connected
  Default:           no
  HW Address:        00:24:2C:52:F9:5E

  Capabilities:
    Speed:           5 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *Homestead:      Infra, 98:FC:11:3E:BC:E2, Freq 2437 MHz, Rate 54 Mb/s, Strength 95 WPA WPA2
    71D446:          Infra, 38:60:77:1D:F3:FA, Freq 2452 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    canadianpress-guest: Infra, 58:6D:8F:8F:A5:F5, Freq 2412 MHz, Rate 54 Mb/s, Strength 2
    7E0635:          Infra, 38:60:77:8D:0A:8A, Freq 2462 MHz, Rate 54 Mb/s, Strength 5 WPA WPA2
    SENNHEISER:      Infra, 00:24:01:CE:EB:BB, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA
    p@tc4e5:         Infra, 00:15:05:F8:0E:1C, Freq 2452 MHz, Rate 54 Mb/s, Strength 10 WPA WPA2
    2WIRE359:        Infra, 28:16:2E:40:E5:B1, Freq 2417 MHz, Rate 54 Mb/s, Strength 9 WPA WPA2
    canadianpress:   Infra, 58:6D:8F:8F:A5:F4, Freq 2412 MHz, Rate 54 Mb/s, Strength 5 WPA WPA2
    8DA8AB:          Infra, 38:60:77:DB:B8:CE, Freq 2412 MHz, Rate 54 Mb/s, Strength 4 WPA WPA2
    mhn312:          Infra, 00:24:56:74:D1:C1, Freq 2412 MHz, Rate 54 Mb/s, Strength 5 WPA WPA2
    9056E6:          Infra, 38:60:77:E3:7F:0F, Freq 2412 MHz, Rate 54 Mb/s, Strength 10 WPA WPA2
    716268:          Infra, 38:60:77:2D:07:97, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    2WIRE446:        Infra, 28:16:2E:CC:80:C9, Freq 2432 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    C50915:          Infra, 78:CD:8E:C5:09:19, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    747E0D:          Infra, 78:CD:8E:74:7E:10, Freq 2427 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    2WIRE881:        Infra, 64:0F:28:F8:7F:F9, Freq 2432 MHz, Rate 54 Mb/s, Strength 75 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.144
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             142.161.2.155
    DNS:             142.161.130.155

```
Also keep in mind that this temporary connection lasts up until the point when I unplug my ethernet cable. This last time, I was able to visit three sites before the wireless disconnected.

---

### Post by wildmanne39 on 2012-03-25
Hi, I suggest we try to insert this parameter and see if it helps but do not reboot after you run the commands:
```
sudo ifconfig wlan0 down
sudo rmmod -f ath5k
sudo modprobe ath5k nohwcrypt=1
sudo ifconfig wlan0 up
```
thanks

---

### Post by chili555 on 2012-03-25
> Homestead:       Infra, 98:FC:11:3E:BC:E2, Freq 2437 MHz, Rate 54 Mb/s, Strength 80 [COLOR="Red"]WPA WPA2[/COLOR]I suggest you try with the router changed to WPA2 only; not mixed WPA and WPA2.

---

### Post by Naturally-Simple on 2012-03-25
ok, ran those commands, but no luck on changing the connection. after the modprobe, I was prompted to enter my wireless password, and it once again connected, I was able to access a site or two, then it disconnected and asked for my password again.

As for only using WPA2, I don't have that option. My options are: WEP 40/128-bit, WEP 128-bit Passphrase, LEAP, Dynamic WEP (802.1x), WPA & WPA2 Personal, and WPA & WPA2 Enterprise.

---

### Post by wildmanne39 on 2012-03-25
Hi, there are a lot of routers in your area that may be causing issues you could try to change the channel your wireless is on.

You could try wicd instead of network manager but you must install wicd before you uninstall networkmanager.

Also you can post the output of this command it should tell us more since your wireless is scanning now.
```
sudo cat /var/log/syslog | grep -e ath -e firmware -e wpa -e wlan -e etork | tail -n35
```
Thanks

---

### Post by Naturally-Simple on 2012-03-25
Here's the output from that command:
```

kevin@deep-thought:~$ sudo cat /var/log/syslog | grep -e ath -e firmware -e wpa -e wlan -e etork | tail -n35
[sudo] password for kevin: 
Mar 25 18:09:18 deep-thought NetworkManager[862]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 25 18:09:18 deep-thought NetworkManager[862]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Mar 25 18:09:19 deep-thought wpa_supplicant[919]: Trying to authenticate with 98:fc:11:3e:bc:e2 (SSID='Homestead' freq=2437 MHz)
Mar 25 18:09:19 deep-thought kernel: [ 2789.299348] wlan0: authenticate with 98:fc:11:3e:bc:e2 (try 1)
Mar 25 18:09:19 deep-thought wpa_supplicant[919]: Trying to associate with 98:fc:11:3e:bc:e2 (SSID='Homestead' freq=2437 MHz)
Mar 25 18:09:19 deep-thought kernel: [ 2789.301075] wlan0: authenticated
Mar 25 18:09:19 deep-thought kernel: [ 2789.301506] wlan0: associate with 98:fc:11:3e:bc:e2 (try 1)
Mar 25 18:09:19 deep-thought kernel: [ 2789.303998] wlan0: RX ReassocResp from 98:fc:11:3e:bc:e2 (capab=0x411 status=0 aid=1)
Mar 25 18:09:19 deep-thought kernel: [ 2789.304035] wlan0: associated
Mar 25 18:09:19 deep-thought wpa_supplicant[919]: Associated with 98:fc:11:3e:bc:e2
Mar 25 18:09:19 deep-thought NetworkManager[862]: <info> (wlan0): supplicant interface state: scanning -> associating
Mar 25 18:09:19 deep-thought NetworkManager[862]: <info> (wlan0): supplicant interface state: associating -> associated
Mar 25 18:09:19 deep-thought NetworkManager[862]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Mar 25 18:09:19 deep-thought wpa_supplicant[919]: WPA: Key negotiation completed with 98:fc:11:3e:bc:e2 [PTK=CCMP GTK=TKIP]
Mar 25 18:09:19 deep-thought wpa_supplicant[919]: CTRL-EVENT-CONNECTED - Connection to 98:fc:11:3e:bc:e2 completed (reauth) [id=0 id_str=]
Mar 25 18:09:19 deep-thought NetworkManager[862]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Mar 25 18:09:19 deep-thought NetworkManager[862]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Homestead'.
Mar 25 18:09:19 deep-thought NetworkManager[862]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Mar 25 18:09:19 deep-thought NetworkManager[862]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Mar 25 18:09:19 deep-thought NetworkManager[862]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Mar 25 18:09:19 deep-thought NetworkManager[862]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Mar 25 18:09:19 deep-thought NetworkManager[862]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Mar 25 18:09:19 deep-thought NetworkManager[862]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Mar 25 18:09:19 deep-thought dhclient: Listening on LPF/wlan0/00:24:2c:52:f9:5e
Mar 25 18:09:19 deep-thought dhclient: Sending on   LPF/wlan0/00:24:2c:52:f9:5e
Mar 25 18:09:19 deep-thought dhclient: DHCPREQUEST of 192.168.1.144 on wlan0 to 255.255.255.255 port 67
Mar 25 18:09:21 deep-thought dhclient: DHCPREQUEST of 192.168.1.144 on wlan0 to 255.255.255.255 port 67
Mar 25 18:09:22 deep-thought NetworkManager[862]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Mar 25 18:09:22 deep-thought NetworkManager[862]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Mar 25 18:09:22 deep-thought NetworkManager[862]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Mar 25 18:09:22 deep-thought NetworkManager[862]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Mar 25 18:09:23 deep-thought NetworkManager[862]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Mar 25 18:09:23 deep-thought NetworkManager[862]: <info> Activation (wlan0) successful, device activated.
Mar 25 18:09:23 deep-thought NetworkManager[862]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Mar 25 18:09:23 deep-thought NetworkManager[862]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.

```

I'm not sure how to change the channel on my router. But I'd be willing to give that a try if I have very simple step-by-step instructions on how to do it. I'd also be up for trying wicd if you really think that would help.

Ah, but this may be it for me tonight. I'm off for dinner and a movie. I'll check this thread again before bed.

---

### Post by chili555 on 2012-03-25
> As for only using WPA2, I don't have that option. My options are: WEP 40/128-bit, WEP 128-bit Passphrase, LEAP, Dynamic WEP (802.1x), WPA & WPA2 Personal, and WPA & WPA2 Enterprise.In the *router* you mean??

---

### Post by Naturally-Simple on 2012-03-26
ok, never mind. Now I know what you mean. So I should switch my router to WPA2 only. And what should I do after this?

This is late in the night, so I don't expect you two to get back to me until the morning. In your next message, can you tell me what kernel you'd like me to boot with and whether I should or shouldn't use only WPA2 (and whether that's something I should do with a different kernel or not).

Thanks!

---

### Post by chili555 on 2012-03-26
> So I should switch my router to WPA2 only. And what should I do after this?Yes! Exactly. Then try to connect with your default 11.10 kernel, having booted without any ethernet cable attached. Note the result and then try with the prior kernels. 

Report your result including such terms as Yippee, Hooray and SOLVED as necessary.

---

### Post by Naturally-Simple on 2012-03-26
Wow, you seemed very confident that that would work. I'm sorry to disappoint you. I did as you said, switched my router to WPA2 Personal, then rebooted first with my default kernel, then with the 2.6.38-13 and then with 2.6.32-25, but no difference. The wireless no longer asks me for my password when Ubuntu loads, as it did before, and this is the same with each of the kernels. There was mention before about changing channels. Right now my router is set to auto. Should I change that? Any other suggestions or commands I should try now that it's switched to WPA2 only?

---

### Post by chili555 on 2012-03-26
I never heard of a channel setting in the *router* of 'Auto,' but I guess I learn something new every day. I'd try channel 1 or 11.> The wireless no longer asks me for my password when Ubuntu loadsWhen you click the Network Manager icon do you see your network? Does it try to connect if you click it?> Wow, you seemed very confident that that would work.I've seen it work many times before, so I was hoping!

---

### Post by Naturally-Simple on 2012-03-26
Well, I tried changing channels, but no luck. Same as before, with trying to connect, then connecting for a bit and actually accessing a few websites, but then it goes up and down in the signal strength, ultimately ending with disconnecting.

Here's a thought I just had:

I have a landline phone through my internet connection. This is how the connection works: My ISP modem is connected to my Cisco router, and of the four spots I have on the router, #1 is my ethernet cable, which I'm using to access the internet now, and #2 is for my Linksys phone modem, which has a phone jack and phone attached.

Would you think this has any bearing on my wireless problem? I feel like it shouldn't, especially considering that my wireless was working just fine for a few weeks prior to this. But let me know what you think.

---

### Post by chili555 on 2012-03-27
> Would you think this has any bearing on my wireless problem? None whatever.

Frankly, I am out of ideas/talent/mojo. I regret that I couldn't have been more help.

---

### Post by wildmanne39 on 2012-03-27
Hi, I know nothing else to do, I really thought booting an older kernel might help the issue but since it did not I guess we are at a dead in.

---

### Post by Naturally-Simple on 2012-03-27
Thanks to both of you for putting in so much effort at helping me solve this problem. I really appreciate your time and energy. I will just be content once again without a wireless connection until I try out 12.04 to see if there's any change.

---

### Post by chili555 on 2012-03-27
> **Kevin-dell1100 said:**
> Thanks to both of you for putting in so much effort at helping me solve this problem. I really appreciate your time and energy. I will just be content once again without a wireless connection until I try out 12.04 to see if there's any change.Please keep us posted.

---

