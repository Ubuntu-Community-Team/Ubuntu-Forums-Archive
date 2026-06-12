---
title: "Initial impressions  generic RT2800USB adapter - pretty good."
date: 2013-03-07
forum: Networking &amp; Wireless
---

### Post by kurt18947 on 2013-03-07
I was tempted by an Ebay offering for this device:
[http://www.ebay.com/itm/Newest-Mini-150Mbps-USB-WiFi-Wireless-N-LAN-Network-Adapter-802-11n-g-b-/170905493801?ssPageName=ADME:L:OC:US:3160](http://www.ebay.com/itm/Newest-Mini-150Mbps-USB-WiFi-Wireless-N-LAN-Network-Adapter-802-11n-g-b-/170905493801?ssPageName=ADME:L:OC:US:3160)
generic RT2800USB nano adapter.  I've sort of shied away from Ralink adapters because they seem to have more than their share of "how do I get this to work?" threads that seem not easily solved.  Figured for $5.59 plus tax I'd take a chance.  I've only had this for about an hour but here are my initial observations.  

-It's surprisingly compatible.  I've tried it on the boxes I have handy - AMD desktop, ThinkPad R61i, ThinkPad R31.  I have a few different distros, all Ubuntu/Debian variants.  13.04 64 bit, Ubuntu Gnome 12.10, Ubuntu 12.04 64 bit, Xubuntu12.04 32 bit, Mint 13 32 bit. In each case  plug it in and it worked.  No compiling, no .conf file modifications so far.  The speed and signal strength seem reasonable but not great, not as good as the Edimax in the same location.   Signal reception is similar to or a bit weaker than the Netgear WNA1100.

-The biggest downside I've seen so far is range.  I have an Edimax EW-7811Un whose signal strength I find remarkable for such a small device.  This generic adapter? Not as good.  Not bad, but I wouldn't recommend it for use where signal strength is marginal.

The biggest upside and a pleasant surprise to me was the fact that it was plug 'n' play.  The speed is fine for web surfing and probably torrents.  I don't know about larger file transfers within a lan or similar bandwidth intensive application.  Here is the lsusb I.D.:

Bus 001 Device 002: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter

lsmod:

```
lsmod
Module                  Size  Used by
rfcomm                 42641  0 
parport_pc             32688  0 
ppdev                  17073  0 
bnep                   18036  2 
bluetooth             228619  10 bnep,rfcomm
snd_hda_codec_realtek    78399  1 
snd_hda_intel          39619  3 
arc4                   12615  2 
snd_hda_codec         136128  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
nvidia               9350503  38 
rt2800usb              26854  0 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
rt2x00usb              20635  1 rt2800usb
rt2800lib              66507  1 rt2800usb
rt2x00lib              54869  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              606411  3 rt2x00lib,rt2x00usb,rt2800lib
kvm_amd                59717  0 
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
joydev                 17377  0 
kvm                   443165  1 kvm_amd
cfg80211              510937  2 mac80211,rt2x00lib
crc_ccitt              12707  1 rt2800lib
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
hid_logitech_dj        18604  0 
hid_generic            12540  0 
snd_timer              29425  2 snd_pcm,snd_seq
snd                    68876  15 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
usblp                  18111  0 
edac_core              62003  0 
usb_storage            57199  0 
usbhid                 47074  1 hid_logitech_dj
soundcore              12680  1 snd
wmi                    19070  0 
microcode              22881  0 
sp5100_tco             13929  0 
psmouse                91076  0 
lp                     17759  0 
hid                   101002  5 hid_generic,usbhid,hid_logitech_dj
edac_mce_amd           23114  0 
i2c_piix4              13266  0 
k10temp                13126  0 
parport                46345  3 lp,ppdev,parport_pc
mac_hid                13205  0 
serio_raw              13215  0 
pata_acpi              13038  0 
r8169                  67446  0 
pata_atiixp            13242  0 
ahci                   25731  1 
libahci                31364  1 ahci

```

Edit:  Speed is more of an issue than I originally thought.  Here is  a sample while connected to an N speed only WAP.  Distance is about 20 feet through 2 drywall walls.
wlan1     IEEE 802.11bgn  ESSID:"xxxxxxx"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:F8:5C:88:F4   
          Bit Rate=39 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=41/70  Signal level=-69 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:220  Invalid misc:97   Missed beacon:0

---

