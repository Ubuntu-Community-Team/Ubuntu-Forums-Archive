---
title: "Activating WiFi on my laptop"
date: 2011-05-27
forum: Networking &amp; Wireless
---

### Post by utaku_ryukko on 2011-05-27
Hello,

My wife got a laptop from her son a few years ago, a Fujitsu Siemens Amilo Pro V3505.
Small precision, this laptop has a german keyboard as he's student there. I'm now using it with an USB keyboard (generic UK, 105 keys)
Until recently that laptop was my main PC and was using only an Ethernet connection, so no problem.
Now that I have a new desktop, I want to use it elsewhere in the house using the wifi connection.
The problem is I can't get that wifi LED working and WiCD says ther's no wifi network.
I looked 1st in the BIOS and the wifi is enabled.
Here are the results of some commands:
```
luc@luc-laptop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.2 LTS"
luc@luc-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 413c:3012 Dell Computer Corp. Optical Wheel Mouse
Bus 004 Device 002: ID 0603:00f2 Novatek Microelectronics Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
luc@luc-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 12)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
0a:06.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
0a:06.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
0a:06.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
0a:06.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
luc@luc-laptop:~$ lspci -nn | grep -i net
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller [11ab:4363] (rev 12)
04:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
luc@luc-laptop:~$ sudo lshw -C network
[sudo] password for luc: 
  *-network               
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:0a:e4:bb:4f:10
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A ip=192.168.1.65 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:26 memory:d2000000-d2003fff ioport:2000(size=256) memory:d0000000-d001ffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 02
       serial: 00:18:de:36:c2:cc
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:28 memory:d4000000-d4000fff
luc@luc-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_si3054     3396  1 
snd_hda_codec_realtek   203408  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
joydev                  8740  0 
ipt_REJECT              1928  1 
ipt_LOG                 4542  5 
xt_multiport            2378  1 
xt_limit                1382  7 
xt_tcpudp               2011  12 
ipt_addrtype            1631  4 
xt_state                1098  7 
snd_hda_intel          22069  2 
snd_hda_codec          74201  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
ip6table_filter         2343  1 
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
ip6_tables             11227  1 ip6table_filter
snd_pcm                70694  4 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
nf_nat_irc              1124  0 
nf_conntrack_irc        3332  1 nf_nat_irc
snd_seq_dummy           1338  0 
nf_nat_ftp              1836  0 
snd_seq_oss            26722  0 
nf_nat                 15735  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      10672  9 nf_nat
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
nf_conntrack_ftp        5381  1 nf_nat_ftp
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
pcmcia                 30784  0 
arc4                    1153  2 
nf_conntrack           61615  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iptable_filter          2271  1 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iwl3945                68727  0 
i915                  287810  2 
ip_tables               9991  1 iptable_filter
iwlcore               106050  1 iwl3945
snd                    54180  17 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         29329  1 i915
x_tables               14299  9 ipt_REJECT,ipt_LOG,xt_multiport,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6_tables,ip_tables
mac80211              205402  2 iwl3945,iwlcore
intel_agp              24375  2 i915
drm                   162345  3 i915,drm_kms_helper
yenta_socket           20408  1 
i2c_algo_bit            5028  1 i915
psmouse                63245  0 
sdhci_pci               5470  0 
rsrc_nonstatic         10015  1 yenta_socket
serio_raw               3978  0 
sdhci                  15462  1 sdhci_pci
led_class               2864  3 iwl3945,iwlcore,sdhci
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
cfg80211              126528  3 iwl3945,iwlcore,mac80211
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
video                  17375  1 i915
output                  1871  1 video
agpgart                31724  2 intel_agp,drm
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67096  1 usbhid
sky2                   40807  0 
ahci                   32200  2 
luc@luc-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
luc@luc-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0a:e4:bb:4f:10  
          inet adr:192.168.1.65  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::20a:e4ff:febb:4f10/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:19364 erreurs:0 :0 overruns:0 frame:0
          TX packets:10754 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:28491247 (28.4 MB) Octets transmis:864974 (864.9 KB)
          Interruption:16 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:8 erreurs:0 :0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:480 (480.0 B) Octets transmis:480 (480.0 B)

luc@luc-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

luc@luc-laptop:~$ uname -r -m
2.6.32-31-generic i686
luc@luc-laptop:~$  cat /etc/network/interfaces
auto lo
iface lo inet loopback

``````
luc@luc-laptop:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
luc@luc-laptop:~$ sudo rfkill unblock all
luc@luc-laptop:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```Before I install Ubuntu on this laptop, it was using Win XP and the wifi was activated by pressing Fn+F10 or by pressing a key that is above the main keyboard. None of these keys are now working. And when with XP, the LED was turning Orange, not green, but I'm not sure that was normal or not.

Anybody can help me having that wireless working?

Thanks in advance

---

### Post by Joe of loath on 2011-05-27
That wifi card should be supported out of the box, what's the output of ifconfig -a and iwconfig?

---

### Post by utaku_ryukko on 2011-05-27
These results should be on my initial post but I will give them again.
```
luc@luc-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0a:e4:bb:4f:10  
          inet adr:192.168.1.65  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::20a:e4ff:febb:4f10/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:21053 erreurs:0 :0 overruns:0 frame:0
          TX packets:12237 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:29849199 (29.8 MB) Octets transmis:1173883 (1.1 MB)
          Interruption:16 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:8 erreurs:0 :0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:480 (480.0 B) Octets transmis:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:18:de:36:c2:cc  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)

luc@luc-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   [COLOR=Red]Tx-Power=off[/COLOR]   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
         [COLOR=Red] Power Management:off[/COLOR]

```Something is telling me that it's hardware related and not a problem with Ubuntu itself.
I read somewhere that these keys for activating/desactivating the wifi need to be reprogrammed :confused:

---

### Post by chili555 on 2011-05-27
Please try:```
sudo modprobe acer-wmi
```Any change in the wireless LED now? Next do:```
sudo rfkill unblock all
```If it's not working, let us see:```
dmesg | tail -n15
```Thanks.

---

### Post by utaku_ryukko on 2011-05-27
```
luc@luc-laptop:~$ sudo modprobe acer-wmi
FATAL: Error inserting acer_wmi (/lib/modules/2.6.32-31-generic/kernel/drivers/platform/x86/acer-wmi.ko): No such device
```No change at all for the LED. I went to see with synaptic and no packet called acer-wmi can be found. The only one I see is acerhk-source

```
luc@luc-laptop:~$ sudo rfkill unblock all
luc@luc-laptop:~$ dmesg \tail -n15
klogctl: Opération non permise
``` Sorry, it's in french, says Operation not allowed

---

### Post by Joe of loath on 2011-05-27
What do you get when you try sudo ifconfig wlan0 up?

---

### Post by chili555 on 2011-05-27
> **utaku_ryukko said:**
> ```
luc@luc-laptop:~$ sudo modprobe acer-wmi
FATAL: Error inserting acer_wmi (/lib/modules/2.6.32-31-generic/kernel/drivers/platform/x86/acer-wmi.ko): No such device
```No change at all for the LED. I went to see with synaptic and no packet called acer-wmi can be found. The only one I see is acerhk-source

```
luc@luc-laptop:~$ sudo rfkill unblock all
luc@luc-laptop:~$ dmesg \tail -n15
klogctl: Opération non permise
``` Sorry, it's in french, says Operation not allowedOui, je comprende un petit peu de francais as you can see by all my mistakes! The symbol is | not \. On my US keyboard they are on the same key.

I'm afraid acer-wmi is not available in 10.04 LTS. I had no way to know that since I am on 11.04; sorry for the confusion.

I suggest you go back to Synaptic and install acerhk-source. Then open a terminal and do:```
sudo su
apt-get install build-essential
cd /usr/src/
tar -xjvf acerhk.tar.bz2
cd modules/acerhk
make -d
make install -d
modprobe acerhk
exit
```I haven't tried this and I'm not running 10.04 LTS so what I have suggested is courtesy of a forum search. Post back any errors or problems.

---

### Post by utaku_ryukko on 2011-05-27
```
luc@luc-laptop:~$ sudo ifconfig wlan0 up
[sudo] password for luc: 
SIOCSIFFLAGS: Erreur inconnue 132
luc@luc-laptop:~$ dmesg | tail -n15
[   60.444618] atkbd.c: Unknown key pressed (translated set 2, code 0xd6 on isa0060/serio0).
[   60.444628] atkbd.c: Use 'setkeycodes e056 <keycode>' to make it known.
[   61.435063] atkbd.c: Unknown key pressed (translated set 2, code 0xd6 on isa0060/serio0).
[   61.435072] atkbd.c: Use 'setkeycodes e056 <keycode>' to make it known.
[  689.402785] CE: hpet increasing min_delta_ns to 15000 nsec
[  707.331363] [UFW BLOCK] IN=eth0 OUT= MAC=00:0a:e4:bb:4f:10:00:1f:9f:3e:47:f2:08:00 SRC=92.226.91.18 DST=192.168.1.65 LEN=93 TOS=0x00 PREC=0x00 TTL=48 ID=0 DF PROTO=UDP SPT=49394 DPT=6881 LEN=73 
[  994.977349] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[  994.977359] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[  994.977366] pcmcia: see http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html for details.
[ 3555.314549] [UFW BLOCK] IN=eth0 OUT= MAC=00:0a:e4:bb:4f:10:00:1f:9f:3e:47:f2:08:00 SRC=84.108.230.27 DST=192.168.1.65 LEN=95 TOS=0x00 PREC=0x00 TTL=111 ID=39203 PROTO=UDP SPT=55003 DPT=6881 LEN=75 
[ 3776.352437] [UFW BLOCK] IN=eth0 OUT= MAC=00:0a:e4:bb:4f:10:00:1f:9f:3e:47:f2:08:00 SRC=88.135.211.241 DST=192.168.1.65 LEN=93 TOS=0x00 PREC=0x00 TTL=108 ID=10428 PROTO=UDP SPT=4597 DPT=6881 LEN=73 
[ 5803.962534] [UFW BLOCK] IN=eth0 OUT= MAC=00:0a:e4:bb:4f:10:00:1f:9f:3e:47:f2:08:00 SRC=64.30.121.101 DST=192.168.1.65 LEN=93 TOS=0x00 PREC=0x00 TTL=40 ID=0 DF PROTO=UDP SPT=6881 DPT=6881 LEN=73 
[ 5853.820645] acer-wmi: Acer Laptop ACPI-WMI Extras
[ 5853.820681] acer-wmi: No or unsupported WMI interface, unable to load
[ 9683.615361] nautilus[1668]: segfault at c ip 0811d8a1 sp bfbf0c30 error 4 in nautilus[8048000+196000]

```

Maybe I can try having acer-wmi by having the backports?

I tried to install through the procedure. Didn't work :(

---

### Post by chili555 on 2011-05-27
> I tried to install through the procedure. Didn't workWhat didn't work? Did you get an error along the way? 

One of the parameters of acer-wmi is a series of laptop. In other words, one can do:```
sudo modprobe acer-wmi force_series=xyz
```I have seen several instances on Google of forcing the series for Fujitsu laptops; now we have to figure out yours.

I'm Googling...

---

### Post by chili555 on 2011-05-27
Here's a start:  [http://www.futuredesktop.com/linux/wireless_in_linux_with_acerhk_driver.txt](http://www.futuredesktop.com/linux/wireless_in_linux_with_acerhk_driver.txt)> # This works with Fujitsu Siemens Amilo Li 1718 and Amilo Pro V3505.
options acerhk force_series=6805 autowlan=1Woo hoo! Let's try:```
sudo rmmod -f acer-wmi
```It may say it's not loaded, that's OK.```
sudo modprobe acer-wmi force_series=6805
```I don't know if the parameters are the same between acerhk and acer-wmi; dmesg will tell us:```
dmesg | tail -n15
```Thanks.

---

### Post by chili555 on 2011-05-27
Here is another interesting thing:  [http://kernelnewbies.org/Linux_2_6_28](http://kernelnewbies.org/Linux_2_6_28)> 11.4. Input

    Add driver for USB VoIP phones with CM109 chipset (commit)

    ati_remote2 - add autosuspend support (commit), add loadable keymap support (commit)

    bf54x-keys - add power management support (commit)

    psmouse - add OLPC touchpad driver (commit), add support for Elantech touchpads (commit)

    [COLOR="Red"]wistron - add support for Fujitsu-Siemens Amilo Pro v3505[/COLOR] (commit)It's not evident to me exactly what wistron does, but it sounds promising:> $ modinfo wistron_btns 
filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/input/misc/wistron_btns.ko
version:        0.3
license:        GPL v2
description:    Wistron [COLOR="Red"]laptop button driver[/COLOR]
author:         Miloslav Trmac <mitr@volny.cz>
srcversion:     AF8D9C3A27B38B6CA2BA1B1
depends:        input-polldev,sparse-keymap
vermagic:       2.6.38-8-generic SMP mod_unload modversions 686 
parm:           force:Load even if computer is not in database (bool)
parm:           keymap:Keymap name, if it can't be autodetected [generic, 1557/MS2141] (charp)
Once again, dmesg will tell us:```
sudo modprobe wistron_btns
dmesg | tail -n15
```

---

### Post by utaku_ryukko on 2011-05-27
```
luc@luc-laptop:~$ sudo rmmod -f acer-wmi
ERROR: Removing 'acer_wmi': No such file or directory
luc@luc-laptop:~$ sudo modprobe acer-wmi force_series=6805
FATAL: Error inserting acer_wmi (/lib/modules/2.6.32-31-generic/kernel/drivers/platform/x86/acer-wmi.ko): No such device
luc@luc-laptop:~$ dmesg | tail -n15
[   61.435063] atkbd.c: Unknown key pressed (translated set 2, code 0xd6 on isa0060/serio0).
[   61.435072] atkbd.c: Use 'setkeycodes e056 <keycode>' to make it known.
[  689.402785] CE: hpet increasing min_delta_ns to 15000 nsec
[  707.331363] [UFW BLOCK] IN=eth0 OUT= MAC=00:0a:e4:bb:4f:10:00:1f:9f:3e:47:f2:08:00 SRC=92.226.91.18 DST=192.168.1.65 LEN=93 TOS=0x00 PREC=0x00 TTL=48 ID=0 DF PROTO=UDP SPT=49394 DPT=6881 LEN=73 
[  994.977349] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[  994.977359] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[  994.977366] pcmcia: see http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html for details.
[ 3555.314549] [UFW BLOCK] IN=eth0 OUT= MAC=00:0a:e4:bb:4f:10:00:1f:9f:3e:47:f2:08:00 SRC=84.108.230.27 DST=192.168.1.65 LEN=95 TOS=0x00 PREC=0x00 TTL=111 ID=39203 PROTO=UDP SPT=55003 DPT=6881 LEN=75 
[ 3776.352437] [UFW BLOCK] IN=eth0 OUT= MAC=00:0a:e4:bb:4f:10:00:1f:9f:3e:47:f2:08:00 SRC=88.135.211.241 DST=192.168.1.65 LEN=93 TOS=0x00 PREC=0x00 TTL=108 ID=10428 PROTO=UDP SPT=4597 DPT=6881 LEN=73 
[ 5803.962534] [UFW BLOCK] IN=eth0 OUT= MAC=00:0a:e4:bb:4f:10:00:1f:9f:3e:47:f2:08:00 SRC=64.30.121.101 DST=192.168.1.65 LEN=93 TOS=0x00 PREC=0x00 TTL=40 ID=0 DF PROTO=UDP SPT=6881 DPT=6881 LEN=73 
[ 5853.820645] acer-wmi: Acer Laptop ACPI-WMI Extras
[ 5853.820681] acer-wmi: No or unsupported WMI interface, unable to load
[ 9683.615361] nautilus[1668]: segfault at c ip 0811d8a1 sp bfbf0c30 error 4 in nautilus[8048000+196000]
[17952.064893] acer-wmi: Acer Laptop ACPI-WMI Extras
[17952.064909] acer-wmi: No or unsupported WMI interface, unable to load
```
Seems that it's impossible to have that module acer-wmi :(

```
luc@luc-laptop:~$ sudo modprobe wistron_btns
luc@luc-laptop:~$ dmesg | tail -n15
[  689.402785] CE: hpet increasing min_delta_ns to 15000 nsec
[  707.331363] [UFW BLOCK] IN=eth0 OUT= MAC=00:0a:e4:bb:4f:10:00:1f:9f:3e:47:f2:08:00 SRC=92.226.91.18 DST=192.168.1.65 LEN=93 TOS=0x00 PREC=0x00 TTL=48 ID=0 DF PROTO=UDP SPT=49394 DPT=6881 LEN=73 
[  994.977349] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[  994.977359] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[  994.977366] pcmcia: see http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html for details.
[ 3555.314549] [UFW BLOCK] IN=eth0 OUT= MAC=00:0a:e4:bb:4f:10:00:1f:9f:3e:47:f2:08:00 SRC=84.108.230.27 DST=192.168.1.65 LEN=95 TOS=0x00 PREC=0x00 TTL=111 ID=39203 PROTO=UDP SPT=55003 DPT=6881 LEN=75 
[ 3776.352437] [UFW BLOCK] IN=eth0 OUT= MAC=00:0a:e4:bb:4f:10:00:1f:9f:3e:47:f2:08:00 SRC=88.135.211.241 DST=192.168.1.65 LEN=93 TOS=0x00 PREC=0x00 TTL=108 ID=10428 PROTO=UDP SPT=4597 DPT=6881 LEN=73 
[ 5803.962534] [UFW BLOCK] IN=eth0 OUT= MAC=00:0a:e4:bb:4f:10:00:1f:9f:3e:47:f2:08:00 SRC=64.30.121.101 DST=192.168.1.65 LEN=93 TOS=0x00 PREC=0x00 TTL=40 ID=0 DF PROTO=UDP SPT=6881 DPT=6881 LEN=73 
[ 5853.820645] acer-wmi: Acer Laptop ACPI-WMI Extras
[ 5853.820681] acer-wmi: No or unsupported WMI interface, unable to load
[ 9683.615361] nautilus[1668]: segfault at c ip 0811d8a1 sp bfbf0c30 error 4 in nautilus[8048000+196000]
[17952.064893] acer-wmi: Acer Laptop ACPI-WMI Extras
[17952.064909] acer-wmi: No or unsupported WMI interface, unable to load
[18286.592197] wistron_btns: BIOS signature found at c00f5b10, entry point 000FDD20
[18286.604659] input: Wistron laptop buttons as /devices/platform/wistron-bios/input/input11
```


Thanks all for the help. It's really appreciated

---

### Post by chili555 on 2011-05-27
> [18286.592197] wistron_btns: [COLOR="Red"]BIOS signature found at c00f5b10, [/COLOR]entry point 000FDD20
[18286.604659] input: Wistron laptop buttons as /devices/platform/wistron-bios/input/input11This is starting to look a bit promising. Now do:```
sudo tail -f /var/log/syslog
```Leave the terminal open and manipulate the wireless button and let's see what the system reports. You can kill the 'tail' command with Ctrl+c.

---

### Post by utaku_ryukko on 2011-05-27
Woohoo, we're on good track. By pressing the Wiriless button, the LED is now Orange :)
Wicd was able to see the local wifi networks available.
And I was able to connect to mine, after entering my WPA key :)

Now, my question is, will that stay that way, or will I have to do some manipulation each time I will start/reboot the laptop?

Thank you very much :D

---

### Post by chili555 on 2011-05-27
Woo hoo, indeed! I'm glad it's working and I learned something. The searchers will find it, too. Great work!

Here's how we get it to load on boot permanently:```
sudo su
echo wistron_btns >> /etc/modules
exit
```You should be all set.

Have fun!

---

### Post by utaku_ryukko on 2011-05-27
It works :D

Thank you all for your support

---

