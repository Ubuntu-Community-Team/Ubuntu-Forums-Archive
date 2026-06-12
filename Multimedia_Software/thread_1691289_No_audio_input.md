---
title: "No audio input"
date: 2011-02-19
forum: Multimedia Software
---

### Post by OhHamburgers on 2011-02-19
Hey Everyone,  

I have been using Ubuntu 10.10 for a bit now and I am having trouble getting a microphone to show up in the input tab in sound preferences.  I have gone into alsamixer and enabled the mic and set it to the front mic jack but nothing shows up.  Are there any other recomendations on how to get this to work?  Oh by the way it is a gaming headset that has 2 split plugs for audio and mic.  I am only using the mic jack if that makes any difference.

Thnaks!

---

### Post by OhHamburgers on 2011-02-19
Update and kind of a bump I guess.

Using Audacity I got the mic to work by changing the default recording device to HDA ATI SB: VT1708S Analog (hw0,0)

Is there any config file that I can add that to so that it will get picked up by PulseAudio?

---

### Post by OhHamburgers on 2011-03-03
Anyone?

---

### Post by redradish on 2011-03-03
Hey, I'm having a similar problem... been trawling the web trying to figure it out, still haven't really got anywhere! What audio chipset do you have? Have you tried installing 'pavucontrol' and fiddling with the levels there? A common things is to turn the 'Front Right' channel down to 0%, and the 'Front Left' up to 100%. Also depending on your model, adding a line to /etc/modprobe.d/alsa-base.conf might do the trick. Otherwise you could try installing linux-backports-modules-alsa-maverick-generic, or updating alsa via a ppa, or any combination thereof :P 

Take a look at 
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1661716](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1661716)
Should ask lidex to help us out

---

### Post by lidex on 2011-03-04
Post your info so I can see what we're working with. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by OhHamburgers on 2011-03-04
[http://www.alsa-project.org/db/?f=b9acde4be46abfdcb9a4b180159577ee24b1cde3](http://www.alsa-project.org/db/?f=b9acde4be46abfdcb9a4b180159577ee24b1cde3)

Is that what you were looking for?

---

### Post by lidex on 2011-03-06
Yep. Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=auto" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**
Then show us what pulse is up to:
```
pkill pulseaudio; sleep 2; pulseaudio -vv
```

---

### Post by OhHamburgers on 2011-03-07
Alright this is what I get after the reboot:
[PHP]I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying iec958:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:iec958:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:iec958:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:iec958-surround-40+input:analog-mono
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying iec958:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:iec958:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:iec958:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:iec958-surround-40+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying iec958:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:iec958:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:iec958:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:iec958-surround-40+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying iec958:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:iec958:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:iec958:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:iec958-surround-40+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying iec958:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: alsa-util.c: Trying plug:iec958:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:iec958:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:iec958:0: Invalid argument
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40+input:analog-mono
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51
D: alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51+input:analog-mono
D: alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:hdmi-stereo
D: alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
D: alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D3p' failed (-2)
I: alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:hdmi-stereo+input:analog-mono
D: alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
D: alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D3p' failed (-2)
I: alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:hdmi-stereo+input:analog-stereo
D: alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
D: alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D3p' failed (-2)
I: alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:hdmi-stereo+input:iec958-stereo
D: alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
D: alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D3p' failed (-2)
I: alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
D: alsa-mixer.c: Looking at profile output:hdmi-stereo+input:iec958-surround-40
D: alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
D: alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D3p' failed (-2)
I: alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
D: alsa-mixer.c: Looking at profile input:analog-mono
D: alsa-mixer.c: Checking for recording on Analog Mono (analog-mono)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-mixer.c: Looking at profile input:analog-stereo
D: alsa-mixer.c: Checking for recording on Analog Stereo (analog-stereo)
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open front:0
D: alsa-util.c: Maximum hw buffer size is 23777 ms
D: alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
D: alsa-mixer.c: Profile input:analog-stereo supported.
D: alsa-mixer.c: Looking at profile input:iec958-stereo
D: alsa-mixer.c: Checking for recording on Digital Stereo (IEC958) (iec958-stereo)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D1c' failed (-2)
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-mixer.c: Looking at profile input:iec958-surround-40
D: alsa-mixer.c: Checking for recording on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D1c' failed (-2)
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
I: module-card-restore.c: Restoring profile for card alsa_card.pci-0000_00_14.2.
I: card.c: Created 1 "alsa_card.pci-0000_00_14.2"
D: reserve-wrap.c: Successfully create reservation lock monitor for device 'Audio0'
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open surround71:0
D: alsa-util.c: Maximum hw buffer size is 5944 ms
D: alsa-util.c: Set buffer size first (to 88200 samples), period size second (to 88200 samples).
I: alsa-sink.c: Successfully opened device surround71:0.
I: alsa-sink.c: Selected mapping 'Analog Surround 7.1' (analog-surround-71).
I: alsa-sink.c: Successfully enabled mmap() mode.
I: alsa-sink.c: Successfully enabled timer-based scheduling mode.
I: (alsa-lib)control.c: Invalid CTL surround71:0
I: alsa-mixer.c: Unable to attach to mixer surround71:0: No such file or directory
I: alsa-mixer.c: Successfully attached to mixer 'hw:0'
D: alsa-mixer.c: Probing path 'analog-output'
D: alsa-mixer.c: Probing path 'analog-output-speaker'
D: alsa-mixer.c: Probe of element 'Speaker' failed.
D: alsa-mixer.c: Probing path 'analog-output-speaker'
D: alsa-mixer.c: Probe of element 'Desktop Speaker' failed.
D: alsa-mixer.c: Probing path 'analog-output-lfe-on-mono'
D: alsa-mixer.c: Probe of element 'Master Mono' failed.
D: alsa-sink.c: Probed mixer paths:
D: alsa-mixer.c: Path Set 0x1b923e0, direction=1, probed=yes
D: alsa-mixer.c: Path analog-output (Analog Output), direction=1, priority=99, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=31, min_dB=-148.5, max_dB=12
D: alsa-mixer.c: Element Master Front, direction=1, switch=1, volume=1, enumeration=0, required=0, required_absent=0, mask=0x4028000000000006, n_channels=2, override_map=yes
D: alsa-mixer.c: Element Headphone, direction=1, switch=1, volume=3, enumeration=0, required=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
D: alsa-mixer.c: Element Front, direction=1, switch=1, volume=1, enumeration=0, required=0, required_absent=0, mask=0x6, n_channels=2, override_map=yes
D: alsa-mixer.c: Element Surround, direction=1, switch=1, volume=1, enumeration=0, required=0, required_absent=0, mask=0x60, n_channels=2, override_map=yes
D: alsa-mixer.c: Element Side, direction=1, switch=1, volume=1, enumeration=0, required=0, required_absent=0, mask=0xc00, n_channels=2, override_map=yes
D: alsa-mixer.c: Element Center, direction=1, switch=1, volume=1, enumeration=0, required=0, required_absent=0, mask=0x4900000000018, n_channels=1, override_map=yes
D: alsa-mixer.c: Element LFE, direction=1, switch=1, volume=1, enumeration=0, required=0, required_absent=0, mask=0x80, n_channels=1, override_map=yes
D: alsa-mixer.c: Element PCM, direction=1, switch=0, volume=1, enumeration=0, required=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
D: core-subscribe.c: Dropped redundant event due to change event.
I: module-device-restore.c: Restoring volume for sink alsa_output.pci-0000_00_14.2.analog-surround-71.
I: module-device-restore.c: Restoring mute state for sink alsa_output.pci-0000_00_14.2.analog-surround-71.
I: sink.c: Created sink 1 "alsa_output.pci-0000_00_14.2.analog-surround-71" with sample spec s16le 8ch 44100Hz and channel map front-left,front-right,rear-left,rear-right,front-center,lfe,side-left,side-right
I: sink.c:     alsa.resolution_bits = "16"
I: sink.c:     device.api = "alsa"
I: sink.c:     device.class = "sound"
I: sink.c:     alsa.class = "generic"
I: sink.c:     alsa.subclass = "generic-mix"
I: sink.c:     alsa.name = "VT1708S Analog"
I: sink.c:     alsa.id = "VT1708S Analog"
I: sink.c:     alsa.subdevice = "0"
I: sink.c:     alsa.subdevice_name = "subdevice #0"
I: sink.c:     alsa.device = "0"
I: sink.c:     alsa.card = "0"
I: sink.c:     alsa.card_name = "HDA ATI SB"
I: sink.c:     alsa.long_card_name = "HDA ATI SB at 0xfb2f4000 irq 16"
I: sink.c:     alsa.driver_name = "snd_hda_intel"
I: sink.c:     device.bus_path = "pci-0000:00:14.2"
I: sink.c:     sysfs.path = "/devices/pci0000:00/0000:00:14.2/sound/card0"
I: sink.c:     device.bus = "pci"
I: sink.c:     device.vendor.id = "1002"
I: sink.c:     device.vendor.name = "ATI Technologies Inc"
I: sink.c:     device.product.id = "4383"
I: sink.c:     device.product.name = "SBx00 Azalia (Intel HDA)"
I: sink.c:     device.form_factor = "internal"
I: sink.c:     device.string = "surround71:0"
I: sink.c:     device.buffering.buffer_size = "1411200"
I: sink.c:     device.buffering.fragment_size = "470400"
I: sink.c:     device.access_mode = "mmap+timer"
I: sink.c:     device.profile.name = "analog-surround-71"
I: sink.c:     device.profile.description = "Analog Surround 7.1"
I: sink.c:     device.description = "Internal Audio Analog Surround 7.1"
I: sink.c:     alsa.mixer_name = "VIA VT1708S"
I: sink.c:     alsa.components = "HDA:11060397,1043836c,00100000"
I: sink.c:     module-udev-detect.discovered = "1"
I: sink.c:     device.icon_name = "audio-card-pci"
D: core-subscribe.c: Dropped redundant event due to change event.
I: module-device-restore.c: Restoring volume for source alsa_output.pci-0000_00_14.2.analog-surround-71.monitor.
I: module-device-restore.c: Restoring mute state for source alsa_output.pci-0000_00_14.2.analog-surround-71.monitor.
I: source.c: Created source 1 "alsa_output.pci-0000_00_14.2.analog-surround-71.monitor" with sample spec s16le 8ch 44100Hz and channel map front-left,front-right,rear-left,rear-right,front-center,lfe,side-left,side-right
I: source.c:     device.description = "Monitor of Internal Audio Analog Surround 7.1"
I: source.c:     device.class = "monitor"
I: source.c:     alsa.card = "0"
I: source.c:     alsa.card_name = "HDA ATI SB"
I: source.c:     alsa.long_card_name = "HDA ATI SB at 0xfb2f4000 irq 16"
I: source.c:     alsa.driver_name = "snd_hda_intel"
I: source.c:     device.bus_path = "pci-0000:00:14.2"
I: source.c:     sysfs.path = "/devices/pci0000:00/0000:00:14.2/sound/card0"
I: source.c:     device.bus = "pci"
I: source.c:     device.vendor.id = "1002"
I: source.c:     device.vendor.name = "ATI Technologies Inc"
I: source.c:     device.product.id = "4383"
I: source.c:     device.product.name = "SBx00 Azalia (Intel HDA)"
I: source.c:     device.form_factor = "internal"
I: source.c:     device.string = "0"
I: source.c:     module-udev-detect.discovered = "1"
I: source.c:     device.icon_name = "audio-card-pci"
I: alsa-sink.c: Using 3.0 fragments of size 470400 bytes (666.67ms), buffer size is 1411200 bytes (2000.00ms)
I: alsa-sink.c: Time scheduling watermark is 20.00ms
D: alsa-sink.c: hwbuf_unused=0
D: alsa-sink.c: setting avail_min=87319
D: alsa-mixer.c: Activating path analog-output
D: alsa-mixer.c: Path analog-output (Analog Output), direction=1, priority=99, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=31, min_dB=-148.5, max_dB=12
D: alsa-mixer.c: Element Master Front, direction=1, switch=1, volume=1, enumeration=0, required=0, required_absent=0, mask=0x4028000000000006, n_channels=2, override_map=yes
D: alsa-mixer.c: Element Headphone, direction=1, switch=1, volume=3, enumeration=0, required=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
D: alsa-mixer.c: Element Front, direction=1, switch=1, volume=1, enumeration=0, required=0, required_absent=0, mask=0x6, n_channels=2, override_map=yes
D: alsa-mixer.c: Element Surround, direction=1, switch=1, volume=1, enumeration=0, required=0, required_absent=0, mask=0x60, n_channels=2, override_map=yes
D: alsa-mixer.c: Element Side, direction=1, switch=1, volume=1, enumeration=0, required=0, required_absent=0, mask=0xc00, n_channels=2, override_map=yes
D: alsa-mixer.c: Element Center, direction=1, switch=1, volume=1, enumeration=0, required=0, required_absent=0, mask=0x4900000000018, n_channels=1, override_map=yes
D: alsa-mixer.c: Element LFE, direction=1, switch=1, volume=1, enumeration=0, required=0, required_absent=0, mask=0x80, n_channels=1, override_map=yes
D: alsa-mixer.c: Element PCM, direction=1, switch=0, volume=1, enumeration=0, required=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
I: alsa-sink.c: Hardware volume ranges from -148.50 dB to 12.00 dB.
I: alsa-sink.c: Fixing base volume to -12.00 dB
I: alsa-sink.c: Using hardware volume control. Hardware dB scale supported.
I: alsa-sink.c: Using hardware mute control.
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Soft volume PCM
D: alsa-util.c: Control: PCM Playback Volume
D: alsa-util.c: min_dB: -51
D: alsa-util.c: max_dB: 0
D: alsa-util.c: resolution: 256
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : PLAYBACK
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 8
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 88200
D: alsa-util.c:   period_size  : 29400
D: alsa-util.c:   period_time  : 666666
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 87319
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 6206523236469964800
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 6206523236469964800
D: alsa-util.c: Slave: Hardware PCM card 0 'HDA ATI SB' device 0 subdevice 0
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : PLAYBACK
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 8
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 88200
D: alsa-util.c:   period_size  : 29400
D: alsa-util.c:   period_time  : 666666
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 87319
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 6206523236469964800
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 6206523236469964800
D: alsa-util.c:   appl_ptr     : 0
D: alsa-util.c:   hw_ptr       : 0
D: alsa-sink.c: Thread starting up
D: alsa-sink.c: Requested volume: 0:  75% 1:  75% 2:  75% 3:  75% 4:  70% 5:  70% 6:  75% 7:  75%
D: alsa-sink.c: Got hardware volume: 0:  75% 1:  75% 2:  63% 3:  63% 4:  63% 5:  63% 6:  63% 7:  63%
D: alsa-sink.c: Calculated software volume: 0: 100% 1: 100% 2: 119% 3: 119% 4: 111% 5: 112% 6: 119% 7: 119% (accurate-enough=no)
D: core-util.c: RealtimeKit worked.
I: core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 5.
I: alsa-sink.c: Starting playback.
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
I: module.c: Loaded "module-alsa-card" (index: #5; argument: "device_id="0" name="pci-0000_00_14.2" card_name="alsa_card.pci-0000_00_14.2" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1"").
I: module-udev-detect.c: Card /devices/pci0000:00/0000:00:14.2/sound/card0 (alsa_card.pci-0000_00_14.2) module loaded.
I: module-udev-detect.c: Found 2 cards.
I: module.c: Loaded "module-udev-detect" (index: #6; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.21/modules/module-bluetooth-discover.so': success
D: dbus-util.c: Successfully connected to D-Bus system bus e04813dcfdb9de7836f22db100000035 as :1.49
D: bluetooth-util.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module.c: Loaded "module-bluetooth-discover" (index: #7; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.21/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #8; argument: "").
I: module.c: Loaded "module-native-protocol-unix" (index: #9; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.21/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #10; argument: "").
D: core-subscribe.c: Dropped redundant event due to change event.
I: module-default-device-restore.c: Restored default sink 'alsa_output.pci-0000_00_14.2.analog-surround-71'.
D: core-subscribe.c: Dropped redundant event due to change event.
I: module-default-device-restore.c: Restored default source 'alsa_output.pci-0000_00_14.2.analog-surround-71.monitor'.
I: module.c: Loaded "module-default-device-restore" (index: #11; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #12; argument: "").
I: module.c: Loaded "module-always-sink" (index: #13; argument: "").
I: module.c: Loaded "module-intended-roles" (index: #14; argument: "").
D: module-suspend-on-idle.c: Sink alsa_output.pci-0000_01_00.1.hdmi-stereo becomes idle, timeout in 5 seconds.
D: module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_14.2.analog-surround-71 becomes idle, timeout in 5 seconds.
I: module.c: Loaded "module-suspend-on-idle" (index: #15; argument: "").
I: client.c: Created 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session1"
D: module-console-kit.c: Added new session /org/freedesktop/ConsoleKit/Session1
I: module.c: Loaded "module-console-kit" (index: #16; argument: "").
I: module.c: Loaded "module-position-event-sounds" (index: #17; argument: "").
D: main.c: Got org.pulseaudio.Server!
I: main.c: Daemon startup complete.
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
I: client.c: Created 1 "Native client (UNIX socket client)"
D: protocol-native.c: Protocol version: remote 16, local 16
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
D: protocol-native.c: SHM possible: yes
D: protocol-native.c: Negotiated SHM: yes
D: module-augment-properties.c: Looking for .desktop file for indicator-sound-service
I: client.c: Created 2 "Native client (UNIX socket client)"
D: protocol-native.c: Protocol version: remote 16, local 16
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
D: protocol-native.c: SHM possible: yes
D: protocol-native.c: Negotiated SHM: yes
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: module-augment-properties.c: Looking for .desktop file for gnome-settings-daemon
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
I: module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_14.2.analog-surround-71 idle for too long, suspending ...
D: sink.c: Suspend cause of sink alsa_output.pci-0000_00_14.2.analog-surround-71 is 0x0004, suspending
I: alsa-sink.c: Device suspended...
I: module-suspend-on-idle.c: Sink alsa_output.pci-0000_01_00.1.hdmi-stereo idle for too long, suspending ...
D: sink.c: Suspend cause of sink alsa_output.pci-0000_01_00.1.hdmi-stereo is 0x0004, suspending
I: alsa-sink.c: Device suspended...
D: reserve-wrap.c: Device lock status of reserve-monitor-wrapper@Audio0 changed: not busy
D: reserve-wrap.c: Device lock status of reserve-monitor-wrapper@Audio1 changed: not busy
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC0 is accessible: yes

[/PHP]

Thanks for the help. I appreciate it!

---

### Post by lidex on 2011-03-07
Your mixer settings are showing:
```
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
 [COLOR="Red"] Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off][/COLOR]

Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Stereo Mixer' 'Mic' 'Front Mic' 'Line'
  [COLOR="Red"]Item0: 'Mic'[/COLOR]
```
Try changing those.

---

### Post by OhHamburgers on 2011-03-08
I'm not quite sure how to do that.  I got into alsamixer and looked for those settings but they either weren't there or they already seemed enabled.

---

### Post by lidex on 2011-03-17
You should be able to open alsamixer, press <F4> for capture devices, scroll over to 'Input Source' and toggle with up/dn keys.

---

### Post by OhHamburgers on 2011-03-18
Alright I have changed the value to front mic and the other values look enabled to me.  

Do you want me to run the commands from post #7 to see if it fixed anything?

---

### Post by lidex on 2011-03-18
No, just see if you have input from your mic. What is now showing in sound preferences, the input tab, connector drop-down?

---

### Post by OhHamburgers on 2011-03-19
There is nothing there in the input tab.  I have no devices to choose from for input.  I'm just guessing that Ubuntu is not seeing that I have an input to choose from.

---

### Post by lidex on 2011-03-19
What about your profile on the hardware tab?

---

### Post by OhHamburgers on 2011-03-19
I have 

HD48x0 audio
1 output
Digital Sterio HDMI Output

Internal Audio
1 Output
Analog Surround 7.1 Output

---

### Post by lidex on 2011-03-20
You need to select a profile with an input or a duplex to capture sound.

---

### Post by OhHamburgers on 2011-03-21
Ah I get it now.  I thought it was going to be picked up automatically.  It works perfect now.  Thanks for all your help!

---

