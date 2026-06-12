---
title: "Crackling in earphones"
date: 2015-11-10
forum: Multimedia Software
---

### Post by Marko_Drobac on 2015-11-10
Hi I've been using Ubuntu 14.04 for maybe about 6 months now and there's always been this issue with a static, crackling noise in my earphones. It's not constant, it only happens during any action that takes CPU usage. Doing things like hovering a mouse over something, opening a new tab, and especially playing a video. During videos, even if you turn the volume all the way down within Ubuntu, as long as the physical volume bar on my speakers which are connected to my earphones is on, the crackling is quite loud. It's possible to remove the crackling if you completely mute within Ubuntu, though. I've tried a lot of different solutions, one which even caused me to break my OS for a day, but nothing worked. For example I tried updating my kernel to 3.16, white_noise_fix.py, and turning power save off, from [this thread]("http://askubuntu.com/questions/524344/noise-from-headphones"). I'm on a Dell Inspiron 530S. Also I dual-boot with Vista and this doesn't happen there.

---

### Post by sandyd on 2015-11-10
Moved to *Multimedia*

---

### Post by tgalati4 on 2015-11-11
I presume you have standard Intel HDA sound, although reviewing the specifications, it supports 7.1 surround sound.

Post the output of:

```
aplay -l
```

and

```
lsmod | grep snd
```

There may be some switches to experiment with:

> tgalati4@Mint17 ~ $ modinfo snd_hda_intel
filename:       /lib/modules/3.13.0-24-generic/kernel/sound/pci/hda/snd-hda-intel.ko
description:    Intel HDA driver
.
.
.
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        69:B0:D0:A7:9B:85:D9:06:21:70:6E:8D:06:60:4D:73:0B:35:9F:C0
sig_hashalgo:   sha512
parm:           index:Index value for Intel HD audio interface. (array of int)
parm:           id:ID string for Intel HD audio interface. (array of charp)
parm:           enable:Enable Intel HD audio interface. (array of bool)
parm:           model:Use the given board model. (array of charp)
parm:           position_fix:DMA pointer read method.(-1 = system default, 0 = auto, 1 = LPIB, 2 = POSBUF, 3 = VIACOMBO, 4 = COMBO). (array of int)
parm:           bdl_pos_adj:BDL position adjustment offset. (array of int)
parm:           probe_mask:Bitmask to probe codecs (default = -1). (array of int)
parm:           probe_only:Only probing and no codec initialization. (array of int)
parm:           jackpoll_ms:Ms between polling for jack events (default = 0, using unsol events only) (array of int)
parm:           single_cmd:Use single command to communicate with codecs (for debugging only). (bool)
parm:           enable_msi:Enable Message Signaled Interrupt (MSI) (bint)
parm:           patch:Patch file for Intel HD audio interface. (array of charp)
parm:           beep_mode:Select HDA Beep registration mode (0=off, 1=on) (default=1). (array of bool)
parm:           power_save:Automatic power-saving timeout (in second, 0 = disable). (xint)
parm:           power_save_controller:Reset controller in power save mode. (bool)
parm:           align_buffer_size:Force buffer and period sizes to be multiple of 128 bytes. (bint)
parm:           snoop:Enable/disable snooping (bool)


Try turning off *pulseaudio* to see if it is a *pulseaudio* issue.  [http://askubuntu.com/questions/82109/bursts-of-white-noise-sound-when-playing-videos](http://askubuntu.com/questions/82109/bursts-of-white-noise-sound-when-playing-videos).  This is an old thread, but I think the procedure still works.

Take notes as you try different approaches.  Fixing sound takes patience.

---

### Post by Marko_Drobac on 2015-11-11
Hmm, I've realized the crackling maybe is not such a big deal. The main concern I had about it was for watching videos/ listening to music, but I found yesterday that the crackling disappears when I'm listening to things.

So the only bother happens if I have earphones on and I'm not actually listening to anything, which isn't actually a big deal, since I can just take them off and do stuff. But maybe it's still worth troubleshooting it.

Anyway, here's what you asked for.

Output of aplay -l

> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Output of lsmod | grep snd

> snd_hda_codec_hdmi     47548  1
snd_hda_codec_realtek    77561  1
snd_hda_codec_generic    69011  1 snd_hda_codec_realtek
snd_hda_intel          30469  5
snd_hda_controller     30228  1 snd_hda_intel
snd_hda_codec         139719  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              17698  1 snd_hda_codec
snd_pcm               104112  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi           13564  0
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30876  1 snd_seq_midi
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29562  2 snd_pcm,snd_seq
snd                    79468  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              15047  2 snd,snd_hda_codec

For turning off pulseaudio:

I wasn't able to follow the instructions exactly in the link, because I don't have a .pulse folder in my home directory. But I found I could access the file in /etc/pulse/client.conf. So there, I uncommented the line with ```
; autospawn = yes
``` and changed it to ```
autospawn = no
``` Then I used the ```
killall pulseaudio
``` After that, there was still crackling.

I'm not sure how to replicate the step where it says to change Audio settings to Alsa:default using MythTv, since I don't have that on my distribution. But if I disabled pulseaudio and still have sound (which I do), then it's already using alsa default, no?

I don't know how I can experiment with the switches you posted.

---

### Post by tgalati4 on 2015-11-12
ALSA is an older sound framework that is used as a fallback when *pulseaudio* is turned off.

Play some familiar music in Windows and measure the loudest level you can play through speakers, not earphones.  Do the same in Linux.  If it is louder in Linux, then you know the base gain is louder under Linux, which will amplify blips and pops that get picked up inside the computer.  *Pulseaudio* is known to cause clicks and pops when the CPU is loaded.  So if you still get the noise without *pulseaudio* then you can be reasonably sure that it is your sound chip, ALC888, and there may not be much you can do about it.

Cheap speakers and earbuds will hide the noise, but expensive, sensitive headphones will reveal all sorts of noise.  PC's are not audiophile equipment.

Some reading:  [http://forums.anandtech.com/showthread.php?t=150208](http://forums.anandtech.com/showthread.php?t=150208)

[http://www.diyaudio.com/forums/pc-based/262236-onboard-audio-chip-noise-cannot-figure-out.html](http://www.diyaudio.com/forums/pc-based/262236-onboard-audio-chip-noise-cannot-figure-out.html)

---

### Post by Yellow Pasque on 2015-11-13
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

I would try the latest kernel module to see if the issue has been fixed upstream: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)
If you're confused as to which package to use, the alsa info you provide will tell us what kernel you're using (and much more).

---

