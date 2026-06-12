---
title: "No sound in Ubuntu 9.04"
date: 2009-04-20
forum: Multimedia Software
---

### Post by Davestom on 2009-04-20
Hey Ubuntuforums

I'm new to Ubuntu, and just installed it today, so I'm sorry if I ask some stupid questions.
Everything worked fine and smoothly except the sound. 
In 8.10, I had no sound device installed, so I upgraded to the beta version of 9.04, and now I have a sound device, but no output in sound. I have checked a lot of guides, but they are mostly for Audigy Audio (I use Realtek). 
Someone told something about GNOME - alsamixer : but it just shuts down when I click "sound card properties". Also tried just downloading the driver from Realtek to LINUX but no use. 

Question is, could anyone help me getting the sound to work?

---

### Post by Jonothewright on 2009-04-22
I also just installed the 9.04 release candidate (64 bit version in my case) and am having the same problem. I have been using Ubuntu for a few years now and have never had this issue before. I hope this is solvable, I like the jackalope and would like to keep it.

Thanks
Jon

---

### Post by redenex on 2009-04-22
I wonder if the 32 bit version would help.


Just one more day for Jauty official release, if I dont get sound in that, I would rather be happy to embrace another distro altogether.

---

### Post by Pitboss on 2009-04-22
Are you sure that there's no sound, and not just that for example your default setting of master front volume is set to the lowest (cause that was my problem). Try to tweak the sound settings and maybe **System > Preferences > Sound** can help.

---

### Post by Davestom on 2009-04-24
Okay guys and girls ...
I have looked at TONS of forums and found out that: ALSA doesn't have support for REALTEK cards, like mine (onboard soundcard).. 

> First thing to do:
**aplay -l **

davestom@davestom:~$ aplay -l
aplay: device_list:217: no soundcards found...

To see if you have a soundcard .. [I]In my case none.. so I have to install one, but haven't found out how because ALSA has no drivers for me.. (I think)
[/I]
**LINK for soundcards**: [http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main) 

> Second thing to do:
**lspci**
This will check your devices, I get following under Audio Devices:

> 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

And here is where I stand still, and try to think of, what to do..

If anyone wants a good guide, here's one:
[https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems](https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems)


And if anyone could help me, it would be appreciated..
*Just want to make 1 guide, which n00bs, like myself can understand*

---

### Post by Davestom on 2009-04-24
Okay Guys and girls..

After ******* lots of hours! I freaking fixed sound and I'm hearing Daft punk - One more time!!!

listen up, short and simple: **INSTALL ALL THE DRIVERS FROM ALSA!**
**LINK:** [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.19.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.19.tar.bz2)

Unpack, and then install from source, (all written in README).

> **Edit:** if Alsa driver link is broken, you can use the following link,
[ftp://ftp.task.gda.pl/pub/linux/misc...-1.0.9.tar.bz2](ftp://ftp.task.gda.pl/pub/linux/misc...-1.0.9.tar.bz2)

(Found by imalloch) thx!

---

### Post by Ciwan21 on 2009-04-24
hi my friend, could you explain how did you install it? I download the regarding file. But there is so many sub folders in it. So which one should i go for?

Thanks

---

### Post by Vitamin-Carrot on 2009-04-24
I also have no sound however I have an audigy 2

:(

it makes me sad face

Found the fault - lolz now i need to buy me some new speakers

---

### Post by oryctes on 2009-04-25
If you have a Creative Audigy sound card, look in this thread:

[http://ubuntuforums.org/showthread.php?t=1120178&highlight=audigy](http://ubuntuforums.org/showthread.php?t=1120178&highlight=audigy)

It worked for me, and it is darn simple!

Edit:

Sorry, I didn't notice it was about Realteak cards and not Audigy ones...

---

### Post by Wistful on 2009-04-25
I have also a Realtek soundcard and no sound in Ubuntu 8.10 or 9.04.
I can't download DRIVERS FROM ALSA from the suggested ftp. Can anyone post another link?

---

### Post by imalloch on 2009-04-25
Hi

Here is another link to alsa drivers

[ftp://ftp.task.gda.pl/pub/linux/misc/alsa/driver/alsa-driver-1.0.9.tar.bz2](ftp://ftp.task.gda.pl/pub/linux/misc/alsa/driver/alsa-driver-1.0.9.tar.bz2)

---

### Post by blurt on 2009-04-25
First, I tried booting into live-cd of 9.04, could not make sound work; then
booted into live-cd of 8.10 and sound worked perfectly!.
Second, went to commandline, did "gnome-volume-control", and the box came on
with the sliders all the way up; but on the terminal line, it said:
gnome-volume-control;3679:debug:deleted custom theme dir.
Third, when downloading/installing RealPlayer11GOLD.bin using 9.04, I get
messages that thus-and-such plugin is missing, but when downloading/installing the same with 8.10, no such thing; works perfectly!
I believe this means 9.04 is broken, at least concerning sound.--blurt
](*,)](*,)](*,)](*,)

---

### Post by jamal2009 on 2009-04-25
its same here .. no sound in 9.04 and work good in ver 8 

we hop that fix it ..

---

### Post by Wistful on 2009-04-25
I have Realtek ALC889 and had issues with my sound and after trying the steps from this thread my sound is 100% working 
-> [http://ubuntuforums.org/showthread.php?p=7146245&posted=1#post7146245](http://ubuntuforums.org/showthread.php?p=7146245&posted=1#post7146245) posted by user [COLOR="Red"]gkgarg24[/COLOR]

---

### Post by Davestom on 2009-04-27
> **Ciwan21 said:**
> hi my friend, could you explain how did you install it? I download the regarding file. But there is so many sub folders in it. So which one should i go for?

Thanks

Hey Dude, there is a INSTALL file in the folder, which gives you instructions ..

---

### Post by adm1968 on 2009-04-28
> **Davestom said:**
> Okay Guys and girls..

After ******* lots of hours! I freaking fixed sound and I'm hearing Daft punk - One more time!!!

listen up, short and simple: **INSTALL ALL THE DRIVERS FROM ALSA!**
**LINK:** [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.19.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.19.tar.bz2)

Unpack, and then install from source, (all written in README).
[FONT="Georgia"]I am following your instructions for my 9.04 system, and getting a huge amount of errors (reading the "install" file)[/FONT]

---

### Post by npast on 2009-04-28
same problem here.  upgraded from 8.04. Before sound was working fine. Now, there is no sound. Checked all volumes, all set a max level.

---

### Post by adm1968 on 2009-04-29
[FONT="Georgia"]This is getting really odd
Now I am getting the welcome Ubuntu sound when opening session, and perfect audio when playing anything through Firefox (including youtube videoclips), but still no sound when using Amarok or Rhythmbox[/FONT]

---

### Post by user_linux08 on 2009-04-29
adm1968
Interesting, I have the opposite problem. Sound works everywhere, except with Flash player in Firefox.
Am I missing a driver, i am not sure. It would be nice if someone could find out  the exact cause and provide solution.

---

### Post by josepagan on 2009-04-29
> **Davestom said:**
> Hey Ubuntuforums

I'm new to Ubuntu, and just installed it today, so I'm sorry if I ask some stupid questions.
Everything worked fine and smoothly except the sound. 
In 8.10, I had no sound device installed, so I upgraded to the beta version of 9.04, and now I have a sound device, but no output in sound. I have checked a lot of guides, but they are mostly for Audigy Audio (I use Realtek). 
Someone told something about GNOME - alsamixer : but it just shuts down when I click "sound card properties". Also tried just downloading the driver from Realtek to LINUX but no use. 

Question is, could anyone help me getting the sound to work?

you have to dowmload&install "gnome alsa mixer" using synaptic package manager then check the (front) line, this solved my problem.

---

### Post by keivan on 2009-05-21
Hey Guys, I just installed ubuntu 9.04 and gotta say, it's pretty cool ! I'm a beginner with this OS. When I log in I have this drum-like sound that doesn't stop !!! It shows that it recognizes my sound card but when I play a movies I have no sound, just the drum keepis drumin :( !!!! 

Keivan

---

### Post by mlrtym00 on 2009-06-04
i am still receiving no sound either... when I run 
pkill pulseaudio; sleep 2; pulseaudio -vv

it will stop and say driver is suspended? Any help?

I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
D: main.c: Started as real root: no, suid root: yes
I: main.c: PolicyKit refuses acquire-high-priority privilege.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: main.c: Can realtime: no, can high-priority: no
D: main.c: Can realtime: no, can high-priority: no
I: main.c: This is PulseAudio 0.9.14
D: main.c: Compilation host: i486-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pedantic -pipe -Wno-long-long -Wvla -Wno-overlength-strings -Wconversion -Wundef -Wformat -Wlogical-op -Wpacked -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wdeclaration-after-statement -Wfloat-equal -Wmissing-declarations -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-noreturn -Wshadow -Wendif-labels -Wpointer-arith -Wcast-align -Wwrite-strings -Wno-unused-parameter -ffast-math
D: main.c: Running on host: Linux i686 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Optimized build: yes
I: main.c: Machine ID is 1c6bb01114a81f693fa41a9a4a27e8d0.
I: main.c: Using runtime directory /home/mlrtym/.pulse/1c6bb01114a81f693fa41a9a4a27e8d0:runtime.
I: main.c: Using state directory /home/mlrtym/.pulse.
I: main.c: Running in system mode: no
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: memblock.c: Using shared memory pool with 1024 slots of size 64.0 KiB each, total size is 64.0 MiB, maximum usable slot size is 65496
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #0; argument: "").
I: module.c: Loaded "module-suspend-on-idle" (index: #1; argument: "").
I: module-device-restore.c: Sucessfully opened database file '/home/mlrtym/.pulse/1c6bb01114a81f693fa41a9a4a27e8d0:device-volumes.i486-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-device-restore" (index: #2; argument: "").
I: module-stream-restore.c: Sucessfully opened database file '/home/mlrtym/.pulse/1c6bb01114a81f693fa41a9a4a27e8d0:stream-volumes.i486-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-stream-restore" (index: #3; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-hal-detect.so': success
I: module-hal-detect.c: Trying capability alsa
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_284b_sound_card_0_alsa_playback_1
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0 tsched=0'
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
I: module-alsa-sink.c: Successfully opened device front:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: module-device-restore.c: Restoring volume for sink alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0.
I: module-device-restore.c: Restoring mute state for sink alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0.
I: sink.c: Created sink 0 "alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-device-restore.c: Restoring volume for source alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0.monitor.
I: module-device-restore.c: Restoring mute state for source alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0.monitor.
I: source.c: Created source 0 "alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-alsa-sink.c: Using 8 fragments of size 1792 bytes, buffer time is 81.27ms
D: module-alsa-sink.c: hwbuf_unused=0
D: module-alsa-sink.c: setting avail_min=1
I: module-alsa-sink.c: Volume ranges from 0 to 127.
I: module-alsa-sink.c: Volume ranges from -95.25 dB to 0.00 dB.
I: alsa-util.c: ALSA device lacks independant volume controls for each channel.
I: module-alsa-sink.c: Using hardware volume control. Hardware dB scale supported.
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Soft volume PCM
D: alsa-util.c: Control: PCM Playback Volume
D: alsa-util.c: min_dB: -51
D: alsa-util.c: max_dB: 0
D: alsa-util.c: resolution: 256
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : PLAYBACK
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 3584
D: alsa-util.c:   period_size  : 448
D: alsa-util.c:   period_time  : 10158
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 448
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 1879048192
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 1879048192
D: alsa-util.c: Slave: Hardware PCM card 0 'HDA Intel' device 0 subdevice 0
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : PLAYBACK
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 3584
D: alsa-util.c:   period_size  : 448
D: alsa-util.c:   period_time  : 10158
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 448
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_thre
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
D: module-alsa-sink.c: Requested volume: 0: 100% 1: 100%
D: module-alsa-sink.c: Got hardware volume: 0: 100% 1: 100%
D: module-alsa-sink.c: Calculated software volume: 0: 100% 1: 100%
I: module-alsa-sink.c: Starting playback.
D: module-suspend-on-idle.c: Source alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0.monitor becomes idle.
D: module-suspend-on-idle.c: Sink alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0 becomes idle.
I: module.c: Loaded "module-alsa-sink" (index: #4; argument: "device_id=0 sink_name=alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0 tsched=0").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 source_name=alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0 tsched=0'
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: module-alsa-sink.c: Underrun!
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: module-device-restore.c: Restoring volume for source alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0.
I: module-device-restore.c: Restoring mute state for source alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0.
I: source.c: Created source 1 "alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-alsa-source.c: Using 8 fragments of size 1792 bytes, buffer time is 81.27ms
D: module-alsa-source.c: hwbuf_unused=0
D: module-alsa-source.c: setting avail_min=1
I: module-alsa-source.c: Volume ranges from 0 to 15.
I: module-alsa-source.c: Volume ranges from 0.00 dB to 22.50 dB.
I: alsa-util.c: All 2 channels can be mapped to mixer channels.
I: module-alsa-source.c: Using hardware volume control. Hardware dB scale supported.
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Soft volume PCM
D: alsa-util.c: Control: PCM Playback Volume
D: alsa-util.c: min_dB: -51
D: alsa-util.c: max_dB: 0
D: alsa-util.c: resolution: 256
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : CAPTURE
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 3584
D: alsa-util.c:   period_size  : 448
D: alsa-util.c:   period_time  : 10158
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 448
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 1879048192
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 1879048192
D: alsa-util.c: Slave: Hardware PCM card 0 'HDA Intel' device 0 subdevice 0
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : CAPTURE
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 3584
D: alsa-util.c:   period_size  : 448
D: alsa-util.c:   period_time  : 10158
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 448
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_thresh
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
D: module-alsa-source.c: Requested volume: 0:  62% 1:  62%
D: module-alsa-source.c: Got hardware volume: 0:  62% 1:  62%
D: module-alsa-source.c: Calculated software volume: 0: 100% 1: 100%
D: module-suspend-on-idle.c: Source alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0 becomes idle.
I: module.c: Loaded "module-alsa-source" (index: #5; argument: "device_id=0 source_name=alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0 tsched=0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_284b_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 2 modules.
I: module.c: Loaded "module-hal-detect" (index: #6; argument: "tsched=0").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #7; argument: "").
I: module.c: Loaded "module-native-protocol-unix" (index: #8; argument: "").
I: module-default-device-restore.c: Restored default sink 'alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0'.
D: core-subscribe.c: Dropped redundant event due to change event.
I: module-default-device-restore.c: Restored default source 'alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0'.
I: module.c: Loaded "module-default-device-restore" (index: #9; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #10; argument: "").
I: module.c: Loaded "module-always-sink" (index: #11; argument: "").
I: client.c: Created 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session1"
D: module-console-kit.c: Added new session /org/freedesktop/ConsoleKit/Session1
I: module.c: Loaded "module-console-kit" (index: #12; argument: "").
I: module.c: Loaded "module-position-event-sounds" (index: #13; argument: "").
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
D: module-console-kit.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module-suspend-on-idle.c: Sink alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Source alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...

---

### Post by penguinehax on 2009-06-04
I found a site that has a perfect fix, I just tried it and it works great for me
[http://moderngeek.com/node/10](http://moderngeek.com/node/10)

---

### Post by blurt on 2009-06-04
I said this before, and I'll say it again; after all the checks for volume
control settings and downloading drivers that have no sensible instructions
for their use, and all the rest of it, the sound in the 9.04 DOESN'T WORK.
Think; you see all these posts from people describing this or that solution,
and it works for this guy but not that guy; this is proof positive that the
sound in 9.04 is *platform dependant*!!!! Now maybe I'm becoming obsolete,
but since when does an elementary function like basic sound depend on the
freaking CARD that you have? The last two or three ubuntu's had no such problem; you install the os on it, and(the sound) is ready to rock and roll. It
was certainly so in windoze!. The point is, a *proper* sound software system in the os, if it requires drivers to work, especially on the old,
mundane cards that MOST computers have, *should be included* in the distro,
or at least, should have been sent as 'updates', if maybe there was not
room on the installation image. As of now, the sound in 9.04 is BROKEN,
and from what I can see, canonical is either unaware, or is in denial;
it's almost as if MICROSOFT has an agent in place at canonical?--blurt.

---

### Post by markbuntu on 2009-06-05
First of all, ubuntu is dependent on the ALSA developers for sound drivers which are included in the distribution. Since many hardware manufacturers do not provide the specifications for how they tweaked the firmware of the sound chips they use it is difficult to make the hardware driver perform properly and making changes to the driver for one chip can break it for another. 

Since it is basically impossible to test every change to the driver on every conceivable piece of hardware the driver writers test as much as they can and release it. Since these people may not have your specific hardware to test, it is possible that something they did to fix another problem affects your hardware in a negative mannner. The only way they will know this is if someone files a bug report.

Reported bugs get fixed as soon as possible. If manufacturers withold information this can become a long drawn out process. It took years to reverse engineer the creative soundblaster cards but it was done.

microserf can force the hardware manufacturers to make windoze drivers. The linux community does not have that kind of leverage. So, if you have a particular piece of hardware that does not work with your linux system then you really need to aim your complaint at the manufacturer to encourage them to release the specs to the open source community so proper drivers can be written.

More people use linux than macs these days but sales figures do not show this since the vast majority of linux installs replace the OS the machine was sold with. The manufacturers need to be made aware of this and the only way they will be is if you tell them.

---

### Post by blurt on 2009-06-05
Call me stupid, but I simply can't believe that the inclusion of newer sound
cards could "back-disengineer" the older cards, which work so well with
8.04 and 8.10, either installed or live-cd; but the 9.04 won't work in either mode. For now, I went back to the 8.10, until I see that the problem 
with 9.04 is fixed.--blurt.

---

### Post by Tapas Bose, India on 2009-07-30
Okay.. Here is a quick installation of ALSA :

_Step -1 :_ Open terminal, then type

sudo apt-get install xmlto

Note : "xmlto" is needed for making alsa-utils.

_Step -2 :_ Open terminal, then type

sudo -i

give your user password, you don't see nothing when type it, then press enter. Then type the following commands one by one and press enter after each command.

apt-get update

apt-get install wget build-essential ncurses-dev libncurses5-dev gettext linux-headers-$(uname -r)

mkdir /usr/src/alsa-source

cd /usr/src/alsa-source

wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.19.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.19.tar.bz2)

wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.19.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.19.tar.bz2)

wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.19.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.19.tar.bz2)

tar xjf alsa-driver-1.0.19.tar.bz2

tar xjf alsa-lib-1.0.19.tar.bz2

tar xjf alsa-utils-1.0.19.tar.bz2

cd alsa-driver-1.0.19

./configure --with-cards=hda-intel


 make

make install


_Step -3 :_ Open another terminal, then type


sudo -i

 give your user password, you don't see nothing when type it, then press enter. Then type the following commands one by one and press enter after each command.

cd alsa-lib-1.0.19

./configure

make

make install

_Step -4 :_ Open another terminal, then type
 

 sudo -i
 
give your user password, you don't see nothing when type it, then press enter. Then type the following commands one by one and press enter after each command.

cd alsa-utils-1.0.19

./configure

make

make install

_Step -5 :_ Then if you need special options open the file
 nano /etc/modprobe.d/alsa-base
 and change the model options for example (find it on reference pages below):
options snd-hda-intel model=acer
 Reboot your pc
 ------------------------
More reference at page:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
 and the homepage of alsa
[http://www.alsa-project.org/](http://www.alsa-project.org/)

---

### Post by malici606 on 2009-08-01
Okay, im a complete nube, and i suck with this OS, hell grub gives me a headache. with that said i rely a lot on this forum to keep ubuntu  working, so im kinda happy i might be able to help someone with this sound prob. my mobo is a 780i from evga and i als have a sound card, now i have done everything these forums have suggested to get sound and nothing, then i just thought, maybe i should unplug my sound card and plug in my mobo sound, and it worked. no code, no sudu, just a stupid wire... who knows maybe this might help someone

---

### Post by Beans Macfru on 2009-08-02
Ok, bet I can win the 'most clueless' newbie ever! I was living with Vista, which got totally hosed thanks to Win32/Crypto. I work with a flavor or two of Unix, but in pretty limited ways, i.e. mainframes, remote access to tcom equipment for repair and maintenance. So, the whiz kid in IP Core, whom I've adopted, came over and set up Ubuntu as a dual boot. I've managed to get online, obviously, but [SIZE=4]I can't figure out how to get to command line...seriously!! And my realtek hd sound doesn't work[/SIZE]. I do have a 'Ubuntu for idiots' ordered, but I really miss my avi files. *Whiz kid also says I already have a bit torrent client, but isohunt denies that...

anyone wanna take on walking me through ANY of this??    :confused:

---

### Post by markbuntu on 2009-08-03
In the menu

Applications/Accessories/Terminal

the line you type on is the command line.

Applications/Internet/Transmission BitTorrent Client

This is your bit torrent application.

The Absolute Beginners section here has links to some good tutorials for noobs, you should read them.

---

### Post by taha116 on 2009-08-08
> **penguinehax said:**
> I found a site that has a perfect fix, I just tried it and it works great for me
[http://moderngeek.com/node/10](http://moderngeek.com/node/10)

This dosent seem to have changed a thing, its only added some stuff that made no diff... no sound working. I now need help really badly!

Please help me get sound it was working fine untill today when i had like 2 updates and did them and then 2 more came and i did them from update manager... then i went to youtube and im getting no sound... same goes for the login sounds... whats up? please help! and note that i already tried the stuff in the qoute i made above.

---

### Post by P_Bang on 2009-08-11
I should download GNOME Alsa Mixer then launch to it. In "External Amplifier" option, you must not select it.

It be work for me!!!

---

### Post by roh8880 on 2009-09-04
> **P_Bang said:**
> I should download GNOME Alsa Mixer then launch to it. In "External Amplifier" option, you must not select it.

It be work for me!!!

Gnome ALSA Mixer worked for me. The master f is at the minimum by default on 9.04. Simple fix! Thanxs again guys!!

---

### Post by lavs on 2009-09-07
I had the same problem ...actually 9.04 comes with pulse audio as the basic but it doesnt support some older driver like mine(I had ac'97) so just install the alsamixer and uninstall pulseaudio. 

Did the job for me .. hope it works for u too

---

### Post by jim_naisium on 2009-09-22
In case this helps anyone else I have a brand new Intel DP45SG motherboard with on board sound that I just installed Ubuntu 9.04 on, all I could get out of the speakers was a little tiny bit of crackling that would start when I hit PLAY and stop when I hit STOP so I knew that it was at least trying.

I too had to install the "Gnome Alsa Mixer" through the /System/Administration/Synaptic Package Manager/ and found that the PCM slider was turned all the way down, after I slid it up I had sound.

If any of the Ubuntu Developers are reading this please include the "Gnome Alsa Mixer" as a default program that gets installed in the next Ubuntu release.

---

### Post by nagender on 2009-09-26
Hii...I am new ubuntu. I have installed ubuntu 9.04 on compaq presario cq45-207tu. Everything is working fine except for speakers. There is no sound from speakers at all. I also have windows vista in which speakers work just fine. I have tried installing alsa drivers and oss drivers...but no result. can anyone help??

---

### Post by jim_naisium on 2009-09-26
Please try what I said in my posting that is right above yours (posting # 35).

---

### Post by nagender on 2009-09-27
Gnome alsa mixer is already installed...

---

### Post by rinyotsu on 2010-02-23
I'm not sure if anyone has found it yet (I'm sure they have but its 3am and just incase), but I've done about all you can with pulseaudio and still nothing. I right-clicked the sound by the date on the menu bar, click "open volume control" and see if the "speaker" bars are at the bottom. I moved them to the top and boom, my sound works again. Hope that helps.

---

