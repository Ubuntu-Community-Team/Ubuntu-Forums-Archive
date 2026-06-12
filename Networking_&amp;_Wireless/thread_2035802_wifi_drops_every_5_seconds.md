---
title: "wifi drops every 5 seconds"
date: 2012-07-31
forum: Networking &amp; Wireless
---

### Post by themaskofwraith on 2012-07-31
EDIT: i found that i should install the kernal from here [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=228&DownTypeID=3&GetDown=false&Downloads=true#2282](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=228&DownTypeID=3&GetDown=false&Downloads=true#2282)
But i dont have any idea how to do it. THX

Hi,

I have ASUS wl-167G usb  wifi card.

My wifi card is in ubuntu supported wifi cards lists. it works perfectly fine  in windows.

After the clean install of ubuntu 12.04 , my wifi card is detected and shows the available networks. But Once i connected to wireless networks, it drops the connection within 5 seconds , it may or maynot connect to network again.

i tried to update the kernal using the 3g connection, from the update wizard but it didnt help me.

i tried checking and unchecking available to all users option, disabled the power management for wlan0, tried ignoring the ipv6 option.

Any ideas how to fix it?

System outputs
1)lsusb 
us 001 Device 002: ID 046d:081b Logitech, Inc. Webcam C310
Bus 002 Device 002: ID 0b05:1791 ASUSTek Computer, Inc. WL-167G v3 802.11n Adapter [Realtek RTL8188SU] (THIS is my wifi card)
Bus 002 Device 005: ID 12d1:1436 Huawei Technologies Co., Ltd. 
Bus 005 Device 002: ID 1c4f:0002 SiGma Micro Keyboard TRACER Gamma Ivory
Bus 005 Device 003: ID 046d:c245 Logitech, Inc. 

2)ifconfig

eth0      Link encap:Ethernet  HWaddr 70:71:bc:77:3b:0a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:d2300000-d2320000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:196 errors:0 dropped:0 overruns:0 frame:0
          TX packets:196 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15532 (15.5 KB)  TX bytes:15532 (15.5 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:49.203.157.209  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:3235 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:4168746 (4.1 MB)  TX bytes:287807 (287.8 KB)

wlan0     Link encap:Ethernet  HWaddr 14:da:e9:79:66:18  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


3)iwconfig

ppp0      no wireless extensions.

lo        no wireless extensions.

wwan0     no wireless extensions.

wlan0     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

4)lsmod

Module                  Size  Used by
ppp_deflate            13038  0 
zlib_deflate           27139  1 ppp_deflate
bsd_comp               12994  0 
ppp_async              17539  1 
crc_ccitt              12667  1 ppp_async
snd_hda_codec_hdmi     32474  4 
rfcomm                 47604  0 
parport_pc             32866  0 
bnep                   18281  2 
ppdev                  17113  0 
bluetooth             180104  10 rfcomm,bnep
snd_usb_audio         122982  1 
snd_hda_codec_realtek   223867  1 
snd_hda_intel          33773  4 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec
r8712u                189603  0 
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
snd_usbmidi_lib        25395  1 snd_usb_audio
snd_seq_midi           13324  0 
snd_rawmidi            30748  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
cdc_ether              13536  0 
psmouse                87603  0 
usbnet                 26212  1 cdc_ether
snd                    78855  22 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nouveau               774571  3 
ttm                    76949  1 nouveau
uvcvideo               72627  0 
drm_kms_helper         46978  1 nouveau
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
drm                   242038  5 nouveau,ttm,drm_kms_helper
serio_raw              13211  0 
i7core_edac            28102  0 
joydev                 17693  0 
edac_core              53746  3 i7core_edac
i2c_algo_bit           13423  1 nouveau
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mxm_wmi                12979  1 nouveau
wmi                    19256  1 mxm_wmi
video                  19596  1 nouveau
mac_hid                13253  0 
option                 25849  2 
usb_wwan               20491  1 option
usbserial              47077  7 option,usb_wwan
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
uas                    18027  0 
usb_storage            49198  0 
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
pata_marvell           12912  0 
e1000e                156693  0 

5)Networkconfiguration 

*-network               
       description: Ethernet interface
       product: 82567LM-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 00
       serial: 70:71:bc:77:3b:0a
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k firmware=1.8-5 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:48 memory:d2300000-d231ffff memory:d2322000-d2322fff ioport:30e0(size=32)
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: wwan0
       serial: 02:50:f3:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=Mobile Broadband Network Device link=no multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       bus info: usb@2:5
       logical name: wlan0
       serial: 14:da:e9:79:66:18
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u multicast=yes wireless=unassociated

---

### Post by themaskofwraith on 2012-07-31
any thoughts?

---

### Post by themaskofwraith on 2012-08-04
4 days no one had any idea, is it the real ubuntu forums?

---

