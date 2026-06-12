---
title: "driver Ralink"
date: 2012-11-17
forum: Networking &amp; Wireless
---

### Post by mondom on 2012-11-17
hello
I've got a pavillion g6 with ubuntu 12.04
my wireless card is Ralink corp. Device 539a
the wifi connection don't work, so I downloaded from the Ralink site the supposed driver :2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO

i've installed this with the command "make, sudo make install" from the shell, and the connection worked fine.
but when I turned off the pc and restart it, the wifi connection don't work anymore.
I suppose the drivers aren't loaded at the start-up, can anyone  help me please?

---

### Post by Abhinav Kumar on 2012-11-17
> **mondom said:**
> hello
I've got a pavillion g6 with ubuntu 12.04
my wireless card is Ralink corp. Device 539a
the wifi connection don't work, so I downloaded from the Ralink site the supposed driver :2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO

i've installed this with the command "make, sudo make install" from the shell, and the connection worked fine.
but when I turned off the pc and restart it, the wifi connection don't work anymore.
I suppose the drivers aren't loaded at the start-up, can anyone  help me please?
Hi mondom,

Have a look at
[http://ubuntuforums.org/showthread.php?t=1743525](http://ubuntuforums.org/showthread.php?t=1743525)

Regards,
Abhinav

---

### Post by wildmanne39 on 2012-11-17
Hi, please do:
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms patch fakeroot unzip
wget http://media.cdn.ubuntu-de.org/forum/attachments/35/07/3208747-angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO.zip
unzip angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO.zip
cd angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/
sudo make
sudo make install
sudo modprobe -v rt5390sta
sudo depmod -a
sudo update-initramfs -u 
```
Thanks

---

### Post by mondom on 2012-11-17
thanks for the fast answers!
i've tried the Wild Man method, everything was right, but when I restarted the pc the wifi card didn't connect 

how can I uninstall the files that I've installed in Wild Man's process?

So, I started to read the thread suggested from Abhinav Kumar from the 9th post
i've skipped the step about the patch because I use ubuntu 12.04,using the new drivers in the Ralink's site, but at the end of the process, the wifi connection don't work yet

i've read in the  driver the README file , that explain ( I suppose) how to charge this driver at the startup, but it's too complicated to me.
help me please

---

### Post by wildmanne39 on 2012-11-17
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by flash63 on 2012-11-17
Hello,
there exist an installation package for DKMS, but both packages work only with Kernel-Image 3.2.0.31 or a lower Version!

Reference:
[http://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3473742](http://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3473742)

Blacklist rt2800pci an load rt5390sta automatically
```
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist.conf
echo rt5390sta | sudo tee -a /etc/modules
```

---

### Post by mondom on 2012-11-18
> then reply back  and attach the netinfo.txt file.

> #!/bin/bash
#Script created by anewguy, tested by chili555 and edited by krytarik, llua and wildmanne39
exec > netinfo.txt 2> /dev/null
echo -e "\n*************** info trace ****************\n"
echo -e "\n\n**** uname -a ****\n\n"
uname -a
echo -e "\n\n**** lsb-release ****\n\n"
cat /etc/lsb-release
echo -e "\n\n**** lspci ****\n\n"
lspci -nnk | grep -iA2 net
echo -e "\n\n**** lsusb ****\n\n"
lsusb
echo -e "\n\n**** iwconfig ****\n\n"
iwconfig
echo -e "\n\n**** rfkill ****\n\n"
rfkill list all
echo -e "\n\n**** lsmod ****\n\n"
lsmod
echo -e "\n\n**** nm-tool ****\n\n"
nm-tool
echo -e "\n\n**** NetworkManager.state ****\n\n"
cat /var/lib/NetworkManager/NetworkManager.state
echo -e "\n\n**** NetworkManager.conf ****\n\n"
cat /etc/NetworkManager/NetworkManager.conf
echo -e "\n\n**** NetworkManager.conf-10.04 ****\n\n"
cat /etc/NetworkManager/nm-system-settings.conf
echo -e "\n\n**** interfaces ****\n\n"
cat /etc/network/interfaces | sed 's/wpa-psk [[:graph:]:]\+/wpa-psk <WPA key removed>/'
echo -e "\n\n**** iwlist ****\n\n"
[ -t 0 ] && sudo iwlist scan
[ ! -t 0 ] && gksudo iwlist scan
echo -e "\n\n**** resolv ****\n\n"
cat /etc/resolv.conf
echo -e "\n\n**** blacklist.conf ****\n\n"
cat /etc/modprobe.d/blacklist.conf
echo -e "\n\n**** dmesg ****\n\n"
dmesg | egrep 'air|ath|carl|at7|iwl|ipw|rtl8|rt2|rt3|rt6|rt7|r818|r871|rtl8|tg3|ssb|wl|b43|bcma|brcm|b44|eth1|ndis|wmi|wlan0'
echo -e "\n\n**************** done ********************\n\n"
sed -i 's/\([[:alnum:]][[:alnum:]]:\)\{5\}[[:alnum:]][[:alnum:]]/<MAC address removed>/' netinfo.txt

this is the script

---

### Post by mondom on 2012-11-18
to flash63
i've made uname -r into the terminal and i this reponse:
> domenico@domenico-HP-Pavilion-g6-Notebook-PC:~$ uname -r
3.2.0-32-generic-pae

so i think i'm out  for your solution, 
thanks anyway

---

### Post by wildmanne39 on 2012-11-18
Hi, you posted the script, we need to see the textinfo file created by the script it will also be in your home folder.
Thanks

---

### Post by mondom on 2012-11-20
sorry
> 
*************** info trace ****************



**** uname -a ****


Linux domenico-HP-Pavilion-g6-Notebook-PC 3.2.0-32-generic-pae #51-Ubuntu SMP Wed Sep 26 21:54:23 UTC 2012 i686 i686 i386 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"


**** lspci ****


01:00.0 Network controller [0280]: Ralink corp. Device [1814:539a]
    Subsystem: Hewlett-Packard Company Device [103c:1839]
    Kernel driver in use: rt2800pci
--
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:1841]
    Kernel driver in use: r8169


**** lsusb ****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 05c8:0223 Cheng Uei Precision Industry Co., Ltd (Foxlink) 


**** iwconfig ****


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


**** rfkill ****


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no


**** lsmod ****


Module                  Size  Used by
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_idt      60251  1 
parport_pc             32114  0 
rfcomm                 38139  0 
bnep                   17830  2 
ppdev                  12849  0 
bluetooth             158438  10 bnep,rfcomm
joydev                 17393  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_hda_intel          32765  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
uvcvideo               67203  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               86588  1 uvcvideo
psmouse                86486  0 
serio_raw              13027  0 
snd                    62064  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
arc4                   12473  2 
hp_accel               25728  0 
lis3lv02d              19268  1 hp_accel
input_polldev          13648  1 lis3lv02d
mac_hid                13077  0 
soundcore              14635  1 snd
wmi                    18744  1 hp_wmi
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
rt2800pci              18340  0 
rt2800lib              53264  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48836  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              436455  3 rt2800lib,rt2x00pci,rt2x00lib
i915                  419110  3 
cfg80211              178679  2 rt2x00lib,mac80211
drm_kms_helper         45466  1 i915
mei                    36570  0 
eeprom_93cx6           12653  1 rt2800pci
drm                   197599  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  56321  0 


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: eth0  [Connessione via cavo 1] ---------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    retedigicom:     Infra, <MAC address removed>, Freq 2432 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2




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


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"retedigicom"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007fd3ae3756
                    Extra: Last beacon: 832ms ago
                    IE: Unknown: 000B7265746564696769636F6D
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030105
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1605070600000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD1E00904C33EE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3405070600000000000000000000000000000000000000



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




**** dmesg ****


[   18.707810] rt2800pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.707838] rt2800pci 0000:01:00.0: setting latency timer to 64
[   18.712778] wmi: Mapper loaded
[   18.800588] Registered led device: rt2800pci-phy0::radio
[   18.800970] Registered led device: rt2800pci-phy0::assoc
[   18.801005] Registered led device: rt2800pci-phy0::quality
[   19.318118] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.322644] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   43.178331] wlan0: authenticate with <MAC address removed> (try 1)
[   43.179756] wlan0: authenticated
[   43.198237] wlan0: associate with <MAC address removed> (try 1)
[   43.201768] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[   43.201772] wlan0: associated
[   43.210392] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   46.437645] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[   47.698496] wlan0: authenticate with <MAC address removed> (try 1)
[   47.701556] wlan0: authenticated
[   47.703571] wlan0: associate with <MAC address removed> (try 1)
[   47.707210] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[   47.707220] wlan0: associated
[   51.441657] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[   52.770697] wlan0: authenticate with <MAC address removed> (try 1)
[   52.772344] wlan0: authenticated
[   52.772827] wlan0: associate with <MAC address removed> (try 1)
[   52.778393] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[   52.778397] wlan0: associated
[   56.465536] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[   57.794611] wlan0: authenticate with <MAC address removed> (try 1)
[   57.798440] wlan0: authenticated
[   57.798892] wlan0: associate with <MAC address removed> (try 1)
[   57.810510] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[   57.810520] wlan0: associated
[   62.465430] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[   63.778865] wlan0: authenticate with <MAC address removed> (try 1)
[   63.780556] wlan0: authenticated
[   63.793972] wlan0: associate with <MAC address removed> (try 1)
[   63.801651] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[   63.801660] wlan0: associated
[   67.465386] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[   68.713394] wlan0: no IPv6 routers present
[   68.718603] wlan0: authenticate with <MAC address removed> (try 1)
[   68.720089] wlan0: authenticated
[   68.720654] wlan0: associate with <MAC address removed> (try 1)
[   68.724173] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[   68.724180] wlan0: associated
[   72.469297] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[   73.722576] wlan0: authenticate with <MAC address removed> (try 1)
[   73.730061] wlan0: authenticated
[   73.746074] wlan0: associate with <MAC address removed> (try 1)
[   73.751554] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[   73.751570] wlan0: associated
[   77.465247] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[   78.754106] wlan0: authenticate with <MAC address removed> (try 1)
[   78.756117] wlan0: authenticated
[   78.756684] wlan0: associate with <MAC address removed> (try 1)
[   78.765689] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[   78.765693] wlan0: associated
[   82.453255] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[   83.746494] wlan0: authenticate with <MAC address removed> (try 1)
[   83.748752] wlan0: authenticated
[   83.749403] wlan0: associate with <MAC address removed> (try 1)
[   83.752999] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[   83.753005] wlan0: associated
[   87.465187] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[   88.709962] wlan0: authenticate with <MAC address removed> (try 1)
[   88.715451] wlan0: authenticated
[   88.716128] wlan0: associate with <MAC address removed> (try 1)
[   88.720661] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[   88.720666] wlan0: associated
[   92.457060] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[   93.718022] wlan0: authenticate with <MAC address removed> (try 1)
[   93.719538] wlan0: authenticated
[   93.720098] wlan0: associate with <MAC address removed> (try 1)
[   93.723532] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[   93.723537] wlan0: associated
[   97.453008] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[   98.697683] wlan0: authenticate with <MAC address removed> (try 1)
[   98.699127] wlan0: authenticated
[   98.700364] wlan0: associate with <MAC address removed> (try 1)
[   98.705993] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[   98.705998] wlan0: associated
[  102.432950] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[  103.346888] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  107.317813] wlan0: authenticate with <MAC address removed> (try 1)
[  107.319362] wlan0: authenticated
[  107.333565] wlan0: associate with <MAC address removed> (try 1)
[  107.339191] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  107.339201] wlan0: associated
[  107.349951] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  113.469129] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)


**************** done ********************



is this the right file?

---

### Post by wildmanne39 on 2012-11-20
Hi, I do not believe the driver you are using is the best one for this card it usually uses the 5390.

You should have posted the infotext file after you installed the 5390 with my directions in my previous post so we could have done some troubleshooting.

You can try this.
```
echo "options rt2800pci  nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci
```
does that help?
Thanks

---

### Post by mondom on 2012-11-20
y.o.u  a.r.e  t.h.e   b.e.s.t!!!!
it work very well!
now i finally enjoy a stable  wifi connection!

---

### Post by wildmanne39 on 2012-11-20
Your welcome! please use thread tools at the to of the page to mark the thread solved.
Thanks

---

