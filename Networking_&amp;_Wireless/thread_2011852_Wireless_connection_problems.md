---
title: "Wireless connection problems"
date: 2012-06-27
forum: Networking &amp; Wireless
---

### Post by pauloz on 2012-06-27
Greetings

I recently installed Ubuntu 12.04 on an Acer Aspire 3500, but I'm having problems with the wireless connection. The Acer is pretty old and I sometimes wonder if I'm flogging a dead horse, however I want to explore all avenues before getting rid of it.

I went to the Help menu (Wireless network troubleshooter) and as a result I've posted the following results:

                                   [COLOR=#3c3c3c][FONT=monospace]nm-tool command produces the following:[/FONT][/COLOR]
  

  [COLOR=#3c3c3c][FONT=monospace]WEP Encryption:  yes [/FONT][/COLOR]
  [COLOR=#3c3c3c]    [FONT=monospace]WPA Encryption:  yes [/FONT][/COLOR]
  [COLOR=#3c3c3c]    [FONT=monospace]WPA2 Encryption: yes [/FONT][/COLOR]
  
  [COLOR=#3c3c3c]  [FONT=monospace]Wireless Access Points  [/FONT][/COLOR]
  [COLOR=#3c3c3c][FONT=monospace] - Device: eth0 ----------------------------------------------------------------- [/FONT][/COLOR]
  [COLOR=#3c3c3c]  [FONT=monospace]Type:              Wired [/FONT][/COLOR]
  [COLOR=#3c3c3c]  [FONT=monospace]Driver:            sis900 [/FONT][/COLOR]
  [COLOR=#3c3c3c]  [FONT=monospace]State:             unavailable [/FONT][/COLOR]
  [COLOR=#3c3c3c]  [FONT=monospace]Default:           no [/FONT][/COLOR]
  [COLOR=#3c3c3c]  [FONT=monospace]HW Address:        00:C0:9F:9C:14:DF [/FONT][/COLOR]
  [COLOR=#3c3c3c][FONT=monospace]   Capabilities: [/FONT][/COLOR]
  [COLOR=#3c3c3c]    [FONT=monospace]Carrier Detect:  yes [/FONT][/COLOR]
  [COLOR=#3c3c3c]    [FONT=monospace]Speed:           100 Mb/s [/FONT][/COLOR]
  [COLOR=#3c3c3c][FONT=monospace]   Wired Properties [/FONT][/COLOR]
  [COLOR=#3c3c3c]    [FONT=monospace]Carrier:         off [/FONT][/COLOR]
  

  [COLOR=#3c3c3c][FONT=monospace]sudo lshw -C network command produces the following:[/FONT][/COLOR]
  

  [COLOR=#3c3c3c][FONT=monospace]capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation [/FONT][/COLOR]
  [COLOR=#3c3c3c]       [FONT=monospace]configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=173 link=no maxlatency=11 mingnt=52 multicast=yes port=MII speed=10Mbit/s [/FONT][/COLOR]
  [COLOR=#3c3c3c]       [FONT=monospace]resources: irq:19 ioport:2000(size=256) memory:e2003000-e2003fff memory:20020000-2003ffff [/FONT][/COLOR]
  [COLOR=#3c3c3c]  [FONT=monospace]*-network:1 DISABLED [/FONT][/COLOR]
  [COLOR=#3c3c3c]       [FONT=monospace]description: Wireless interface [/FONT][/COLOR]
  [COLOR=#3c3c3c]       [FONT=monospace]product: AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg] [/FONT][/COLOR]
  [COLOR=#3c3c3c]       [FONT=monospace]vendor: Atheros Communications Inc. [/FONT][/COLOR]
  [COLOR=#3c3c3c]       [FONT=monospace]physical id: b [/FONT][/COLOR]
  [COLOR=#3c3c3c]       [FONT=monospace]bus info: pci@0000:00:0b.0 [/FONT][/COLOR]
  [COLOR=#3c3c3c]       [FONT=monospace]logical name: wlan0 [/FONT][/COLOR]
  [COLOR=#3c3c3c]       [FONT=monospace]version: 01 [/FONT][/COLOR]
  [COLOR=#3c3c3c]       [FONT=monospace]serial: 00:0e:9b:cf:e0:0f [/FONT][/COLOR]
  [COLOR=#3c3c3c]       [FONT=monospace]width: 32 bits [/FONT][/COLOR]
  [COLOR=#3c3c3c]       [FONT=monospace]clock: 33MHz [/FONT][/COLOR]
  [COLOR=#3c3c3c]       [FONT=monospace]capabilities: pm bus_master cap_list ethernet physical wireless [/FONT][/COLOR]
  [COLOR=#3c3c3c]       [FONT=monospace]configuration: broadcast=yes driver=ath5k driverversion=3.2.0-25-generic-pae firmware=N/A latency=168 link=no maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg [/FONT][/COLOR]
  [COLOR=#3c3c3c]       [FONT=monospace]resources: irq:17 memory:e2010000-e201ffff [/FONT][/COLOR]
  
I'm guessing here but because the unit previously had Windows XP, there may be a problem with Ubuntu not recognising the driver properly.

I get conflicting messages on the menu bar - sometimes the wireless connection is enabled when the ethernet connection is disabled but I still can't connect. When I do connect the ethernet connection, the Enable Wireless option is greyed out and I get another greyed out message, "Wireless is disabled by hardware switch". I know there are CTRL commands that can be used to enable but I don't know what to use.

Any help that can be given is appreciated.

pauloz

---

### Post by wildmanne39 on 2012-06-27
Hi, please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by pauloz on 2012-06-28
OK thanks - here are the results:

graham@graham-Aspire-3500:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux graham-Aspire-3500 3.2.0-25-generic-pae #40-Ubuntu SMP Wed May 23 22:11:24 UTC 2012 i686 i686 i386 GNU/Linux


00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet [1039:0900] (rev 91)
    Subsystem: Acer Incorporated [ALI] Device [1025:0082]
    Kernel driver in use: sis900
--
00:0b.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg] [168c:001a] (rev 01)
    Subsystem: AMBIT Microsystem Corp. Device [1468:0418]
    Kernel driver in use: ath5k


lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.



0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no



Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39553  1 
rfcomm                 38139  0 
bnep                   17830  2 
vesafb                 13516  1 
parport_pc             32114  0 
bluetooth             158438  10 rfcomm,bnep
ppdev                  12849  0 
snd_intel8x0           33455  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
arc4                   12473  2 
snd_seq_midi_event     14475  1 snd_seq_midi
ath5k                 145127  0 
ath                    19387  1 ath5k
mac80211              436455  1 ath5k
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                72919  0 
cfg80211              178679  3 ath5k,ath,mac80211
serio_raw              13027  0 
snd                    62064  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia                 39791  0 
joydev                 17393  0 
yenta_socket           27465  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
shpchp                 32325  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_intel8x0,snd_pcm
i2c_sis96x             12743  0 
mac_hid                13077  0 
sis_agp                13165  1 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
sis900                 22729  0 

Thanks again

pauloz

---

### Post by wildmanne39 on 2012-06-28
Hi, please post the output of:
```
sudo cat /var/log/syslog | grep -e ath -e firmware -e wlan | tail -n45
```
also is there anymore information from:
```
nm-tool
```
Thanks

---

### Post by pauloz on 2012-06-28
Here's the output:

graham@graham-Aspire-3500:~$ sudo cat /var/log/syslog | grep -e ath -e firmware -e wlan | tail -n45
[sudo] password for graham: 
Jun 28 17:17:05 graham-Aspire-3500 NetworkManager[745]: <info> (wlan0): using nl80211 for WiFi device control
Jun 28 17:17:05 graham-Aspire-3500 NetworkManager[745]: <warn> (wlan0): driver supports Access Point (AP) mode
Jun 28 17:17:05 graham-Aspire-3500 NetworkManager[745]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath5k' ifindex: 3)
Jun 28 17:17:05 graham-Aspire-3500 NetworkManager[745]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jun 28 17:17:05 graham-Aspire-3500 NetworkManager[745]: <info> (wlan0): now managed
Jun 28 17:17:05 graham-Aspire-3500 NetworkManager[745]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 28 17:17:05 graham-Aspire-3500 NetworkManager[745]: <info> (wlan0): bringing up device.
Jun 28 17:17:05 graham-Aspire-3500 NetworkManager[745]: <info> (wlan0): preparing device.
Jun 28 17:17:05 graham-Aspire-3500 NetworkManager[745]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jun 28 17:17:05 graham-Aspire-3500 kernel: [   25.240189] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 28 17:17:05 graham-Aspire-3500 kernel: [   25.240931] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 28 17:17:05 graham-Aspire-3500 NetworkManager[745]: <info> (wlan0): supplicant interface state: starting -> ready
Jun 28 17:17:05 graham-Aspire-3500 NetworkManager[745]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jun 28 17:17:05 graham-Aspire-3500 NetworkManager[745]: <info> (wlan0): supplicant interface state: ready -> inactive
Jun 28 17:19:57 graham-Aspire-3500 kernel: [   21.618956] ath5k 0000:00:0b.0: enabling device (0010 -> 0012)
Jun 28 17:19:57 graham-Aspire-3500 kernel: [   21.618992] ath5k 0000:00:0b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun 28 17:19:57 graham-Aspire-3500 kernel: [   21.619078] ath5k 0000:00:0b.0: registered as 'phy0'
Jun 28 17:19:57 graham-Aspire-3500 kernel: [   22.330302] ath: EEPROM regdomain: 0x63
Jun 28 17:19:57 graham-Aspire-3500 kernel: [   22.330306] ath: EEPROM indicates we should expect a direct regpair map
Jun 28 17:19:57 graham-Aspire-3500 kernel: [   22.330312] ath: Country alpha2 being used: 00
Jun 28 17:19:57 graham-Aspire-3500 kernel: [   22.330315] ath: Regpair used: 0x63
Jun 28 17:19:57 graham-Aspire-3500 kernel: [   22.370278] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
Jun 28 17:19:59 graham-Aspire-3500 NetworkManager[773]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:04.0/net/eth0, iface: eth0)
Jun 28 17:19:59 graham-Aspire-3500 NetworkManager[773]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:04.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jun 28 17:19:59 graham-Aspire-3500 NetworkManager[773]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:0b.0/net/wlan0, iface: wlan0)
Jun 28 17:19:59 graham-Aspire-3500 NetworkManager[773]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:0b.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jun 28 17:19:59 graham-Aspire-3500 NetworkManager[773]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jun 28 17:19:59 graham-Aspire-3500 NetworkManager[773]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jun 28 17:19:59 graham-Aspire-3500 kernel: [   25.784370] type=1400 audit(1340869799.600:19): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=783 comm="apparmor_parser"
Jun 28 17:19:59 graham-Aspire-3500 kernel: [   25.785274] type=1400 audit(1340869799.600:20): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=783 comm="apparmor_parser"
Jun 28 17:19:59 graham-Aspire-3500 NetworkManager[773]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jun 28 17:19:59 graham-Aspire-3500 NetworkManager[773]: <info> (wlan0): using nl80211 for WiFi device control
Jun 28 17:19:59 graham-Aspire-3500 NetworkManager[773]: <warn> (wlan0): driver supports Access Point (AP) mode
Jun 28 17:19:59 graham-Aspire-3500 NetworkManager[773]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath5k' ifindex: 3)
Jun 28 17:19:59 graham-Aspire-3500 NetworkManager[773]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jun 28 17:19:59 graham-Aspire-3500 NetworkManager[773]: <info> (wlan0): now managed
Jun 28 17:19:59 graham-Aspire-3500 NetworkManager[773]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 28 17:19:59 graham-Aspire-3500 NetworkManager[773]: <info> (wlan0): bringing up device.
Jun 28 17:20:00 graham-Aspire-3500 NetworkManager[773]: <info> (wlan0): preparing device.
Jun 28 17:20:00 graham-Aspire-3500 kernel: [   26.194335] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 28 17:20:00 graham-Aspire-3500 NetworkManager[773]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jun 28 17:20:00 graham-Aspire-3500 kernel: [   26.196484] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 28 17:20:00 graham-Aspire-3500 NetworkManager[773]: <info> (wlan0): supplicant interface state: starting -> ready
Jun 28 17:20:00 graham-Aspire-3500 NetworkManager[773]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jun 28 17:20:00 graham-Aspire-3500 NetworkManager[773]: <info> (wlan0): supplicant interface state: ready -> inactive

Result of nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        00:0E:9B:CF:E0:0F

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            sis900
  State:             connected
  Default:           yes
  HW Address:        00:C0:9F:9C:14:DF

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.76
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254


graham@graham-Aspire-3500:~$ sudo rfkill unblock wifi

Thanks again.

pauloz

---

### Post by wildmanne39 on 2012-06-28
Hi, open network manager and make sure it is set to infrastructure.
Please run:
```
echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```
Keep your wired connection unplug while trying to connect by wireless.
Please post the output of:
```
sudo iwlist scan
cat /var/lib/NetworkManager/NetworkManager.state
cat /etc/network/interfaces
ps aux | grep nm-apple
```
Thanks

---

### Post by pauloz on 2012-06-28
Hello again 

Network Manager is set to infrastructure - here is the output of all the commands you asked for. Appreciate your time.

graham@graham-Aspire-3500:~$ echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
[sudo] password for graham: 
options ath5k nohwcrypt=1
graham@graham-Aspire-3500:~$ sudo modprobe -rfv ath5k
rmmod /lib/modules/3.2.0-25-generic-pae/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
rmmod /lib/modules/3.2.0-25-generic-pae/kernel/drivers/net/wireless/ath/ath.ko
rmmod /lib/modules/3.2.0-25-generic-pae/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.2.0-25-generic-pae/kernel/net/wireless/cfg80211.ko
graham@graham-Aspire-3500:~$ sudo modprobe -v ath5k
insmod /lib/modules/3.2.0-25-generic-pae/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.2.0-25-generic-pae/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.2.0-25-generic-pae/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.2.0-25-generic-pae/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko nohwcrypt=1
graham@graham-Aspire-3500:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

eth0      Interface doesn't support scanning.

graham@graham-Aspire-3500:~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
graham@graham-Aspire-3500:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

graham@graham-Aspire-3500:~$ ps aux | grep nm-apple
graham    1412  0.0  1.6 108568  7224 ?        Sl   08:32   0:00 nm-applet
graham    2548  0.0  0.1   4376   808 pts/1    S+   09:24   0:00 grep --color=auto nm-apple
graham@graham-Aspire-3500:~$

---

### Post by wildmanne39 on 2012-06-28
Hi, did you run these commands one line at a time?
```
echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```
there should only be output for those commands if there was an error, it was meant to add a driver parameter not for information.

Please post the contents of:
```
gksudo gedit /etc/modprobe.d/ath5k.conf
```
Thanks

---

### Post by pauloz on 2012-06-28
Hi - yes I did run those command lines one at a time, so it looks like I received 3 error messages, which you should see in my previous post.

The results of the command you asked me to do is

options ath5k nohwcrypt=1

This appeared in a separate screen.

Thanks again.

---

### Post by wildmanne39 on 2012-06-30
Hi, everything from the commands look good I forgot that the -v option was in the command so it would show the progress even without errors.

Please post the output of:
```
nm-tool
dmesg | egrep 'ath|firm|radio|switch|wlan0'
lsmod | grep ath
ndiswrapper -l
```
Thanks

---

### Post by pauloz on 2012-06-30
Hi again 

Here is the output. I did all this with the wired connection unplugged. Also, I have not installed 'ndiswrapper' until I hear back from you. With thanks.


graham@graham-Aspire-3500:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        00:0E:9B:CF:E0:0F

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sis900
  State:             unavailable
  Default:           no
  HW Address:        00:C0:9F:9C:14:DF

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off


graham@graham-Aspire-3500:~$ dmesg | egrep 'ath|firm|radio|switch|wlan0'
[    0.009019] SMP alternatives: switching to UP code
[   21.366286] ath5k 0000:00:0b.0: enabling device (0010 -> 0012)
[   21.366325] ath5k 0000:00:0b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   21.366411] ath5k 0000:00:0b.0: registered as 'phy0'
[   22.909509] ath: EEPROM regdomain: 0x63
[   22.909515] ath: EEPROM indicates we should expect a direct regpair map
[   22.909522] ath: Country alpha2 being used: 00
[   22.909524] ath: Regpair used: 0x63
[   23.031417] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[   23.699706] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.700990] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.191018] Console: switching to colour frame buffer device 80x30
[  530.016068] Modules linked in: usbhid hid vesafb arc4 joydev snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm pcmcia snd_seq_midi ath5k ath mac80211 snd_rawmidi snd_seq_midi_event psmouse serio_raw cfg80211 yenta_socket pcmcia_rsrc snd_seq pcmcia_core parport_pc rfcomm bnep ppdev bluetooth snd_timer snd_seq_device snd soundcore snd_page_alloc mac_hid shpchp i2c_sis96x sis_agp lp parport sis900
[  530.016138]  [<c105a682>] warn_slowpath_common+0x72/0xa0
[  530.016153]  [<c105a753>] warn_slowpath_fmt+0x33/0x40
graham@graham-Aspire-3500:~$ 
graham@graham-Aspire-3500:~$ 
graham@graham-Aspire-3500:~$ 
graham@graham-Aspire-3500:~$ lsmod | grep ath
ath5k                 145127  0 
ath                    19387  1 ath5k
mac80211              436455  1 ath5k
cfg80211              178679  3 ath5k,ath,mac80211
graham@graham-Aspire-3500:~$ 
graham@graham-Aspire-3500:~$ 
graham@graham-Aspire-3500:~$ 
graham@graham-Aspire-3500:~$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
graham@graham-Aspire-3500:~$

---

### Post by wildmanne39 on 2012-06-30
Hi, do not install ndiswrapper I was just checking to make sure it was not installed.

Go to the network icon in the top right corner of the screen, is enable wireless checked?
if so go into your router and make sure your wireless is turned on and at 100 percent if it is then unplug the router completely for about five minutes then plug it back in or reboot it.
Thanks

---

### Post by pauloz on 2012-06-30
Hi - this is where it gets to be confusing for me. 'Enable Wireless' is checked but at the same time it is displaying 'Wireless Networks' greyed out and 'disconnected' greyed out as well. This is the problem I had in the first place. I unplugged my router completely for over 5 minutes, but nothing has changed. There's nothing wrong with my router because the wireless works fine on my ASUS netbook and desktop.
It looks like there may be a problem with the hardware in the Acer - if that's the case, it's time to get rid of it.
Thanks for your time and effort over the past few days.
All the best.

---

### Post by wildmanne39 on 2012-06-30
Hi, please show:
```
lsmod | grep wmi
rfkill list all
```
Thanks

---

### Post by pauloz on 2012-07-01
OK - here's the output

graham@graham-Aspire-3500:~$ lsmod | grep wmi
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
graham@graham-Aspire-3500:~$ 
graham@graham-Aspire-3500:~$ 
graham@graham-Aspire-3500:~$ 
graham@graham-Aspire-3500:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
graham@graham-Aspire-3500:~$ 

Thanks

---

### Post by wildmanne39 on 2012-07-01
Hi, please post the output of:
```
cat /var/lib/NetworkManager/NetworkManager.state
cat /etc/resolv.conf
cat /etc/network/interfaces
cat /etc/udev/rules.d/70-persistent-net.rules
ls -al /lib/firmware/ath
```
[COLOR="Red"]by clicking on new reply and click # then paste the information between the brackets.[/COLOR]
Thank you
Thanks

---

### Post by pauloz on 2012-07-01
Hi - I haven't been pasting the info between the brackets because I keep getting the words CODE and HTML coming up between brackets and then I strike formatting problems, so I'm just doing a complete paste from terminal. Hope that's OK.

[IMG]http://ubuntuforums.org/data:image/jpg;base64,PCFET0NUWVBFIEhUTUwgUFVCTElDICItLy9XM0MvL0RURCBIVE1MIDQuMCBUcmFuc2l0aW9uYWwvL0VOIj4KPEhUTUw+CjxIRUFEPgoJPE1FVEEgSFRUUC1FUVVJVj0iQ09OVEVOVC1UWVBFIiBDT05URU5UPSJ0ZXh0L2h0bWw7IGNoYXJzZXQ9dXRmLTgiPgoJPFRJVExFPjwvVElUTEU+Cgk8TUVUQSBOQU1FPSJHRU5FUkFUT1IiIENPTlRFTlQ9IkxpYnJlT2ZmaWNlIDMuNSAgKExpbnV4KSI+Cgk8U1RZTEUgVFlQRT0idGV4dC9jc3MiPgoJPCEtLQoJCUBwYWdlIHsgbWFyZ2luOiAyY20gfQoJCVAgeyBtYXJnaW4tYm90dG9tOiAwLjIxY20gfQoJLS0+Cgk8L1NUWUxFPgo8L0hFQUQ+CjxCT0RZIExBTkc9ImVuLUFVIiBESVI9IkxUUiI+CjxQIFNUWUxFPSJtYXJnaW4tYm90dG9tOiAwY207IGZvbnQtdmFyaWFudDogbm9ybWFsOyBmb250LXN0eWxlOiBub3JtYWw7IGZvbnQtd2VpZ2h0OiBub3JtYWw7IGxpbmUtaGVpZ2h0OiAwLjY0Y207IHdpZG93czogMjsgb3JwaGFuczogMiI+CjxGT05UIENPTE9SPSIjM2MzYzNjIj48Rk9OVCBGQUNFPSJtb25vc3BhY2UiPltDT0RFXVsvQ09ERV1bSFRNTF1bL0hUTUxdPC9GT05UPjwvRk9OVD48L1A+CjwvQk9EWT4KPC9IVE1MPgA=[/IMG] Here's the complete paste with the wired connection unplugged:

graham@graham-Aspire-3500:~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
graham@graham-Aspire-3500:~$ 
graham@graham-Aspire-3500:~$ 
graham@graham-Aspire-3500:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
graham@graham-Aspire-3500:~$ 
graham@graham-Aspire-3500:~$ 
graham@graham-Aspire-3500:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

graham@graham-Aspire-3500:~$ 
graham@graham-Aspire-3500:~$ 
graham@graham-Aspire-3500:~$ cat /etc/udev/rules.d/70-persistent-net.rules
# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.

# PCI device 0x1039:/sys/devices/pci0000:00/0000:00:04.0 (sis900)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:c0:9f:9c:14:df", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:0b.0 (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0e:9b:cf:e0:0f", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
graham@graham-Aspire-3500:~$ 
graham@graham-Aspire-3500:~$ 
graham@graham-Aspire-3500:~$ ls -al /lib/firmware/ath
ls: cannot access /lib/firmware/ath: No such file or directory
graham@graham-Aspire-3500:~$ 

Thanks again.

---

### Post by wildmanne39 on 2012-07-02
Hi, please post the output of:
```
ls /lib/firmware
```
Thanks

---

### Post by pauloz on 2012-07-02
Hi again - here's the output

graham@graham-Aspire-3500:~$ ls /lib/firmware
3.2.0-23-generic-pae         libertas
3.2.0-25-generic-pae         matrox
3.2.0-26-generic-pae         mrvl
3com                         mts_cdma.fw
acenic                       mts_edge.fw
adaptec                      mts_gsm.fw
advansys                     mts_mt9234mu.fw
agere_ap_fw.bin              mts_mt9234zba.fw
agere_sta_fw.bin             mwl8335_duplex.fw
aic94xx-seq.fw               mwl8k
ar3k                         myri10ge_ethp_z8e.dat
ar7010_1_1.fw                myri10ge_eth_z8e.dat
ar7010.fw                    myri10ge_rss_ethp_z8e.dat
ar9170-1.fw                  myri10ge_rss_eth_z8e.dat
ar9170-2.fw                  myricom
ar9170.fw                    NPE-B
ar9271.fw                    NPE-C
asihpi                       ositech
ath3k-1.fw                   phanfw.bin
ath6k                        ql2100_fw.bin
atmel_at76c502_3com.bin      ql2200_fw.bin
atmel_at76c502.bin           ql2300_fw.bin
atmel_at76c502d.bin          ql2322_fw.bin
atmel_at76c502e.bin          ql2400_fw.bin
atmel_at76c504_2958.bin      ql2500_fw.bin
atmel_at76c504a_2958.bin     qlogic
atmel_at76c504.bin           r128
atmel_at76c506.bin           radeon
atmsar11.fw                  rt2561.bin
av7110                       rt2561s.bin
bnx2                         rt2661.bin
bnx2x                        rt2860.bin
brcm                         rt2870.bin
carl9170-1.fw                rt3070.bin
cis                          rt3071.bin
cpia2                        rt3090.bin
cxgb3                        rt73.bin
cxgb4                        RTL8192E
dabusb                       RTL8192SE
dsp56k                       rtl_nic
dvb-fe-xc5000-1.6.114.fw     rtlwifi
dvb-usb-dib0700-1.20.fw      s2250.fw
dvb-usb-terratec-h5-drxk.fw  s2250_loader.fw
e100                         sb16
ea                           scripts
edgeport                     slicoss
emi26                        sun
emi62                        sxg
ene-ub6250                   TDA7706_OM_v2.5.1_boot.txt
ess                          TDA7706_OM_v3.0.2_boot.txt
f2255usb.bin                 tehuti
GPL-3                        ti_3410.fw
hp                           ti_5052.fw
htc_7010.fw                  ti-connectivity
htc_9271.fw                  tigon
i2400m-fw-usb-1.4.sbcf       tlg2300_firmware.bin
i2400m-fw-usb-1.5.sbcf       tr_smctr.bin
i6050-fw-usb-1.5.sbcf        ttusb-budget
intelliport2.bin             ueagle-atm
ipw2100-1.3.fw               usbdux
ipw2100-1.3-i.fw             usbduxfast_firmware.bin
ipw2100-1.3-p.fw             usbdux_firmware.bin
ipw2200-bss.fw               usbduxsigma_firmware.bin
ipw2200-ibss.fw              v4l-cx231xx-avcore-01.fw
ipw2200-sniffer.fw           v4l-cx23418-apu.fw
isci                         v4l-cx23418-cpu.fw
iwlwifi-1000-5.ucode         v4l-cx23418-dig.fw
iwlwifi-100-5.ucode          v4l-cx2341x-dec.fw
iwlwifi-105-6.ucode          v4l-cx2341x-enc.fw
iwlwifi-135-6.ucode          v4l-cx2341x-init.mpg
iwlwifi-2000-6.ucode         v4l-cx23885-avcore-01.fw
iwlwifi-2030-6.ucode         v4l-cx23885-enc.fw
iwlwifi-3945-2.ucode         v4l-cx25840.fw
iwlwifi-4965-2.ucode         v4l-pvrusb2-24xxx-01.fw
iwlwifi-5000-5.ucode         v4l-pvrusb2-29xxx-01.fw
iwlwifi-5150-2.ucode         vicam
iwlwifi-6000-4.ucode         vntwusb.fw
iwlwifi-6000g2a-5.ucode      vxge
iwlwifi-6000g2b-6.ucode      WHENCE.ubuntu
iwlwifi-6050-5.ucode         whiteheat.fw
kaweth                       whiteheat_loader.fw
keyspan                      yam
keyspan_pda                  yamaha
korg                         zd1201-ap.fw
lbtf_usb.bin                 zd1201.fw
lgs8g75.fw                   zd1211
graham@graham-Aspire-3500:~$ 

Cheers

---

### Post by wildmanne39 on 2012-07-02
Hi, please do:
```
sudo apt-get install --reinstall linux-firmware-nonfree
```
Reboot
Thanks

---

### Post by gordintoronto on 2012-07-02
That wireless adapter should "just work." Have you ever set up a wireless connection in Ubuntu?

I don't understand "sometimes the wireless connection is enabled when the ethernet connection is disabled but I still can't connect."

If you know the ssid, encryption type and password for your router, it should be a piece of cake.

---

### Post by pauloz on 2012-07-02
Hi again - unfortunately still no dice. I get the same messages as before i.e. when I unplug the wired connection to reboot, "Enable Wireless" is checked but I get a contradictory message that is greyed out displaying "wireless is disabled".
When I plug the wired connection, "Enable Wireless" is greyed out and a message "wireless is disabled by hardware switch" is also greyed out.
I think it's time to bite the bullet and kiss the Acer goodbye.

Thanks.

---

### Post by wildmanne39 on 2012-07-02
Hi, did you run the command from post 20? did you reboot?

Please try:
```
sudo rmmod -f acer-wmi
```
if it does not connect post the output of:
```
ls /lib/firmware
nm-tool
```
if it does work we will need to make it permanent so do not reboot.
Thanks

---

### Post by pauloz on 2012-07-02
Yes - I ran the command from post 20 and yes, I rebooted. Here are the latest results you've asked for - thanks:

graham@graham-Aspire-3500:~$ sudo rmmod -f acer-wmi
[sudo] password for graham: 
ERROR: Removing 'acer_wmi': No such file or directory
graham@graham-Aspire-3500:~$ 
graham@graham-Aspire-3500:~$ 
graham@graham-Aspire-3500:~$ ls /lib/firmware
3.2.0-23-generic-pae         iwlwifi-2030-6.ucode
3.2.0-25-generic-pae         iwlwifi-3945-2.ucode
3.2.0-26-generic-pae         iwlwifi-4965-2.ucode
3com                         iwlwifi-5000-5.ucode
acenic                       iwlwifi-5150-2.ucode
adaptec                      iwlwifi-6000-4.ucode
advansys                     iwlwifi-6000g2a-5.ucode
agere_ap_fw.bin              iwlwifi-6000g2b-6.ucode
agere_sta_fw.bin             iwlwifi-6050-5.ucode
aic94xx-seq.fw               kaweth
ar3k                         keyspan
ar7010_1_1.fw                keyspan_pda
ar7010.fw                    korg
ar9170-1.fw                  lbtf_usb.bin
ar9170-2.fw                  lgs8g75.fw
ar9170.fw                    libertas
ar9271.fw                    macxvi200.bin
asihpi                       macxvi.cfg
ath3k-1.fw                   matrox
ath6k                        mrvl
atmel_at76c502_3com.bin      mts_cdma.fw
atmel_at76c502.bin           mts_edge.fw
atmel_at76c502d.bin          mts_gsm.fw
atmel_at76c502e.bin          mts_mt9234mu.fw
atmel_at76c504_2958.bin      mts_mt9234zba.fw
atmel_at76c504a_2958.bin     mwl8335_duplex.fw
atmel_at76c504.bin           mwl8k
atmel_at76c506.bin           myri10ge_ethp_z8e.dat
atmsar11.fw                  myri10ge_eth_z8e.dat
av7110                       myri10ge_rss_ethp_z8e.dat
b43                          myri10ge_rss_eth_z8e.dat
bcm2033-fw.bin               myricom
bcm2033-md.hex               ngene_15.fw
bcm70012fw.bin               ngene_17.fw
bcm70015fw.bin               NPE-B
bnx2                         NPE-C
bnx2x                        ositech
brcm                         phanfw.bin
carl9170-1.fw                ql2100_fw.bin
cis                          ql2200_fw.bin
cpia2                        ql2300_fw.bin
cxgb3                        ql2322_fw.bin
cxgb4                        ql2400_fw.bin
dabusb                       ql2500_fw.bin
dsp56k                       qlogic
dvb-cx18-mpc718-mt352.fw     r128
dvb-dibusb-5.0.0.11.fw       radeon
dvb-fe-cx24116.fw            rt2561.bin
dvb-fe-nxt2004.fw            rt2561s.bin
dvb-fe-or51132-qam.fw        rt2661.bin
dvb-fe-or51132-vsb.fw        rt2860.bin
dvb-fe-or51211.fw            rt2870.bin
dvb-fe-tda10046.fw           rt3070.bin
dvb-fe-tda10048-1.0.fw       rt3071.bin
dvb-fe-xc5000-1.6.114.fw     rt3090.bin
dvb-ttpci-01.fw              rt73.bin
dvb-ttusb-dec-2000t.fw       RTL8192E
dvb-ttusb-dec-2540t.fw       RTL8192SE
dvb-ttusb-dec-3000s.fw       rtl_nic
dvb-usb-af9015.fw            rtlwifi
dvb-usb-avertv-a800-02.fw    s2250.fw
dvb-usb-bluebird-01.fw       s2250_loader.fw
dvb-usb-dib0700-1.10.fw      sb16
dvb-usb-dib0700-1.20.fw      scripts
dvb-usb-dibusb-5.0.0.11.fw   slicoss
dvb-usb-dibusb-6.0.0.8.fw    sms1xxx-hcw-55xxx-dvbt-02.fw
dvb-usb-dtt200u-01.fw        sun
dvb-usb-terratec-h5-drxk.fw  sxg
dvb-usb-tvwalkert.fw         TDA7706_OM_v2.5.1_boot.txt
dvb-usb-umt-010-02.fw        TDA7706_OM_v3.0.2_boot.txt
dvb-usb-vp702x-01.fw         tehuti
dvb-usb-vp7045-01.fw         ti_3410.fw
dvb-usb-wt220u-02.fw         ti_5052.fw
dvb-usb-wt220u-fc03.fw       ti-connectivity
dvb-usb-wt220u-zl0353-01.fw  tigon
e100                         tlg2300_firmware.bin
ea                           tr_smctr.bin
edgeport                     ttusb-budget
emi26                        ueagle-atm
emi62                        usbdux
ene-ub6250                   usbduxfast_firmware.bin
ess                          usbdux_firmware.bin
f2255usb.bin                 usbduxsigma_firmware.bin
GPL-3                        v4l-cx231xx-avcore-01.fw
hp                           v4l-cx23418-apu.fw
htc_7010.fw                  v4l-cx23418-cpu.fw
htc_9271.fw                  v4l-cx23418-dig.fw
i2400m-fw-usb-1.4.sbcf       v4l-cx2341x-dec.fw
i2400m-fw-usb-1.5.sbcf       v4l-cx2341x-enc.fw
i6050-fw-usb-1.5.sbcf        v4l-cx2341x-init.mpg
intelliport2.bin             v4l-cx23885-avcore-01.fw
ipw2100-1.3.fw               v4l-cx23885-enc.fw
ipw2100-1.3-i.fw             v4l-cx25840.fw
ipw2100-1.3-p.fw             v4l-pvrusb2-24xxx-01.fw
ipw2200-bss.fw               v4l-pvrusb2-29xxx-01.fw
ipw2200-ibss.fw              vicam
ipw2200-sniffer.fw           vntwusb.fw
isci                         vxge
isl3877                      WHENCE.ubuntu
isl3886pci                   whiteheat.fw
isl3886usb                   whiteheat_loader.fw
isl3887usb                   xc3028-v27.fw
isl3890                      yam
iwlwifi-1000-5.ucode         yamaha
iwlwifi-100-5.ucode          zd1201-ap.fw
iwlwifi-105-6.ucode          zd1201.fw
iwlwifi-135-6.ucode          zd1211
iwlwifi-2000-6.ucode
graham@graham-Aspire-3500:~$ 
graham@graham-Aspire-3500:~$ 
graham@graham-Aspire-3500:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             unavailable
  Default:           no
  HW Address:        00:0E:9B:CF:E0:0F

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sis900
  State:             unavailable
  Default:           no
  HW Address:        00:C0:9F:9C:14:DF

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off


graham@graham-Aspire-3500:~$

---

### Post by chili555 on 2012-07-03
First of all, please remove this file:```
sudo rm /etc/modprobe.d/ath5k.conf
```The parameter is boolean; i.e Y or N, not an integer:```
$ modinfo ath5k
filename:       /lib/modules/3.2.0-25-generic-pae/updates/cw-3.3/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
<snip>
depends:        mac80211,cfg80211,ath
vermagic:       3.2.0-25-generic-pae SMP mod_unload modversions 686 
parm:           [COLOR="Red"]nohwcrypt:Disable hardware encryption. (bool)[/COLOR]
parm:           all_channels:Expose all channels the device can use. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)
```Please let me see:```
cat /etc/NetworkManager/NetworkManager.conf
```Also, please try:```
sudo modprobe -r ath5k
sudo modprobe ath5k no_hw_rfkill_switch=Y
sudo iwlist wlan0 scan
```

---

### Post by wildmanne39 on 2012-07-03
Hi chili555, thank you for the help it is very appreciated.

---

### Post by pauloz on 2012-07-04
Hi chili555 and wildmanne39

Results from last post as requested - please note there was no output from sudo modprobe -r ath5k:

graham@graham-Aspire-3500:~$ sudo rm /etc/modprobe.d/ath5k.conf
[sudo] password for graham: 
graham@graham-Aspire-3500:~$ sudo rm /etc/modprobe.d/ath5k.conf
rm: cannot remove `/etc/modprobe.d/ath5k.conf': No such file or directory
graham@graham-Aspire-3500:~$ 
graham@graham-Aspire-3500:~$ 
graham@graham-Aspire-3500:~$ cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false
graham@graham-Aspire-3500:~$ 
graham@graham-Aspire-3500:~$ 
graham@graham-Aspire-3500:~$ sudo modprobe -r ath5k
graham@graham-Aspire-3500:~$ 
graham@graham-Aspire-3500:~$ 
graham@graham-Aspire-3500:~$ sudo modprobe ath5k no_hw_rfkill_switch=Y
FATAL: Error inserting ath5k (/lib/modules/3.2.0-26-generic-pae/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko): Unknown symbol in module, or unknown parameter (see dmesg)
graham@graham-Aspire-3500:~$ 
graham@graham-Aspire-3500:~$ 
graham@graham-Aspire-3500:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

graham@graham-Aspire-3500:~$ 

Thanks.

---

### Post by chili555 on 2012-07-04
> $ sudo modprobe ath5k no_hw_rfkill_switch=Y
FATAL: Error inserting ath5k (/lib/modules/3.2.0-26-generic-pae/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko): Unknown symbol in module, or unknown parameter (see dmesg)Let's see:```
modinfo ath5k | tail -n5
dmesg | grep ath5
```Thanks.

---

### Post by pauloz on 2012-07-05
> **chili555 said:**
> Let's see:```
modinfo ath5k | tail -n5
dmesg | grep ath5
```Thanks.

Hi again - as requested:

graham@graham-Aspire-3500:~$ modinfo ath5k | tail -n5
intree:         Y
vermagic:       3.2.0-26-generic-pae SMP mod_unload modversions 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           all_channels:Expose all channels the device can use. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
graham@graham-Aspire-3500:~$ 
graham@graham-Aspire-3500:~$ 
graham@graham-Aspire-3500:~$ dmesg | grep ath5
[   21.554498] ath5k 0000:00:0b.0: enabling device (0010 -> 0012)
[   21.554536] ath5k 0000:00:0b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   21.554624] ath5k 0000:00:0b.0: registered as 'phy0'
[   23.060347] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
graham@graham-Aspire-3500:~$ 

Thanks.

---

### Post by chili555 on 2012-07-05
Got it! The earlier ath5k module included in Ubuntu 10.10 doesn't include that parameter. Please try:```
sudo modprobe -r ath5k
sudo modprobe ath5k nohwcrypt=Y
```Any improvement? If so, we'll write a file and make it persistent.

---

### Post by pauloz on 2012-07-06
> **chili555 said:**
> Got it! The earlier ath5k module included in Ubuntu 10.10 doesn't include that parameter. Please try:```
sudo modprobe -r ath5k
sudo modprobe ath5k nohwcrypt=Y
```Any improvement? If so, we'll write a file and make it persistent.

Hi - I'm afraid nothing happened and have the same problems I've described previously. Here is the output - as you can see, nothing:

graham@graham-Aspire-3500:~$ sudo modprobe -r ath5k
[sudo] password for graham: 
graham@graham-Aspire-3500:~$ 
graham@graham-Aspire-3500:~$ 
graham@graham-Aspire-3500:~$ sudo modprobe ath5k nohwcrypt=Y
graham@graham-Aspire-3500:~$ 
graham@graham-Aspire-3500:~$ 
graham@graham-Aspire-3500:~$

---

### Post by chili555 on 2012-07-07
> *-network:1 [COLOR="Red"]DISABLED[/COLOR]
description: Wireless interface
product: AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg]
vendor: Atheros Communications Inc.
physical id: b
bus info: pci@0000:00:0b.0
logical name: wlan0 This suggests a hardware switch problem, as does this:> I get another greyed out message, "Wireless is disabled by hardware switch". *I know there are CTRL commands that can be used to enable but I don't know what to use*.However, this suggests that there is *NO* problem:> 0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: noVery confusing and very conflicting. Please run:```
sudo lshw -C network
```Does it still show as *DISABLED*? Now try:```
rfkill list all
```Any blocks?

What is the status of the wireless LED as you press the switch? Please see attached.

---

### Post by pauloz on 2012-07-08
@ chili555 - well finally I have some good news. I'm trying to fix this laptop for a friend, so I wasn't familiar with its functions. When you posted a thumbnail of the front section of the laptop, I pressed the wireless communication button (#5) for a few seconds and it worked! I had a wireless connection! The strange thing was when I first got the laptop, the wireless connection was working then stopped operating - I never went near that particular button because I thought it was a display to indicate the computer was on.

Many thanks for your help chili555 and special thanks to wildmanne39 for your time and patience. I do have an issue with the screen remaining blank when I either start or reboot the computer (!!!) however I'll commence a new thread in Absolute Beginner.

Sincerely
pauloz

---

### Post by chili555 on 2012-07-08
We're glad it's working by whatever means. We hope you'll fine-tune the display issue and have fun!

---

### Post by karnev on 2012-09-15
> **Wild Man said:**
> Hi, open network manager and make sure it is set to infrastructure.
Please run:
```
echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```Keep your wired connection unplug while trying to connect by wireless.


Hi Wild Man,

Works fine on my Toshiba L20-155 with Atheros AR5005G running ubuntu 12.04 32 bit PAE.

I tried to make it permanent by modifying /etc/modules by :
sudo nano /etc/modules:
# load ath5k module
ath5k


might be handy for others

---

### Post by lgducalg on 2012-09-15
Hello.

I installed yesterday the available/last version of ubuntu because I will need to work on it for some university courses(Robotics). Hereupon, I have to say I really don't know nothing about this operative system, therefore I need you to explain me very well what to do in a very exaustive way for you :lolflag: 

That said, the problem is:

Ubuntu recognize all wireless conections available but it is not capable of connect to anywhere.

Problem way:

Ubuntu request the router/connection password and it keeps asking for it in of space of few seconds, incapable to connect.
What I think it is in my little knowledge in this area:
Ubuntu don't recognize my wireless driver, or simply don't have available the drivers for it, and and designated a standard driver that is not stable.

Wireless card:
Bigfoot Killer-N 1102

Thx for your time.

---

### Post by chili555 on 2012-09-16
> **lgducalg said:**
> Hello.

I installed yesterday the available/last version of ubuntu because I will need to work on it for some university courses(Robotics). Hereupon, I have to say I really don't know nothing about this operative system, therefore I need you to explain me very well what to do in a very exaustive way for you :lolflag: 

That said, the problem is:

Ubuntu recognize all wireless conections available but it is not capable of connect to anywhere.

Problem way:

Ubuntu request the router/connection password and it keeps asking for it in of space of few seconds, incapable to connect.
What I think it is in my little knowledge in this area:
Ubuntu don't recognize my wireless driver, or simply don't have available the drivers for it, and and designated a standard driver that is not stable.

Wireless card:
Bigfoot Killer-N 1102

Thx for your time.The Wild Man may be temporarily away. Since this thread is largely about ath5k, I suggest you start your own new thread and include:```
lspci -nn | grep 0280
```

---

### Post by lgducalg on 2012-09-16
As you advise I created a new topic with the output of the code you enter, already.

[http://ubuntuforums.org/showthread.php?p=12242358#post12242358](http://ubuntuforums.org/showthread.php?p=12242358#post12242358)

Thx

---

