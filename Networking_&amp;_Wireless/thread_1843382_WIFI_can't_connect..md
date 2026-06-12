---
title: "WIFI can't connect."
date: 2011-09-13
forum: Networking &amp; Wireless
---

### Post by Renosam on 2011-09-13
Hi. I just installed Ubuntu 11.04 I'm new to the Linux world.

Installed Ubuntu yesterday, and when i plugged my USB dongle in i was online right away. I unplugged it after some updates was still working, but i want to see if my built in wifi would work.

I couldn't get the WIFI to work. And i want to use N network so i used the USB dongle again but now i can't get online. I can see my network and i can use my WPA2 key, but i can't connect. Its just trying to connect over and over again.
i have been trying with networks with no security and it can't connect there aswell. Have reinstalled Ubuntu about 5 times, also installed Kubuntu but its the same story every time.


I have no option to get the laptop on the network as i only got WIFI in my house..
Is there a way to reset all network settings.

---

### Post by praseodym on 2011-09-13
Please show:

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
```

---

### Post by Renosam on 2011-09-13
> **praseodym said:**
> Please show:

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
```


lspci -nnk | grep -iA2 net
00:09.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet [10ec:8169] (rev 10)
	Subsystem: Fujitsu Technology Solutions Device [1734:1093]
	Kernel driver in use: r8169
--
00:0a.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
	Subsystem: Device [17f9:0006]
	Kernel driver in use: b43-pci-bridge


lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0461:4d16 Primax Electronics, Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0781:5567 SanDisk Corp. Cruszer Blade
Bus 001 Device 004: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub







lsmod
Module                  Size  Used by
ath9k_htc              55795  0 
ath9k_common           13611  1 ath9k_htc
ath9k_hw              300328  2 ath9k_htc,ath9k_common
ath                    19141  2 ath9k_htc,ath9k_hw
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_via82xx            24685  2 
gameport               15027  1 snd_via82xx
snd_ac97_codec        105614  1 snd_via82xx
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  2 snd_via82xx,snd_ac97_codec
snd_page_alloc         14073  2 snd_via82xx,snd_pcm
joydev                 17322  0 
snd_mpu401_uart        13865  1 snd_via82xx
snd_seq_midi           13132  0 
arc4                   12473  4 
snd_rawmidi            25269  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
b43                   296610  0 
radeon                896428  3 
mac80211              257001  2 ath9k_htc,b43
psmouse                73312  0 
ttm                    65184  1 radeon
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              156212  4 ath9k_htc,ath,b43,mac80211
shpchp                 32345  0 
serio_raw              12990  0 
drm_kms_helper         40745  1 radeon
video                  18951  0 
drm                   180037  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13184  1 radeon
i2c_viapro             12969  0 
snd                    55295  12 snd_via82xx,snd_ac97_codec,snd_pcm,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
k8temp                 12872  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
pata_via               13368  2 
r8169                  42534  0 
ssb                    45942  1 b43
crc_itu_t              12627  1 firewire_core
sata_via               13464  0 
reno@Amilo:~$

---

### Post by praseodym on 2011-09-13
For this device only the firmware has to be installed:

```
sudo apt-get install b43-fwcutter firmware-b43-installer
```

---

### Post by Renosam on 2011-09-13
> **praseodym said:**
> For this device only the firmware has to be installed:

```
sudo apt-get install b43-fwcutter firmware-b43-installer
```

Just to be sure.

I want to use the USB dongle TP-Link think its Atheros. will the command make it work or the build in wifi ?

---

### Post by Renosam on 2011-09-13
> **Renosam said:**
> Just to be sure.

I want to use the USB dongle TP-Link think its Atheros. will the command make it work or the build in wifi ?

This is what i got.


[sudo] password for reno: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package b43-fwcutter
E: Unable to locate package firmware-b43-installer

---

### Post by praseodym on 2011-09-13
The command will make the internal wifi work, but obviously you have no connection. I attached the firmware package, save it on the Desktop and install it via:

```
sudo tar xvf ~/Desktop/Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
The firmware package for the usb device is also attached. Unpack the file on your desktop and move the files:

```
sudo mv ~/Desktop/htc_7010.fw /lib/firmware
sudo mv ~/Desktop/htc_9271.fw /lib/firmware
sudo modprobe -rf ath9k_htc
sudo modprobe -v ath9k_htc
```
replug the stick. Check:

```
iwconfig
dmesg | egrep 'b43|ath'
sudo iwlist scan
rfkill list
```

---

### Post by Renosam on 2011-09-13
> **praseodym said:**
> The command will make the internal wifi work, but obviously you have no connection. I attached the firmware package, save it on the Desktop and install it via:

```
sudo tar xvf ~/Desktop/Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
The firmware package for the usb device is also attached. Unpack the file on your desktop and move the files:

```
sudo mv ~/Desktop/htc_7010.fw /lib/firmware
sudo mv ~/Desktop/htc_9271.fw /lib/firmware
sudo modprobe -rf ath9k_htc
sudo modprobe -v ath9k_htc
```
replug the stick. Check:

```
iwconfig
dmesg | egrep 'b43|ath'
sudo iwlist scan
rfkill list
```


Ok done it all. And now the builtin are able to see networks aswell. 
But i can't connect to any networks, on build in or with the dongle. its just trying to connect all the time. i never get any connection. checked with Secure network and with no security.

---

### Post by praseodym on 2011-09-13
Show the outputs of the "Check"-commands (after a reboot), copy them into a txt file and upload them

---

### Post by Renosam on 2011-09-13
could you tell me how to do the check commands :D I'm very new in linux.

---

### Post by praseodym on 2011-09-13
These (added some more):

```
iwconfig
cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
dmesg | egrep 'b43|ath'
sudo iwlist scan [COLOR="Red"]#which is your network here?[/COLOR]
iwlist chan
lsmod
rfkill list
```

---

### Post by Renosam on 2011-09-13
> **praseodym said:**
> These (added some more):

```
iwconfig
cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
dmesg | egrep 'b43|ath'
sudo iwlist scan [COLOR="Red"]#which is your network here?[/COLOR]
iwlist chan
lsmod
rfkill list
```

Ok done it.

---

### Post by praseodym on 2011-09-13
Maybe you try only one device at a time, if both try to connect there could be problems. Which country do you live? **wlan0** shows 14, **wlan1** 13 channels, respectively.

A little script, which unloads the Broadcom driver if the stick is plugged in:
```
gksu gedit /etc/udev/rules.d/10-wlan-stick.rules
```
Copy this into it:

```
# UDEV-rule for external WLAN-sticks
# unloads/loads driver for internal WLAN-card

ACTION=="add", GOTO="device_check"
ACTION=="remove", GOTO="onboard_load"

LABEL="device_check
### WLAN-stick plugged, Onboard-card deactivated
BUS=="usb", KERNEL=="wlan*" RUN+="/sbin/modprobe -rf b43"

GOTO="rules_end"

LABEL="onboard_load"
### WLAN-Stick removed, Onboard-Karte aktivated
BUS=="usb", KERNEL=="wlan*" RUN+="/sbin/modprobe b43"

LABEL="rules_end"
```
Save, exit, and
```
sudo service udev reload
```
Now try both devices separately.

---

### Post by Renosam on 2011-09-13
> **praseodym said:**
> Maybe you try only one device at a time, if both try to connect there could be problems. Which country do you live? **wlan0** shows 14, **wlan1** 13 channels, respectively.

A little script, which unloads the Broadcom driver if the stick is plugged in:
```
gksu gedit /etc/udev/rules.d/10-wlan-stick.rules
```
Copy this into it:

```
# UDEV-rule for external WLAN-sticks
# unloads/loads driver for internal WLAN-card

ACTION=="add", GOTO="device_check"
ACTION=="remove", GOTO="onboard_load"

LABEL="device_check
### WLAN-stick plugged, Onboard-card deactivated
BUS=="usb", KERNEL=="wlan*" RUN+="/sbin/modprobe -rf b43"

GOTO="rules_end"

LABEL="onboard_load"
### WLAN-Stick removed, Onboard-Karte aktivated
BUS=="usb", KERNEL=="wlan*" RUN+="/sbin/modprobe b43"

LABEL="rules_end"
```
Save, exit, and
```
sudo service udev reload
```
Now try both devices separately.

IT WORKS!!! Ty very very much, Im from Denmark.

Im very happy about the fast support on this forum and I'm very happy about your help. you really made my day :) hope you have a great day thx :D

---

### Post by praseodym on 2011-09-13
:popcorn:

You can install the package **iw** and set your country code for the possible channels:

```
sudo iw reg set DK
```

---

### Post by el_koraco on 2011-09-13
> **praseodym said:**
> :popcorn:

You can install the package **iw** and set your country code for the possible channels:

```
sudo iw reg set DK
```

Dude, you really aced this one. An udev rule! Thumbs up.

---

### Post by praseodym on 2011-09-13
It can be used for any PCI/USB device combination, just replace b43 from this example with the PCI-device module of your choice.

Taken from [here]("http://forum.ubuntuusers.de/topic/wlan-usb-8194/#post-3133322")

---

