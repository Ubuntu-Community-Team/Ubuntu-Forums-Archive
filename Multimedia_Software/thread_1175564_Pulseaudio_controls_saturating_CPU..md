---
title: "Pulseaudio controls saturating CPU."
date: 2009-06-01
forum: Multimedia Software
---

### Post by Omnutia on 2009-06-01
I'm using 9.04 on my laptop (HP NX6325) which has an "HDA ATI SB - AD198x" sound chipset. I also have an Terratec Aureon 5.1 mk.2 USB soundcard which I use to hook up to my speakers.

The problem I've run into seems to strike whenever I open a program which controls Pulseaudio, my processor is filled with IOwait cycles and the program, such as Pulseaudio volume control (pavucontrol), loads and runs incredibly slowly.

Problems occurs with or without the USB soundcard attached, I'm going to test to see if it occurs with the LiveCD as it could be a configuration file left over from the upgrade.

Below is the output of the user.log.

Can anyone tell me what to do to make it stop?


```
May 29 21:04:43 Panza-Panda pulseaudio[3398]: alsa-util.c: Device front:3 doesn't support 44100 Hz, changed to 48000 Hz.
May 29 21:04:43 Panza-Panda pulseaudio[3398]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.
May 29 21:04:43 Panza-Panda pulseaudio[3398]: alsa-util.c: Device hw:2 doesn't support 44100 Hz, changed to 16000 Hz.
May 29 21:04:43 Panza-Panda pulseaudio[3398]: alsa-util.c: Device hw:2 doesn't support 2 channels, changed to 1.
May 29 21:04:43 Panza-Panda pulseaudio[3398]: module-alsa-source.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
May 29 21:04:43 Panza-Panda pulseaudio[3398]: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.
May 29 21:04:43 Panza-Panda pulseaudio[3398]: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.
May 29 23:07:49 Panza-Panda pulseaudio[3405]: alsa-util.c: Device front:3 doesn't support 44100 Hz, changed to 48000 Hz.
May 29 23:07:49 Panza-Panda pulseaudio[3405]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.
May 29 23:07:49 Panza-Panda pulseaudio[3405]: alsa-util.c: Device hw:2 doesn't support 44100 Hz, changed to 16000 Hz.
May 29 23:07:49 Panza-Panda pulseaudio[3405]: alsa-util.c: Device hw:2 doesn't support 2 channels, changed to 1.
May 29 23:07:49 Panza-Panda pulseaudio[3405]: module-alsa-source.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
May 29 23:07:49 Panza-Panda pulseaudio[3405]: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.
May 29 23:07:49 Panza-Panda pulseaudio[3405]: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.
May 30 10:42:34 Panza-Panda pulseaudio[3398]: alsa-util.c: Device front:3 doesn't support 44100 Hz, changed to 48000 Hz.
May 30 10:42:34 Panza-Panda pulseaudio[3398]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.
May 30 10:42:34 Panza-Panda pulseaudio[3398]: alsa-util.c: Device hw:2 doesn't support 44100 Hz, changed to 16000 Hz.
May 30 10:42:34 Panza-Panda pulseaudio[3398]: alsa-util.c: Device hw:2 doesn't support 2 channels, changed to 1.
May 30 10:42:34 Panza-Panda pulseaudio[3398]: module-alsa-source.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
May 30 10:42:34 Panza-Panda pulseaudio[3398]: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.
May 30 10:42:34 Panza-Panda pulseaudio[3398]: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.
May 30 18:01:14 Panza-Panda pulseaudio[3456]: alsa-util.c: Device front:3 doesn't support 44100 Hz, changed to 48000 Hz.
May 30 18:01:14 Panza-Panda pulseaudio[3456]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.
May 30 18:01:14 Panza-Panda pulseaudio[3456]: alsa-util.c: Device hw:2 doesn't support 44100 Hz, changed to 16000 Hz.
May 30 18:01:14 Panza-Panda pulseaudio[3456]: alsa-util.c: Device hw:2 doesn't support 2 channels, changed to 1.
May 30 18:01:14 Panza-Panda pulseaudio[3456]: module-alsa-source.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
May 30 18:01:14 Panza-Panda pulseaudio[3456]: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.
May 30 18:01:14 Panza-Panda pulseaudio[3456]: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.
May 31 11:36:58 Panza-Panda pulseaudio[3393]: alsa-util.c: Device front:3 doesn't support 44100 Hz, changed to 48000 Hz.
May 31 11:36:58 Panza-Panda pulseaudio[3393]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.
May 31 11:36:58 Panza-Panda pulseaudio[3393]: alsa-util.c: Device hw:2 doesn't support 44100 Hz, changed to 16000 Hz.
May 31 11:36:58 Panza-Panda pulseaudio[3393]: alsa-util.c: Device hw:2 doesn't support 2 channels, changed to 1.
May 31 11:36:58 Panza-Panda pulseaudio[3393]: module-alsa-source.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
May 31 11:36:58 Panza-Panda pulseaudio[3393]: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.
May 31 11:36:58 Panza-Panda pulseaudio[3393]: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.
May 31 14:16:44 Panza-Panda pulseaudio[3393]: module-alsa-sink.c: Error opening PCM device front:1: Device or resource busy
May 31 14:21:45 Panza-Panda pulseaudio[3393]: module-alsa-sink.c: Error opening PCM device front:1: Device or resource busy
May 31 15:13:36 Panza-Panda pulseaudio[3393]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 16000 Hz.
May 31 15:13:36 Panza-Panda pulseaudio[3393]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
May 31 15:13:36 Panza-Panda pulseaudio[3393]: module-alsa-source.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
May 31 15:28:34 Panza-Panda pulseaudio[3179]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 16000 Hz.
May 31 15:28:34 Panza-Panda pulseaudio[3179]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
May 31 15:28:34 Panza-Panda pulseaudio[3179]: module-alsa-source.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
May 31 15:33:59 Panza-Panda pulseaudio[3179]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 16000 Hz.
May 31 15:33:59 Panza-Panda pulseaudio[3179]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
May 31 15:33:59 Panza-Panda pulseaudio[3179]: module-alsa-source.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
May 31 15:35:49 Panza-Panda pulseaudio[3179]: sound-file.c: Failed to open file /usr/share/sounds/ubuntu/stereo/window-slide.ogg
May 31 15:35:52 Panza-Panda last message repeated 2 times
May 31 15:36:43 Panza-Panda pulseaudio[3179]: sound-file.c: Failed to open file /usr/share/sounds/ubuntu/stereo/window-slide.ogg
May 31 15:42:30 Panza-Panda pulseaudio[3179]: module-rescue-streams.c: Failed to move source output 8 "PulseAudio Volume Control" to alsa_input.pci_1002_437b_sound_card_0_alsa_capture_0.
May 31 15:47:51 Panza-Panda pulseaudio[3179]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 16000 Hz.
May 31 15:47:51 Panza-Panda pulseaudio[3179]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
May 31 15:47:51 Panza-Panda pulseaudio[3179]: module-alsa-source.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
May 31 20:22:41 Panza-Panda pulseaudio[3407]: alsa-util.c: Device front:3 doesn't support 44100 Hz, changed to 48000 Hz.
May 31 20:22:41 Panza-Panda pulseaudio[3407]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.
May 31 20:22:41 Panza-Panda pulseaudio[3407]: alsa-util.c: Device hw:2 doesn't support 44100 Hz, changed to 16000 Hz.
May 31 20:22:41 Panza-Panda pulseaudio[3407]: alsa-util.c: Device hw:2 doesn't support 2 channels, changed to 1.
May 31 20:22:41 Panza-Panda pulseaudio[3407]: module-alsa-source.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
May 31 20:22:41 Panza-Panda pulseaudio[3407]: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.
May 31 20:22:41 Panza-Panda pulseaudio[3407]: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.
May 31 21:14:03 Panza-Panda pulseaudio[3407]: module-alsa-source.c: snd_pcm_mmap_commit: Device or resource busy
May 31 21:14:03 Panza-Panda pulseaudio[3407]: module-rescue-streams.c: Failed to move source output 30 "PulseAudio Volume Control" to alsa_input.usb_device_5e1_408_noserial_if1_sound_card_0_alsa_capture_0.
Jun  1 08:58:02 Panza-Panda pulseaudio[3401]: alsa-util.c: Device front:3 doesn't support 44100 Hz, changed to 48000 Hz.
Jun  1 08:58:02 Panza-Panda pulseaudio[3401]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.
Jun  1 08:58:02 Panza-Panda pulseaudio[3401]: alsa-util.c: Device hw:2 doesn't support 44100 Hz, changed to 16000 Hz.
Jun  1 08:58:02 Panza-Panda pulseaudio[3401]: alsa-util.c: Device hw:2 doesn't support 2 channels, changed to 1.
Jun  1 08:58:02 Panza-Panda pulseaudio[3401]: module-alsa-source.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
Jun  1 08:58:02 Panza-Panda pulseaudio[3401]: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.
Jun  1 08:58:02 Panza-Panda pulseaudio[3401]: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.
Jun  1 14:17:36 Panza-Panda pulseaudio[3386]: alsa-util.c: Device front:3 doesn't support 44100 Hz, changed to 48000 Hz.
Jun  1 14:17:36 Panza-Panda pulseaudio[3386]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.
Jun  1 14:17:36 Panza-Panda pulseaudio[3386]: alsa-util.c: Device hw:2 doesn't support 44100 Hz, changed to 16000 Hz.
Jun  1 14:17:36 Panza-Panda pulseaudio[3386]: alsa-util.c: Device hw:2 doesn't support 2 channels, changed to 1.
Jun  1 14:17:36 Panza-Panda pulseaudio[3386]: module-alsa-source.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
Jun  1 14:17:36 Panza-Panda pulseaudio[3386]: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.
Jun  1 14:17:36 Panza-Panda pulseaudio[3386]: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.
Jun  1 14:22:19 Panza-Panda pulseaudio[3386]: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.
Jun  1 14:22:19 Panza-Panda pulseaudio[3386]: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.
Jun  1 14:41:52 Panza-Panda pulseaudio[3387]: alsa-util.c: Device front:3 doesn't support 44100 Hz, changed to 48000 Hz.
Jun  1 14:41:52 Panza-Panda pulseaudio[3387]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.
Jun  1 14:41:52 Panza-Panda pulseaudio[3387]: alsa-util.c: Device hw:2 doesn't support 44100 Hz, changed to 16000 Hz.
Jun  1 14:41:52 Panza-Panda pulseaudio[3387]: alsa-util.c: Device hw:2 doesn't support 2 channels, changed to 1.
Jun  1 14:41:52 Panza-Panda pulseaudio[3387]: module-alsa-source.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
Jun  1 14:41:52 Panza-Panda pulseaudio[3387]: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.
Jun  1 14:41:52 Panza-Panda pulseaudio[3387]: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.
Jun  1 14:43:57 Panza-Panda pulseaudio[3387]: cpulimit.c: Received request to terminate due to CPU overload.

```

---

### Post by screig on 2009-06-02
mine has the same cr*p

---

### Post by gcastro on 2009-06-06
I had the same problem (amd64) followed the instructions in:
[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384) and then 
[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

Now it works fine but some applications still would not work.
Skype, wine, flashplugin-installer, googleearth.

Hope it helps

---

### Post by Omnutia on 2009-07-14
For anyone else afflicted by this, I have found a workaround.
This is an alternate method for changing the sound card without having to go through pavcontrol.

1) Open up the padevchooser menu.
2) Open up "Manager.."
3) Go to the "Devices" tab.
4) Find your desired output device.
5) Highlight -> Properties.
6) Highlight and copy the whole "Name:" entry. In my case: ```
alsa_output.usb_device_ccd_28_noserial_if0_sound_card_0_alsa_playback_0_0
```
7) Go back to the padevchooser menu.
8 ) Go into the "Default sink" sub-menu.
9) Click on "Other..".
10) Paste the text you got in step 6 and click ok.
11) Close and re-open the program and you should get sound coming out of the right soundcard!

Does this work for anyone else?

---

