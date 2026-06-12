---
title: "Intel HDA - Realtek ALC888"
date: 2011-04-14
forum: Multimedia Software
---

### Post by moose2 on 2011-04-14
Hi,

I have a Medion Akoya MD 96630 Notebook and Ubuntu 10.10.

Before I tried this ([http://ubuntuforums.org/showthread.php?t=558069](http://ubuntuforums.org/showthread.php?t=558069)) the internal speakers worked, but not the mic or headphones.

Now nothing works at all:

[PHP]$ aplay -l
aplay: device_list:235: keine Soundkarten gefunden ...

$ cat /proc/asound/cards
cat: /proc/asound/cards: Datei oder Verzeichnis nicht gefunden

$ lspci -v
[...]
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Wistron Corp. Device 4085
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at fa200000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel
[...]

$ lspci -nnk | grep -iA2 audio 
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
	Subsystem: Wistron Corp. Device [17c0:4085]
	Kernel modules: snd-hda-intel


$ ps -C esd
  PID TTY          TIME CMD


$ ps -C arts
  PID TTY          TIME CMD
[/PHP]

What should I do now?

---

### Post by Yellow Pasque on 2011-04-14
```
cd <directory_where_you_placed>/realtek-linux-audiopack-5.16rc6
sudo make uninstall
sudo apt-get install --reinstall linux-image-`uname -r`-generic
```

If you get sound working after reboot, try this for microphone and headphones:
```
echo "options snd-hda-intel model=medion" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```

---

### Post by moose2 on 2011-04-15
Hi Temüjin,

I've just reinstalled the whole system and executed your command, but "options snd-hda-intel model=medion" changed nothing. Mic and Line out don't work, Line-In and internal speakers work.

```

$ aplay -l
**** Liste der Hardware-Geräte (PLAYBACK) ****
Karte 0: Intel [HDA Intel], Gerät 0: ALC888 Analog [ALC888 analog]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0

$ lspci -v
[...]
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Wistron Corp. Device 4085
	Flags: bus master, fast devsel, latency 0, IRQ 48
	Memory at fa200000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
[...]

$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.


$ lsmod | grep snd
snd_hda_codec_realtek   218492  1 
snd_hda_intel          22235  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    49038  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm

```

See also:
[LIST]
[*][http://mailman.alsa-project.org/pipermail/alsa-devel/2011-April/038430.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2011-April/038430.html)
[*][http://www.alsa-project.org/main/index.php/Changes_v1.0.23_v1.0.24](http://www.alsa-project.org/main/index.php/Changes_v1.0.23_v1.0.24) : Some changes are related to Realtek / ALC888. Do you think the next version of Ubuntu could solve the problem?
[/LIST]

---

