---
title: "No Wifi Detected. Natty"
date: 2011-09-22
forum: Networking &amp; Wireless
---

### Post by car0003 on 2011-09-22
Normally when i have issues with ubuntu, i do look for the answers myself. But a few months ago my wifi stopped working, i looked it up online tried all sorts of things and came across [this]("http://ubuntuforums.org/showthread.php?t=1726035")

sudo rmmod -f ath5k
sudo rfkill unblock all
sudo modprobe ath5k

Anyways it worked and i had wifi running for about 2 weeks,then i lent it to my nephew and it stopped working. so i tried that again to no avail. And now here i am. so if you could please help me id really appreciate it :)

oh btw i have an AR5001 Wireless Network Adapter and Ubuntu 11.04, and can only connect online if i plug in an ethernet cable

---

### Post by wildmanne39 on 2011-09-22
Hi, please post the results of these commands:
```
cat /etc/lsb-release; uname -a
```
```
sudo lshw -C network 
```
```
lspci -nnk | grep -iA2 net
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
```
nm-tool
```
```
sudo iwlist scan
```
```
dmesg | egrep 'ath|firm|radio|switch|wlan0'
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by car0003 on 2011-09-22
...

---

### Post by car0003 on 2011-09-22
Thank you, Heres the info: 
```


**cat /etc/lsb-release; uname -a**

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux carlos-Compaq-Presario-CQ50-Notebook-PC 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686 athlon i386 GNU/Linux

**sudo lshw -C network**

  *-network               
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1d:72:6a:74:4a
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.107 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 memory:c0009000-c0009fff ioport:30f8(size=8) memory:c0007c00-c0007cff memory:c0007800-c000780f
  *-network DISABLED
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 00:22:68:ad:df:06
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.38-11-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:23 memory:c2000000-c200ffff


**lspci -nnk | grep -iA2 net**

00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP77 Ethernet [10de:0760] (rev a2)
	Subsystem: Hewlett-Packard Company Device [103c:360a]
	Kernel driver in use: forcedeth
--
07:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:137a]
	Kernel driver in use: ath5k

**iwconfig**

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


**rfkill list all**
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
2: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no


**lsmod**

Module                  Size  Used by
ath5k                 144534  0 
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_conexant    43782  1 
nvidia               9766978  42 
snd_hda_intel          24113  4 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
binfmt_misc            13213  1 
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
joydev                 17322  0 
hp_wmi                 13418  0 
snd_seq_midi           13132  0 
sparse_keymap          13666  1 hp_wmi
snd_rawmidi            25269  1 snd_seq_midi
arc4                   12473  2 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
ath                    19141  1 ath5k
mac80211              257001  1 ath5k
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  17 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              156212  3 ath5k,ath,mac80211
psmouse                73312  0 
soundcore              12600  1 snd
shpchp                 32345  0 
k10temp                12951  0 
serio_raw              12990  0 
video                  18951  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_nforce2            12906  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usb_storage            43946  0 
uas                    17676  0 
ahci                   21591  2 
libahci                25548  1 ahci
forcedeth              58190  0 
pata_amd               13762  0 


**nm-tool**

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             connected
  Default:           yes
  HW Address:        00:1D:72:6A:74:4A

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.107
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             209.18.47.61
    DNS:             209.18.47.62


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             unavailable
  Default:           no
  HW Address:        00:22:68:AD:DF:06

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


**sudo iwlist scan**

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

**dmesg | egrep 'ath|firm|radio|switch|wlan0'**
[    1.186773] device-mapper: multipath: version 1.2.0 loaded
[    1.186777] device-mapper: multipath round-robin: version 1.0.0 loaded
[   19.110072] ath5k 0000:07:00.0: PCI INT A -> Link[Z012] -> GSI 23 (level, low) -> IRQ 23
[   19.110086] ath5k 0000:07:00.0: setting latency timer to 64
[   19.110148] ath5k 0000:07:00.0: registered as 'phy0'
[   19.609942] ath: EEPROM regdomain: 0x64
[   19.609946] ath: EEPROM indicates we should expect a direct regpair map
[   19.609951] ath: Country alpha2 being used: 00
[   19.609954] ath: Regpair used: 0x64
[   19.620646] Registered led device: ath5k-phy0::rx
[   19.620703] Registered led device: ath5k-phy0::tx
[   19.620719] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   19.767759] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.633296] Console: switching to colour frame buffer device 80x30
[ 2655.908739] ath5k 0000:07:00.0: PCI INT A disabled
[ 2690.261099] ath5k 0000:07:00.0: PCI INT A -> Link[Z012] -> GSI 23 (level, low) -> IRQ 23
[ 2690.261115] ath5k 0000:07:00.0: setting latency timer to 64
[ 2690.261179] ath5k 0000:07:00.0: registered as 'phy1'
[ 2690.760265] ath: EEPROM regdomain: 0x64
[ 2690.760268] ath: EEPROM indicates we should expect a direct regpair map
[ 2690.760273] ath: Country alpha2 being used: 00
[ 2690.760275] ath: Regpair used: 0x64
[ 2690.761656] Registered led device: ath5k-phy1::rx
[ 2690.761691] Registered led device: ath5k-phy1::tx
[ 2690.761701] ath5k phy1: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
```

---

### Post by wildmanne39 on 2011-09-22
Hi, it shows that the hardware switch is off do you have a switch that turns is on and off? or is it like fn r2? you may want to check in your bios also, if that does not turn it on post back and we will go from there.
Thank you

---

### Post by car0003 on 2011-09-22
> **wildmanne39 said:**
> Hi, it shows that the hardware switch is off do you have a switch that turns is on and off? or is it like fn r2? you may want to check in your bios also, if that does not turn it on post back and we will go from there.
Thank you

I do have a button, but it only worked on vista. then i replaced vista w/ ubuntu 9.04 a while ago. Ever since then the button doesnt do anything.
Also i dont know how to do it from the bios. i tried restarting it several times to check F10> Bios Setup but i didnt see anything regarding wifi.

PS.up where the icon is that shows the ethernet cable, theres an option that says "enable wireless". Sometimes its grayed out, but other times like now i can check it, however it doesnt seem to affect anything.

---

### Post by wildmanne39 on 2011-09-22
Hi, see if this helps, disconnect your wired connection then run the command if it helps we will need to make it permanent, if it does not restart your computer and we will go from there.
```
rmmod -f hp-wmi
```
Thank you

---

### Post by car0003 on 2011-09-22
> **wildmanne39 said:**
> Hi, see if this helps, disconnect your wired connection then run the command if it helps we will need to make it permanent, if it does not restart your computer and we will go from there.
```
rmmod -f hp-wmi
```
Thank you


i got this
```
ERROR: Removing 'hp_wmi': Operation not permitted
```

---

### Post by wildmanne39 on 2011-09-22
Hi, sorry my mistake it should have been:
```
sudo rmmod -f hp-wmi
```
Thank you

---

### Post by car0003 on 2011-09-22
> **wildmanne39 said:**
> Hi, sorry my mistake it should have been:
```
sudo rmmod -f hp-wmi
```
Thank you

thats ok, but this time i got this
```
ERROR: Removing 'hp_wmi': No such file or directory
```

---

### Post by wildmanne39 on 2011-09-22
Hi, that is okay, I did not think it would work but I need to eliminate it from the list.

I am going to ask a good friend to help out,
Thank you

---

### Post by car0003 on 2011-09-22
> **wildmanne39 said:**
> Hi, that is okay, I did not think it would work but I need to eliminate it from the list.

I am going to ask a good friend to help out,
Thank you
ok thank you, when should i check back?

---

### Post by wildmanne39 on 2011-09-22
Hi, he is on line, he will probably be here in a few minutes, and he is the Doctor when it come to these matters, he has mad skills.
Thank you

---

### Post by car0003 on 2011-09-22
oh, ok, thank you. i very much appreciate it :)

---

### Post by wildmanne39 on 2011-09-22
Hi, he had to get off for a little while, so let's try this.

Turn your switch off the run: 
```
sudo rfkill unblock all
```
then turn the switch back on with wired unplugged.
Thank you

---

### Post by wildmanne39 on 2011-09-22
Hi, if that does not work post the results of:

```
cat /var/lib/NetworkManager/NetworkManager.state
```
Thank you

---

### Post by car0003 on 2011-09-22
> **wildmanne39 said:**
> Hi, if that does not work post the results of:

```
cat /var/lib/NetworkManager/NetworkManager.state
```
Thank you

i tried but nothing happaned
```
sudo rfkill unblock all
```

```
[main]
**cat /var/lib/NetworkManager/NetworkManager.state** gives me this

NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

```

---

### Post by wildmanne39 on 2011-09-22
Hi, that looked good, this is from one of chili555's post, I have not tried it before because you said it does not work when you do it manually anymore, but this will make it permanent so let's try it, it will not hurt anything.
```
gksudo gedit /etc/rc.local
```
Add your three lines above exit 0 without sudo:
```
rmmod -f ath5k
rfkill unblock all
modprobe ath5k
```
Proofread carefully, save and close gedit. Reboot and tell us if it's working.
Thank you

---

### Post by car0003 on 2011-09-22
THANK YOU SOOOO MUCH!!!!!
It works! im responding from the wifi right now, i really appreciated the help :D

---

### Post by wildmanne39 on 2011-09-22
Hi, that is great, I wish I had done that in the first place, because that was my first thought, your very welcome! Enjoy ubuntu and wireless, and thank you to chili555 for having posted it in another thread.

---

### Post by chili555 on 2011-09-22
Glad you have it all sorted. Have fun!

---

