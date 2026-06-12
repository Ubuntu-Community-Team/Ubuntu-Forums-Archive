---
title: "Belkin N300 F7D2102 Wireless state disconnected"
date: 2012-09-04
forum: Networking &amp; Wireless
---

### Post by lillypad on 2012-09-04
Hello Ubuntu users. I have been trying to install this driver for the past 3 days and with no avail. 

lsusb gives:
```
Bus 001 Device 009: ID 050d:2103 Belkin Components F7D2102 802.11n N300 Micro Wireless Adapter v3000 [Realtek RTL8192CU]
```lsmod gives:
```
Module                  Size  Used by
arc4                   12529  2 
rtl8192cu             103297  0 
rtl8192c_common        75767  1 rtl8192cu
rtlwifi               111202  1 rtl8192cu
mac80211              506816  3 rtl8192cu,rtl8192c_common,rtlwifi
cfg80211              205544  2 rtlwifi,mac80211
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
snd_usb_audio         122982  3 
snd_hda_codec_realtek   224066  1 
snd_hda_intel          33773  3 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
snd_pcm                97188  3 snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
snd_usbmidi_lib        25395  1 snd_usb_audio
snd_seq_midi           13324  0 
snd_rawmidi            30748  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
adt7475                31231  0 
hwmon_vid              12827  1 adt7475
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
nouveau               774641  3 
ttm                    76949  1 nouveau
drm_kms_helper         46978  1 nouveau
joydev                 17693  0 
drm                   242038  5 nouveau,ttm,drm_kms_helper
usbhid                 47199  0 
i2c_algo_bit           13423  1 nouveau
mxm_wmi                12979  1 nouveau
hid                    99559  1 usbhid
edac_core              53746  0 
psmouse                87692  0 
snd                    78855  23 snd_usb_audio,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
k10temp                13166  0 
edac_mce_amd           23709  0 
video                  19596  1 nouveau
sp5100_tco             13791  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
soundcore              15091  1 snd
i2c_piix4              13301  0 
mac_hid                13253  0 
serio_raw              13211  0 
wmi                    19256  1 mxm_wmi
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usb_storage            49198  1 
r8169                  62099  0 
```ndiswrapper -l gives:
```
net8192cu : driver installed
    device (050D:2103) present (alternate driver: rtl8192cu)
```ifconfig gives:
```
wlan0     Link encap:Ethernet  HWaddr 08:86:3b:03:3c:a3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```iwconfig gives:
```
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
```nm-tool gives:
```

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             disconnected
  Default:           no
  HW Address:        08:86:3B:03:3C:A3

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    MOTOROLA-85C25:  Infra, 00:26:82:DC:EC:0F, Freq 2412 MHz, Rate 54 Mb/s, Strength 67 WPA2


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        1C:C1:DE:61:9A:09

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.42.0.81
    Prefix:          24 (255.255.255.0)
    Gateway:         10.42.0.1

    DNS:             10.42.0.1
```
sudo lshw -C network gives:

```
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 05
       serial: 1c:c1:de:61:9a:09
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=10.42.0.81 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:e800(size=256) memory:febff000-febfffff memory:faffc000-faffffff
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@1:2
       logical name: wlan0
       serial: 08:86:3b:03:3c:a3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.2.0-29-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bgn
```

My best guess is the problem arises from the network state being disconnected also there are many other networks that are not showing even though it says it supports the encryptions. Am I missing something here? Any help would be appreciated as I love to have ubuntu on my PC but if this wireless does not workout it's probably going back to windows :(

Thanks guys!!

---

### Post by chili555 on 2012-09-04
Well, the native driver rtl8192cu is loaded and not ndiswrapper. Let's see if we can troubleshoot the native driver first. Please run and post:```
dmesg | grep -i rtl
rfkill list all
```I notice that you have a wired ethernet connection active. Network Manager will disallow wireless if you have wired available. Throughout our troubleshooting, please detach the ethernet.

---

### Post by lillypad on 2012-09-04
dmesg | grep -i rtl gives:
```

[    2.427701] r8169 0000:02:00.0: eth0: RTL8168e/8111e at 0xffffc90000c74000, 1c:c1:de:61:9a:09, XID 0c200000 IRQ 42
[ 4065.271647] rtl8192cu: MAC address: 08:86:3b:03:3c:a3
[ 4065.271661] rtl8192cu: Board Type 0
[ 4065.285637] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[ 4065.292214] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[ 4065.293515] usbcore: registered new interface driver rtl8192cu
[ 4065.313611] rtl8192cu: MAC auto ON okay!
[ 4065.835657] rtl8192cu: Tx queue select: 0x05
[ 4065.842699] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cufw.bin
[ 7758.084243] rtlwifi: reg 0x102, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x40060103
[ 7758.084257] rtlwifi: reg 0x422, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x90e1317
[ 7758.084266] rtlwifi: reg 0x542, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x3903f2a
[ 7758.084277] rtlwifi: reg 0x608, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x3f3f3f3f
[ 7758.084299] rtlwifi: reg 0x102, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x3f3f3f3f
[ 7758.084307] rtlwifi: reg 0x422, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x3f3f3f27
[ 7758.084314] rtlwifi: reg 0x542, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x40370004
[ 7758.084325] rtlwifi: reg 0x824, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x40060100
[ 7758.087302] rtlwifi: reg 0x820, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x1000100
[ 7758.087309] rtlwifi: reg 0x8b8, usbctrl_vendorreq TimeOut! status:0xffffffed value=0xf0002a0e
[ 7758.087320] rtlwifi: reg 0x2, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x4d5
[ 7758.087327] rtlwifi: reg 0x2, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x3903f2a
[ 7758.087334] rtlwifi: reg 0x2, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x3f3f3f3f
[ 7758.087342] rtlwifi: reg 0x44, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x3f3f3f3f
[ 7758.087350] rtlwifi: reg 0x42, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x3f3f3f27
[ 7848.875273] rtl8192cu: MAC address: 08:86:3b:03:3c:a3
[ 7848.875286] rtl8192cu: Board Type 0
[ 7848.880039] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[ 7848.880572] ieee80211 phy1: Selected rate control algorithm 'rtl_rc'
[ 7848.904649] rtl8192cu: MAC auto ON okay!
[ 7848.937392] rtl8192cu: Tx queue select: 0x05
[ 7848.938306] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cufw.bin

```rfkill list all gives:
```
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

Does this help and I will switch to my netbook that I'm currently tethering with instead to disconnect the Ethernet.

---

### Post by chili555 on 2012-09-04
> rtlwifi: reg 0x102, usbctrl_vendorreq TimeOut!It does help. Googling shows it's probably a firmware issue and I see no solution. You might verify its integrity:```
md5sum /lib/firmware/rtlwifi/rtl8192cufw.bin
```If you get 943e9b714a926e630b8152d7aad91d2e then it's not corrupted in any way.

Assuming so, the next step is to blacklist rtl8192cu and try ndiswrapper:```
sudo su
echo "blacklist rtl8192cu" >> /etc/modprobe.d/blacklist.conf
echo ndiswrapper >> /etc/modules
exit
```Reboot. Verify that ndiswrapper loaded:```
lsmod | grep ndiswrapper
iwconfig
```Any improvements?

---

### Post by lillypad on 2012-09-04
md5sum /lib/firmware/rtlwifi/rtl8192cufw.bin gives:
```
943e9b714a926e630b8152d7aad91d2e  /lib/firmware/rtlwifi/rtl8192cufw.bin
```lsmod | grep ndiswrapper gives:
```
ndiswrapper           282628  0 
```iwconfig gives:
```
lo        no wireless extensions.

eth0      no wireless extensions.
```It appears that there is no conflicting driver but wlan0 is not up

rfkill list all gives nothing so ndiswrapper is seeing the device but nm-tool is not.

sudo ifconfig wlan0 up gives:
```
wlan0: ERROR while getting interface flags: No such device
```perhaps running ndiswrapper -m should get it going?

---

### Post by chili555 on 2012-09-04
Let's see what interesting clues we can find:```
ndiswrapper -l
dmesg | grep ndis
```Thanks.

---

### Post by lillypad on 2012-09-04
ndiswrapper -l gives:
```
net8192cu : driver installed
    device (050D:2103) present (alternate driver: rtl8192cu)

```

dmesg | grep ndis gives:
```
[    9.157046] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[    9.878333] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[    9.878337] ndiswrapper (load_sys_files:199): couldn't prepare driver 'net8192cu'
[    9.878446] ndiswrapper (load_wrap_driver:121): couldn't load driver 'net8192cu'
[    9.878484] usbcore: registered new interface driver ndiswrapper
```

So I believe you found that the ndiswrapper driver is not 64 bit so thus I will try the windows 7 driver instead. 

I believe to do this I should
```
sudo ndiswrapper -i win7x64driver.inf
sudo ndiswrapper -m
```

Hopefully this is the right path to take! I appreciate your help your great!

---

### Post by lillypad on 2012-09-05
**This is with the Win7X64 driver:**

**ndiswrapper -l gives:**
```
net8192cu : driver installed
    device (050D:2103) present (alternate driver: rtl8192cu)

```**dmesg | grep ndis gives:**
```
[    8.797870] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[    9.250063] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'PoRegisterPowerSettingCallback'
[    9.250070] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'PoUnregisterPowerSettingCallback'
[    9.250083] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[    9.250086] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[    9.250090] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[    9.250093] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisRegisterDeviceEx'
[    9.250096] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[    9.250100] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[    9.250103] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[    9.250106] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[    9.250111] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[    9.250126] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[    9.250129] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[    9.250134] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[    9.250142] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[    9.250145] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[    9.250152] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisDeregisterDeviceEx'
[    9.250155] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[    9.250159] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[    9.250162] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[    9.250165] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[    9.250171] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[    9.250174] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[    9.250177] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreePort'
[    9.250180] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[    9.250183] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBindClass'
[    9.250186] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[    9.250189] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[    9.250191] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbindClass'
[    9.250193] ndiswrapper (load_sys_files:199): couldn't prepare driver 'net8192cu'
[    9.250270] ndiswrapper (load_wrap_driver:121): couldn't load driver 'net8192cu'
[    9.250322] usbcore: registered new interface driver ndiswrapper
```

Was thinking of using the bus id in ndiswrapper because...

lsusb gives:
```
Bus 001 Device 002: ID 050d:2103 Belkin Components F7D2102 802.11n N300 Micro Wireless Adapter v3000 [Realtek RTL8192CU]

```

and then maybe using this could clean it up?
```
sudo ndiswrapper -a net8192cu 050D:2103
```
Thinking of grabbing some popcorn cause this is gonna be longer than watching all the lord of the ring movies back to  back lol :popcorn: would u guys like some pop corn?

---

### Post by chili555 on 2012-09-05
Ndiswrapper *MUST* use the XP driver. [http://en.wikipedia.org/wiki/NDISwrapper](http://en.wikipedia.org/wiki/NDISwrapper)> NDISwrapper is a free software driver wrapper that enables the use of ***Windows XP*** network device drivers (for devices such as PCI cards, USB modems, and routers) on Linux operating systems. So you need to find and install the 64-bit XP driver. Is one on Realtek's site in the download section?

---

### Post by lillypad on 2012-09-05
So i downloaded and installed the WinX64 driver.

Here is what happened to the pc and now it won't even boot to ttyl1 or terminal even:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=223718&stc=1&d=1346853018[/IMG]

---

### Post by chili555 on 2012-09-05
Can you boot in failsafe mode and do:```
rm -rf /etc/ndiswrapper/*
```Then reboot normally?

Can you boot the Live CD and delete all the /etc/ndiswrapper/whatever files from the installed partition and then reboot normally?

---

### Post by lillypad on 2012-09-05
Alright! we are back in business as in the computer is actually using gui.

Wireless is however still not working.

---

### Post by chili555 on 2012-09-05
Hook up the ethernet and let's compile the latest from Realtek. Please open a terminal and do:```
sudo apt-get remove --purge ndiswrapper*
sudo apt-get install linux-headers-generic build-essential
```Now grap the file here: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true) 

Download it to your desktop and right-click it and select Extract Here. Now back to the terminal:```
cd Desktop/RTL81
```Press the Tab key and the remiander will fill in automatically. Press Enter.```
sudo su
chmod +x install.sh
./install.sh
modprobe -r rtl8192cu
modprobe 8192cu
exit
```If it works correctly, we'll need to amend the blacklist file.

---

### Post by lillypad on 2012-09-05
> **chili555 said:**
> Hook up the ethernet and let's compile the latest from Realtek. Please open a terminal and do:```
sudo apt-get remove --purge ndiswrapper*
sudo apt-get install linux-headers-generic build-essential
```Now grap the file here: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true) 

Download it to your desktop and right-click it and select Extract Here. Now back to the terminal:```
cd Desktop/RTL81
```Press the Tab key and the remiander will fill in automatically. Press Enter.```
sudo su
./install.sh
modprobe -r rtl8192cu
modprobe 8192cu
exit
```If it works correctly, we'll need to amend the blacklist file.

After these steps the device does work excellent! I hope that we can mark the thread as solved now! Thank you for you help and if it's alright I'd love to repost your solution on my web-space is there a website you have or anywhere I can link to in-order to give credit?

---

### Post by chili555 on 2012-09-05
Excellent! Glad it's working and solved. You may feel free to publish the solution. If want a link, I suggest you link back to this thread.

Have fun!

---

### Post by lillypad on 2012-09-05
Thanks chili555! The help has be greatly appreciated!

---

### Post by chili555 on 2012-09-05
When an updated kernel or linux-image, as it's known in Ubuntu, is installed by Update Manager, you'll probably need to re-compile as above.

Please use thread tools at the top to mark Solved.

---

