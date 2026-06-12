---
title: "No audio on Asus EB1501P and XBMC"
date: 2010-11-13
forum: Multimedia Software
---

### Post by greven79 on 2010-11-13
Hi,

I've spent the whole day trying to get xbmc to run on my Asus EB1501P. It seems impossible to get the sound to work.

I've installed ubuntu and xbmc acording to the wiki:

[http://wiki.xbmc.org/index.php?title=HOW-TO_preform_a_Miminal_Ubuntu_and_XBMC_install_on_a_Asus_EeeBox_PC_EB1501](http://wiki.xbmc.org/index.php?title=HOW-TO_preform_a_Miminal_Ubuntu_and_XBMC_install_on_a_Asus_EeeBox_PC_EB1501)

But I can't eaven get analogue audio from the device.

Have anyone succeeded with this ?

I'm almost at the point of giving up and installing win7 instead =/

Thankful for any help.

//Karl

---

### Post by RaZoR1394 on 2010-12-19
Hi

I have exactly the same type of computer. I don't get audio from HDMI myself but the headphone jack works. I haven't tried TOSLINK S/PDIF yet. HDMI audio works with Windows 7. Things I've done:

- Creating an asound.conf according to the XBMC wiki.
- Adding Ubuntu audio dev and updating the system giving me new alsa for example.
- Setting HDMI output as default in audio properties.
- Unmuted S/PDIF 1 on HDA NVIDIA in alsamixer.

The HDMI light lights up on my receiver but not PCM so It's no go.

What more can I do?

edit:

Here is my dmesg stuff regarding hdmi:

```

[   56.913693] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=0
[   56.937705] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=1
[   57.720051] HDMI: detected monitor TX-SR608
[   57.720056]     at connection type HDMI
[   57.720066] HDMI: available speakers: FL/FR LFE FC RL/RR RLC/RRC
[   57.720079] ------------[ cut here ]------------
[   57.720094] WARNING: at /build/buildd/linux-2.6.35/lib/vsprintf.c:1283 vsnprintf+0x416/0x430()
[   57.720102] Hardware name: EB1501P
[   57.720107] Modules linked in: parport_pc ppdev snd_hda_codec_nvhdmi nvidia(P) snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm arc4 snd_seq_midi ath9k ath9k_common ath9k_hw ath snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device mac80211 cfg80211 snd led_class soundcore xhci_hcd psmouse serio_raw snd_page_alloc intel_agp asus_atk0110 uvcvideo videodev v4l1_compat joydev agpgart lp parport usbhid hid usb_storage ahci libahci r8169 mii
[   57.720204] Pid: 891, comm: hd-audio1 Tainted: P            2.6.35-23-generic #41-Ubuntu
[   57.720211] Call Trace:
[   57.720226]  [<c014acf2>] warn_slowpath_common+0x72/0xa0
[   57.720238]  [<c0358e16>] ? vsnprintf+0x416/0x430
[   57.720249]  [<c0358e16>] ? vsnprintf+0x416/0x430
[   57.720261]  [<c014ad42>] warn_slowpath_null+0x22/0x30
[   57.720272]  [<c0358e16>] vsnprintf+0x416/0x430
[   57.720283]  [<c0358eba>] snprintf+0x1a/0x20
[   57.720305]  [<f986666d>] snd_print_pcm_bits+0x5d/0x80 [snd_hda_codec]
[   57.720328]  [<f986f8a7>] hdmi_show_short_audio_desc+0xf7/0x100 [snd_hda_codec]
[   57.720341]  [<c0358eba>] ? snprintf+0x1a/0x20
[   57.720363]  [<f986f90f>] snd_hdmi_show_eld+0x5f/0xa0 [snd_hda_codec]
[   57.720385]  [<f986fcb0>] ? snd_hdmi_get_eld+0xd0/0x100 [snd_hda_codec]
[   57.720408]  [<f986fcb0>] ? snd_hdmi_get_eld+0xd0/0x100 [snd_hda_codec]
[   57.720422]  [<f804764e>] hdmi_present_sense+0x5e/0x70 [snd_hda_codec_nvhdmi]
[   57.720435]  [<f804774d>] hdmi_intrinsic_event+0xed/0x100 [snd_hda_codec_nvhdmi]
[   57.720448]  [<f80477a6>] hdmi_unsol_event+0x46/0x80 [snd_hda_codec_nvhdmi]
[   57.720459]  [<c013eb7d>] ? finish_task_switch+0x3d/0xc0
[   57.720479]  [<f9866106>] process_unsol_events+0x56/0x70 [snd_hda_codec]
[   57.720492]  [<c0161aee>] run_workqueue+0x8e/0x150
[   57.720512]  [<f98660b0>] ? process_unsol_events+0x0/0x70 [snd_hda_codec]
[   57.720549]  [<c0161c34>] worker_thread+0x84/0xe0
[   57.720560]  [<c0165eb0>] ? autoremove_wake_function+0x0/0x50
[   57.720569]  [<c0161bb0>] ? worker_thread+0x0/0xe0
[   57.720578]  [<c0165a84>] kthread+0x74/0x80
[   57.720586]  [<c0165a10>] ? kthread+0x0/0x80
[   57.720595]  [<c010363e>] kernel_thread_helper+0x6/0x10
[   57.720601] ---[ end trace ffb98d8a94079dea ]---
[   57.720608] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200 176400 192000 384000, bits = 16
[   57.720622] HDMI: supports coding type LPCM: channels = 8, rates = 44100 48000 88200 176400 192000 384000, bits = 16
[   57.720633] HDMI: supports coding type AC-3: channels = 8, rates = 44100 48000 88200, max bitrate = 640000
[   57.720643] HDMI: supports coding type DTS: channels = 8, rates = 48000 88200, max bitrate = 1536000
[   57.720651] HDMI: supports coding type DSD (One Bit Audio): channels = 6, rates = 48000
[   57.720659] HDMI: supports coding type E-AC-3/DD+ (Dolby Digital Plus): channels = 8, rates = 48000 88200
[   57.720670] HDMI: supports coding type DTS-HD: channels = 8, rates = 48000 88200 176400 192000 384000
[   57.720679] HDMI: supports coding type MLP (Dolby TrueHD): channels = 8, rates = 88200 192000
[   58.508524] HDMI: detected monitor TX-SR608
[   58.508528]     at connection type HDMI
[   58.508536] HDMI: available speakers: FL/FR LFE FC RL/RR RLC/RRC
[   58.508547] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200 176400 192000 384000, bits = 16
[   58.508557] HDMI: supports coding type LPCM: channels = 8, rates = 44100 48000 88200 176400 192000 384000, bits = 16
[   58.508565] HDMI: supports coding type AC-3: channels = 8, rates = 44100 48000 88200, max bitrate = 640000
[   58.508572] HDMI: supports coding type DTS: channels = 8, rates = 48000 88200, max bitrate = 1536000
[   58.508578] HDMI: supports coding type DSD (One Bit Audio): channels = 6, rates = 48000
[   58.508585] HDMI: supports coding type E-AC-3/DD+ (Dolby Digital Plus): channels = 8, rates = 48000 88200
[   58.508593] HDMI: supports coding type DTS-HD: channels = 8, rates = 48000 88200 176400 192000 384000
[   58.508600] HDMI: supports coding type MLP (Dolby TrueHD): channels = 8, rates = 88200 192000

```

---

### Post by baberone on 2010-12-25
I have an Zotac zBox HD-11 and the same problem (no HDMI sound) on Maverick 10.10


```
[   24.227646] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=0
[   24.252590] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=1
[   25.044040] HDMI: detected monitor PhilipsTV (5 at connection type HDMI
[   25.044052] HDMI: available speakers: FL/FR
[   25.044062] ------------[ cut here ]------------
[   25.044077] WARNING: at lib/vsprintf.c:1283 vsnprintf+0x416/0x430()
[   25.044084] Hardware name: To Be Filled By O.E.M.
[   25.044089] Modules linked in: parport_pc ppdev dm_crypt arc4 nvidia(P) ath9k ath9k_common ath9k_hw ath mac80211 cfg80211 psmouse led_class joydev serio_raw lp parport hid_logitech ff_memless usbhid hid intel_agp r8169 mii agpgart
[   25.044151] Pid: 88, comm: hd-audio1 Tainted: P            2.6.35.8-custom #1
[   25.044158] Call Trace:
[   25.044173]  [<c0149332>] warn_slowpath_common+0x72/0xa0
[   25.044184]  [<c0351c76>] ? vsnprintf+0x416/0x430
[   25.044194]  [<c0351c76>] ? vsnprintf+0x416/0x430
[   25.044205]  [<c0149382>] warn_slowpath_null+0x22/0x30
[   25.044216]  [<c0351c76>] vsnprintf+0x416/0x430
[   25.044227]  [<c0351d1a>] snprintf+0x1a/0x20
[   25.044240]  [<c050413d>] snd_print_pcm_bits+0x5d/0x80
[   25.044252]  [<c050d107>] hdmi_show_short_audio_desc+0xf7/0x100
[   25.044264]  [<c0351d1a>] ? snprintf+0x1a/0x20
[   25.044275]  [<c050d16f>] snd_hdmi_show_eld+0x5f/0xa0
[   25.044287]  [<c034f3c9>] ? strlcpy+0x39/0x50
[   25.044298]  [<c050d47c>] ? snd_hdmi_get_eld+0x29c/0x2d0
[   25.044310]  [<c05328ee>] hdmi_present_sense+0x5e/0x70
[   25.044321]  [<c0532a24>] hdmi_unsol_event+0x124/0x160
[   25.044334]  [<c0503bd6>] process_unsol_events+0x56/0x70
[   25.044348]  [<c015fff2>] worker_thread+0x112/0x220
[   25.044360]  [<c061cbca>] ? schedule+0x37a/0x7a0
[   25.044373]  [<c0503b80>] ? process_unsol_events+0x0/0x70
[   25.044384]  [<c0164280>] ? autoremove_wake_function+0x0/0x50
[   25.044396]  [<c015fee0>] ? worker_thread+0x0/0x220
[   25.044406]  [<c0163e54>] kthread+0x74/0x80
[   25.044416]  [<c0163de0>] ? kthread+0x0/0x80
[   25.044426]  [<c01036fe>] kernel_thread_helper+0x6/0x10
[   25.044433] ---[ end trace 79c37b04e27021ae ]---
[   25.044441] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200, bits = 16
[   25.822348] HDMI: detected monitor PhilipsTV (5 at connection type HDMI
[   25.822362] HDMI: available speakers: FL/FR
[   25.822375] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200, bits = 16
```

nVidia drivers: version 260.19.29
Kernel: 2.6.35.8-custom (recompiled to have OSS support)

So I think it is not related to XBMC or your Asus mobo, but more generally about Alsa/NVidia drivers and software.

---

### Post by RaZoR1394 on 2010-12-26
I believe it has something to do with alsa...

nVidia drivers however don't handle audio on Linux they only handle video. Audio is left for alsa to handle.

I managed to get audio by using speakertest. I got this far on my htpc, next step I got sound from chromium+youtube but after that I surrendered. I never got Gnome audio to work.

Now I'm trying on my EB1501P.

> 
$ aplay -l
**** Lista över PLAYBACK hårdvaruenheter ****
kort 0: Intel [HDA Intel], enhet 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
kort 0: Intel [HDA Intel], enhet 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
kort 1: NVidia [HDA NVidia], enhet 3: NVIDIA HDMI [NVIDIA HDMI]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
kort 1: NVidia [HDA NVidia], enhet 7: NVIDIA HDMI [NVIDIA HDMI]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
kort 1: NVidia [HDA NVidia], enhet 8: NVIDIA HDMI [NVIDIA HDMI]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
kort 1: NVidia [HDA NVidia], enhet 9: NVIDIA HDMI [NVIDIA HDMI]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0


> 
~$ speaker-test -D plughw:1,7 -r 44100

speaker-test 1.0.23

Uppspelningsenhet är plughw:1,7
Strömparametrar är 44100 Hz, S16_LE, 1 kanaler
Använder 16-oktavers rosa brus
Frekvensen inställd till 44100 Hz (begärde 44100 Hz)
Buffertstorleken varierar från 64 till 1048576
Periodstorleken varierar från 32 till 524288
Använder maximal buffertstorlek 1048576
Perioder = 4
tidigare inställd period_size = 262144
tidigare inställd buffer_size = 1048576
 0 - Vänster fram
Tid per period = 6,030939
 0 - Vänster fram


Speaker test produces noise through the speakers with hdmi and pcm indicator lights up.

So if you get noise by using speakertest you are close.

1,7 is the same as "s/pdif 1" in "alsamixer -c1".

---

### Post by baberone on 2010-12-27
I managed to get audio on HDMI ! My girlfriend is already enjoying!

But to have it working I've compiled a 2.6.37 kernel (rc-7). (I followed [this tuto]("http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/"), but with newer kernel)

Kernel:
```
sudo wget http://www.kernel.org/pub/linux/kernel/v2.6/testing/linux-2.6.37-rc7.tar.bz2
```


I've changed a couple of things in the .config file (the one you should have copied from /boot for your current working kernel) Since OSS support in Ubuntu is being removed, I added those modules to the kernel (to get alsamixer working)


```
CONFIG_SOUND=y
CONFIG_SOUND_OSS_CORE=y
CONFIG_SOUND_OSS_CORE_PRECLAIM=y
CONFIG_SND=y
CONFIG_SND_TIMER=y
CONFIG_SND_PCM=y
CONFIG_SND_HWDEP=m
CONFIG_SND_RAWMIDI=m
CONFIG_SND_JACK=y
CONFIG_SND_SEQUENCER=m
CONFIG_SND_SEQ_DUMMY=m
CONFIG_SND_OSSEMUL=y
CONFIG_SND_MIXER_OSS=y
CONFIG_SND_PCM_OSS=y
CONFIG_SND_PCM_OSS_PLUGINS=y
```

Compile the kernel (this will take some time, especialy if not stripped down to minimal needs)


```

make-kpkg clean

//make sure we set new config options, a lot of ENTERs
make oldconfig

set CONCURRENCY=3
fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel-headers

dpkg -i linux-headers-2.6.37-rc7-custom_2.6.37-rc7-custom-10.00.Custom_i386.deb
dpkg -i linux-image-2.6.37-rc7-custom_2.6.37-rc7-custom-10.00.Custom_i386.deb

sudo reboot
```


Gnome sound working, also in VLC but not in some other apps (Media Player) and nVidia drivers too (propietary drivers)

---

### Post by RaZoR1394 on 2010-12-28
Yay. I got sound from Gnome.

First of all you can reach the NVidia HDMI S/PDIF settings by writing

```

alsamixer -c1

```

in a terminal as the NVidia HDMI chip is usually on card 1. The IEC958 is on card 0.

You don't need to upgrade the kernel for that.

Also when upgrading the kernel you can just install an appropriate 2.6.37 .deb from Ubuntu kernel mainline ppa.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

So I now tried the procedure from here (ION2)

[http://wiki.xbmc.org/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210%2C_GT220%2C_or_GT240](http://wiki.xbmc.org/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210%2C_GT220%2C_or_GT240)

I lost sound totally after doing all three stages but I now noticed that the hdmi light wasn't constantly lit up but it flickered when the computer was sending sound to the receiver.

So I added this as described by the wiki to /etc/asound.conf

```

pcm.!default hdmi:NVidia
pcm:iec958 hdmi:NVidia

```

That didn't help so I removed all other hacks except that and now when I logged in I got sound from Gnome. I also get sound from Grooveshark in Chromium.

I'm currently on the latest official 2.6.35 Maverick kernel with the latest audio stuff from the Ubuntu audio dev ppa but I'm not sure if the ppa stuff is really needed.

However just like you I'm not getting sound from some media players but I think this is easily fixed by entering a custom output.

---

### Post by baberone on 2010-12-29
I had some problems with the Ubuntu kernel mainline ppa. It seems to be compiled with gcc 4.2 but I've only gcc 4.4 installed and this was causing me some issues when trying to compile and install the latest NVidia drivers from NVidia (and not from ubuntu's repo's). 

Anyhow, thanks for sharing this! I feel a bit less a linux noob :)

---

### Post by lidex on 2010-12-29
Have a look here:
[http://ubuntuforums.org/showthread.php?t=1532355](http://ubuntuforums.org/showthread.php?t=1532355)
[http://ubuntuforums.org/showthread.php?t=1552250](http://ubuntuforums.org/showthread.php?t=1552250)

---

### Post by RaZoR1394 on 2010-12-29
> **baberone said:**
> I had some problems with the Ubuntu kernel mainline ppa. It seems to be compiled with gcc 4.2 but I've only gcc 4.4 installed and this was causing me some issues when trying to compile and install the latest NVidia drivers from NVidia (and not from ubuntu's repo's). 

Anyhow, thanks for sharing this! I feel a bit less a linux noob :)

You can install the latest NVidia driver from the X-swat ppa.

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

I noticed what seems to be wrong with my configuration. I can only get sound from one application at once. If I exit Chromium sounds starts playing out of Banshee for ex. But for now getting sound out of Chromium I'm ok with it. I'll keep on working.

---

### Post by RaZoR1394 on 2011-01-12
I found a better solution that works on this machine but also my two towers with gtx460. The only downside is that all audio chips except hdmi stops working. In my case it doesn't matter so much. The only thing I miss is the mic jack.

[http://forum.xbmc.org/showthread.php?t=85078](http://forum.xbmc.org/showthread.php?t=85078)

In my case I did:

```

sudo rmmod snd_hda_intel
sudo modprobe snd_hda_intel enable_msi=0 probe_mask=0x102
echo "options snd-hda-intel enable_msi=0 probe_mask=0x102" | sudo tee /etc/modprobe.d/nvidia-hdmi.conf

```

As my receiver was on /proc/asound/card1/eld#1.0 I choose 0x102.

---

