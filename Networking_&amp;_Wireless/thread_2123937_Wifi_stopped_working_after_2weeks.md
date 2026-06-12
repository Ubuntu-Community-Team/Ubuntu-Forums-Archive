---
title: "Wifi stopped working after 2weeks"
date: 2013-03-09
forum: Networking &amp; Wireless
---

### Post by miekku on 2013-03-09
Hello
I'm kind of new ubuntu user, when I installed ubuntu(not by wubi) everything worked fine, later it stopped working, I dont know if the ubuntu were updated beacuse I'm not the only 1 whose use this PC. When I scan, no single result is given(but on other pc's its find a lot of them). 
wifi device - atheros ar9485
driver - ath9k
Ethernet imo is fine, it's connected to my xbox, to share videos/music with it(via uShare)
Any solution to make my wifi work again?

---

### Post by varunendra on 2013-03-09
For a quick shot try-
```
sudo rfkill unblock all
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k nohwcrypt=1 btcoex_enable=0
```

If it doesn't help, follow the 'Wireless Script' link in my signature, and do what it asks to do.

Thanks.

---

### Post by miekku on 2013-03-09
This didnt help, log in attachment.

---

### Post by varunendra on 2013-03-09
> **miekku said:**
> This didnt help, log in attachment.
Copy-pasting contents for easy follow-up :
```

*************** info trace ****************



**** uname -a ****


Linux ewa-pc 3.5.0-23-generic #35-Ubuntu SMP Thu Jan 24 13:15:40 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"


**** lspci ****


02:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)
	Subsystem: Atheros Communications Inc. Device [168c:3118]
	Kernel driver in use: ath9k
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Giga-byte Technology GA-EP45-DS5/GA-EG45M-DS2H Motherboard [1458:e000]
	Kernel driver in use: r8169


**** lsusb ****


Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 004: ID 1058:1021 Western Digital Technologies, Inc. Elements 2TB
Bus 002 Device 004: ID 1058:1021 Western Digital Technologies, Inc. Elements 2TB
Bus 002 Device 005: ID 0951:1653 Kingston Technology Data Traveler 100 G2 8 GiB
Bus 002 Device 003: ID 0a81:0203 Chesen Electronics Corp. Mouse


**** iwconfig ****


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


**** rfkill ****


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


**** lsmod ****


Module                  Size  Used by
rfcomm                 46620  0 
parport_pc             32689  0 
bnep                   18141  2 
bluetooth             209249  10 rfcomm,bnep
ppdev                  17074  0 
nls_iso8859_1          12714  2 
coretemp               13401  0 
kvm                   414071  0 
ghash_clmulni_intel    13221  0 
cryptd                 20404  1 ghash_clmulni_intel
snd_hda_codec_realtek    78048  1 
arc4                   12530  2 
microcode              22804  0 
joydev                 17458  0 
snd_hda_intel          33492  3 
snd_hda_codec         134213  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17699  1 snd_hda_codec
snd_pcm                96668  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0 
ath9k                 131355  0 
snd_rawmidi            30513  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
mac80211              539958  1 ath9k
psmouse                95595  0 
ath9k_common           14056  1 ath9k
ath9k_hw              395264  2 ath9k,ath9k_common
serio_raw              13216  0 
snd_timer              29426  2 snd_pcm,snd_seq
ath                    23828  3 ath9k,ath9k_common,ath9k_hw
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              206797  3 ath9k,mac80211,ath
mac_hid                13206  0 
snd                    78921  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lpc_ich                17062  0 
i915                  520621  3 
drm_kms_helper         49113  1 i915
drm                   288721  4 i915,drm_kms_helper
i2c_algo_bit           13414  1 i915
soundcore              15048  1 snd
video                  19336  1 i915
mei                    40691  0 
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
lp                     17760  0 
parport                46346  3 parport_pc,ppdev,lp
hid_logitech_dj        18605  0 
hid_generic            12541  0 
usbhid                 46987  1 hid_logitech_dj
hid                   100411  3 hid_logitech_dj,hid_generic,usbhid
r8169                  61651  0 
usb_storage            48839  3 


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: eth0  [Po&#322;&#261;czenie przewodowe 1] ------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.1
    Prefix:          24 (255.255.255.0)
    Gateway:         0.0.0.0



- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 




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

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false


**** NetworkManager.conf-10.04 ****




**** interfaces ****


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


**** iwlist ****


wlan0     No scan results



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
blacklist acer-wmi


**** dmesg ****


[    3.157736] ath9k 0000:02:00.0: enabling device (0000 -> 0002)
[    3.179462] ath: EEPROM regdomain: 0x21
[    3.179520] ath: EEPROM indicates we should expect a direct regpair map
[    3.179522] ath: Country alpha2 being used: AU
[    3.179523] ath: Regpair used: 0x21
[    3.215644] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[    3.216203] Registered led device: ath9k-phy0
[    4.624951] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    4.627978] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready


**************** done ********************


```
Everything seems normal to me in the first glance.

Please note that most laptops have BIOS settings to prefer faster connection. Means it won't connect via wireless (slower) if the Ethernet (usually faster) cable is plugged in.

So in order to try the wireless, please detach the cable first.

---

### Post by miekku on 2013-03-09
1st of all this is normal pc not laptop ;), next time I will copy-paste, sorry for problem.

---

### Post by varunendra on 2013-03-09
lspci "April Fooled" me in March?

Anyway, the preference logic may still apply. So please try with cable disconnected.

---

### Post by miekku on 2013-03-10
I plugged off the cable, still i got no connection with wifi, also when I tried to "connect with hidden wireless network", it doesnt establish connection beacuse system "suggest" that I typed wrong password(Router got  netw. auth - WPA-PSK, encypt TKIP, and i type my pass without any typo). I didn't change configuration of router so its 99% fault of software in this pc

edit - i tried run ubuntu 12.10 on live-usb, it dont see network, when I try to use hidden wireless network - still same issue about wrong pass

---

### Post by varunendra on 2013-03-10
If it is your own router, can you disable the security just for a test ? So we can make sure whether it is authentication related or something else.

If it connects, run **iwconfig** > check signal strength, enable the security again, make sure **NOT** to use WPA/WPA2 mixed mode. Preferably, keep it WPA2 only. Then retry to connect. If it fails again, try just one parameter this time -
```
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k nohwcrypt=1
```

Post back the results.

Thanks.

---

### Post by miekku on 2013-03-10
I disabled the security, still nothing happens, when i try to "connect to hidden wireless network" after some time I get notification: "Wireless connection - disconnected"
btw. iwlist scan should give some results but it doesnt - on laptop with win7 or kubuntu it finds about 7 results
edit. before u ask: router doesnt have any mac filter enabled

---

### Post by varunendra on 2013-03-10
> **miekku said:**
> edit. before u ask: router doesnt have any mac filter enabled
No, I didn't think of that yet, but you just gave me an idea ;)

Do you by any chance happen to have played with ubuntu firewall ? What says -
```
sudo ufw status
```


**PS:**
It seems we are suddenly having an abnormal number of complains with ath9k.
Wondering if some bug is causing that.

Maybe I'll need to do some research before posting again. I suggest you do the same and post back if something significant is found.

---

### Post by miekku on 2013-03-10
sudo ufw status - Status: inactive,
btw. I already tried some things about blacklisting some devices, i tried also connect to other wireless networks, and some other solutions like put out wireless card([http://www.amazon.com/TP-Link-TL-WN781ND-150Mbps-Wireless-Express/dp/B0036AFAEW](http://www.amazon.com/TP-Link-TL-WN781ND-150Mbps-Wireless-Express/dp/B0036AFAEW)) and put into other pci-e x1 slot but nothing happened.
I didnt tried reinstall drivers yet.

---

### Post by Jbouska on 2013-03-10
Hi everyone,

I'm experiencing the same problem over here.  My laptop says I have a full connection to my network, but Firefox keeps giving me the "can't find server" run-around.  Everything was fine yesterday morning, I shut my laptop down, then rebooted it a few hours later to return to this problem.  Any ideas on why this happened and how I get started on fixing it?

---

### Post by miekku on 2013-04-01
when i type 
"sudo iw wlan0 link", terminal said "Not connected" it is ok?
iwconfig detect wlan0, ifconfig too, I've got connected card thru PCI, and I already tried another PCI(on this motherboard) it detects this wifi card in same way.

---

