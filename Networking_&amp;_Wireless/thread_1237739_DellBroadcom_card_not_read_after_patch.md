---
title: "Dell/Broadcom card not read after patch"
date: 2009-08-11
forum: Networking &amp; Wireless
---

### Post by jamiejrg on 2009-08-11
Good afternoon ladies and gents,

A couple weeks ago I patched my Zydas USB wifi card for injection using this ( [http://forum.aircrack-ng.org/index.php?topic=5334.0](http://forum.aircrack-ng.org/index.php?topic=5334.0) ) tutorial in order to use the aircrack suit. During the patching process I was given the error that some modules were in use so they could not be patched. The module was ieee80211_crypt I believe, and there may have been another, can't remember.

Using 'lsmod' i determined that the module 'wl' was using that module. I was pretty sure that my laptop's internal broadcom wireless card was responsible for that so I turned my laptop's wifi switch off, restarted, and saw that it was no longer in use. So i continued with the patching process and everything worked great. I've used the injection functionality many times thus far and i'm very happy with it. Thus the patch for my Zydas card was clearly successful.

The only problem now is that ubuntu doesn't recognize the internal card at all (obviously turned my laptop's wifi switch back to the on position after :D), and I haven't the foggiest idea why. Without it I don't have access to wireless networks for internet etc, unless i use my zydas usb card that i use for injection, and i don't want to carry that thing around with me all the time, plus it's quite slow.

Also, it's probably important to say that I had been using the internal card successfully before I patched for my Zydas card. I didn't change anything else on my system.

Network Card specs

Board Name: Dell Wireless 1395 WLAN Mini-card Rev 3.00
Chipset: BCM4315 (Broadcom)

Ubuntu Specs/Output
Kernel: 2.6.28-13-generic


What baffles me is that both the wl and b43 mdules seem to be initialized but my hardware just isn't working/being recognized.

lsmod

```
Module                  Size  Used by
i915                   65668  2 
drm                    96296  3 i915
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
lp                     17156  0 
parport                42220  2 ppdev,lp
joydev                 18368  0 
snd_hda_intel         434100  3 
b43                   136860  0 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
mac80211              223780  1 b43
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
cfg80211               71584  2 b43,mac80211
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
led_class              12036  1 b43
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
input_polldev          11912  1 b43
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
wl                   1281236  0 
ieee80211_crypt        13444  1 wl
uvcvideo               63240  0 
compat_ioctl32          9344  1 uvcvideo
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                61972  0 
ssb                    53256  1 b43
videodev               41600  1 uvcvideo
soundcore              15200  1 snd
sdhci_pci              15232  0 
sdhci                  23940  1 sdhci_pci
dcdbas                 15264  0 
serio_raw              13316  0 
pcspkr                 10496  0 
v4l1_compat            21764  2 uvcvideo,videodev
usbhid                 42336  0 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
pcmcia                 44748  2 b43,ssb
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
video                  25360  0 
btusb                  19608  2 
intel_agp              34108  1 
pcmcia_core            43540  3 b43,ssb,pcmcia
output                 11008  1 video
agpgart                42696  3 drm,intel_agp
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
sky2                   54916  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```

Thanks ahead of time guys. If you need any more information about my system or hardware just post and i'll be happy to find it for you.

---

