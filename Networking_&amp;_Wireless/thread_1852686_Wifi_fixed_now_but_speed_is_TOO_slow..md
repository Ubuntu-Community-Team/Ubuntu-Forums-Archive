---
title: "Wifi fixed now but speed is TOO slow."
date: 2011-09-30
forum: Networking &amp; Wireless
---

### Post by rishi_singh on 2011-09-30
Ubuntu forums page takes 15-30 seconds to load. Nothing downloading in background. Speed in win 7 is faster. I use ubuntu 11.04.

Can you help me to diagnose the problem. I use a realtek wifi card.

---

### Post by rishi_singh on 2011-10-02
Anyone ? Please let me know what the problem could be and how to find the cause.

---

### Post by papibe on 2011-10-02
I would recommend taking a look at this [thread]("http://ubuntuforums.org/showthread.php?t=872346"). Setting the right MTU may increase your browsing experience.

Regards.

---

### Post by rishi_singh on 2011-10-13
> **papibe said:**
> I would recommend taking a look at this [thread]("http://ubuntuforums.org/showthread.php?t=872346"). Setting the right MTU may increase your browsing experience.

Regards.

Sorry to reply so late. That does not work. I keep on getting a "bad packets...." error when i type the first command on that thread. I used lot of values in place of that 14XX, and always got the same error.

---

### Post by rishi_singh on 2011-10-13
I managed to make wifi work, but it is getting disconnected again and again. Please tell me the possible cause and how to make it work. My wifi is ok in win 7 though.
Also, the speed is too slow as i mentioned in another thread [http://ubuntuforums.org/showthread.php?p=11339842#post11339842](http://ubuntuforums.org/showthread.php?p=11339842#post11339842)


I use ubuntu 11.04 with win 7 dual boot and realtek wifi card.

---

### Post by cariboo on 2011-10-14
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by rishi_singh on 2011-10-14
> **cariboo907 said:**
> Please don't create multiple threads on the same subject, I have merged your two threads.

Ok, please help me to make my connection stable.

---

### Post by varunendra on 2011-10-14
Rishi,

Please enter the following commands in a terminal one-by-one and post back their outputs here:

(do a couple of minutes' browsing first)
```
ifconfig -a
iwconfig
sudo lshw -C network
lsmod
```

Please wrap each set of outputs in different [noparse]```
..and..
```[/noparse] tags (by clicking on the **#** symbol at the top of edit box, and pasting the output in between the generated tags) for better readability.

---

### Post by rishi_singh on 2011-10-14
> **varunendra said:**
> Rishi,

Please enter the following commands in a terminal one-by-one and post back their outputs here:

(do a couple of minutes' browsing first)
```
ifconfig -a
iwconfig
sudo lshw -C network
lsmod
```Please wrap each set of outputs in different [noparse]```
..and..
```[/noparse] tags (by clicking on the **#** symbol at the top of edit box, and pasting the output in between the generated tags) for better readability.


Browsed for 30 minutes. Connection dropped once so far.
[SIZE=3]**ONE IMPORTANT CONCERN I HAVE - **[/SIZE]I hope that this is not private information and that my privacy will be maintained. If any of the data below could harm my privacy, please let me know.

**ifconfig -a :**

eth0      Link encap:Ethernet  HWaddr f0:de:f1:8c:df:e9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:41 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1620 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1620 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:130770 (130.7 KB)  TX bytes:130770 (130.7 KB)

wlan0     Link encap:Ethernet  HWaddr 38:59:f9:e0:82:c2  
          inet addr:172.16.6.252  Bcast:172.16.15.255  Mask:255.255.240.0
          inet6 addr: fe80::3a59:f9ff:fee0:82c2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:42087 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27823 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:50751619 (50.7 MB)  TX bytes:2833710 (2.8 MB)

**iwconfig**

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Rishi"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:74:D2:CE:22   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:10   Missed beacon:0

**sudo lshw -C network**

*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: f0:de:f1:8c:df:e9
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:41 ioport:5000(size=256) memory:d0404000-d0404fff memory:d0400000-d0403fff
  *-network
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 01
       serial: 38:59:f9:e0:82:c2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=2.6.38-8-generic firmware=N/A ip=172.16.6.252 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 ioport:3000(size=256) memory:d1d00000-d1d03fff

**lsmod**

Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  1 
aes_generic            38023  1 aes_i586
rfcomm                 38125  8 
binfmt_misc            13213  1 
sco                    17779  2 
bnep                   17785  2 
l2cap                  48656  16 rfcomm,bnep
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     27479  1 
snd_hda_codec_conexant    43782  1 
joydev                 17322  0 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
i915                  450944  3 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
arc4                   12473  2 
btusb                  18160  2 
rtl8192ce             120897  0 
thinkpad_acpi          73750  0 
snd_timer              28659  2 snd_pcm,snd_seq
nvram                  14035  1 thinkpad_acpi
rtlwifi                78961  1 rtl8192ce
drm_kms_helper         40745  1 i915
bluetooth              65565  9 rfcomm,sco,bnep,l2cap,btusb
drm                   180037  4 i915,drm_kms_helper
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              257001  2 rtl8192ce,rtlwifi
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
cfg80211              156212  2 rtlwifi,mac80211
psmouse                73312  0 
snd                    55295  15 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,thinkpad_acpi,snd_timer,snd_seq_device
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
r8169                  42534  0 
sdhci_pci              13623  0 
sdhci                  22720  1 sdhci_pci
ahci                   21591  2 
libahci                25548  1 ahci

---

### Post by varunendra on 2011-10-14
> **rishi_singh said:**
> 
[SIZE=3]**ONE IMPORTANT CONCERN I HAVE - **[/SIZE]I hope that this is not private information and that my privacy will be maintained. If any of the data below could harm my privacy, please let me know. No, none of these outputs ever contain any sensitive data which may be exploited by anyone for privacy violation or any other kind of harm. Be assured on this one.

Onto your problem. Nothing seems wrong to me with your wireless connection. In fact, it is your ethernet interface whose details ring a bell to me:

> **rishi_singh said:**
> ```
**sudo lshw -C network**

*-network               
       description: Ethernet interface
       product: **RTL8111/8168B** PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
<snip>
       configuration: autonegotiation=on broadcast=yes **driver=r8169 **driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII **speed=10Mbit/s**
``` This hardware-driver combination is infamous for speed and packet-drop issues on wired connection. If you find yourself struggling with a wired connection too, this post may hopefully be helpful: [http://ubuntuforums.org/showthread.php?p=11053381&postcount=6](http://ubuntuforums.org/showthread.php?p=11053381&postcount=6)

However, I don't think it may interfere with the wireless connection. So I may have to do some research on your wireless issue before I can come up with something significantly helpful. For now, please post outputs of:
```
cat /etc/resolv.conf
ping -c 4 google.com
```**PS:**
Please wrap your outputs in [noparse]```
 and 
```[/noparse] tags as I told earlier.

---

