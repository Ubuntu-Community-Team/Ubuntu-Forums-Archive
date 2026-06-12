---
title: "Wireless networks detected, can't connect (Atheros)"
date: 2012-07-01
forum: Networking &amp; Wireless
---

### Post by Martificiam on 2012-07-01
I have an Atheros AR5005G Wireless adapter and a Broadcom 440x 10/100 integrated controller. Currently, my laptop is dualbooted with XP and Lubuntu 12.04, but the following problem persists in ALL Linux versions (works on XP though).

Basically, the wireless networks are being detected, but when I try to connect to them, it never happens. I've already tried using ndiswrapper and the drivers seemed to be installed but nothing changed. ```
sudo rfkill list
``` tells me ```
Hard blocked: yes
``` although after endless terminal commands it was once set to "no".

When I untick "Enable wireless" in the system tray, the item becomes gray (unclickable) and it says something about the hardware switch. I suppose it asks me to press a certain key to enable wireless, but why does it detect wireless networks on startup then?

Back on XP, the program "Power Manager" must be running in the background in order for the hardware wireless key to work. When I press it, a blue LED light at the corner of the laptop lights up and the computer is able to use Wi-Fi. This button doesn't work on any Linux.

Any ideas?

---

### Post by jackyboy633 on 2012-07-01
Hi there,
This is only a suggestion, but have you checked in the BIOS to see if the wireless is enabled. I used to have an Eee PC that did this to enable/disable wireless.

Hope this helps :-)
Jackyboy633

---

### Post by Martificiam on 2012-07-01
There is nothing related to Wireless in the BIOS setup. The BIOS itself seems to be very simple and provides only a few options overall.

---

### Post by jackyboy633 on 2012-07-01
What is the make and model of your laptop. This will enable us to solve your question better.

Kind regards,
Jackyboy633

---

### Post by Martificiam on 2012-07-01
Fujitsu Siemens Amilo L1310G

---

### Post by wildmanne39 on 2012-07-01
Hi, please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
nm-tool
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by Martificiam on 2012-07-01
Here it is. Please note that after unticking Enable Wireless on the network manager, it becomes grey and hard blocked becomes this:

```
Hard blocked: yes
```

```
mantas@Home:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux Home 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:41:14 UTC 2012 i686 i686 i386 GNU/Linux
mantas@Home:~$ lspci -nnk | grep -iA2 net
02:01.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg] [168c:001a] (rev 01)
	Subsystem: Atheros Communications Inc. Compex Wireless 802.11 b/g  MiniPCI Adapter, Rev A1 [WLM54G] [168c:2052]
	Kernel driver in use: ath5k
--
02:0d.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
	Subsystem: Fujitsu Technology Solutions Device [1734:1098]
	Kernel driver in use: b44
mantas@Home:~$ nm-tool

NetworkManager Tool

State: connecting

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             unavailable
  Default:           no
  HW Address:        00:40:CA:D9:EF:0B

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [SpeedTouch6FDDBB] --------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             connecting (configuring)
  Default:           no
  HW Address:        00:02:E3:48:44:8A

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    SpeedTouch6FDDBB:Infra, 00:1F:9F:75:FE:E7, Freq 2412 MHz, Rate 54 Mb/s, Strength 27


mantas@Home:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

mantas@Home:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
mantas@Home:~$ lsmod
Module                  Size  Used by
joydev                 17393  0 
snd_atiixp             19337  1 
snd_atiixp_modem       18604  5 
snd_ac97_codec        106082  2 snd_atiixp,snd_atiixp_modem
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  5 snd_atiixp,snd_atiixp_modem,snd_ac97_codec
rfcomm                 38139  0 
snd_seq_midi           13132  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
snd_rawmidi            25424  1 snd_seq_midi
arc4                   12473  2 
snd_seq_midi_event     14475  1 snd_seq_midi
pcmcia                 39791  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ath5k                 145127  0 
ath                    19387  1 ath5k
radeon                729591  2 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              436455  1 ath5k
tifm_7xx1              12937  0 
snd                    62064  18 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                87140  0 
tifm_core              15040  1 tifm_7xx1
serio_raw              13027  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
ttm                    65344  1 radeon
cfg80211              178679  3 ath5k,ath,mac80211
drm_kms_helper         45466  1 radeon
soundcore              14635  1 snd
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
drm                   197692  4 radeon,ttm,drm_kms_helper
snd_page_alloc         14115  3 snd_atiixp,snd_atiixp_modem,snd_pcm
i2c_piix4              13093  0 
i2c_algo_bit           13199  1 radeon
shpchp                 32325  0 
mac_hid                13077  0 
ati_agp                13242  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40180  0 
b44                    31412  0 
pata_atiixp            12999  3 
ssb                    50691  1 b44
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
usbhid                 41906  0 
hid                    77367  1 usbhid

```

---

### Post by wildmanne39 on 2012-07-01
Hi, your signal strength is to low to connect, is this the network SpeedTouch6FDDBB that you want to connect too?

If you uncheck enabled wireless then it would show a hardblock because you are turning wireless off.

Please try this:
```
echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```
Thanks

---

### Post by Martificiam on 2012-07-01
Yes, it's that network that I'm trying to connect to. The signal is weak, but I'm able to browse the internet in Windows XP (dualboot setup).
The problem is that when disable wireless I can't reenable it from the network manager, the item becomes grey.
I'll try those cmds in a minute and will post the output here.

---

### Post by Martificiam on 2012-07-01
> **wildmanne39 said:**
>  
```
echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```

Now when I boot up my lubuntu it detects the wireless network. But the network manager asks for the sudo password (system policy something). When I enter it, the nm applet says "wireless is disabled by hardware switch". Pressing the key does nothing and I've already tried using the windows drivers with ndiswrapper (not sure if I did everything correctly though, but the driver loaded).

---

### Post by wildmanne39 on 2012-07-01
Hi, please remove ndiswrapper if you have it installed now with:
```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a

```
Go to the link and do what is in post 18.
[http://ubuntuforums.org/showthread.php?p=11792710#post11792710](http://ubuntuforums.org/showthread.php?p=11792710#post11792710)
Thanks

---

### Post by Martificiam on 2012-07-02
Still doesn't work, same result. It detects the network and when I try to connect it keeps connecting but never establishes a connection :/

---

### Post by wildmanne39 on 2012-07-02
Hi, please post the contents of:
```
gksudo gedit /etc/rc.local
```

Then post the output of:
```
lsmod | grep ath
ndiswrapper -l
cat /etc/network/interfaces
```
```
sudo cat /var/log/syslog | grep -e ath -e firmware -e wlan -e wpa -e etork | tail -n55
```
Thanks

---

### Post by Martificiam on 2012-07-08
Sorry I took so long.
I've just reinstalled lubuntu, therefore there is no ndiswrapper. But here's the output anyway:

/etc/rc.local:
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

exit 0

```

lsmod | grep ath:

```
ath5k                 145127  0 
ath                    19387  1 ath5k
mac80211              436455  1 ath5k
cfg80211              178679  3 ath5k,ath,mac80211

```

ndiswrapper -1:

```
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common

```

cat /etc/network/interfaces:

```

auto lo
iface lo inet loopback

```

sudo cat /var/log/syslog | grep -e ath -e firmware -e wlan -e wpa -e etork | tail -n55:

```

Jul  8 11:52:34 Namai NetworkManager[850]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.4/0000:02:01.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jul  8 11:52:34 Namai NetworkManager[850]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.4/0000:02:0d.0/ssb0:0/net/eth0, iface: eth0)
Jul  8 11:52:34 Namai NetworkManager[850]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.4/0000:02:0d.0/ssb0:0/net/eth0, iface: eth0): no ifupdown configuration found.
Jul  8 11:52:34 Namai NetworkManager[850]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jul  8 11:52:34 Namai NetworkManager[850]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jul  8 11:52:34 Namai NetworkManager[850]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jul  8 11:52:34 Namai NetworkManager[850]: <info> (wlan0): using nl80211 for WiFi device control
Jul  8 11:52:34 Namai NetworkManager[850]: <warn> (wlan0): driver supports Access Point (AP) mode
Jul  8 11:52:34 Namai NetworkManager[850]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath5k' ifindex: 3)
Jul  8 11:52:34 Namai NetworkManager[850]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Jul  8 11:52:34 Namai NetworkManager[850]: <info> (wlan0): now managed
Jul  8 11:52:34 Namai NetworkManager[850]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jul  8 11:52:34 Namai NetworkManager[850]: <info> (wlan0): bringing up device.
Jul  8 11:52:34 Namai NetworkManager[850]: <info> (wlan0): preparing device.
Jul  8 11:52:34 Namai NetworkManager[850]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jul  8 11:52:34 Namai kernel: [   18.857983] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul  8 11:52:34 Namai kernel: [   18.858649] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul  8 11:52:34 Namai dbus[758]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Jul  8 11:52:35 Namai dbus[758]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Jul  8 11:52:35 Namai NetworkManager[850]: <info> wpa_supplicant started
Jul  8 11:52:35 Namai NetworkManager[850]: <info> (wlan0): supplicant interface state: starting -> ready
Jul  8 11:52:35 Namai NetworkManager[850]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jul  8 11:52:35 Namai NetworkManager[850]: <info> (wlan0): supplicant interface state: ready -> inactive
Jul  8 14:21:21 Namai kernel: [ 8946.470370] ath5k 0000:02:01.0: PCI INT A disabled
Jul  8 14:21:21 Namai NetworkManager[850]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:14.4/0000:02:01.0/net/wlan0, iface: wlan0)
Jul  8 14:21:21 Namai NetworkManager[850]: <info> (wlan0): now unmanaged
Jul  8 14:21:21 Namai NetworkManager[850]: <info> (wlan0): device state change: disconnected -> unmanaged (reason 'removed') [30 10 36]
Jul  8 14:21:21 Namai NetworkManager[850]: <info> (wlan0): cleaning up...
Jul  8 14:21:22 Namai wpa_supplicant[882]: Could not read interface wlan0 flags: No such device
Jul  8 14:21:27 Namai kernel: [ 8952.128273] ath5k 0000:02:01.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Jul  8 14:21:27 Namai kernel: [ 8952.128381] ath5k 0000:02:01.0: registered as 'phy0'
Jul  8 14:21:27 Namai kernel: [ 8952.724915] ath: EEPROM regdomain: 0x30
Jul  8 14:21:27 Namai kernel: [ 8952.724920] ath: EEPROM indicates we should expect a direct regpair map
Jul  8 14:21:27 Namai kernel: [ 8952.724925] ath: Country alpha2 being used: AM
Jul  8 14:21:27 Namai kernel: [ 8952.724928] ath: Regpair used: 0x30
Jul  8 14:21:27 Namai kernel: [ 8952.726760] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
Jul  8 14:21:27 Namai NetworkManager[850]: <info> (wlan0): using nl80211 for WiFi device control
Jul  8 14:21:27 Namai NetworkManager[850]: <warn> (wlan0): driver supports Access Point (AP) mode
Jul  8 14:21:27 Namai NetworkManager[850]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath5k' ifindex: 9)
Jul  8 14:21:27 Namai NetworkManager[850]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/2
Jul  8 14:21:27 Namai NetworkManager[850]: <info> (wlan0): now managed
Jul  8 14:21:27 Namai NetworkManager[850]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jul  8 14:21:27 Namai NetworkManager[850]: <info> (wlan0): bringing up device.
Jul  8 14:21:27 Namai kernel: [ 8953.065345] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul  8 14:21:27 Namai NetworkManager[850]: <warn> (wlan0): device not up after timeout!
Jul  8 14:21:27 Namai NetworkManager[850]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jul  8 14:21:27 Namai kernel: [ 8953.083916] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul  8 14:21:27 Namai wpa_supplicant[882]: Could not set interface wlan0 flags: Operation not possible due to RF-kill
Jul  8 14:21:27 Namai wpa_supplicant[882]: Could not set interface 'wlan0' UP
Jul  8 14:21:27 Namai wpa_supplicant[882]: Could not set interface wlan0 flags: Operation not possible due to RF-kill
Jul  8 14:21:27 Namai wpa_supplicant[882]: Failed to initialize driver interface
Jul  8 14:21:27 Namai NetworkManager[850]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.4/0000:02:01.0/net/wlan0, iface: wlan0)
Jul  8 14:21:27 Namai NetworkManager[850]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.4/0000:02:01.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jul  8 14:21:27 Namai NetworkManager[850]: <error> [1341746487.771842] [nm-supplicant-interface.c:804] interface_add_cb(): (wlan0): error adding interface: wpa_supplicant couldn't grab this interface.
Jul  8 14:21:27 Namai NetworkManager[850]: <info> (wlan0): supplicant interface state: starting -> down

```

"Namai" is the hostname.

---

### Post by wildmanne39 on 2012-07-08
Hi, since you reinstalled lubuntu please post the output of the commands in post 6 again.
Thanks

---

### Post by Martificiam on 2012-07-09
Pretty much the same, although note that this time I'm trying to connect to the TRENDnet network through WiFi.
The detected networks are there and when I select one (TRENDnet doesn't have any encryption, I connect to it successfully with my phone and other devices) it just keeps connecting until a notification pops up "Disconnected". Strange.

```
cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux Namai 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 16:26:01 UTC 2012 i686 i686 i386 GNU/Linux
mantas@Namai:~$ lspci -nnk | grep -iA2 net
02:01.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg] [168c:001a] (rev 01)
	Subsystem: Atheros Communications Inc. Compex Wireless 802.11 b/g  MiniPCI Adapter, Rev A1 [WLM54G] [168c:2052]
	Kernel driver in use: ath5k
--
02:0d.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
	Subsystem: Fujitsu Technology Solutions Device [1734:1098]
	Kernel driver in use: b44
mantas@Namai:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             connected
  Default:           yes
  HW Address:        00:40:CA:D9:EF:0B

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         79.133.243.85
    Prefix:          28 (255.255.255.240)
    Gateway:         79.133.243.81

    DNS:             80.240.0.2
    DNS:             212.59.1.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        00:02:E3:48:44:8A

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    gerosios666:     Infra, 00:14:D1:A9:83:CF, Freq 2472 MHz, Rate 54 Mb/s, Strength 20 WPA2
    TRENDnet:        Infra, 00:01:23:45:67:89, Freq 2437 MHz, Rate 54 Mb/s, Strength 72
    ac1212:          Infra, 00:1D:73:73:B5:DC, Freq 2417 MHz, Rate 54 Mb/s, Strength 20 WPA2


mantas@Namai:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

mantas@Namai:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
mantas@Namai:~$ lsmod
Module                  Size  Used by
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
joydev                 17393  0 
snd_usb_audio         101566  0 
arc4                   12473  2 
snd_hwdep              13276  1 snd_usb_audio
snd_usbmidi_lib        24603  1 snd_usb_audio
snd_seq_midi           13132  0 
snd_rawmidi            25424  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_atiixp             19337  1 
pcmcia                 39791  0 
snd_atiixp_modem       18604  5 
snd_ac97_codec        106082  2 snd_atiixp,snd_atiixp_modem
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ac97_bus               12642  1 snd_ac97_codec
ath5k                 145127  0 
snd_pcm                80845  6 snd_usb_audio,snd_atiixp,snd_atiixp_modem,snd_ac97_codec
radeon                729591  2 
ath                    19387  1 ath5k
mac80211              436455  1 ath5k
snd_timer              28931  2 snd_seq,snd_pcm
tifm_7xx1              12937  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                87213  0 
tifm_core              15040  1 tifm_7xx1
uvcvideo               67203  0 
snd                    62064  21 snd_usb_audio,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_seq,snd_pcm,snd_timer,snd_seq_device
serio_raw              13027  0 
snd_page_alloc         14115  3 snd_atiixp,snd_atiixp_modem,snd_pcm
videodev               86588  1 uvcvideo
cfg80211              178679  3 ath5k,ath,mac80211
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
drm                   197692  4 radeon,ttm,drm_kms_helper
soundcore              14635  1 snd
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
i2c_piix4              13093  0 
i2c_algo_bit           13199  1 radeon
mac_hid                13077  0 
ati_agp                13242  0 
shpchp                 32325  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
b44                    31412  0 
firewire_ohci          40180  0 
ssb                    50691  1 b44
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
pata_atiixp            12999  3 
```

---

### Post by wildmanne39 on 2012-07-09
Hi, please do:
```
sudo modprobe -r ath5k
sudo modprobe ath5k nohwcrypt=Y
```
do not reboot if it works we will need to make it permanent.
Thanks

---

### Post by wnelson on 2012-07-09
I found the following. This may help?

[http://ubuntuforums.org/showthread.php?t=1530962](http://ubuntuforums.org/showthread.php?t=1530962)

walt

---

### Post by Martificiam on 2012-07-15
> **wnelson said:**
> I found the following. This may help?

[http://ubuntuforums.org/showthread.php?t=1530962](http://ubuntuforums.org/showthread.php?t=1530962)

walt

This worked perfectly. Thanks a lot to everyone who helped, now I can completely switch to Linux as my primary desktop environment.

P.S. How do I mark this thread as solved?

---

### Post by wildmanne39 on 2012-07-16
Hi, I am glad it is sorted, you use thread tools at the top of the page to mark the thread solved.
Thanks

---

