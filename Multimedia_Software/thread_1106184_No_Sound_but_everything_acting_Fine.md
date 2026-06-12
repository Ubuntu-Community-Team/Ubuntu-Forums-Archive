---
title: "No Sound but everything acting Fine?"
date: 2009-03-25
forum: Multimedia Software
---

### Post by cjdaweasel on 2009-03-25
My sound has been working fine for months now, then all of the sudden, today, it just stopped. I installed a couple of updates yesterday, but I think they were CUPS stuff and not related to sound.

Visualizations and equalizers in programs act like they're playing sound, but nothing is coming through.

In any case, here's what I know:

1. The speakers are not faulty, plugged a set of good headphones into the jack and still nothing.

2. The sound works fine in Windows, can play music, record sound and such.

3. I have gone through the guide stickied here in the forums, but to no avail. According to the guide everything is fine.
     a. I am part of the audio group along with root
```

audio:x:1001:cjdaweasel,root

```

     b. The hardware is detected (aplay -l)
```

card 0: CMI8738 [C-Media CMI8738], device 0: CMI8738-MC6 [C-Media PCI DAC/ADC]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 1: CMI8738-MC6 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 2: CMI8738-MC6 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

     c. Alsamixer is loading the correct sound card (shows it on the mixer page as C-Media CMI8738 )

     d. Nothing is muted in alsamixer, everything has been turned up to 100 and still nothing.

     e. In my Sound system preferences, the sound options are listed as Autodect. I have tried all the other options (there are quite a few of them) and all give no sound when hitting the test. However, one option (OSS) does give the following error:
```

sudiotestsrc wave=sine freq=512 ! audioconvert !
audioresample ! gconfaudiosink: Could not open audio
device for playback. Device is being used by another application.

```

     f. Attempted to remove and reinstall/purge:
         libesd-alsa0
         alsa-utils
         alsa-base
         libasound2
         linux-sound-base
       However, this did not affect the issue.

     g. Tried sudo alsa reload and got the following output:
```

lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/cjdaweasel/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 5754(pulseaudio) 5971(mixer_applet2). 
Unloading ALSA sound driver modules: snd-usb-audio snd-usb-lib snd-cmipci snd-pcm-oss snd-mixer-oss snd-pcm snd-page-alloc snd-opl3-lib snd-hwdep snd-mpu401-uart snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device (failed: modules still loaded: snd-usb-audio snd-usb-lib snd-cmipci snd-pcm snd-page-alloc snd-opl3-lib snd-hwdep snd-mpu401-uart snd-rawmidi snd-timer snd-seq-device).
Loading ALSA sound driver modules: snd-usb-audio snd-usb-lib snd-cmipci snd-pcm-oss snd-mixer-oss snd-pcm snd-page-alloc snd-opl3-lib snd-hwdep snd-mpu401-uart snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device.

```

     h. Switching Kernels on boot does not seem to fix the problem. I still have no sound.

     i. When checking the PulseAudio Device Changer, under Volume Control>Playback I see the software I have running that *should* be playing sound.

     j. When running pkill pulseaudio; sleep 2; pulseaudio -vv I get the following output:
```

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
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=1 source_name=alsa_input.usb_device_93a_2621_noserial_if1_sound_card_0_alsa_capture_0'
D: alsa-util.c: Trying front:1...
I: alsa-util.c: PCM device front:1 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround40:1...
I: alsa-util.c: PCM device surround40:1 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround41:1...
I: alsa-util.c: PCM device surround41:1 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround50:1...
I: alsa-util.c: PCM device surround50:1 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround51:1...
I: alsa-util.c: PCM device surround51:1 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround71:1...
I: alsa-util.c: PCM device surround71:1 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying hw:1 as last resort...
W: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 48000 Hz.
W: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
I: module-alsa-source.c: Successfully opened device hw:1.
I: module-alsa-source.c: Successfully enabled mmap() mode.
I: alsa-util.c: Successfully attached to mixer 'hw:1'
I: alsa-util.c: Cannot find mixer control "Capture".
I: alsa-util.c: Using mixer control "Mic".
I: source.c: Created source 0 "alsa_input.usb_device_93a_2621_noserial_if1_sound_card_0_alsa_capture_0" with sample spec "s16le 1ch 48000Hz"
I: module-alsa-source.c: Using 8 fragments of size 880 bytes.
I: alsa-util.c: All 1 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
I: module.c: Loaded "module-alsa-source" (index: #0; argument: "device_id=1 source_name=alsa_input.usb_device_93a_2621_noserial_if1_sound_card_0_alsa_capture_0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/usb_device_93a_2621_noserial_if1_sound_card_0_alsa_control__1
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_13f6_111_sound_card_0_alsa_playback_2
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_13f6_111_sound_card_0_alsa_capture_2
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_13f6_111_sound_card_0_alsa_playback_1
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0'
D: alsa-util.c: Trying front:0...
I: module-alsa-sink.c: Successfully opened device front:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: sink.c: Created sink 0 "alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0" with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 1 "alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0.monitor" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-sink.c: Using 8 fragments of size 1760 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #1; argument: "device_id=0 sink_name=alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 source_name=alsa_input.pci_13f6_111_sound_card_0_alsa_capture_0'
D: alsa-util.c: Trying front:0...
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Cannot find mixer control "Capture".
I: alsa-util.c: Using mixer control "Mic".
I: source.c: Created source 2 "alsa_input.pci_13f6_111_sound_card_0_alsa_capture_0" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-source.c: Using 8 fragments of size 1760 bytes.
I: alsa-util.c: ALSA device lacks separate volumes control for channel 'front-right', falling back to software volume control.
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+27
I: module.c: Loaded "module-alsa-source" (index: #2; argument: "device_id=0 source_name=alsa_input.pci_13f6_111_sound_card_0_alsa_capture_0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_13f6_111_sound_card_0_alsa_midi_0
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_13f6_111_sound_card_0_alsa_hw_specific_0
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_13f6_111_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 3 modules.
I: module.c: Loaded "module-hal-detect" (index: #3; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #4; argument: "").
I: protocol-native.c: loading cookie from disk.
I: module.c: Loaded "module-native-protocol-unix" (index: #5; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #6; argument: "").
I: module.c: Loaded "module-volume-restore" (index: #7; argument: "").
D: module-default-device-restore.c: Restored default sink 'alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0'.
D: core-subscribe.c: dropped redundant event.
D: module-default-device-restore.c: Restored default source 'alsa_input.usb_device_93a_2621_noserial_if1_sound_card_0_alsa_capture_0'.
I: module.c: Loaded "module-default-device-restore" (index: #8; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #9; argument: "").
D: module-suspend-on-idle.c: Sink alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0 becomes idle.
D: module-suspend-on-idle.c: Source alsa_input.usb_device_93a_2621_noserial_if1_sound_card_0_alsa_capture_0 becomes idle.
D: module-suspend-on-idle.c: Source alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0.monitor becomes idle.
D: module-suspend-on-idle.c: Source alsa_input.pci_13f6_111_sound_card_0_alsa_capture_0 becomes idle.
I: module.c: Loaded "module-suspend-on-idle" (index: #10; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-x11-publish.so': success
D: module-x11-publish.c: using already loaded auth cookie.
I: module.c: Loaded "module-x11-publish" (index: #11; argument: "").
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module-suspend-on-idle.c: Source alsa_input.pci_13f6_111_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Source alsa_input.usb_device_93a_2621_noserial_if1_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Sink alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...

```



Any idea why it is acting like everything is fine, but still no sound?

---

### Post by Sylslay on 2009-03-25
Meaby:Try use kernel before update. Meaby alsa-headrs are not upgrate with latest kernel?
2.6.24-23-generic -sound working ok.
2.6.24-24-generic - no sound at some apps, after latest update.

---

### Post by jhchadwell on 2009-03-25
I am also having a similiar problem.  Sound works at login (i get the login sound).  Once my desktop has loaded and i try to open any app that plays sound ( like totem or rythembox) the app freezes and I have to force quit.  It doesn't happen until I try to play a file. When I try to test my sound devices using system>preferences>sound I get this error and the app freezes:

 audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument

It was all fine working when i installed ubuntu 8.10 originally.

---

### Post by cjdaweasel on 2009-03-25
> **Sylslay said:**
> Meaby:Try use kernel before update. Meaby alsa-headrs are not upgrate with latest kernel?
2.6.24-23-generic -sound working ok.
2.6.24-24-generic - no sound at some apps, after latest update.

I tried to boot from another kernel version, but still no sound.

---

### Post by jhchadwell on 2009-03-25
sorry i am a dope.  I should have checked the previous posts better.  The solution turned out to be to get my drivers from a fresh kernel.  
try reading this post:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

in it is this:


Getting the ALSA drivers from a *fresh* kernel

Sometimes, sound might be configured correctly, but for some reason or another (tinkering) it stops working. One way to go back to the old setup is to reinstall Ubuntu. However, this step is actually quite unnecessary since you are reinstalling everything because of one thing.

A faster way, is to just remove the problematic packages and reinstall them cleanly.

(1) Remove these packages
Code:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils


(2) Reinstall those same packages
Code:

sudo apt-get install linux-sound-base alsa-base alsa-utils

[list][*]
VERY IMPORTANT NOTE: Ubuntu (GNOME) users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following
Code:

sudo apt-get install gdm ubuntu-desktop


(3) Reboot
[*][left]
VERY IMPORTANT NOTE: Xubuntu (XFCE) users have reported that packages 'gdm' and 'xubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following
Code:

sudo apt-get install gdm xubuntu-desktop


(3) Reboot
Now you may ask "I already had the packages, so why did I go through the trouble of removing them, then installing them". The answer lies in the --purge option which removes all the extra information that accumulated from tinkering and upgrading. After doing a purge then install, the packages are unpackaged as if it they are brand new.
(4) At this point, try using
Code:

 aplay -l

you should get your soundcard listed.

Thanks LordRaiden for writing that.

---

### Post by cjdaweasel on 2009-03-26
> **jhchadwell said:**
> sorry i am a dope.  I should have checked the previous posts better.  The solution turned out to be to get my drivers from a fresh kernel.  
try reading this post:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

in it is this:


...


I removed and reinstalled everything listed, but aside from setting my login screen back to the default nothing has changed.

This is kind of aggravating because I haven't DONE anything. No new programs, no new system software, it just STOPPED.

---

### Post by jhchadwell on 2009-03-26
just realized that maybe you are using pulseaudio and not alsa. Check your copy of your error codes in your previous posts from when you tried to restart alsa:


 lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/cjdaweasel/.gvfs
      Output information may be incomplete.
/sbin/alsa:**_ Warning:[B] Processes using sound devices: 5754(pulseaudio) 5971(mixer_applet2).** [/B]_
Unloading ALSA sound driver modules: snd-usb-audio snd-usb-lib snd-cmipci snd-pcm-oss snd-mixer-oss snd-pcm snd-page-alloc snd-opl3-lib snd-hwdep snd-mpu401-uart snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device (failed: modules still loaded: snd-usb-audio snd-usb-lib snd-cmipci snd-pcm snd-page-alloc snd-opl3-lib snd-hwdep snd-mpu401-uart snd-rawmidi snd-timer snd-seq-device).
Loading ALSA sound driver modules: snd-usb-audio snd-usb-lib snd-cmipci snd-pcm-oss snd-mixer-oss snd-pcm snd-page-alloc snd-opl3-lib snd-hwdep snd-mpu401-uart snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device.

So maybe you have to ditch pulse first and then start with alsa.  Maybe this works?  Let me know either way. 

 Apparently pulse has a bug. check this thread out:

[http://ubuntuforums.org/showthread.php?t=800242](http://ubuntuforums.org/showthread.php?t=800242)

---

### Post by cjdaweasel on 2009-03-26
> **jhchadwell said:**
> just realized that maybe you are using pulseaudio and not alsa. Check your copy of your error codes in your previous posts from when you tried to restart alsa:


 lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/cjdaweasel/.gvfs
      Output information may be incomplete.
/sbin/alsa:**_ Warning:[B] Processes using sound devices: 5754(pulseaudio) 5971(mixer_applet2).** [/B]_
Unloading ALSA sound driver modules: snd-usb-audio snd-usb-lib snd-cmipci snd-pcm-oss snd-mixer-oss snd-pcm snd-page-alloc snd-opl3-lib snd-hwdep snd-mpu401-uart snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device (failed: modules still loaded: snd-usb-audio snd-usb-lib snd-cmipci snd-pcm snd-page-alloc snd-opl3-lib snd-hwdep snd-mpu401-uart snd-rawmidi snd-timer snd-seq-device).
Loading ALSA sound driver modules: snd-usb-audio snd-usb-lib snd-cmipci snd-pcm-oss snd-mixer-oss snd-pcm snd-page-alloc snd-opl3-lib snd-hwdep snd-mpu401-uart snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device.

So maybe you have to ditch pulse first and then start with alsa.  Maybe this works?  Let me know either way. 

 Apparently pulse has a bug. check this thread out:

[http://ubuntuforums.org/showthread.php?t=800242](http://ubuntuforums.org/showthread.php?t=800242)

I tried everything that was in that thread as well as what was listed in a couple of links in posts. Still no sound.

Pulse Audio sees my device, and shows an application in volume control when I try load, say VLC, and play sound on it. But there is still no sound.

I ran the pkill pulseaudio; sleep 2; pulseaudio -vv command listed the pulse audio guide, and posted the output in part (j) of my first post on this thread. Still nada.

---

