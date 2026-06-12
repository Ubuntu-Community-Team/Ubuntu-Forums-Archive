---
title: "Unknown symbol in module, or unknown parameter"
date: 2009-09-20
forum: Multimedia Software
---

### Post by doesntcount on 2009-09-20
Hi there,

I have a sound card that was recently supported in the very latest alsa-drivers. I found a great howto to get it working:

[http://wiki.debian.org/X-Fi](http://wiki.debian.org/X-Fi)

but when I went to load the newly built module, I encountered this error:

```
root@donny:/usr/src/alsa/alsa-driver-1.0.21# modprobe snd-ctxfi
FATAL: Error inserting snd_ctxfi (/lib/modules/2.6.28-15-generic/updates/alsa/pci/ctxfi/snd-ctxfi.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

dmesg suggests a tonne of version mismatches:

```
[ 2191.862110] snd_ctxfi: disagrees about version of symbol snd_ctl_add
[ 2191.862114] snd_ctxfi: Unknown symbol snd_ctl_add
[ 2191.862209] snd_ctxfi: disagrees about version of symbol snd_pcm_new
[ 2191.862211] snd_ctxfi: Unknown symbol snd_pcm_new
[ 2191.862276] snd_ctxfi: disagrees about version of symbol snd_card_register
[ 2191.862277] snd_ctxfi: Unknown symbol snd_card_register
[ 2191.862337] snd_ctxfi: disagrees about version of symbol snd_card_free
[ 2191.862338] snd_ctxfi: Unknown symbol snd_card_free
[ 2191.862396] snd_ctxfi: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
....

```

When I ran ./configure, i was sure to add this option:

--with-moddir=/lib/modules/$(uname -r)

Is my problem that these drivers are simply incompable with 2.6.28-15? Am I going to have to upgrade my kernel? That would be lame.

FYI, i've also double checked that I have the correct linux-headers package installed. For the record, i'm using 2.6.28-15

Any help on this would be greatly appreciated. I desperately need sound :/

Thanks.

---

### Post by lloyd_b on 2009-09-20
You can try running modprobe with the "-f" option, which will skip past those version errors.

This *is* dangerous, and can cause problems, up to and including crashing the kernel, so I would recommend not trying it while anything important is running...

Lloyd B.

---

### Post by doesntcount on 2009-09-20
Rebooting has solved this issue. I don't understand why it solved it. I rebooted with the exact same kernel i was running with when i got the error :/

Anyway, my next issue is that, while i have the new driver installed, and my soundcard is now recognized, it's not playing sound from certain applications. For example, alsamixer shows that I'm editing the settings for the x-fi card, which is good. And when I go to gnome's sound settings widget, and select the x-fi card as the output device, it plays the beeping sound out my s/pdif, which is an awesome step forward. Yet, when I use aplay, or try to play sound from firefox, i don't get sound :(

I hope I'm close, but I feel like I still have a ways to go. Why does sound have to be so difficult in Linux. It's easily the category where I've had the most problems historically.

If anybody has some pointers, please give me a shout. I'd really appreciate any help here.

---

### Post by raboofje on 2009-09-20
> **doesntcount said:**
> For example, alsamixer shows that I'm editing the settings for the x-fi card, which is good. And when I go to gnome's sound settings widget, and select the x-fi card as the output device, it plays the beeping sound out my s/pdif, which is an awesome step forward. Yet, when I use aplay, or try to play sound from firefox, i don't get sound :(

What do 'aplay -l' and 'cat /proc/asound/cards' tell you?

---

### Post by doesntcount on 2009-09-20
pretty much what I think it should:

```
root@donny:/home/nkaun# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: XFi [Creative X-Fi], device 0: ctxfi [Front/WaveIn]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 1: ctxfi [Surround]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 2: ctxfi [Center/LFE]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 3: ctxfi [Side]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 4: ctxfi [IEC958 Non-audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 1: ALC887 Digital [ALC887 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
root@donny:/home/nkaun# cat /proc/asound/cards
 0 [XFi            ]: SB-XFi - Creative X-Fi
                      Creative X-Fi 20K1 Unknown
 1 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf7df8000 irq 21

```

Seems reasonable, right?

---

### Post by doesntcount on 2009-09-20
Man, sound on linux confuses the heck out of me. 

So, in the gnome sound settings, like I said before, i choose Alsa output, and it plays dolby digital to my decoder. So that's excellent. If I choose OSS output, it plays stereo to the decoder. Fine. I installed Audacious, and if i tell it to play to the alsa output plugin, there is no sound. But if i tell it to play to it's oss plugin, i get sound. This is fine for me since what i'm playing with audacious will only have 2 channels anyway, but any idea why it can't play to the alsa plugin?

In firefox, however, i can't get sound from flash movies at all. Firefox doesn't seem to have any options to choose a sound output plugin like audacious has. Is there some trick to getting firefox to play sound? It's really annoying that this doesn't just work.

---

### Post by doesntcount on 2009-09-20
Hmmm, playing to the oss with stereo output is no good, because what I do is I split the coax to two separate decoders. If it's just stereo output, only one of the decoders gets the signal. So I do need audacious to be able to play to the alsa plugin.

---

