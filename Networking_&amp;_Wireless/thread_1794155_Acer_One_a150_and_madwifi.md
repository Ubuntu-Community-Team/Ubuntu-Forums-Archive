---
title: "Acer One a150 and madwifi"
date: 2011-06-30
forum: Networking &amp; Wireless
---

### Post by Orlando84 on 2011-06-30
Hi all.
I've installed Ubuntu 10.10 netbook edition on Acer Aspire One a150.  Folllowed the instructions to setup madwifi. But there is a problem:  wicd says that there are no networks.
Ok, I'm giving you my settings and some system variables

```
lsmod
```Module                  Size  Used by
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_realtek   217980  1 
snd_hda_intel          22107  4 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  3 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
wlan_scan_sta          12012  1 
snd_rawmidi            17783  1 snd_seq_midi
ath_rate_sample        11424  1 
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
ath_pci               179564  0 
snd_timer              19067  2 snd_pcm,snd_seq
joydev                  8735  0 
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  291004  4 
drm_kms_helper         30200  1 i915
snd                    49006  16  snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,   snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,sn  d_seq_device
wlan                  220280  4 wlan_scan_sta,ath_rate_sample,ath_pci
drm                   168054  5 i915,drm_kms_helper
soundcore                880  1 snd
ath_hal               396940  3 ath_rate_sample,ath_pci
i2c_algo_bit            5168  1 i915
uvcvideo               55847  0 
videodev               43098  1 uvcvideo
psmouse                59033  0 
video                  18712  1 i915
serio_raw               4022  0 
led_class               2633  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
lp                      7342  0 
v4l1_compat            13359  2 uvcvideo,videodev
acerhdf                 6895  0 
output                  1883  1 video
parport                31492  3 parport_pc,ppdev,lp
intel_agp              26360  2 i915
agpgart                32011  2 drm,intel_agp
r8169                  36489  0 
mii                     4425  1 r8169
```

ifconfig
```ath0      Link encap:Ethernet  HWaddr 00:22:69:0d:88:fa  
          inet6 addr: fe80::222:69ff:fe0d:88fa/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:1e:68:ac:5f:72  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:feac:5f72/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21847 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12301 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32038578 (32.0 MB)  TX bytes:1021463 (1.0 MB)
          Interrupt:44 Base address:0x2000 

lo        Link encap:&#1051;&#1086;&#1082;&#1072;&#1083;&#1100;&#1085;&#1072;&#1103; &#1087;&#1077;&#1090;&#1083;&#1103; (Loopback)  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-22-69-0D-88-FA-30-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:409 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:0 (0.0 B)  TX bytes:25246 (25.2 KB)
          Interrupt:18 


```
iwlist ath0 scanning 
```ath0      No scan results
```

sudo lshw -C Network
```*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:ac:5f:72
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169  driverversion=2.3LK-NAPI duplex=full ip=192.168.0.101 latency=0 link=yes  multicast=yes port=MII speed=100MB/s
       resources: irq:44 ioport:3000(size=256) memory:51010000-51010fff memory:51000000-5100ffff memory:51020000-5103ffff
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:22:69:0d:88:fa
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 multicast=yes wireless=IEEE 802.11g
       resources: irq:18 memory:55200000-5520ffff

Any suggestions would be very useful for my problem.

---

### Post by chili555 on 2011-06-30
We love our Acers! Please post:```
rfkill list all
dmesg | grep -e acer -e dmi
```Thanks.

---

### Post by Orlando84 on 2011-07-01
```
rfkill list all
```
returned empty output, there's nothing


```
dmesg | grep -e acer -e dmi
```
[   16.998057] acerhdf: Acer Aspire One Fan driver, v.0.5.22
[   16.998068] acerhdf: Fan control off, to enable do:
[   16.998073] acerhdf: echo -n "enabled" > /sys/class/thermal/thermal_zone0/mode

```
lspci | grep ar5001
```
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

---

### Post by chili555 on 2011-07-01
> *-network
description: Wireless interface
product: AR5001 Wireless Network Adapter
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:03:00.0
logical name: wifi0
version: 01
serial: 00:22:69:0d:88:fa
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes [COLOR="Red"]driver=ath_pci[/COLOR] latency=0 multicast=yes wireless=IEEE 802.11g
resources: irq:18 memory:55200000-5520ffffIn my system, ath-pci is blacklisted. I don't know too much about Netbook Edition. Let's try an experiment. Please do:```
sudo rmmod -f ath-pci
sudo modprobe ath5k
```Network Manager is designed to disallow a wireless connection if you have wired, which you do. Please detach the ethernet cable and tell us if your wireless is working. If so, we can blacklist ath-pci and load ath5k automatically.

---

### Post by Orlando84 on 2011-07-03
In my blacklist.conf I've added the ath_pci, commented blacklisted ath5k and rebooted with disconnected eth0 - wicd is not founding airport connections. So I'm going to my guake terminal which screen by default is black (but  some tuning and he is perfectly goes LEFT and  takes me there HAHAHA). So then goes cat ```

cat /etc/network/interfaces
```
cat auto lo
iface lo inet loopback

This cat command tells there is no active wlan0 device.
What else can I do?

---

### Post by Orlando84 on 2011-07-03
> **chili555 said:**
> In my system, ath-pci is blacklisted. I don't know too much about Netbook Edition.
There is no by default ath_pci driver it comes with madwifi, which  I compiled with installed  kernel headers. So it  comes

---

### Post by chili555 on 2011-07-03
> This cat command tells there is no active wlan0 device.Not quite. It tells you that the manual method, /etc/network/interfaces, is not managing wlan0. It isn't because Wicd is.

Did ath5k load?```
lsmod | grep ath
```If not, load it:```
sudo modprobe ath5k
```Was an interface created?```
iwconfig
```Now does Wicd see your network?

We can tweak a setting or two and get ath5k to load automatically if that was the problem.

---

### Post by Orlando84 on 2011-07-04
Ok,
```
lsmod | grep ath
```
ath5k                 130051  0 
mac80211              231541  1 ath5k
ath                     8153  1 ath5k
cfg80211              144470  3 ath5k,mac80211,ath
led_class               2633  1 ath5k

```
iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

Notice, taht Power Management is off, so I tried ```
iwconfig wlan0 txpower  on
``` and it returned me empty string
```

iwlist wlan0 scanning 
```
wlan0     No scan results

If needed I'll give all dmesg  etc, if you want to watch

---

### Post by chili555 on 2011-07-04
> If needed I'll give all dmesg etc, if you want to watchLet's filter it:```
dmesg | grep -e ath -e wlan
```Thanks.

---

### Post by Orlando84 on 2011-07-05
> **chili555 said:**
> Let's filter it:```
dmesg | grep -e ath -e wlan
```Thanks.
```
dmesg | grep -e ath -e wlan
```
[    0.470999] device-mapper: multipath: version 1.1.1 loaded
[    0.471009] device-mapper: multipath round-robin: version 1.0.0 loaded
[   17.680811] ath5k 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   17.680837] ath5k 0000:03:00.0: setting latency timer to 64
[   17.680954] ath5k 0000:03:00.0: registered as 'phy0'
[   18.189500] ath: EEPROM regdomain: 0x65
[   18.189507] ath: EEPROM indicates we should expect a direct regpair map
[   18.189516] ath: Country alpha2 being used: 00
[   18.189521] ath: Regpair used: 0x65
[   18.707599] Registered led device: ath5k-phy0::rx
[   18.707657] Registered led device: ath5k-phy0::tx
[   18.707665] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   18.817783] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  503.429451] ath5k 0000:03:00.0: PCI INT A disabled
[  575.075598] ath5k 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  575.075625] ath5k 0000:03:00.0: setting latency timer to 64
[  575.075864] ath5k 0000:03:00.0: registered as 'phy0'
[  575.579292] ath: EEPROM regdomain: 0x65
[  575.579299] ath: EEPROM indicates we should expect a direct regpair map
[  575.579307] ath: Country alpha2 being used: 00
[  575.579311] ath: Regpair used: 0x65
[  575.584614] Registered led device: ath5k-phy0::rx
[  575.584691] Registered led device: ath5k-phy0::tx
[  575.584702] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[  575.636682] ADDRCONF(NETDEV_UP): wlan0: link is not ready

I've found this one thread, is  it true about acer-wmi? I haven't tried yet, want to know your opinion, if I get in another WEB thread [http://ubuntuforums.org/showthread.php?t=1469799&highlight=acer+madwifi](http://ubuntuforums.org/showthread.php?t=1469799&highlight=acer+madwifi)

---

### Post by chili555 on 2011-07-05
> I've found this one thread, is it true about acer-wmi? I haven't tried yet, want to know your opinion, if I get in another WEB thread [http://ubuntuforums.org/showthread.p...t=acer+madwifi](http://ubuntuforums.org/showthread.p...t=acer+madwifi)You certainly could try it. Generally, if you search the forum, acer-wmi *prevents* wireless from working and needs to be removed. In your case, acer-wmi was not loaded in lsmod, which surprised me. That's usually the first thing we check in Acers. I was also surprised that rfkill returned nothing. 

Do you have a wireless switch and an LED on your laptop? Do they work as expected? Open a terminal and do:```
sudo tail -f /var/log/syslog
```Leave it open as you manipulate the switch. Does the syslog show any recognition of the switch? 

Just in the way of a minor observation, I suspect many newbies find a not working wireless after install, install madwifi and then install ndiswrapper and go back to another operating system when, all along, the trouble was elsewhere.

I love a mystery!

---

### Post by Orlando84 on 2011-07-09
> **chili555 said:**
> You certainly could try it. Generally, if you search the forum, acer-wmi *prevents* wireless from working and needs to be removed. In your case, acer-wmi was not loaded in lsmod, which surprised me. That's usually the first thing we check in Acers. I was also surprised that rfkill returned nothing. 

Do you have a wireless switch and an LED on your laptop? Do they work as expected? Open a terminal and do:```
sudo tail -f /var/log/syslog
```Leave it open as you manipulate the switch. Does the syslog show any recognition of the switch? 

Just in the way of a minor observation, I suspect many newbies find a not working wireless after install, install madwifi and then install ndiswrapper and go back to another operating system when, all along, the trouble was elsewhere.

I love a mystery!

I've opened a terminal aqnd ran sudo tail -f /var/log/syslog and then moved the switch - nothing happens. Maybe windows is disabling power on the  wifi, and enables it only on  its own boot?

---

### Post by chili555 on 2011-07-09
> **Orlando84 said:**
> I've opened a terminal aqnd ran sudo tail -f /var/log/syslog and then moved the switch - nothing happens. Maybe windows is disabling power on the  wifi, and enables it only on  its own boot?I think it's a possibility. If so, the folks at Acer and the folks at Atheros should be very ashamed that they have knowingly engaged in anti-competitive behavior.

Let's try another approach. Do the same:> Open a terminal and do:
```
sudo tail -f /var/log/syslog
```

Leave it open as you manipulate the switch. Does the syslog show any recognition of the switch?
Now open a new terminal, leaving the first open, and do:```
sudo modprobe acer-wmi
```Now manipulate the button and see if there is either any complaint about acer-wmi or any recognition of key presses.

---

### Post by Orlando84 on 2011-07-23
Thank you, chili555 for your answeres, but the netbook doesn't belong to me, so I had only two weeks to setup Ubuntu on it with dualboot in pair with WinXP.
You know, the most interesting, that I had devided the HDD into 3 partitions (WinXP [C], Work[D], Linux). And the D partition wasn't formatted, so I have formatted it under the WinXP and next time grub was hanging with errors. So I've booted from LiveUSB (Ubuntu Netbook) and fixed. BUT!!! The first thoughts was that my work on Ubuntu for two weeks has gone to the cat's under tale place. Oh, sometimes we make stupid mistakes and errors.
Chill, could you please watch for another my thread [Mod_proxy and ejabberd]("http://ubuntuforums.org/showthread.php?t=1810409&highlight=proxy") I've found the same case (the link in the thread) as mine but don't understand what I'm misconfiguring. Please, if you have time watch for it.
Best Regards, Alex

---

