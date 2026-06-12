---
title: "Not able to connect to home wireless (HP ProBook laptop)"
date: 2012-10-28
forum: Networking &amp; Wireless
---

### Post by luben on 2012-10-28
Hello,

I installed Ubuntu recently and I can't make my wireless connection at home to work. With WINDOWS 7 it works. Also, the cable connection work fine in Ubuntu but I can't keep my laptop in the dining room all the time. So I need to make the wireless work. Here are some information I collected. Thank you for your help.

Laptop HP ProBook 4530s

lspci
25:00.0 Network controller: Ralink corp. Device 3592
26:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

lsusb
Bus 002 Device 004: ID 148f:2000 Ralink Technology, Corp. 

ifconfig
wlan0     Link encap:Ethernet  HWaddr 44:6d:57:5a:af:f7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:85 errors:0 dropped:0 overruns:0 frame:0
          TX packets:118 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13176 (13.1 KB)  TX bytes:22704 (22.7 KB)

iwconfig
wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

lsmod
Module                  Size  Used by
bnep                   18281  2 
parport_pc             32866  0 
rfcomm                 47604  12 
ppdev                  17113  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
uvcvideo               72627  0 
joydev                 17693  0 
snd_seq_midi_event     14899  1 snd_seq_midi
videodev               98259  1 uvcvideo
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
arc4                   12529  2 
rt2800pci              18715  0 
rt2800lib              58925  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14577  1 rt2800pci
rt2x00lib              55279  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              506816  3 rt2800lib,rt2x00pci,rt2x00lib
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
v4l2_compat_ioctl32    17128  1 videodev
snd                    78855  19 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  473298  2 
fglrx                3263886  0 
hp_accel               25976  0 
cfg80211              205544  2 rt2x00lib,mac80211
drm_kms_helper         46978  1 i915
btusb                  18288  2 
mac_hid                13253  0 
lis3lv02d              19876  1 hp_accel
eeprom_93cx6           12725  1 rt2800pci
drm                   241921  3 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
mei                    41616  0 
psmouse                97443  0 
video                  19596  1 i915
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
soundcore              15091  1 snd
jmb38x_ms              17646  0 
memstick               16569  1 jmb38x_ms
serio_raw              13211  0 
input_polldev          13896  1 lis3lv02d
bluetooth             180104  23 bnep,rfcomm,btusb
wmi                    19256  1 hp_wmi
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
r8169                  62099  0 

dmesg | grep "wlan"
[   22.284562] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.285194] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.194808] wlan0: authenticate with a0:21:b7:a0:65:e2 (try 1)
[   29.196158] wlan0: authenticated
[   29.218858] wlan0: associate with a0:21:b7:a0:65:e2 (try 1)
[   29.223384] wlan0: RX AssocResp from a0:21:b7:a0:65:e2 (capab=0x431 status=0 aid=3)
[   29.223392] wlan0: associated
[   29.235560] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   39.518889] wlan0: no IPv6 routers present
[   53.649639] ieee80211 phy0: wlan0: No probe response from AP a0:21:b7:a0:65:e2 after 500ms, disconnecting.
[   69.297031] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5106.019162] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5112.559323] wlan0: authenticate with a0:21:b7:a0:65:e2 (try 1)
[ 5112.756481] wlan0: authenticate with a0:21:b7:a0:65:e2 (try 2)
[ 5112.757918] wlan0: authenticated
[ 5112.758338] wlan0: associate with a0:21:b7:a0:65:e2 (try 1)
[ 5112.762153] wlan0: RX AssocResp from a0:21:b7:a0:65:e2 (capab=0x431 status=0 aid=3)
[ 5112.762163] wlan0: associated
[ 5112.774336] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5123.969283] wlan0: no IPv6 routers present
[ 5136.978025] ieee80211 phy0: wlan0: No probe response from AP a0:21:b7:a0:65:e2 after 500ms, disconnecting.
[ 5152.624737] ADDRCONF(NETDEV_UP): wlan0: link is not ready

sudo lshw -C network
  *-network               
       description: Wireless interface
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:25:00.0
       logical name: wlan0
       version: 00
       serial: 44:6d:57:5a:af:f7
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.2.0-32-generic firmware=0.34 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:19 memory:d4700000-d470ffff

iwlist scan
lo        Interface doesn't support scanning.

wlan0     No scan results

eth0      Interface doesn't support scanning.

lsb_release -d
Description:    Ubuntu 12.04.1 LTS

uname -mr
3.2.0-32-generic x86_64

sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...

---

### Post by chili555 on 2012-10-28
>  29.194808] wlan0: authenticate with a0:21:b7:a0:65:e2 (try 1)
[ 29.196158] wlan0: authenticated
[ 29.218858] wlan0: associate with a0:21:b7:a0:65:e2 (try 1)
[ 29.223384] wlan0: RX AssocResp from a0:21:b7:a0:65:e2 (capab=0x431 status=0 aid=3)
[ 29.223392] wlan0: associated
[ 29.235560] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 39.518889] wlan0: no IPv6 routers present
[ 53.649639] [COLOR="Red"]ieee80211 phy0: wlan0: No probe response from AP a0:21:b7:a0:65:e2 after 500ms, disconnecting.[/COLOR]
[ 69.297031] ADDRCONF(NETDEV_UP): wlan0: link is not readyIt looks like it worked great until it dropped. You might check here and try the fix in post #5: [http://ubuntuforums.org/showthread.php?t=1867114](http://ubuntuforums.org/showthread.php?t=1867114)

---

### Post by luben on 2012-10-29
Tried, but didn't work. There was not such file /etc/modprobe.d/mac80211.conf
so I created it with the line "options mac80211 probe_wait_ms=1000" only.

This is what I got:

 ~$dmesg | grep wlan
[   16.688378] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.689044] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.318920] wlan0: authenticate with a0:21:b7:a0:65:e2 (try 1)
[   23.320353] wlan0: authenticated
[   23.342793] wlan0: associate with a0:21:b7:a0:65:e2 (try 1)
[   23.346514] wlan0: RX AssocResp from a0:21:b7:a0:65:e2 (capab=0x431 status=0 aid=1)
[   23.346518] wlan0: associated
[   23.355281] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   33.738176] wlan0: no IPv6 routers present
[   49.937076] ieee80211 phy0: wlan0: No probe response from AP a0:21:b7:a0:65:e2 after 1000ms, disconnecting.
[   65.326650] ADDRCONF(NETDEV_UP): wlan0: link is not ready

Even when it was saying "connected" I couldn't really get on the Internet.

---

### Post by chili555 on 2012-10-29
Would you please change the file to:```
options mac80211  max_nullfunc_tries=60 max_probe_tries=60 probe_wait_ms=3600000
```Reboot and let us hear your report.

---

### Post by luben on 2012-10-30
Tried and for 1 minute it was working fine. But then it started saying "not able to connect" and I could not get to the web page anymore. Now it stays connected to my wireless network but can't browse the Internet. Here's the report:

 dmesg | grep wlan
[   21.166431] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.167353] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.769061] wlan0: authenticate with a0:21:b7:a0:65:e2 (try 1)
[   27.770491] wlan0: authenticated
[   27.793035] wlan0: associate with a0:21:b7:a0:65:e2 (try 1)
[   27.796766] wlan0: RX AssocResp from a0:21:b7:a0:65:e2 (capab=0x431 status=0 aid=1)
[   27.796769] wlan0: associated
[   27.809534] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   38.758150] wlan0: no IPv6 routers present

---

### Post by chili555 on 2012-10-30
> Now it stays connected to my wireless network but can't browse the Internet. We are making some slow progress. Let's see what DNS nameservers got assigned:```
nm-tool
```

---

### Post by luben on 2012-10-30
Here it is:

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        E4:11:5B:55:72:C9

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [homewifi] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             connected
  Default:           yes
  HW Address:        44:6D:57:5A:AF:F7

  Capabilities:
    Speed:           6 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *homewifi:         Infra, A0:21:B7:A0:65:E2, Freq 2427 MHz, Rate 54 Mb/s, Strength 91 WPA2
    SIM-MP:          Infra, 00:14:D1:21:FA:D8, Freq 2437 MHz, Rate 54 Mb/s, Strength 65 WPA2
    J&M:             Infra, A0:21:B7:99:32:E4, Freq 2417 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    2WIRE676:        Infra, 98:2C:BE:03:47:99, Freq 2447 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2
    HOME-1FF2:       Infra, 00:1D:D4:01:1F:F0, Freq 2437 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2
    S&M:             Infra, 64:0F:29:0E:E4:21, Freq 2422 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    2WIRE209:        Infra, 3C:EA:4F:7D:AC:C9, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    Get Lost:        Infra, 00:18:E7:D4:72:93, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA
    2WIRE923:        Infra, 00:21:7C:44:DD:21, Freq 2447 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    urworkingit:     Infra, A0:21:B7:A4:F4:A2, Freq 2422 MHz, Rate 54 Mb/s, Strength 19 WPA2
    2WIRE584:        Infra, 00:21:7C:4A:89:01, Freq 2447 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    WiFiRSU_16:      Infra, AC:81:12:1D:05:16, Freq 2452 MHz, Rate 54 Mb/s, Strength 12 WPA2
    EmeraldDove:     Infra, 58:6D:8F:CE:82:01, Freq 2437 MHz, Rate 54 Mb/s, Strength 12 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.175
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

---

### Post by chili555 on 2012-10-30
> IPv4 Settings:
Address: 192.168.1.175
Prefix: 24 (255.255.255.0)
Gateway: 192.168.1.1

DNS: 192.168.1.1Looks normal enough. Let's see:```
cat /etc/resolv.conf
ping -c3 8.8.8.8
ping -c3 www.google.com
```I even like this!> *homewifi: Infra, A0:21:B7:A0:65:E2, Freq 2427 MHz, Rate 54 Mb/s, Strength [COLOR="Red"]91[/COLOR] [COLOR="Red"]WPA2[/COLOR]

---

### Post by luben on 2012-10-31
~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1

~$ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
From 192.168.1.175 icmp_seq=1 Destination Host Unreachable
From 192.168.1.175 icmp_seq=2 Destination Host Unreachable
From 192.168.1.175 icmp_seq=3 Destination Host Unreachable

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2014ms
pipe 3

~$ ping -c3 [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)

---

### Post by chili555 on 2012-11-01
Weird. I wonder if this isn't a combo wifi and bluetooth device. If so, I wonder if bluetooth isn't interfering. I looked at the driver parameters for your driver rt2800pci and its dependencies and can't see any way to test my suspicion.

I wonder if there isn't another, better driver available. Let's see:```
lspci -nn | grep 0280
```You might see if there is a setting in System Settings > Bluetooth to turn it off. If so, does it change your connectivity at all?

---

### Post by luben on 2012-11-01
I turned the bluetooth off but apparently nothing changed. Here's the response:
 
~$ lspci -nn | grep 0280
25:00.0 Network controller [0280]: Ralink corp. Device [1814:3592]

---

### Post by chili555 on 2012-11-02
Let's try another driver parameter:```
sudo modprobe -r rt2800pci
sudo modprobe rt2800pci nohwcrypt=Y
```Is there any improvement?

---

### Post by luben on 2012-11-02
There's kind of progress. The first command makes me loose the connection. Then I type the second command and when I get connected again I can access the first web site. But then if I try change page I get 'Server not found'. So, I go again with the first command and I loose connection. Then the second and when I get connected again I push 'try again' and I connect to the page. But then again I can't change page. I hope I manage to explain.

---

### Post by chili555 on 2012-11-02
> **luben said:**
> There's kind of progress. The first command makes me loose the connection. Then I type the second command and when I get connected again I can access the first web site. But then if I try change page I get 'Server not found'. So, I go again with the first command and I loose connection. Then the second and when I get connected again I push 'try again' and I connect to the page. But then again I can't change page. I hope I manage to explain.Yes, perfectly. We are going try a hopefully better driver. I will write out the procedure tomorrow after a needed nights sleep. See you then.

---

### Post by chili555 on 2012-11-03
We are going to try the compat-wireless package. Please open a terminal and do:```
sudo apt-get install linux-headers-generic build-essential
wget http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.2/compat-wireless-3.2.5-1.tar.bz2
tar -xf compat-wireless-3.2.5-1.tar.bz2
cd compat-wireless-3.2.5-1
./scripts/driver-select rt2x00
make
sudo make install
sudo modprobe -rf rt2800pci
sudo rm /etc/modprobe.d/mac80211.conf
sudo modprobe rt2800pci
```It may take a bit of fiddling with the driver; unloading and reloading, to get the packages downloaded.

If there is an error at 'make,' stop and ask.

I look forward to a good report!

---

### Post by luben on 2012-11-03
At the make command I got a bunch of lines and then 

cc1: some warnings being treated as errors
make[3]: *** [/home/luben/compat-wireless-3.2.5-1/net/wireless/util.o] Error 1
make[2]: *** [/home/luben/compat-wireless-3.2.5-1/net/wireless] Error 2
make[1]: *** [_module_/home/luben/compat-wireless-3.2.5-1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-32-generic'
make: *** [modules] Error 2

What do I have to do?

---

### Post by chili555 on 2012-11-03
In order to tell what to do, I have to see more of the error messages. Do you have build-essential installed correctly?```
sudo dpkg -s build-essential | head -n3
```It ought to return:> Package: build-essential
Status: install ok installed
Priority: optional

---

### Post by luben on 2012-11-03
Sorry, this is the whole message I got:

~/compat-wireless-3.2.5-1$ make
./scripts/gen-compat-autoconf.sh config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/3.2.0-32-generic/build M=/home/luben/compat-wireless-3.2.5-1 modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-32-generic'
  LD      /home/luben/compat-wireless-3.2.5-1/compat/built-in.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/compat/main.o
  LD [M]  /home/luben/compat-wireless-3.2.5-1/compat/compat.o
  LD      /home/luben/compat-wireless-3.2.5-1/drivers/misc/eeprom/built-in.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/drivers/misc/eeprom/eeprom_93cx6.o
  LD      /home/luben/compat-wireless-3.2.5-1/drivers/net/wireless/built-in.o
  LD      /home/luben/compat-wireless-3.2.5-1/drivers/net/wireless/rt2x00/built-in.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/drivers/net/wireless/rt2x00/rt2x00dev.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/drivers/net/wireless/rt2x00/rt2x00mac.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/drivers/net/wireless/rt2x00/rt2x00config.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/drivers/net/wireless/rt2x00/rt2x00queue.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/drivers/net/wireless/rt2x00/rt2x00link.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/drivers/net/wireless/rt2x00/rt2x00crypto.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/drivers/net/wireless/rt2x00/rt2x00firmware.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/drivers/net/wireless/rt2x00/rt2x00leds.o
  LD [M]  /home/luben/compat-wireless-3.2.5-1/drivers/net/wireless/rt2x00/rt2x00lib.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/drivers/net/wireless/rt2x00/rt2x00pci.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/drivers/net/wireless/rt2x00/rt2x00usb.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/drivers/net/wireless/rt2x00/rt2800lib.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/drivers/net/wireless/rt2x00/rt2400pci.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/drivers/net/wireless/rt2x00/rt2500pci.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/drivers/net/wireless/rt2x00/rt61pci.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/drivers/net/wireless/rt2x00/rt2800pci.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/drivers/net/wireless/rt2x00/rt2500usb.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/drivers/net/wireless/rt2x00/rt73usb.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/drivers/net/wireless/rt2x00/rt2800usb.o
  LD      /home/luben/compat-wireless-3.2.5-1/net/mac80211/built-in.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/main.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/status.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/sta_info.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/wep.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/wpa.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/scan.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/offchannel.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/ht.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/agg-tx.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/agg-rx.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/ibss.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/mlme.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/work.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/iface.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/rate.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/michael.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/tkip.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/aes_ccm.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/aes_cmac.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/cfg.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/rx.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/spectmgmt.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/tx.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/key.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/util.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/wme.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/event.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/chan.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/led.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/debugfs.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/debugfs_sta.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/debugfs_netdev.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/debugfs_key.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/mesh.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/mesh_pathtbl.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/mesh_plink.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/mesh_hwmp.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/pm.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/driver-trace.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/rc80211_pid_algo.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/rc80211_pid_debugfs.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/rc80211_minstrel.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/rc80211_minstrel_debugfs.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/rc80211_minstrel_ht.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/rc80211_minstrel_ht_debugfs.o
  LD [M]  /home/luben/compat-wireless-3.2.5-1/net/mac80211/mac80211.o
  LD      /home/luben/compat-wireless-3.2.5-1/net/rfkill/built-in.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/rfkill/rfkill-regulator.o
  LD      /home/luben/compat-wireless-3.2.5-1/net/wireless/built-in.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/wireless/core.o
/home/luben/compat-wireless-3.2.5-1/net/wireless/core.c:7:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
/home/luben/compat-wireless-3.2.5-1/net/wireless/core.c:7:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/wireless/sysfs.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/wireless/radiotap.o
  CC [M]  /home/luben/compat-wireless-3.2.5-1/net/wireless/util.o
/home/luben/compat-wireless-3.2.5-1/net/wireless/util.c: In function ‘cfg80211_change_iface’:
/home/luben/compat-wireless-3.2.5-1/net/wireless/util.c:810:2: error: implicit declaration of function ‘br_port_exists’ [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
make[3]: *** [/home/luben/compat-wireless-3.2.5-1/net/wireless/util.o] Error 1
make[2]: *** [/home/luben/compat-wireless-3.2.5-1/net/wireless] Error 2
make[1]: *** [_module_/home/luben/compat-wireless-3.2.5-1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-32-generic'
make: *** [modules] Error 2

And then:

~/compat-wireless-3.2.5-1$ sudo dpkg -s build-essential | head -n3
[sudo] password for luben: 
Package: build-essential
Status: install ok installed
Priority: optional

---

### Post by chili555 on 2012-11-03
> util.c:810:2: error: implicit declaration of function ‘br_port_exists’ [-Werror=implicit-function-declaration]That usually means a mis-match between the package you are trying to compile and your kernel; in this case, 3.2.0-32-generic.

I am at a disadvantage because I no longer have a 12.04 install in my herd of Ubuntu computers. Usually, I compile first and recommend second. I suggest you delete compat-wireless-3.2.5-1 and try this:

[http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.2/compat-wireless-3.2-1.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.2/compat-wireless-3.2-1.tar.bz2)

---

### Post by luben on 2012-11-03
I got again an error:

~/compat-wireless-3.2-1$ make
./scripts/gen-compat-autoconf.sh config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/3.2.0-32-generic/build M=/home/luben/compat-wireless-3.2-1 modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-32-generic'
  LD      /home/luben/compat-wireless-3.2-1/compat/built-in.o
  CC [M]  /home/luben/compat-wireless-3.2-1/compat/main.o
In file included from /home/luben/compat-wireless-3.2-1/include/linux/compat-2.6.29.h:5:0,
                 from /home/luben/compat-wireless-3.2-1/include/linux/compat-2.6.h:24,
                 from <command-line>:0:
include/linux/netdevice.h:1150:5: warning: "IS_ENABLED" is not defined [-Wundef]
include/linux/netdevice.h:1150:15: error: missing binary operator before token "("
include/linux/netdevice.h: In function ‘netdev_uses_dsa_tags’:
include/linux/netdevice.h:1418:9: error: ‘struct net_device’ has no member named ‘dsa_ptr’
include/linux/netdevice.h:1419:31: error: ‘struct net_device’ has no member named ‘dsa_ptr’
include/linux/netdevice.h: In function ‘netdev_uses_trailer_tags’:
include/linux/netdevice.h:1428:9: error: ‘struct net_device’ has no member named ‘dsa_ptr’
include/linux/netdevice.h:1429:35: error: ‘struct net_device’ has no member named ‘dsa_ptr’
make[3]: *** [/home/luben/compat-wireless-3.2-1/compat/main.o] Error 1
make[2]: *** [/home/luben/compat-wireless-3.2-1/compat] Error 2
make[1]: *** [_module_/home/luben/compat-wireless-3.2-1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-32-generic'
make: *** [modules] Error 2

---

### Post by chili555 on 2012-11-04
Greater love for the forum hath no Chili than he dig out a USB drive and actually install 12.04 LTS so he can properly compile compat-wireless! 

Try this one. It compiles with one hopefully minor warning and no errors.

[http://www.orbit-lab.org/kernel/compat-wireless/2012/10/compat-wireless-2012-10-30.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless/2012/10/compat-wireless-2012-10-30.tar.bz2)

---

### Post by ORF1000 on 2012-11-04
Chili, is there any chance that you (or someone) could come over to either [this thread]("http://ubuntuforums.org/showthread.php?t=2073380") or [this thread]("http://ubuntuforums.org/showthread.php?p=12327654") to give us a hand?  This is a problem with wired networks that has appeared with 12.10.

---

### Post by chili555 on 2012-11-04
> **ORF1000 said:**
> Chili, is there any chance that you (or someone) could come over to either [this thread]("http://ubuntuforums.org/showthread.php?t=2073380") or [this thread]("http://ubuntuforums.org/showthread.php?p=12327654") to give us a hand?  This is a problem with wired networks that has appeared with 12.10.Done.

---

### Post by luben on 2012-11-04
I tried the package compat-wireless-2012-10-30.tar.bz2
It compiled with 2 warnings, I think, and 2 notes but no errors.
I rebooted and now my laptop doesn't even detect any wireless network at home (there used to be tens). Fortunately the wired keep working well.

---

### Post by chili555 on 2012-11-04
Are there any useful clues when you run:```
sudo modprobe rt2800pci
dmesg | grep rt2
```

---

### Post by luben on 2012-11-04
~$ sudo modprobe rt2800pci
[sudo] password for luben: 

~$ dmesg | grep rt2
[   16.482382] Modules linked in: rt2800lib(O) crc_ccitt rt2x00pci(O) rt2x00lib(O) snd_hda_codec_hdmi snd_hda_codec_idt mac80211(O) i915(O+) cfg80211(O) drm_kms_helper(O) joydev hp_wmi sparse_keymap drm(O) snd_hda_intel snd_hda_codec snd_hwdep snd_pcm eeprom_93cx6(O) snd_seq_midi snd_rawmidi snd_seq_midi_event psmouse uvcvideo videodev v4l2_compat_ioctl32 serio_raw fglrx(P) snd_seq snd_timer compat(O) snd_seq_device jmb38x_ms memstick snd soundcore snd_page_alloc mei(C) video mac_hid wmi hp_accel lis3lv02d input_polldev lp parport r8169 sdhci_pci sdhci
[   16.484454] rt2800pci 0000:25:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   16.484466] rt2800pci 0000:25:00.0: setting latency timer to 64
[   16.486413] phy0 -> rt2x00lib_probe_dev: Error - Failed to initialize hw.
[   16.486447] rt2800pci 0000:25:00.0: PCI INT A disabled
[   16.486453] rt2800pci: probe of 0000:25:00.0 failed with error -22

---

### Post by chili555 on 2012-11-04
> [ 16.486413] phy0 -> rt2x00lib_probe_dev: Error - Failed to initialize hw.
[ 16.486447] rt2800pci 0000:25:00.0: PCI INT A disabled
[ [COLOR="Red"]16.486453[/COLOR]] rt2800pci: probe of 0000:25:00.0 failed with error -22This all happened while booting. Are there any newer messages if you do:```
sudo modprobe -r rt2800pci
sudo modprobe rt2800pci
dmesg | grep -e rt2 -e 80211
```I am wondering, no, hoping this may be a one-time anomaly.

---

### Post by luben on 2012-11-04
~$ sudo modprobe -r rt2800pci
[sudo] password for luben: 
~$ sudo modprobe rt2800pci
~$ dmesg | grep -e rt2 -e 80211
[   16.102009] cfg80211: Calling CRDA to update world regulatory domain
[   16.105246] cfg80211: World regulatory domain updated:
[   16.105248] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   16.105250] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.105252] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.105254] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.105255] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.105257] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.482382] Modules linked in: rt2800lib(O) crc_ccitt rt2x00pci(O) rt2x00lib(O) snd_hda_codec_hdmi snd_hda_codec_idt mac80211(O) i915(O+) cfg80211(O) drm_kms_helper(O) joydev hp_wmi sparse_keymap drm(O) snd_hda_intel snd_hda_codec snd_hwdep snd_pcm eeprom_93cx6(O) snd_seq_midi snd_rawmidi snd_seq_midi_event psmouse uvcvideo videodev v4l2_compat_ioctl32 serio_raw fglrx(P) snd_seq snd_timer compat(O) snd_seq_device jmb38x_ms memstick snd soundcore snd_page_alloc mei(C) video mac_hid wmi hp_accel lis3lv02d input_polldev lp parport r8169 sdhci_pci sdhci
[   16.484454] rt2800pci 0000:25:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   16.484466] rt2800pci 0000:25:00.0: setting latency timer to 64
[   16.486413] phy0 -> rt2x00lib_probe_dev: Error - Failed to initialize hw.
[   16.486447] rt2800pci 0000:25:00.0: PCI INT A disabled
[   16.486453] rt2800pci: probe of 0000:25:00.0 failed with error -22
[ 2603.831059] cfg80211: Calling CRDA to update world regulatory domain
[ 2603.836498] cfg80211: World regulatory domain updated:
[ 2603.836501] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2603.836504] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2603.836507] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2603.836509] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2603.836512] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2603.836515] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2603.837905] rt2800pci 0000:25:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 2603.837917] rt2800pci 0000:25:00.0: setting latency timer to 64
[ 2603.839852] phy0 -> rt2x00lib_probe_dev: Error - Failed to initialize hw.
[ 2603.839877] rt2800pci 0000:25:00.0: PCI INT A disabled
[ 2603.839882] rt2800pci: probe of 0000:25:00.0 failed with error -22

---

### Post by luben on 2012-11-04
I rebooted different times, but my laptop can't detect any wireless network anymore and I always get this:

~$ sudo modprobe -r rt2800pci
[sudo] password for luben: 
~$ sudo modprobe rt2800pci
~$ dmesg | grep -e rt2 -e 80211
[   10.654724] cfg80211: Calling CRDA to update world regulatory domain
[   10.664799] Modules linked in: mac_hid(+) snd_seq(+) mac80211(O) jmb38x_ms memstick snd_timer snd_seq_device cfg80211(O) i915(O+) mei(C) eeprom_93cx6(O) drm_kms_helper(O) snd soundcore snd_page_alloc drm(O) compat(O) video lp parport sdhci_pci sdhci r8169
[   10.667111] rt2800pci 0000:25:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   10.667122] rt2800pci 0000:25:00.0: setting latency timer to 64
[   10.669382] phy0 -> rt2x00lib_probe_dev: Error - Failed to initialize hw.
[   10.669423] rt2800pci 0000:25:00.0: PCI INT A disabled
[   10.669434] rt2800pci: probe of 0000:25:00.0 failed with error -22
[   10.809890] cfg80211: World regulatory domain updated:
[   10.809893] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.809896] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.809898] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.809901] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.809903] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.809905] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  318.448514] cfg80211: Calling CRDA to update world regulatory domain
[  318.452215] cfg80211: World regulatory domain updated:
[  318.452219] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  318.452222] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  318.452224] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  318.452227] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  318.452229] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  318.452231] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  318.454719] rt2800pci 0000:25:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[  318.454732] rt2800pci 0000:25:00.0: setting latency timer to 64
[  318.456679] phy0 -> rt2x00lib_probe_dev: Error - Failed to initialize hw.
[  318.456708] rt2800pci 0000:25:00.0: PCI INT A disabled

---

### Post by chili555 on 2012-11-04
I fired up my USB 12.04 install and fiddled with this for an hour. It's a mess and I can't get it to work right either and I don't even have the device! We have no reasonable alternative except to remove compat-wireless and take another swing at trouble-shooting.```
cd Desktop/compat-wireless-2012-10-30  [COLOR="Red"]<--or wherever you extracted it[/COLOR]
sudo make install
```Reboot and let us see:```
dmesg | grep -e rt2 -e 80211
```**Sigh**

---

### Post by luben on 2012-11-05
I typed those commands and rebooted but still I can't detect wireless. Here's the report:

~$ dmesg | grep -e rt2 -e 80211
[   10.346112] cfg80211: Calling CRDA to update world regulatory domain
[   10.348943] Modules linked in: i915(O+) memstick(+) cfg80211(O+) snd drm_kms_helper(O) drm(O) video mei(C) soundcore snd_page_alloc lp compat(O) eeprom_93cx6(O) parport r8169 sdhci_pci sdhci
[   10.359776] rt2800pci 0000:25:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   10.359787] rt2800pci 0000:25:00.0: setting latency timer to 64
[   10.362684] phy0 -> rt2x00lib_probe_dev: Error - Failed to initialize hw.
[   10.362727] rt2800pci 0000:25:00.0: PCI INT A disabled
[   10.362735] rt2800pci: probe of 0000:25:00.0 failed with error -22
[   10.517665] cfg80211: World regulatory domain updated:
[   10.517667] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.517669] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.517671] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.517673] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.517674] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.517676] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

---

### Post by chili555 on 2012-11-06
I apologize. I am deeply sorry I made a mistake. I meant to say:```
cd Desktop/compat-wireless-2012-10-30  [COLOR="Red"]<--or wherever you extracted it[/COLOR]
sudo make [COLOR="Red"]**un**[/COLOR]install
```I'm very sorry. Please do so, reboot and let us see:```
dmesg | grep -e rt2 -e 80211
```I hope we are *NOT* going to see this any longer:> [ 10.362684] phy0 -> rt2x00lib_probe_dev: [COLOR="Red"]Error - Failed to initialize hw.[/COLOR]
[ 10.362727] rt2800pci 0000:25:00.0: PCI INT A disabled
[ 10.362735] rt2800pci: probe of 0000:25:00.0 failed with error -22

---

### Post by luben on 2012-11-06
You don't have to apologize, I should have understand that it was uninstall instead of install. Unfortunately I'm a very beginner and I need all the commands to be spelled out exactly for the moment. Anyway, this is the long report:
:~$ dmesg | grep -e rt2 -e 80211
[   10.061236] cfg80211: Calling CRDA to update world regulatory domain
[   10.126720] cfg80211: World regulatory domain updated:
[   10.126723] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.126726] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.126729] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.126732] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.126734] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.126737] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.492020] rt2800pci 0000:25:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   10.492030] rt2800pci 0000:25:00.0: setting latency timer to 64
[   10.494000] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   10.494003] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.494005] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   10.494007] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.494008] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   10.494010] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.494011] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   10.494013] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.494015] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   10.494016] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.494018] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   10.494020] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.494021] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   10.494023] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.494024] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   10.494026] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.494027] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   10.494029] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.494031] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   10.494032] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.494034] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   10.494036] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.494037] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   10.494039] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.494040] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   10.494042] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.494044] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   10.494045] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.494047] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[   10.494049] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.494050] cfg80211: Updating information on frequency 5190 MHz for a 20 MHz width channel with regulatory rule:
[   10.494052] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.494054] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[   10.494055] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.494057] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[   10.494059] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.494060] cfg80211: Updating information on frequency 5230 MHz for a 20 MHz width channel with regulatory rule:
[   10.494062] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.494063] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[   10.494065] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.494066] cfg80211: Disabling freq 5260 MHz
[   10.494068] cfg80211: Disabling freq 5270 MHz
[   10.494069] cfg80211: Disabling freq 5280 MHz
[   10.494070] cfg80211: Disabling freq 5300 MHz
[   10.494071] cfg80211: Disabling freq 5310 MHz
[   10.494072] cfg80211: Disabling freq 5320 MHz
[   10.494073] cfg80211: Disabling freq 5500 MHz
[   10.494074] cfg80211: Disabling freq 5510 MHz
[   10.494074] cfg80211: Disabling freq 5520 MHz
[   10.494075] cfg80211: Disabling freq 5540 MHz
[   10.494077] cfg80211: Disabling freq 5550 MHz
[   10.494078] cfg80211: Disabling freq 5560 MHz
[   10.494079] cfg80211: Disabling freq 5580 MHz
[   10.494079] cfg80211: Disabling freq 5590 MHz
[   10.494080] cfg80211: Disabling freq 5600 MHz
[   10.494081] cfg80211: Disabling freq 5620 MHz
[   10.494082] cfg80211: Disabling freq 5630 MHz
[   10.494083] cfg80211: Disabling freq 5640 MHz
[   10.494084] cfg80211: Disabling freq 5660 MHz
[   10.494085] cfg80211: Disabling freq 5670 MHz
[   10.494086] cfg80211: Disabling freq 5680 MHz
[   10.494087] cfg80211: Disabling freq 5700 MHz
[   10.494089] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[   10.494090] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.494092] cfg80211: Updating information on frequency 5755 MHz for a 20 MHz width channel with regulatory rule:
[   10.494094] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.494095] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[   10.494097] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.494098] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[   10.494100] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.494102] cfg80211: Updating information on frequency 5795 MHz for a 20 MHz width channel with regulatory rule:
[   10.494103] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.494105] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[   10.494107] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.494108] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[   10.494110] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.494111] cfg80211: Disabling freq 5835 MHz
[   10.494112] cfg80211: Disabling freq 5845 MHz
[   10.494113] cfg80211: Disabling freq 5855 MHz
[   10.494114] cfg80211: Disabling freq 5865 MHz
[   10.587663] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   10.588004] Registered led device: rt2800pci-phy0::radio
[   10.588027] Registered led device: rt2800pci-phy0::assoc
[   10.588046] Registered led device: rt2800pci-phy0::quality
[   11.194858] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
[   17.958536] cfg80211: Calling CRDA for country: US
[   17.960955] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   17.960958] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   17.960959] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   17.960961] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   17.960963] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   17.960964] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   17.960966] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   17.960967] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   17.960969] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   17.960971] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   17.960972] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   17.960974] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   17.960975] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   17.960977] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   17.960978] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   17.960980] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   17.960981] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   17.960983] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   17.960984] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   17.960986] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   17.960987] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   17.960989] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   17.960990] cfg80211: Disabling freq 2467 MHz
[   17.960991] cfg80211: Disabling freq 2472 MHz
[   17.960992] cfg80211: Disabling freq 2484 MHz
[   17.960993] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[   17.960995] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   17.960996] cfg80211: Updating information on frequency 5190 MHz for a 20 MHz width channel with regulatory rule:
[   17.960998] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   17.960999] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[   17.961001] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   17.961002] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[   17.961004] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   17.961005] cfg80211: Updating information on frequency 5230 MHz for a 20 MHz width channel with regulatory rule:
[   17.961007] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   17.961008] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[   17.961010] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   17.961011] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule:
[   17.961013] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.961014] cfg80211: Updating information on frequency 5270 MHz for a 20 MHz width channel with regulatory rule:
[   17.961016] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.961017] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule:
[   17.961019] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.961020] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule:
[   17.961022] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.961024] cfg80211: Updating information on frequency 5310 MHz for a 20 MHz width channel with regulatory rule:
[   17.961025] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.961027] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule:
[   17.961028] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.961030] cfg80211: Updating information on frequency 5500 MHz for a 20 MHz width channel with regulatory rule:
[   17.961031] cfg80211: 5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.961033] cfg80211: Updating information on frequency 5510 MHz for a 20 MHz width channel with regulatory rule:
[   17.961034] cfg80211: 5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.961036] cfg80211: Updating information on frequency 5520 MHz for a 20 MHz width channel with regulatory rule:
[   17.961037] cfg80211: 5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.961039] cfg80211: Updating information on frequency 5540 MHz for a 20 MHz width channel with regulatory rule:
[   17.961041] cfg80211: 5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.961042] cfg80211: Updating information on frequency 5550 MHz for a 20 MHz width channel with regulatory rule:
[   17.961044] cfg80211: 5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.961045] cfg80211: Updating information on frequency 5560 MHz for a 20 MHz width channel with regulatory rule:
[   17.961047] cfg80211: 5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.961048] cfg80211: Updating information on frequency 5580 MHz for a 20 MHz width channel with regulatory rule:
[   17.961050] cfg80211: 5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.961051] cfg80211: Updating information on frequency 5590 MHz for a 20 MHz width channel with regulatory rule:
[   17.961053] cfg80211: 5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.961054] cfg80211: Disabling freq 5600 MHz
[   17.961055] cfg80211: Disabling freq 5620 MHz
[   17.961056] cfg80211: Disabling freq 5630 MHz
[   17.961057] cfg80211: Disabling freq 5640 MHz
[   17.961058] cfg80211: Updating information on frequency 5660 MHz for a 20 MHz width channel with regulatory rule:
[   17.961059] cfg80211: 5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.961061] cfg80211: Updating information on frequency 5670 MHz for a 20 MHz width channel with regulatory rule:
[   17.961062] cfg80211: 5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.961064] cfg80211: Updating information on frequency 5680 MHz for a 20 MHz width channel with regulatory rule:
[   17.961065] cfg80211: 5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.961067] cfg80211: Updating information on frequency 5700 MHz for a 20 MHz width channel with regulatory rule:
[   17.961068] cfg80211: 5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.961070] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[   17.961072] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   17.961073] cfg80211: Updating information on frequency 5755 MHz for a 20 MHz width channel with regulatory rule:
[   17.961075] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   17.961076] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[   17.961078] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   17.961079] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[   17.961081] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   17.961082] cfg80211: Updating information on frequency 5795 MHz for a 20 MHz width channel with regulatory rule:
[   17.961084] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   17.961085] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[   17.961087] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   17.961088] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[   17.961090] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   17.961091] cfg80211: Disabling freq 5835 MHz
[   17.961092] cfg80211: Disabling freq 5845 MHz
[   17.961093] cfg80211: Disabling freq 5855 MHz
[   17.961094] cfg80211: Disabling freq 5865 MHz
[   17.961098] cfg80211: Regulatory domain changed to country: US
[   17.961099] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.961101] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   17.961102] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   17.961104] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.961105] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.961107] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.961108] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   42.678456] ieee80211 phy0: wlan0: No probe response from AP a0:21:b7:a0:65:e2 after 500ms, disconnecting.
[   42.850453] cfg80211: All devices are disconnected, going to restore regulatory settings
[   42.850467] cfg80211: Restoring regulatory settings
[   42.850470] cfg80211: Calling CRDA to update world regulatory domain
[   42.852857] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   42.852860] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.852862] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   42.852864] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.852865] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   42.852867] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.852868] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   42.852870] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.852872] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   42.852873] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.852875] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   42.852877] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.852878] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   42.852880] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.852881] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   42.852883] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.852885] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   42.852886] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.852888] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   42.852890] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.852891] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   42.852893] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.852895] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   42.852896] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   42.852898] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   42.852900] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   42.852901] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   42.852903] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   42.852904] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[   42.852906] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.852908] cfg80211: Updating information on frequency 5190 MHz for a 20 MHz width channel with regulatory rule:
[   42.852910] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.852911] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[   42.852913] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.852914] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[   42.852916] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.852918] cfg80211: Updating information on frequency 5230 MHz for a 20 MHz width channel with regulatory rule:
[   42.852919] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.852921] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[   42.852923] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.852924] cfg80211: Disabling freq 5260 MHz
[   42.852925] cfg80211: Disabling freq 5270 MHz
[   42.852926] cfg80211: Disabling freq 5280 MHz
[   42.852927] cfg80211: Disabling freq 5300 MHz
[   42.852928] cfg80211: Disabling freq 5310 MHz
[   42.852929] cfg80211: Disabling freq 5320 MHz
[   42.852930] cfg80211: Disabling freq 5500 MHz
[   42.852931] cfg80211: Disabling freq 5510 MHz
[   42.852932] cfg80211: Disabling freq 5520 MHz
[   42.852933] cfg80211: Disabling freq 5540 MHz
[   42.852934] cfg80211: Disabling freq 5550 MHz
[   42.852935] cfg80211: Disabling freq 5560 MHz
[   42.852936] cfg80211: Disabling freq 5580 MHz
[   42.852937] cfg80211: Disabling freq 5590 MHz
[   42.852938] cfg80211: Disabling freq 5600 MHz
[   42.852939] cfg80211: Disabling freq 5620 MHz
[   42.852940] cfg80211: Disabling freq 5630 MHz
[   42.852941] cfg80211: Disabling freq 5640 MHz
[   42.852942] cfg80211: Disabling freq 5660 MHz
[   42.852943] cfg80211: Disabling freq 5670 MHz
[   42.852944] cfg80211: Disabling freq 5680 MHz
[   42.852945] cfg80211: Disabling freq 5700 MHz
[   42.852946] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[   42.852949] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.852950] cfg80211: Updating information on frequency 5755 MHz for a 20 MHz width channel with regulatory rule:
[   42.852952] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.852954] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[   42.852957] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.852959] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[   42.852961] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.852963] cfg80211: Updating information on frequency 5795 MHz for a 20 MHz width channel with regulatory rule:
[   42.852965] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.852967] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[   42.852969] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.852971] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[   42.852974] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.852976] cfg80211: Disabling freq 5835 MHz
[   42.852977] cfg80211: Disabling freq 5845 MHz
[   42.852978] cfg80211: Disabling freq 5855 MHz
[   42.852980] cfg80211: Disabling freq 5865 MHz
[   42.852984] cfg80211: World regulatory domain updated:
[   42.852985] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   42.852988] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.852990] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   42.852993] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   42.852995] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.852998] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

---

### Post by luben on 2012-11-07
Ok, now I'm kind of back to the initial point: I can detect wireless networks but I can't connect to the network.

---

### Post by chili555 on 2012-11-07
> [ 11.194858] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardwareI'm fairly confident this is a part of the problem but I have no further suggestions.

---

### Post by luben on 2012-11-24
Hello,

I finally managed to solve my problem. Here's how I did it.
After digging for a while on the Internet I found this post here:
 [http://kerlubasola.iteye.com/blog/1579653](http://kerlubasola.iteye.com/blog/1579653)
where this guy had the same problem. I did what he suggests, went on the ralink website and downloaded the package 
RT3062PCI/mPCI/CB/PCIe(RT3060/RT3062/RT3562/RT3592) 
from here: 
[http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)
 After you untar the package you can find the instructions inside the unpacked directory, but I just followed the instructions of the guy (there are some space that you have to delete in the commands he listed, but even I could understand which spaces I had to cancel).
In the end it was a problem of driver and ralink itself gave the solution.
The only con is that to download the package you have to give them your email address (or one of your addresses).

Ok, that's it. Many thanks to chili555 for the help.

---

