---
title: "Problems with rt2800"
date: 2010-10-27
forum: Networking &amp; Wireless
---

### Post by davm92 on 2010-10-27
Hi, i have a touchsmart 300 wich worked fine with the last version (lucig lynx) of ubuntu, (in fact i had to make a change in the /etc/Wireless directory to make my wirless work)
```
sudo mkdir /etc/Wireless
sudo mkdir /etc/Wireless/RT2860STA
sudo gedit /etc/Wireless/RT2860STA/RT2860STA.dat
Default
```Now that i've upgraded the wireless card doesnt work any more, after some research in the forum I made the conclussion that the change in /etc/Wireless is affecting the dirvers that came with the new version (maverik). but before blacklisting( I *dont know how to do that) *whats your opinion, here there are some codes, feel fre to ask me for more.

**sudo iwconfig**
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
diego@diego-desktop:~$ lspci | grep -i network
02:00.0 Network controller: RaLink RT3092 Wireless 802.11n 2T/2R PCIe
```**nm-tool**
```
NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             disconnected
  Default:           no
  HW Address:        00:26:82:76:CB:85

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        70:71:BC:40:21:5C

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off
```[B]sudo lshw -C network
[/B]```
 *-network DISABLED      
       description: Wireless interface
       product: RT3092 Wireless 802.11n 2T/2R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:26:82:76:cb:85
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.35-22-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:feaf0000-feafffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: 70:71:bc:40:21:5c
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:42 ioport:e800(size=256) memory:febff000-febfffff memory:fdffc000-fdffffff memory:febc0000-febdffff
```[B]lsmod | grep rt2
[/B]```
rt2860sta             559618  0 
rt2800pci              10233  0 
rt2800lib              31970  1 rt2800pci
rt2x00usb              11316  1 rt2800lib
rt2x00pci               6993  1 rt2800pci
crc_ccitt               1699  2 rt2860sta,rt2800pci
rt2x00lib              31575  4 rt2800pci,rt2800lib,rt2x00usb,rt2x00pci
led_class               3393  1 rt2x00lib
mac80211              266657  3 rt2x00usb,rt2x00pci,rt2x00lib
cfg80211              170293  2 rt2x00lib,mac80211
eeprom_93cx6            1789  1 rt2800pci
```

---

### Post by MooPi on 2010-10-27
Can you determine if it is scanning for or can see the available networks ?
Try this in terminal  ```
iwlist scanning
``` 
Post results back here

---

### Post by chili555 on 2010-10-27
Your card will work with either rt2860sta or rt2800pci and its dependents but probably not both. Let's blacklist the rt2800pci family and see if we get it working. In a terminal, please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add four new lines:```
blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread carefully, save and close gedit.

Reboot and post back and tell us how it's working.

---

### Post by not_a_phd on 2010-10-27
> **chili555 said:**
> Your card will work with either rt2860sta or rt2800pci and its dependents but probably not both. Let's blacklist the rt2800pci family and see if we get it working. In a terminal, please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add four new lines:```
blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread carefully, save and close gedit.

Reboot and post back and tell us how it's working.

Will this do anything if he doesn't also blacklist rt2800pci and rt2x00pci? I have similar issues on an eeepc 901. Perhaps the difference is that it works fine on my home WEP network (except when waking up from hibernate). It hasn't worked at my work WPA network since I installed from the live CD. 

When I blacklist the pci items along with your 4, it won't connect on the WEP network. When I only blacklist your 4, it appears as if they load anyway. (children of the pci modules?)

---

### Post by not_a_phd on 2010-10-27
UPDATE: I blacklisted rt2860sta on my machine. The WEP networking still worked. It came back after a hibernate cycle. Will try it on a WPA network tomorrow...

---

### Post by chili555 on 2010-10-27
> Will this do anything if he doesn't also blacklist rt2800pci and rt2x00pci? You are correct; my bad. Those need to be blacklisted, too.

---

### Post by davm92 on 2010-10-28
thanks chili555 and not_a_phd, you and me were right, thanks to the other users which contributed to the answer, my wireless is now working.

---

### Post by not_a_phd on 2010-10-28
> **davm92 said:**
> thanks chili555 and not_a_phd, you and me were right, thanks to the other users which contributed to the answer, my wireless is now working.

I am glad for you...Mine is sort of working at this point... It looks like I need to blacklist rt2860sta when I am at home, and blacklist the rt2800 and rt2x00 family when I am at work. 

I think the best way to handle this perhaps is with a script. I know how to remove these modules using the rmmod command. Do I insert the correct ones with insmod? if so, where do I locate the .ko files?

---

### Post by chili555 on 2010-10-28
> Do I insert the correct ones with insmod? if so, where do I locate the .ko files?insmod, which requires the absolute path to the module, is not the handiest way to do this. I suggest:```
sudo modprobe rt2860sta
```It's hard to accept that one module works at home but not at work and vice versa; but I guess anything is possible.

To find the location of any module, do:```
modinfo yourmodule
```For example:```
modinfo rt2860sta
filename:       [COLOR="Red"]/lib/modules/2.6.35-22-generic/kernel/drivers/staging/rt2860/rt2860sta.ko[/COLOR]
version:        2.1.0.0
alias:          rt3090sta
license:        GPL
description:    RT2860/RT3090 Wireless Lan Linux Driver
etc., etc.
```

---

### Post by not_a_phd on 2010-10-28
> **chili555 said:**
> It's hard to accept that one module works at home but not at work and vice versa; but I guess anything is possible.




I hear you. At this point it seems that neither driver-set provides a completely stable solution. I just tried to sleep the machine, and when it came back up, the wireless would not reconnect. 

I think I have seen some other threads in this category that address that issue, so I am off to find them!

---

### Post by mja on 2010-10-30
After blacklisting rt2xxpci and rt2800pci plus adding rt2860 and rt2860sta to /etc/modules I've got 2.4ghz wifi-n working but I can't get 5ghz. Anyone managed to do this? Adding /etc/Wireless/RT2860STA/RT2860STA.dat doesn't help.

Help.. anyone? The platform is Zotac H55ITX-C-E with the rt2860 mini pcie card (I think). Are there any alternative cards/chipsets that would work out of the box on Ubuntu (AR9280 maybe??)

Edit: seems to be version 2.1.0.0 rt2860sta. Ralink has 2.4.0.0 available. Worth compiling?

---

### Post by chili555 on 2010-10-30
> Adding /etc/Wireless/RT2860STA/RT2860STA.dat doesn't help.
Is Wireless Mode set to 9? Is HT_BW set to 1?

If so, I have no further suggestions.

---

### Post by mja on 2010-10-31
> **chili555 said:**
> Is Wireless Mode set to 9? Is HT_BW set to 1?

If so, I have no further suggestions.

Wireless Mode seemed to be 5 so I changed it to 9.. no effect unfortunately. Seems like the whole file is ignored. On the other hand, I noticed that my connection according to iwconfig is 54Mbit/s so I guess it's wireless-g and not wireless-n to begin with :( What a crappy chipset and crappy driver. My router has dual bands, 2.4ghz set to wpa2-aes 130Mbit/s and 5ghz set to 300Mbit/s wpa2-aes so I don't think it's the router that's at fault.

I'm strongly considering just thrashing the RT2860 and getting a Wifi Link 5300 (which I guess is known to have problems with Netgear WNDR3700 that I have) or Atheros 9280 (Linux driver problems?). Any suggestions as to which card to upgrade to?

---

### Post by chili555 on 2010-10-31
> I noticed that my connection according to iwconfig is 54Mbit/s so I guess it's wireless-g and not wireless-n to begin with AFAIK, that just means that's the speed that is currently in use, not the maximum it's capable of.

Is there an indication in dmesg of whether the file is being used?```
dmesg | grep -i rt2
```

I am a big fan of Intel chipsets; I have two lappys using them and have swapped out one for a faster one. I have no experience with mini-pci cards other than Intel. Mine have been perfect. I have no N hardware, however.

---

### Post by mja on 2010-10-31
> **chili555 said:**
> AFAIK, that just means that's the speed that is currently in use, not the maximum it's capable of.

Is there an indication in dmesg of whether the file is being used?```
dmesg | grep -i rt2
```

I am a big fan of Intel chipsets; I have two lappys using them and have swapped out one for a faster one. I have no experience with mini-pci cards other than Intel. Mine have been perfect. I have no N hardware, however.
Cheers for the help! Will probably get the intel 5300 chip. I couldn't check the dmesg because I once again ended in not being able to boot ubuntu due to what I believe is an intel hd graphics related problem (combined with the Zotac hardware). I thought I fixed it by doing some mtrr-related magic but nope.. Will try Opensuse next.

---

### Post by not_a_phd on 2010-10-31
Ugh. I have been fighting this for a week now, but I am highly motivated to see this through.

10.10 install. eeePC901, rt2860 chipset, running freshly compiled rt2860sta.ko module, blacklisting the rt2800 and rt2x00 stuff that came with stock Ubuntu. 

So after following some directions for patching RaLink's drivers (from Sven if I am not mistaken), and installing the RaLink firmware, I am able to connect to both a WEP and a WPA access point with a common driver configuration. 

The problem now is that my connection is not quite right. In the background, it is disconnecting and reconnecting about once every 5-seconds. I can see the following repeat every 5-sec when tailing my syslog:

```

Oct 31 14:39:39 jim-laptop-0 NetworkManager[768]: <info> (ra0): supplicant connection state:  associated -> completed
Oct 31 14:39:44 jim-laptop-0 wpa_supplicant[807]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Oct 31 14:39:44 jim-laptop-0 wpa_supplicant[807]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Oct 31 14:39:44 jim-laptop-0 NetworkManager[768]: <info> (ra0): supplicant connection state:  completed -> disconnected
Oct 31 14:39:44 jim-laptop-0 wpa_supplicant[807]: Trying to associate with SSID 'roxiedog'
Oct 31 14:39:44 jim-laptop-0 NetworkManager[768]: <info> (ra0): supplicant connection state:  disconnected -> scanning
Oct 31 14:39:44 jim-laptop-0 NetworkManager[768]: <info> (ra0): supplicant connection state:  scanning -> associating
Oct 31 14:39:46 jim-laptop-0 kernel: [ 5126.839732] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 104
Oct 31 14:39:46 jim-laptop-0 wpa_supplicant[807]: Associated with 00:0f:66:0b:32:f7
Oct 31 14:39:46 jim-laptop-0 wpa_supplicant[807]: CTRL-EVENT-CONNECTED - Connection to 00:0f:66:0b:32:f7 completed (reauth) [id=1 id_str=]
Oct 31 14:39:46 jim-laptop-0 NetworkManager[768]: <info> (ra0): supplicant connection state:  associating -> associated
Oct 31 14:39:46 jim-laptop-0 NetworkManager[768]: <info> (ra0): supplicant connection state:  associated -> completed
Oct 31 14:39:53 jim-laptop-0 wpa_supplicant[807]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Oct 31 14:39:53 jim-laptop-0 wpa_supplicant[807]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Oct 31 14:39:53 jim-laptop-0 NetworkManager[768]: <info> (ra0): supplicant connection state:  completed -> disconnected
Oct 31 14:39:53 jim-laptop-0 wpa_supplicant[807]: Trying to associate with SSID 'roxiedog'
Oct 31 14:39:53 jim-laptop-0 NetworkManager[768]: <info> (ra0): supplicant connection state:  disconnected -> scanning
Oct 31 14:39:53 jim-laptop-0 NetworkManager[768]: <info> (ra0): supplicant connection state:  scanning -> associating
Oct 31 14:39:55 jim-laptop-0 NetworkManager[768]: <info> (ra0): roamed from BSSID 00:0F:66:0B:32:F7 (roxiedog) to (none) ((none))
Oct 31 14:39:55 jim-laptop-0 kernel: [ 5135.858012] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 104
Oct 31 14:39:55 jim-laptop-0 wpa_supplicant[807]: Associated with 00:0f:66:0b:32:f7
Oct 31 14:39:55 jim-laptop-0 wpa_supplicant[807]: CTRL-EVENT-CONNECTED - Connection to 00:0f:66:0b:32:f7 completed (reauth) [id=1 id_str=]

```

When I ping my router, I drop packets during these disconnect/reconnect events. The situation is far worse when running wicd instead of NetworkManager. With wicd, it does not auto-reconnect. 

I am using a Wireless-G router, so I dropped back to WirelessMode=4 in the RT2860STA.dat file. My questions are as follows:
1. Has anyone else seen (and fixed) this behavior?
2. Why is the wpa_supplicant running when I am in WEP mode?
3. What is the significance of the rt_ioctl_giwscan error ?

I feel like I am very close to resolution...Thank you in advance for your help!!

---

### Post by mja on 2010-11-02
As an update, Opensuse worked wrt graphics related problems but as I wanted to easily use Nokia QT SDK I decided to return to Kubuntu and am now experimenting with 10.04 that seems to work somewhat better than 10.10. I ordered the AR9280 which seems to work out of the box on 10.04, both 2.4ghz and 5ghz! And it cost only 15 pounds so a good deal. 

I also feel a bit noobish as it turns out the card installed in the Zotac MB is actually an Azurewave with RT2700E that is _single_ band and not even dual band.... The label is under the card so I only found this out having swapped the new Atheros card in. lspci reports the card as RT2860 which led me to believe it might be a dual-band card.

Edit: AR9280 works really slow out of the box but having installed compat-wireless it's full awesome.

---

### Post by cb_rex on 2010-11-27
I'm having some similar depressing poor performance and frequent connection drop issues with this wireless card (Linksys WMP600N).  

I've created the "/etc/Wireless/RT2860STA/RT2860STA.dat" file and have updated the blocklist to stop the RT2800 conflict, however now I can't even see my WPA2 dual band wireless-N network, never mind connect to it.  The best I currently get is an unstable 24Mb/s wireless-G connection.

Any help with this network adaptor would be most appreciated.

---

### Post by chili555 on 2010-11-27
Please post:```
lsmod | grep rt2
dmesg | grep rt2
lspci -nn
```The last command will output a lot of data unrelated to your Linksys; feel free to strip it away.

---

### Post by cb_rex on 2010-11-27
Thanks for the quick response. 

Output from lsmod | grep rt2
> rt2860sta             559618  1 
crc_ccitt               1699  1 rt2860sta

Output from dmesg | grep rt2
> [    2.489523] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
[    2.494766] rt2860 0000:05:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    5.350144] <==== rt28xx_init, Status=0
[    5.446827] <==== rt28xx_init, Status=0
[  115.456842] <==== rt28xx_init, Status=0
[  237.634040] <==== rt28xx_init, Status=0
[ 7597.613980] <==== rt28xx_init, Status=0
[ 7678.236384] <==== rt28xx_init, Status=0
[ 7820.205112] <==== rt28xx_init, Status=0
[ 7902.287570] <==== rt28xx_init, Status=0
[ 7961.195168] <==== rt28xx_init, Status=0
[10290.245200] <==== rt28xx_init, Status=0


And finally the output from lspci -nn
> 00:00.0 Host bridge [0600]: Intel Corporation 4 Series Chipset DRAM Controller [8086:2e20] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 4 Series Chipset PCI Express Root Port [8086:2e21] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4 [8086:3a37]
00:1a.1 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5 [8086:3a38]
00:1a.2 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6 [8086:3a39]
00:1a.7 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 [8086:3a3c]
00:1b.0 Audio device [0403]: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller [8086:3a3e]
00:1c.0 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1 [8086:3a40]
00:1c.4 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5 [8086:3a48]
00:1c.5 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6 [8086:3a4a]
00:1d.0 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1 [8086:3a34]
00:1d.1 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2 [8086:3a35]
00:1d.2 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3 [8086:3a36]
00:1d.7 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 [8086:3a3a]
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 90)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801JIB (ICH10) LPC Interface Controller [8086:3a18]
00:1f.2 IDE interface [0101]: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1 [8086:3a20]
00:1f.3 SMBus [0c05]: Intel Corporation 82801JI (ICH10 Family) SMBus Controller [8086:3a30]
00:1f.5 IDE interface [0101]: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2 [8086:3a26]
01:00.0 VGA compatible controller [0300]: nVidia Corporation GT200 [GeForce GTX 260] [10de:05e2] (rev a1)
02:00.0 Ethernet controller [0200]: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)
03:00.0 IDE interface [0101]: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface [11ab:6101] (rev b2)
05:02.0 Network controller [0280]: RaLink RT2800 802.11n PCI [1814:0601]

---

### Post by chili555 on 2010-11-27
Please let us see:```
ls /lib/firmware | grep -e rt2 -e rt3
cat /etc/Wireless/RT2860STA/RT2860STA.dat 
iwconfig
rfkill list all
```Your dmesg is a bit mystifying; there is no obvious error to fix, yet all we see are messages that seem to be turning the card off. Can you confirm that the wired ethernet is detached?

---

### Post by cb_rex on 2010-11-28
There is no Ethernet cable connected, the speed and reported signal strength seem to be fluctuating then the connection will drop every few minutes. 

output of:
ls /lib/firmware | grep -e rt2 -e rt3
> intelliport2.bin
rt2561.bin
rt2561s.bin
rt2661.bin
rt2860.bin
rt2870.bin
rt3070.bin
rt3071.bin
rt3090.bin

output of:
cat /etc/Wireless/RT2860STA/RT2860STA.dat 
> #The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=
ChannelGeography=1
SSID=Dennis2860AP
NetworkType=Infra
WirelessMode=5
Channel=0
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
PktAggregate=0
WmmCapable=1
AckPolicy=0;0;0;0
AuthMode=OPEN
EncrypType=NONE
WPAPSK=
DefaultKeyID=1
Key1Type=0
Key1Str=
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
PSMode=CAM
AutoRoaming=0
RoamThreshold=70
APSDCapable=0
APSDAC=0;0;0;0
HT_RDG=1
HT_EXTCHA=0
HT_OpMode=0
HT_MpduDensity=4
HT_BW=1
HT_AutoBA=1
HT_BADecline=0
HT_AMSDU=0
HT_BAWinSize=64
HT_GI=1
HT_MCS=33
HT_MIMOPSMode=3
HT_DisallowTKIP=1
HT_STBC=0
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0
CarrierDetect=0
AntDiversity=0
BeaconLostTime=4
PSP_XLINK_MODE=0
RadioOn=1

output of:
iwconfig
> lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     Ralink STA  ESSID:"DragonFly-G"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.427 GHz  Access Point: 30:46:9A:32:FF:0D   
          Bit Rate=24 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=86/100  Signal level:-76 dBm  Noise level:-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


"rfkill list all" doesn't output anything.

---

### Post by not_a_phd on 2010-12-04
cb_rex, did you ever find a fix?

Your signal and noise level output from iwconfig seemed odd to me.

> Link Quality=86/100 Signal level:-76 dBm Noise level:-71 dBm


On my machine, the noise floor gets above -80 only when I am quite close to the router. But, the signal level is high in that case (-50dBm). The fact that your reported signal level is below the noise level is not a healthy indicator.

---

### Post by cb_rex on 2010-12-06
I've turned the orientation of the ariels to horizontal which increases the signal strength, but it's still not great, there must be some metal in my walls or something, thanks for the help everyone.

---

### Post by xv3 on 2010-12-18
using ubuntu 10.10 and was not able to get above 54Mbs till i started reading here. 

Compiled the rt2860sta.ko (v2.4.0.0 from ralink website) and installed it. Now i can connect a wifi-N with speeds ranging from 243MBs to 300MBs (mostly on 270MBs).  Internet connection is a stable 60Mbs. 

I connect to a Linksys Wrt610n with two networks (2.4Ghz and 5GHz). 

Connecting to the 2.4Ghz network, i get a connection of 270Mbs. But my ping times to the router are so bad i cannot load a website (or wait minutes). 

Connecting to the 5Ghz network gives me a connection of just 13.5Mbs but gives ping times between 0.8-1.2 miliseconds

.. connected tot the 5Ghz network 
4 bytes from 192.168.1.1: icmp_req=11 ttl=64 time=0.910 ms
64 bytes from 192.168.1.1: icmp_req=12 ttl=64 time=0.893 ms
64 bytes from 192.168.1.1: icmp_req=13 ttl=64 time=0.900 ms
64 bytes from 192.168.1.1: icmp_req=14 ttl=64 time=1.41 ms
64 bytes from 192.168.1.1: icmp_req=15 ttl=64 time=1.36 ms

... switching to the 2.4Ghz network
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
64 bytes from 192.168.1.1: icmp_req=20 ttl=64 time=3865 ms
64 bytes from 192.168.1.1: icmp_req=21 ttl=64 time=3691 ms
64 bytes from 192.168.1.1: icmp_req=30 ttl=64 time=697 ms
64 bytes from 192.168.1.1: icmp_req=32 ttl=64 time=568 ms
64 bytes from 192.168.1.1: icmp_req=35 ttl=64 time=413 ms
64 bytes from 192.168.1.1: icmp_req=36 ttl=64 time=547 ms
64 bytes from 192.168.1.1: icmp_req=38 ttl=64 time=519 ms
64 bytes from 192.168.1.1: icmp_req=40 ttl=64 time=652 ms
and it stays at this level. 

iwconfig when connected to the 5Ghz network: 
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"linksys_media"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=5.26 GHz  Access Point: <removed>   
          Bit Rate=13.5 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:<removed>
          Link Quality=70/100  Signal level:-91 dBm  Noise level:-93 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

 Ralink STA  ESSID:"linksys"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.472 GHz  Access Point: <removed>
          Bit Rate=270 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key: <removed>
          Link Quality=98/100  Signal level:-68 dBm  Noise level:-78 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Both networks are configured to get their IP and DNS through DHCP.


update: after enabling the blacklisted RT2800pci/usb/lib and a reboot the connection was back to 54Mbs. So i blacklisted those modules again. But somehow this solved my huge ping times also. They are back at 1 ms.

---

### Post by xv3 on 2010-12-27
hmm, the problems in my last post are back (large ping times). Any idea how to solve this?
 
Also Unbuntu hangs completly several times if for example watching youtube, or changing some network connections. Might be that the compiled RT2860 module is still up to some troubles.

---

