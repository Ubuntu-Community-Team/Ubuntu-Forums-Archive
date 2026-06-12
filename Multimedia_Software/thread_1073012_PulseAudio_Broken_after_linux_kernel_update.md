---
title: "PulseAudio Broken after linux kernel update"
date: 2009-02-17
forum: Multimedia Software
---

### Post by jjtechno on 2009-02-17
I did the upgrade to 2.6.27-11 linux kernel and my audio is gone. I show volume when I am playing and I walked through the sticky guides.. 
I am missing something I am not sure what?
Included the  files:
 List of PLAYBACK Hardware Devices ****
card 0: Audigy2 [Audigy 2 [SB0350b]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 31/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy2 [Audigy 2 [SB0350b]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy2 [Audigy 2 [SB0350b]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Audigy2 [Audigy 2 [SB0350b]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
and the results of :

:~$ pkill pulseaudio; sleep 2; pulseaudio -vv
I: main.c: PolicyKit refuses acquire-high-priority privilige.
I: main.c: Called SUID root and real-time/high-priority scheduling was requested in the configuration. However, we lack the necessary priviliges:
I: main.c: We are not in group 'pulse-rt' and PolicyKit refuse to grant us priviliges. Dropping SUID again.
I: main.c: For enabling real-time scheduling please acquire the appropriate PolicyKit priviliges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
I: main.c: Note that real-time/high-priority scheduling is NOT normally required. If you experience crackling or other sound anomalies, consider one or more of the above solutions.
I: main.c: High-priority scheduling enabled in configuration but now allowed by policy. Disabling forcibly.
W: ltdl-bind-now.c: Failed to find original dlopen loader.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: main.c: This is PulseAudio 0.9.10
I: main.c: Page size is 4096 bytes
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-hal-detect.so': success
I: module-hal-detect.c: Trying capability alsa
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_4_sound_card_0_alsa_playback_4
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_4_sound_card_0_alsa_capture_4
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_4_sound_card_0_alsa_playback_3
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_4_sound_card_0_alsa_playback_2
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_4_sound_card_0_alsa_capture_2
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_4_sound_card_0_alsa_capture_1
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_1102_4_sound_card_0_alsa_playback_0'
D: alsa-util.c: Trying front:0...
I: module-alsa-sink.c: Successfully opened device front:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: sink.c: Created sink 0 "alsa_output.pci_1102_4_sound_card_0_alsa_playback_0" with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 0 "alsa_output.pci_1102_4_sound_card_0_alsa_playback_0.monitor" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-sink.c: Using 8 fragments of size 1760 bytes.
I: alsa-util.c: ALSA device lacks independant volume controls for each channel, falling back to software volume control.
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #0; argument: "device_id=0 sink_name=alsa_output.pci_1102_4_sound_card_0_alsa_playback_0").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 source_name=alsa_input.pci_1102_4_sound_card_0_alsa_capture_0'
D: alsa-util.c: Trying front:0...
ALSA lib setup.c:96:(snd_sctl_install) Cannot lock ctl elem
I: alsa-util.c: PCM device front:0 refused our hw parameters: Device or resource busy
D: alsa-util.c: Trying surround40:0...
I: alsa-util.c: Couldn't open PCM device surround40:0: Device or resource busy
D: alsa-util.c: Trying surround41:0...
I: alsa-util.c: Couldn't open PCM device surround41:0: Device or resource busy
D: alsa-util.c: Trying surround50:0...
I: alsa-util.c: Couldn't open PCM device surround50:0: Device or resource busy
D: alsa-util.c: Trying surround51:0...
I: alsa-util.c: Couldn't open PCM device surround51:0: Device or resource busy
D: alsa-util.c: Trying surround71:0...
I: alsa-util.c: Couldn't open PCM device surround71:0: Device or resource busy
D: alsa-util.c: Trying hw:0 as last resort...
I: module-alsa-source.c: Successfully opened device hw:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Cannot find mixer control "Capture".
I: alsa-util.c: Using mixer control "Mic".
I: source.c: Created source 1 "alsa_input.pci_1102_4_sound_card_0_alsa_capture_0" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-source.c: Using 2 fragments of size 1792 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
I: module.c: Loaded "module-alsa-source" (index: #1; argument: "device_id=0 source_name=alsa_input.pci_1102_4_sound_card_0_alsa_capture_0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_4_sound_card_0_alsa_midi_3
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_4_sound_card_0_alsa_midi_2
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_4_sound_card_0_alsa_midi_1
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_4_sound_card_0_alsa_midi_0
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_4_sound_card_0_alsa_hw_specific_2
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_4_sound_card_0_alsa_hw_specific_0
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_4_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 2 modules.
I: module.c: Loaded "module-hal-detect" (index: #2; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #3; argument: "").
I: protocol-native.c: loading cookie from disk.
I: module.c: Loaded "module-native-protocol-unix" (index: #4; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
D: module-gconf.c: Loading module 'module-null-sink' with args 'sink_name=rtp format=s16be channels=2 rate=44100 description="RTP Multicast Sink"' due to GConf configuration.
I: sink.c: Created sink 1 "rtp" with sample spec "s16be 2ch 44100Hz"
I: source.c: Created source 2 "rtp.monitor" with sample spec "s16be 2ch 44100Hz"
D: module-null-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+27
I: module.c: Loaded "module-null-sink" (index: #5; argument: "sink_name=rtp format=s16be channels=2 rate=44100 description="RTP Multicast Sink"").
D: module-gconf.c: Loading module 'module-rtp-send' with args 'source=rtp.monitor loop=1' due to GConf configuration.
I: source-output.c: Created output 0 "RTP Monitor Stream" on rtp.monitor with sample spec s16be 2ch 44100Hz and channel map front-left,front-right
D: memblockq.c: memblockq requested: maxlength=174080, tlength=174080, base=4, prebuf=1, minreq=0
D: memblockq.c: memblockq sanitized: maxlength=174080, tlength=174080, base=4, prebuf=4, minreq=4
I: module-rtp-send.c: RTP stream initialized with mtu 1280 on 224.0.0.56:46392, SSRC=0x440f990d, payload=10, initial sequence #13894
I: module-rtp-send.c: SDP-Data:
I: module-rtp-send.c: v=0
I: module-rtp-send.c: o=jaye 3443913692 0 IN IP4 192.168.0.192
I: module-rtp-send.c: s=PulseAudio RTP Stream on TheZoo
I: module-rtp-send.c: c=IN IP4 224.0.0.56
I: module-rtp-send.c: t=3443913692 0
I: module-rtp-send.c: a=recvonly
I: module-rtp-send.c: m=audio 46392 RTP/AVP 10
I: module-rtp-send.c: a=rtpmap:10 L16/44100/2
I: module-rtp-send.c: a=type:broadcast
I: module-rtp-send.c: EOF
I: module.c: Loaded "module-rtp-send" (index: #6; argument: "source=rtp.monitor loop=1").
D: module-gconf.c: Loading module 'module-combine' with args '' due to GConf configuration.
I: sink.c: Created sink 2 "combined" with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 3 "combined.monitor" with sample spec "s16le 2ch 44100Hz"
D: memblockq.c: memblockq requested: maxlength=174080, tlength=174080, base=4, prebuf=1, minreq=0
D: memblockq.c: memblockq sanitized: maxlength=174080, tlength=174080, base=4, prebuf=4, minreq=4
I: resampler.c: Using resampler 'trivial'
I: resampler.c: Using s16le as working format.
I: sink-input.c: Created input 0 "Simultaneous output on ALSA PCM on front:0 (ADC Capture/Standard PCM Playback) via DMA" on alsa_output.pci_1102_4_sound_card_0_alsa_playback_0 with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-combine.c: Master sink is now 'alsa_output.pci_1102_4_sound_card_0_alsa_playback_0'
D: module-combine.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+26
I: module.c: Loaded "module-combine" (index: #7; argument: "").
D: module-gconf.c: Loading module 'module-rtp-recv' with args '' due to GConf configuration.
I: module.c: Loaded "module-rtp-recv" (index: #8; argument: "").
D: module-gconf.c: Loading module 'module-native-protocol-tcp' with args 'auth-anonymous=1' due to GConf configuration.
I: protocol-native.c: using already loaded auth cookie.
I: protocol-native.c: using already loaded auth cookie.
I: module.c: Loaded "module-native-protocol-tcp" (index: #9; argument: "auth-anonymous=1").
D: module-gconf.c: Loading module 'module-esound-protocol-tcp' with args 'auth-anonymous=1' due to GConf configuration.
I: module.c: Loaded "module-esound-protocol-tcp" (index: #10; argument: "auth-anonymous=1").
D: module-gconf.c: Loading module 'module-zeroconf-publish' with args '' due to GConf configuration.
D: module-zeroconf-publish.c: Publishing services in Zeroconf
D: module-zeroconf-publish.c: Successfully created entry group for jaye@TheZoo: ALSA PCM on front:0 (ADC Capture/Standard PCM Play.
D: module-zeroconf-publish.c: Successfully created entry group for jaye@TheZoo: RTP Multicast Sink.
D: module-zeroconf-publish.c: Successfully created entry group for jaye@TheZoo: Simultaneous output to ALSA PCM on front:0 (ADC Ca.
D: module-zeroconf-publish.c: Successfully created entry group for jaye@TheZoo: ALSA PCM on hw:0 (ADC Capture/Standard PCM Playbac.
I: module.c: Loaded "module-zeroconf-publish" (index: #11; argument: "").
D: module-gconf.c: Loading module 'module-zeroconf-discover' with args '' due to GConf configuration.
I: module.c: Loaded "module-zeroconf-discover" (index: #12; argument: "").
I: module.c: Loaded "module-gconf" (index: #13; argument: "").
I: module.c: Loaded "module-volume-restore" (index: #14; argument: "").
D: module-default-device-restore.c: Restored default sink 'alsa_output.pci_1102_4_sound_card_0_alsa_playback_0'.
D: core-subscribe.c: dropped redundant event.
D: module-default-device-restore.c: Restored default source 'alsa_input.pci_1102_4_sound_card_0_alsa_capture_0'.
I: module.c: Loaded "module-default-device-restore" (index: #15; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #16; argument: "").
D: module-suspend-on-idle.c: Sink rtp becomes idle.
D: module-suspend-on-idle.c: Sink combined becomes idle.
D: module-suspend-on-idle.c: Source alsa_output.pci_1102_4_sound_card_0_alsa_playback_0.monitor becomes idle.
D: module-suspend-on-idle.c: Source alsa_input.pci_1102_4_sound_card_0_alsa_capture_0 becomes idle.
D: module-suspend-on-idle.c: Source combined.monitor becomes idle.
I: module.c: Loaded "module-suspend-on-idle" (index: #17; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-x11-publish.so': success
D: module-x11-publish.c: using already loaded auth cookie.
I: module.c: Loaded "module-x11-publish" (index: #18; argument: "").
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module-zeroconf-publish.c: Successfully established service jaye@TheZoo: ALSA PCM on front:0 (ADC Capture/Standard PCM Play.
I: module-zeroconf-publish.c: Successfully established service jaye@TheZoo: RTP Multicast Sink.
I: module-zeroconf-publish.c: Successfully established service jaye@TheZoo: Simultaneous output to ALSA PCM on front:0 (ADC Ca.
I: module-zeroconf-publish.c: Successfully established service jaye@TheZoo: ALSA PCM on hw:0 (ADC Capture/Standard PCM Playbac.
I: module-zeroconf-publish.c: Successfully established main service.
I: module-suspend-on-idle.c: Source combined.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Source alsa_input.pci_1102_4_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.pci_1102_4_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Sink combined idle for too long, suspending ...
D: module-suspend-on-idle.c: Sink alsa_output.pci_1102_4_sound_card_0_alsa_playback_0 becomes idle.
D: module-suspend-on-idle.c: Sink alsa_output.pci_1102_4_sound_card_0_alsa_playback_0 becomes idle.
I: sink-input.c: Freeing output 0 "Simultaneous output on ALSA PCM on front:0 (ADC Capture/Standard PCM Playback) via DMA"
I: module-combine.c: No master selected, lacking suitable outputs.
I: module-combine.c: Device suspended...
I: module-suspend-on-idle.c: Sink rtp idle for too long, suspending ...
I: module-suspend-on-idle.c: Sink alsa_output.pci_1102_4_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
I: module-alsa-sink.c: Trying resume...
I: module-alsa-sink.c: Resumed successfully...
I: module-alsa-sink.c: Starting playback.
D: module-suspend-on-idle.c: Sink alsa_output.pci_1102_4_sound_card_0_alsa_playback_0 becomes idle.
D: module-suspend-on-idle.c: Sink alsa_output.pci_1102_4_sound_card_0_alsa_playback_0 becomes busy.
I: resampler.c: Forcing resampler 'copy', because of fixed, identical sample rates.
I: resampler.c: Using resampler 'copy'
I: resampler.c: Using s16le as working format.
I: sink-input.c: Created input 1 "RTP Stream (PulseAudio RTP Stream on TheZoo)" on alsa_output.pci_1102_4_sound_card_0_alsa_playback_0 with sample spec s16be 2ch 44100Hz and channel map front-left,front-right
D: memblockq.c: memblockq requested: maxlength=174080, tlength=174080, base=4, prebuf=17641, minreq=0
D: memblockq.c: memblockq sanitized: maxlength=174080, tlength=174080, base=4, prebuf=17644, minreq=4
I: module-rtp-recv.c: New session 'PulseAudio RTP Stream on TheZoo'
D: module-rtp-recv.c: Checking for dead streams ...

---

### Post by greyfox1 on 2009-02-21
Hi jjtechno,

I've read that for some reason with this particular kernel, one setting gets changed during the update process that shouldn't and messes with your config.  See [this page]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/310179") for more info and a fix (just read the thread for instructions).

Hope this helps!

---

