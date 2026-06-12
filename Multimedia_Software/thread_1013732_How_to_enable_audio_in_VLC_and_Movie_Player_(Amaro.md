---
title: "How to enable audio in VLC and Movie Player (Amarok/Youtube has)"
date: 2008-12-17
forum: Multimedia Software
---

### Post by AlexOslo on 2008-12-17
I am running Ubuntu 8.04 and audio is not working in VLC and Movie Player, but works in Amarok.
At one point I remember a dialogue box came up and alerted me of something about the sound not working in VLC because of another application running (if I'm not mistaken - was it Amarok?). I mistakenly hit "yes" to the disable sound option, so now I need to enable it again.

Anyone got a clue on this?

Alex

PS. This was previously posted to another thread without the issue being resolved: 
[http://ubuntuforums.org/showthread.php?t=996164](http://ubuntuforums.org/showthread.php?t=996164)

---

### Post by jay li on 2008-12-17
Try to write "vlc preference" in terminal, to get vlc preference window and press reset all or just the option you made a mistake. 
But I have to warn you first, if you choose "reset all" all your vlc preference will be restored to default.

---

### Post by AlexOslo on 2008-12-17
> **jay li said:**
> Try to write "vlc preference" in terminal, to get vlc preference window and press reset all or just the option you made a mistake. 
But I have to warn you first, if you choose "reset all" all your vlc preference will be restored to default.
I tried, but got an error message
> "Unable to open 'preference'"
The terminal output was:
> VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Encrypted DVD support unavailable.
libdvdread: Can't stat preference
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000292] main input error: no suitable access module for `preference'
[00000283] main playlist: nothing to play
[00000283] main playlist: stopping playback

---

### Post by jay li on 2008-12-18
Then try this one "vlc --reset-config"

---

### Post by AlexOslo on 2008-12-18
> **jay li said:**
> Then try this one "vlc --reset-config"

Hmm...didn't work either (but there was no error message this time).

---

### Post by jay li on 2008-12-18
Tell me what did you write exactly

---

### Post by timcredible on 2008-12-18
in 8.04, not everything uses the same sound server. if i recall, firefox uses pulse, and amarok uses alsa.  only 1 sound server can access the speakers at a time.  so, what you want to do is set everything to use the pulse sound server, that way all your applications (firefox, amarok, cd player, etc.) can all work together.  to test this, try killing amarok (make sure to 'quit', just clicking on the X doesn't kill amarok, it stays in the panel) and see if you can then start firefox and get sound.  if so, this is your problem and you'll want to change the settings in amarok to use the pulse sound server.

---

### Post by gandaran on 2008-12-18
maybe you need to fix pulseaudio [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by AlexOslo on 2008-12-18
> **jay li said:**
> Tell me what did you write exactly
Here is a copy of what I wrote and the terminal output:
(after the $ sign)> vlc --reset-config
VLC media player 0.8.6e Janus

---

### Post by AlexOslo on 2008-12-18
> **gandaran said:**
> maybe you need to fix pulseaudio [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

After following the instructions (and a lengthy update), I restarted, but there was no difference. VLC has no audio. Amarok, however, does (as before), but YouTube, which had, is now without audio.

The webpage states:
> Providing you've followed this guide, you can gain access to all the utilities by launching "Applications/Sound & Video/PulseAudio Device Chooser". The applet's icon will appear in your notificiation tray - left-click to see the options.
but no such applet icon appeared there.

Under Preferences/Sound/Devices I tested all three Sound playbacks successfully (they gave a continuous beep), but the Sound capture test did not emit any sound (I set it to PulseAudio Sound Server, but also tested it with ALSA and OSS with the same result).

On the site I am asked to provide the following information in case I > require assistance...(which I do):

   1. Hardy Heron i386 (on a Dell GX270 2.6Ghz P4, 512MB memory)

   2. > **** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

   3. The verbose output from pulseaudio on your system:
      
       > $ pkill pulseaudio; sleep 2; pulseaudio -vv
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
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-hal-detect.so': success
I: module-hal-detect.c: Trying capability alsa
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_24d5_sound_card_0_alsa_playback_4
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_24d5_sound_card_0_alsa_capture_3
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_24d5_sound_card_0_alsa_capture_2
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_24d5_sound_card_0_alsa_capture_1
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_8086_24d5_sound_card_0_alsa_playback_0'
D: alsa-util.c: Trying front:0...
I: module-alsa-sink.c: Successfully opened device front:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: sink.c: Created sink 0 "alsa_output.pci_8086_24d5_sound_card_0_alsa_playback_0" with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 0 "alsa_output.pci_8086_24d5_sound_card_0_alsa_playback_0.monitor" with sample spec "s16le 2ch 44100Hz"

I: module-alsa-sink.c: Using 8 fragments of size 880 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #0; argument: "device_id=0 sink_name=alsa_output.pci_8086_24d5_sound_card_0_alsa_playback_0").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 source_name=alsa_input.pci_8086_24d5_sound_card_0_alsa_capture_0'
D: alsa-util.c: Trying front:0...
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: source.c: Created source 1 "alsa_input.pci_8086_24d5_sound_card_0_alsa_capture_0" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-source.c: Using 8 fragments of size 880 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
I: module.c: Loaded "module-alsa-source" (index: #1; argument: "device_id=0 source_name=alsa_input.pci_8086_24d5_sound_card_0_alsa_capture_0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_24d5_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 2 modules.
I: module.c: Loaded "module-hal-detect" (index: #2; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #3; argument: "").
I: protocol-native.c: loading cookie from disk.
I: module.c: Loaded "module-native-protocol-unix" (index: #4; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #5; argument: "").
I: module.c: Loaded "module-volume-restore" (index: #6; argument: "").
D: module-default-device-restore.c: Restored default sink 'alsa_output.pci_8086_24d5_sound_card_0_alsa_playback_0'.
D: core-subscribe.c: dropped redundant event.
D: module-default-device-restore.c: Restored default source 'alsa_input.pci_8086_24d5_sound_card_0_alsa_capture_0'.
I: module.c: Loaded "module-default-device-restore" (index: #7; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #8; argument: "").
D: module-suspend-on-idle.c: Sink alsa_output.pci_8086_24d5_sound_card_0_alsa_playback_0 becomes idle.
D: module-suspend-on-idle.c: Source alsa_output.pci_8086_24d5_sound_card_0_alsa_playback_0.monitor becomes idle.
D: module-suspend-on-idle.c: Source alsa_input.pci_8086_24d5_sound_card_0_alsa_capture_0 becomes idle.
I: module.c: Loaded "module-suspend-on-idle" (index: #9; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-x11-publish.so': success
D: module-x11-publish.c: using already loaded auth cookie.
I: module.c: Loaded "module-x11-publish" (index: #10; argument: "").
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module-suspend-on-idle.c: Source alsa_input.pci_8086_24d5_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.pci_8086_24d5_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Sink alsa_output.pci_8086_24d5_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
I: main.c: Got signal SIGINT.
I: main.c: Exiting.
I: main.c: Daemon shutdown initiated.
I: module.c: Unloading "module-alsa-sink" (index: #0).
D: module-rescue-streams.c: No sink inputs to move away.
D: module-rescue-streams.c: No source outputs to move away.
D: module-alsa-sink.c: Thread shutting down
I: sink.c: Freeing sink 0 "alsa_output.pci_8086_24d5_sound_card_0_alsa_playback_0"
I: source.c: Freeing source 0 "alsa_output.pci_8086_24d5_sound_card_0_alsa_playback_0.monitor"
I: module.c: Unloaded "module-alsa-sink" (index: #0).
I: module.c: Unloading "module-alsa-source" (index: #1).
D: module-rescue-streams.c: No source outputs to move away.
D: module-alsa-source.c: Thread shutting down
I: source.c: Freeing source 1 "alsa_input.pci_8086_24d5_sound_card_0_alsa_capture_0"
I: module.c: Unloaded "module-alsa-source" (index: #1).
I: module.c: Unloading "module-hal-detect" (index: #2).
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus.Local, path=/org/freedesktop/DBus/Local, member=Disconnected
I: module.c: Unloaded "module-hal-detect" (index: #2).
I: module.c: Unloading "module-esound-protocol-unix" (index: #3).
I: module.c: Unloaded "module-esound-protocol-unix" (index: #3).
I: module.c: Unloading "module-native-protocol-unix" (index: #4).
I: module.c: Unloaded "module-native-protocol-unix" (index: #4).
I: module.c: Unloading "module-gconf" (index: #5).
I: module.c: Unloaded "module-gconf" (index: #5).
I: module.c: Unloading "module-volume-restore" (index: #6).
I: module.c: Unloaded "module-volume-restore" (index: #6).
I: module.c: Unloading "module-default-device-restore" (index: #7).
I: module.c: Unloaded "module-default-device-restore" (index: #7).
I: module.c: Unloading "module-rescue-streams" (index: #8).
I: module.c: Unloaded "module-rescue-streams" (index: #8).
I: module.c: Unloading "module-suspend-on-idle" (index: #9).
I: module.c: Unloaded "module-suspend-on-idle" (index: #9).
I: module.c: Unloading "module-x11-publish" (index: #10).
I: module.c: Unloaded "module-x11-publish" (index: #10).
I: main.c: Daemon terminated.


   4. Problem is with VLC and Movie Player.

---

### Post by AlexOslo on 2008-12-18
> **gandaran said:**
> maybe you need to fix pulseaudio [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

This is just to notify that I have now given the results in the previous posting which I edited.

---

### Post by jay li on 2008-12-19
Hi AlexOslo,

Basically you need to bring vlc back to it's default preferences. 
When I had vlc 0.8.6 version - the command was "vlc preferences" but now (vlc 0.9.4 version) it has changed to "vlc --reset-config". 
So i suggest you to run "vlc --help" command and see by yourself what is the correct command (among the others) to do that and avoid mys-typo etc. 

If that won't help try reinstall vlc by using the following commands: 

1. sudo apt-get remove --purge vlc
2. sudo apt-get autoremove
3. sudo apt-get update
4. sudo apt-get install vlc

---

### Post by AlexOslo on 2008-12-19
> **jay li said:**
> Hi AlexOslo,

Basically you need to bring vlc back to it's default preferences. 
When I had vlc 0.8.6 version - the command was "vlc preferences" but now (vlc 0.9.4 version) it has changed to "vlc --reset-config". 
So i suggest you to run "vlc --help" command and see by yourself what is the correct command (among the others) to do that and avoid mys-typo etc. 

If that won't help try reinstall vlc by using the following commands: 

1. sudo apt-get remove --purge vlc
2. sudo apt-get autoremove
3. sudo apt-get update
4. sudo apt-get install vlc
I tried reinstalling, but no difference.

---

### Post by gandaran on 2008-12-19
> **AlexOslo said:**
> I tried reinstalling, but no difference.
reinstalling doesn't make any deference, your vlc configuration files still remain the the same in your home user vlc profile, they don't remove when you unistall vlc, what you have to do is find every vlc folder or file in your hidden home user folder and delete all of them, then just restart vlc again, a new default profile will be created.

---

### Post by AlexOslo on 2008-12-19
> **gandaran said:**
> reinstalling doesn't make any deference, your vlc configuration files still remain the the same in your home user vlc profile, they don't remove when you unistall vlc, what you have to do is find every vlc folder or file in your hidden home user folder and delete all of them, then just restart vlc again, a new default profile will be created.

I deleted all the files that came up in the "file system" folder upon searching "vlc" (had to press Alt F2 -> gksudo nautilus -> Enter, to gain permission to delete the files). Then I went to Synaptic, searched "vlc", and reinstalled all the files that came up. But there was no difference when I started up VLC again (no audio).

---

### Post by jay li on 2008-12-19
Hi AlexOslo,
gandaran told you to delete the ".vlc" folder which is located under your home folder but it's hidden (Ctrl+H), and not in the "file system" folder. 
But let me ask you something, have you tried totem, firefox etc?
Did you try the sound system test checking (goto System > Preferences > Sound)?

---

### Post by AlexOslo on 2008-12-20
> **jay li said:**
> Hi AlexOslo,
gandaran told you to delete the ".vlc" folder which is located under your home folder but it's hidden (Ctrl+H), and not in the "file system" folder. 

What I'm doing to get, as you say,
[/QUOTE]under your home folder but it's hidden[/QUOTE]
is to go to the home folder, and go up two levels (using the "up" arrow), then search for "vlc" which generates a number of files/folders. I would be thankful to know how to get to the ".vlc" folder otherwise!

> have you tried totem, firefox etc?
No sound in totem either (as thread title indicates). I use firefox (not sure what you mean exactly) version 3.0.5.

> Did you try the sound system test checking (goto System > Preferences > Sound)?

Yes. (As mentioned)
> Under Preferences/Sound/Devices I tested all three Sound playbacks successfully (they gave a continuous beep), but the Sound capture test did not emit any sound (I set it to PulseAudio Sound Server, but also tested it with ALSA and OSS with the same result).

---

### Post by AlexOslo on 2008-12-20
> > **gandaran said:**
> maybe you need to fix pulseaudio [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

After following the instructions (and a lengthy update), I restarted, but there was no difference. VLC has no audio. Amarok, however, does (as before), but YouTube, which had, is now without audio.

Please note that I lost sound in YouTube also after the above!

---

### Post by jay li on 2008-12-20
When you open your Home directory, go to "view" menu and select "Show hidden files" (the Ctrl+H is just a shortcut). Now, scroll down and you'll see the ".vlc"
 - delete it. 

Try in the Sound system configuration, to set everything to "Autodetect" except "Sound capture". 

Also try to check the volume control applet preferences and choose "Playback: ALSA PCM... via DMA (Pulse Audio...)".

---

### Post by AlexOslo on 2008-12-20
> **jay li said:**
> When you open your Home directory, go to "view" menu and select "Show hidden files" (the Ctrl+H is just a shortcut). Now, scroll down and you'll see the ".vlc"
 - delete it. 

Try in the Sound system configuration, to set everything to "Autodetect" except "Sound capture". 

Also try to check the volume control applet preferences and choose "Playback: ALSA PCM... via DMA (Pulse Audio...)".

Ok, I found and deleted it, then configured the Sound system as you mentioned. However VLC is still without audio.

---

### Post by jay li on 2008-12-20
Now go to reinstall vlc, but before you do that check again if the ".vlc" hidden folder was not created again. 
If it does delete it again then reinstall.

---

### Post by AlexOslo on 2008-12-20
> **jay li said:**
> Now go to reinstall vlc, but before you do that check again if the ".vlc" hidden folder was not created again. 
If it does delete it again then reinstall.

I re-deleted the .vlc hidden folder and in Synaptic reinstalled all the green buttons that came up upon searching for "vlc". Then started VLC again but there is no change.

---

### Post by jay li on 2008-12-20
Please run this code in terminal: "aplay -l" (without the quotes) and post the output here.

---

### Post by AlexOslo on 2008-12-20
> **jay li said:**
> Please run this code in terminal: "aplay -l" (without the quotes) and post the output here.

**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by jay li on 2008-12-20
Right click on the volume control applet.

Select "Open Volume Control"

In File menu select the "Change Device", and change it to Intel ICH5. 
Check also if something there is muted. 
Then check your sound.

---

### Post by AlexOslo on 2008-12-21
> **jay li said:**
> Right click on the volume control applet.

Select "Open Volume Control"

In File menu select the "Change Device", and change it to Intel ICH5. 
Check also if something there is muted. 
Then check your sound.

It was already set to Intel ICH5. Only muted ones under Playback were line-in and microphone.

---

### Post by jocheem67 on 2008-12-21
I notice with my installed vlc that pulse-audio isn't listed there ( vlc -preferences - audio )..it uses the "system default".
Well I use alsa, as marked in ubuntu's sound preferences, maybe you could try that?

Furthermore, I always use the asoundconf command in the terminal:

[HTML]asoundconf list[/HTML]

and 

[HTML]asoundconf set-default-card 'name of the preffered card/chip'[/HTML]

But beware, this kind of disables pulse as sound-server ( which is exactly my intention ). It's just too buggy....


Another option is to install the "vlc-plugin-pulse" from synaptic.

---

### Post by jay li on 2008-12-21
Hi AlexOslo,

Not sure, but maybe there is a conflict between Amarok & vlc, so my suggestion is temporary unistall Amarok to check if the problem coming from there.

---

