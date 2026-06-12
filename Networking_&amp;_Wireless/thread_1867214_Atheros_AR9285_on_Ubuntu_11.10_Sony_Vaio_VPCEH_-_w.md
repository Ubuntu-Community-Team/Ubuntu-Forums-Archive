---
title: "Atheros AR9285 on Ubuntu 11.10 Sony Vaio VPCEH - wifi does't works"
date: 2011-10-22
forum: Networking &amp; Wireless
---

### Post by dixoncx on 2011-10-22
I am unable to use wireless network and bluetooth on my laptop..
Before in Ubuntu 11.04 is worked fine, but after a fresh install of Ubuntu 11.10 it doesn't works..:(

1) Machine Brand and Model (PC/Laptop):
```

SONY VAIO VPCEH15EN

```2 ) Wireless Brand, Model and Wireless Chipset:
```

dixon@dixon-vaio:~$ lspci -nn|grep "Atheros"
07:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)

```3 ) Checking interface:
```

dixon@dixon-vaio:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 90:00:4e:d2:24:5d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

dixon@dixon-vaio:~$ iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```4 ) Checking for modules:
```

dixon@dixon-vaio:~$ lsmod | grep "ath9k"
ath9k                 127538  0 
mac80211              310872  1 ath9k
ath9k_common           13839  1 ath9k
ath9k_hw              312866  2 ath9k,ath9k_common
ath                    24067  2 ath9k,ath9k_hw
cfg80211              199587  3 ath9k,mac80211,ath

```5 ) Kernel boot messages
```

dixon@dixon-vaio:~$ dmesg|grep "ath9k"
[    9.541422] ath9k 0000:07:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.541439] ath9k 0000:07:00.0: setting latency timer to 64
[    9.619352] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[    9.619965] Registered led device: ath9k-phy0

```6 ) Network configuration
```

dixon@dixon-vaio:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 90:00:4e:d2:24:5d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.0.0-12-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:92500000-9250ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:13:00.0
       logical name: eth0
       version: 06
       serial: 78:84:3c:e5:2c:e8
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:40 ioport:2000(size=256) memory:91404000-91404fff memory:91400000-91403fff

```7 ) Scan for networks:
```

dixon@dixon-vaio:~$ iwlist wlan0 scan
wlan0     No scan results

```8 ) Ubuntu Version:
```

dixon@dixon-vaio:~$ lsb_release -d
Description:    Ubuntu 11.10

```9 ) Kernel/architecture:
```

dixon@dixon-vaio:~$ uname -mr
3.0.0-12-generic x86_64

```10 ) Restarting the network:
```

dixon@dixon-vaio:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                                                                                         [ OK ]

```11) rfkill list: 
```

dixon@dixon-vaio:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: sony-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: sony-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```Any additional informations needed ?
Thanks in advance...

---

### Post by varunendra on 2011-10-24
Nothing seems suspicious to me in the outputs. Please try-
```
sudo ifdown wlan0
```
then
```
sudo ifup wlan0
```
Make sure "Enable Networking" and "Enable Wireless" are checked in Network Manager drop-down menu.

If this doesn't do the trick, please post complete output of **lsmod** and-
```
cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf
```

Just out of curiosity- was your 11.04 setup 64-bit too? Have you given wicd a try yet?

---

### Post by dixoncx on 2011-10-25
Here we go:

```

dixon@dixon-vaio:~$ sudo ifdown wlan0
ifdown: interface wlan0 not configured

``````

dixon@dixon-vaio:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.

``````

dixon@dixon-vaio:~$ lsmod
Module                  Size  Used by
ppp_deflate            13038  0 
zlib_deflate           27139  1 ppp_deflate
bsd_comp               12994  0 
ppp_async              17539  1 
crc_ccitt              12667  1 ppp_async
cdc_phonet             13042  0 
phonet                 30565  1 cdc_phonet
cdc_acm                22761  3 
bnep                   18436  2 
rfcomm                 47946  0 
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_conexant    62197  1 
psmouse                77381  0 
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
btusb                  18600  1 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
arc4                   12529  2 
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
bluetooth             166112  13 bnep,rfcomm,btusb
ath9k                 127538  0 
snd_seq_midi_event     14899  1 snd_seq_midi
mac80211              310872  1 ath9k
ath9k_common           13839  1 ath9k
ath9k_hw              312866  2 ath9k,ath9k_common
ath                    24067  2 ath9k,ath9k_hw
cfg80211              199587  3 ath9k,mac80211,ath
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
sony_laptop            45393  0 
serio_raw              13166  0 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
rts_pstor             445246  0 
i915                  566711  3 
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
snd                    68266  14  snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
mei                    41480  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
r8169                  52788  0 
ahci                   26002  2 
libahci                26861  1 ahci

``````

dixon@dixon-vaio:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


``````

dixon@dixon-vaio:~$ cat /etc/NetworkManager/NetworkManager.conf 
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

```

Currently, i can't check my wi-fi connectivity because there is no wi-fi connection in my home..
I will check it soon in my collage and inform u...

My Ubuntu version is **Ubuntu 11.10 x64** , [fresh install]..

---

### Post by dixoncx on 2011-10-25
Before going into wi-fi problem, lets fix bluetooth problem..
See the attached screenshot..

In applet, it shows [COLOR=Red]Bluetooth: On[/COLOR]
But in bluetooth menu, it shows: [COLOR=Red]Bluetooth is disabled[/COLOR]
I can't enable my bluetooth..
How can i fix it ?

Since bluetooth and wi-fi function is provided by same hardware,
either both will work properly or both will fail to work, is it?

---

### Post by chili555 on 2011-10-25
> Since bluetooth and wi-fi function is provided by same hardware,
either both will work properly or both will fail to work, is it?I'm not at all sure that's the case. For now, let's concentrate on wireless.

Dr. Chili has been called in on a consult. I don't normally barge in when my colleagues are progressing towards a logical solution. Let's have a peek at:```
dmesg | grep -e ath -e wlan
sudo cat /var/log/syslog | grep -e ath -e wlan -e etwork | tail -n25
```Thanks.

---

### Post by varunendra on 2011-10-25
> **chili555 said:**
> Dr. Chili has been called in on a consult. I don't normally barge in when my colleagues are progressing towards a logical solution. Let's have a peek at:```
dmesg | grep -e ath -e wlan
sudo cat /var/log/syslog | grep -e ath -e wlan -e etwork | tail -n25
```Thanks.
Thanks a lot for the kind response chili, I was (and still am) completely lost in this issue :)

---

### Post by dixoncx on 2011-10-25
Here:
```

dixon@dixon-vaio:~$ dmesg | grep -e ath -e wlan
[    6.676414] ath9k 0000:07:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.676429] ath9k 0000:07:00.0: setting latency timer to 64
[    6.725527] ath: EEPROM regdomain: 0x65
[    6.725530] ath: EEPROM indicates we should expect a direct regpair map
[    6.725534] ath: Country alpha2 being used: 00
[    6.725536] ath: Regpair used: 0x65
[    6.786127] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[    6.786650] Registered led device: ath9k-phy0
[   14.714381] ADDRCONF(NETDEV_UP): wlan0: link is not ready

``````

dixon@dixon-vaio:~$ sudo cat /var/log/syslog | grep -e ath -e wlan -e etwork | tail -n 25
[sudo] password for dixon: 
Oct 26 08:05:02 dixon-vaio NetworkManager[961]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) started...
Oct 26 08:05:02 dixon-vaio NetworkManager[961]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) complete.
Oct 26 08:05:03 dixon-vaio NetworkManager[961]: <info> WWAN now enabled by management service
Oct 26 08:05:05 dixon-vaio NetworkManager[961]: <info> Activation (ttyACM0) Stage 2 of 5 (Device Configure) scheduled...
Oct 26 08:05:05 dixon-vaio NetworkManager[961]: <info> Activation (ttyACM0) Stage 2 of 5 (Device Configure) starting...
Oct 26 08:05:05 dixon-vaio NetworkManager[961]: <info> (ttyACM0): device state change: prepare -> config (reason 'none') [40 50 0]
Oct 26 08:05:05 dixon-vaio NetworkManager[961]: <info> Activation (ttyACM0) Stage 2 of 5 (Device Configure) successful.
Oct 26 08:05:05 dixon-vaio NetworkManager[961]: <info> Activation (ttyACM0) Stage 3 of 5 (IP Configure Start) scheduled.
Oct 26 08:05:05 dixon-vaio NetworkManager[961]: <info> Activation (ttyACM0) Stage 2 of 5 (Device Configure) complete.
Oct 26 08:05:05 dixon-vaio NetworkManager[961]: <info> Activation (ttyACM0) Stage 3 of 5 (IP Configure Start) started...
Oct 26 08:05:05 dixon-vaio NetworkManager[961]: <info> (ttyACM0): device state change: config -> ip-config (reason 'none') [50 70 0]
Oct 26 08:05:05 dixon-vaio NetworkManager[961]: <info> starting PPP connection
Oct 26 08:05:05 dixon-vaio NetworkManager[961]: <info> pppd started with pid 2023
Oct 26 08:05:05 dixon-vaio NetworkManager[961]: <info> Activation (ttyACM0) Stage 3 of 5 (IP Configure Start) complete.
Oct 26 08:05:05 dixon-vaio NetworkManager[961]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Oct 26 08:05:05 dixon-vaio NetworkManager[961]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Oct 26 08:05:08 dixon-vaio NetworkManager[961]: <info> PPP manager(IP Config Get) reply received.
Oct 26 08:05:08 dixon-vaio NetworkManager[961]: <info> Activation (ttyACM0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Oct 26 08:05:08 dixon-vaio NetworkManager[961]: <info> Activation (ttyACM0) Stage 4 of 5 (IP4 Configure Get) started...
Oct 26 08:05:08 dixon-vaio NetworkManager[961]: <info> Activation (ttyACM0) Stage 5 of 5 (IP Configure Commit) started...
Oct 26 08:05:09 dixon-vaio NetworkManager[961]: <info> (ttyACM0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Oct 26 08:05:10 dixon-vaio NetworkManager[961]: <info> Policy set 'Airtel Default' (ppp0) as default for IPv4 routing and DNS.
Oct 26 08:05:10 dixon-vaio NetworkManager[961]: <info> Activation (ttyACM0) successful, device activated.
Oct 26 08:05:10 dixon-vaio NetworkManager[961]: <info> Activation (ttyACM0) Stage 5 of 5 (IP Configure Commit) complete.
Oct 26 08:05:10 dixon-vaio NetworkManager[961]: <info> Activation (ttyACM0) Stage 4 of 5 (IP4 Configure Get) complete.

```

Please note that am currently connected to internet through [COLOR=Red]**Mobile Broadband**[/COLOR] .
Thanks..

---

### Post by faldore on 2011-10-27
I have the same problem.
x64 11.10
my wireless worked before the upgrade and now it will not connect.

---

### Post by chili555 on 2011-10-30
> **dixoncx said:**
> 
Please note that am currently connected to internet through [COLOR=Red]**Mobile Broadband**[/COLOR] .
Thanks..We need to see what Network Manager is doing without the broadband connected. Please detach it, reboot and show us the result again.

---

### Post by kopiad on 2011-11-02
Have the same issue with my AR9285 wireless.
The issue is patly solved by switching the wireless router to not use 802.11 n, but only b and/or g. Ubuntu 11.04 worked fine with both 802.11 b, g and n.

---

### Post by JF382 on 2011-11-20
I also have this issue just with a different Sony Vaio Model. [http://ubuntuforums.org/showthread.php?p=11475048#post11475048](http://ubuntuforums.org/showthread.php?p=11475048#post11475048)

---

### Post by ontwowheels on 2011-12-02
Same issue, AR9285 on an HP laptop.  No fix?  I will post the output to those commands from my laptop tomorrow.

Hopefully someone can fix.  What I found will work:

I have black listed acer_wmi and acer-wmi, does not seem to do anything.  After I restart no wireless.  I do a rfkill unblock all, then go in to network settings.  Turn off air plane mode then turn wifi on and off a bunch of times and it finally starts to work.  It's a pain....does this info help?

---

