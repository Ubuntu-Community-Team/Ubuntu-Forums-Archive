---
title: "Lenovo s205 ubuntu 13.04"
date: 2013-06-13
forum: Networking &amp; Wireless
---

### Post by soeki on 2013-06-13
Hi! To start with: I am a complete newbie to Linux and Ubuntu, so please bear with me if I don or say anything stupid. 

My problem is: I have upgraded ubuntu 12.10 to ubuntu 13.04. Before that I have used 12.10 with wubi and have then migrated it to a partition with the help of a script. Now 13.04 is up and running with one exception:
The wifi connection doesn't work. It doesn't show my wifi network and I can't enable wifi connections. I have tried many things which I have found here in the forum especially in that thread: 

[http://ubuntuforums.org/showthread.php?t=2143840 ]("http://ubuntuforums.org/showthread.php?t=2143840")

But either I don't get what they mean or it doesn't work for me. To give you as much information as possible I have just entered the same in terminal as the (at least to me) more experienced user in that thread. So I hope it gives you a good overview over the status of my failing wifi connection. 

    >> cat /etc/lsb-release 

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu 13.04"
```


>> lsusb


```
Bus 002 Device 002: ID 04f2:b278 Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 0bda:0139 Realtek Semiconductor Corp. Card reader
Bus 003 Device 002: ID 0489:e00d Foxconn / Hon Hai Broadcom Bluetooth 2.1 Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```


>>lspci -k -nn | grep -A 3 -i net 

```
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Lenovo Device [17aa:397b]
    Kernel driver in use: r8169
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Lenovo Device [17aa:30a1]

```


>>sudo lshw -C network 

```
*-network               
       Beschreibung: Ethernet interface
       Produkt: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       Hersteller: Realtek Semiconductor Co., Ltd.
       Physische ID: 0
       Bus-Informationen: pci@0000:02:00.0
       Logischer Name: eth0
       Version: 05
       Seriennummer: f0:de:f1:d1:68:8b
       Größe: 100Mbit/s
       Kapazität: 100Mbit/s
       Breite: 64 bits
       Takt: 33MHz
       Fähigkeiten: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       Konfiguration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.1.6 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       Ressourcen: irq:42 ioport:1000(Größe=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network UNGEFORDERT
       Beschreibung: Network controller
       Produkt: AR9285 Wireless Network Adapter (PCI-Express)
       Hersteller: Atheros Communications Inc.
       Physische ID: 0
       Bus-Informationen: pci@0000:03:00.0
       Version: 01
       Breite: 64 bits
       Takt: 33MHz
       Fähigkeiten: pm msi pciexpress bus_master cap_list
       Konfiguration: latency=0
       Ressourcen: memory:f0100000-f010ffff
```

>>   lsmod 

```
Module                  Size  Used by
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  12 
bnep                   18036  2 
binfmt_misc            17500  1 
snd_hda_codec_conexant    62000  1 
snd_hda_codec_hdmi     36913  1 
joydev                 17377  0 
acer_wmi               32467  0 
kvm_amd                59717  0 
kvm                   443165  1 kvm_amd
microcode              22881  0 
rts5139               352481  0 
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
psmouse                95870  0 
serio_raw              13215  0 
ideapad_laptop         18394  0 
sparse_keymap          13890  2 acer_wmi,ideapad_laptop
k10temp                13126  0 
ath_pci               198355  0 
wlan                  248398  1 ath_pci
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
snd_hda_intel          39619  5 
snd_hda_codec         136453  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
video                  19390  1 acer_wmi
wmi                    19070  1 acer_wmi
ath_hal               426954  1 ath_pci
mac_hid                13205  0 
radeon                937749  3 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
sp5100_tco             13735  0 
i2c_piix4              13266  0 
snd_timer              29425  2 snd_pcm,snd_seq
ttm                    83187  1 radeon
snd                    68876  20 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
drm_kms_helper         49394  1 radeon
drm                   286313  5 ttm,drm_kms_helper,radeon
soundcore              12680  1 snd
btusb                  22474  0 
bluetooth             228619  22 bnep,btusb,rfcomm
i2c_algo_bit           13413  1 radeon
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
r8169                  67446  0 
ahci                   25731  1 
libahci                31364  1 ahci

```



>>    iwconfig 

```
eth0      no wireless extensions.

lo        no wireless extensions.

```

>>    ifconfig -a 

```
eth0      Link encap:Ethernet  Hardware Adresse f0:de:f1:d1:68:8b  
          inet Adresse:192.168.1.6  Bcast:192.168.1.255  Maske:255.255.255.0
          inet6-Adresse: fe80::f2de:f1ff:fed1:688b/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:88851 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46781 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX-Bytes:68406757 (68.4 MB)  TX-Bytes:3569370 (3.5 MB)

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:65536  Metrik:1
          RX packets:755 errors:0 dropped:0 overruns:0 frame:0
          TX packets:755 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX-Bytes:63202 (63.2 KB)  TX-Bytes:63202 (63.2 KB)

```


>>sudo iwlist scan 

```
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

```


>>uname -r -m

```
3.8.0-23-generic x86_64
```


>>    cat /etc/network/interfaces 

```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```


>>nm-tool 



```
NetworkManager Tool

State: connected (global)

- Device: eth0  [Kabelnetzwerkverbindung 1] ------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        F0:DE:F1:D1:68:8B

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

```


>>sudo rfkill list 

```
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

It seems to me, that i don't have the same problem as the one which is described in the quoted thread. Especially the entry I get under >>iwconfig is different
and worries me... Is there anyone who can help? Thank you very much in advance!

---

### Post by praseodym on 2013-06-14
Try to load the driver by hand:
```

sudo modprobe -v ath9k
```

---

### Post by soeki on 2013-06-15
Thanks! I have tried that and it gives me

```
insmod /lib/modules/3.8.0-23-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.8.0-23-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.8.0-23-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.8.0-23-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko 
insmod /lib/modules/3.8.0-23-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko 
insmod /lib/modules/3.8.0-23-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko 
```

But there is still no wifi...

---

### Post by praseodym on 2013-06-15
Check now:
```

iwconfig
lsmod
rfkill list
dmesg | grep ath
sudo iwlist scan
cat /etc/resolv.conf
route -n
```Any button, switch, key or key combination?

---

### Post by soeki on 2013-06-16
Ok, here is what I get:

iwconfig

```
eth0      no wireless extensions.

lo        no wireless extensions.
```



lsmod

```
Module                  Size  Used by
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  12 
bnep                   18036  2 
snd_hda_codec_conexant    62000  1 
snd_hda_codec_hdmi     36913  1 
joydev                 17377  0 
binfmt_misc            17500  1 
acer_wmi               32467  0 
kvm_amd                59717  0 
kvm                   443165  1 kvm_amd
rts5139               352481  0 
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
microcode              22881  0 
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
psmouse                95870  0 
serio_raw              13215  0 
ath_pci               198355  0 
ideapad_laptop         18394  0 
sparse_keymap          13890  2 acer_wmi,ideapad_laptop
snd_hda_intel          39619  5 
snd_hda_codec         136453  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
wlan                  248398  1 ath_pci
snd_rawmidi            30180  1 snd_seq_midi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
ath_hal               426954  1 ath_pci
radeon                937749  3 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
video                  19390  1 acer_wmi
btusb                  22474  0 
snd_timer              29425  2 snd_pcm,snd_seq
ttm                    83187  1 radeon
mac_hid                13205  0 
wmi                    19070  1 acer_wmi
drm_kms_helper         49394  1 radeon
bluetooth             228619  22 bnep,btusb,rfcomm
k10temp                13126  0 
drm                   286313  5 ttm,drm_kms_helper,radeon
snd                    68876  20 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
sp5100_tco             13735  0 
lp                     17759  0 
i2c_algo_bit           13413  1 radeon
i2c_piix4              13266  0 
parport                46345  3 lp,ppdev,parport_pc
soundcore              12680  1 snd
r8169                  67446  0 
ahci                   25731  1 
libahci                31364  1 ahci
```


rfkill list

```
1: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```



dmesg | grep ath


```
[    1.252000] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 56e46bc0cb04523939d9ba580c4ec55a355d1a93
```




sudo iwlist scan

```
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

```










cat /etc/resolv.conf


```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search localdomain
```








route -n

```
Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
```


> Any button, switch, key or key combination

I don't know what you mean by that. Should I try something? Sorry, if I am a bit slow there. And thank you very much again for your help!

---

### Post by praseodym on 2013-06-16
Unload the following module:
```

sudo rmmod acer_wmi
```
Load the driver again:
```

sudo modprobe -v ath9k
```

---

### Post by soeki on 2013-06-16
I have done this and it gives me the following code:


sudo rmmod acer_wmi

No Code at all. I enter my password and then just a new line to enter a command pops up.



sudo modprobe -v ath9k```
insmod /lib/modules/3.8.0-23-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.8.0-23-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.8.0-23-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.8.0-23-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko 
insmod /lib/modules/3.8.0-23-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko 
insmod /lib/modules/3.8.0-23-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko 
```


Do you think it would be worth considering downgrading to Ubuntu 12.04? Or is it likely that I will have the same problem there? Or is it too early to give up?
Thanks again for your help!

---

### Post by praseodym on 2013-06-16
Try to reset the BIOS settings to default. Please also show:

```
cat /etc/udev/rules.d/70-persistent-net.rules
cat /var/lib/NetworkManager/NetworkManager.state
cat /etc/NetworkManager/NetworkManager.conf 

```

---

### Post by soeki on 2013-06-16
I have reset the BIOS to default. Still there is no wifi connection mentioned in the network drop-down menu.

Here is the code for:


cat /etc/udev/rules.d/70-persistent-net.rules

```
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:15.0/0000:02:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="f0:de:f1:d1:68:8b", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:15.2/0000:03:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="9c:b7:0d:8b:1c:c0", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
```


cat /var/lib/NetworkManager/NetworkManager.state

```
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

```


cat /etc/NetworkManager/NetworkManager.conf

```
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

```

---

### Post by praseodym on 2013-06-17
Is there a possibility to activate wireless in the BIOS settings? Maybe the boot-system needs to be changed to 1) wireless and 2) OS?!

---

### Post by soeki on 2013-06-18
> Is there a possibility to activate wireless in the BIOS settings?

Yes, there is and wireless is enabled in the BIOS settings.


> Maybe the boot-system needs to be changed to 1) wireless and 2) OS

If I enter the setup menu of the BIOS and go to the Boot Priority Order it gives me the following:

1. USB FDD:
2. ATA HDDO: ST9500325AS
3. USB HDD:
4. USB CD
5. PCI LAN: Realtek PXE BO2 DOO

If I enter the multiboot menu under Boot menu I get: 

1. ATA HDDO: ST9500325AS
2. PCI LAN Realtek PXE BO2 DOO

So ist the PCI entry the wireless? I don't dare to change anything there without being sure...

---

### Post by praseodym on 2013-06-18
No, thats for the LAN chip. Try loading the driver forced at boot-up:

```
echo ath9k | sudo tee -a /etc/modules
```
and reboot

---

