---
title: "Why am I getting No sound and No help?"
date: 2009-06-24
forum: Multimedia Software
---

### Post by tpgames on 2009-06-24
Okay, I have tried new things, I've added to my original post and was ignored. Maybe someone thought I was communicating with someone. :-\"  Sorry if iconfused people. (I realized that all those with knowledge are super busy elsewhere. :D ) I redid everything that manual said posted the results and was ignored and I still have no sound and one blasted error that is so obvious that someone should know what the items is I need to completely purge and reinstall. I did try purging gnome-alsa mixer and reinstalling it but can't prove it as i can't find that data. I think I must have used synaptic manager because I thought I saved all my terminal data. I'm going to try this again and the edit this post with the results using get-apt remove command. 
ps. The Pulse Audio Volume Control says that no streams available after I tried playing Rhythm box to see if I have sound. I did uninstall gnome-alsa mixer and reinstalled ubuntu desktop.  Still no sound. 

 I did try deleting my other thread. Couldn't! Below is the link to the txt files in a folder on my website (with no links to or words about anything in my website. Links below are strictly for resolving this issue. ) 

Here is the blasted error:
[Complete Error test here]("http://www.tpgames.net/files/gnome-alsaERROR-MSG.txt")
[Here is the Last group of stuff I did complete with results.]("http://www.tpgames.net/files/2.txt")

[URL="http://www.tpgames.net/files/"]UPDATE- Folder with all latest I did as more was done. 
[/URL] 
Here is tinybit of the error:
```
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9708,11-Master": `,' is an invalid character in key/directory names

```Thanks for ANY help I get. 

Update: I removed it using apt-get but can not reinstall it using apt-get. So, I reinstalled it using synaptic package manager.  Did check and no sound at this point. And same error message about bad directory or key. 
```
jyzrxal@jyzrxal-desktop:~$ sudo apt-get remove gnome-alsamixer
[sudo] password for jyzrxal: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-zopeinterface python-twisted-core python-editobj python-cerealizer
  libcal3d12 python-soya python-tofu libode0debian1 python-twisted-bin
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  gnome-alsamixer
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 602kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 243803 files and directories currently installed.)
Removing gnome-alsamixer ...
jyzrxal@jyzrxal-desktop:~$ sudo apt-get gnome-alsamixer
E: Invalid operation gnome-alsamixer

```And the details of the synaptic reinstall.
```

Unpacking gnome-alsamixer (from.../gnome-alsamixer_0.9.7~cvs.20060916.ds.1-1_i386.deb
Setting up gnome-alsa mixer.....

```Thanks for anyhelp I get. I'm not going to try anything else until I get some response as their is nothing I know to  do. 
By the way, my 8.04 Ubuntu is fresh install and not an upgrade if that should matter. And, I had no sound before the fresh install.

---

### Post by dmizer on 2009-06-26
Looks like a config file has been edited incorrectly. Don't know much about sound, but it seems to be complaining that there is a comma where there shouldn't be.

Have you seen either of these threads?
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by alphacrucis2 on 2009-06-26
[QUOTE=tpgames;7507831]
```

jyzrxal@jyzrxal-desktop:~$ sudo apt-get gnome-alsamixer
E: Invalid operation gnome-alsamixer

```

The command should be

```
sudo apt-get **install** gnome-alsamixer
```

---

### Post by tpgames on 2009-06-26
Here's is what I get now PLUS the gnome-alsa mixer configuration error:
The application **does not** play audio and **does** list an entry in the Playback tab;
 [COLOR=Blue]- the application is using PulseAudio but there is a problem, such as: a bug in PulseAudio, a problem with your ALSA kernel module or libraries, or your PCM/Master volume is muted.[/COLOR]

Here is the information that the how-to requests that I post:
1) I did edit the source list a second time. I am using 8.04, amd but I believe its a 32-bit as computer is older. 
2) This is with the Radio Rhythm box on as I forgot to turn it off first:
```
 jyzrxal@jyzrxal-desktop:~$  aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
```3) ```
 jyzrxal@jyzrxal-desktop:~$  pkill pulseaudio; sleep 2; pulseaudio -vv
I: main.c: Called SUID root and real-time/high-priority scheduling was requested in the configuration. However, we lack the necessary priviliges:
I: main.c: We are not in group 'pulse-rt' and PolicyKit refuse to grant us priviliges. Dropping SUID again.
I: main.c: For enabling real-time scheduling please acquire the appropriate PolicyKit priviliges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
I: main.c: Note that real-time/high-priority scheduling is NOT normally required. If you experience crackling or other sound anomalies, consider one or more of the above solutions.
I: main.c: High-priority scheduling enabled in configuration but now allowed by policy. Disabling forcibly.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: main.c: This is PulseAudio 0.9.10
I: main.c: Page size is 4096 bytes
I: main.c: Fresh high-resolution timers available! Bon appetit!
OIL: ERROR liboiltest.c 361: oil_test_check_impl(): illegal instruction in mmxCombineAddU
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-hal-detect.so': success
I: module-hal-detect.c: Trying capability alsa
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1274_1371_sound_card_0_alsa_playback_1
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_1274_1371_sound_card_0_alsa_playback_0'
D: alsa-util.c: Trying front:0...
I: module-alsa-sink.c: Successfully opened device front:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: sink.c: Created sink 0 "alsa_output.pci_1274_1371_sound_card_0_alsa_playback_0" with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 0 "alsa_output.pci_1274_1371_sound_card_0_alsa_playback_0.monitor" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-sink.c: Using 8 fragments of size 880 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #0; argument: "device_id=0 sink_name=alsa_output.pci_1274_1371_sound_card_0_alsa_playback_0").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 source_name=alsa_input.pci_1274_1371_sound_card_0_alsa_capture_0'
D: alsa-util.c: Trying front:0...
W: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 44099 Hz.
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: source.c: Created source 1 "alsa_input.pci_1274_1371_sound_card_0_alsa_capture_0" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-source.c: Using 8 fragments of size 880 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
I: module.c: Loaded "module-alsa-source" (index: #1; argument: "device_id=0 source_name=alsa_input.pci_1274_1371_sound_card_0_alsa_capture_0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1274_1371_sound_card_0_alsa_midi_0
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1274_1371_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 2 modules.
I: module.c: Loaded "module-hal-detect" (index: #2; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #3; argument: "").
I: protocol-native.c: loading cookie from disk.
I: module.c: Loaded "module-native-protocol-unix" (index: #4; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
D: module-gconf.c: Loading module 'module-rtp-send' with args 'source=@DEFAULT_SOURCE@ loop=0' due to GConf configuration.
I: resampler.c: Forcing resampler 'copy', because of fixed, identical sample rates.
I: resampler.c: Using resampler 'copy'
I: resampler.c: Using s16le as working format.
I: source-output.c: Created output 0 "RTP Monitor Stream" on alsa_input.pci_1274_1371_sound_card_0_alsa_capture_0 with sample spec s16be 2ch 44100Hz and channel map front-left,front-right
D: memblockq.c: memblockq requested: maxlength=174080, tlength=174080, base=4, prebuf=1, minreq=0
D: memblockq.c: memblockq sanitized: maxlength=174080, tlength=174080, base=4, prebuf=4, minreq=4
I: module-rtp-send.c: RTP stream initialized with mtu 1280 on 224.0.0.56:46132, SSRC=0xae41302a, payload=10, initial sequence #14670
I: module-rtp-send.c: SDP-Data:
I: module-rtp-send.c: v=0
I: module-rtp-send.c: o=jyzrxal 3455043696 0 IN IP4 192.168.2.7
I: module-rtp-send.c: s=PulseAudio RTP Stream on jyzrxal-desktop
I: module-rtp-send.c: c=IN IP4 224.0.0.56
I: module-rtp-send.c: t=3455043696 0
I: module-rtp-send.c: a=recvonly
I: module-rtp-send.c: m=audio 46132 RTP/AVP 10
I: module-rtp-send.c: a=rtpmap:10 L16/44100/2
I: module-rtp-send.c: a=type:broadcast
I: module-rtp-send.c: EOF
I: module.c: Loaded "module-rtp-send" (index: #5; argument: "source=@DEFAULT_SOURCE@ loop=0").
D: module-gconf.c: Loading module 'module-combine' with args '' due to GConf configuration.
I: sink.c: Created sink 1 "combined" with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 2 "combined.monitor" with sample spec "s16le 2ch 44100Hz"
D: memblockq.c: memblockq requested: maxlength=174080, tlength=174080, base=4, prebuf=1, minreq=0
D: memblockq.c: memblockq sanitized: maxlength=174080, tlength=174080, base=4, prebuf=4, minreq=4
I: resampler.c: Using resampler 'trivial'
I: resampler.c: Using s16le as working format.
I: sink-input.c: Created input 0 "Simultaneous output on ALSA PCM on front:0 (ES1371 DAC2/ADC) via DMA" on alsa_output.pci_1274_1371_sound_card_0_alsa_playback_0 with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-combine.c: Master sink is now 'alsa_output.pci_1274_1371_sound_card_0_alsa_playback_0'
D: module-combine.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+27
I: module.c: Loaded "module-combine" (index: #6; argument: "").
D: module-gconf.c: Loading module 'module-rtp-recv' with args '' due to GConf configuration.
I: module.c: Loaded "module-rtp-recv" (index: #7; argument: "").
D: module-gconf.c: Loading module 'module-native-protocol-tcp' with args '' due to GConf configuration.
I: protocol-native.c: using already loaded auth cookie.
I: protocol-native.c: using already loaded auth cookie.
I: module.c: Loaded "module-native-protocol-tcp" (index: #8; argument: "").
D: module-gconf.c: Loading module 'module-esound-protocol-tcp' with args '' due to GConf configuration.
I: module.c: Loaded "module-esound-protocol-tcp" (index: #9; argument: "").
D: module-gconf.c: Loading module 'module-zeroconf-discover' with args '' due to GConf configuration.
I: module.c: Loaded "module-zeroconf-discover" (index: #10; argument: "").
I: module.c: Loaded "module-gconf" (index: #11; argument: "").
I: module.c: Loaded "module-volume-restore" (index: #12; argument: "").
D: module-default-device-restore.c: Restored default sink 'alsa_output.pci_1274_1371_sound_card_0_alsa_playback_0'.
I: module-default-device-restore.c: Manually configured default source, not overwriting.
I: module.c: Loaded "module-default-device-restore" (index: #13; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #14; argument: "").
D: module-suspend-on-idle.c: Sink combined becomes idle.
D: module-suspend-on-idle.c: Source alsa_output.pci_1274_1371_sound_card_0_alsa_playback_0.monitor becomes idle.
D: module-suspend-on-idle.c: Source combined.monitor becomes idle.
I: module.c: Loaded "module-suspend-on-idle" (index: #15; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-x11-publish.so': success
D: module-x11-publish.c: using already loaded auth cookie.
I: module.c: Loaded "module-x11-publish" (index: #16; argument: "").
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module-suspend-on-idle.c: Sink combined idle for too long, suspending ...
D: module-suspend-on-idle.c: Sink alsa_output.pci_1274_1371_sound_card_0_alsa_playback_0 becomes idle.
D: module-suspend-on-idle.c: Sink alsa_output.pci_1274_1371_sound_card_0_alsa_playback_0 becomes idle.
I: sink-input.c: Freeing output 0 "Simultaneous output on ALSA PCM on front:0 (ES1371 DAC2/ADC) via DMA"
I: module-combine.c: No master selected, lacking suitable outputs.
I: module-combine.c: Device suspended...
I: module-suspend-on-idle.c: Source combined.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Source alsa_output.pci_1274_1371_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Sink alsa_output.pci_1274_1371_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...

```Then it keeps repeating the last line over and over again.  

This is with Rhythm box and everything audio closed:
```

jyzrxal@jyzrxal-desktop:~$  pkill pulseaudio; sleep 2; pulseaudio -v
I: main.c: Called SUID root and real-time/high-priority scheduling was requested in the configuration. However, we lack the necessary priviliges:
I: main.c: We are not in group 'pulse-rt' and PolicyKit refuse to grant us priviliges. Dropping SUID again.
I: main.c: For enabling real-time scheduling please acquire the appropriate PolicyKit priviliges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
I: main.c: Note that real-time/high-priority scheduling is NOT normally required. If you experience crackling or other sound anomalies, consider one or more of the above solutions.
I: main.c: High-priority scheduling enabled in configuration but now allowed by policy. Disabling forcibly.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: main.c: This is PulseAudio 0.9.10
I: main.c: Page size is 4096 bytes
I: main.c: Fresh high-resolution timers available! Bon appetit!
OIL: ERROR liboiltest.c 361: oil_test_check_impl(): illegal instruction in mmxCombineAddU
I: module-hal-detect.c: Trying capability alsa
I: module-alsa-sink.c: Successfully opened device front:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: sink.c: Created sink 0 "alsa_output.pci_1274_1371_sound_card_0_alsa_playback_0" with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 0 "alsa_output.pci_1274_1371_sound_card_0_alsa_playback_0.monitor" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-sink.c: Using 8 fragments of size 880 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #0; argument: "device_id=0 sink_name=alsa_output.pci_1274_1371_sound_card_0_alsa_playback_0").
W: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 44099 Hz.
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: source.c: Created source 1 "alsa_input.pci_1274_1371_sound_card_0_alsa_capture_0" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-source.c: Using 8 fragments of size 880 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
I: module.c: Loaded "module-alsa-source" (index: #1; argument: "device_id=0 source_name=alsa_input.pci_1274_1371_sound_card_0_alsa_capture_0").
I: module-hal-detect.c: Loaded 2 modules.
I: module.c: Loaded "module-hal-detect" (index: #2; argument: "").
I: module.c: Loaded "module-esound-protocol-unix" (index: #3; argument: "").
I: protocol-native.c: loading cookie from disk.
I: module.c: Loaded "module-native-protocol-unix" (index: #4; argument: "").
I: resampler.c: Forcing resampler 'copy', because of fixed, identical sample rates.
I: resampler.c: Using resampler 'copy'
I: resampler.c: Using s16le as working format.
I: source-output.c: Created output 0 "RTP Monitor Stream" on alsa_input.pci_1274_1371_sound_card_0_alsa_capture_0 with sample spec s16be 2ch 44100Hz and channel map front-left,front-right
I: module-rtp-send.c: RTP stream initialized with mtu 1280 on 224.0.0.56:46626, SSRC=0x1a687df3, payload=10, initial sequence #28922
I: module-rtp-send.c: SDP-Data:
I: module-rtp-send.c: v=0
I: module-rtp-send.c: o=jyzrxal 3455044867 0 IN IP4 192.168.2.7
I: module-rtp-send.c: s=PulseAudio RTP Stream on jyzrxal-desktop
I: module-rtp-send.c: c=IN IP4 224.0.0.56
I: module-rtp-send.c: t=3455044867 0
I: module-rtp-send.c: a=recvonly
I: module-rtp-send.c: m=audio 46626 RTP/AVP 10
I: module-rtp-send.c: a=rtpmap:10 L16/44100/2
I: module-rtp-send.c: a=type:broadcast
I: module-rtp-send.c: EOF
I: module.c: Loaded "module-rtp-send" (index: #5; argument: "source=@DEFAULT_SOURCE@ loop=0").
I: sink.c: Created sink 1 "combined" with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 2 "combined.monitor" with sample spec "s16le 2ch 44100Hz"
I: resampler.c: Using resampler 'trivial'
I: resampler.c: Using s16le as working format.
I: sink-input.c: Created input 0 "Simultaneous output on ALSA PCM on front:0 (ES1371 DAC2/ADC) via DMA" on alsa_output.pci_1274_1371_sound_card_0_alsa_playback_0 with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-combine.c: Master sink is now 'alsa_output.pci_1274_1371_sound_card_0_alsa_playback_0'
I: module.c: Loaded "module-combine" (index: #6; argument: "").
I: module.c: Loaded "module-rtp-recv" (index: #7; argument: "").
I: protocol-native.c: using already loaded auth cookie.
I: protocol-native.c: using already loaded auth cookie.
I: module.c: Loaded "module-native-protocol-tcp" (index: #8; argument: "").
I: module.c: Loaded "module-esound-protocol-tcp" (index: #9; argument: "").
I: module.c: Loaded "module-zeroconf-discover" (index: #10; argument: "").
I: module.c: Loaded "module-gconf" (index: #11; argument: "").
I: module.c: Loaded "module-volume-restore" (index: #12; argument: "").
I: module-default-device-restore.c: Manually configured default source, not overwriting.
I: module.c: Loaded "module-default-device-restore" (index: #13; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #14; argument: "").
I: module.c: Loaded "module-suspend-on-idle" (index: #15; argument: "").
I: module.c: Loaded "module-x11-publish" (index: #16; argument: "").
I: main.c: Daemon startup complete.
I: module-suspend-on-idle.c: Source combined.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Source alsa_output.pci_1274_1371_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Sink combined idle for too long, suspending ...
I: sink-input.c: Freeing output 0 "Simultaneous output on ALSA PCM on front:0 (ES1371 DAC2/ADC) via DMA"
I: module-combine.c: No master selected, lacking suitable outputs.
I: module-combine.c: Device suspended...
I: module-suspend-on-idle.c: Sink alsa_output.pci_1274_1371_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...

```Then it hangs here. 

So 1)  How do I reconfigure the gnome-alsa mixer configurations so that I don't get this...
```
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9708,11-Master": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9708,11-Master": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9708,11-Master_Mono": `,' is an invalid character in key/directory names
etc.

```2) How do I resolve the sound issues, now that I finally got the system recognized on the tab? (I did use Rhythm box before). 

3) Is it possible to accidentally delete a sound card? I thought it was like a chip, but can't remember for sure. The computer I'm fixing did have stuff arbitrarilly deleted (not by me) without thought to what was being deleted. I did try a fresh install of the system, but am not sure if any damage was done to the sound cards, or anything to do with sound. I also don't know how to check this except as to what was posted in the above links, which I had done before, and redid today as I thought I had typos when I did it before. 

Thanks!  :D

---

### Post by tpgames on 2009-07-01
I think I should BUMP this thread to the NEWBIE forum as NO ONE is here is going to be able to help me anyways. I've already bumped this once and really do not like to spam boards. I will, however, only post the last bit as posting the entire thread I believe is wrong. So, anyone else with these issues maybe might want to consider the newbie area as perhaps your issue is with beginning level configuration issues which really is better served there perhaps. If I am wrong in this matter, then maybe we need to find more help in this forum as it appears to me, we have 100,000 people with questions to every 1 person with answers.

---

### Post by dmizer on 2009-07-01
> **tpgames said:**
> If I am wrong in this matter, then maybe we need to find more help in this forum as it appears to me, we have 100,000 people with questions to every 1 person with answers.

Actually, it's been my experience that most people at least get replies with useful information and potential answers. Your problem seems to be extremely unusual. Frankly I don't see how moving it to the beginners area will get you any more replies than you are now.

It may be that you'll need to open a bug report: [http://kmandla.wordpress.com/2007/12/20/howto-file-a-bug-report-on-launchpad/](http://kmandla.wordpress.com/2007/12/20/howto-file-a-bug-report-on-launchpad/)

---

### Post by tpgames on 2009-07-01
I guess I needed to know if it was a buggy problem. :D  
Because of how my brain works, I don't always know when its a bug, or when its something I did. Thanks for your opinions. Now, I know that I should ask this question. :D
Someone might have solved the problem ( I just need to try it now), and if not, I'm upgrading to Jaunty when the CD arrives because a fresh install might solve any hidden configuration issues I am having because I might have errored somewheres.
Thanks!

---

### Post by nineowls on 2009-07-02
I have had sound issues since after 8.04
try 
       sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
       sudo apt-get install linux-sound-base alsa-base alsa-utils
       sudo apt-get install gdm ubuntu-desktop
then
       sudo apt-get install gnome-alsamixer
       gnome-alsamixer
look at all the settings
play with the settings
maybe you'll find something that will work for you? (I did)

---

### Post by cleatus99 on 2009-07-02
ok I'm having same problem, I ran Updates, and boom sound gone, 

00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)

is what I have but alsamixer only shows Card: Conexant CX8801 

so the new Kernel update for 8.10 whacked it?

Linux mythtv 2.6.27-14-generic #1 SMP Tue Jun 30 19:54:46 UTC 2009 x86_64 GNU/Linux

---

### Post by tpgames on 2009-07-02
I did* upgrade* to 9.04. I still get the same gnome-alsa bad key errors. So, what I'm goiing to do  is wait until the CD comes in the mail, and do a fresh install. I was told that there is a bug with the gnome-alsa mixer and 8.04 hardy. 

I was told that I might have found a bug - besides the gnome-alsa  mixer error. Due to how my brain is wired, I never know when I've found these things. 
However, I'm also dealing with another possibility - the person I got computer from might have done damage to it in how he deleted files randomly. Or something was massively configured wrong. We should know after a completely fresh install (after wiping the system).

---

### Post by tpgames on 2009-07-02
> **dmizer said:**
> Actually, it's been my experience that most people at least get replies with useful information and potential answers. Your problem seems to be extremely unusual. Frankly I don't see how moving it to the beginners area will get you any more replies than you are now.

It may be that you'll need to open a bug report: [http://kmandla.wordpress.com/2007/12/20/howto-file-a-bug-report-on-launchpad/](http://kmandla.wordpress.com/2007/12/20/howto-file-a-bug-report-on-launchpad/)

I did do a test that sent data to launchpad (8.04 data) - about all of my drivers and everything. I was hoping that if it was former owner damage, I'd find out. My sister will help me send the bug report tomorrow, as I still have all the data.

---

