---
title: "Compaq c60, can't enable wifi"
date: 2013-03-13
forum: Networking &amp; Wireless
---

### Post by dentedileone on 2013-03-13
i've got ubuntu 12.04 installed on a compaq c60. wireless connection doesn't work anymore, the wifi led is red which means that it is not enabled. i ve activated it in the bios setup. wireless connection is also disappeared in the network menu. I tried reading similar posts on this forum but apparently rfkill command doesn't work for me, it says nothing. I hope I can get some help, thank you very much and sorry for my bad english.nO

---

### Post by nd456 on 2013-03-13
You could try:

killall nm-applet; nm-applet

---

### Post by dentedileone on 2013-03-14
thanks for your answer. says  'applet now removed from the notifications area' but wireless connection still not appear and the wifi led is still red.

---

### Post by varunendra on 2013-03-14
> **dentedileone said:**
> i've got ubuntu 12.04 installed on a compaq c60. wireless connection doesn't work anymore, the wifi led is red which means that it is not enabled.

Welcome to the forums dentedileone :)

Please follow the 'Wireless Script' link in my signature and do as the linked post suggests to do. Post back the diagnostics report here.

---

### Post by dentedileone on 2013-03-14
thank you very much :)
here's the netinfo.txt file output.
```
   
*************** info trace ****************


**** uname -a ****

Linux pc-selene 3.2.0-38-generic-pae #61-Ubuntu SMP Tue Feb 19 12:39:51 UTC 2013 i686 athlon i386 GNU/Linux


**** lsb-release ****   
DISTRIB_ID=Ubuntu DISTRIB_RELEASE=12.04 DISTRIB_CODENAME=precise DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"


**** lspci ****   

00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP77 Ethernet [10de:0760] (rev a2)
 	Subsystem: Hewlett-Packard Company Device [103c:360a]
 	Kernel driver in use: forcedeth
 -- 
07:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
 	Subsystem: Hewlett-Packard Company Device [103c:137b]
 	Kernel modules: ath5k


**** lsusb ****   

 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
 Bus 002 Device 003: ID 04f2:b091 Chicony Electronics Co., Ltd Webcam
 Bus 004 Device 002: ID 04e8:685e Samsung Electronics Co., Ltd GT-I9100 Phone [Galaxy S II] (USB Debugging mode)


**** iwconfig ****


**** rfkill ****


**** lsmod ****

   Module                  Size  Used by
nls_iso8859_1          12617  2
nls_cp437              12751  2
vfat                   17308  2
fat                    55605  1 vfat
snd_hda_codec_hdmi     31775  1
snd_hda_codec_conexant    52554  1
joydev                 17393  0
snd_hda_intel          32765  3
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ath                    19387  0
mac80211              436493  0
nouveau               712674  3
snd_seq_midi           13132  0
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
psmouse                86520  0
ttm                    65344  1 nouveau
drm_kms_helper         45466  1 nouveau
drm                   197641  5 nouveau,ttm,drm_kms_helper
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13027  0
k10temp                12990  0
i2c_algo_bit           13199  1 nouveau
uvcvideo               67203  0
cfg80211              178877  2 ath,mac80211
cdc_acm                22277  0
mxm_wmi                12893  1 nouveau
snd                    62218  16 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               86588  1 uvcvideo
shpchp                 32325  0
rfcomm                 38139  0
bnep                   17830  2
parport_pc             32114  0
ppdev                  12849  0
bluetooth             158479  10 rfcomm,bnep
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
video                  19115  1 nouveau
wmi                    18744  1 mxm_wmi
mac_hid                13077  0
i2c_nforce2            12906  0
lp                     17455  0
parport                40930  3 parport_pc,ppdev,lp
pata_amd               13750  0
forcedeth              58096  0
ums_realtek            17920  0
usb_storage            39646  3 ums_realtek


**** nm-tool ****

    NetworkManager Tool

  State: disconnected
  - Device: eth0
 -----------------------------------------------------------------
   Type:              Wired
   Driver:            forcedeth
   State:             unavailable
   Default:           no
   HW Address:        <MAC address removed>
    Capabilities:     Carrier Detect:  yes
    Wired Properties     Carrier:         off 


**** NetworkManager.state **** 

   [main]
 NetworkingEnabled=true
 WirelessEnabled=true
 WWANEnabled=true
 WimaxEnabled=true


**** NetworkManager.conf ****
   [main]
 plugins=ifupdown,keyfile
 dns=dnsmasq
  [ifupdown]
 managed=false


**** NetworkManager.conf-10.04 **** 


**** interfaces **** 

  auto lo
 iface lo inet loopback


**** iwlist ****


**** resolv ****

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN


**** blacklist.conf **** 
# This file lists those modules which we don't want to be loaded by 
# alias expansion, usually so some other driver will be loaded for the 
# device instead.  
# evbug is a debug tool that should be loaded explicitly 
blacklist evbug  

# these drivers are very simple, the HID drivers are usually preferred 
blacklist usbmouse 
blacklist usbkbd  

# replaced by e100 
blacklist eepro100  

# replaced by tulip 
blacklist de4x5  

# causes no end of confusion by creating unexpected network interfaces 
blacklist eth1394  

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much 
# hardware on its own (Ubuntu bug #2011, #6810) 
blacklist snd_intel8x0m  

# Conflicts with dvb driver (which is better for handling this device) 
blacklist snd_aw2 

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306) 
blacklist i2c_i801  

# replaced by p54pci 
blacklist prism54  

# replaced by b43 and ssb. 
blacklist bcm43xx  

# most apps now use garmin usb driver directly (Ubuntu: #114565) 
blacklist garmin_gps  

# replaced by asus-laptop (Ubuntu: #184721) 
blacklist asus_acpi  

# low-quality, just noise when being used for sound playback, causes 
# hangs at desktop session start (Ubuntu: #246969) 
blacklist snd_pcsp  

# ugly and loud noise, getting on everyone's nerves; this should be done by a 
# nice pulseaudio bing (Ubuntu: #77010) 
blacklist pcspkr  

# EDAC driver for amd76x clashes with the agp driver preventing the aperture 
# from being initialised (Ubuntu: #297750). Blacklist so that the driver 
# continues to build and is installable for the few cases where its 
# really needed. 
blacklist amd76x_edac 
blacklist hp-wmi 


**** dmesg ****

[    0.000000] DMI: Hewlett-Packard Compaq Presario CQ60 Notebook PC/303C, BIOS F.54 08/18/2009 
[   13.846134] wmi: Mapper loaded 
[   14.933666] ath5k: Unknown parameter `rfkill'   

**************** done ********************  
```

---

### Post by varunendra on 2013-03-14
Looks like you have already tried a few things in a wrong way -
> **dentedileone said:**
> 
```

**** blacklist.conf **** 
....
....
blacklist amd76x_edac 
**[COLOR="#FF0000"]blacklist hp-wmi [/COLOR]**


**** dmesg ****

[   14.933666] **[COLOR="#FF0000"]ath5k: Unknown parameter `rfkill'[/COLOR] **  

```
I would really like to know all the changes you have made so far.

Meanwhile, please try -
```
sudo modprobe ath5k
```

Then post back results of -
```
rfkill list all
iwconfig
iwlist scan
dmesg | grep ath
```

---

### Post by dentedileone on 2013-03-14
sudo modprobe ath5k says:
```
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
FATAL: Error inserting ath5k (/lib/modules/3.2.0-38-generic-pae/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko): unknow symbol in module, or unknow parameter (see dmesg)

```

rfkill list
```
Usage: rfkill [options] command
Options: 
-- version show version (0.4-1ubuntu2 (Ubuntu) )
Commands: 
help
event
list [IDENTIFIER]
block IDENTIFIER
unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
<idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm
```

iwconfig
```
lo no wireless extensions.
eth0 no wireless extensions
```


iwlist scan
```
lo Interface doesn't support scanning.
eth0 interface doesn't support scanning
```

dmesg | grep ath
```
[ 15.771404] ath5k: unknown parameter `rfkill`
[ 75.768873] ath5k: unknown parameter `rfkill`
[ 184.042352] ath5k: unknown parameter `rfkill` 
```

I've been trying by using different solutions i've found on internet but i guess i did something wrong :(
i really can't remember how i'm here now.
thanks again for your help

---

### Post by varunendra on 2013-03-14
Please delete the file in /etc/modprobe.d directory where you added "rfkill" as parameter for ath5k.
```
sudo rm /etc/modprobe.d/<file name>
```
Then retry the modprobe command from my previous post.

If not sure, please post output of -
```
grep -iR rfkill /etc/modprobe.d/
```

---

### Post by dentedileone on 2013-03-14
If not sure, please post output of -
```
grep -iR rfkill /etc/modprobe.d/
```[/QUOTE]

```
/etc/modprobe.d/options:options ath5k rfkill=0
```


i'm not really sure, i'd prefer to avoid other mistakes :)
could you tell me which file should i delete please?
thank you

---

### Post by praseodym on 2013-03-14
Remove this file and create a new one:
```

sudo rm /etc/modprobe.d/options
echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```
This disables the hardware encryption of the driver.

---

### Post by varunendra on 2013-03-14
**EDIT:** [COLOR="#800000"]Missed praseodym's post (had the editor open for a while), disregard my post and do what he suggested.[/COLOR]

[s]Good idea. Please do-
```
cat /etc/modprobe.d/options
```
If it returns a single line as output ("options ath5k rfkill=0"), then do-
```
sudo rm /etc/modprobe.d/options
```
then try the modprobe command.

If however, it returns multiple lines of output (not likely), post back the output.[/s]

---

### Post by dentedileone on 2013-03-14
That's great, the led is blue and the wireless connections seems on now! :D
Well at the moment it says in the network manager wifi 's active, but i can't see any connectionavailable... what's the matter now?
Thanks you all for helping !

---

### Post by varunendra on 2013-03-14
> **dentedileone said:**
> Well at the moment it says in the network manager wifi 's active, but i can't see any connectionavailable...

Please post outputs of -
```
nm-tool
iwconfig
iwlist scan
dmesg | grep -ie ath -e net
```

---

### Post by dentedileone on 2013-03-19
nm-tool
```
NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        00:24:2B:B1:CA:D4

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Connessione via cavo 1] ---------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             connected
  Default:           yes
  HW Address:        00:1F:16:71:C3:E2

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.4
    Prefix:          25 (255.255.255.128)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


```

iwconfig
```
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
eth0      no wireless extensions.


```

iwlist scan
```
lo        Interface doesn't support scanning.

wlan0     No scan results

eth0      Interface doesn't support scanning.


```


dmesg | grep -ie ath -e net
```
[    0.000000]   Transmeta GenuineTMx86
[    0.072003] NET: Registered protocol family 16
[    0.126696] NetLabel: Initializing
[    0.126699] NetLabel:  domain hash size = 128
[    0.126700] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.126713] NetLabel:  unlabeled traffic allowed by default
[    0.181162] NET: Registered protocol family 2
[    0.182594] NET: Registered protocol family 1
[    0.293345] audit: initializing netlink socket (disabled)
[    0.848519] NET: Registered protocol family 10
[    0.849038] NET: Registered protocol family 17
[    1.586833] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[   17.180524] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.012713] type=1400 audit(1363704204.399:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=594 comm="apparmor_parser"
[   18.178907] NET: Registered protocol family 31
[   18.216101] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.357511] ath5k 0000:07:00.0: PCI INT A -> Link[Z012] -> GSI 23 (level, low) -> IRQ 23
[   18.357526] ath5k 0000:07:00.0: setting latency timer to 64
[   18.357587] ath5k 0000:07:00.0: registered as 'phy0'
[   19.004685] ath: EEPROM regdomain: 0x67
[   19.004689] ath: EEPROM indicates we should expect a direct regpair map
[   19.004694] ath: Country alpha2 being used: 00
[   19.004696] ath: Regpair used: 0x67
[   19.053529] Registered led device: ath5k-phy0::rx
[   19.053612] Registered led device: ath5k-phy0::tx
[   19.053628] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   20.162501] type=1400 audit(1363704206.547:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=862 comm="apparmor_parser"
[   21.315059] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.316335] ADDRCONF(NETDEV_UP): wlan0: link is not ready


```

---

### Post by varunendra on 2013-03-19
Can you please also post the same results while the cable is unplugged and the wireless shows as 'On' ?

Or even better, just run the wireless script again (after deleting the old "netinfo.txt" file) while the wireless shows as 'On' and cable is disconnected, and post back the new file's contents.

Thanks!

---

### Post by dentedileone on 2013-03-19
is this ok?
```

*************** info trace ****************



**** uname -a ****


Linux pc-selene 3.2.0-38-generic-pae #61-Ubuntu SMP Tue Feb 19 12:39:51 UTC 2013 i686 athlon i386 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"


**** lspci ****


00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP77 Ethernet [10de:0760] (rev a2)
    Subsystem: Hewlett-Packard Company Device [103c:360a]
    Kernel driver in use: forcedeth
--
07:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:137b]
    Kernel driver in use: ath5k


**** lsusb ****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 002 Device 002: ID 04f2:b091 Chicony Electronics Co., Ltd Webcam


**** iwconfig ****


wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


**** rfkill ****


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


**** lsmod ****


Module                  Size  Used by
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_conexant    52554  1 
joydev                 17393  0 
snd_hda_intel          32765  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
nouveau               712674  3 
arc4                   12473  2 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ttm                    65344  1 nouveau
drm_kms_helper         45466  1 nouveau
ath5k                 145127  0 
ath                    19387  1 ath5k
drm                   197641  5 nouveau,ttm,drm_kms_helper
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
mac80211              436493  1 ath5k
bnep                   17830  2 
parport_pc             32114  0 
bluetooth             158479  7 bnep
ppdev                  12849  0 
i2c_algo_bit           13199  1 nouveau
snd_timer              28931  2 snd_pcm,snd_seq
psmouse                86520  0 
cfg80211              178877  3 ath5k,ath,mac80211
mxm_wmi                12893  1 nouveau
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               67203  0 
k10temp                12990  0 
serio_raw              13027  0 
snd                    62218  16 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 32325  0 
videodev               86588  1 uvcvideo
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
video                  19115  1 nouveau
wmi                    18744  1 mxm_wmi
mac_hid                13077  0 
i2c_nforce2            12906  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
forcedeth              58096  0 
pata_amd               13750  0 
ums_realtek            17920  0 
usb_storage            39646  1 ums_realtek


**** nm-tool ****



NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off




**** NetworkManager.state ****



[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


**** NetworkManager.conf ****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false


**** NetworkManager.conf-10.04 ****




**** interfaces ****


auto lo
iface lo inet loopback



**** iwlist ****


wlan0     No scan results



**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1


**** blacklist.conf ****


# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist hp-wmi


**** dmesg ****


[    0.000000] DMI: Hewlett-Packard Compaq Presario CQ60 Notebook PC/303C, BIOS F.54 08/18/2009
[   17.603129] wmi: Mapper loaded
[   18.357511] ath5k 0000:07:00.0: PCI INT A -> Link[Z012] -> GSI 23 (level, low) -> IRQ 23
[   18.357526] ath5k 0000:07:00.0: setting latency timer to 64
[   18.357587] ath5k 0000:07:00.0: registered as 'phy0'
[   19.004685] ath: EEPROM regdomain: 0x67
[   19.004689] ath: EEPROM indicates we should expect a direct regpair map
[   19.004694] ath: Country alpha2 being used: 00
[   19.004696] ath: Regpair used: 0x67
[   19.053529] Registered led device: ath5k-phy0::rx
[   19.053612] Registered led device: ath5k-phy0::tx
[   19.053628] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   21.315059] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.316335] ADDRCONF(NETDEV_UP): wlan0: link is not ready


**************** done ********************


```

---

### Post by varunendra on 2013-03-19
Sorry for a late response, I was trying hard to get a clue from the outputs, but couldn't. Frankly, I'm out of ideas, maybe praseodym could recognize why you are disconnected.

Meanwhile, please try -
```
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k nohwcrypt=Y all_channels=Y
```

Then do -
```
iwlist scan
```
Does it see any networks ?

---

### Post by dentedileone on 2013-03-19
here's what it says

```
lo        Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

eth0      Interface doesn't support scanning.


```

It says "wireless connection disabled by switch hardware"
when I open the network manager i can see airplane mode is on and wifi is disabled. I tried to set airplane mode off but doesn't work, and i also cannot set wifi on.
thanks a lot anyway for your time :)

---

### Post by praseodym on 2013-03-19
Any "real" button/switch? Checked the BIOS settings?

---

### Post by dentedileone on 2013-03-19
> **praseodym said:**
> Any "real" button/switch? Checked the BIOS settings?

there is a real button and it's on. wireless connection is active in the  bios settings.
:(

---

### Post by varunendra on 2013-03-19
There is only one more thing that seems obviously abnormal (although recommended *sometimes* in some specific situations). That is blacklisting of 'hp-wmi'.

Please un-blacklist it for a test -
```
sudo sed -i 's:blacklist hp-wmi:# &:' etc/modprobe.d/blacklist.conf
sudo modprobe -v hp-wmi
```

Then retry the physical switch or the Fn key combination whatever you have to enable wireless.

Also, are you dual booting with Windows or is it Ubuntu-only from the beginning. If dual booting, does it work in windows?

---

### Post by praseodym on 2013-03-20
Is it an (U)EFI secure boot? If not, reset the BIOS to default settings.

---

### Post by michael22 on 2013-08-18
ok_so_talk_bout_an_easy_fix._all_i_had_to_do_was_to_add_this_blacklist_asus_command_to_the_blacklist.conf_file_and_walloa_my_wifi_is_back_in_action.
it_wasnt_actuly_in_the_file_so_i_had_to_type_it_in_at_the_bottom._im_not_to_sure_if_its_the_right_command_(blacklist)_but_within_this_post_is_were_
i_got_the_info_so_just_keep_looking_n_u_will_find_it.thankls_so_much_ubuntu_13.04._i_gave_up_on_windows_vista_as_it_was_eating_all_my_mem_and_cpu_
so_i_jump_to_this_and_wow_talk_bout_speed._now_on_to_the_next_propblem_trying_to_remap_the_right_alt_key_(orany_other_key)to_be_used_as_the_space_bar.
mines_broken_due_to_hardwere._should_be_an_easy_fix.

thanks_again_guys_thanks_so_much
blacklist asus

---

### Post by wildmanne39 on 2013-08-18
Hi michael22, is there something wrong when you type text? if not please fix the text you typed so it will be normal.
Thanks

---

