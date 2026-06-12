---
title: "suddenly no sound after weird behaviour"
date: 2009-02-09
forum: Multimedia Software
---

### Post by t-mo_ on 2009-02-09
I'm running intrepid with 2.6.27-3-rt kernel on a eeepc900 with 2GB Ram. I was using a M-Audio Transit USB sound card without problems. A week ago I purchased a ESI MAYA44 USB (AFTER trying out), and it was totally plug n' play.

The only thing I've done is removing the volume control applet from the panel, it caused incredibly high CPU usage.
After the next reboot, channel 1+2 was not master anymore, it changed without a reason to channel 3+4, but no other problems.

Next reboot, sound was gone. It seems like Pulse audio is not able to connect/find the ESI MAYA44 USB anymore. After following every how to I found and still having no solution, I found out there is also a problem for klodg to find the System.map. It is reported as a bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/277924]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/277924")
Already tried different variations to fix this in /etc/init.d/klogd. The last attempt I commented out, result of all attempts was that the boot process was hanging for a while, saying "chown: cannot access "/var/log/whatever" (this could be normal, I mount /var to RAM)
```
#  Use KLOGD="-k /boot/System.map-$(uname -r)" to specify System.map
#
KLOGD="-P $kmsgpipe"
# KLOGD="-k /boot/System.map-2.6.27-3-rt"
```

some other output:
```
tmo@timotor:~$ lsusb
Bus 005 Device 009: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 005 Device 008: ID 152e:2507 LG (HLDS) 
Bus 005 Device 007: ID 0603:00f2 Novatek Microelectronics Corp. 
Bus 005 Device 006: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 005 Device 005: ID 04f2:b071 Chicony Electronics Co., Ltd 
Bus 005 Device 004: ID 0951:1606 Kingston Technology 
Bus 005 Device 002: ID 059f:0c41 LaCie, Ltd 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 016: ID 0a92:0091 EGO SYStems, Inc. Maya 44
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

```
lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
03:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0
```

```
tmo@timotor:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf7eb8000 irq 5
 1 [USB            ]: USB-Audio - MAYA44 USB
                      AUDIOTRAK MAYA44 USB at usb-0000:00:1d.1-2, full speed

```
I see, there is no irq for MAYA44, and it's recognized as AUDIOTRACK instead of ESI... No idea what this means.

```
tmo@timotor:~$ cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_usb_audio

```


```
tmo@timotor:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: USB [MAYA44 USB], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
tmo@timotor:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: USB [MAYA44 USB], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
```
tmo@timotor:~$ alsamixer
ALSA lib pulse.c:272:(pulse_connect) PulseAudio: Unable to connect: Connection refused


alsamixer: function snd_ctl_open failed for default: Connection refused

```

```
tmo@timotor:~$ pulseaudio -D
W: ltdl-bind-now.c: Failed to find original dlopen loader.
E: main.c: daemon startup failed.

```

Working on this since days, without success.. any help would be very appreciated. BTW, the internal sound card only works when I set System/Preferences/Sound to "Autodetect". If I choose the Hardware [HDA Intel ALC662 Analog (ALSA)] a error message comes up..

```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.
```

---

### Post by t-mo_ on 2009-02-09
As recommended by psyke83 in his great How To [http://ubuntuforums.org/showthread.php?t=789578&highlight=pulse]("http://ubuntuforums.org/showthread.php?t=789578&highlight=pulse")(Appendix A), I also post this output:
```
 pkill pulseaudio; sleep 2; pulseaudio -vv
I: main.c: PolicyKit refuses acquire-high-priority privilige.
I: main.c: We're in the group 'pulse-rt', allowing real-time and high-priority scheduling.
I: core-util.c: Successfully gained nice level -11.
W: ltdl-bind-now.c: **Failed to find original dlopen loader.**
I: main.c: This is PulseAudio 0.9.10
I: main.c: Page size is 4096 bytes
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-hal-detect.so': success
I: module-hal-detect.c: Trying capability alsa
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/usb_device_a92_91_noserial_if0_sound_card_0_alsa_control__1
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=1 source_name=alsa_input.usb_device_a92_91_noserial_if0_sound_card_0_alsa_capture_0'
D: alsa-util.c: Trying surround40:1...
I: module-alsa-source.c: Successfully opened device surround40:1.
I: module-alsa-source.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL surround40:1
I: alsa-util.c: Unable to attach to mixer surround40:1: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:1'
I: alsa-util.c: Cannot find mixer control "Capture".
W: alsa-util.c: **Cannot find fallback mixer control "Mic".**
I: source.c: Created source 0 "alsa_input.usb_device_a92_91_noserial_if0_sound_card_0_alsa_capture_0" with sample spec "s16le 4ch 44100Hz"
I: module-alsa-source.c: Using 8 fragments of size 1760 bytes.
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
I: module.c: Loaded "module-alsa-source" (index: #0; argument: "device_id=1 source_name=alsa_input.usb_device_a92_91_noserial_if0_sound_card_0_alsa_capture_0").
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=1 sink_name=alsa_output.usb_device_a92_91_noserial_if0_sound_card_0_alsa_playback_0'
D: alsa-util.c: Trying surround40:1...
I: module-alsa-sink.c: Successfully opened device surround40:1.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL surround40:1
I: alsa-util.c: Unable to attach to mixer surround40:1: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:1'
I: alsa-util.c: Using mixer control "Master".
I: sink.c: Created sink 0 "alsa_output.usb_device_a92_91_noserial_if0_sound_card_0_alsa_playback_0" with sample spec "s16le 4ch 44100Hz"
I: source.c: Created source 1 "alsa_output.usb_device_a92_91_noserial_if0_sound_card_0_alsa_playback_0.monitor" with sample spec "s16le 4ch 44100Hz"
I: module-alsa-sink.c: Using 8 fragments of size 1760 bytes.
I: alsa-util.c: ALSA device lacks separate volumes control for channel 'rear-left', falling back to software volume control.
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #1; argument: "device_id=1 sink_name=alsa_output.usb_device_a92_91_noserial_if0_sound_card_0_alsa_playback_0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_8086_2668_sound_card_0_alsa_playback_0'
D: alsa-util.c: Trying surround40:0...
I: alsa-util.c: PCM device surround40:0 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround41:0...
I: alsa-util.c: PCM device surround41:0 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround50:0...
I: alsa-util.c: PCM device surround50:0 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround51:0...
I: alsa-util.c: PCM device surround51:0 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround71:0...
I: alsa-util.c: PCM device surround71:0 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying front:0...
I: module-alsa-sink.c: Successfully opened device front:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: sink.c: Created sink 1 "alsa_output.pci_8086_2668_sound_card_0_alsa_playback_0" with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 2 "alsa_output.pci_8086_2668_sound_card_0_alsa_playback_0.monitor" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-sink.c: Using 8 fragments of size 896 bytes.
I: alsa-util.c: ALSA device lacks independant volume controls for each channel, falling back to software volume control.
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+27
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #2; argument: "device_id=0 sink_name=alsa_output.pci_8086_2668_sound_card_0_alsa_playback_0").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 source_name=alsa_input.pci_8086_2668_sound_card_0_alsa_capture_0'
D: alsa-util.c: Trying surround40:0...
I: alsa-util.c: PCM device surround40:0 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround41:0...
I: alsa-util.c: PCM device surround41:0 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround50:0...
I: alsa-util.c: PCM device surround50:0 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround51:0...
I: alsa-util.c: PCM device surround51:0 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround71:0...
I: alsa-util.c: PCM device surround71:0 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying front:0...
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: source.c: Created source 3 "alsa_input.pci_8086_2668_sound_card_0_alsa_capture_0" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-source.c: Using 8 fragments of size 896 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+26
I: module.c: Loaded "module-alsa-source" (index: #3; argument: "device_id=0 source_name=alsa_input.pci_8086_2668_sound_card_0_alsa_capture_0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_2668_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 4 modules.
I: module.c: Loaded "module-hal-detect" (index: #4; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #5; argument: "").
I: protocol-native.c: loading cookie from disk.
I: module.c: Loaded "module-native-protocol-unix" (index: #6; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #7; argument: "").
E: module-volume-restore.c:** [COLOR="Red"]parse failure in /home/tmo/.pulse/volume-restore.table:4, stopping parsing[/COLOR]**
E: module.c: **[COLOR="Red"]Failed to load  module "module-volume-restore" (argument: ""): initialization failed.[/COLOR]**
E: main.c: **[COLOR="Red"]Module load failed.[/COLOR]**
E: main.c: **[COLOR="Red"]Failed to initialize daemon.[/COLOR]**
I: module.c: Unloading "module-alsa-source" (index: #0).
D: module-alsa-source.c: Thread shutting down
I: source.c: Freeing source 0 "alsa_input.usb_device_a92_91_noserial_if0_sound_card_0_alsa_capture_0"
I: module.c: Unloaded "module-alsa-source" (index: #0).
I: module.c: Unloading "module-alsa-sink" (index: #1).
D: module-alsa-sink.c: Thread shutting down
I: sink.c: Freeing sink 0 "alsa_output.usb_device_a92_91_noserial_if0_sound_card_0_alsa_playback_0"
I: source.c: Freeing source 1 "alsa_output.usb_device_a92_91_noserial_if0_sound_card_0_alsa_playback_0.monitor"
I: module.c: Unloaded "module-alsa-sink" (index: #1).
I: module.c: Unloading "module-alsa-sink" (index: #2).
D: module-alsa-sink.c: Thread shutting down
I: sink.c: Freeing sink 1 "alsa_output.pci_8086_2668_sound_card_0_alsa_playback_0"
I: source.c: Freeing source 2 "alsa_output.pci_8086_2668_sound_card_0_alsa_playback_0.monitor"
I: module.c: Unloaded "module-alsa-sink" (index: #2).
I: module.c: Unloading "module-alsa-source" (index: #3).
D: module-alsa-source.c: Thread shutting down
I: source.c: Freeing source 3 "alsa_input.pci_8086_2668_sound_card_0_alsa_capture_0"
I: module.c: Unloaded "module-alsa-source" (index: #3).
I: module.c: Unloading "module-hal-detect" (index: #4).
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus.Local, path=/org/freedesktop/DBus/Local, member=Disconnected
I: module.c: Unloaded "module-hal-detect" (index: #4).
I: module.c: Unloading "module-esound-protocol-unix" (index: #5).
I: module.c: Unloaded "module-esound-protocol-unix" (index: #5).
I: module.c: Unloading "module-native-protocol-unix" (index: #6).
I: module.c: Unloaded "module-native-protocol-unix" (index: #6).
I: module.c: Unloading "module-gconf" (index: #7).
I: module.c: Unloaded "module-gconf" (index: #7).
I: main.c: Daemon terminated.

```

---

### Post by t-mo_ on 2009-02-10
I managed it to have sound again. The Channels are still mixed up (front is 3+4, rear 1+2) but I can live with that.

---

