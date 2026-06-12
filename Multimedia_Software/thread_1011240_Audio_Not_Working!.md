---
title: "Audio Not Working!"
date: 2008-12-14
forum: Multimedia Software
---

### Post by Morticutor UK on 2008-12-14
OK, so I'm running on 8.10 and everything works fine except there's no sound.  

I've tried a whole bunch of stuff and this is what I have so far...

 > **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


I've checked on the supported driver listings, but I have a feeling they're not there.  

 However, the cards are most definitely recognised - running the -less command gets me: 

> 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
        Subsystem: Mitac Device 9008
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at fa200000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

And: 
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
        Subsystem: Mitac Device 9008
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at c7eec000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-int


I've also updated my sound modules.  

I've no idea what to do next and I need sound for podcasting.  Any ideas?

---

### Post by alex.rayu on 2008-12-14
Most probably, its just PulseAudio. Problems with PulseAudio have become very extensive. Such things could only happen to open source. Not even Microsoft could afford to have such extensive sound problems. 

KDE should not be having these. Try KDE.

---

### Post by markbuntu on 2008-12-14
Don't listen to him, try the first link. If it does not help there is a link to more troubleshooting help.

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

I have and ALC 888 and an ATI HDMI and my sound works just fine so do not despair.

---

### Post by Morticutor UK on 2008-12-14
OK, so I rebooted in Vista to watch a DVD and came back to try links...and all of the sounds - the startup worked and now I'm listening to Amarok.  

While that's a great thing, I wish I knew the why of it...   :confused:

Thanks anyway.  Now I just need to get the title changed to 'solved'.

EDIT: Aaaand now it's not working.  I've gone through the second link,  installed everything and played with the settings, but everything has the 'mute' icon and it won't click off!  

](*,)  I know it works - it did yesterday - I just can't figure out *why*...

---

### Post by Morticutor UK on 2008-12-17
Aarrgghh!

So I decided to go for a clean install, see if that fixed it, which it did.  The sound worked from the get-go, although it was a little quiet (easily fixed).  So, after sorting out the repositories and fixing my audio/video to what I wanted,  I switched over to my Vista install and played me some Mass Effect before going to bed.

Then I boot up Ubuntu this morning...and no sound.  

I get some channels (if I turn up the internal mike I can hear myself type, which is just weird), but no music or system sounds.  

This is really pissing me off.  I've gone through most of everything everything I can find on here, checking alsa in the terminal, checking the sound settings, and nothing works!  

And the irony of this?  I was planning to write up a piece on using Linux for the university magazine, but how can I when I can't even fix this problem?  Also I need the audio for podcasting...

---

### Post by Morticutor UK on 2008-12-17
OK, this is strange.  I messed around some more with the controls, before bugging out and playing ME again.  

I switch off, start up again and go into Ubuntu...and the sound is on...  

Can anyone make a guess as to what's going on?

---

### Post by Tomatz on 2008-12-17
In the systray (top rh) **r-click the volume applet** and click **open volume control**. 

Now click **file** and **change the device from alsa to OSS**.



If this works post back and we can try to fix alsa ;)

---

### Post by Morticutor UK on 2008-12-17
> **Tomatz said:**
> In the systray (top rh) **r-click the volume applet** and click **open volume control**. 

Now click **file** and **change the device from alsa to OSS**.



If this works post back and we can try to fix alsa ;)

Should I notice an immediate change in doing this?    Because, uh, I already tried that.  I went through all the options given.

EDIT: OK so I rebooted back into Linux to see what would happen and the sound is fine.  Could booting into Windows be messing it about?  I'm pretty sure that's a dumb question, but I can't name anything else that changes.

---

### Post by Tomatz on 2008-12-17
> **Morticutor UK said:**
> Should I notice an immediate change in doing this?    Because, uh, I already tried that.  I went through all the options given.

EDIT: OK so I rebooted back into Linux to see what would happen and the sound is fine.  Could booting into Windows be messing it about?  I'm pretty sure that's a dumb question, but I can't name anything else that changes.

I doubt its a problem caused by booting into windows and you shouldn't notice an immediate difference because as you say the problem is intermittent and happens after time.

You do know that audio will stop working (from one output) using alsa if you have more than one audio channel open. I.e 2 media players open at the same time.

If this is the problem i suggest you set up pulseaudio properly.

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

;)

---

### Post by Morticutor UK on 2008-12-17
> **Tomatz said:**
> I doubt its a problem caused by booting into windows and you shouldn't notice an immediate difference because as you say the problem is intermittent and happens after time.

You do know that audio will stop working (from one output) using alsa if you have more than one audio channel open. I.e 2 media players open at the same time.

If this is the problem i suggest you set up pulseaudio properly.

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

;)

Ooh, I haven't come across that workaround.  I'll keep it for if/when it stops working...hopefully it won't come to that...

---

### Post by Morticutor UK on 2008-12-17
Well, I booted up after going out and the sound had gone again.  So I tried the workaround...and it hasn't worked.  I had tried configuring pulseaudio from a different howto and didn't get anywhere then, either.

The verbose output from pulseaudio looks like this: 

```
mark@mark-laptop:~$ pkill pulseaudio; sleep 2; pulseaudio -vv
I: main.c: PolicyKit refuses acquire-high-priority privilige.
I: main.c: Called SUID root and real-time/high-priority scheduling was requested in the configuration. However, we lack the necessary priviliges:
I: main.c: We are not in group 'pulse-rt' and PolicyKit refuse to grant us priviliges. Dropping SUID again.
I: main.c: For enabling real-time scheduling please acquire the appropriate PolicyKit priviliges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
I: main.c: Note that real-time/high-priority scheduling is NOT normally required. If you experience crackling or other sound anomalies, consider one or more of the above solutions.
I: main.c: High-priority scheduling enabled in configuration but now allowed by policy. Disabling forcibly.
W: ltdl-bind-now.c: Failed to find original dlopen loader.
W: pid.c: Stale PID file, overwriting.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: main.c: This is PulseAudio 0.9.10
I: main.c: Page size is 4096 bytes
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-hal-detect.so': success
I: module-hal-detect.c: Trying capability alsa
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0_alsa_capture_2
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0_alsa_playback_1
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0'
D: alsa-util.c: Trying front:0...
I: module-alsa-sink.c: Successfully opened device front:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: sink.c: Created sink 0 "alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0" with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 0 "alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0.monitor" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-sink.c: Using 8 fragments of size 1792 bytes.
I: alsa-util.c: ALSA device lacks independant volume controls for each channel, falling back to software volume control.
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #0; argument: "device_id=0 sink_name=alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 source_name=alsa_input.pci_8086_293e_sound_card_0_alsa_capture_0'
D: alsa-util.c: Trying front:0...
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: source.c: Created source 1 "alsa_input.pci_8086_293e_sound_card_0_alsa_capture_0" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-source.c: Using 8 fragments of size 1792 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
I: module.c: Loaded "module-alsa-source" (index: #1; argument: "device_id=0 source_name=alsa_input.pci_8086_293e_sound_card_0_alsa_capture_0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0_alsa_control__1
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1002_aa28_sound_card_0_alsa_playback_3
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1002_aa28_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 2 modules.
I: module.c: Loaded "module-hal-detect" (index: #2; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #3; argument: "").
I: protocol-native.c: loading cookie from disk.
I: module.c: Loaded "module-native-protocol-unix" (index: #4; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
D: module-gconf.c: Loading module 'module-combine' with args '' due to GConf configuration.
I: sink.c: Created sink 1 "combined" with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 2 "combined.monitor" with sample spec "s16le 2ch 44100Hz"
D: memblockq.c: memblockq requested: maxlength=174080, tlength=174080, base=4, prebuf=1, minreq=0
D: memblockq.c: memblockq sanitized: maxlength=174080, tlength=174080, base=4, prebuf=4, minreq=4
I: resampler.c: Using resampler 'trivial'
I: resampler.c: Using s16le as working format.
I: sink-input.c: Created input 0 "Simultaneous output on ALSA PCM on front:0 (ALC888 Analog) via DMA" on alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0 with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-combine.c: Master sink is now 'alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0'
D: module-combine.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+27
I: module.c: Loaded "module-combine" (index: #5; argument: "").
I: module.c: Loaded "module-gconf" (index: #6; argument: "").
I: module.c: Loaded "module-volume-restore" (index: #7; argument: "").
I: module.c: Loaded "module-default-device-restore" (index: #8; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #9; argument: "").
D: module-suspend-on-idle.c: Sink combined becomes idle.
D: module-suspend-on-idle.c: Source alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0.monitor becomes idle.
D: module-suspend-on-idle.c: Source alsa_input.pci_8086_293e_sound_card_0_alsa_capture_0 becomes idle.
D: module-suspend-on-idle.c: Source combined.monitor becomes idle.
I: module.c: Loaded "module-suspend-on-idle" (index: #10; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-x11-publish.so': success
D: module-x11-publish.c: using already loaded auth cookie.
I: module.c: Loaded "module-x11-publish" (index: #11; argument: "").
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module-suspend-on-idle.c: Source combined.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Source alsa_input.pci_8086_293e_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Sink combined idle for too long, suspending ...
D: module-suspend-on-idle.c: Sink alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0 becomes idle.
D: module-suspend-on-idle.c: Sink alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0 becomes idle.
I: sink-input.c: Freeing output 0 "Simultaneous output on ALSA PCM on front:0 (ALC888 Analog) via DMA"
I: module-combine.c: No master selected, lacking suitable outputs.
I: module-combine.c: Device suspended...
I: module-suspend-on-idle.c: Sink alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
```

I suspect it's not good...

---

### Post by Tomatz on 2008-12-17
What output do you get from totem when running it in a terminal?

Just type **totem** into a terminal and press return.

---

### Post by markbuntu on 2008-12-17
You should try unchecking the simultaneous output box in pa configure local sound server. That seems to be at least part of the problem from the log.

---

### Post by Morticutor UK on 2008-12-17
> **Tomatz said:**
> What output do you get from totem when running it in a terminal?

Just type **totem** into a terminal and press return.

** (totem:6552): DEBUG: Init of Python module
** (totem:6552): DEBUG: Registering Python plugin instance: BBCViewer+TotemPythonPlugin
** (totem:6552): DEBUG: Creating object of type BBCViewer+TotemPythonPlugin
** (totem:6552): DEBUG: Creating Python plugin instance
** (totem:6552): DEBUG: Init of Python module
** (totem:6552): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem:6552): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem:6552): DEBUG: Creating Python plugin instance

---

### Post by Morticutor UK on 2008-12-17
> **markbuntu said:**
> You should try unchecking the simultaneous output box in pa configure local sound server. That seems to be at least part of the problem from the log.

Done, and no change.  I noticed that I pretty much always have Firefox ALSA running (mainly because FF is always on with me) and then I'll often run Amarok as well, although this isn't a new thing so I don't get why it's doing it off and on.

---

### Post by Tomatz on 2008-12-17
No errors there then.

Imo its a problem with alsa and as alsa is the backend for pulseaudio, pulseaudio wont work either :(

Try fully uninstalling and reinstalling alsa. Open a terminal and copy and paste the following:

```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```

If you still have no luck you will probably have to compile alsa from source. Or use the helpful script in the following post:

[http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695)

---

### Post by Morticutor UK on 2008-12-17
> **Tomatz said:**
> No errors there then.

Imo its a problem with alsa and as alsa is the backend for pulseaudio, pulseaudio wont work either :(

Try fully uninstalling and reinstalling alsa. Open a terminal and copy and paste the following:

```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```

If you still have no luck you will probably have to compile alsa from source. Or use the helpful script in the following post:

[http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695)



Running the command now.  

As an aside, I rebooted into Windows and played ME for a bit, then came back...and the sound works...

I'm sure it shouldn't be a connection, but it is weirding me out...

EDIT: Rebooting and it worked, but I won't know if anything's changed till tomorrow.  

You know, I've installed Ubuntu a bunch of times and this is teh only time I've had problems like this.  Or at all...

---

### Post by Tomatz on 2008-12-17
> **Morticutor UK said:**
> Running the command now.  

As an aside, I rebooted into Windows and played ME for a bit, then came back...and the sound works...

I'm sure it shouldn't be a connection, but it is weirding me out...

EDIT: Rebooting and it worked, but I won't know if anything's changed till tomorrow.  

You know, I've installed Ubuntu a bunch of times and this is teh only time I've had problems like this.  Or at all...

Yeah 8.10 has only been out for a short while so not all compatibility problems have been fixed. I run 8.04 and have no problems with anything whatsoever. Well unless i mess it up lol.

---

### Post by Morticutor UK on 2008-12-18
Yup, not working.  ](*,)

I've no idea what to try next...

---

### Post by Tomatz on 2008-12-18
> **Morticutor UK said:**
> Yup, not working.  ](*,)

I've no idea what to try next...

Even compiling from source?

I'm stumped. Your next step really is filing a bug at launchpad and hopefully a developer will help you. 

[https://bugs.launchpad.net/ubuntu/intrepid](https://bugs.launchpad.net/ubuntu/intrepid)

Either that or install hardy (8.04)

---

### Post by Morticutor UK on 2008-12-18
> **Tomatz said:**
> Even compiling from source?

I'm stumped. Your next step really is filing a bug at launchpad and hopefully a developer will help you. 

[https://bugs.launchpad.net/ubuntu/intrepid](https://bugs.launchpad.net/ubuntu/intrepid)

Either that or install hardy (8.04)

I haven't tried compiling from source, mostly because I lack confidence in my ability to get it right.  And the sound does work - I've just rebooted from playing Mass Effect again and I have the sound back...

---

### Post by Tomatz on 2008-12-18
> **Morticutor UK said:**
> I haven't tried compiling from source, mostly because I lack confidence in my ability to get it right.  And the sound does work - I've just rebooted from playing Mass Effect again and I have the sound back...

Sorry what i mean is did you try the script in the link i posted. This will compile alsa from source for you easily.

---

### Post by Morticutor UK on 2008-12-18
> **Tomatz said:**
> Sorry what i mean is did you try the script in the link i posted. This will compile alsa from source for you easily.

I've run the script.  I haven't logged in/out yet, mostly because I'm doing other things and am trying to catch up on the radio.

---

### Post by Tomatz on 2008-12-18
> **Morticutor UK said:**
> I've run the script.  I haven't logged in/out yet, mostly because I'm doing other things and am trying to catch up on the radio.

Cool. Let me know how it goes :)

---

### Post by Morticutor UK on 2009-01-14
OK, so...

I have tried editing the alsabase file, with no luck - I managed get sound with one control, but only for one user session.  

One suggestion I found was to deactivate one of my soundcards (I register as having two), but the BIOS controls won't let me.  

According to the ALSA wiki my Intel card (the ICH9) isn't supported anyway, and I tried purging ALSA and compiling OSS instead from another howto.  Didn't work.  

I really don't understand this. I do and have had sound, but not natively.  

I've logged a bug report.  Hopefully something will come out of it, or it's back to Windows - I need sound for my work.

---

### Post by fenian on 2009-01-17
I think you need to use Alsa 1.0.18a for your sound card to work.Use the attached script to install alsa for HDA-Intel on Ubuntu 8.10.To run the script download and extract it to your desktop  then in a terminal enter...

> cd ~/Desktop
sh alsa-intelhd.sh

---

