---
title: "Rosegarden4 and computer crashing, freezes, locks up and no sound to boot."
date: 2006-07-14
forum: Multimedia &amp; Video
---

### Post by yurtboy on 2006-07-14
Well other things work but ie hydrogen, timidity etc.  But this does not.
Tried with jack and without
Tried on two computers one with gnome and one with kubuntu
Looked for instructions and followed many.
But still it plays and looks like it is enjoying itself by I hear nothing.
It is hard to work on because every so often the computer(s) freeze.
It is not a hardware problem so I would like to hear if anyone else had this struggle and got it to work with dapper.
Settings are below?
Well thanks in advance and I look forward to making audio work out.
ps..I have not midi hooked up but I do have a midi port.
I am going back to the rosegarden site since I noticed something there but these crashes are killing my progress.
lsmod | grep -i seq
snd_seq_dummy           3908  0
snd_seq_oss            37216  0
snd_seq_midi            9600  0
snd_seq_midi_event      7520  2 snd_seq_oss,snd_seq_midi
snd_seq                58160  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_rawmidi            26848  2 snd_seq_midi,snd_ens1371
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd_timer              26884  2 snd_seq,snd_pcm
snd                    60004  12 snd_seq_oss,snd_seq,snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer


more /proc/interrupts
           CPU0       CPU1
  0:     494752        158    IO-APIC-edge  timer
  1:       2356          1    IO-APIC-edge  i8042
  7:          0          0    IO-APIC-edge  parport0
  8:          2          1    IO-APIC-edge  rtc
  9:          0          0   IO-APIC-level  acpi
 12:      17501          3    IO-APIC-edge  i8042
 14:      24214          1    IO-APIC-edge  ide0
169:       3767          1   IO-APIC-level  uhci_hcd:usb1
177:       3352          0   IO-APIC-level  eth1
185:       9379          0   IO-APIC-level  Ensoniq AudioPCI
NMI:          0          0
LOC:     492184     492192
ERR:          0
MIS:          0

sudo lspci -v
0000:00:08.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 06)
        Subsystem: Ensoniq Creative Sound Blaster AudioPCI64V, AudioPCI128
        Flags: bus master, slow devsel, latency 64, IRQ 185
        I/O ports at e400 [size=64]
        Capabilities: [dc] Power Management version 1

cat /proc/version
Linux version 2.6.15-23-686 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Tue May 23 14:03:07 UTC 2006

---

