---
title: "Wireless Keeps Disconnecting"
date: 2011-07-19
forum: Networking &amp; Wireless
---

### Post by plzdontkillme11 on 2011-07-19
Hey,

I'm in need of serious help. I own an Acer Aspire TimelineX 3820T and my wireless is frustrating me to no end. Network manager says that I am connected, but within 1-2 minutes of connecting I am either unable to load any web pages or they load extremely slowly. Also, I have to keep reconnecting with my wireless in order to temporarily regain my usual speed (which lasts for 1-2 minutes, as states above).

I'll post some information to start off with, but be sure to ask me for more if needed.

lspci:
```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Ethernet controller: Atheros Communications AR8151 v1.0 Gigabit Ethernet (rev c0)
04:00.0 Network controller: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

```nm-tools: 
```
NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        20:6A:8A:2B:34:19

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0  [Auto SSekar] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        20:7C:8F:4F:70:67

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    The White House: Infra, 00:24:B2:63:07:64, Freq 2417 MHz, Rate 54 Mb/s, Strength 61 WPA WPA2
    *SSekar:         Infra, C0:3F:0E:A2:F4:50, Freq 2412 MHz, Rate 54 Mb/s, Strength 94 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1



```ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 20:6a:8a:2b:34:19  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:236 errors:0 dropped:0 overruns:0 frame:0
          TX packets:236 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17616 (17.6 KB)  TX bytes:17616 (17.6 KB)

wlan0     Link encap:Ethernet  HWaddr 20:7c:8f:4f:70:67  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::227c:8fff:fe4f:7067/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28679 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23678 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28010152 (28.0 MB)  TX bytes:3722248 (3.7 MB)


```iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"SSekar"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: C0:3F:0E:A2:F4:50   
          Bit Rate=54 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:eek:ff   Fragment thr:eek:ff
          Power Management:eek:ff
          Link Quality=67/70  Signal level=-43 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:22   Missed beacon:0

vboxnet0  no wireless extensions.

```

Thanks in advance!

---

### Post by nm_geo on 2011-07-19
plzdontkillme11

I like that user name ..

Ok a few questions.. New computer?  Right?

I think it would help if we knew what version you are running.

```
 cat /etc/lsb-release
```and kernel

```
uname -r
```and then 
```

lspci -nn | grep 0280
```That will give us the pci number of the wireless

Then 

```
lsmod
```lists loaded modules

```
dmesg | grep wlan0
```

---

### Post by plzdontkillme11 on 2011-07-19
Woah, didn't expect such a speedy reply! 

Here's the info you requested:

```
 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

```Kernel: 2.6.38-10-generic

lspci -nn | grep 0280:

```
04:00.0 Network controller [0280]: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)

```lsmod:

```
Module                  Size  Used by
nls_utf8               12557  0 
hfsplus                84797  0 
usb_storage            53538  0 
uas                    17996  0 
cryptd                 20510  0 
aes_x86_64             17208  1 
aes_generic            38279  1 aes_x86_64
binfmt_misc            17565  1 
vboxnetadp             13382  0 
vboxnetflt             28297  0 
vboxdrv               268268  2 vboxnetadp,vboxnetflt
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     28167  1 
snd_hda_codec_realtek   336771  1 
snd_hda_intel          33211  1 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
arc4                   12529  2 
snd_rawmidi            30486  1 snd_seq_midi
ath9k                 118238  0 
mac80211              294370  1 ath9k
ath9k_common           13851  1 ath9k
uvcvideo               72195  0 
ath9k_hw              323077  2 ath9k,ath9k_common
snd_seq_midi_event     14899  1 snd_seq_midi
videodev               82052  1 uvcvideo
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
v4l2_compat_ioctl32    17078  1 videodev
joydev                 17606  0 
ath                    23773  2 ath9k,ath9k_hw
snd_timer              29602  2 snd_pcm,snd_seq
psmouse                73535  0 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13166  0 
sparse_keymap          13898  0 
snd                    67382  12 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              178528  3 ath9k,mac80211,ath
lp                     17825  0 
intel_ips              18097  0 
parport                46458  3 parport_pc,ppdev,lp
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i915                  514975  9 
drm_kms_helper         42136  1 i915
drm                   227495  5 i915,drm_kms_helper
ahci                   25951  2 
atl1c                  41171  0 
i2c_algo_bit           13400  1 i915
video                  19438  1 i915
libahci                26642  1 ahci

```dmesg | grep wlan0:

```
[   25.315772] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   56.044446] wlan0: authenticate with c0:3f:0e:a2:f4:50 (try 1)
[   56.046427] wlan0: authenticated
[   56.046465] wlan0: associate with c0:3f:0e:a2:f4:50 (try 1)
[   56.049251] wlan0: RX AssocResp from c0:3f:0e:a2:f4:50 (capab=0x411 status=0 aid=1)
[   56.049257] wlan0: associated
[   56.049845] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   66.550762] wlan0: no IPv6 routers present
[  275.282207] wlan0: deauthenticating from c0:3f:0e:a2:f4:50 by local choice (reason=3)
[  276.670601] wlan0: authenticate with c0:3f:0e:a2:f4:50 (try 1)
[  276.672590] wlan0: authenticated
[  276.672632] wlan0: associate with c0:3f:0e:a2:f4:50 (try 1)
[  276.677655] wlan0: RX AssocResp from c0:3f:0e:a2:f4:50 (capab=0x411 status=0 aid=1)
[  276.677663] wlan0: associated
[ 5059.511520] wlan0: deauthenticating from c0:3f:0e:a2:f4:50 by local choice (reason=3)
[ 5060.970880] wlan0: authenticate with c0:3f:0e:a2:f4:50 (try 1)
[ 5060.972955] wlan0: authenticated
[ 5060.972981] wlan0: associate with c0:3f:0e:a2:f4:50 (try 1)
[ 5060.975727] wlan0: RX AssocResp from c0:3f:0e:a2:f4:50 (capab=0x411 status=0 aid=1)
[ 5060.975735] wlan0: associated
[ 8332.744470] wlan0: deauthenticating from c0:3f:0e:a2:f4:50 by local choice (reason=3)
[ 8340.297736] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8342.831504] wlan0: authenticate with c0:3f:0e:a2:f4:50 (try 1)
[ 8342.833483] wlan0: authenticated
[ 8342.833522] wlan0: associate with c0:3f:0e:a2:f4:50 (try 1)
[ 8342.836314] wlan0: RX AssocResp from c0:3f:0e:a2:f4:50 (capab=0x411 status=0 aid=4)
[ 8342.836321] wlan0: associated
[ 8342.837234] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 8353.177762] wlan0: no IPv6 routers present
[ 8508.059918] wlan0: deauthenticating from c0:3f:0e:a2:f4:50 by local choice (reason=3)
[ 8509.532651] wlan0: authenticate with c0:3f:0e:a2:f4:50 (try 1)
[ 8509.534660] wlan0: authenticated
[ 8509.534690] wlan0: associate with c0:3f:0e:a2:f4:50 (try 1)
[ 8509.537421] wlan0: RX AssocResp from c0:3f:0e:a2:f4:50 (capab=0x411 status=0 aid=4)
[ 8509.537431] wlan0: associated
[ 8982.798120] wlan0: deauthenticating from c0:3f:0e:a2:f4:50 by local choice (reason=3)
[ 8984.268034] wlan0: authenticate with c0:3f:0e:a2:f4:50 (try 1)
[ 8984.269978] wlan0: authenticated
[ 8984.270102] wlan0: associate with c0:3f:0e:a2:f4:50 (try 1)
[ 8984.272874] wlan0: RX AssocResp from c0:3f:0e:a2:f4:50 (capab=0x411 status=0 aid=4)
[ 8984.272884] wlan0: associated
[ 9063.991508] wlan0: deauthenticating from c0:3f:0e:a2:f4:50 by local choice (reason=3)
[ 9065.396901] wlan0: authenticate with c0:3f:0e:a2:f4:50 (try 1)
[ 9065.398898] wlan0: authenticated
[ 9065.398937] wlan0: associate with c0:3f:0e:a2:f4:50 (try 1)
[ 9065.403291] wlan0: RX AssocResp from c0:3f:0e:a2:f4:50 (capab=0x411 status=0 aid=4)
[ 9065.403299] wlan0: associated
[10555.294799] wlan0: deauthenticating from c0:3f:0e:a2:f4:50 by local choice (reason=3)
[10556.744939] wlan0: authenticate with c0:3f:0e:a2:f4:50 (try 1)
[10556.746928] wlan0: authenticated
[10556.746970] wlan0: associate with c0:3f:0e:a2:f4:50 (try 1)
[10556.749776] wlan0: RX AssocResp from c0:3f:0e:a2:f4:50 (capab=0x411 status=0 aid=4)
[10556.749786] wlan0: associated
[10830.150566] wlan0: deauthenticating from c0:3f:0e:a2:f4:50 by local choice (reason=3)
[10831.676721] wlan0: authenticate with c0:3f:0e:a2:f4:50 (try 1)
[10831.678675] wlan0: authenticated
[10831.678717] wlan0: associate with c0:3f:0e:a2:f4:50 (try 1)
[10831.681453] wlan0: RX AssocResp from c0:3f:0e:a2:f4:50 (capab=0x411 status=0 aid=4)
[10831.681460] wlan0: associated
[11243.541853] wlan0: deauthenticating from c0:3f:0e:a2:f4:50 by local choice (reason=3)
[11245.042450] wlan0: authenticate with c0:3f:0e:a2:f4:50 (try 1)
[11245.044428] wlan0: authenticated
[11245.044454] wlan0: associate with c0:3f:0e:a2:f4:50 (try 1)
[11245.047177] wlan0: RX AssocResp from c0:3f:0e:a2:f4:50 (capab=0x411 status=0 aid=4)
[11245.047180] wlan0: associated
[11378.734199] wlan0: deauthenticating from c0:3f:0e:a2:f4:50 by local choice (reason=3)
[11380.132089] wlan0: authenticate with c0:3f:0e:a2:f4:50 (try 1)
[11380.134078] wlan0: authenticated
[11380.134105] wlan0: associate with c0:3f:0e:a2:f4:50 (try 1)
[11380.136859] wlan0: RX AssocResp from c0:3f:0e:a2:f4:50 (capab=0x411 status=0 aid=4)
[11380.136863] wlan0: associated
[12216.934013] wlan0: deauthenticating from c0:3f:0e:a2:f4:50 by local choice (reason=3)
[12218.366168] wlan0: authenticate with c0:3f:0e:a2:f4:50 (try 1)
[12218.368113] wlan0: authenticated
[12218.388748] wlan0: associate with c0:3f:0e:a2:f4:50 (try 1)
[12218.391501] wlan0: RX AssocResp from c0:3f:0e:a2:f4:50 (capab=0x411 status=0 aid=4)
[12218.391510] wlan0: associated
[13403.178814] wlan0: deauthenticating from c0:3f:0e:a2:f4:50 by local choice (reason=3)
[13404.644458] wlan0: authenticate with c0:3f:0e:a2:f4:50 (try 1)
[13404.646406] wlan0: authenticated
[13404.646430] wlan0: associate with c0:3f:0e:a2:f4:50 (try 1)
[13404.649223] wlan0: RX AssocResp from c0:3f:0e:a2:f4:50 (capab=0x411 status=0 aid=4)
[13404.649229] wlan0: associated
[13443.977629] wlan0: deauthenticating from c0:3f:0e:a2:f4:50 by local choice (reason=3)
[13445.537630] wlan0: authenticate with c0:3f:0e:a2:f4:50 (try 1)
[13445.539625] wlan0: authenticated
[13445.539666] wlan0: associate with c0:3f:0e:a2:f4:50 (try 1)
[13445.542445] wlan0: RX AssocResp from c0:3f:0e:a2:f4:50 (capab=0x411 status=0 aid=4)
[13445.542451] wlan0: associated

```

And yes, it's a new computer. I've had this only for around 2 or 3 months. I forgot to say: wireless worked flawlessly at first, but it only recently started doing this (maybe 4 weeks to a month ago).

---

### Post by thefasterblueone on 2011-07-19
Here is a bug report on this, [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/548992]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/548992")

Some users solved this issue by turning off "power management".

```
iwconfig wlan0 power off
```

Other users uninstalled "Network Manager" and installed "WICD".

WICD can be found in "Ubuntu Software Center". 

Before uninstalling "Network Manager" be sure to install "WICD" first or you will not have an internet connection to install "WICD".

Then you will need to uninstall "Network Manager".

```
sudo apt-get remove --purge network-manager
```

I use "WICD" and my wireless works great, never could get "Network Manager" to work right/consistently.

---

### Post by plzdontkillme11 on 2011-07-19
Wow, what a difference!

However, I won't mark this thread as solved just yet - I'll see if it's still this fast tomorrow.

Thanks for the help, thefasterblueone.

---

### Post by nm_geo on 2011-07-19
> **plzdontkillme11 said:**
> Wow, what a difference!

However, I won't mark this thread as solved just yet - I'll see if it's still this fast tomorrow.

Thanks for the help, thefasterblueone.


Does the wicd icon appear in the upper panel?  I used wicd during the alpha testing of Natty and I can not remember.

---

### Post by plzdontkillme11 on 2011-07-19
nm_geo - It doesn't, though you can just add it to the dock. Not as good, but it'll do. :]

---

### Post by nm_geo on 2011-07-19
> **plzdontkillme11 said:**
> nm_geo - It doesn't, though you can just add it to the dock. Not as good, but it'll do. :]

There is a fix.. 

```
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
```
If you have issues go to the website.  good stuff there

[http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)

---

### Post by plzdontkillme11 on 2011-07-20
Nice, thanks! And that article is definitely a good read as well.

---

