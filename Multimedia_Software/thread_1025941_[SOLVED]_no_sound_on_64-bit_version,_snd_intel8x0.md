---
title: "[SOLVED] no sound on 64-bit version, snd_intel8x0"
date: 2008-12-30
forum: Multimedia Software
---

### Post by IQRules on 2008-12-30
Here is the info I have.

root@ubuntuHP:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], **device 0**: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], **device 4**: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

root@ubuntuHP:~# lshw -C  sound
  *-multimedia            
       description: Multimedia audio controller
       product: **82801EB/ER** (ICH5/ICH5R) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0 module=snd_intel8x0
root@ubuntuHP:~# 

root@ubuntuHP:~# lsmod | grep snd_
snd_intel8x0           43688  3 
snd_ac97_codec        133080  1 snd_intel8x0
ac97_bus               10368  1 snd_ac97_codec
snd_pcm_oss            52608  0 
snd_mixer_oss          25088  1 snd_pcm_oss
snd_pcm                99208  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            42368  0 
snd_seq_midi           15872  0 
snd_rawmidi            34176  1 snd_seq_midi
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
snd_seq                67168  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34320  2 snd_pcm,snd_seq
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    79432  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         17680  2 snd_intel8x0,snd_pcm
root@ubuntuHP:~# 


Thanks for the help.

---

### Post by IQRules on 2008-12-30
Found this in /var/log/syslog file.


Dec 30 18:37:32 ubuntuHP pulseaudio[5980]: ltdl-bind-now.c: Failed to find original dlopen loader.
Dec 30 18:37:32 ubuntuHP pulseaudio[5982]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Dec 30 18:37:32 ubuntuHP pulseaudio[5982]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Dec 30 18:37:44 ubuntuHP x-session-manager[5893]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout
Dec 30 18:37:45 ubuntuHP NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Dec 30 18:37:45 ubuntuHP pulseaudio[5982]: module-x11-xsmp.c: X11 session manager not running.
Dec 30 18:37:45 ubuntuHP pulseaudio[5982]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 12f2
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 3000 [size=256]
	I/O ports at 3400 [size=64]
	Memory at fa200400 (32-bit, non-prefetchable) [size=512]
	Memory at fa200600 (32-bit, non-prefetchable) [size=256]
[COLOR="Red"]**	Capabilities: <access denied>**[/COLOR]
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

root@ubuntuHP:~# uname -rm
2.6.27-9-server x86_64

---

### Post by IQRules on 2009-01-03
32-bit liveCD proofs to be no issue on /dev/dsp or /dev/audio, internal speakers sounds work fine.

Only things I can think of is the 64-bit server has RAID subsystem and loads with nVidia 177 (FX 1400) driver. I disabled pulseaudio and still no sounds from this command.

$ aplay /usr/share/sounds/purple/login.wav

I do get the system alert (short beep) sound from internal speakers and headphone sound works fine.

Somewrong with /dev/dsp or /dev/audio.

---

### Post by IQRules on 2009-01-07
Just fixed my sound problem.

Put this in /etc/modprobe.d/alsa-base
options snd-intel8x0 index=0 ac97_quirk=3 enable=1

Reboot it.
And un-mute PCM in gnome-alsamixer and adjust PCM to control loundess.

---

