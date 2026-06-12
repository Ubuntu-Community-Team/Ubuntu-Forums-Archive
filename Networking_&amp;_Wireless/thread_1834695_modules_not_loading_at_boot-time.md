---
title: "modules not loading at boot-time"
date: 2011-08-27
forum: Networking &amp; Wireless
---

### Post by jackoneill87 on 2011-08-27
I've recently been having a lot of trouble trying to install a ralink 3062 driver on my ubuntu 11.04 desktop. There are quite a few excellent tutorials on this website. 
[http://ubuntuforums.org/showthread.php?t=960642&highlight=ubuntu+rt2860&nojs=1#goto_threadsearch](http://ubuntuforums.org/showthread.php?t=960642&highlight=ubuntu+rt2860&nojs=1#goto_threadsearch)

In my case, however, adding the conflicting drivers to /etc/modprobe.d/blacklist.conf didn't prevent them being loaded at boot-time, so I could not make the change permanent. I eventually found a workaround online which I thought I'd share here. Once you have updated your blacklist and module list, use

> sudo update-initramfs -u

I'm a beginner so I'm not sure, but I think the problem is that initramfs loads the conflicting modules into memory before the system comes to reading the blacklist and module files. Once you've done this, restart your system and you shouldn't have any further problems.

P.s. As far as I know this only works (but should only be a problem for kernel 2.6 and later)

Hope it helps!

---

### Post by northd_tech on 2011-08-27
Let's take a look at the output from the following terminal commands:
```
lsmod
cat /etc/modules
```

---

### Post by jackoneill87 on 2011-08-28
Oh, I'm sorry. I'd managed to fix the problem already, it just took me quite a while to eventually find the answer (on a different forum) so I thought I'd post it here to help anybody was having similar problems. Thank you for your quick reply though, here's the output if you're interested. Maybe the problem wasn't what I thought it was.

lsmod
 
> lp
rtc
rt2860sta
rt3562sta.kocat etc/modules
> Module                  Size  Used by
rt3562sta             986681  1 
nls_utf8               12557  1 
isofs                  40283  1 
vesafb                 13761  1 
snd_hda_codec_hdmi     28167  4 
binfmt_misc            17565  1 
snd_usb_audio         112426  1 
snd_usbmidi_lib        25139  1 snd_usb_audio
snd_hda_codec_realtek   336771  1 
snd_hda_intel          33176  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  2 snd_usb_audio,snd_hda_codec
snd_pcm                96391  4 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
ppdev                  17113  0 
nvidia              10709116  38 
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             36959  1 
snd                    67382  18 snd_hda_codec_hdmi,snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               72195  0 
videodev               82052  1 uvcvideo
v4l2_compat_ioctl32    17078  1 videodev
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17825  0 
parport                46458  3 ppdev,parport_pc,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
r8168                 194904  0 

Before using the update r8169 (the default realtek ethernet driver) was being loaded but neither rt3562sta (wireless) nor r8168 (the correct ethernet driver) were.

---

