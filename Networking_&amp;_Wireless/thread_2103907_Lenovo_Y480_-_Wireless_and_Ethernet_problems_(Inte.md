---
title: "Lenovo Y480 - Wireless and Ethernet problems (Intel Centrino N-2200 / Atheros AR8161)"
date: 2013-01-11
forum: Networking &amp; Wireless
---

### Post by DjBuss on 2013-01-11
I'm having problems to conect with some wireless networks.
My wireles works fine at home, but now I'm not being able to connect in a friends network.

The same thing is happening with my Ethernet connection, I does work.

I have already copied the file described as Intel® Centrino® Wireless-N 2200 3.2+ iwlwifi-2000-ucode-18.168.6.1.tgzthat I downloaded from [http://wireless.kernel.org/en/users/Drivers/iwlwifi?p=iwlwifi](http://wireless.kernel.org/en/users/Drivers/iwlwifi?p=iwlwifi)
and I just copied it the iwlwifi-2000-6.ucode to /lit/firmware

Following what's described here [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681) I'm posting the following:

model/brand
```
notebook Lenovo Y480
```

lspci

```
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GK107 [GeForce GT 650M] (rev a1)
02:00.0 Ethernet controller: Atheros Communications Inc. AR8161 Gigabit Ethernet (rev 08)
03:00.0 Network controller: Intel Corporation Centrino Wireless-N 2200 (rev c4)
04:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 30)
04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 30)
04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 30)
04:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 30)

```

lsusb
```
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GK107 [GeForce GT 650M] (rev a1)
02:00.0 Ethernet controller: Atheros Communications Inc. AR8161 Gigabit Ethernet (rev 08)
03:00.0 Network controller: Intel Corporation Centrino Wireless-N 2200 (rev c4)
04:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 30)
04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 30)
04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 30)
04:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 30)

```

lspci -nn | grep 'Centrino'

```
03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2200 [8086:0891] (rev c4)

```

ifconfig

```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1472 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1472 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:119904 (119.9 KB)  TX bytes:119904 (119.9 KB)

wlan0     Link encap:Ethernet  HWaddr 9c:4e:36:5b:4a:48  
          inet6 addr: fe80::9e4e:36ff:fe5b:4a48/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:460 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:128276 (128.2 KB)
```

iwconfig
```
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

```

lsmod
```
Module                  Size  Used by
iwlwifi               386826  0 
nls_utf8               12557  1 
isofs                  39842  1 
snd_hda_codec_hdmi     32007  1 
snd_hda_codec_realtek    78045  1 
uvcvideo               76749  0 
videobuf2_core         32851  1 uvcvideo
videodev              120309  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12860  1 uvcvideo
videobuf2_memops       13368  1 videobuf2_vmalloc
rfcomm                 46619  12 
parport_pc             32688  0 
bnep                   18140  2 
ppdev                  17073  0 
binfmt_misc            17500  1 
nls_iso8859_1          12713  1 
coretemp               13400  0 
arc4                   12529  2 
kvm                   414070  0 
ghash_clmulni_intel    13180  0 
aesni_intel            51037  0 
cryptd                 20403  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17208  1 aesni_intel
joydev                 17457  0 
btusb                  22474  0 
bluetooth             209199  22 rfcomm,bnep,btusb
hid_generic            12493  0 
snd_hda_intel          33491  3 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30512  1 snd_seq_midi
microcode              22803  0 
mac80211              539908  1 iwlwifi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
cfg80211              206566  2 iwlwifi,mac80211
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78734  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
jmb38x_ms              17416  0 
lpc_ich                17061  0 
memstick               16554  1 jmb38x_ms
psmouse                95552  0 
serio_raw              13215  0 
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
mei                    40690  0 
usbhid                 46947  0 
hid                   100366  2 hid_generic,usbhid
i915                  520539  3 
ideapad_laptop         18086  0 
sparse_keymap          13890  1 ideapad_laptop
nouveau               895609  0 
ttm                    83595  1 nouveau
drm_kms_helper         49112  2 i915,nouveau
drm                   288670  6 i915,nouveau,ttm,drm_kms_helper
mac_hid                13205  0 
i2c_algo_bit           13413  2 i915,nouveau
mxm_wmi                12979  1 nouveau
video                  19335  2 i915,nouveau
wmi                    19070  2 nouveau,mxm_wmi
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
sdhci_pci              18616  0 
sdhci                  32645  1 sdhci_pci
```

dmesg (just a portion)

```
[ 2384.063568] wlan0: authenticate with 00:22:b0:44:6c:61
[ 2384.077980] wlan0: send auth to 00:22:b0:44:6c:61 (try 1/3)
[ 2384.081360] wlan0: authenticated
[ 2384.084778] wlan0: associate with 00:22:b0:44:6c:61 (try 1/3)
[ 2384.087446] wlan0: RX AssocResp from 00:22:b0:44:6c:61 (capab=0x431 status=0 aid=2)
[ 2384.089878] wlan0: associated
[ 2429.715001] wlan0: deauthenticating from 00:22:b0:44:6c:61 by local choice (reason=3)
[ 2429.758283] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 2429.758288] cfg80211: Restoring regulatory settings
[ 2429.758290] cfg80211: Calling CRDA to update world regulatory domain
[ 2429.762753] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 2429.762758] cfg80211: World regulatory domain updated:
[ 2429.762760] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2429.762763] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2429.762766] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2429.762768] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2429.762770] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2429.762773] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2433.038011] wlan0: authenticate with 00:22:b0:44:6c:61
[ 2433.049873] wlan0: send auth to 00:22:b0:44:6c:61 (try 1/3)
[ 2433.052241] wlan0: authenticated
[ 2433.055854] wlan0: associate with 00:22:b0:44:6c:61 (try 1/3)
[ 2433.059512] wlan0: RX AssocResp from 00:22:b0:44:6c:61 (capab=0x431 status=0 aid=2)
[ 2433.061892] wlan0: associated
[ 2478.640209] wlan0: deauthenticating from 00:22:b0:44:6c:61 by local choice (reason=3)
[ 2478.689080] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 2478.689089] cfg80211: Restoring regulatory settings
[ 2478.689096] cfg80211: Calling CRDA to update world regulatory domain
[ 2478.692711] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 2478.692713] cfg80211: World regulatory domain updated:
[ 2478.692713] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2478.692715] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2478.692716] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2478.692717] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2478.692717] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2478.692718] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2704.946116] wlan0: authenticate with 00:22:b0:44:6c:61
[ 2704.954083] wlan0: send auth to 00:22:b0:44:6c:61 (try 1/3)
[ 2704.956587] wlan0: authenticated
[ 2704.958891] wlan0: associate with 00:22:b0:44:6c:61 (try 1/3)
[ 2704.961546] wlan0: RX AssocResp from 00:22:b0:44:6c:61 (capab=0x431 status=0 aid=2)
[ 2704.963869] wlan0: associated

```

lsb_release -d

```
Description:	Ubuntu-Secure-Remix 12.10 30nov2012

```

sudo lshw -C network
```
 *-network UNCLAIMED     
       description: Ethernet controller
       product: AR8161 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 08
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list
       configuration: latency=0
       resources: memory:d3600000-d363ffff ioport:2000(size=128)
  *-network
       description: Wireless interface
       product: Centrino Wireless-N 2200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: c4
       serial: 9c:4e:36:5b:4a:48
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.5.0-21-generic firmware=18.168.6.1 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:43 memory:d3500000-d3501fff

```

After searching around the forum I have found this.
[http://ubuntuforums.org/showthread.php?p=12206393](http://ubuntuforums.org/showthread.php?p=12206393)
and [http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller](http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller)

So I kind of have a chance to get it working but only after having a wireless connection.

Could you please change the prefix of this topic if it is not right? I think it would be better described as Ubuntu instead of 64 bits.

---

### Post by DjBuss on 2013-01-11
My problem was the wireless pass.

I tried what was in the links above to fix my Ethernet and Bluetooth.
I used this solution [http://ubuntuforums.org/showthread.php?p=12206393](http://ubuntuforums.org/showthread.php?p=12206393) because it used a newer version off the compat-wireless.

Please, someone has to mark it as solved or is it me the one to do it?

---

