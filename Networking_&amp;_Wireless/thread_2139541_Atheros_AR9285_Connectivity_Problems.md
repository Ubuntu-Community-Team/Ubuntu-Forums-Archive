---
title: "Atheros AR9285 Connectivity Problems"
date: 2013-04-27
forum: Networking &amp; Wireless
---

### Post by henriquev16 on 2013-04-27
Hi guys, I'm new in Linux world, I started to use Ubuntu in the university where I study and I like It! But I'm sad because it's the second time I try to install and I'm having problems with my Wireless Card! :( It's an Atheros AR9285 (in my laptop Acer Aspire 5300) and the problem is: when I use Windows my card works correctly no matter how much away I am from my Wireless Router.. but with Ubuntu 13.04 If I go to my room as I did before with Windows (about 5 meters)  I lose connectivity! Someone with the same problem? I want to use Ubuntu !   Today I will not be at but I will come see your answers and reply the fastest I can! Thank you.

---

### Post by henriquev16 on 2013-04-27
No one?

---

### Post by Elfy on 2013-04-27
*Thread moved to **Networking & Wireless**.*

Hopefully you'll get some help in this section, you'd posted in the development sub-forum.

---

### Post by henriquev16 on 2013-04-27
Ok thanks and sorry for the mistake. Can anyone help me?  I need wifi working for monday because of my work in school.. Right now I'm posting with my smartphone in my room where laptop wireless should work but not...  Please help.

---

### Post by wildmanne39 on 2013-04-27
Hi, please try:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
This may help but you are probably not going to get as good as signal sgtrength with ubuntu as you do with windows because the driver needs a little work but  I use this same driver with a few other tweaks as well and it works pretty good.
Thanks

---

### Post by henriquev16 on 2013-04-28
Hi, thanks for your answer but when I insert the first command in terminal I recieve a message : " su: must be run from a terminal "
What am I doing wrong?

---

### Post by wildmanne39 on 2013-04-28
Hi, where did you insert the command?

You just need to copy and paste them one line at a time for accuracy into the terminal, you can open it with CTRL+ALT+T.
Thanks

---

### Post by henriquev16 on 2013-04-28
Modified: Sorry, I was doing wrong ... I have done that but the same thing.. I can connect close to the router but If I go to my room I lose conectivity.. In school where the AP is distante I will not have conection ...

---

### Post by ronnyroll on 2013-04-28
i faced similar problem within 5 meters

---

### Post by henriquev16 on 2013-04-28
Have you solved this issue? That's it! Only a few meters!

---

### Post by wildmanne39 on 2013-04-28
Hi, you can try:
```
sudo iwconfig wlan0 txpower 20
```
see if it will take that setting and if it helps.
Thanks

---

### Post by wildmanne39 on 2013-04-28
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by henriquev16 on 2013-04-29
Hi Wild Man, I need to run that script using Wifi or I can do it with cable? .. I had to install windows again because I need internet access to work ...

Today, later, I will reinstall ubuntu and do that.. .

Thanks for your time. 

At worst, if I have to change my wireless card I change...

---

### Post by varunendra on 2013-04-29
> **henriquev16 said:**
> Hi Wild Man, I need to run that script using Wifi or I can do it with cable?

You can run it while being connected via cable. You can also just download it on another computer > copy it to the Ubuntu computer > run it while trying to connect via wireless. For details on second method, follow the "Wireless Script" link in my signature.

---

### Post by henriquev16 on 2013-04-29
Thanks ! I hope this can help you solving my problem, I will do that the fastest I can ...

---

### Post by wildmanne39 on 2013-04-29
You might also consider installing dual boot so you will have the option to boot windows or  ubuntu.
Thanks

---

### Post by henriquev16 on 2013-04-29
That's what I just did! While I do not have Ubuntu running perfectly I'll keep the Dual Boot...

And now I'll do what you mention !

--
EDITED
--

I have no network access in the ubuntu so I have done this with the step 2 ...

Here is the file:

```
*************** info trace ****************






**** uname -a ****




Linux henriquebuntu 3.8.0-19-generic #29-Ubuntu SMP Wed Apr 17 18:16:28 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux




**** lsb-release ****




DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu 13.04"




**** lspci ****




01:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
    Subsystem: Acer Incorporated [ALI] Device [1025:0601]
    Kernel driver in use: tg3
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:6631]
    Kernel driver in use: ath9k




**** lsusb ****




Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0402:7675 ALi Corp. 
Bus 002 Device 004: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 002 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth




**** iwconfig ****




wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          




**** rfkill ****




0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no




**** lsmod ****




Module                  Size  Used by
usb_storage            57204  1 
snd_hda_codec_realtek    78399  1 
coretemp               13355  0 
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
arc4                   12615  2 
snd_hda_intel          39619  3 
snd_hda_codec         136453  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
ath9k                 149924  0 
ath9k_common           14055  1 ath9k
snd_pcm                97451  2 snd_hda_codec,snd_hda_intel
ath9k_hw              413680  2 ath9k_common,ath9k
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
uvcvideo               80847  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
snd_timer              29425  2 snd_pcm,snd_seq
videodev              129260  2 uvcvideo,videobuf2_core
mac80211              606457  1 ath9k
snd                    68876  15 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
i915                  600351  3 
microcode              22881  0 
drm_kms_helper         49394  1 i915
psmouse                95870  0 
serio_raw              13215  0 
drm                   286313  4 i915,drm_kms_helper
cfg80211              510937  3 ath,ath9k,mac80211
i2c_algo_bit           13413  1 i915
soundcore              12680  1 snd
intel_ips              17978  0 
lpc_ich                17061  0 
mei                    41158  0 
bnep                   18036  2 
parport_pc             28152  0 
rfcomm                 42641  0 
ppdev                  17073  0 
bluetooth             228619  10 bnep,rfcomm
joydev                 17377  0 
acer_wmi               32467  0 
sparse_keymap          13890  1 acer_wmi
mxm_wmi                13021  0 
video                  19390  2 i915,acer_wmi
wmi                    19070  2 acer_wmi,mxm_wmi
mac_hid                13205  0 
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
hid_generic            12540  0 
usbhid                 47074  0 
hid                   101002  2 hid_generic,usbhid
ahci                   25731  1 
libahci                31364  1 ahci
tg3                   153796  0 
ptp                    18621  1 tg3
pps_core               14080  1 ptp




**** nm-tool ****






NetworkManager Tool


State: disconnected


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
    SAPO-ZL51275:    Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA
    acaciobar:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA2




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


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




# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback




**** iwlist ****




wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"acaciobar"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000f9873e46d8
                    Extra: Last beacon: 76ms ago
                    IE: Unknown: 000961636163696F626172
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700E04C01020100






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




**** dmesg ****




[    0.830990] pci 0000:00:1c.1: [8086:3b44] type 01 class 0x060400
[    4.416146] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: d490763cc418e29de79f40a5aa7d97747ec8882c'
[    6.095050] tg3.c:v3.128 (December 03, 2012)
[    6.110962] libphy: tg3 mdio bus: probed
[    6.118993] tg3 0000:01:00.0 eth0: Tigon3 [partno(BCM57780) rev 57780001] (PCI Express) MAC address <MAC address removed>
[    6.118999] tg3 0000:01:00.0 eth0: attached PHY driver [Broadcom BCM57780] (mii_bus:phy_addr=100:01)
[    6.119001] tg3 0000:01:00.0 eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    6.119004] tg3 0000:01:00.0 eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   16.118902] wmi: Mapper loaded
[   16.179893] acer_wmi: Acer Laptop ACPI-WMI Extras
[   16.179914] acer_wmi: Function bitmap for Communication Button: 0x1
[   16.180053] acer_wmi: Brightness must be controlled by acpi video driver
[   17.742513] ath: phy0: ASPM enabled: 0x43
[   17.742516] ath: EEPROM regdomain: 0x65
[   17.742517] ath: EEPROM indicates we should expect a direct regpair map
[   17.742519] ath: Country alpha2 being used: 00
[   17.742520] ath: Regpair used: 0x65
[   17.783378] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   20.061556] tg3 0000:01:00.0: irq 44 for MSI/MSI-X
[   20.089882] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.090269] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.108176] tg3 0000:01:00.0 eth0: Link is down




**************** done ********************
```

Hope you have all the needed. Thanks

---

### Post by henriquev16 on 2013-04-30
Up! (Remove this later, please)

---

### Post by varunendra on 2013-04-30
> **henriquev16 said:**
> Up! (Remove this later, please)

Bumping in less than 24 hours may be frowned upon here, so avoid doing that.

Did you try what Wild Man suggested about tx power? Your output still shows it to be 14 dBm.

Assuming you tried that (but it didn't accept) and have also set the nohwcrypt=1 parameter permanently as suggested in post #5, there isn't much left to try, unfortunately. But I'd wait for Wild Man to confirm as he knows much more things that I may not have even the slightest idea of..

Meanwhile, let's confirm that you have applied the nohwcrypt parameter correctly (not that I'm very hopeful with it..) :
```
cat /sys/module/ath9k/parameters/nohwcrypt
```
It should return "1" as output.

Also, if you haven't tried yet, try the tx power trick as well, and post back the results.

---

### Post by henriquev16 on 2013-04-30
Ok I'm sorry.

I will do all you have mention and post here. Thanks

--EDIT--

Ok, now with all the configuration that Wild Man mentioned... I'm in school, Dual Boot, 2 meters away from an access point, high signal in windows and ubuntu but I can't connect anyway... the network is in WPA2 Enterprise.. I'm in the communications Lab and the network administrator tells me that the configs are correctly... 

```



*************** info trace ****************






**** uname -a ****




Linux henriquebuntu 3.8.0-19-generic #29-Ubuntu SMP Wed Apr 17 18:16:28 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux




**** lsb-release ****




DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu 13.04"




**** lspci ****




01:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
	Subsystem: Acer Incorporated [ALI] Device [1025:0601]
	Kernel driver in use: tg3
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: Lite-On Communications Inc Device [11ad:6631]
	Kernel driver in use: ath9k




**** lsusb ****




Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0402:7675 ALi Corp. 
Bus 002 Device 003: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 002 Device 004: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth




**** iwconfig ****




wlan0     IEEE 802.11bgn  ESSID:"eduroam"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=36 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:287   Missed beacon:0






**** rfkill ****




0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no




**** lsmod ****




Module                  Size  Used by
snd_hda_codec_realtek    78399  1 
coretemp               13355  0 
kvm_intel             132891  0 
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
kvm                   443165  1 kvm_intel
arc4                   12615  2 
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
ath9k                 149924  0 
videodev              129260  2 uvcvideo,videobuf2_core
ath9k_common           14055  1 ath9k
ath9k_hw              413680  2 ath9k_common,ath9k
snd_hda_intel          39619  3 
snd_hda_codec         136453  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
snd_pcm                97451  2 snd_hda_codec,snd_hda_intel
mac80211              606457  1 ath9k
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
cfg80211              510937  3 ath,ath9k,mac80211
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
microcode              22881  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
intel_ips              17978  0 
psmouse                95870  0 
serio_raw              13215  0 
lpc_ich                17061  0 
snd                    68876  15 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              12680  1 snd
i915                  600351  3 
mei                    41158  0 
drm_kms_helper         49394  1 i915
drm                   286313  4 i915,drm_kms_helper
i2c_algo_bit           13413  1 i915
bnep                   18036  2 
parport_pc             28152  0 
rfcomm                 42641  0 
ppdev                  17073  0 
bluetooth             228619  10 bnep,rfcomm
joydev                 17377  0 
acer_wmi               32467  0 
sparse_keymap          13890  1 acer_wmi
mxm_wmi                13021  0 
video                  19390  2 i915,acer_wmi
wmi                    19070  2 acer_wmi,mxm_wmi
mac_hid                13205  0 
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
hid_generic            12540  0 
usbhid                 47074  0 
hid                   101002  2 hid_generic,usbhid
usb_storage            57204  1 
ahci                   25731  1 
libahci                31364  1 ahci
tg3                   153796  0 
ptp                    18621  1 tg3
pps_core               14080  1 ptp




**** nm-tool ****






NetworkManager Tool


State: connecting


- Device: wlan0  [eduroam] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connecting (configuring)
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    eduroam:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 85 WPA2 Enterprise




- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connecting (getting IP configuration)
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on








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




# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback




**** iwlist ****




wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001ba8fad44c2
                    Extra: Last beacon: 44ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 01079618243048606C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 851E000081000F00FF0359006170313632000000000000000000000004000025
                    IE: Unknown: 9606004096000D00
                    IE: Unknown: DD06004096010100
                    IE: Unknown: DD050040960304
                    IE: Unknown: DD050040960B01
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00






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




**** dmesg ****




[    0.833568] pci 0000:00:1c.1: [8086:3b44] type 01 class 0x060400
[    4.427763] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: d490763cc418e29de79f40a5aa7d97747ec8882c'
[    6.118276] tg3.c:v3.128 (December 03, 2012)
[    6.130561] libphy: tg3 mdio bus: probed
[    6.141246] tg3 0000:01:00.0 eth0: Tigon3 [partno(BCM57780) rev 57780001] (PCI Express) MAC address <MAC address removed>
[    6.141252] tg3 0000:01:00.0 eth0: attached PHY driver [Broadcom BCM57780] (mii_bus:phy_addr=100:01)
[    6.141255] tg3 0000:01:00.0 eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    6.141257] tg3 0000:01:00.0 eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   16.218798] wmi: Mapper loaded
[   16.275315] acer_wmi: Acer Laptop ACPI-WMI Extras
[   16.275337] acer_wmi: Function bitmap for Communication Button: 0x1
[   16.275478] acer_wmi: Brightness must be controlled by acpi video driver
[   17.735877] ath: phy0: ASPM enabled: 0x43
[   17.735880] ath: EEPROM regdomain: 0x65
[   17.735881] ath: EEPROM indicates we should expect a direct regpair map
[   17.735883] ath: Country alpha2 being used: 00
[   17.735883] ath: Regpair used: 0x65
[   17.772566] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   19.363456] tg3 0000:01:00.0: irq 44 for MSI/MSI-X
[   19.391655] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.392033] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.130765] tg3 0000:01:00.0 eth0: Link is down
[   21.130170] tg3 0000:01:00.0 eth0: Link is up at 100 Mbps, full duplex
[   21.130174] tg3 0000:01:00.0 eth0: Flow control is off for TX and off for RX
[  121.978625] wlan0: authenticate with <MAC address removed>
[  121.984677] wlan0: send auth to <MAC address removed> (try 1/3)
[  121.986450] wlan0: authenticated
[  121.989822] wlan0: associate with <MAC address removed> (try 1/3)
[  121.992498] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=19)
[  121.992558] wlan0: associated
[  121.992887] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  123.032417] wlan0: deauthenticated from <MAC address removed> (Reason: 23)
[  124.017094] wlan0: authenticate with <MAC address removed>
[  124.023385] wlan0: send auth to <MAC address removed> (try 1/3)
[  124.025173] wlan0: authenticated
[  124.028601] wlan0: associate with <MAC address removed> (try 1/3)
[  124.031076] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=20)
[  124.031145] wlan0: associated
[  125.074996] wlan0: deauthenticated from <MAC address removed> (Reason: 23)
[  126.060181] wlan0: authenticate with <MAC address removed>
[  126.066379] wlan0: send auth to <MAC address removed> (try 1/3)
[  126.068168] wlan0: authenticated
[  126.071507] wlan0: associate with <MAC address removed> (try 1/3)
[  126.074041] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=21)
[  126.074117] wlan0: associated
[  127.112441] wlan0: deauthenticated from <MAC address removed> (Reason: 23)
[  128.099064] wlan0: authenticate with <MAC address removed>
[  128.105249] wlan0: send auth to <MAC address removed> (try 1/3)
[  128.107073] wlan0: authenticated
[  128.110331] wlan0: associate with <MAC address removed> (try 1/3)
[  128.112872] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=22)
[  128.112941] wlan0: associated
[  129.151428] wlan0: deauthenticated from <MAC address removed> (Reason: 23)
[  130.139822] wlan0: authenticate with <MAC address removed>
[  130.144166] wlan0: send auth to <MAC address removed> (try 1/3)
[  130.145929] wlan0: authenticated
[  130.149232] wlan0: associate with <MAC address removed> (try 1/3)
[  130.153486] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=23)
[  130.153553] wlan0: associated
[  146.197075] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)




**************** done ********************





```

---

### Post by wildmanne39 on 2013-04-30
Please post the results of:
```
cat /sys/module/ath9k/parameters/nohwcrypt
```
as varunendra asked for.
Thanks

---

### Post by henriquev16 on 2013-04-30
> **Wild Man said:**
> Please post the results of:
```
cat /sys/module/ath9k/parameters/nohwcrypt
```
as varunendra asked for.
Thanks

Sorry I forgot, the output was: 1

---

### Post by wildmanne39 on 2013-04-30
Please set your wireless settings in network manager to match the screenshots.

---

### Post by wildmanne39 on 2013-04-30
If that does not help please try:
```
gksudo gedit /etc/modprobe.d/ath9k.conf
```
Remove the line that is in the file then and ```
options ath9k nohwcrypt=1 blink=1 btcoex_enable=1 enable_diversity=1
```
save and close gedit then reboot.
Thanks

---

### Post by henriquev16 on 2013-04-30
I have done that but I still can't connect to the network! :S Always pumping to insert password for network but nothing else...

---

### Post by wildmanne39 on 2013-04-30
I would install 12.04.2, I use it with ```
options ath9k nohwcrypt=1
```
and my wireless settings match the screenshots I posted and it works great.
Thanks

---

### Post by henriquev16 on 2013-04-30
I wanted Ubuntu 13.04 but If there's no other option I will install 12.04 and try to see if this works...

Thanks.

---

### Post by wildmanne39 on 2013-04-30
There is no guarantee eirther way.

It is easier for linux drivers to connect to wpa2 networks but since yours is at a college you have no say in the way there settings are set so we can only change the things that are within your control.

13.04 has just come out and I know that the ath9k driver has had some issues with some devices.

---

### Post by varunendra on 2013-04-30
> **henriquev16 said:**
> I wanted Ubuntu 13.04 but If there's no other option I will install 12.04 and try to see if this works...

@henriquev16,

Before giving up on 13.04, you might want to try the suggestion in this post : [http://ubuntuforums.org/showthread.php?t=2139111&p=12621558](http://ubuntuforums.org/showthread.php?t=2139111&p=12621558)

I and Wild Man had a short discussion in the background about your problem, and we think it may also help if you try wicd instead of the default Network Manager. It has a good record of working better with wireless authentication issues where NM fails.

---

### Post by henriquev16 on 2013-05-02
Thanks @varunendra I will try, I am losing hope but I will try...

---

### Post by henriquev16 on 2013-05-02
Nothing... nothing seems to work guys... I will try 12.04 and see if that is the solution...

---

### Post by varunendra on 2013-05-03
> **henriquev16 said:**
> Nothing... nothing seems to work guys... I will try 12.04 and see if that is the solution...

..And we'd eagerly await your feedback.

I may have forgot to mention that I have the same card AR9285, and last I checked (about a week ago, while I was travelling), it was working great with ath9k included in kernel 3.2.0-36 (Ubuntu 12.04.1)
I haven't updated for months, so can't say about its performance with newer versions.

(I have downloaded 13.04, as well as updates for 12.04, but unfortunately, I don't have any wireless networks around where I live, so can't do the testing myself.)

---

### Post by henriquev16 on 2013-05-03
You all were amazing ! Great support I really appreciate what you have done for me ! I'm sad because I can't install 13.04 ... maybe another time... 

I will try Ubuntu 12.04 do the updates like you said and hope this works! Tell me.. have you simple install ubuntu 12.04 and update or you have done something more? Like one of the things you have mention before...

One thing.. I'm really sorry about my English lol I'm from Portugal but I think I could understand you all ! Thanks!

---

### Post by varunendra on 2013-05-03
Thanks for your kind words, and sorry for not being able to help with 13.04. But the good thing is, 12.04 will be supported till April 2017, while 13.04 is only for 9 months.

> **henriquev16 said:**
> Tell me.. have you simple install ubuntu 12.04 and update or you have done something more? Like one of the things you have mention before...
Nope! I didn't have to use any custom parameters. Everything was at default and it was a clean install of First version of 12.04 (not point release 12.04.1) + usual updates (when kernel 3.2.0-36 was the latest, didn't update after that due to the ultra slow connection I have).

But that was me. Sometimes, with some particular types of available wireless networks, the nohwcrypt=1 parameter makes the connection better. But use it only if needed, otherwise defaults are usually better.

> One thing.. I'm really sorry about my English lol I'm from Portugal but I think I could understand you all ! Thanks!
I couldn't get any hints of 'bad English' from you so far. If you had any troubles in understanding what we wrote, maybe fault was in our English.. (not my first language either) ;)

---

### Post by henriquev16 on 2013-05-03
Thanks you all for the support one more time! I'm learning day by day to get better in English, Linux and other things that I love.. thank you. 

I liked the new look of 13.04 that's why I wanted it... but if 12.04 works I will be happy... So far I have not had time to try 12.04 but when I have I will post here If I succed.

I downloaded 12.04.4 ... hope that don't change anything..

---

### Post by henriquev16 on 2013-05-04
I don't know why this not works... I'm using 12.04 right now but I only have connectivity when I'm close to my Wireless Router... I have the Broadcast SSID Disabled.. could this be a problem?

I tried ath9k driver configurations.. tried to update my system but nothing ... I will have to give up on Ubuntu... :/ I also tried wicd and nothing...

---

### Post by micknotten on 2013-05-04
Hi, I have the same problem, using a HP630. After coding the above, still no connection...

mick@zilverendoos:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
3: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes

---

### Post by varunendra on 2013-05-04
> **henriquev16 said:**
> I don't know why this not works... I'm using 12.04 right now but I only have connectivity when I'm close to my Wireless Router... I have the Broadcast SSID Disabled.. could this be a problem?

Not sure about that. May we see the current report please? That is, the output of "Wireless Script" in my sig.
Also -
```
grep -R [0-9a-zA-Z] /sys/module/ath9k/parameters/
```


@micknotten,
Are you sure you have the same card? Please show us -
```
lspci -nnk | grep -iA2 net
```

As of now, your wireless seems to be hard blocked. Means either it is switched off by a hardware switch, or from BIOS. Please check these.

---

### Post by micknotten on 2013-05-05
Hi, I don't know what wireless script is, but the other two i coded:
thanks for replying.
Mick 
mick@zilverendoos:~$ grep -R [0-9a-zA-Z] /sys/module/ath9k/parameters/
/sys/module/ath9k/parameters/enable_diversity:0
/sys/module/ath9k/parameters/blink:0
/sys/module/ath9k/parameters/nohwcrypt:1
/sys/module/ath9k/parameters/btcoex_enable:0
mick@zilverendoos:~$ 
mick@zilverendoos:~$ 
mick@zilverendoos:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Hewlett-Packard Company Device [103c:3672]
    Kernel driver in use: r8169
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1461]
    Kernel driver in use: ath9k
mick@zilverendoos:~$

---

### Post by varunendra on 2013-05-05
> **micknotten said:**
> 02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1461]
    Kernel driver in use: ath9k

Nevermind, the wireless script part was intended for henriquev16, not for you. As per above, you do seem to have the same card. Have you checked the hardware switch and BIOS?

---

### Post by micknotten on 2013-05-05
In the bios I don't see anything that relates to the wireless connector. For the hardware switch I don't know what you mean....How do I check these?
Thanks in advance,
Mick

---

### Post by varunendra on 2013-05-05
> **micknotten said:**
> In the bios I don't see anything that relates to the wireless connector. For the hardware switch I don't know what you mean....How do I check these?
Thanks in advance,
Mick

Usually the BIOS contains sections to enable/disable onboard adapters/cards, including network controllers. See if yours has something similar. If it is not a UEFI based system (which it won't be if is more than 1.5 year old), the easiest thing to do is to reset the BIOS to defaults.

By hardware switch I mean a physical button, key or a combination of keys that can be used to turn the wireless on/off. It can be a touch-point indicator type, flip-type switch, a push button/key, a Fn+<some function key> combination, etc.

These are especially dodgy in HP/Compaq laptops and don't always work as expected. For example the push button type switches in HP laptops have been frequently reported to be malfunctioning (in both windows and Linux when they do). They won't turn the wireless on no matter how hardly you press them. Then after a few attempts, they suddenly will.

[[COLOR="#800000"]**EDIT: ***Please note that the wireless devices take some time to change their state, which can be upto about half a minute. So give the switch some time before toggling it again.*[/COLOR]]

Similarly, the Fn+<some key> combinatioin sometimes works with a different key than as indicated on the keypad. (for example, it may work with Fn + F10, while the wifi icon was on F6 key).

Another common confusion with the Fn+ combinational keys is that sometimes a key performs its secondary function when pressed alone, while the primary function (F1, F2, F3.... etc.) when pressed with Fn key.

Just take a look at the user manual of your laptop to see what kind of switch it has for quick functions (wireless, volume/brightness control, etc.), and how it works. Try it and post back if it doesn't work.

For removing 'Soft Blocked' states, run the following command -
```
sudo rfkill unblock all
```
Then check the state -
```
rfkill list all
```

---

### Post by micknotten on 2013-05-05
Great, it was the bios set-up! Many thanks to you!
Cheers, Mick

---

### Post by varunendra on 2013-05-05
> **micknotten said:**
> Great, it was the bios set-up! Many thanks to you!
Cheers, Mick
Glad it worked :)

---

