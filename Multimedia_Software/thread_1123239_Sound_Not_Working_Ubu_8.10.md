---
title: "Sound Not Working Ubu 8.10"
date: 2009-04-12
forum: Multimedia Software
---

### Post by 8Bit_Matt on 2009-04-12
I am having some trouble getting ANY sound to play no matter what program or test program I use.

First I tried this and it worked for about 10 min the stopped.
[HTML]http://onlyubuntu.blogspot.com/2008/11/fix-for-no-sound-issue-in-ubuntu-810.html[/HTML]

Next I tried this, which did not seem to fix the issue.
[HTML]http://ubuntuforums.org/showthread.php?t=789578[/HTML]

Then I tried looking for something to show me how to completely remove my sound system and reinstall, but that did not end well.  

So, here I am.

I did:
```
8bit:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

Then I did:
```
8bit:~$ pkill pulseaudio; sleep 2; pulseaudio -vv
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
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1002_4378_sound_card_0_alsa_playback_0
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1002_4378_sound_card_0_alsa_capture_0
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1002_4378_sound_card_0_alsa_control__1
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_1002_4370_sound_card_0_alsa_playback_0'
D: alsa-util.c: Trying front:0...
W: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
I: module-alsa-sink.c: Successfully opened device front:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: sink.c: Created sink 0 "alsa_output.pci_1002_4370_sound_card_0_alsa_playback_0" with sample spec "s16le 2ch 48000Hz"
I: source.c: Created source 0 "alsa_output.pci_1002_4370_sound_card_0_alsa_playback_0.monitor" with sample spec "s16le 2ch 48000Hz"
I: module-alsa-sink.c: Using 8 fragments of size 1760 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #0; argument: "device_id=0 sink_name=alsa_output.pci_1002_4370_sound_card_0_alsa_playback_0").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 source_name=alsa_input.pci_1002_4370_sound_card_0_alsa_capture_0'
D: alsa-util.c: Trying front:0...
W: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: source.c: Created source 1 "alsa_input.pci_1002_4370_sound_card_0_alsa_capture_0" with sample spec "s16le 2ch 48000Hz"
I: module-alsa-source.c: Using 8 fragments of size 1760 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
I: module.c: Loaded "module-alsa-source" (index: #1; argument: "device_id=0 source_name=alsa_input.pci_1002_4370_sound_card_0_alsa_capture_0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1002_4370_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 2 modules.
I: module.c: Loaded "module-hal-detect" (index: #2; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #3; argument: "").
I: protocol-native.c: loading cookie from disk.
I: module.c: Loaded "module-native-protocol-unix" (index: #4; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
D: module-gconf.c: Loading module 'module-rtp-recv' with args '' due to GConf configuration.
I: module.c: Loaded "module-rtp-recv" (index: #5; argument: "").
I: module.c: Loaded "module-gconf" (index: #6; argument: "").
I: module.c: Loaded "module-volume-restore" (index: #7; argument: "").
D: module-default-device-restore.c: Restored default sink 'alsa_output.pci_1002_4370_sound_card_0_alsa_playback_0'.
D: core-subscribe.c: dropped redundant event.
D: module-default-device-restore.c: Restored default source 'alsa_input.pci_1002_4370_sound_card_0_alsa_capture_0'.
I: module.c: Loaded "module-default-device-restore" (index: #8; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #9; argument: "").
D: module-suspend-on-idle.c: Sink alsa_output.pci_1002_4370_sound_card_0_alsa_playback_0 becomes idle.
D: module-suspend-on-idle.c: Source alsa_output.pci_1002_4370_sound_card_0_alsa_playback_0.monitor becomes idle.
D: module-suspend-on-idle.c: Source alsa_input.pci_1002_4370_sound_card_0_alsa_capture_0 becomes idle.
I: module.c: Loaded "module-suspend-on-idle" (index: #10; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-x11-publish.so': success
D: module-x11-publish.c: using already loaded auth cookie.
I: module.c: Loaded "module-x11-publish" (index: #11; argument: "").
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module-suspend-on-idle.c: Source alsa_input.pci_1002_4370_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.pci_1002_4370_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Sink alsa_output.pci_1002_4370_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-rtp-recv.c: Checking for dead streams ...
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-rtp-recv.c: Checking for dead streams ...
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-rtp-recv.c: Checking for dead streams ...
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-rtp-recv.c: Checking for dead streams ...
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
```




Now I am somewhat stuck ... soundless.  Anyone have any suggestions?

---

### Post by wolfen69 on 2009-04-12
it looks like you are having trouble with your modules.

you could try rebuilding alsa and go from there.

enable your backports repos first. then apt-get update.

then
```
sudo apt-get install module-assistant
```
then
```
sudo m-a a-i alsa
```
then reboot

then
```
sudo rmmod alsa && sudo modprobe alsa
```
then go into volume control to make sure all sound levels are correct.

then you can go back and disable your backports repos.

---

### Post by 8Bit_Matt on 2009-04-12
Thank you!  I did the first two steps (before the reboot) and I got an error on the ALSA rebuild.

```
for i in control postinst postrm ; do \                                    &#8593;
 &#9474;         if [ -f debian/$i.orig ]; then \                                   &#9646;
 &#9474;         mv -f debian/$i.orig debian/$i ; \                                 &#9618;
 &#9474;         fi ; \                                                             &#9618;
 &#9474;         done                                                               &#9618;
 &#9474; rm -f control-munge                                                        &#9618;
 &#9474; make mrproper                                                              &#9618;
 &#9474; make[1]: Entering directory `/usr/src/modules/alsa-driver'                 &#9618;
 &#9474; rm -f .depend *.o snd.map*                                                 &#9618;
 &#9474; rm -f /*.ver                                                               &#9618;
 &#9474; rm -f modules/*.o modules/*.ko                                             &#9618;
 &#9474; make[2]: Entering directory `/usr/src/modules/alsa-driver/acore'           &#9618;
 &#9474; make[2]: Leaving directory `/usr/src/modules/alsa-driver/acore'            &#9618;
 &#9474; make[1]: Leaving directory `/usr/src/modules/alsa-driver'                  &#9618;
 &#9474; rm -f configure-stamp                  
```

I tried to get the entire code, but it does not appear to have let me.

Any other suggestions?

---

### Post by 8Bit_Matt on 2009-04-12
I should also mention that now I am having a problem with my Add/Remove programs.  As in it is displaying NOTHING. Like there are no programs for my OS.

I would prefer to fix the glitch, however it is a new build should I consider a complete format / reinstall?

---

### Post by wolfen69 on 2009-04-12
since it is a new build, yes, a reinstall sounds like it is in order. however, i would try [ubuntu 9.04]("http://cdimage.ubuntu.com/daily-live/current/"). your sound may work with the new release. remember you have to update it manually.

---

### Post by ravindran.k on 2009-04-14
coastgnus's method of disabling unnecessary stuff [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/187963](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/187963)
 worked for me :)

---

