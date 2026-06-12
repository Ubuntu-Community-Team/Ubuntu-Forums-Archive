---
title: "rtl8192se - Wireless Problems on 1201N"
date: 2010-01-30
forum: Networking &amp; Wireless
---

### Post by Sld on 2010-01-30
Hi there,

I'm currently using Ubuntu 9.10 on my brand new Asus Eee PC 1201N, everything was working great till a couple of days ago, when wireless decided not to work anymore.

Wireless connections still appear on network-manager list, but when I select one, it shows me a popup message with "Wireless network Disconnected".

I did not change anything in network-manager, and according to the settings I have on my old laptop, which has a different wireless card, everything is ok.

So I really don't know if this is due to some problems on network-manager or, wireless drivers.

I would appreciate if someone could give some tips on how to solve/debug this problem.

Below are some system informations!

uname -a:
```
Linux hades 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 17:01:44 UTC 2009 x86_64 GNU/Linux
```

lspci:
```
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b3)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:18.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
05:00.0 VGA compatible controller: nVidia Corporation Device 0876 (rev b1)
07:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8171 (rev 10)
09:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
```

lsusb:
```
Bus 003 Device 002: ID 0f62:1001 Acrox Technologies Co., Ltd Targus Mini Trackball Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 2.0 Stick (4GB) / PNY Attache 4GB Stick
Bus 001 Device 004: ID 13d3:5111 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 0b05:1788 ASUSTek Computer, Inc. 
Bus 004 Device 002: ID 04d9:1503 Holtek Semiconductor, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr e0:cb:4e:39:92:e0  
          inet addr:192.168.0.105  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::e2cb:4eff:fe39:92e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:78190 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56555 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:99234132 (99.2 MB)  TX bytes:6811207 (6.8 MB)
          Interrupt:27 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:440 (440.0 B)  TX bytes:440 (440.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:25:d3:93:1f:22  
          inet6 addr: fe80::225:d3ff:fe93:1f22/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Memory:ffffc90002ac8000-ffffc90002ac8100
```

iwconfig:
```
lo        no wireless extensions.

wlan0     802.11bg  Nickname:"rtl8191SEVA1"
          Mode:Managed  Frequency=2.467 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

pan0      no wireless extensions.
```

lsmod:
```
Module                  Size  Used by
nls_iso8859_1           5280  1 
nls_cp437               6976  1 
vfat                   13184  1 
fat                    59832  1 vfat
michael_mic             2848  0 
arc4                    2144  0 
ecb                     3296  0 
binfmt_misc            10220  1 
ppdev                   8232  0 
snd_hda_codec_nvhdmi     6048  1 
snd_hda_codec_realtek   277860  1 
bridge                 56384  0 
stp                     3012  1 bridge
joydev                 13088  0 
bnep                   15168  2 
snd_hda_intel          31880  2 
snd_hda_codec          87584  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
atl1c                  36516  0 
btusb                  14260  2 
uvcvideo               65260  0 
videodev               43360  1 uvcvideo
v4l1_compat            16804  2 uvcvideo,videodev
v4l2_compat_ioctl32    13344  1 videodev
psmouse                57124  0 
serio_raw               6596  0 
r8192se_pci           453960  0 
iptable_filter          3872  0 
shpchp                 37756  0 
eeepc_laptop           17160  0 
ip_tables              21200  1 iptable_filter
x_tables               25832  1 ip_tables
snd                    77096  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
i2c_nforce2             8168  0 
nvidia              10316904  28 
lp                     11908  0 
parport                40528  2 ppdev,lp
usbhid                 43968  0 
usb_storage            66016  1 
video                  23612  0 
output                  3680  1 video

```

modprobe -l | grep 819:
```
kernel/drivers/media/video/bt819.ko
kernel/drivers/staging/rtl8192su/r8192s_usb.ko
kernel/drivers/staging/rtl8192su/ieee80211-rsl.ko
kernel/drivers/staging/rtl8192su/ieee80211/ieee80211_crypt.ko
kernel/drivers/staging/rtl8192su/ieee80211/ieee80211_crypt_tkip.ko
kernel/drivers/staging/rtl8192su/ieee80211/ieee80211_crypt_ccmp.ko
kernel/drivers/staging/rtl8192su/ieee80211/ieee80211_crypt_wep.ko

```

Installed wireless drivers: rtl8192se_linux_2.6.0010.1012.2009_64bit.tar.gz

PS: If you need some more informations, please let me know.

Thanks in advance.

---

### Post by CompMAS2 on 2010-01-31
I am having the same exact problem with Ubuntu Netbook Remix 9.10 with my Eee 1201N.  I also setup wireless with NDISWrapper.  It was working with a router that uses WPA encryption, but now it doesn't want to connect.  I could never get it to work with another wireless router that uses the older WEP security.

---

### Post by chili555 on 2010-01-31
Please see here:> eth0      Link encap:Ethernet  HWaddr e0:cb:4e:39:92:e0  
          inet addr:192.168.0.105  Bcast:192.168.0.255  Mask:255.255.255.0
Also see here:  [https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)

Especially this:> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has has been managed for them; they should simply see uninterrupted network connectivity.You are being 'managed.' Please unplug the ethernet cable and try the wireless again. It may take a reboot.

---

### Post by IceCap on 2010-01-31
Take a look at post #35 from brocie in this thread [here]("http://ubuntuforums.org/showthread.php?t=1343847&page=4").  It looks like ndiswrapper doesn't work well with kernel 2.6.31 (and some earlier ones).

  I have a Mythbuntu 9.10 system (based on xubuntu, but this seems to fairly common within ubuntu distros) and a TrendNet TEW-643PI (rlt8190 chip).  First when I installed it (and used wicd, seems to work much better than network manager) it worked fine.  Since then, it was hit of miss (mostly miss) whether it connected.  Seemed to help to turn my router off and then on.  Didn't matter whether I used DHCP or static IP (typically worked only once in ~50 attempts).

  Since I installed the 2.6.32-10 kernel it works every time.  The only thing that now doesn't seem to work is my remote on my Mythbuntu box but that is probably something that can be easily fixed.

  Note that 2.6.32 is for 10.04 it is not officially compatible with 9.10.

  I guess everyone is hoping for a backport to 2.6.31 but given the status of the wifi on Ubuntu I doubt that will happen.

  Hope this helps.

  IceCap

---

### Post by CompMAS2 on 2010-01-31
I found a solution to get wireless networking to work without NDISWrapper!  I went to the following link to figure it out:
 [COLOR=Blue]
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all)[/COLOR]


I used the rtl8192se_linux_2.6.0010.1211.2009.tar.gz file which was referenced in post #134 and is available here:

[COLOR=Blue][http://launchpadlibrarian.net/36688638/rtl8192se_linux_2.6.0010.1211.2009.tar.gz](http://launchpadlibrarian.net/36688638/rtl8192se_linux_2.6.0010.1211.2009.tar.gz)[/COLOR]


I did the following to get it to work after downloading the file:
```

tar xzf rtl8192se_linux_2.6.0010.1211.2009.tar.gz
cd rtl8192se_linux_2.6.0010.1211.2009
sudo make
```Then you need to edit two files to work with Ubuntu using the following commands (This works on Ubuntu 9.10):
 ```
sed -i 's/install: modules/install:/g' ./ieee80211/Makefile
sed -i 's/install: modules/install:/g' ./HAL/rtl8192/Makefile
```Then you install with the following command:
 ```
sudo make install
sudo echo "r8192se_pci" > /etc/modules
sudo modprobe r8192se_pci
```Your wireless should now be working.  Make sure to remove the NDISWrapper driver before doing this if you have already installed and set it up.

---

### Post by w1ll15 on 2010-02-06
Ndiswrapper Never worked for me 1201n karmic 64bit....HERE is what worked for me...

[http://ohioloco.ubuntuforums.org/showthread.php?t=1267961&highlight=1201n&page=4]("http://ohioloco.ubuntuforums.org/showthread.php?t=1267961&highlight=1201n&page=4")

---

### Post by w1ll15 on 2010-02-11
> **CompMAS2 said:**
> I found a solution to get wireless networking to work without NDISWrapper!  I went to the following link to figure it out:
 [COLOR=Blue]
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all)[/COLOR]


I used the rtl8192se_linux_2.6.0010.1211.2009.tar.gz file which was referenced in post #134 and is available here:

[COLOR=Blue][http://launchpadlibrarian.net/36688638/rtl8192se_linux_2.6.0010.1211.2009.tar.gz](http://launchpadlibrarian.net/36688638/rtl8192se_linux_2.6.0010.1211.2009.tar.gz)[/COLOR]


I did the following to get it to work after downloading the file:
```

tar xzf rtl8192se_linux_2.6.0010.1211.2009.tar.gz
cd rtl8192se_linux_2.6.0010.1211.2009
sudo make
```Then you need to edit two files to work with Ubuntu using the following commands (This works on Ubuntu 9.10):
 ```
sed -i 's/install: modules/install:/g' ./ieee80211/Makefile
sed -i 's/install: modules/install:/g' ./HAL/rtl8192/Makefile
```Then you install with the following command:
 ```
sudo make install
sudo echo "r8192se_pci" > /etc/modules
sudo modprobe r8192se_pci
```Your wireless should now be working.  Make sure to remove the NDISWrapper driver before doing this if you have already installed and set it up.
Hey Much Thanks  CompMAS2 That was the bit of code I was missing...Now the Network Manager see's my card and connects automatically to my network...:) ...Any Reason I have to keep unlocking the Network Manager key ring after reboot?? hmm

---

### Post by ivosir on 2010-03-26
Hi folks,

Sorry for crossposting... but after a sleepless night I managed to make my connection working and stable. :-)

Running Ubuntu Karmic (9.10) 64bit on Asus EEE 1201N with rtl8192se wifi interface.

A few days ago I bought a new wifi router, 802.11n capable. Since that time the connection was a nightmare. Drop-outs every few minutes, kernel panics, cold resets. I tried many driver versions from both [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126) and [http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/), no joy. Ndiswrapper does not work for this network interface on the 64bit OS.

Finally, switching the router from WPA2 to WPA did the magic. Now running the latest driver from the Realtek web site,tThe connection has been rock stable, about 30 hours without a single drop-out, 150 Mbps.

Either the WPA2 implementation must be faulty in the device driver or there is a coincidence of the WPA2 and the 802.11n standard.

Cheers!
Ivo

---

### Post by onlybui on 2010-04-30
Gonna save you guys trouble to get wireless working on 1201N 
follow link for explanation ---> [http://dillernet.com/apple/2010/01/10/eee-1201n-wifi-working-in-karmic-ubuntu/](http://dillernet.com/apple/2010/01/10/eee-1201n-wifi-working-in-karmic-ubuntu/)

or just download 
[http://launchpadlibrarian.net/30532486/e1312wlan.tar.gz](http://launchpadlibrarian.net/30532486/e1312wlan.tar.gz)

use ndiswrapper and load driver listed above.

---

