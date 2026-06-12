---
title: "No sound after upgrade"
date: 2009-01-06
forum: Multimedia Software
---

### Post by 24601oxy on 2009-01-06
My sound issues actually started after upgrading to 8.04. At first the sound was completely missing, but a workaround showed up. If I put my laptop into suspend, usually when it resumed the sound would work. The computer became usable, so I didn't really bother to try and fix it. 

I upgraded to 8.10 this weekend, and the workaround no longer seems to work. I would appreciate if anyone could help me fix this issue...

---

### Post by theozzlives on 2009-01-06
what kind of sound card?

---

### Post by 24601oxy on 2009-01-06
I think its an Intel. Whatever is built into a Dell Inspiron 1420.

---

### Post by 24601oxy on 2009-01-10
Could anyone help me figure this out?

---

### Post by bigtom71 on 2009-01-10
I had the same problem and saw somewhere on the forum to run in terminal sudo apt-get install linux-rt and then reboot and would solve sound problems in 8.04. I ran it and it solved my problems.

---

### Post by 24601oxy on 2009-01-11
No luck...

---

### Post by 24601oxy on 2009-01-14
I would really appreciate it if anyone could help.

This is my exact soundcard specs-- 

```
 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: Dell Device 01f3
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at fe9fc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

---

### Post by 24601oxy on 2009-01-26
I really hate to bump things up, but this problem is getting annoying...

---

### Post by Linuxdork on 2009-01-26
What's the output of lsmod?

---

### Post by 24601oxy on 2009-01-26
```
Module                  Size  Used by
nls_iso8859_1          12032  0 
vfat                   18816  0 
fat                    57376  1 vfat
usb_storage            81728  0 
libusual               27156  1 usb_storage
nls_cp437              13696  1 
isofs                  40100  1 
udf                    88356  0 
crc_itu_t              10112  1 udf
i915                   38144  2 
drm                    86056  3 i915
af_packet              25728  4 
binfmt_misc            16904  1 
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
ipv6                  263972  14 
ppdev                  15620  0 
acpi_cpufreq           15500  1 
cpufreq_userspace      11396  0 
cpufreq_stats          13188  0 
cpufreq_powersave       9856  0 
cpufreq_ondemand       14988  1 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative    14600  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
pci_slot               12552  0 
container              11520  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
arc4                    9984  2 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
iwl3945                98804  0 
dcdbas                 15008  0 
evdev                  17696  15 
rfkill                 17176  2 iwl3945
mac80211              216820  1 iwl3945
led_class              12164  1 iwl3945
snd_hda_intel         381488  5 
cfg80211               32392  2 iwl3945,mac80211
psmouse                45200  0 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
serio_raw              13444  0 
snd_pcm                83204  3 snd_hda_intel,snd_pcm_oss
sdhci_pci              15360  0 
sdhci                  23940  1 sdhci_pci
ricoh_mmc              11904  0 
mmc_core               58268  1 sdhci
snd_seq_dummy          10884  0 
video                  25104  0 
output                 11008  1 video
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcspkr                 10624  0 
battery                18436  0 
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
wmi                    14504  0 
button                 14224  0 
ac                     12292  0 
snd                    63268  19 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
intel_agp              33724  1 
agpgart                42184  3 drm,intel_agp
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
ext3                  133384  2 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  1 
cdrom                  43168  1 sr_mod
sd_mod                 42264  4 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_piix               24580  1 
pata_acpi              12160  0 
usbhid                 35840  0 
hid                    50560  1 usbhid
ahci                   37132  3 
ata_generic            12932  0 
ohci1394               37936  0 
libata                177312  4 ata_piix,pata_acpi,ahci,ata_generic
scsi_mod              155212  5 usb_storage,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
ieee1394               96324  1 ohci1394
tg3                   129924  0 
libphy                 27392  1 tg3
ehci_hcd               43276  0 
uhci_hcd               30736  0 
usbcore               148848  6 usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

```

---

### Post by Linuxdork on 2009-01-26
Okay, the snd modules all seem to be loaded.  I bet it's a pulseaudio issue.  Try this link.  It helped all of my issues.

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by 24601oxy on 2009-01-26
I followed instructions A and C (general and 8.10), and still no sound. 

I got to Appendix A, and have part C 
> The application does not play audio and does list an entry in the Playback tab;
- the application is using PulseAudio but there is a problem, such as: a bug in PulseAudio, a problem with your ALSA kernel module or libraries, or your PCM/Master volume is muted.  

I'm pretty sure that my master volume isn't muted, I've checked a bunch of times. So I guess its an ALSA problem? 

It said to post the results of the following commands. 

$ aplay -l
```
 **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice # 
```

 $ pkill pulseaudio; sleep 2; pulseaudio -vv

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
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0'
D: alsa-util.c: Trying front:0...
I: module-alsa-sink.c: Successfully opened device front:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: sink.c: Created sink 0 "alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0" with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 0 "alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0.monitor" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-sink.c: Using 8 fragments of size 1792 bytes.
I: alsa-util.c: ALSA device lacks independant volume controls for each channel, falling back to software volume control.
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #0; argument: "device_id=0 sink_name=alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 source_name=alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0'
D: alsa-util.c: Trying front:0...
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: source.c: Created source 1 "alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-source.c: Using 8 fragments of size 1792 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
I: module.c: Loaded "module-alsa-source" (index: #1; argument: "device_id=0 source_name=alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_284b_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 2 modules.
I: module.c: Loaded "module-hal-detect" (index: #2; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #3; argument: "").
I: protocol-native.c: loading cookie from disk.
I: module.c: Loaded "module-native-protocol-unix" (index: #4; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #5; argument: "").
I: module.c: Loaded "module-volume-restore" (index: #6; argument: "").
D: module-default-device-restore.c: Restored default sink 'alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0'.
D: core-subscribe.c: dropped redundant event.
D: module-default-device-restore.c: Restored default source 'alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0'.
I: module.c: Loaded "module-default-device-restore" (index: #7; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #8; argument: "").
D: module-suspend-on-idle.c: Sink alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0 becomes idle.
D: module-suspend-on-idle.c: Source alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0.monitor becomes idle.
D: module-suspend-on-idle.c: Source alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0 becomes idle.
I: module.c: Loaded "module-suspend-on-idle" (index: #9; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-x11-publish.so': success
D: module-x11-publish.c: using already loaded auth cookie.
I: module.c: Loaded "module-x11-publish" (index: #10; argument: "").
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module-suspend-on-idle.c: Source alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Sink alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...

I: main.c: Got signal SIGTERM.
I: main.c: Exiting.
I: main.c: Daemon shutdown initiated.
I: module.c: Unloading "module-alsa-sink" (index: #0).
D: module-rescue-streams.c: No sink inputs to move away.
D: module-rescue-streams.c: No source outputs to move away.
D: module-alsa-sink.c: Thread shutting down
I: sink.c: Freeing sink 0 "alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0"
I: source.c: Freeing source 0 "alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0.monitor"
I: module.c: Unloaded "module-alsa-sink" (index: #0).
I: module.c: Unloading "module-alsa-source" (index: #1).
D: module-rescue-streams.c: No source outputs to move away.
D: module-alsa-source.c: Thread shutting down
I: source.c: Freeing source 1 "alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0"
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

``` 

That looks like something might be wrong...

---

### Post by Linuxdork on 2009-01-26
Okay, that's interesting.  I'm no expert but I think alsa might be hosed.  I probably should have asked you if you followed this first: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)  This is a sticky in the Multimedia & Video section of this forum.  I'm thinking you will need to unload (uninstall) alsa and reload.  Follow that thread if you haven't and keep us updated.

---

### Post by 24601oxy on 2009-01-27
Ok... so I did all this last night, and got nothing. I got up to reinstalling the drivers from Kernal. 

But when I came back today (from an overnight suspend), I was planning to try and compile the drivers. But, I decided to try a few steps again, especially sudo modprobe snd-hda-intel, which produces no message, error or success or otherwise. 

So... a little later, I notice the sound is back! I do some stuff, some of it sound, some not. Eventually, I reboot. When I get back... no sound. I tried sudo modprobe snd-hda-intel again, and got nothing. Tried suspending, nothing. Tried the command again, still nothing. 

This is really weird.

---

### Post by Linuxdork on 2009-01-27
Interesting indeed.  When you do:

```
sudo modprobe snd-hda-intel
```

you don't want any output.  If it is quiet, that means that the module was found and loaded.  I'm kindof at a loss now, to me it still sounds like alsa or pulseaudio is broke.  Did you add snd-hda-intel to /etc/modules ?

---

### Post by markbuntu on 2009-01-27
There is a listing here for the Dell Inspirion 1420n

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

If you think your problem may be more involved

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by 24601oxy on 2009-01-27
> **Linuxdork said:**
> Interesting indeed.  When you do:

```
sudo modprobe snd-hda-intel
```

you don't want any output.  If it is quiet, that means that the module was found and loaded.  I'm kindof at a loss now, to me it still sounds like alsa or pulseaudio is broke.  Did you add snd-hda-intel to /etc/modules ?

Yeah, I added it after trying to reload the module after rebooting. Neither that, not loading them by hand worked.

---

### Post by Linuxdork on 2009-01-27
> **markbuntu said:**
> There is a listing here for the Dell Inspirion 1420n

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

If you think your problem may be more involved

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Those look like some nice guides/resources.  Very well done.  I will definitely be adding those to my troubleshooting lists.  Thanks.

---

### Post by 24601oxy on 2009-01-27
> **markbuntu said:**
> There is a listing here for the Dell Inspirion 1420n

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

If you think your problem may be more involved

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

The first one seems to work. I haven't rebooted yet though...

---

### Post by 24601oxy on 2009-01-28
Yeah, Ok. I'm marking this as solved. 

Thanks for everyone's help.

---

### Post by Linuxdork on 2009-01-28
You're welcome.  Sorry I didn't lead you in the right spot.

---

