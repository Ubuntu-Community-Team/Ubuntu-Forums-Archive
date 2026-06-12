---
title: "No microphone detected, only mono (one speaker) working"
date: 2009-08-06
forum: Multimedia Software
---

### Post by guiar69 on 2009-08-06
Hi All

My laptop: Compaq 610. My Ubuntu level: apprentice.
Uninstalled Vista and now I am running Ubuntu 9.04 (64 bits) after trying on another laptop ubuntu on virtual machine, initially previous ubuntu version, then 9.04 (both 32 bits), and never had any problem with sounds.

With this new laptop, After installation I had no sound at all and then, watching different forums information, managed to get only mono sound (only one speaker). I did a lot, but I think that I managed to hear something because of ALSA version upgrade.

Now I have no idea about what to do in order to get stereo sound but mainly to get the microphone working. It is not detected when you want to include the mic volume control. You can see "what I cannot find" looking at the attached screenshots. Everything is checked on volume control window but still I cannot find a mic volume control

[IMG]file:///tmp/moz-screenshot.jpg[/IMG]


I got the following info using lspci and lsmod commands:

**lspci**

guillermo@guillermo-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile GME965/GLE960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
30:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4357 (rev 10)


**lsmod**

guillermo@guillermo-laptop:~$ lsmod
Module                  Size  Used by
usbhid                 47040  0 
nls_iso8859_1          13440  1 
nls_cp437              15104  1 
vfat                   21120  1 
fat                    65592  1 vfat
usb_storage           115392  2 
aes_x86_64             16384  3 
aes_generic            36264  1 aes_x86_64
i915                   75528  3 
drm                   123232  4 i915
binfmt_misc            18572  1 
ppdev                  16904  0 
bridge                 63904  0 
stp                    11140  1 bridge
bnep                   22912  2 
vboxnetflt            110444  0 
vboxdrv              1705004  2 vboxnetflt
input_polldev          12688  0 
joydev                 20864  0 
lp                     19588  0 
parport                49584  2 ppdev,lp
snd_hda_codec_idt      78476  1 
snd_hda_intel          38536  7 
snd_hda_codec          93824  2 snd_hda_codec_idt,snd_hda_intel
arc4                   10240  2 
snd_hwdep              17032  1 snd_hda_codec
snd_pcm_oss            51872  0 
snd_mixer_oss          25088  1 snd_pcm_oss
ecb                    11392  2 
snd_pcm                98696  5 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_oss            40320  0 
snd_seq_midi_event     16640  1 snd_seq_oss
snd_seq                66848  4 snd_seq_oss,snd_seq_midi_event
snd_timer              33168  2 snd_pcm,snd_seq
snd_seq_device         16532  2 snd_seq_oss,snd_seq
iwl3945               111096  0 
snd                    82760  23 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq,snd_timer,snd_seq_device
uvcvideo               69640  0 
mac80211              251528  1 iwl3945
compat_ioctl32         18304  1 uvcvideo
soundcore              16800  1 snd
video                  29204  0 
psmouse                64028  0 
videodev               45184  2 uvcvideo,compat_ioctl32
v4l1_compat            23940  2 uvcvideo,videodev
snd_page_alloc         18960  2 snd_hda_intel,snd_pcm
output                 11648  1 video
intel_agp              39408  1 
serio_raw              14468  0 
led_class              13064  1 iwl3945
iTCO_wdt               21712  0 
iTCO_vendor_support    12420  1 iTCO_wdt
cfg80211               43680  2 iwl3945,mac80211
pcspkr                 11136  0 
sky2                   63364  0 
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit
guillermo@guillermo-laptop:~$ 

Thanks in advance for your valuable help.

Best,


Guillermo

---

### Post by wgarciamachmar on 2009-12-04
I have the same problem. Actually, I haven't tried the mic. But still, the mono sound is kinda annoying.

Edit: mic works perfectly, with no tweaks. Sound is still in mono, don't know what to try.

---

### Post by ubshreenath on 2010-03-20
A little late a reply but the Compaq 610 has only mono inbuilt speakers.

Check the specification here:[URL="http://h10010.www1.hp.com/wwpc/us/en/sm/WF06a/321957-321957-64295-3929949-3955548-3958407.html"]
http://h10010.www1.hp.com/wwpc/us/en/sm/WF06a/321957-321957-64295-3929949-3955548-3958407.html[/URL]

Cheers
Sreenath
[http://sreenath.net](http://sreenath.net)

---

### Post by guiar69 on 2010-06-01
Hi Sreenath

Thanks for your answer, anyway. I realized later on that this laptop had only one mono speaker. I lost this laptop 6 months ago in Mexico (stolen in a restaurant) amd I had to come back to my old and loyal toshiba a135.

Best,


Guillermo

---

