---
title: "Sound suddenly stops working"
date: 2007-12-30
forum: Multimedia &amp; Video
---

### Post by plafuro on 2007-12-30
Hi all,

I got a new computer with an Intel sound chip (module snd_hda_intel), and it works perfectly most of the time (running Gutsy here, btw). Unfortunatelly sometimes, let's say, if i'm listening music being played with mpd, then i watch something in totem/vlc and i try to resume playback in mpd, sound will stop working. I tried restarting alsa with the init.d script and sound won't be back (EDIT: I also tried killing all osd/esd related processes). I checked dmesg, daemon.log, syslog, kern.log, daemon.log and user.log and there's not a trace of any kind there.

Killing X brings sound back most of the time (i supose some software running gets hold of the soundcard even though i try to kill everything i'm running to track down the root problem, and, as mentioned before, restarted alsa), what -i suppose- means that it's not really a module problem. Anyway here is the output of my "snd grepped" lsmod:

```
snd_usb_audio          81024  0 
snd_usb_lib            17920  1 snd_usb_audio
snd_hwdep              10244  1 snd_usb_audio
snd_hda_intel         263712  2 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  2 snd_pcm_oss
snd_pcm                80388  3 snd_usb_audio,snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  13 snd_usb_audio,snd_hwdep,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  2 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
usbcore               138632  10 snd_usb_audio,snd_usb_lib,gspca,usb_storage,hci_usb,usblp,libusual,ehci_hcd,uhci_hcd
```


I don't know where else to look or how to approach this problem in another way :confused: ... What are your thoughts?

Thank you very much in advance!!!

---

### Post by plafuro on 2008-01-06
bump . . .

---

