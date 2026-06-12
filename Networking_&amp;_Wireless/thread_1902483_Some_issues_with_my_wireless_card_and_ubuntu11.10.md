---
title: "Some issues with my wireless card and ubuntu11.10"
date: 2011-12-30
forum: Networking &amp; Wireless
---

### Post by ChrisJCL on 2011-12-30
Okay, 

Fresh install of ubuntu 11.10 and it had found my card and I'm able to browse the web. Alongside of aircrack and other programs the main issue I'm having is the -1 channel issue that i've found to be quite abundant with my wireless card. None, of the information I've read was able to help me and I've decided to come here since majority of those posts were from here and have been since resolved.

chris@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 98:4b:e1:bc:dc:de  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:41 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr cc:52:af:58:18:12  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ce52:afff:fe58:1812/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2184 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2134 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2029636 (2.0 MB)  TX bytes:436460 (436.4 KB)

chris@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Seahorses4eva"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: C0:3F:0E:A6:56:5A   
          Bit Rate=54 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:77   Missed beacon:0

chris@ubuntu:~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  8 
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
wl                   2646601  0 
joydev                 17393  0 
lib80211               14570  1 wl
bcma                   19571  0 
arc4                   12473  2 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_idt      60049  1 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
btusb                  18160  2 
bluetooth             148839  23 bnep,rfcomm,btusb
psmouse                73673  0 
snd_timer              28932  2 snd_pcm,snd_seq
serio_raw              12990  0 
rts_pstor             353227  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
intel_ips              17753  0 
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
brcmsmac              591864  0 
brcmutil               16885  1 brcmsmac
mac80211              393459  1 brcmsmac
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
cfg80211              172392  2 brcmsmac,mac80211
crc_ccitt              12595  1 brcmsmac
i915                  505159  3 
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
wmi                    18744  1 hp_wmi
mei                    36466  0 
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  43104  0 
ahci                   21634  1 
libahci                25727  1 ahci


I've tried to install the compat-wireless patch and the others that come along, but I feel I haven't done this properly. 

I'm not sure what other information you would need, feel free to ask and I'll post anything that I can.

---

