---
title: "Networking problem, wired and wireless TP Link and Buffalo"
date: 2012-02-04
forum: Networking &amp; Wireless
---

### Post by magicguitarman on 2012-02-04
Hi guys,

Not a total beginner but getting really confused and frustrated today!

Having a massive problem getting the internet to work correctly on my home build. I was donated a TP Link TL-WN951N which isn't supported. Given up on that and moved onto another donated thing (I have no spare money at all) A Buffalo USB 2.0 WLAN adaptor. The wired connection behaves in the same way.

The problem is that every time I load a website 9 out of 10 times my browser crashes. Firefox shuts down totally and Chromium shows me the oops page. I am currently using Chromium because I can hit refresh a lot and get back to the page in the end without restarting the browser. I have also tried Opera without any difference. This has happened with Fedora, Ubuntu, OpenSUZE and now Ubuntu Studio. Hardware must be at fault, but I don't know if there is a way out of this :(

I don't know what to include with this post other than the info from the guide thread, so ask if I need to post anything else. Here goes and thanks in advance!

```
harry@HarryPC:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 004 Device 002: ID 043d:00c8 Lexmark International, Inc. Printing Support
Bus 005 Device 003: ID 045e:00b4 Microsoft Corp. 
Bus 005 Device 004: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 001 Device 003: ID 0411:00da MelCo., Inc. WLI-U2-KG54L 802.11bg [ZyDAS ZD1211B]
harry@HarryPC:~$ 
```

```
harry@HarryPC:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 8c:89:a5:60:fb:a1  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::8e89:a5ff:fe60:fba1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40300 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25195 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:53081358 (53.0 MB)  TX bytes:2583614 (2.5 MB)
          Interrupt:51 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:780 (780.0 B)  TX bytes:780 (780.0 B)

wlan0     Link encap:Ethernet  HWaddr f4:ec:38:ab:5d:6a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan1     Link encap:Ethernet  HWaddr 00:16:01:b3:a9:a7  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:1ff:feb3:a9a7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3861 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3667 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3258615 (3.2 MB)  TX bytes:579774 (579.7 KB)

```

```
harry@HarryPC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan1     IEEE 802.11bg  ESSID:"virgin broadband"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 1C:AF:F7:05:C4:5B   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/100  Signal level=51/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:126   Missed beacon:0
```

```
lsmod
Module                  Size  Used by
zd1211rw               59482  0 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
vesafb                 13809  1 
binfmt_misc            17540  1 
joydev                 17693  0 
usbhid                 47198  0 
hid                    95463  1 usbhid
snd_emu10k1_synth      17241  0 
snd_emux_synth         42825  1 snd_emu10k1_synth
snd_seq_virmidi        13525  1 snd_emux_synth
snd_seq_midi_emul      17854  1 snd_emux_synth
arc4                   12529  4 
k10temp                13166  0 
ath9k                 127538  0 
edac_core              53746  0 
edac_mce_amd           23709  0 
mac80211              462092  2 zd1211rw,ath9k
snd_hda_codec_hdmi     32040  1 
ath9k_common           13839  1 ath9k
ath9k_hw              312914  2 ath9k,ath9k_common
ath                    24067  2 ath9k,ath9k_hw
cfg80211              199630  4 zd1211rw,ath9k,mac80211,ath
psmouse                73882  0 
snd_emu10k1           157353  4 snd_emu10k1_synth
serio_raw              13166  0 
snd_hda_intel          33390  2 
snd_hda_codec         104931  2 snd_hda_codec_hdmi,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  2 snd_seq_virmidi,snd_seq_midi
sp5100_tco             13791  0 
snd_rawmidi            30547  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
i2c_piix4              13301  0 
snd_ac97_codec        134826  1 snd_emu10k1
snd_seq                61896  5 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi,snd_seq_midi_event
ac97_bus               12730  1 snd_ac97_codec
fglrx                2928969  80 
snd_pcm                96714  5 snd_hda_codec_hdmi,snd_emu10k1,snd_hda_intel,snd_hda_codec,snd_ac97_codec
snd_seq_device         14540  5 snd_emu10k1_synth,snd_emu10k1,snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              29991  3 snd_emu10k1,snd_seq,snd_pcm
snd_util_mem           14074  2 snd_emux_synth,snd_emu10k1
snd_hwdep              13668  3 snd_emux_synth,snd_emu10k1,snd_hda_codec
snd                    68266  23 snd_emux_synth,snd_seq_virmidi,snd_hda_codec_hdmi,snd_emu10k1,snd_hda_intel,snd_hda_codec,snd_rawmidi,snd_ac97_codec,snd_seq,snd_pcm,snd_seq_device,snd_timer,snd_hwdep
shpchp                 37345  0 
soundcore              12680  1 snd
snd_page_alloc         18529  3 snd_emu10k1,snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
pata_atiixp            13164  0 
r8169                  52788  0 
pata_jmicron           12747  0 
ahci                   26002  2 
libahci                26861  1 ahci
xhci_hcd               82820  0 

```

**Dmsg is far too big to post, advice as to how to trim down?**

```
harry@HarryPC:~$ sudo lshw -C network
[sudo] password for harry: 
  *-network               
       description: Wireless interface
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:05:05.0
       logical name: wlan0
       version: 01
       serial: f4:ec:38:ab:5d:6a
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.0.0-15-generic firmware=N/A latency=168 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:20 memory:fe8e0000-fe8effff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 03
       serial: 8c:89:a5:60:fb:a1
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-1.fw ip=192.168.1.4 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:51 ioport:e800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff memory:fe9e0000-fe9fffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:2
       logical name: wlan1
       serial: 00:16:01:b3:a9:a7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=zd1211rw driverversion=3.0.0-15-generic firmware=4725 ip=192.168.1.5 link=yes multicast=yes wireless=IEEE 802.11bg
harry@HarryPC:~$ 

```

```
harry@HarryPC:~$ lsb_release -d
Description:	Ubuntu 11.10
harry@HarryPC:~$ 

```

```
harry@HarryPC:~$ uname -mr
3.0.0-15-generic x86_64
harry@HarryPC:~$ 

```

```
harry@HarryPC:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]

```

Sorry for all that. Thanks in advance again!

---

### Post by magicguitarman on 2012-02-05
No one able to help at all? I guess bumping is frowned on but I don't know what else to do.

---

### Post by magicguitarman on 2012-02-05
Update:

Dmesg reports the following:

```
[  157.752211] show_signal_msg: 24 callbacks suppressed
[  157.752215] chromium-browse[1990]: segfault at 44a5fb7ccc4 ip 0000092ecda06e28 sp 00007fff8fa5a1e8 error 4
[  160.989382] chromium-browse[2035]: segfault at ffffffff8d0ffeff ip 00003735cc0c8746 sp 00007fff8fa59fb8 error 6
[  163.184595] chromium-browse[2043]: segfault at ffffffff8d0ffeff ip 0000124048fbf546 sp 00007fff8fa59fb8 error 6
[  165.401241] chromium-browse[2051] general protection ip:1b77ec575404 sp:7fff8fa59fb8 error:0
```

---

