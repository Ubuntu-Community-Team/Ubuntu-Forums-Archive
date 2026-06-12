---
title: "no sound in Flash in Firefox (Intrepid)"
date: 2008-12-10
forum: Multimedia Software
---

### Post by sickgirl485 on 2008-12-10
I have been trying for a long time to get sound to work in flash videos online because I am missing out on a huge chunk of culture by being deprived of YouTube. I am using OSS sound system, ALSA and everything else does not work for me, I've tried it. I have already done this:

```
sudo gedit /etc/firefox/firefoxrc
```

In the resulting file, I changed the entry from:

```

FIREFOX_DSP=""

```

and changed it to:

```
FIREFOX_DSP="aoss"
```

as countless "how to's" have told me to. I am also using flashplugin-nonfree version 10.0.12.36 which is the most recent version, and have tried adobe-flashplugin (same version) and gnash. I also have ubuntu-restricted-extras, and of course the dependencies for the other packages I have listed here (including flashplugin-nonfree-extrasounds).

Judging from what I have done, I cannot think of anything else to do that could work. Is there any way of just getting the sound to work? It's really frustrating.

---

### Post by sickgirl485 on 2008-12-10
I have tried PulseAudio, but it works less than OSS. At least with OSS I can get Rhythmbox to play music properly. Also, mplayer works with OSS too. Just so I can say I tried it, Flash videos don't work with PulseAudio either. 

I set up Pulse Audio according to [this How To]("http://ubuntuforums.org/showthread.php?t=789578"), but it's kind of crappy, since at the bottom it tells you how to determine whether your Pulse Audio is working, but doesn't tell you how to fix it if it's not. Plus, if I can discern correctly, all the instructions do is update your sources, and make sure you don't have libflashsupport installed.

Here is my output for aplay -l:

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

If I go into the PulseAudio Device Chooser, after these instructions, I get a listing for Rhythmbox (which is the program I am concerned about right now, other than flash) but obviously there is no sound. So apparently, according to the How To:

> [COLOR="Blue"]The application does not play audio and does list an entry in the Playback tab;
- the application is using PulseAudio but there is a problem, such as: a bug in PulseAudio, a problem with your ALSA kernel module or libraries, or your PCM/Master volume is muted.[/COLOR]

This is the last instruction in the How To, and from what I can tell just kills pulseaudio. Here is the output anyway:

```
$ pkill pulseaudio; sleep 2; pulseaudio -vv
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
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_266e_sound_card_0_alsa_playback_4
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_266e_sound_card_0_alsa_capture_3
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_266e_sound_card_0_alsa_capture_2
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_266e_sound_card_0_alsa_capture_1
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=1 sink_name=alsa_output.pci_8086_266e_sound_card_0_alsa_playback_0'
D: alsa-util.c: Trying front:1...
I: module-alsa-sink.c: Successfully opened device front:1.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:1
I: alsa-util.c: Unable to attach to mixer front:1: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:1'
I: alsa-util.c: Using mixer control "Master".
I: sink.c: Created sink 0 "alsa_output.pci_8086_266e_sound_card_0_alsa_playback_0" with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 0 "alsa_output.pci_8086_266e_sound_card_0_alsa_playback_0.monitor" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-sink.c: Using 8 fragments of size 1760 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #0; argument: "device_id=1 sink_name=alsa_output.pci_8086_266e_sound_card_0_alsa_playback_0").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=1 source_name=alsa_input.pci_8086_266e_sound_card_0_alsa_capture_0'
D: alsa-util.c: Trying front:1...
I: module-alsa-source.c: Successfully opened device front:1.
I: module-alsa-source.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:1
I: alsa-util.c: Unable to attach to mixer front:1: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:1'
I: alsa-util.c: Using mixer control "Capture".
I: source.c: Created source 1 "alsa_input.pci_8086_266e_sound_card_0_alsa_capture_0" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-source.c: Using 8 fragments of size 1760 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
I: module.c: Loaded "module-alsa-source" (index: #1; argument: "device_id=1 source_name=alsa_input.pci_8086_266e_sound_card_0_alsa_capture_0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_266e_sound_card_0_alsa_control__1
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_7_sound_card_0_alsa_playback_3
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_7_sound_card_0_alsa_capture_3
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_7_sound_card_0_alsa_playback_2
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_7_sound_card_0_alsa_capture_2
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_7_sound_card_0_alsa_playback_1
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_7_sound_card_0_alsa_capture_1
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_1102_7_sound_card_0_alsa_playback_0'
D: alsa-util.c: Trying front:0...
W: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
I: module-alsa-sink.c: Successfully opened device front:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Cannot find mixer control "Master".
W: alsa-util.c: Cannot find fallback mixer control "PCM".
I: sink.c: Created sink 1 "alsa_output.pci_1102_7_sound_card_0_alsa_playback_0" with sample spec "s16le 2ch 48000Hz"
I: source.c: Created source 2 "alsa_output.pci_1102_7_sound_card_0_alsa_playback_0.monitor" with sample spec "s16le 2ch 48000Hz"
I: module-alsa-sink.c: Using 8 fragments of size 1792 bytes.
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+27
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #2; argument: "device_id=0 sink_name=alsa_output.pci_1102_7_sound_card_0_alsa_playback_0").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 source_name=alsa_input.pci_1102_7_sound_card_0_alsa_capture_0'
D: alsa-util.c: Trying front:0...
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Cannot find mixer control "Capture".
I: alsa-util.c: Using mixer control "Mic".
I: source.c: Created source 3 "alsa_input.pci_1102_7_sound_card_0_alsa_capture_0" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-source.c: Using 2 fragments of size 1792 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+26
I: module.c: Loaded "module-alsa-source" (index: #3; argument: "device_id=0 source_name=alsa_input.pci_1102_7_sound_card_0_alsa_capture_0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_7_sound_card_0_alsa_midi_0
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_7_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 4 modules.
I: module.c: Loaded "module-hal-detect" (index: #4; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #5; argument: "").
I: protocol-native.c: loading cookie from disk.
I: module.c: Loaded "module-native-protocol-unix" (index: #6; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #7; argument: "").
I: module.c: Loaded "module-volume-restore" (index: #8; argument: "").
D: module-default-device-restore.c: Restored default sink 'alsa_output.pci_8086_266e_sound_card_0_alsa_playback_0'.
D: core-subscribe.c: dropped redundant event.
D: module-default-device-restore.c: Restored default source 'alsa_input.pci_8086_266e_sound_card_0_alsa_capture_0'.
I: module.c: Loaded "module-default-device-restore" (index: #9; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #10; argument: "").
D: module-suspend-on-idle.c: Sink alsa_output.pci_8086_266e_sound_card_0_alsa_playback_0 becomes idle.
D: module-suspend-on-idle.c: Sink alsa_output.pci_1102_7_sound_card_0_alsa_playback_0 becomes idle.
D: module-suspend-on-idle.c: Source alsa_output.pci_8086_266e_sound_card_0_alsa_playback_0.monitor becomes idle.
D: module-suspend-on-idle.c: Source alsa_input.pci_8086_266e_sound_card_0_alsa_capture_0 becomes idle.
D: module-suspend-on-idle.c: Source alsa_output.pci_1102_7_sound_card_0_alsa_playback_0.monitor becomes idle.
D: module-suspend-on-idle.c: Source alsa_input.pci_1102_7_sound_card_0_alsa_capture_0 becomes idle.
I: module.c: Loaded "module-suspend-on-idle" (index: #11; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-x11-publish.so': success
D: module-x11-publish.c: using already loaded auth cookie.
I: module.c: Loaded "module-x11-publish" (index: #12; argument: "").
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module-suspend-on-idle.c: Source alsa_input.pci_1102_7_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.pci_1102_7_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Source alsa_input.pci_8086_266e_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.pci_8086_266e_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Sink alsa_output.pci_1102_7_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
I: module-suspend-on-idle.c: Sink alsa_output.pci_8086_266e_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
```

One thing that is strange though is when I enter $ alsamixer -Dhw into the terminal, I get the volume thing, but it says the first entry ( IEC958 ) is "off" and has a box and "MM" instead of a volume meter. I don't know if this is normal or if I am just reading it wrong.

---

### Post by gandaran on 2008-12-10
you should try adobe flash 10 or fix pulseaudio [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by sickgirl485 on 2008-12-10
> **gandaran said:**
> you should try adobe flash 10 or fix pulseaudio [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

As I said in my post, I have tried Adobe Flash 10 and the second half of my post details my going through that How To with no success.

---

### Post by psyke83 on 2008-12-10
> **sickgirl485 said:**
> I have been trying for a long time to get sound to work in flash videos online because I am missing out on a huge chunk of culture by being deprived of YouTube. I am using OSS sound system, ALSA and everything else does not work for me, I've tried it. I have already done this:

```
sudo gedit /etc/firefox/firefoxrc
```

In the resulting file, I changed the entry from:

```

FIREFOX_DSP=""

```

and changed it to:

```
FIREFOX_DSP="aoss"
```

as countless "how to's" have told me to. I am also using flashplugin-nonfree version 10.0.12.36 which is the most recent version, and have tried adobe-flashplugin (same version) and gnash. I also have ubuntu-restricted-extras, and of course the dependencies for the other packages I have listed here (including flashplugin-nonfree-extrasounds).

Judging from what I have done, I cannot think of anything else to do that could work. Is there any way of just getting the sound to work? It's really frustrating.

Unfortunately, using the aoss wrapper won't work with OSSv4 (it's intended to be used by ALSA to emulate OSS calls), and Flash v9/v10 no longer supports OSS output anyway. I recommend that you undo the changes to Firefox that you have documented in your post.

The way to get Flash working with OSSv4 is to install the "libflashsupport" library. This allows Flash to use OSS, ESD or PulseAudio output, but it causes instability ([bug #192888]("https://bugs.launchpad.net/bugs/192888")).

Try installing "libflashsupport" (or "flashplugin-nonfree-extrasound") first, and if it works, worry about stability later.

Note: you may need to acquire an alternative version of "libflashsupport" (as the version in our repositories are intended for use by PulseAudio). Please also see my next post re: OSSv4.

---

### Post by psyke83 on 2008-12-10
> **sickgirl485 said:**
> As I said in my post, I have tried Adobe Flash 10 and the second half of my post details my going through that How To with no success.

OSSv4 does not work with PulseAudio (and Flash, as you've discovered), so you won't have any luck with that guide.

I would question whether you really needed to install OSSv4. There's a bug in Intrepid where the PCM mixer gets muted by default - it's so simple to fix, but often overlooked.

Having said that, you may have more problems reverting back to ALSA due to "cruft" left over from OSSv4, so I'm unsure what advice to give you...

Perhaps you may want to try booting from the live cd to check if sound works (and be sure to check the PCM mixer - see Part C, Step 3 of my guide).

---

### Post by sickgirl485 on 2008-12-10
> **psyke83 said:**
> 
You do have an option, but it has a drawback - install the "libflashsupport" library. This allows Flash to use OSS, ESD or PulseAudio output, but it causes instability ([bug #192888]("https://bugs.launchpad.net/bugs/192888")).

Try installing "libflashsupport" (or "flashplugin-nonfree-extrasound") first, and if it works, worry about stability later.



I downloaded and installed flashplugin-nonfree-extrasound and still it doesn't work. libflashsupport isn't available anymore, so I couldn't try it.

Also, here is the output for $ alsamixer -Dhw :

[IMG]http://img408.imageshack.us/img408/1820/alsamixeraf7.png[/IMG]

---

### Post by psyke83 on 2008-12-10
> **sickgirl485 said:**
> I downloaded and installed flashplugin-nonfree-extrasound and still it doesn't work. libflashsupport isn't available anymore, so I couldn't try it.

Also, here is the output for $ alsamixer -Dhw :

[IMG]http://img408.imageshack.us/img408/1820/alsamixeraf7.png[/IMG]

Well, how to fix your problem depends on the extent to which you've changed your configuration.

1. When you said that you're using OSS, do you mean that you set the Playback options to "OSS" in System/Preferences/Sound?
- If that's the case, then you can follow my guide.
- If that's not the case (i.e. you followed instructions to install OSSv4), then my guide won't help.

The alsamixer output indicates that the default sound card is the digital output of your sound card - that may not be correct. If you follow my guide again, you'll see a step where you are required to choose the correct "sink" (sound device), so your problem may be fixed trivially.

If you didn't install OSSv4, you can try to follow the guide again, and pay attention to Part A, Step 5.

If you need further help, I need the information outlined in Appendix A of my guide. However, you could be suffering from an ALSA kernel bug that's unrelated to PulseAudio; it's hard to tell without the proper information at hand.

---

### Post by sickgirl485 on 2008-12-10
> **psyke83 said:**
> Well, how to fix your problem depends on the extent to which you've changed your configuration.

1. When you said that you're using OSS, do you mean that you set the Playback options to "OSS" in System/Preferences/Sound?
- If that's the case, then you can follow my guide.
- If that's not the case (i.e. you followed instructions to install OSSv4), then my guide won't help.

The alsamixer output indicates that the default sound card is the digital output of your sound card - that may not be correct. If you follow my guide again, you'll see a step where you are required to choose the correct "sink" (sound device), so your problem may be fixed trivially.

If you didn't install OSSv4, you can try to follow the guide again, and pay attention to Part A, Step 5.

If you need further help, I need the information outlined in Appendix A of my guide. However, you could be suffering from an ALSA kernel bug that's unrelated to PulseAudio; it's hard to tell without the proper information at hand.

When I say I use OSS I mean I went into Sounds and changed the sound type to OSS, and nothing more. 

I went through the guide again, and paid particular attention to step 5. I went and chose pretty much all of the devices listed on my computer in both PulseAudio and in the Sound menu as default sources, and none of them worked for PulseAudio. 

I am not sure what you mean by alsamixer saying that the output is the digital output for my sound, and I also don't know if this is good or bad. 

As for the info in Appendix A of your guide, I attached that already in my first reply to this post (where I added more information). If that's not quite right let me know.

---

### Post by psyke83 on 2008-12-10
> **sickgirl485 said:**
> When I say I use OSS I mean I went into Sounds and changed the sound type to OSS, and nothing more. 

I went through the guide again, and paid particular attention to step 5. I went and chose pretty much all of the devices listed on my computer in both PulseAudio and in the Sound menu as default sources, and none of them worked for PulseAudio. 

I am not sure what you mean by alsamixer saying that the output is the digital output for my sound, and I also don't know if this is good or bad. 

As for the info in Appendix A of your guide, I attached that already in my first reply to this post (where I added more information). If that's not quite right let me know.

Ah, I missed the second post, thanks.

You have two sound cards, correct? Which sound card are your speakers connected to? From your output it seems that PulseAudio is choosing card 0, device 0 (which is "card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]" from the aplay output). Perhaps you need to change it to card 1, device 0 (the ICH6 card)?

If you think this may be your problem, see this post to change the default card: [http://ubuntuforums.org/showpost.php?p=6345254&postcount=946](http://ubuntuforums.org/showpost.php?p=6345254&postcount=946)

In your case, X=1 and Y=0.

Once you've restarted PulseAudio (logging out and back in), try to play some sound again, and be sure to check the ALSA mixer for the ICH6 device.

If it doesn't work, perhaps it's a kernel bug... in that case, you should revert the changes in that post.

---

### Post by sail on 2008-12-11
I'm having the same problem. I use ALSA and am using a System 76 Gazelle laptop. Switching to OSS doesn't help.

---

### Post by sickgirl485 on 2008-12-14
> **psyke83 said:**
> Ah, I missed the second post, thanks.

You have two sound cards, correct? Which sound card are your speakers connected to? From your output it seems that PulseAudio is choosing card 0, device 0 (which is "card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]" from the aplay output). Perhaps you need to change it to card 1, device 0 (the ICH6 card)?

If you think this may be your problem, see this post to change the default card: [http://ubuntuforums.org/showpost.php?p=6345254&postcount=946](http://ubuntuforums.org/showpost.php?p=6345254&postcount=946)

In your case, X=1 and Y=0.

Once you've restarted PulseAudio (logging out and back in), try to play some sound again, and be sure to check the ALSA mixer for the ICH6 device.

If it doesn't work, perhaps it's a kernel bug... in that case, you should revert the changes in that post.

I went through that and still it's not working. How do you know that 1,0 is the right device? There is also card 0, device 4, which has sort of the same name (see my aplay -l output above). Just to be clear, here is a screenshot of my sound menu to make sure everything is right there. I have also tried putting all of the settings to PulseAudio as well. 

[IMG]http://img234.imageshack.us/img234/8499/screenshotsoundpreferenqd6.png[/IMG]

---

### Post by sickgirl485 on 2009-01-17
I really hope there is something to fix this somewhere out there...

---

### Post by sickgirl485 on 2009-01-17
I figured it out! I downgraded to Flash 7 and it works now! Yay! That took a really long time but I am very happy I finally got this working

---

