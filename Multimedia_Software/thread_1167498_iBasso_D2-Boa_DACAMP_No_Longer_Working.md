---
title: "iBasso D2-Boa DAC/AMP No Longer Working"
date: 2009-05-22
forum: Multimedia Software
---

### Post by overshard on 2009-05-22
When I first installed ubuntu (and had the dac/amp plugged in during the install) it works working just fine. However, since this is a laptop I am on, I unplugged it to take it somewhere and when I got back the device no longer worked.

I have tested many thing and finally got it to work under one circumstance. Running gnome-sound-properties as my own user got me the following error while trying to play a test sound:

```

(gnome-sound-properties:15483): sound-properties-DEBUG: setting theme ubuntu
sound-properties-Message: Error running pipeline 'audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink': Could not open audio device for playback. [gstalsasink.c(694): gst_alsasink_open (): /GstBin:bin0/GstHalAudioSink:halaudiosink0/GstBin:bin1/GstAlsaSink:alsasink0:
Playback open error on device 'default:1': Invalid argument]

```

However, running sudo gnome-sound-properties it worked just fine.

I checked group permissions and I was in the audio sound group. I also found that this seems to only be an alsa bug, it works just fine under OSS. I must use alsa though because most of the software I use has limited to no OSS support.

I guess I could reinstall and never unplug the dac/amp but that would be annoying. ;)

Thanks for any help.


Oh, and here is some additional info if needed:

dmesg output related to the dac/amp:
```

[ 4528.068744] [drm] Loading R500 Microcode
[ 4528.068802] [drm] Num pipes: 1
[ 4528.068815] [drm] writeback test succeeded in 2 usecs
[ 4785.501060] usb 1-1.5: USB disconnect, address 16
[ 4795.172344] usb 1-1.5: new full speed USB device using ehci_hcd and address 17
[ 4795.266519] usb 1-1.5: configuration #1 chosen from 1 choice
[ 4795.275687] input: Burr-Brown from TI               USB Audio DAC    as /devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1.5/1-1.5:1.2/input/input19
[ 4795.336188] generic-usb 0003:08BB:2706.000A: input,hidraw3: USB HID v1.00 Device [Burr-Brown from TI               USB Audio DAC   ] on usb-0000:00:1d.7-1.5/input2
[ 5458.105056] usbcore: deregistering interface driver snd-usb-audio
[ 5458.139541] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 5458.371416] usbcore: registered new interface driver snd-usb-audio
[ 5458.424537] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 5458.424674] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 5458.457457] hda_codec: STAC922x, Apple subsys_id=106b0200
[ 5459.504010] hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x00af0900

```

Some of the syslog that may be related:
```

May 22 23:11:19 scyindo pulseaudio[14881]: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
May 22 23:11:53 scyindo kernel: [ 6545.644074] usbcore: deregistering interface driver snd-usb-audio
May 22 23:11:53 scyindo kernel: [ 6545.681687] HDA Intel 0000:00:1b.0: PCI INT A disabled
May 22 23:11:54 scyindo kernel: [ 6545.917035] usbcore: registered new interface driver snd-usb-audio
May 22 23:11:54 scyindo kernel: [ 6545.931643] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
May 22 23:11:54 scyindo kernel: [ 6545.931808] HDA Intel 0000:00:1b.0: setting latency timer to 64
May 22 23:11:54 scyindo kernel: [ 6545.965081] hda_codec: STAC922x, Apple subsys_id=106b0200
May 22 23:11:58 scyindo pulseaudio[15158]: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
May 22 23:11:58 scyindo pulseaudio[15158]: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
May 22 23:11:58 scyindo pulseaudio[15158]: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
May 22 23:13:50 scyindo kernel: [ 6661.796223] CE: hpet increasing min_delta_ns to 15000 nsec
May 22 23:17:01 scyindo /USR/SBIN/CRON[15252]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 22 23:20:01 scyindo /USR/SBIN/CRON[15349]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)

```

Output from catting some of the asound procs:
```

isaac@scyindo:/proc/asound$ cat devices 
  2:        : timer
  3:        : sequencer
  4: [ 1- 0]: digital audio playback
  5: [ 1]   : control
  6: [ 0- 1]: digital audio playback
  7: [ 0- 1]: digital audio capture
  8: [ 0- 0]: digital audio playback
  9: [ 0- 0]: digital audio capture
 10: [ 0]   : control
isaac@scyindo:/proc/asound$ cat cards 
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0x98400000 irq 22
 1 [default        ]: USB-Audio - USB Audio DAC   
                      Burr-Brown from TI               USB Audio DAC    at usb-0000:00:1d.7-1.5, full
isaac@scyindo:/proc/asound$ 

```

---

### Post by overshard on 2009-05-23
After some more testing I have completely disabled on-board audio by blacklisting it. Now, when I try to go to sound and do a test it comes up with the testing bar but no sound comes out. When I sudo it no sound comes out either until I do a alsa force-reload, then it will work under sudo mode but not normal mode.

Very frustrating.

---

