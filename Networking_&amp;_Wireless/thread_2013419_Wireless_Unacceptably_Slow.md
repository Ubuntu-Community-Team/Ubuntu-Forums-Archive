---
title: "Wireless Unacceptably Slow"
date: 2012-06-30
forum: Networking &amp; Wireless
---

### Post by Jeff9 on 2012-06-30
As title says, my internet browsing/ download speeds are unbearably slow. Videos won't load and browsing is just generally unpleasant. I did what was recommended here to no avail...

[http://www.unixmen.com/resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal/](http://www.unixmen.com/resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal/)

Please help!

---

### Post by wildmanne39 on 2012-06-30
Hi, please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by Jeff9 on 2012-06-30
**cat /etc/lsb-release; uname -a**
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux jeff-desktop 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

**lspci -nnk | grep -iA2 net**
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
    Kernel driver in use: r8169
--
05:00.0 Network controller [0280]: Ralink corp. RT3062 Wireless 802.11n 2T/2R [1814:3062]
    Subsystem: Edimax Computer Co. Device [1432:7722]
    Kernel driver in use: rt2800pci

**lsusb**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:2106 Dell Computer Corp. Dell QuietKey Keyboard
Bus 003 Device 003: ID 0461:4d22 Primax Electronics, Ltd 

**iwconfig**
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"SwampHouse"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 68:7F:74:BA:1B:97   
          Bit Rate=43.3 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:44  Invalid misc:152   Missed beacon:0

eth0      no wireless extensions.

**rfkill list all**
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

**lsmod**
Module                  Size  Used by
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
vesafb                 13844  1 
binfmt_misc            17540  1 
arc4                   12529  2 
rt2800pci              18715  0 
rt2800lib              58925  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
snd_hda_codec_hdmi     32474  1 
rt2x00pci              14577  1 rt2800pci
rt2x00lib              55301  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              506816  3 rt2800lib,rt2x00pci,rt2x00lib
snd_hda_codec_realtek   223867  1 
ppdev                  17113  0 
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi_event     14899  1 snd_seq_midi
cfg80211              205544  2 rt2x00lib,mac80211
nvidia              12319264  40 
eeprom_93cx6           12725  1 rt2800pci
parport_pc             32866  1 
mac_hid                13253  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_rawmidi,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
psmouse                87692  0 
serio_raw              13211  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
it87                   43384  0 
hwmon_vid              12827  1 it87
coretemp               13525  0 
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
floppy                 70365  0 
usbhid                 47199  0 
hid                    99559  1 usbhid
pata_jmicron           12747  0 
r8169                  62099  0 




I changed the channel on my router which positive affected browsing speeds, but download and video loading is incredibly slow. Under Windows, this was not the case.  Any help is appreciated!

---

### Post by wildmanne39 on 2012-06-30
Hi, the things from the link you posted would not work because they have nothing to do with your driver please undo those changes.

Then do:
```
echo "options rt2800pci  nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci 
sudo modprobe -v rt2800pci
```
Then change your wireless settings in network manager to match the screenshots and make sure your wired connection is unplugged.

If you still have issues please post the output of:
```
nm-tool

```

I suspect your internet is slow partly due to the fact if you have the wired connection plugged in it is used by default, and the driver for your ehternet card probably needs changed to the r8168
Thanks

---

### Post by Jeff9 on 2012-07-01
The wired connection is not plugged in. How to I go about switching to the "correct" driver?  Below is the output from [B]nm-tool

[/B]NetworkManager Tool

State: connected (global)

- Device: wlan0  [SwampHouse] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             connected
  Default:           yes
  HW Address:        80:1F:02:4F:11:7B

  Capabilities:
    Speed:           120 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    JNSI2:           Infra, 00:1F:90:EE:5B:0E, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WEP
    *SwampHouse:     Infra, 68:7F:74:BA:1B:97, Freq 2417 MHz, Rate 54 Mb/s, Strength 63 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.147
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             75.75.75.75
    DNS:             75.75.76.76


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:24:1D:29:95:2A

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

---

### Post by wildmanne39 on 2012-07-01
Hi, I would set the router to channel 1 or 11 for best results, also set the encryption to just wpa2 only in the router it works best with linux.

For the ethernet if it is working good you can leave it or start a new thread just for ehternet.
Thanks

---

### Post by Jeff9 on 2012-07-01
Will set the router and the security as you say.

Where can I learn about which driver is most appropriate for my wireless adapter?

---

### Post by wildmanne39 on 2012-07-02
Hi, you have the best driver that comes with ubuntu already installed for wireless.

You might be able to compile a driver from the manufacturers website, but there is no guarantee that it will help.

Is wireless still slow?
Thanks

---

