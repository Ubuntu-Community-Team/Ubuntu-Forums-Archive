---
title: "Ubuntu server sound problem"
date: 2008-09-01
forum: Multimedia Software
---

### Post by unbkbl on 2008-09-01
I've installed Ubuntu server because i don't really like gnome (too heavy for my 512 Mg in RAM) and I'm trying Enlightenment e17 (really beautiful).
I tried to manually install sound like this:

```
apt-get install alsa-base alsa-utils alsa-tools libasound2
```
But it doesn't work. I've turned up the volume in the alsamixer... and nothing

so..

My lspi output is this:

```

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:06.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
06:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:09.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
daniel@lab:~$ 
```
My aplay -l output is this:

```
daniel@lab:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

My lspci -v output is this:

```
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 3080
        Flags: bus master, medium devsel, latency 0, IRQ 22
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at b0040800 (32-bit, non-prefetchable) [size=512]
        Memory at b0040400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2
```

I have done the procedure in the first code tag installing sound in Debian a few days ago it and worked!

Any Ideas?
:confused:

---

### Post by minky311 on 2008-09-01
I would make sure everything in System->Preferences->Sound is set to ALSA.
Then I would press alt f2 and type in gstreamer-properties once there try different devices and see if any of them work.

---

### Post by unbkbl on 2008-09-01
the problem is that i don't have gnome, and my distro is "Ubuntu server", so, i don't have a System->Preferences->Sound menu.
I've installed my window manager manually (I'm using enlightenment e17)
how can i do that in console?

---

### Post by cariboo on 2008-09-01
Make sure the sound modules for your card are loaded, type:

```
lsmod | grep snd
```

This will show a listing of all the loaded sound modules eg:

```
lsmod | grep snd
snd_ens1371            27168  2 
gameport               16008  1 snd_ens1371
snd_ac97_codec        101028  1 snd_ens1371
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  4 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  2 snd_ens1371,snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  3 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  13 snd_ens1371,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  1 snd_pcm
```



Have you setup your card with asoundconf? In a terminal type:

```
asoundconf list
```

Add the output to:

```
asoundconf set-default-card PARAMETER
```

Where PARAMETER is your sound card from the previous commad.

I've tried this with 4 different sound cards i defective 2 distorted sound and an old soundblaster that works properly all of them worked except for the dead card.

Jim

---

### Post by unbkbl on 2008-09-01
Hi Jim
I did it just as you said and still, i haven't heard a sound :(

```
snd_seq_dummy           4868  0 
snd_seq_oss            35456  0 
snd_seq_midi            9248  0 
snd_rawmidi            25632  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54096  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_pcm_oss            42016  0 
snd_mixer_oss          17792  1 snd_pcm_oss
snd_intel8x0           35356  0 
snd_ac97_codec        100772  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm                78596  3 snd_pcm_oss,snd_intel8x0,snd_ac97_codec
snd_page_alloc         11528  2 snd_intel8x0,snd_pcm
snd_timer              24836  2 snd_seq,snd_pcm
snd                    56868  11 snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_timer
soundcore               8800  1 snd
```

```

daniel@lab:/var$ asoundconf list
Names of available sound cards:
ICH6
```

```
asoundconf set-default-card ICH6
daniel@lab:/var$ 
```

but when i do this...
```
root@lab:~# alsa reload
Unloading ALSA sound driver modules: snd-intel8x0 snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-intel8x0 snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
```

it sounds like speaker turning on... and after that, not a sound

Any other idea?

Thnx for your time an attention, 

Daniel

---

### Post by jp.hendrix on 2010-05-02
Me too is trying to get sound working on Ubuntu server. Previously on 9.10 but now on 10.4 Lucid and I am running it from Virtualbox. Full desktop distributions work fine, but they are way too bulky.

I followed [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) but so far no success.

At the moment I am trying to get sound output with the:
eplay /usr/share/sounds/alsa/Front_Center.wav
But although I am not receiving any errors, I hear no sound from the speakers too :(

Eventually I want to run a skype client from the ubuntu server, thus the mic should also work. I know it can be done because I have a destop virtual machine that does precisely this. I just want to cut on the overhead.

---

### Post by jp.hendrix on 2010-05-02
I found a solution here: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Use "M" in alsamixer to unmute the correct channels.

hope this helps!

---

