---
title: "Networking icon disabled yet wifi can still scan"
date: 2011-11-04
forum: Networking &amp; Wireless
---

### Post by gear3D on 2011-11-04
Hello (Using Lubuntu 11.10),

I just installed a D-Link DWL-G520+ PCI Wifi card and installed the Win2000 drivers using Ndiswrapper.

Drivers are working fine as I can scan for wireless networks. However my Networking icon in the taskbar displays 'Networking disabled'. I have right-clicked it and ticked 'Enable Wireless' but everything is still grayed out if I edit my connections. Wired ethernet is working great but I can't see any setting for the LAN either.

I read through jaguare22's post [http://ubuntuforums.org/showthread.php?t=1719366](http://ubuntuforums.org/showthread.php?t=1719366) and look to be having the same problem. I have tried uninstalling ConnMan using

```
sudo apt-get remove ConnMann
```
But is isn't installed like I thought by default. I can restart the network-manager service but that makes no difference.

My /var/lib/NetworkManager/NetworkManager.state
```
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
```

I don't have a /etc/NetworkManager/nm-system-settings.conf
Could that be my issue? Seems nm-tool can't connect to Network Manager.

Thanks.

```
  sudo lshw -C network
*-network:0
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 2
       bus info: pci@0000:01:02.0
       logical name: wlan0
       version: 00
       serial: 00:80:c8:2c:c2:41
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+gplus driverversion=1.56+D-Link,07/02/2003,4.0.40.1 latency=32 link=no multicast=yes wireless=IEEE 802.11b
       resources: irq:22 memory:e0020000-e0021fff memory:e0000000-e001ffff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: eth0
       version: 10
       serial: 00:20:ed:56:67:00
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=10.0.0.1 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:21 ioport:c000(size=256) memory:e0022000-e00220ff

```

```
nm-tool

** (process:2497): WARNING **: _nm_object_get_property: Error getting 'WirelessHardwareEnabled' for /org/freedesktop/NetworkManager: (9) Rejected send message, 2 matched rules; type="method_call", sender=":1.57" (uid=1000 pid=2497 comm="nm-tool ") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply="0" destination="org.freedesktop.NetworkManager" (uid=0 pid=2340 comm="NetworkManager ")


** (process:2497): WARNING **: _nm_object_get_property: Error getting 'WwanHardwareEnabled' for /org/freedesktop/NetworkManager: (9) Rejected send message, 2 matched rules; type="method_call", sender=":1.57" (uid=1000 pid=2497 comm="nm-tool ") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply="0" destination="org.freedesktop.NetworkManager" (uid=0 pid=2340 comm="NetworkManager ")


** (process:2497): WARNING **: _nm_object_get_property: Error getting 'WimaxHardwareEnabled' for /org/freedesktop/NetworkManager: (9) Rejected send message, 2 matched rules; type="method_call", sender=":1.57" (uid=1000 pid=2497 comm="nm-tool ") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply="0" destination="org.freedesktop.NetworkManager" (uid=0 pid=2340 comm="NetworkManager ")


** (process:2497): WARNING **: _nm_object_get_property: Error getting 'State' for /org/freedesktop/NetworkManager: (9) Rejected send message, 2 matched rules; type="method_call", sender=":1.57" (uid=1000 pid=2497 comm="nm-tool ") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply="0" destination="org.freedesktop.NetworkManager" (uid=0 pid=2340 comm="NetworkManager ")


NetworkManager Tool


** (process:2497): WARNING **: _nm_object_get_property: Error getting 'State' for /org/freedesktop/NetworkManager: (9) Rejected send message, 2 matched rules; type="method_call", sender=":1.57" (uid=1000 pid=2497 comm="nm-tool ") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply="0" destination="org.freedesktop.NetworkManager" (uid=0 pid=2340 comm="NetworkManager ")

State: unknown


** (process:2497): WARNING **: error: could not connect to NetworkManager

```

```
lspci -nnk | grep -iA2 net
01:02.0 Network controller [0280]: Texas Instruments ACX 111 54Mbps Wireless Interface [104c:9066]
        Subsystem: D-Link System Inc DWL-G520+ Wireless PCI Adapter [1186:3b04]
        Kernel driver in use: ndiswrapper
01:05.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139]
        Kernel driver in use: 8139too

```

```
lsmod
Module                  Size  Used by
ndiswrapper           193669  0
bnep                   17923  2
rfcomm                 38408  0
bluetooth             148839  10 bnep,rfcomm
ppdev                  12849  0
snd_wavefront          34737  0
snd_cs4236             29294  0
snd_wss_lib            30063  2 snd_wavefront,snd_cs4236
snd_opl3_lib           18863  2 snd_wavefront,snd_cs4236
snd_hwdep              13276  2 snd_wavefront,snd_opl3_lib
snd_mpu401             13847  0
snd_mpu401_uart        13865  3 snd_wavefront,snd_cs4236,snd_mpu401
snd_seq_midi           13132  0
snd_rawmidi            25241  3 snd_wavefront,snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_intel8x0           33318  0
snd_ac97_codec        106082  1 snd_intel8x0
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80468  4 snd_cs4236,snd_wss_lib,snd_intel8x0,snd_ac97_codec
serio_raw              12990  0
snd_seq_device         14172  4 snd_opl3_lib,snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              28932  4 snd_wss_lib,snd_opl3_lib,snd_seq,snd_pcm
snd_page_alloc         14115  3 snd_wss_lib,snd_intel8x0,snd_pcm
i915                  505108  2
shpchp                 32356  0
snd                    55902  14 snd_wavefront,snd_cs4236,snd_wss_lib,snd_opl3_lib,snd_hwdep,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_intel8x0,snd_seq,snd_ac97_codec,snd_pcm,snd_seq_device,snd_timer
ns558                  12654  0
gameport               15060  2 ns558
soundcore              12600  1 snd
drm_kms_helper         32889  1 i915
drm                   192226  3 i915,drm_kms_helper
parport_pc             32114  1
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0
parport                40930  3 ppdev,parport_pc,lp
8139too                23283  0
8139cp                 22636  0

```

```
sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:26:44:97:AE:13
                    ESSID:"BigPond97AE13"
                    Protocol:IEEE 802.11FH
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:95/100  Signal level:-35 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:60:64:3F:56:60
                    ESSID:"NetComm Wireless"
                    Protocol:IEEE 802.11FH
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:21/100  Signal level:-82 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```

```
dmesg | egrep 'b43|firm|radio|switch|wlan0'
[    0.005238] SMP alternatives: switching to UP code
[   23.765414] Console: switching to colour frame buffer device 128x48
[  129.876380] wlan0: ethernet device 00:80:c8:2c:c2:41 using NDIS driver: gplus, version: 0x40000, NDIS version: 0x500, vendor: 'D-Link AirPlus Wireless Adapter', 104C:9066.5.conf
[  129.876620] wlan0: encryption modes supported: none
[  129.936431] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1478.991530] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

---

### Post by amjjawad on 2011-11-05
Hello and Welcome to Ubuntu Forum :)

Thanks for choosing and using Lubuntu, it's a great OS and I'm glad many are using it :)

I'm amjjawad, Lubuntu Team Member who is in charge of Forum Support and some other things and he's at your service :)

Could you please confirm whether you do have something like that?

[IMG]http://ubuntuforums.org/picture.php?albumid=2432&pictureid=8204[/IMG]

It's a display BUG in Lubuntu 11.10 and even though none are ticked or selected, you still can be connected.

Are you able to Scan Wireless Networks and connect to that?

Is this a normal installation? or you are using a Virtual Box?

Waiting for your reply :)

P.S.
I'm so impressed by your first post. You have mentioned everything :)
I wish everyone could follow your steps and be as informative as possible.

---

### Post by gear3D on 2011-11-06
Hi amjjawad,

Thanks for responding. Before when I entered the NetworkManager any options to see my wired or wireless connections was grayed out and I wasn't able change anything. I tried being a bit adventurous and removed, then reinstalled the NetworkManager and reinstalled the network-manager-gnome applet.

Now when I click on the NetworkManager icon I can change the settings that were before grayed out. If that wasn't the best thing to do, please let me know :(

Also I can see the same wireless networks as I could see in iwlist scan but I can not connect. My wireless network is using WPA encryption and I think the default is WEP. 

For example /etc/NetworkManager/system-connections
```
[connection]
id=BigPond97AE13
uuid=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
type=802-11-wireless

[802-11-wireless]
ssid=BigPond97AE13
mode=infrastructure
mac-address=xx:x:x:xx:xx:xx
security=802-11-wireless-security

[802-11-wireless-security]
key-mgmt=none
wep-key0=xxxxxxxxxx

[ipv4]
method=auto

```

Should the 'wep-key0' line be wpa-key0?

A another problem, how can I set the drivers for my wireless card to automatically start? Every time I reboot the machine, I have to uninstall and reinstall the drivers using the Ndiswrapper program :) This is a stand-alone box as well. I've been using Lubuntu, my first distro, for about 2 months now and am trying to learn as much as I can. Thanks for the encouragement too.

---

### Post by gear3D on 2011-11-06
Since the last post I have tried changing from WPA to WEP 64 and 128bit encryption - neither will work.

I have been able to connect to my wireless connection if there is no security. Every time I have the encryption I am able to connect with my Windows machine.

Is there anything else I can try? :confused: Thanks.

---

### Post by amjjawad on 2011-11-06
Hi,

I think the problem is a network problem more than being an OS problem. Hence, I'll consult some friends who know much better than me in these stuff. I'll see who is Online and if no one is there, I'll leave them a message :)

---

### Post by amjjawad on 2011-11-06
I know two friends and both are Offline. I left a message to one of them and I'm sure he'll jump in once he'll read it. 

Sorry if I couldn't help much!

---

