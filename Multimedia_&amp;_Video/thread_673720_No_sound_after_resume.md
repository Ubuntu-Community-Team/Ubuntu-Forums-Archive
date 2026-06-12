---
title: "No sound after resume"
date: 2008-01-20
forum: Multimedia &amp; Video
---

### Post by PhilipGanchev on 2008-01-20
After resuming from sleep or suspend, I cannot play sound files, though the system beep works.  It works again if I remove and reinsert the sound driver module, snd_cs46xx.  Is there a way to fix this or to remove/reinsert automatically on sleep/hibernate? Should I file a bug somewhere?  Even if I add "snd_cs46xx" under MODULES in /etc/default/acpi-support, it still does not work: the dmesg output is attached.

I'm running Ubuntu Feisty (Linux 2.6.20-16-generic #2 SMP) on an IBM Thinkpad A21m.

% lspci | grep audio
00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)

% lsmod | grep snd
snd_cs46xx             85096  0
gameport               16520  2 snd_cs46xx
snd_ac97_codec         98464  1 snd_cs46xx
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_cs46xx,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0
snd_seq_oss            32896  0
snd_seq_midi            9600  0
snd_rawmidi            25472  2 snd_cs46xx,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  10 snd_cs46xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_cs46xx,snd_pcm

---

### Post by PhilipGanchev on 2008-01-22
I should add that the command "sudo modprobe -r snd_cs46xx" removes the sound driver module without errors, and "sudo modprobe snd_cs46xx" reinserts it, after which I can play sound files.

I also found this bug report: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/11149](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/11149) , which suggests that if no programs that use the sound card are running, the modules should be removed on suspend without a problem.  But they are not for me.

---

### Post by mättu on 2008-01-22
sounds good to me. It's very easy to write a little sudo-script which one adds as a panel-icon..
But..

sudo modprobe -r snd_intel8x0
FATAL: Module snd_intel8x0 is in use.

How do you manage to unload it?

:m)

---

### Post by PhilipGanchev on 2008-01-22
Modules which are being used by programs or by other modules that are used by programs cannot be cleanly removed until you quit the programs.  For sound modules, those programs include audio players and recorders, movie viewers and sound configuration programs.  The command "lsmod" shows how many programs or which modules are using each module.

---

### Post by mättu on 2008-01-23
lsmod:
..
snd_intel8x0           34332  1 
..
There seems to be 1 program using snd_intel8x0, but no name is returned.
It's "1" as long as xfce is startet and "0" if not.
Workaround (not appropriate): logout, restart sound, login..

---

### Post by PhilipGanchev on 2008-01-23
Have you disabled all sounds for events in the XFCE preferences?  Are any applets running, which sometimes play sounds?

---

### Post by mättu on 2008-01-23
The number does not change, if many sound-programs are open or none.

---

