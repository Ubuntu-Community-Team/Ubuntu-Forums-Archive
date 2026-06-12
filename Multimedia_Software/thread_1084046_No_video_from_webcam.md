---
title: "No video from webcam"
date: 2009-03-01
forum: Multimedia Software
---

### Post by lingenfr on 2009-03-01
According to my research, the;

tv8532		0923:010f	ICM532 cams

should work. LSUSB produces:

Bus 001 Device 014: ID 0923:010f IC Media Corp. SIIG MobileCam

However, I can't seem to get any video. The lights come on as if it is being accessed, but no app will produce video. In dmesg, the errors are as follows:

[31475.148637] usb 1-6.1: new full speed USB device using ehci_hcd and address 14
[31475.270630] usb 1-6.1: configuration #1 chosen from 1 choice
[31475.275252] gspca: probing 0923:010f
[31475.660592] gspca: probe ok
[31556.641114] gspca: usb_submit_urb [0] err -28
[31556.865348] gspca: usb_submit_urb [0] err -28


Those errors go on for ever until I force camorama to quit. FWIW, it is not the app, I have tried many. Any assistance is appreciated. Thanks.

---

### Post by lingenfr on 2009-03-07
bumpski

---

### Post by lingenfr on 2009-04-11
bumposity

---

### Post by jmore9 on 2009-04-11
I use a creative instant web cam for a security camera in my apt.  When i upgraded to 9.04 it ceased to work.  I then found out the camstream that i used was using the v4l1 software.  So i went to launchpad and typed in camstream in launchpad they had a work around that has made it work just fine.

Maybe you should try going to launchpad and entering your software package and see if there are any problems.

Also try lsusb and see if your cam is listed.  Also try Cheese Webcam Booth.  If you get video out of it you are good to go.  Cheese Webcam Booth is in the standard repos.

Hope that helps a little.

---

### Post by lingenfr on 2009-04-18
I looked on lauchpad. This seems to be a long standing problem. Looks like this is one area where Fedora is kicking debian/ubuntu ****. It seems that it is fixed for some. I tried cheese, camorama and ekiga and none worked. I tried their LD_PRELOAD ideas which produced different errors but still no joy. If it is helpful, here are the results of lsmod:

lingenfr@U100-UBU:~$ lsmod
Module                  Size  Used by
gspca_tv8532           19584  0 
gspca_main             29952  1 gspca_tv8532
videodev               41600  1 gspca_main
v4l1_compat            21764  1 videodev
i915                   65540  2 
drm                    96296  3 i915
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_intel8x0           37532  3 
pcmcia                 44748  0 
snd_ac97_codec        112292  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
wlan_scan_sta          20480  1 
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ath_rate_sample        19840  1 
sdhci_pci              15232  0 
yenta_socket           32396  1 
rsrc_nonstatic         19328  1 yenta_socket
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
ath_pci                99224  0 
snd                    62628  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
sdhci                  23940  1 sdhci_pci
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
wlan                  210288  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               198864  3 ath_rate_sample,ath_pci
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm
intel_agp              34108  1 
pcspkr                 10496  0 
btusb                  19608  2 
shpchp                 40212  0 
agpgart                42696  3 drm,intel_agp
psmouse                61972  0 
video                  25360  0 
output                 11008  1 video
serio_raw              13316  0 
toshiba_acpi           18624  0 
input_polldev          11912  1 toshiba_acpi
usbhid                 42336  0 
ohci1394               38576  0 
usb_storage            82880  0 
ieee1394               94660  1 ohci1394
e100                   41740  0 
mii                    13312  1 e100
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

---

### Post by jmore9 on 2009-04-20
Try this :

[https://answers.launchpad.net/ubuntu/+question/49739](https://answers.launchpad.net/ubuntu/+question/49739)

This got it working for me

---

### Post by lingenfr on 2009-05-03
I read through that and various links off the page. No joy. This one is really silly. I can't believe that we are moving forward with something this basic broken.

---

