---
title: "Maverick suspend and resume"
date: 2010-09-22
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by wadam on 2010-09-22
I feel like I'm full of questions here, however, I thought that I'd post this one too:

When I attempt to suspend my computer, everything seems to go well (and the logs suggest that everything has gone well), but it never quite suspends.  It drops down to a blinking white cursor, the fans kick up to 100% (I assume pwm has been suspended), and it just sits there, frozen, until I do a hard reboot.

My computer has had suspend problems with 10.04.  Those seemed to be about the xhci (USB 3.0) module, and the nVidia proprietary drivers.  But they would drop me down to a locked screen, from which I could easily recover.

What's changed?  Is it still xhci that's the problem?  Is there any way for me to fix this?

For reference, I'm including an excerpt from my pm-suspend.log here:

```
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux atu300 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64 GNU/Linux
Module                  Size  Used by
binfmt_misc             7984  1 
parport_pc             30086  0 
ppdev                   6804  0 
snd_hda_codec_realtek   299533  1 
snd_usb_audio         105727  1 
snd_usbmidi_lib        21313  1 snd_usb_audio
rt2860sta             559618  0 
snd_hda_intel          26019  2 
arc4                    1497  2 
snd_hda_codec         100919  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6660  2 snd_usb_audio,snd_hda_codec
snd_pcm                89104  3 snd_usb_audio,snd_hda_intel,snd_hda_codec
rt2800pci              10233  0 
snd_seq_midi            5932  0 
nvidia              11087157  38 
rt2800lib              31970  1 rt2800pci
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_rawmidi            22207  2 snd_usbmidi_lib,snd_seq_midi
rt2x00usb              11316  1 rt2800lib
rt2x00pci               6993  1 rt2800pci
crc_ccitt               1699  2 rt2860sta,rt2800pci
rt2x00lib              31575  4 rt2800pci,rt2800lib,rt2x00usb,rt2x00pci
led_class               3393  1 rt2x00lib
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_seq,snd_rawmidi
mac80211              266657  3 rt2x00usb,rt2x00pci,rt2x00lib
uvcvideo               62379  0 
it87                   35308  0 
hwmon_vid               3154  1 it87
videodev               49359  1 uvcvideo
v4l1_compat            15519  2 uvcvideo,videodev
v4l2_compat_ioctl32    12646  1 videodev
snd                    64117  17 snd_hda_codec_realtek,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_rawmidi,snd_timer,snd_seq_device
cfg80211              170293  2 rt2x00lib,mac80211
eeprom_93cx6            1789  1 rt2800pci
serio_raw               4910  0 
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
xhci_hcd               58578  0 
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
hid_apple               5695  0 
usbhid                 42062  0 
hid                    84678  2 hid_apple,usbhid
firewire_sbp2          15033  1 
usb_storage            50372  0 
firewire_ohci          24679  0 
firewire_core          54327  2 firewire_sbp2,firewire_ohci
crc_itu_t               1739  1 firewire_core
r8169                  42222  0 
ahci                   21857  0 
mii                     5261  1 r8169
libahci                26167  4 ahci
             total       used       free     shared    buffers     cached
Mem:       8152644    3095788    5056856          0     231812    2029972
-/+ buffers/cache:     834004    7318640
Swap:     12681212          0   12681212

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...method return sender=:1.2 -> dest=:1.97 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend:

/usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Tue Sep 21 10:43:02 EDT 2010: performing suspend
```

Thanks ahead of time!

---

