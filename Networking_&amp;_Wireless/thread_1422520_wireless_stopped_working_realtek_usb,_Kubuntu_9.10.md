---
title: "wireless stopped working: realtek usb, Kubuntu 9.10, custom meshcomputers machine"
date: 2010-03-05
forum: Networking &amp; Wireless
---

### Post by phischphood on 2010-03-05
I just fresh installed Kubuntu last night on an external HD. I spent a few hours getting the wireless card to work and succeeded. This morning I turn on my machine and the wireless doesn't work. I followed this guide [http://ubuntuforums.org/showthread.php?t=946893](http://ubuntuforums.org/showthread.php?t=946893) then added a connection in the wireless tab  and it worked.
lsusb gives:
> Bus 001 Device 003: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter

iwconfig gives:
> lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"BeBox"
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Tx-Power=20 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lsmod gives:

> lsmod
Module                  Size  Used by
ndiswrapper           245248  0      
snd_hda_codec_analog    79680  1     
arc4                    2144  2      
ecb                     3296  2      
lp                     11908  0      
ppdev                   8232  0      
rtl8187                53604  0      
mac80211              210104  1 rtl8187
led_class               5256  1 rtl8187
eeprom_93cx6            2528  1 rtl8187
psmouse                57124  0
amd64_edac_mod         26688  0
serio_raw               6596  0
edac_core              48876  1 amd64_edac_mod
k8temp                  5504  0
ns558                   6688  0
i2c_nforce2             8168  0
gameport               13712  2 ns558
parport_pc             37352  1
snd_mpu401              9288  0
snd_mpu401_uart         8480  1 snd_mpu401
asus_atk0110            9472  0
parport                40528  3 lp,ppdev,parport_pc
snd_hda_intel          31880  2
snd_hda_codec          87584  2 snd_hda_codec_analog,snd_hda_intel
snd_usb_audio         102976  0
snd_pcm_oss            44704  0
snd_mixer_oss          18976  1 snd_pcm_oss
snd_seq_dummy           3460  0
snd_pcm                93160  4 snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm_oss
snd_usb_lib            19648  1 snd_usb_audio
snd_hwdep               9352  2 snd_hda_codec,snd_usb_audio
snd_seq_oss            33440  0
snd_seq_midi            8192  0
snd_rawmidi            27360  3 snd_mpu401_uart,snd_usb_lib,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iptable_filter          3872  0
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ip_tables              21200  1 iptable_filter
snd                    77096  19 snd_hda_codec_analog,snd_mpu401,snd_mpu401_uart,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
x_tables               25832  1 ip_tables
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
soundcore               9088  1 snd
cfg80211              109144  2 rtl8187,mac80211
nvidia              10316904  36
usbhid                 43968  0
usb_storage            65952  4
ohci1394               33780  0
ieee1394              100896  1 ohci1394
floppy                 65192  0
forcedeth              61292  0


ask if there's any more info you want. Oh yeah I'm using 64bit Kubunto 9.10, I have an AMD Athalon XP 3500+ processor

---

### Post by chili555 on 2010-03-05
> wlan0 IEEE 802.11bg ESSID:"BeBox"
Mode:Managed Frequency:2.462 GHz Access Point: Not-Associated
Tx-Power=20 dBmIt looks like it's working. What, specifically, doesn't work as expected?

---

### Post by phischphood on 2010-03-06
Sorry, forgot to include that bit. If I try to use anything I don't get an internet connection. If I click on the connections icon on the toolbar There is an icon for BeBox, the name of the connection, but it doesn't say active below it like my ethernet connection does. 

If I click on it then it says "Configuring interface" when I hover over the connections icon, "activating" under the BeBox icon and 
"Type: Wi-Fi
interface: wlan0
Hardware address: 00:11:3B:14:13:34
Driver: rtl8187
Status: preparing to connect
IP Address:
Name Servers:
Domains:
"
when I hover over the BeBox icon. Then in about the amount of time it takes to write this post it gives up and stops. Every so often during the period before it gives up it comes up with a dialogue box titled "Secrets for BeBox - KNetworkManager" containing all the security info I've already given it and ok/cancel buttons. It is worth noting that the WiFi still works when I'm on Windows XP and it did work on Kubuntu for the evening when I set it up.

---

### Post by phischphood on 2010-03-08
Anyone got any idea how to fix this issue?

---

### Post by phischphood on 2010-03-28
Still having this problem, I'm guessing it's a problem with my WEP settings. In my WiFi network connection settings I have the following:

Wireless tab shows:

SSID: BeBox
Mode: Infrastructure
BSSID: __:__:__:__:__:__
Restrict to interface: any
MTU: Automatic
________________________________________
Security tab shows:

Security: WEP
Key type: Key (for 64 or 128 bits)
Key: (My key is a 10 character hex string)
WEP Index: 1(Default)
Authentication: Open System
________________________________________
IP Address tab shows:

Configure: Automatic (DHCP)
the other fields are disabled:
IP Address, Subnet Mask, Gateway, Search Domains, DNS Servers


I've tried changing most of the drop down options with no success in any of the combinations.

---

### Post by chili555 on 2010-03-28
I notice in your lsmod that both ndiswrapper and rtl8187 are loaded. Are they fighting for wireless domination? Is ndiswrapper explicitly loaded in */etc/modules*?

I also noticed:> "Type: Wi-Fi
interface: wlan0
Hardware address: 00:11:3B:14:13:34
[COLOR="Red"]Driver: rtl8187[/COLOR]
Status: preparing to connect
IP Address:
Name Servers:
Domains:
"You might unload ndiswrapper:```
sudo rmmod -f ndiswrapper
```See if things improve. If it works, we will have to do some tweaking to make it permanent.

---

