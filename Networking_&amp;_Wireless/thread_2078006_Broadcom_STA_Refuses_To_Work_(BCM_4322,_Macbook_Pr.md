---
title: "Broadcom STA Refuses To Work (BCM 4322, Macbook Pro), Have Tried Many Things"
date: 2012-10-29
forum: Networking &amp; Wireless
---

### Post by alphavictorwhiskey on 2012-10-29
I'm brand new to Linux, recently installed Kubuntu 12.10. Wi-fi worked after first install, but after shutdown, failed to work. Did fresh installs hoping to resurrect, didn't work (WLAN Interface Not Connected). I've been diligent with my search for a solution and have tried almost everything that's been suggested and I still can't seem to get wi-fi to work. I finally decided to post here to request system specfic help in fixing my problem. I'm currently sitting at a fresh install awaiting your command! Your help is truly appreciated; I really like this distro and would like to see it work!

The HOWTO suggested I post the following:

Machine Brand/Model: Macbook Pro 7,1
3.5.0-17-generic x86_64

02:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01) [14e4:432b]


eth0      Link encap:Ethernet  HWaddr 10:9a:dd:4b:18:1b  
          inet addr:10.0.0.22  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::129a:ddff:fe4b:181b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5866 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4408 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6067546 (6.0 MB)  TX bytes:912406 (912.4 KB)
          Interrupt:23 

eth1      Link encap:Ethernet  HWaddr f0:b4:79:1f:fe:0f  
          inet6 addr: fe80::f2b4:79ff:fe1f:fe0f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:617
          TX packets:0 errors:41 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:364 errors:0 dropped:0 overruns:0 frame:0
          TX packets:364 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:67000 (67.0 KB)  TX bytes:67000 (67.0 KB)

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:168
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

lo        no wireless extensions.

Module                  Size  Used by
hid_magicmouse         13740  0 
hidp                   22208  1 
bnep                   18140  2 
rfcomm                 46619  16 
parport_pc             32688  0 
ppdev                  17073  0 
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     32007  3 
snd_hda_codec_cirrus    23806  1 
lib80211_crypt_tkip    17379  0 
uvcvideo               76749  0 
snd_hda_intel          33491  5 
wl                   2573568  0 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel
videobuf2_core         32851  1 uvcvideo
videodev              120309  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12860  1 uvcvideo
videobuf2_memops       13368  1 videobuf2_vmalloc
coretemp               13400  0 
snd_hwdep              13602  1 snd_hda_codec
kvm_intel             132759  0 
btusb                  18334  0 
snd_pcm                96580  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
bluetooth             209199  27 hidp,bnep,rfcomm,btusb
snd_seq_midi           13324  0 
kvm                   414070  1 kvm_intel
snd_rawmidi            30512  1 snd_seq_midi
bcm5974                17315  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17457  0 
lib80211               14381  2 lib80211_crypt_tkip,wl
microcode              22803  0 
snd                    78734  19 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
applesmc               19314  0 
soundcore              15047  1 snd
input_polldev          13896  1 applesmc
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
shpchp                 37108  0 
mac_hid                13205  0 
apple_bl               13673  0 
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
hid_apple              13237  0 
usbhid                 46947  0 
hid                   100366  4 hid_magicmouse,hidp,hid_apple,usbhid
usb_storage            48838  0 
uas                    17844  0 
nouveau               895609  3 
ttm                    83595  1 nouveau
drm_kms_helper         46784  1 nouveau
drm                   275528  5 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13413  1 nouveau
mxm_wmi                12979  1 nouveau
wmi                    19070  2 nouveau,mxm_wmi
video                  19335  1 nouveau
firewire_ohci          40401  0 
tg3                   148780  0 
firewire_core          64368  1 firewire_ohci
crc_itu_t              12707  1 firewire_core

---

