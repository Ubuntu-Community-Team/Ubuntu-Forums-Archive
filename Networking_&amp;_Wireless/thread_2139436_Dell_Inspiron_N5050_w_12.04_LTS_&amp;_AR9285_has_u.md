---
title: "Dell Inspiron N5050 w/ 12.04 LTS &amp; AR9285 has unstable wireless"
date: 2013-04-26
forum: Networking &amp; Wireless
---

### Post by Compynerd255 on 2013-04-26
Hello All,

A few days ago, I've noticed that my wireless has suddenly stopped working properly on my computer. It lasts a few hours, survives a few on/offs with the wireless switch (Fn + F2), but then it simply does not work when I turn on my wireless again. The wireless icon in the top right indicates that the wireless is disabled, and when I attempt to toggle Airplane Mode in the network manager in Settings, that message changes to "device not ready". In order to get it working again, I have to dual-boot back into Windows (where it isn't working there either when I boot it up), and disable/reenable the device driver in there using Device Manager. Not even a cold shutdown does it any good.

I am in the bad state right now, connected to my Ethernet for Internet. This is infeasible for me because my school does not have wired Internet virtually anywhere.

I should also note that I also installed Dansguardian and Squid 3 on my computer a few days ago and did not experience the problem before this. But I can't help but feel uneasy about the state of my laptop since I have to fiddle around with it in Windows as well to get it to work. And disconnecting Dansguardian and Squid did not restore my wireless Internet, as far as I can tell. I'll have to see what happens if I uninstall them.

Does anyone have any ideas? Thank you very much for your help.

Here's my output from "lspci -v | grep Wireless":

```
09:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Dell Wireless 1702 802.11bgn Half-size Mini PCIe Card [AR9002WB-1NGCD]

```

Here's my output from "ifconfig -a":
```
eth0      Link encap:Ethernet  HWaddr 24:b6:fd:55:85:20  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::26b6:fdff:fe55:8520/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7909 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6090 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7166476 (7.1 MB)  TX bytes:1162325 (1.1 MB)
          Interrupt:42 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:49573 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49573 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:33101028 (33.1 MB)  TX bytes:33101028 (33.1 MB)

wlan0     Link encap:Ethernet  HWaddr 84:4b:f5:1b:4e:43  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:89 errors:0 dropped:0 overruns:0 frame:0
          TX packets:143 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17185 (17.1 KB)  TX bytes:23232 (23.2 KB)
```
> With just plain "ifconfig", wlan0 is absent if the wireless is not working. If it is,
the two outputs are identical.

"iwconfig":
```
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

"lsmod" (I believe the wireless module is ath9k):
```
ath9k                 132428  0 
mac80211              506862  1 ath9k
ath9k_common           14053  1 ath9k
ath9k_hw              411239  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
cfg80211              205774  3 ath9k,mac80211,ath
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
joydev                 17693  0 
rfcomm                 47604  12 
parport_pc             32866  0 
ppdev                  17113  0 
bnep                   18281  2 
binfmt_misc            17540  1 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
ath3k                  12961  0 
btusb                  18332  2 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
bluetooth             180153  24 rfcomm,bnep,ath3k,btusb
snd_hda_intel          33719  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
ums_realtek            18248  0 
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
dell_laptop            18119  0 
dcdbas                 14490  1 dell_laptop
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
arc4                   12529  2 
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                97485  0 
serio_raw              13211  0 
wmi                    19256  1 dell_wmi
snd                    79041  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13253  0 
i915                  477748  3 
drm_kms_helper         46978  1 i915
drm                   241971  4 i915,drm_kms_helper
soundcore              15091  1 snd
i2c_algo_bit           13423  1 i915
video                  19651  1 i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41616  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usb_storage            49243  2 ums_realtek
r8169                  62154  0 
```

"dmesg | grep ath9k":
```
[   19.326239] ath9k 0000:09:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   19.326255] ath9k 0000:09:00.0: setting latency timer to 64
[   19.391574] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   19.392889] Registered led device: ath9k-phy0
[ 2888.781733] ath9k 0000:09:00.0: PCI INT A disabled
[ 2888.781761] ath9k: Driver unloaded
[ 2895.898109] ath9k 0000:09:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 2895.898126] ath9k 0000:09:00.0: setting latency timer to 64
[ 2895.950254] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[ 2895.951561] Registered led device: ath9k-phy0
[ 5738.854787] ath9k 0000:09:00.0: PCI INT A disabled
[ 5738.854841] ath9k: Driver unloaded
[ 5745.472367] ath9k 0000:09:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 5745.472383] ath9k 0000:09:00.0: setting latency timer to 64
[ 5745.523796] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[ 5745.524199] Registered led device: ath9k-phy0
```

"sudo lshw -C network":
```
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 05
       serial: 24:b6:fd:55:85:20
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.1.10 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:e000(size=256) memory:f1104000-f1104fff memory:f1100000-f1103fff
  *-network DISABLED
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: wlan0
       version: 01
       serial: 84:4b:f5:1b:4e:43
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-40-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:f7d00000-f7d0ffff
```

"uname -mr":
```
3.2.0-40-generic x86_64
```

EDIT: Bypassing the proxies and disabling DansGuardian and Squid allowed the wireless to work again (without booting into Windows) but as soon as I turn it off using the hardware switch, it won't turn back on again. I still think this is some sort of software problem. So I don't think DansGuardian and Squid were meddling with my Internet that badly.

EDIT 2: After fixing broken packages in Recovery Mode, my wireless still won't turn on, and my tty terminals are now being flooded with information like this (which was also retrieved from "dmesg | grep ath"):
[CODE][  115.190064] ath: Chip reset failed
[  115.191098] ath: Unable to reset channel, reset status -22
[  115.192155] ath: Unable to set channel
[  115.259601] ath: Failed to stop TX DMA, queues=0x10f!
[  115.273814] ath: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[  115.274854] ath: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  115.392651] ath: Chip reset failed
[  115.393683] ath: Unable to reset channel (2412 MHz), reset status -22
[  115.836211] ath: Failed to wakeup in 500us
[  120.823331] ath: Failed to wakeup in 500us
[  125.826253] ath: Failed to wakeup in 500us
[  130.813437] ath: Failed to wakeup in 500us[CODE]

---

### Post by Compynerd255 on 2013-04-29
Update: I fiddled around with resetting some services and the like, and now my Wifi works again *just as long as I don't disable it via the hardware switch*. As much as I'm glad that I can keep my Wifi working, the fact that I can't disable it to save battery worries me. Can I safely do the same thing with Airplane mode?

---

### Post by Compynerd255 on 2013-05-08
Another update: now it doesn't work at all. I tried restarting the computer, and I was able to see the device there and that it appears to work, but it isn't finding any networks. And, worse, any fiddling I do on Windows is yielding the same symptoms. This means that my wireless Internet does not work at all. Does anyone have any ideas?

EDIT: Well, whaddaya know? It works again. All I had to do was put the laptop to sleep while I was in Windows. I should probably go back into Ubuntu and turn the SUSPEND_MODULES off.

---

