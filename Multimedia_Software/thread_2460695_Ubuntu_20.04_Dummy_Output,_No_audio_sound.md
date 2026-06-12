---
title: "Ubuntu 20.04: Dummy Output, No audio sound"
date: 2021-04-16
forum: Multimedia Software
---

### Post by smakbar on 2021-04-16
```

/sbin/lsmod | grep snd


snd_hda_codec_realtek   131072  1
snd_hda_codec_generic    81920  1 snd_hda_codec_realtek
ledtrig_audio          16384  1 snd_hda_codec_generic
snd_hda_codec_hdmi     61440  2
snd_hda_intel          53248  7
snd_intel_dspcfg       24576  1 snd_hda_intel
snd_hda_codec         139264  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_i  ntel,snd_hda_codec_realtek
snd_hda_core           94208  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_i  ntel,snd_hda_codec,snd_hda_codec_realtek
snd_hwdep              20480  1 snd_hda_codec
snd_pcm               114688  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd  _hda_core
snd_seq_midi           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            36864  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              40960  2 snd_seq,snd_pcm
snd                    94208  25  snd_hda_codec_generic,snd_seq,snd_seq_device,snd_h   da_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_code   c,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawm  idi
soundcore              16384  1 snd
```

```
lspci -v


Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS522A PCI Express Card Reader (rev 01)
    Subsystem: Hewlett-Packard Company RTS522A PCI Express Card Reader
    Physical Slot: 4
    Flags: bus master, fast devsel, latency 0, IRQ 129
    Memory at b4300000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: rtsx_pci
    Kernel modules: rtsx_pci

```

```
pavucontrol

{IN GUI}
no card detected

```

```
alsamixer

{in GUI}
Card: HDA Intel PCH                                                                                                                                         
&#9474; Chip: Realtek ALC295                                                                                                                                    
&#9474; View: F3:[Playback] F4: Capture  F5: All                                                                                                                  
&#9474; Item: Master [dB gain: 0.00]

```

```
HDAJackRetask

{IN GUI}
3 options availabe Nvidia GPU 80 HDMI/UP,  Intel Kaylake HDMI, Realtek ALC 295
```


[B]Initially the speakers and earphones were working properly but the  mic wasn't. However, I ruined everything in order to fix mic input.
PLEASE HELP!!! [/B]

---

### Post by Yellow Pasque on 2021-04-16
> **smakbar said:**
> I ruined everything in order to fix mic input.

What exactly did you do? At least give links.

Also, there's a beter way to get info:
```
sudo alsa-info
```
Upload the info and give us the link.

---

### Post by annajane on 2021-04-23
[COLOR=#242729][FONT=Arial]Had the same issue, I just did:[/FONT][/COLOR]
sudo killall timidity
[COLOR=#242729][FONT=Arial]Then the sound came back.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]But after reboot, there is no sound again.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Then I figured out the proper way of disabling timidity:[/FONT][/COLOR]
sudo systemctl stop timidity.service
sudo systemctl disable timidity.service

---

### Post by airinghouse on 2021-05-22
I have a fresh install of 20.04 and I'm receiving the same Dummy Output problem, as well as no input device being recognized in System Settings > Sound menu.

Here's the alsa info for my device: [http://alsa-project.org/db/?f=ad0b67fbb6fecd5a285e7654d8cfd664094376f4](http://alsa-project.org/db/?f=ad0b67fbb6fecd5a285e7654d8cfd664094376f4).  In case it matters: it is a Dell Inspiron 15 model 3501.  It is a dualboot with two drives: its SSD has Windows and the HDD boots into Ubuntu.  The sound works fine in Windows. 

 I've searched through the ubuntu forums, help.ubuntu's pages, and what seems like countless random articles claiming to have a solution to no sound, dummy output, etc. But none have worked for me.  I've tried installing, reinstalling, and all sorts of things with alsa-mixer, pulseaudio, and pavucontrol, for example. 

 The only thing that has made any actual visible change (although still not working) is adding "options snd-hda-intel model=generic" to the end of the alsa-mixer conf file.  What happens when I add that is: Dummy Output is replaced by the HDMI / Internal audio output option; however, this doesn't actually fix the audio problem - still no sound (no sound from the speakers, through the headphone jack, or other device when connected by HDMI, nothing).

Running inxi - SMA and alsamixer seems to show that the system apparently sees my audio card: HDA Intel PCH and the chip.  But there's still no recognition of any output sound options from the system sound settings or pavucontrol. 

  Any ideas?  I've tried my hardest to troubleshoot it what I can find online, but nothing so far has worked.  I tried booting a live USB of a different ubuntu distro (lubuntu) to see if a live session would have proper sound, but it had the same "dummy output" too.

---

### Post by Yellow Pasque on 2021-05-23
> **airinghouse said:**
> In case it matters: it is a Dell Inspiron 15 model 3501.

Support was added in 5.13.x kernel:
[https://github.com/torvalds/linux/commit/6cc7e93f46a5ce9f65ad3c6c6f645f1d831a8fa4#diff-4a8cb4b7b03a103d12291bca0dc0787152b4507c3776329229328b56cd3088f2](https://github.com/torvalds/linux/commit/6cc7e93f46a5ce9f65ad3c6c6f645f1d831a8fa4#diff-4a8cb4b7b03a103d12291bca0dc0787152b4507c3776329229328b56cd3088f2)

---

### Post by airinghouse on 2021-05-23
> **Yellow Pasque said:**
> Support was added in 5.13.x kernel:
[https://github.com/torvalds/linux/commit/6cc7e93f46a5ce9f65ad3c6c6f645f1d831a8fa4#diff-4a8cb4b7b03a103d12291bca0dc0787152b4507c3776329229328b56cd3088f2](https://github.com/torvalds/linux/commit/6cc7e93f46a5ce9f65ad3c6c6f645f1d831a8fa4#diff-4a8cb4b7b03a103d12291bca0dc0787152b4507c3776329229328b56cd3088f2)

Thank you so much for your help and reply.  That's great that the new kernel looks like it will solve it.  

If I understand correctly, my options now are to manually upgrade the kernel to 5.13-rc3 preview/release candidate or wait until it becomes officially upgradable through ubuntu's updater?

Is there a way that I can add the relevant code or install a package to enable compatibility without having to upgrade to 5.13?

---

### Post by Yellow Pasque on 2021-05-23
You're going to be waiting a while for 5.13 to be available in 20.04 repo. The easiest way to do it is install a 5.13.x kernel from: [https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
(This will not remove or overwrite the regular kernel, so you can fallback to that if 5.13.x doesn't work out.)

---

### Post by airinghouse on 2021-05-27
Update: there weren't any 5.13rc3 kernel amd64 files on the list.  I tried installing 5.13 rc2 (which didn't work properly) and also updating 20.04 to 21.04 (as a "lets just try everything" method) but that didn't solve the problem either..

I'll keep an eye on the 5.13 kernels and try later when there's a stable release.

---

