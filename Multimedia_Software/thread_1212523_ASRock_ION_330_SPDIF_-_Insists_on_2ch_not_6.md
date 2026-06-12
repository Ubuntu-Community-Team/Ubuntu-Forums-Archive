---
title: "ASRock ION 330 SPDIF - Insists on 2ch not 6"
date: 2009-07-13
forum: Multimedia Software
---

### Post by mintochris on 2009-07-13
No matter what I do I can't get 6 ch out of spdif.

My .asoundrc has had various thing in it ranging from nothing to massively complex things, currently it is blank.

I have uncommented the channels line from /etc/pulse/daemons.conf and set it to 6
my /etc/pulse/default.pa is unmodified.

No matter what I have changed, from fresh install through to now, where I have used the script from [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810) to compile the latests alsa, I get exactly the same behaviour. No matter what I set, i get stereo sound when "iec958" and "iec958 default pcm" are enabled in the mixer, with "iec958 1" having no effect (i assume this is the hdmi audio - which doesnt work but is beside thee point)

If i run "speaker-test -Dplug:surround51 -c6 -l1 -twav" it says...
```

speaker-test 1.0.20

Playback device is plug:surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 4 - Centre
 1 - Front Right
 3 - Rear Right
 2 - Rear Left
 5 - LFE
Time per period = 8.367402

```
implying that it plays all the samples on all the channels, but for everything except fron left and front right my amp's digital light goes off and no sound is made. The rest of the time only the 2.1 lights are on, but when sound is played the digital light is on.

Loads more files follow! Any advice or a solution would be a god send, I've been tearing my hair out all day!


lspci
```

00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
01:00.0 VGA compatible controller: nVidia Corporation Device 087d (rev b1)

```

aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

aplay -L
```

n:~$ aplay -L
front:CARD=NVidia,DEV=0
    HDA NVidia, VT1708S Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, VT1708S Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, VT1708S Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, VT1708S Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, VT1708S Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, VT1708S Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, VT1708S Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

```

pulseaudio -k && pulseaudio -vv
```

I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
D: main.c: Started as real root: no, suid root: yes
I: main.c: PolicyKit refuses acquire-high-priority privilege.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: main.c: Can realtime: no, can high-priority: no
D: main.c: Can realtime: no, can high-priority: no
I: main.c: This is PulseAudio 0.9.14
D: main.c: Compilation host: i486-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pedantic -pipe -Wno-long-long -Wvla -Wno-overlength-strings -Wconversion -Wundef -Wformat -Wlogical-op -Wpacked -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wdeclaration-after-statement -Wfloat-equal -Wmissing-declarations -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-noreturn -Wshadow -Wendif-labels -Wpointer-arith -Wcast-align -Wwrite-strings -Wno-unused-parameter -ffast-math
D: main.c: Running on host: Linux i686 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Optimized build: yes
I: main.c: Machine ID is 608e79eb4978435f7e93fc264a5bab1c.
I: main.c: Using runtime directory /home/chris/.pulse/608e79eb4978435f7e93fc264a5bab1c:runtime.
I: main.c: Using state directory /home/chris/.pulse.
I: main.c: Running in system mode: no
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: memblock.c: Using shared memory pool with 1024 slots of size 64.0 KiB each, total size is 64.0 MiB, maximum usable slot size is 65496
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #0; argument: "").
I: module.c: Loaded "module-suspend-on-idle" (index: #1; argument: "").
I: module-device-restore.c: Sucessfully opened database file '/home/chris/.pulse/608e79eb4978435f7e93fc264a5bab1c:device-volumes.i486-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-device-restore" (index: #2; argument: "").
I: module-stream-restore.c: Sucessfully opened database file '/home/chris/.pulse/608e79eb4978435f7e93fc264a5bab1c:stream-volumes.i486-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-stream-restore" (index: #3; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-hal-detect.so': success
I: module-hal-detect.c: Trying capability alsa
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10de_ac0_sound_card_0_alsa_playback_3
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10de_ac0_sound_card_0_alsa_playback_1
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_10de_ac0_sound_card_0_alsa_playback_0 tsched=0'
D: alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: PCM device plug:surround51:0 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: PCM device plug:surround71:0 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: Trying plug:surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: PCM device plug:surround50:0 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: Trying plug:surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: PCM device plug:surround41:0 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: PCM device plug:surround40:0 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
I: module-alsa-sink.c: Successfully opened device front:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Cannot find mixer control "Master" or mixer control is no combination of switch/volume.
W: alsa-util.c: Cannot find fallback mixer control "PCM" or mixer control is no combination of switch/volume.
I: alsa-util.c: Using mixer control "PCM".
I: module-device-restore.c: Restoring volume for sink alsa_output.pci_10de_ac0_sound_card_0_alsa_playback_0.
I: module-device-restore.c: Restoring mute state for sink alsa_output.pci_10de_ac0_sound_card_0_alsa_playback_0.
I: sink.c: Created sink 0 "alsa_output.pci_10de_ac0_sound_card_0_alsa_playback_0" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-device-restore.c: Restoring volume for source alsa_output.pci_10de_ac0_sound_card_0_alsa_playback_0.monitor.
I: module-device-restore.c: Restoring mute state for source alsa_output.pci_10de_ac0_sound_card_0_alsa_playback_0.monitor.
I: source.c: Created source 0 "alsa_output.pci_10de_ac0_sound_card_0_alsa_playback_0.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-alsa-sink.c: Using 8 fragments of size 1792 bytes, buffer time is 81.27ms
D: module-alsa-sink.c: hwbuf_unused=0
D: module-alsa-sink.c: setting avail_min=1
I: module-alsa-sink.c: Volume ranges from 0 to 255.
I: module-alsa-sink.c: Volume ranges from -51.00 dB to 0.00 dB.
I: alsa-util.c: All 2 channels can be mapped to mixer channels.
I: module-alsa-sink.c: Using hardware volume control. Hardware dB scale supported.
I: module-alsa-sink.c: Using software mute control.
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
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 3584
D: alsa-util.c:   period_size  : 448
D: alsa-util.c:   period_time  : 10158
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 448
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 1879048192
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 1879048192
D: alsa-util.c: Slave: Hardware PCM card 0 'HDA NVidia' device 0 subdevice 0
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : PLAYBACK
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 3584
D: alsa-util.c:   period_size  : 448
D: alsa-util.c:   period_time  : 10158
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 448
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_thr
D: module-alsa-sink.c: Thread starting up
D: module-alsa-sink.c: Requested volume: 0: 100% 1: 100%
D: module-alsa-sink.c: Got hardware volume: 0: 100% 1: 100%
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
D: module-alsa-sink.c: Calculated software volume: 0: 100% 1: 100%
I: module-alsa-sink.c: Starting playback.
D: module-suspend-on-idle.c: Source alsa_output.pci_10de_ac0_sound_card_0_alsa_playback_0.monitor becomes idle.
D: module-suspend-on-idle.c: Sink alsa_output.pci_10de_ac0_sound_card_0_alsa_playback_0 becomes idle.
I: module.c: Loaded "module-alsa-sink" (index: #4; argument: "device_id=0 sink_name=alsa_output.pci_10de_ac0_sound_card_0_alsa_playback_0 tsched=0").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 source_name=alsa_input.pci_10de_ac0_sound_card_0_alsa_capture_0 tsched=0'
D: alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround51:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: PCM device plug:surround51:0 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround71:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: PCM device plug:surround71:0 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: Trying plug:surround50:0 without SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: PCM device plug:surround50:0 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
D: alsa-util.c: Trying plug:surround41:0 without SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: alsa-util.c: PCM device plug:surround41:0 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:surround40:0 without SND_PCM_NO_AUTO_FORMAT ...
I: alsa-util.c: PCM device plug:surround40:0 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: module-device-restore.c: Restoring volume for source alsa_input.pci_10de_ac0_sound_card_0_alsa_capture_0.
I: module-device-restore.c: Restoring mute state for source alsa_input.pci_10de_ac0_sound_card_0_alsa_capture_0.
I: source.c: Created source 1 "alsa_input.pci_10de_ac0_sound_card_0_alsa_capture_0" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-alsa-source.c: Using 8 fragments of size 1792 bytes, buffer time is 81.27ms
D: module-alsa-source.c: hwbuf_unused=0
D: module-alsa-source.c: setting avail_min=1
I: module-alsa-source.c: Volume ranges from 0 to 31.
I: module-alsa-source.c: Volume ranges from -16.50 dB to 30.00 dB.
I: alsa-util.c: All 2 channels can be mapped to mixer channels.
I: module-alsa-source.c: Using hardware volume control. Hardware dB scale supported.
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Soft volume PCM
D: alsa-util.c: Control: PCM Playback Volume
D: alsa-util.c: min_dB: -51
D: alsa-util.c: max_dB: 0
D: alsa-util.c: resolution: 256
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : CAPTURE
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 3584
D: alsa-util.c:   period_size  : 448
D: alsa-util.c:   period_time  : 10158
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 448
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 1879048192
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 1879048192
D: alsa-util.c: Slave: Hardware PCM card 0 'HDA NVidia' device 0 subdevice 0
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : CAPTURE
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 3584
D: alsa-util.c:   period_size  : 448
D: alsa-util.c:   period_time  : 10158
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 448
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_thres
D: module-alsa-source.c: Requested volume: 0: 100% 1: 100%
D: module-alsa-source.c: Got hardware volume: 0: 100% 1: 100%
D: module-alsa-source.c: Calculated software volume: 0: 100% 1: 100%
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
D: module-suspend-on-idle.c: Source alsa_input.pci_10de_ac0_sound_card_0_alsa_capture_0 becomes idle.
I: module.c: Loaded "module-alsa-source" (index: #5; argument: "device_id=0 source_name=alsa_input.pci_10de_ac0_sound_card_0_alsa_capture_0 tsched=0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10de_ac0_sound_card_0_alsa_hw_specific_3
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10de_ac0_sound_card_0_alsa_hw_specific_0
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10de_ac0_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 2 modules.
I: module.c: Loaded "module-hal-detect" (index: #6; argument: "tsched=0").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #7; argument: "").
I: module.c: Loaded "module-native-protocol-unix" (index: #8; argument: "").
I: module-default-device-restore.c: Restored default sink 'alsa_output.pci_10de_ac0_sound_card_0_alsa_playback_0'.
D: core-subscribe.c: Dropped redundant event due to change event.
I: module-default-device-restore.c: Restored default source 'alsa_input.pci_10de_ac0_sound_card_0_alsa_capture_0'.
I: module.c: Loaded "module-default-device-restore" (index: #9; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #10; argument: "").
I: module.c: Loaded "module-always-sink" (index: #11; argument: "").
I: client.c: Created 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session1"
D: module-console-kit.c: Added new session /org/freedesktop/ConsoleKit/Session1
I: module.c: Loaded "module-console-kit" (index: #12; argument: "").
I: module.c: Loaded "module-position-event-sounds" (index: #13; argument: "").
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
D: module-console-kit.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module-suspend-on-idle.c: Sink alsa_output.pci_10de_ac0_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.pci_10de_ac0_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Source alsa_input.pci_10de_ac0_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
^CI: main.c: Got signal SIGINT.
I: main.c: Exiting.
I: main.c: Daemon shutdown initiated.
I: module.c: Unloading "module-gconf" (index: #0).
I: module.c: Unloaded "module-gconf" (index: #0).
I: module.c: Unloading "module-suspend-on-idle" (index: #1).
I: module.c: Unloaded "module-suspend-on-idle" (index: #1).
I: module.c: Unloading "module-device-restore" (index: #2).
I: module.c: Unloaded "module-device-restore" (index: #2).
I: module.c: Unloading "module-stream-restore" (index: #3).
I: module.c: Unloaded "module-stream-restore" (index: #3).
I: module.c: Unloading "module-alsa-sink" (index: #4).
D: module-always-sink.c: Autoloading null-sink as no other sinks detected.
I: sink.c: Created sink 1 "auto_null" with sample spec s16le 6ch 44100Hz and channel map front-left,rear-left,front-center,front-right,rear-right,lfe
I: source.c: Created source 2 "auto_null.monitor" with sample spec s16le 6ch 44100Hz and channel map front-left,rear-left,front-center,front-right,rear-right,lfe
D: module-null-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+27
I: module.c: Loaded "module-null-sink" (index: #14; argument: "sink_name=auto_null").
D: module-rescue-streams.c: No sink inputs to move away.
D: module-rescue-streams.c: No source outputs to move away.
D: module-alsa-sink.c: Thread shutting down
I: sink.c: Freeing sink 0 "alsa_output.pci_10de_ac0_sound_card_0_alsa_playback_0"
I: source.c: Freeing source 0 "alsa_output.pci_10de_ac0_sound_card_0_alsa_playback_0.monitor"
I: module.c: Unloaded "module-alsa-sink" (index: #4).
I: module.c: Unloading "module-alsa-source" (index: #5).
D: module-rescue-streams.c: No source outputs to move away.
D: module-alsa-source.c: Thread shutting down
I: source.c: Freeing source 1 "alsa_input.pci_10de_ac0_sound_card_0_alsa_capture_0"
I: module.c: Unloaded "module-alsa-source" (index: #5).
I: module.c: Unloading "module-hal-detect" (index: #6).
I: module.c: Unloaded "module-hal-detect" (index: #6).
I: module.c: Unloading "module-esound-protocol-unix" (index: #7).
I: module.c: Unloaded "module-esound-protocol-unix" (index: #7).
I: module.c: Unloading "module-native-protocol-unix" (index: #8).
I: module.c: Unloaded "module-native-protocol-unix" (index: #8).
I: module.c: Unloading "module-default-device-restore" (index: #9).
I: module.c: Unloaded "module-default-device-restore" (index: #9).
I: module.c: Unloading "module-rescue-streams" (index: #10).
I: module.c: Unloaded "module-rescue-streams" (index: #10).
I: module.c: Unloading "module-always-sink" (index: #11).
I: module.c: Unloaded "module-always-sink" (index: #11).
I: module.c: Unloading "module-console-kit" (index: #12).
D: module-console-kit.c: Removing session /org/freedesktop/ConsoleKit/Session1
I: client.c: Freed 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session1"
I: module.c: Unloaded "module-console-kit" (index: #12).
I: module.c: Unloading "module-position-event-sounds" (index: #13).
I: module.c: Unloaded "module-position-event-sounds" (index: #13).
I: module.c: Unloading "module-null-sink" (index: #14).
D: core-subscribe.c: Dropped redundant event due to remove event.
D: core-subscribe.c: Dropped redundant event due to remove event.
D: module-null-sink.c: Thread shutting down
I: sink.c: Freeing sink 1 "auto_null"
I: source.c: Freeing source 2 "auto_null.monitor"
I: module.c: Unloaded "module-null-sink" (index: #14).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: main.c: Daemon terminated.

```

---

### Post by mintochris on 2009-07-14
I hate to do this... but
**bump**

It's almost as though alsa is outputting the 6 channels, but not encoded properly for the amp to decode. - I'm probably talking crap there though!

---

### Post by mtippett on 2009-07-14
> **mintochris said:**
> I hate to do this... but
**bump**

It's almost as though alsa is outputting the 6 channels, but not encoded properly for the amp to decode. - I'm probably talking crap there though!

I have seen something similar.  

I have confirmed that passthrough works properly.  I have followed [http://www.nvnews.net/vbulletin/showthread.php?p=2044902](http://www.nvnews.net/vbulletin/showthread.php?p=2044902).  I distinct output on all 5 channels.  The sample doesn't seem to have any LFE output, so I can't confirm that.

As far as I can tell with the PCM output, I can't get it to output on anything other than left and right channels.

The way I have xbmc set up now is to always output over digital using /etc/asound.conf

```

pcm.!default {
&#12288;type plug
&#12288;slave {
&#12288;&#12288;pcm "spdif"
&#12288;&#12288;rate 48000
&#12288;&#12288;format S16_LE
&#12288;}
}

```

At least it prevents the switching from analog out to digital.

I'll post back if I find anything.

Regards,

Matthew

---

### Post by mintochris on 2009-07-15
i can't get any kind of passthrough to work without either the same symptoms or no audio at all.

I tried your config file and all it did was remove my alsa options from the sound config app and leeave just oss.

---

### Post by mintochris on 2009-07-15
i take it back. a blank asoundrc with passthrough in boxee (and only in boxee!?) allows files with ac3 or dts to be played in full surround sound. Awesome. Just a shame about my 5 channel aac mp4s.

Thanks for the advice, and if anyone can resolve the underlying issue for alsa generated audio (ie not just passthrough) it would make my day.

maybe i could just remuux my old mp4s and re-encoode the audio. anyone got a command for mencoder that'll do it?

---

