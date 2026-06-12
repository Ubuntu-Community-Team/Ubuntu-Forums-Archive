---
title: "No Sound After Boot"
date: 2011-04-09
forum: Multimedia Software
---

### Post by Deersindal on 2011-04-09
After installing and uninstalling a couple backports modules in synaptic and reinstalling almost every alsa package, I have no sound in ubuntu after the boot chime.

In my sound preferences, No hardware is listed and only "dummy output" is available under the outputs option.

This is quite frustrating, but I guess that if it isn't resolved by April 28th, then I can always do a clean install with 11.04. :mad:

---

### Post by xaviers67 on 2011-04-09
Hi,

Please check that you have installed the drivers properly of the sound now
First you must find which model of sound card you use, so run this command:

cat /proc/asound/card0/codec#* | grep Codec
It will return model of your sound card(s), for example: "Codec: Realtek ALC260", so your sound card is ALC260.

You should open a file in ALSA documentation. This file is here:

/usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz
or if that file does not exist, try:

/usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz
or check: HD-Audio-Models

---

### Post by Deersindal on 2011-04-09
Here are the results of the command:
```
jonathan@Aspire:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC271X
```
I know that I need to find the appropriate description of my sound card, but the ALC271X is not listed in the documentation file.

EDIT: I should mention I am using an Acer Aspire 5553G-5357

---

### Post by Deersindal on 2011-04-09
This is important:

I have sound for system sounds (e.g. the ping when I get a message on empathy)
I also have sound for flash applications on firefox (e.g. youtube)

I DO NOT have sound for banshee, any mp3s I hover on for preview in nautilus, or on VLC or Totem.
In sound preferences, I still have no devices recognized.

This is quite a strange problem, and I feel it has something to do with the use of pulse, alsa, and oss in different ubuntu applications and one of those protocols isn't recognizing my sound card.

---

### Post by Yellow Pasque on 2011-04-10
Basically, alsa apps are working, but pulse not. Try deleting the user-specific pulse info and logging out/in.
```
cd
rm -rf ~/.pulse*
```

---

### Post by Deersindal on 2011-04-10
> **Temüjin said:**
> Basically, alsa apps are working, but pulse not. Try deleting the user-specific pulse info and logging out/in.
```
cd
rm -rf ~/.pulse*
```

I ran the command and logged out and in. I still don't have sound in any of the applications I listed before, but now when I try to go to System > Preferences > Sound, it hangs on a window saying "Waiting for sound system to respond."

If I try to go to Applications > Sound & Video > PulseAudio Volume Control, an error window comes up saying "Connection failed: Connection refused."

---

### Post by Yellow Pasque on 2011-04-10
I would try starting pulseaudio from terminal and see what it says:
```
pulseaudio -v
```

You could you also try creating another user and seeing if that one has issues or purging pulseaudio packages and reinstalling them.

---

### Post by Deersindal on 2011-04-10
Here is what I get when I run pulseaudio -v in terminal:

```
jonathan@Aspire:~$ pulseaudio -v
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: core-util.c: Successfully gained nice level -11.
I: main.c: This is PulseAudio 0.9.21-63-gd3efa-dirty
I: main.c: Page size is 4096 bytes
I: main.c: Machine ID is de11c41af534b0840cc8631100000007.
I: main.c: Session ID is de11c41af534b0840cc8631100000007-1302464690.83913-2036639028.
I: main.c: Using runtime directory /home/jonathan/.pulse/de11c41af534b0840cc8631100000007-runtime.
I: main.c: Using state directory /home/jonathan/.pulse.
I: main.c: Using modules directory /usr/lib/pulse-0.9.21/modules.
I: main.c: Running in system mode: no
I: main.c: Fresh high-resolution timers available! Bon appetit!
I: cpu-x86.c: CPU flags: CMOV MMX SSE SSE2 SSE3 MMXEXT 3DNOW 3DNOWEXT 
I: svolume_mmx.c: Initialising MMX optimized functions.
I: remap_mmx.c: Initialising MMX optimized remappers.
I: svolume_sse.c: Initialising SSE2 optimized functions.
I: remap_sse.c: Initialising SSE2 optimized remappers.
I: sconv_sse.c: Initialising SSE2 optimized conversions.
I: module-device-restore.c: Sucessfully opened database file '/home/jonathan/.pulse/de11c41af534b0840cc8631100000007-device-volumes'.
I: module.c: Loaded "module-device-restore" (index: #0; argument: "").
I: module-stream-restore.c: Sucessfully opened database file '/home/jonathan/.pulse/de11c41af534b0840cc8631100000007-stream-volumes'.
I: module.c: Loaded "module-stream-restore" (index: #1; argument: "").
I: module-card-restore.c: Sucessfully opened database file '/home/jonathan/.pulse/de11c41af534b0840cc8631100000007-card-database'.
I: module.c: Loaded "module-card-restore" (index: #2; argument: "").
I: module.c: Loaded "module-augment-properties" (index: #3; argument: "").
E: module.c: Failed to open module "module-alsa-card": file not found
I: module-udev-detect.c: Card /devices/pci0000:00/0000:00:02.0/0000:02:00.1/sound/card1 (alsa_card.pci-0000_02_00.1) failed to load module.
E: module.c: Failed to open module "module-alsa-card": file not found
I: module-udev-detect.c: Card /devices/pci0000:00/0000:00:14.2/sound/card0 (alsa_card.pci-0000_00_14.2) failed to load module.
I: module-udev-detect.c: Found 2 cards.
I: module.c: Loaded "module-udev-detect" (index: #4; argument: "").
I: module.c: Loaded "module-bluetooth-discover" (index: #5; argument: "").
E: socket-server.c: bind(): Address already in use
E: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.
I: module.c: Unloading "module-device-restore" (index: #0).
I: module.c: Unloaded "module-device-restore" (index: #0).
I: module.c: Unloading "module-stream-restore" (index: #1).
I: module.c: Unloaded "module-stream-restore" (index: #1).
I: module.c: Unloading "module-card-restore" (index: #2).
I: module.c: Unloaded "module-card-restore" (index: #2).
I: module.c: Unloading "module-augment-properties" (index: #3).
I: module.c: Unloaded "module-augment-properties" (index: #3).
I: module.c: Unloading "module-udev-detect" (index: #4).
I: module.c: Unloaded "module-udev-detect" (index: #4).
I: module.c: Unloading "module-bluetooth-discover" (index: #5).
I: module.c: Unloaded "module-bluetooth-discover" (index: #5).
I: main.c: Daemon terminated.
```

Which pulseaudio packages would you recommend I try purging? I will create a new user now and report back with how well that worked.
[B]
EDIT:[/B] The new user did not have any sound either.

---

### Post by Deersindal on 2011-04-11
Today I purged and reinstalled a few pulse packages. pulseaudio is running at boot, so I killed the process (still only registering 'dummy output') and ran pulseaudio -v again. Here were my results.

```
jonathan@Aspire:~$ pulseaudio -v
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: core-util.c: Successfully gained nice level -11.
I: main.c: This is PulseAudio 0.9.21-63-gd3efa-dirty
I: main.c: Page size is 4096 bytes
I: main.c: Machine ID is de11c41af534b0840cc8631100000007.
I: main.c: Session ID is de11c41af534b0840cc8631100000007-1302568862.188579-1589290952.
I: main.c: Using runtime directory /home/jonathan/.pulse/de11c41af534b0840cc8631100000007-runtime.
I: main.c: Using state directory /home/jonathan/.pulse.
I: main.c: Using modules directory /usr/lib/pulse-0.9.21/modules.
I: main.c: Running in system mode: no
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.
jonathan@Aspire:~$ sudo killall pulseaudio
[sudo] password for jonathan: 
jonathan@Aspire:~$ pulseaudio -v
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: core-util.c: Successfully gained nice level -11.
I: main.c: This is PulseAudio 0.9.21-63-gd3efa-dirty
I: main.c: Page size is 4096 bytes
I: main.c: Machine ID is de11c41af534b0840cc8631100000007.
I: main.c: Session ID is de11c41af534b0840cc8631100000007-1302568862.188579-1589290952.
I: main.c: Using runtime directory /home/jonathan/.pulse/de11c41af534b0840cc8631100000007-runtime.
I: main.c: Using state directory /home/jonathan/.pulse.
I: main.c: Using modules directory /usr/lib/pulse-0.9.21/modules.
I: main.c: Running in system mode: no
I: main.c: Fresh high-resolution timers available! Bon appetit!
I: cpu-x86.c: CPU flags: CMOV MMX SSE SSE2 SSE3 MMXEXT 3DNOW 3DNOWEXT 
I: svolume_mmx.c: Initialising MMX optimized functions.
I: remap_mmx.c: Initialising MMX optimized remappers.
I: svolume_sse.c: Initialising SSE2 optimized functions.
I: remap_sse.c: Initialising SSE2 optimized remappers.
I: sconv_sse.c: Initialising SSE2 optimized conversions.
I: module-device-restore.c: Sucessfully opened database file '/home/jonathan/.pulse/de11c41af534b0840cc8631100000007-device-volumes'.
I: module.c: Loaded "module-device-restore" (index: #0; argument: "").
I: module-stream-restore.c: Sucessfully opened database file '/home/jonathan/.pulse/de11c41af534b0840cc8631100000007-stream-volumes'.
I: module.c: Loaded "module-stream-restore" (index: #1; argument: "").
I: module-card-restore.c: Sucessfully opened database file '/home/jonathan/.pulse/de11c41af534b0840cc8631100000007-card-database'.
I: module.c: Loaded "module-card-restore" (index: #2; argument: "").
I: module.c: Loaded "module-augment-properties" (index: #3; argument: "").
E: module.c: Failed to open module "module-alsa-card": file not found
I: module-udev-detect.c: Card /devices/pci0000:00/0000:00:02.0/0000:02:00.1/sound/card1 (alsa_card.pci-0000_02_00.1) failed to load module.
E: module.c: Failed to open module "module-alsa-card": file not found
I: module-udev-detect.c: Card /devices/pci0000:00/0000:00:14.2/sound/card0 (alsa_card.pci-0000_00_14.2) failed to load module.
I: module-udev-detect.c: Found 2 cards.
I: module.c: Loaded "module-udev-detect" (index: #4; argument: "").
I: module.c: Loaded "module-bluetooth-discover" (index: #5; argument: "").
I: module.c: Loaded "module-esound-protocol-unix" (index: #6; argument: "").
I: module.c: Loaded "module-native-protocol-unix" (index: #7; argument: "").
I: module.c: Loaded "module-gconf" (index: #8; argument: "").
I: module-default-device-restore.c: Saved default sink 'auto_null' not existant, not restoring default sink setting.
I: module-default-device-restore.c: Saved default source 'auto_null.monitor' not existant, not restoring default source setting.
I: module.c: Loaded "module-default-device-restore" (index: #9; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #10; argument: "").
I: module-device-restore.c: Restoring volume for sink auto_null.
I: sink.c: Created sink 0 "auto_null" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: sink.c:     device.description = "Dummy Output"
I: sink.c:     device.class = "abstract"
I: sink.c:     device.icon_name = "audio-card"
I: source.c: Created source 0 "auto_null.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: source.c:     device.description = "Monitor of Dummy Output"
I: source.c:     device.class = "monitor"
I: source.c:     device.icon_name = "audio-input-microphone"
I: module.c: Loaded "module-null-sink" (index: #11; argument: "sink_name=auto_null sink_properties='device.description="Dummy Output"'").
I: module.c: Loaded "module-always-sink" (index: #12; argument: "").
I: module.c: Loaded "module-intended-roles" (index: #13; argument: "").
I: module.c: Loaded "module-suspend-on-idle" (index: #14; argument: "").
I: client.c: Created 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session2"
I: module.c: Loaded "module-console-kit" (index: #15; argument: "").
I: module.c: Loaded "module-position-event-sounds" (index: #16; argument: "").
I: main.c: Daemon startup complete.
I: client.c: Created 1 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: client.c: Created 2 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: module-suspend-on-idle.c: Sink auto_null idle for too long, suspending ...
```

And the command hangs at that line. Any ideas?

---

### Post by Yellow Pasque on 2011-04-11
This is the part that jumps out to me:
```
E: module.c: Failed to open module "module-alsa-card": file not found
I: module-udev-detect.c: Card /devices/pci0000:00/0000:00:02.0/0000:02:00.1/sound/card1 (alsa_card.pci-0000_02_00.1) failed to load module.
E: module.c: Failed to open module "module-alsa-card": file not found
I: module-udev-detect.c: Card /devices/pci0000:00/0000:00:14.2/sound/card0 (alsa_card.pci-0000_00_14.2) failed to load module.
I: module-udev-detect.c: Found 2 cards.
```

Can't find much with google though.

---

### Post by Deersindal on 2011-04-11
Well, it appears that I have found a solution. I was looking around for an unstable ppa for pulseaudio to possibly remedy the situtation and I came across this one.

**[https://launchpad.net/~ricotz/+archive/unstable]("https://launchpad.net/%7Ericotz/+archive/unstable")**

I added it to my software sources, updated, and it upgraded several audio-related packages, including pulseaudio and alsa packages. Everything is as it should be for now.

Thank you for all of your help, Temüjin. It's people like you who keep people like me from going insane sometimes ;)

---

