---
title: "ATI Technologies Inc RS780 Azalia controller; no sound"
date: 2009-08-16
forum: Multimedia Software
---

### Post by exalangumna on 2009-08-16
I'm new to Linux, and having a hard time getting my sound to work. I've tried most of the fixes on the internet. Please help me; i love sounds. Here are those infos so often asked for:
lol@lol-laptop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
08:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

lol@lol-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


lspci -v | less

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
        Subsystem: Hewlett-Packard Company Device 3059
        Flags: bus master, slow devsel, latency 64, IRQ 16
        Memory at d2400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel



lol@lol-laptop:~$ lsmod
Module                  Size  Used by
isofs                  43688  1 
udf                    92712  0 
crc_itu_t              10496  1 udf
binfmt_misc            18572  1 
ppdev                  16904  0 
bridge                 63904  0 
stp                    11140  1 bridge
bnep                   22912  2 
nfsd                  285728  13 
lockd                  83924  1 nfsd
nfs_acl                11776  1 nfsd
auth_rpcgss            52512  1 nfsd
sunrpc                227304  13 nfsd,lockd,nfs_acl,auth_rpcgss
exportfs               13440  1 nfsd
input_polldev          12688  0 
lp                     19588  0 
parport                49584  2 ppdev,lp
arc4                   10240  2 
ecb                    11392  2 
snd_hda_intel         544724  3 
snd_pcm_oss            51872  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                98440  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         18960  2 snd_hda_intel,snd_pcm
snd_hwdep              17032  1 snd_hda_intel
snd_seq_dummy          11652  0 
snd_seq_oss            43264  0 
ath9k                 288568  0 
snd_seq_midi           15680  0 
snd_rawmidi            33824  1 snd_seq_midi
snd_seq_midi_event     16640  2 snd_seq_oss,snd_seq_midi
mac80211              251528  1 ath9k
snd_seq                66848  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              33296  2 snd_pcm,snd_seq
snd_seq_device         16532  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fglrx                2376104  34 
uvcvideo               69640  0 
snd                    81096  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211               43680  1 mac80211
shpchp                 44572  0 
joydev                 20864  0 
i2c_piix4              20112  0 
compat_ioctl32         18304  1 uvcvideo
videodev               45184  2 uvcvideo,compat_ioctl32
v4l1_compat            23940  2 uvcvideo,videodev
video                  29204  0 
psmouse                64028  0 
leds_hp_disk           11400  0 
led_class              13064  2 ath9k,leds_hp_disk
soundcore              16800  1 snd
serio_raw              14468  0 
output                 11648  1 video
pcspkr                 11136  0 
lis3lv02d              19408  0 
usbhid                 47040  0 
r8169                  46596  0 
mii                    14464  1 r8169
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit
compcache              13808  1 
lzo_decompress         11264  1 compcache
lzo_compress           11264  1 compcache
tlsf                   15392  1 compcache
lol@lol-laptop:~$ 



Please ask me for more information, or, perhaps, give me some! I am a fan of 'sound', you see; this is very important!

Thanks for reading my pleas!

---

### Post by exalangumna on 2009-08-17
tried uninstalling and reinstalling ALSA from scratch; but still no good.

---

### Post by exalangumna on 2009-08-17
i am doing things and this looked interesting: 

lol@lol-laptop:~$ pkill pulseaudio; sleep 2; pulseaudio -vv
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
D: main.c: Compilation host: x86_64-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pedantic -pipe -Wno-long-long -Wvla -Wno-overlength-strings -Wconversion -Wundef -Wformat -Wlogical-op -Wpacked -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wdeclaration-after-statement -Wfloat-equal -Wmissing-declarations -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-noreturn -Wshadow -Wendif-labels -Wpointer-arith -Wcast-align -Wwrite-strings -Wno-unused-parameter -ffast-math
D: main.c: Running on host: Linux x86_64 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 01:19:55 UTC 2009
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Optimized build: yes
I: main.c: Machine ID is f4af8c42db559e7dfb63b3cb4a831739.
I: main.c: Using runtime directory /home/lol/.pulse/f4af8c42db559e7dfb63b3cb4a831739:runtime.
I: main.c: Using state directory /home/lol/.pulse.
I: main.c: Running in system mode: no
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: memblock.c: Using shared memory pool with 1024 slots of size 64.0 KiB each, total size is 64.0 MiB, maximum usable slot size is 65472
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #0; argument: "").
I: module.c: Loaded "module-suspend-on-idle" (index: #1; argument: "").
I: module-device-restore.c: Sucessfully opened database file '/home/lol/.pulse/f4af8c42db559e7dfb63b3cb4a831739:device-volumes.x86_64-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-device-restore" (index: #2; argument: "").
I: module-stream-restore.c: Sucessfully opened database file '/home/lol/.pulse/f4af8c42db559e7dfb63b3cb4a831739:stream-volumes.x86_64-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-stream-restore" (index: #3; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-hal-detect.so': success
I: module-hal-detect.c: Trying capability alsa
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1002_960f_sound_card_0_alsa_control__1
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1002_960f_sound_card_0_alsa_hw_specific_0
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1002_960f_sound_card_0_alsa_playback_3
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_control__1
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_hw_specific_0
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_hw_specific_1
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0 tsched=0'
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
I: module-alsa-sink.c: Successfully opened device front:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: module-device-restore.c: Restoring volume for sink alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0.
I: module-device-restore.c: Restoring mute state for sink alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0.
I: sink.c: Created sink 0 "alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-device-restore.c: Restoring volume for source alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0.monitor.
I: module-device-restore.c: Restoring mute state for source alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0.monitor.
I: source.c: Created source 0 "alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-alsa-sink.c: Using 8 fragments of size 1792 bytes, buffer time is 81.27ms
D: module-alsa-sink.c: hwbuf_unused=0
D: module-alsa-sink.c: setting avail_min=1
I: module-alsa-sink.c: Volume ranges from 0 to 127.
I: module-alsa-sink.c: Volume ranges from -95.25 dB to 0.00 dB.
I: alsa-util.c: ALSA device lacks independant volume controls for each channel.
I: module-alsa-sink.c: Using hardware volume control. Hardware dB scale supported.
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
D: alsa-util.c:   stop_threshold   : 8070450532247928832
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 8070450532247928832
D: alsa-util.c: Slave: Hardware PCM card 0 'HDA ATI SB' device 0 subdevice 0
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
D: alsa-util.c:   period_eve
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
D: module-alsa-sink.c: Requested volume: 0: 100% 1: 100%
D: module-alsa-sink.c: Got hardware volume: 0: 100% 1: 100%
D: module-alsa-sink.c: Calculated software volume: 0: 100% 1: 100%
I: module-alsa-sink.c: Starting playback.
D: module-suspend-on-idle.c: Source alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0.monitor becomes idle.
D: module-suspend-on-idle.c: Sink alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0 becomes idle.
I: module.c: Loaded "module-alsa-sink" (index: #4; argument: "device_id=0 sink_name=alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0 tsched=0").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 source_name=alsa_input.pci_1002_4383_sound_card_0_alsa_capture_0 tsched=0'
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: module-device-restore.c: Restoring volume for source alsa_input.pci_1002_4383_sound_card_0_alsa_capture_0.
I: module-device-restore.c: Restoring mute state for source alsa_input.pci_1002_4383_sound_card_0_alsa_capture_0.
I: source.c: Created source 1 "alsa_input.pci_1002_4383_sound_card_0_alsa_capture_0" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-alsa-source.c: Using 8 fragments of size 1792 bytes, buffer time is 81.27ms
D: module-alsa-source.c: hwbuf_unused=0
D: module-alsa-source.c: setting avail_min=1
I: module-alsa-source.c: Volume ranges from 0 to 15.
I: module-alsa-source.c: Volume ranges from 0.00 dB to 22.50 dB.
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
D: alsa-util.c:   stop_threshold   : 8070450532247928832
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 8070450532247928832
D: alsa-util.c: Slave: Hardware PCM card 0 'HDA ATI SB' device 0 subdevice 0
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
D: alsa-util.c:   period_event
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
D: module-alsa-source.c: Requested volume: 0:  62% 1:  62%
D: module-alsa-source.c: Got hardware volume: 0:  62% 1:  62%
D: module-alsa-source.c: Calculated software volume: 0: 100% 1: 100%
D: module-suspend-on-idle.c: Source alsa_input.pci_1002_4383_sound_card_0_alsa_capture_0 becomes idle.
I: module.c: Loaded "module-alsa-source" (index: #5; argument: "device_id=0 source_name=alsa_input.pci_1002_4383_sound_card_0_alsa_capture_0 tsched=0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_playback_1
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer
I: module-hal-detect.c: Loaded 2 modules.
I: module.c: Loaded "module-hal-detect" (index: #6; argument: "tsched=0").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #7; argument: "").
I: module.c: Loaded "module-native-protocol-unix" (index: #8; argument: "").
I: module-default-device-restore.c: Restored default sink 'alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0'.
D: core-subscribe.c: Dropped redundant event due to change event.
I: module-default-device-restore.c: Restored default source 'alsa_input.pci_1002_4383_sound_card_0_alsa_capture_0'.
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
I: module-suspend-on-idle.c: Sink alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Source alsa_input.pci_1002_4383_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-console-kit.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-hal-detect.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionAdded
D: module-console-kit.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionAdded
D: module-hal-detect.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionAdded
D: module-console-kit.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionAdded
D: module-hal-detect.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionRemoved
D: module-console-kit.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionRemoved
D: module-hal-detect.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionRemoved
D: module-console-kit.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionRemoved
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-console-kit.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-console-kit.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-console-kit.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-console-kit.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-console-kit.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-console-kit.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-hal-detect.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionAdded
D: module-console-kit.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionAdded
D: module-hal-detect.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionRemoved
D: module-console-kit.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionRemoved
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-console-kit.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-console-kit.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-console-kit.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-console-kit.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-hal-detect.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionAdded
D: module-console-kit.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionAdded
D: module-hal-detect.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionRemoved
D: module-console-kit.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionRemoved
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-console-kit.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-hal-detect.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionAdded
D: module-console-kit.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionAdded
D: module-hal-detect.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionRemoved
D: module-console-kit.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionRemoved
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-console-kit.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified

---

### Post by exalangumna on 2009-08-17
this looks even more interesting; when i opened up system-preferences-sound; the terminal displayed this: 

I: client.c: Created 1 "Native client (UNIX socket client)"
I: client.c: Freed 1 "Native client (UNIX socket client)"
I: protocol-native.c: Connection died.
I: client.c: Created 2 "Native client (UNIX socket client)"
D: protocol-native.c: Protocol version: remote 14, local 14
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
D: protocol-native.c: SHM possible: yes
D: protocol-native.c: Negotiated SHM: yes
I: client.c: Freed 2 "gnome-sound-properties"
I: protocol-native.c: Connection died.
I: client.c: Created 3 "Native client (UNIX socket client)"
D: protocol-native.c: Protocol version: remote 14, local 14
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
D: protocol-native.c: SHM possible: yes
D: protocol-native.c: Negotiated SHM: yes
I: client.c: Freed 3 "gnome-sound-properties"
I: protocol-native.c: Connection died.
I: client.c: Created 4 "Native client (UNIX socket client)"
D: protocol-native.c: Protocol version: remote 14, local 14
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
D: protocol-native.c: SHM possible: yes
D: protocol-native.c: Negotiated SHM: yes
I: client.c: Freed 4 "gnome-sound-properties"
I: protocol-native.c: Connection died.
I: client.c: Created 5 "Native client (UNIX socket client)"
D: protocol-native.c: Protocol version: remote 14, local 14
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
D: protocol-native.c: SHM possible: yes
D: protocol-native.c: Negotiated SHM: yes
I: client.c: Freed 5 "gnome-sound-properties"
I: protocol-native.c: Connection died.
I: client.c: Created 6 "Native client (UNIX socket client)"
D: protocol-native.c: Protocol version: remote 14, local 14
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
D: protocol-native.c: SHM possible: yes
D: protocol-native.c: Negotiated SHM: yes
I: client.c: Freed 6 "gnome-sound-properties"
I: protocol-native.c: Connection died.
I: client.c: Created 7 "Native client (UNIX socket client)"
D: protocol-native.c: Protocol version: remote 14, local 14
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
D: protocol-native.c: SHM possible: yes
D: protocol-native.c: Negotiated SHM: yes
I: client.c: Freed 7 "gnome-sound-properties"
I: protocol-native.c: Connection died.
I: client.c: Created 8 "Native client (UNIX socket client)"
D: protocol-native.c: Protocol version: remote 14, local 14
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
D: protocol-native.c: SHM possible: yes
D: protocol-native.c: Negotiated SHM: yes
I: client.c: Freed 8 "gnome-sound-properties"
I: protocol-native.c: Connection died.
I: client.c: Created 9 "Native client (UNIX socket client)"
D: protocol-native.c: Protocol version: remote 14, local 14
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
D: protocol-native.c: SHM possible: yes
D: protocol-native.c: Negotiated SHM: yes
I: module-stream-restore.c: Restoring device for stream sink-input-by-application-name:ALSA plug-in [gnome-sound-properties].
I: module-stream-restore.c: Restoring volume for sink input sink-input-by-application-name:ALSA plug-in [gnome-sound-properties].
D: module-stream-restore.c: Not restoring mute state for sink input sink-input-by-application-name:ALSA plug-in [gnome-sound-properties], because already set.
I: module-alsa-sink.c: Trying resume...
D: module-alsa-sink.c: hwbuf_unused=0
D: module-alsa-sink.c: setting avail_min=1
I: module-alsa-sink.c: Resumed successfully...
D: module-suspend-on-idle.c: Sink alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0 becomes idle.
D: module-suspend-on-idle.c: Sink alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0 becomes busy.
I: resampler.c: Forcing resampler 'copy', because of fixed, identical sample rates.
D: resampler.c: Channel matrix:
D: resampler.c:        I00 
D: resampler.c:     +------
D: resampler.c: O00 | 1.000
D: resampler.c: O01 | 1.000
I: resampler.c: Using resampler 'copy'
I: resampler.c: Using float32le as working format.
D: memblockq.c: memblockq requested: maxlength=33554432, tlength=0, base=4, prebuf=0, minreq=1 maxrewind=0
D: memblockq.c: memblockq sanitized: maxlength=33554432, tlength=33554432, base=4, prebuf=0, minreq=4 maxrewind=0
I: sink-input.c: Created input 0 "ALSA Playback" on alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0 with sample spec s32le 1ch 44100Hz and channel map mono
I: protocol-native.c: Requested tlength=200.00 ms, minreq=10.00 ms
D: protocol-native.c: Early requests mode enabled, configuring sink latency to minreq.
D: memblockq.c: memblockq requested: maxlength=4194304, tlength=35280, base=4, prebuf=33516, minreq=1764 maxrewind=0
D: memblockq.c: memblockq sanitized: maxlength=4194304, tlength=35280, base=4, prebuf=33516, minreq=1764 maxrewind=0
I: protocol-native.c: Final latency 210.00 ms = 180.00 ms + 2*10.00 ms + 10.00 ms
I: module-alsa-sink.c: Starting playback.
D: module-alsa-sink.c: hwbuf_unused=0
D: module-alsa-sink.c: setting avail_min=1
D: protocol-native.c: Requesting rewind due to end of underrun.
D: sink-input.c: Requesting rewind due to corking
D: module-suspend-on-idle.c: Sink alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0 becomes idle.
D: module-alsa-sink.c: hwbuf_unused=0
D: module-alsa-sink.c: setting avail_min=1
D: module-suspend-on-idle.c: Sink alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0 becomes idle.
I: sink-input.c: Freeing input 0 "ALSA Playback"
I: module-stream-restore.c: Restoring device for stream sink-input-by-application-name:ALSA plug-in [gnome-sound-properties].
I: module-stream-restore.c: Restoring volume for sink input sink-input-by-application-name:ALSA plug-in [gnome-sound-properties].
D: module-stream-restore.c: Not restoring mute state for sink input sink-input-by-application-name:ALSA plug-in [gnome-sound-properties], because already set.
D: module-suspend-on-idle.c: Sink alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0 becomes busy.
I: resampler.c: Forcing resampler 'copy', because of fixed, identical sample rates.
D: resampler.c: Channel matrix:
D: resampler.c:        I00 
D: resampler.c:     +------
D: resampler.c: O00 | 1.000
D: resampler.c: O01 | 1.000
I: resampler.c: Using resampler 'copy'
I: resampler.c: Using float32le as working format.
D: memblockq.c: memblockq requested: maxlength=33554432, tlength=0, base=4, prebuf=0, minreq=1 maxrewind=0
D: memblockq.c: memblockq sanitized: maxlength=33554432, tlength=33554432, base=4, prebuf=0, minreq=4 maxrewind=0
I: sink-input.c: Created input 1 "ALSA Playback" on alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0 with sample spec s32le 1ch 44100Hz and channel map mono
I: protocol-native.c: Requested tlength=200.00 ms, minreq=10.00 ms
D: protocol-native.c: Early requests mode enabled, configuring sink latency to minreq.
D: memblockq.c: memblockq requested: maxlength=4194304, tlength=35280, base=4, prebuf=33516, minreq=1764 maxrewind=0
D: memblockq.c: memblockq sanitized: maxlength=4194304, tlength=35280, base=4, prebuf=33516, minreq=1764 maxrewind=0
I: protocol-native.c: Final latency 210.00 ms = 180.00 ms + 2*10.00 ms + 10.00 ms
D: module-alsa-sink.c: hwbuf_unused=0
D: module-alsa-sink.c: setting avail_min=1
D: sink-input.c: Requesting rewind due to corking
D: module-suspend-on-idle.c: Sink alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0 becomes idle.
D: module-alsa-sink.c: hwbuf_unused=0
D: module-alsa-sink.c: setting avail_min=1
D: module-suspend-on-idle.c: Sink alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0 becomes idle.
I: sink-input.c: Freeing input 1 "ALSA Playback"
I: module-stream-restore.c: Restoring device for stream sink-input-by-application-name:ALSA plug-in [gnome-sound-properties].
I: module-stream-restore.c: Restoring volume for sink input sink-input-by-application-name:ALSA plug-in [gnome-sound-properties].
D: module-stream-restore.c: Not restoring mute state for sink input sink-input-by-application-name:ALSA plug-in [gnome-sound-properties], because already set.
D: module-suspend-on-idle.c: Sink alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0 becomes busy.
I: resampler.c: Forcing resampler 'copy', because of fixed, identical sample rates.
D: resampler.c: Channel matrix:
D: resampler.c:        I00 
D: resampler.c:     +------
D: resampler.c: O00 | 1.000
D: resampler.c: O01 | 1.000
I: resampler.c: Using resampler 'copy'
I: resampler.c: Using float32le as working format.
D: memblockq.c: memblockq requested: maxlength=33554432, tlength=0, base=4, prebuf=0, minreq=1 maxrewind=0
D: memblockq.c: memblockq sanitized: maxlength=33554432, tlength=33554432, base=4, prebuf=0, minreq=4 maxrewind=0
I: sink-input.c: Created input 2 "ALSA Playback" on alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0 with sample spec s32le 1ch 44100Hz and channel map mono
I: protocol-native.c: Requested tlength=200.00 ms, minreq=10.00 ms
D: protocol-native.c: Early requests mode enabled, configuring sink latency to minreq.
D: memblockq.c: memblockq requested: maxlength=4194304, tlength=35280, base=4, prebuf=33516, minreq=1764 maxrewind=0
D: memblockq.c: memblockq sanitized: maxlength=4194304, tlength=35280, base=4, prebuf=33516, minreq=1764 maxrewind=0
I: protocol-native.c: Final latency 210.00 ms = 180.00 ms + 2*10.00 ms + 10.00 ms
D: module-alsa-sink.c: hwbuf_unused=0
D: module-alsa-sink.c: setting avail_min=1
D: sink-input.c: Requesting rewind due to corking
D: module-suspend-on-idle.c: Sink alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0 becomes idle.
D: module-alsa-sink.c: hwbuf_unused=0
D: module-alsa-sink.c: setting avail_min=1
D: module-suspend-on-idle.c: Sink alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0 becomes idle.
I: sink-input.c: Freeing input 2 "ALSA Playback"
I: client.c: Freed 9 "ALSA plug-in [gnome-sound-properties]"
I: protocol-native.c: Connection died.
I: module-suspend-on-idle.c: Sink alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
I: client.c: Created 10 "Native client (UNIX socket client)"
D: protocol-native.c: Protocol version: remote 14, local 14
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
D: protocol-native.c: SHM possible: yes
D: protocol-native.c: Negotiated SHM: yes
I: module-stream-restore.c: Restoring device for stream sink-input-by-application-name:gnome-sound-properties.
I: module-stream-restore.c: Restoring volume for sink input sink-input-by-application-name:gnome-sound-properties.
D: module-stream-restore.c: Not restoring mute state for sink input sink-input-by-application-name:gnome-sound-properties, because already set.
I: module-alsa-sink.c: Trying resume...
D: module-alsa-sink.c: hwbuf_unused=0
D: module-alsa-sink.c: setting avail_min=1
I: module-alsa-sink.c: Resumed successfully...
D: module-suspend-on-idle.c: Sink alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0 becomes idle.
D: module-suspend-on-idle.c: Sink alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0 becomes busy.
I: resampler.c: Forcing resampler 'copy', because of fixed, identical sample rates.
D: resampler.c: Channel matrix:
D: resampler.c:        I00 
D: resampler.c:     +------
D: resampler.c: O00 | 1.000
D: resampler.c: O01 | 1.000
I: resampler.c: Using resampler 'copy'
I: resampler.c: Using float32le as working format.
D: memblockq.c: memblockq requested: maxlength=33554432, tlength=0, base=4, prebuf=0, minreq=1 maxrewind=0
D: memblockq.c: memblockq sanitized: maxlength=33554432, tlength=33554432, base=4, prebuf=0, minreq=4 maxrewind=0
I: sink-input.c: Created input 3 "Playback Stream" on alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0 with sample spec float32le 1ch 44100Hz and channel map mono
I: protocol-native.c: Requested tlength=200.00 ms, minreq=10.00 ms
D: protocol-native.c: Adjust latency mode enabled, configuring sink latency to half of overall latency.
D: memblockq.c: memblockq requested: maxlength=70560, tlength=19404, base=4, prebuf=17644, minreq=1764 maxrewind=0
D: memblockq.c: memblockq sanitized: maxlength=70560, tlength=19404, base=4, prebuf=17644, minreq=1764 maxrewind=0
I: protocol-native.c: Final latency 200.00 ms = 90.00 ms + 2*10.00 ms + 90.00 ms
I: module-alsa-sink.c: Starting playback.
D: module-alsa-sink.c: hwbuf_unused=0
D: module-alsa-sink.c: setting avail_min=1
D: sink-input.c: Requesting rewind due to uncorking
D: module-suspend-on-idle.c: Sink alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0 becomes busy.
D: protocol-native.c: Requesting rewind due to end of underrun.
D: sink-input.c: Requesting rewind due to corking
D: module-suspend-on-idle.c: Sink alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0 becomes idle.
D: module-alsa-sink.c: hwbuf_unused=0
D: module-alsa-sink.c: setting avail_min=1
D: module-suspend-on-idle.c: Sink alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0 becomes idle.
I: sink-input.c: Freeing input 3 "audiotest wave"
I: client.c: Freed 10 "gnome-sound-properties"
I: protocol-native.c: Connection died.
I: module-suspend-on-idle.c: Sink alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...

---

### Post by exalangumna on 2009-08-21
Can anyone help me with this? I've tried switching between kubuntu/ubuntu and 64 and 32 bit, and nothing works.

---

