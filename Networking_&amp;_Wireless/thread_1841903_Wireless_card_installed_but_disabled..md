---
title: "Wireless card installed but disabled."
date: 2011-09-10
forum: Networking &amp; Wireless
---

### Post by stu_e_hughes on 2011-09-10
I have a PCI wireless card installed which Ubuntu has found and it seems installed drivers for. I cannot get it to become active though. I have 2 screenshots here which say it is disabled and unavailable. Any ideas?

[IMG]http://i36.photobucket.com/albums/e39/stuarthughes/wlan1.png[/IMG]

[IMG]http://i36.photobucket.com/albums/e39/stuarthughes/wlan2.png[/IMG]

---

### Post by wildmanne39 on 2011-09-10
Hi, welcome to the forum! Please run these commands in a terminal and post the results here.
```
sudo lshw -C network 
```
```
lspci -nn | grep 0280
```
```
lsusb
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
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by s031jd on 2011-09-10
Get the ndiswrapper and related packages from the Synaptic Package Manager.  Then run the following commands: 

[LIST]
[*]sudo rfkill list all
[*]rfkill unblock wifi
[*]sudo rfkill list all
[*]sudo ifconfig wlan0 up            -------> wlan0 if that is your wireless device in iwconfig.
[/LIST]
The "rfkill unblock wifi" command should work if you have rfkill installed and it's a soft block.

---

### Post by wildmanne39 on 2011-09-10
Hi, please do not install ndiswrapper until you post the information I asked for it is almost never needed and is he last resort, because it almost never works as well as linux drivers which we have for most cards these days.
Thank you

---

### Post by stu_e_hughes on 2011-09-10
```

stuart@stuart-A7N8X2-0:~$ sudo lshw -C network
[sudo] password for stuart: 
  *-network               
       description: Ethernet interface
       product: nForce2 Ethernet Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth1
       version: a1
       serial: 00:0e:a6:16:bf:01
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.0.4 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100Mbit/s
       resources: irq:22 memory:ea086000-ea086fff ioport:e000(size=8)
  *-network DISABLED
       description: Wireless interface
       product: RT2500 802.11g
       vendor: Ralink corp.
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: wlan0
       version: 01
       serial: 00:11:50:8e:f4:e2
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci driverversion=2.6.38-11-generic firmware=N/A latency=32 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:0 memory:e9010000-e9011fff
  *-network
       description: Ethernet interface
       product: 3C920B-EMB Integrated Fast Ethernet Controller [Tornado]
       vendor: 3Com Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 40
       serial: 00:26:54:16:5e:6a
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=32 link=no maxlatency=10 mingnt=10 multicast=yes port=MII speed=10Mbit/s
       resources: irq:21 ioport:b000(size=128) memory:e5000000-e500007f memory:40100000-4011ffff
stuart@stuart-A7N8X2-0:~$ 

```

```

stuart@stuart-A7N8X2-0:~$ lspci -nn | grep 0280
01:08.0 Network controller [0280]: Ralink corp. RT2500 802.11g [1814:0201] (rev 01)

```

```

stuart@stuart-A7N8X2-0:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```

stuart@stuart-A7N8X2-0:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

```

```

stuart@stuart-A7N8X2-0:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

```

stuart@stuart-A7N8X2-0:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17335  0 
fat                    55505  1 vfat
usb_storage            43946  0 
uas                    17676  0 
lm63                   13998  0 
snd_wavefront          34696  0 
snd_cs4236             29291  0 
snd_wss_lib            30006  2 snd_wavefront,snd_cs4236
snd_opl3_lib           18760  2 snd_wavefront,snd_cs4236
snd_hwdep              13274  2 snd_wavefront,snd_opl3_lib
snd_intel8x0           33213  2 
radeon                900494  3 
snd_ac97_codec        105614  1 snd_intel8x0
arc4                   12473  2 
ac97_bus               12642  1 snd_ac97_codec
rt2500pci              18668  0 
snd_pcm                80042  4 snd_cs4236,snd_wss_lib,snd_intel8x0,snd_ac97_codec
rt2x00pci              13986  1 rt2500pci
rt2x00lib              39075  2 rt2500pci,rt2x00pci
snd_mpu401             13800  0 
snd_mpu401_uart        13865  3 snd_wavefront,snd_cs4236,snd_mpu401
ttm                    65184  1 radeon
snd_seq_midi           13132  0 
drm_kms_helper         40745  1 radeon
mac80211              257001  2 rt2x00pci,rt2x00lib
snd_rawmidi            25269  3 snd_wavefront,snd_mpu401_uart,snd_seq_midi
binfmt_misc            13213  1 
snd_seq_midi_event     14475  1 snd_seq_midi
ppdev                  12849  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  4 snd_wss_lib,snd_opl3_lib,snd_pcm,snd_seq
drm                   184164  5 radeon,ttm,drm_kms_helper
snd_seq_device         14110  4 snd_opl3_lib,snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              156212  2 rt2x00lib,mac80211
i2c_algo_bit           13184  1 radeon
psmouse                73312  0 
eeprom_93cx6           12653  1 rt2500pci
snd                    55295  18 snd_wavefront,snd_cs4236,snd_wss_lib,snd_opl3_lib,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
shpchp                 32345  0 
ns558                  12618  0 
snd_page_alloc         14073  3 snd_wss_lib,snd_intel8x0,snd_pcm
gameport               15027  2 ns558
i2c_nforce2            12906  0 
soundcore              12600  1 snd
parport_pc             32111  1 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
firewire_ohci          31504  0 
pata_amd               13762  0 
sata_sil               13278  2 
firewire_core          56138  1 firewire_ohci
3c59x                  37398  0 
crc_itu_t              12627  1 firewire_core
floppy                 60032  0 
forcedeth              58190  0 


```

---

### Post by wildmanne39 on 2011-09-10
Hi, it looks like you have the right driver loaded, please post the results of these commands.
```
nm-tool
```
```
dmesg | grep wlan0
```
```
dmesg | egrep 'rt2|firm'
```
```
lsmod | grep rt2
```
```
cat /var/lib/NetworkManager/NetworkManager.state
```
Thank you

---

### Post by stu_e_hughes on 2011-09-10
```

stuart@stuart-A7N8X2-0:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth1  [Auto eth1] ----------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             connected
  Default:           yes
  HW Address:        00:0E:A6:16:BF:01

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            3c59x
  State:             unavailable
  Default:           no
  HW Address:        00:26:54:16:5E:6A

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2500pci
  State:             unavailable
  Default:           no
  HW Address:        00:11:50:8E:F4:E2

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 




```

This command does not appear to do anything
```

stuart@stuart-A7N8X2-0:~$ dmesg | grep wlan0
stuart@stuart-A7N8X2-0:~$ dmesg | grep wlan0


```

```

stuart@stuart-A7N8X2-0:~$ dmesg | egrep 'rt2|firm'
[   18.227276] Registered led device: rt2500pci-phy0::radio
[   18.227426] Registered led device: rt2500pci-phy0::quality
[   18.376185] phy0 -> rt2x00pci_initialize: Error - IRQ 0 allocation failed (error -16).
[   18.398656] phy0 -> rt2x00pci_initialize: Error - IRQ 0 allocation failed (error -16).


```

```

stuart@stuart-A7N8X2-0:~$ lsmod | grep rt2
rt2500pci              18668  0 
rt2x00pci              13986  1 rt2500pci
rt2x00lib              39075  2 rt2500pci,rt2x00pci
mac80211              257001  2 rt2x00pci,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211
eeprom_93cx6           12653  1 rt2500pci


```

```

stuart@stuart-A7N8X2-0:~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


```

---

### Post by wildmanne39 on 2011-09-10
Hi, I forgot one I need to see this too please:
```
sudo iwlist scan
```
Thank you

---

### Post by stu_e_hughes on 2011-09-10
```

stuart@stuart-A7N8X2-0:~$ sudo iwlist scan
[sudo] password for stuart: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down



```

---

### Post by wildmanne39 on 2011-09-10
Hi, I am going to have to do more research apparently you have a bug in that driver.
Thank you

---

### Post by stu_e_hughes on 2011-09-10
Thanks for your help. I'm looking forward to getting the wireless working so I can use this as a main computer. I suppose in the worst case scenario I can always buy a new wireless card which we know is supported. Would be great if you could get this one working though. I suppose if it's a bug in the driver it is probably in Ubuntu's best interest to get it fixed anyway though.

---

### Post by praseodym on 2011-09-10
Do you have a button/switch etc.? "Tx-Power=0 dBm" indicated that the card is just "off". Check your BIOS settings about wireless.

The driver can be updated using the backported modules:
```

sudo apt-get install --reinstall  linux-backports-modules-cw-2.6.39-natty-generic
```and reboot.

---

