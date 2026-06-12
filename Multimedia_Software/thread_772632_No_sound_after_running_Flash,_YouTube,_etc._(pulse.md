---
title: "No sound after running Flash, YouTube, etc. (pulseaudio solution)"
date: 2008-04-28
forum: Multimedia Software
---

### Post by Vegetarianrage on 2008-04-28
If anyone with any experience can something in this post feel free to pm me.

As I understand it, Pulseaudio is a "soundserver" which is simply to say that it takes the input from your apps and manages/mixes them to send it all as a single stream to the soundcard.

After running flash audio in firefox, (youtube, for example) my sound would no longer work for anything but other flash audio. Trying to play audio files in totem or any other player would hang at 0 seconds.
A very help user in #alsa on chat.freenode.net walked me through this solution last night and the end result was that my sound worked with flash and other programs, even simultaneously. 

Here is EVERYTHING that we did:

<hypercool^> my sound seems to work fine, then i load a webpage with flash in it, which also works fine. But afterwards, only flash sounds will work. normal sounds will not play
<wishie> hypercool^: flash has a way of not using 'dmix' on some systems.. which means it hogs the soundcard.
<wishie> hypercool^: is pulseaudio working ?
<wishie> pulseaudio is a 'soundserver'
<wishie> basically, apps send sound to it, and it mixes the sounds together, and outputs to the sound card.
<hypercool^> i checked synaptic and it is installed for sure.
<hypercool^> i had sound before i tried to use flash
<hypercool^> so i assume it works? or it did?
<wishie> well, make sure its running.. ```
ps aux |grep pulse
```
<hypercool^> 
```

john@eleanor:/etc/init.d$ ps aux |grep pulse
john      5866  0.0  0.2  28628  6004 ?        Sl   Apr27   0:00 /usr/bin/pulseaudio --log-target=syslog
john      5872  0.0  0.1   5776  2248 ?        S    Apr27   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
john      7721  0.0  0.0   3008   772 pts/0    R+   00:22   0:00 grep pulse

```
<wishie> hypercool^: so, its running.. now we want to know if its being used..heh
<wishie> hypercool^: is libflashsupport installed
```
sudo apt-cache policy libflashsupport
```
<hypercool^> ok
<hypercool^> "installed: none"
<hypercool^> i'm a little confused, what does libflashsupport do if i already have working flash?
<wishie> tells flash to use pulseaudio, among other things
<wishie> was there a 'candidate' ?
<hypercool^> yes 1.9-0ubuntu1
<wishie> install that
```
sudo apt-get install libflashsupport
```
<hypercool^> wishie, ok installed it
<wishie> unfortunately, im not too familiar with the ubuntu 8.04 default install..
<wishie> hypercool^: check if padevchooser and paman are installed
```
apt-cache policy padevchooser
apt-cache policy paman
```
<hypercool^> no, neither of them are installed
<hypercool^> but there is a candidate for each one? should i repeat what we did for libflashsupport?
<wishie> ok, install padevchooser and paman
```
sudo apt-get install padevchooser paman
```
<hypercool^> ok
<wishie> that way, we can monitor if flash uses pulseaudio
<hypercool^> thanks for explaining :) i hate following blind instructions
<hypercool^> installing...
<hypercool^> done
<wishie> hypercool^: ok, run (i think, from memory) its padevchooser
```
padevchooser
```
<wishie> is there an icon in the gnome bar now ?
<hypercool^> wishie, lol yes good call
<wishie> hypercool^: what options does it give (been a while since i used it.. brb
<hypercool^> manager, volume control, volume meter (playback), volume meter (recording), configure local sound server
<wishie> manager
<wishie> thats the one you want to run

Note: You can run the manager by clicking the pulse audio icon in the gnome bar and clicking "manager" or by running ```
paman
``` in a terminal.

<hypercool^> lol
<hypercool^> ok
<wishie> run that, click on the clients tab
<wishie> run a flash video, and see if it shows up as a client.
<hypercool^> yes just showed up
<hypercool^> oh well this interesting, it shows up but the flash video won't play lol
<hypercool^> ok it's working
<hypercool^> it's in the client list
<hypercool^> wishie, "Adobe Flash" showed up in the client list
<wishie> configure your other apps to use pulseaudio now..
<wishie> create the file ~/.asoundrc
```
sudo nano ~/.asoundrc
```
<wishie> and put the following in it.
```
pcm.!default {
type pulse
}
ctl.!default {
type pulse
}
```
<hypercool^> ok done
<wishie> test flash with other programs now
<hypercool^> testing...
<wishie> each program you open, should show up in "clients" tab of paman
<wishie> they should all play nicely now
<hypercool^> :) hopefully
<wishie> are other sound apps showing up in 'clients' as you use them ?
<hypercool^> yes.....
<hypercool^> you're a genius thank you
<wishie> heh
<wishie> now
<hypercool^> everything seems to working
<wishie> you might want..
<wishie> pavucontrol, pavumeter 
<wishie> each program now has its own seperate volume control aswell
<wishie> and you can monitor it all, etc.
<hypercool^> niceeeeee
<wishie> all accessible from 'padevchooser' (which is the tray icon)
<wishie> why ubuntu doesnt have it like this in the first place, is beyond me.
<hypercool^> yeah i don't know
<hypercool^> even vista has process specific volume control
<wishie> well, you can even move streams to different cards with PA
<wishie> if you have several cards, you can move different sound streams to different cards, mid stream... on the fly
<hypercool^> niice
<hypercool^> well that's coming
<hypercool^> but i'n not there just yet
<wishie> well, i gotta run now
<wishie> bread to bake
* wishie is now known as wishie[work]
<hypercool^> THANK YOU!
<wishie[work]> no worries
<wishie[work]> you're welcome

---

### Post by fizikz on 2008-05-20
Thanks! I was having the same issue and getting libflashsupport, padevchooser, and pamon seem to have solved the problem. The only difference is that I had to restart X after having installed these to start seeing the 'Adobe Flash' entry in the clients tab (as described in the above post), and I didn't make the .asoundrc file.

---

### Post by thorgal on 2008-05-20
the .asoundrc is for apps that still use the ALSA layer because they have not been programmed with direct PA instructions. So PA provided an alsa plugin to fool these apps. Same with a jack plugin to be able to run with jack. When PA is properly configured, it is very flexible. You can net-stream to your LAN through PA as well. Just run the PA daemon in all your running boxes and each one of them can become a sink and a source for the others.

---

### Post by fizikz on 2008-05-21
A while after having 'fixed' the problem as I described above, at some point Youtube stopped working. I read in some places that Pulse may have some problems with Flash, and although I don't know what they are, I'm guessing I ran into this. When I tried to open Pulse Audio Manager, it said 'could not connect to sound server' and showed no other information. I have since added the .asoundrc file as described in the first post and restarted X. So far it's working...

The problem that often comes up goes something like "Pulse: Connection to sound server failed. Connection refused." I sometimes see this output in the terminal when playing an audio file with mplayer. At times it will also include a similar error about ALSA. The last time this happened it seemed to be using OSS to play after having failed to use Pulse or ALSA. However, usually it is only the Pulse error message that shows up, if any. These problems get me a bit homesick for my good old Dapper.

One thing that comes to mind is that in Dapper I had downloaded the tarball for Flash from Adobe's site and installed it in the usual way compared to now with Hardy where I've only installed flashplugin-nonfree via Synaptic Package manager. It sounds like it's the same thing, but I never know just what the package manager actually does.

---

### Post by thorgal on 2008-05-21
> **fizikz said:**
> 
One thing that comes to mind is that in Dapper I had downloaded the tarball for Flash from Adobe's site and installed it in the usual way compared to now with Hardy where I've only installed flashplugin-nonfree via Synaptic Package manager. It sounds like it's the same thing, but I never know just what the package manager actually does.

it is the same thing. The ubuntu package is simply a wrapper that downloads the flash plugin for you so you do not have to manually download it yourself from the website. The plugin itself cannot be part of the ubuntu package.

---

### Post by fizikz on 2008-05-27
After having added .asoundrc, I've noticed that some programs previously had no sound problems (aMSN, several games) now don't have sound anymore. If I remove .asoundrc, they work again. Is there a way to reconcile this?

---

### Post by Vegetarianrage on 2008-07-09
> **fizikz said:**
> After having added .asoundrc, I've noticed that some programs previously had no sound problems (aMSN, several games) now don't have sound anymore. If I remove .asoundrc, they work again. Is there a way to reconcile this?

You may have to go into the sound settings of these applications and change the device that they are using. If they were previously trying to access the device directly and now pulse has it all the time, they will not be able to play sound. Tell the programs to route their sound output to the pulsemixer. I had to to do this for one or two things but all of my programs work now with sound simultaneously, including flash and skype. Hope this helps.

---

### Post by culturepunk on 2008-08-20
:) Thanks alot for this, I was having the same problem! Sorted it now.

---

### Post by ivodalves on 2008-08-21
Hello,

I've also sound problems in my Laptop.

More strange is. I can hear sound in my headphone output but not in my speakers.

Can someone help?

Thanks

---

### Post by banzairx7 on 2008-08-21
Thank You! Im a complete ubuntu nube and was having this problem for weeks. This so far has 100% solved it.

Only hang up I ran into, because I have no idea what Im doing, was creating asoundrc file. After I entered the text in the editor I had to figure out how to save it. I figured out I had to hit ctrl+X and then answer "Y"

again thank you!

---

### Post by nawazpatel on 2008-08-29
Thank you for sharing this information.

---

### Post by PPPP on 2009-05-12
```
sudo apt-get install flashplugin-nonfree-extrasound
```

This fixed it for me on Jackalope.  Thanks all!

---

### Post by psyke83 on 2009-05-12
> **PPPP said:**
> ```
sudo apt-get install flashplugin-nonfree-extrasound
```

This fixed it for me on Jackalope.  Thanks all!

This is not a good solution. You're going to start noticing one of two symptoms.

If you're using the 32bit release, Firefox will crash when switching between pages with Flash content (e.g. Youtube).

If you're using the 64bit release, Flash will spontaneously crash in Firefox, leaving a grey window in the space that the Flash content previously occupied.

The flashplugin-nonfree-extrasound is merely a rename of the libflashsupport library, and libflashsupport is the source instability in Flash. 

The libflashsupport library is no longer necessary. Please, remove this package and refer to [bug #192888]("https://bugs.launchpad.net/bugs/192888") for more details. Too many users are installing this library and then experiencing instability in their Firefox sessions - this needs to end.

If you're using **U**buntu (from Hardy onwards), you simply need to ensure PulseAudio is configured correctly, and your Flash issues (and more) will be resolved. See my PulseAudio guide for details.

---

### Post by PPPP on 2009-05-12
Thanks psyke for the info.  I was actually following your guide but I got stuck @ Part A step 5.  I got  "Connection failed: Connection refused" and ran the command:

```
$ pulseaudio & pavucontrol
```

But was greeted by the following error:

```
pavucontrol:10078): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
E: alsa-util.c: Error opening PCM device hw:0: Device or resource busy
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_10de_59_sound_card_0_alsa_playback_0 tsched=0"): initialization failed.
W: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
E: socket-server.c: bind(): Address already in use
E: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.

```

Did some google search but not sure how to fix it...saw some mention of MPD?  Disabling it or uninstalling it should fix it?  I'm not sure what that means...

---

### Post by psyke83 on 2009-05-12
> **PPPP said:**
> Thanks psyke for the info.  I was actually following your guide but I got stuck @ Part A step 5.  I got  "Connection failed: Connection refused" and ran the command:

```
$ pulseaudio & pavucontrol
```

But was greeted by the following error:

```
pavucontrol:10078): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
E: alsa-util.c: Error opening PCM device hw:0: Device or resource busy
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_10de_59_sound_card_0_alsa_playback_0 tsched=0"): initialization failed.
W: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
E: socket-server.c: bind(): Address already in use
E: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.

```

Did some google search but not sure how to fix it...saw some mention of MPD?  Disabling it or uninstalling it should fix it?  I'm not sure what that means...

The first error in your output suggests that another application has "locked" your sound card. There can be no other applications trying to access the sound card when you launch PulseAudio.

The Music Player Daemon (MPD) is one such application that can potentially interfere in this way (as it runs as a daemon in the background and keeps the sound card locked). MPD is a common culprit, but it's not necessarily the cause on your system.

---

### Post by PPPP on 2009-05-13
> **psyke83 said:**
> The first error in your output suggests that another application has "locked" your sound card. There can be no other applications trying to access the sound card when you launch PulseAudio.

The Music Player Daemon (MPD) is one such application that can potentially interfere in this way (as it runs as a daemon in the background and keeps the sound card locked). MPD is a common culprit, but it's not necessarily the cause on your system.

So how do I hunt down which process is using the sound card?

---

### Post by PPPP on 2009-05-13
Btw, I'm on Ubuntu Jackalope i686

```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```

$ pkill pulseaudio; sleep 2; pulseaudio -vvI: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
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
I: main.c: Machine ID is 0297676a9644a7f896a84c0046d96584.
I: main.c: Using runtime directory /home/plui/.pulse/0297676a9644a7f896a84c0046d96584:runtime.
I: main.c: Using state directory /home/plui/.pulse.
I: main.c: Running in system mode: no
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: memblock.c: Using shared memory pool with 1024 slots of size 64.0 KiB each, total size is 64.0 MiB, maximum usable slot size is 65496
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #0; argument: "").
I: module.c: Loaded "module-suspend-on-idle" (index: #1; argument: "").
I: module-device-restore.c: Sucessfully opened database file '/home/plui/.pulse/0297676a9644a7f896a84c0046d96584:device-volumes.i486-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-device-restore" (index: #2; argument: "").
I: module-stream-restore.c: Sucessfully opened database file '/home/plui/.pulse/0297676a9644a7f896a84c0046d96584:stream-volumes.i486-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-stream-restore" (index: #3; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-hal-detect.so': success
I: module-hal-detect.c: Trying capability alsa
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10de_59_sound_card_0_alsa_playback_2
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10de_59_sound_card_0_alsa_capture_1
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_10de_59_sound_card_0_alsa_playback_0 tsched=0'
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
W: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
I: module-alsa-sink.c: Successfully opened device front:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: module-device-restore.c: Restoring volume for sink alsa_output.pci_10de_59_sound_card_0_alsa_playback_0.
I: module-device-restore.c: Restoring mute state for sink alsa_output.pci_10de_59_sound_card_0_alsa_playback_0.
I: sink.c: Created sink 0 "alsa_output.pci_10de_59_sound_card_0_alsa_playback_0" with sample spec s16le 2ch 48000Hz and channel map front-left,front-right
I: module-device-restore.c: Restoring volume for source alsa_output.pci_10de_59_sound_card_0_alsa_playback_0.monitor.
I: module-device-restore.c: Restoring mute state for source alsa_output.pci_10de_59_sound_card_0_alsa_playback_0.monitor.
I: source.c: Created source 0 "alsa_output.pci_10de_59_sound_card_0_alsa_playback_0.monitor" with sample spec s16le 2ch 48000Hz and channel map front-left,front-right
I: module-alsa-sink.c: Using 8 fragments of size 1920 bytes, buffer time is 80.00ms
D: module-alsa-sink.c: hwbuf_unused=0
D: module-alsa-sink.c: setting avail_min=1
I: module-alsa-sink.c: Volume ranges from 0 to 31.
I: module-alsa-sink.c: Volume ranges from -46.50 dB to 0.00 dB.
I: alsa-util.c: All 2 channels can be mapped to mixer channels.
I: module-alsa-sink.c: Using hardware volume control. Hardware dB scale supported.
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Hardware PCM card 0 'NVidia CK804' device 0 subdevice 0
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : PLAYBACK
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 48000
D: alsa-util.c:   exact rate   : 48000 (48000/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 3840
D: alsa-util.c:   period_size  : 480
D: alsa-util.c:   period_time  : 10000
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 480
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 2013265920
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 2013265920
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
D: module-alsa-sink.c: Requested volume: 0: 100% 1: 100%
D: module-alsa-sink.c: Got hardware volume: 0: 100% 1: 100%
D: module-alsa-sink.c: Calculated software volume: 0: 100% 1: 100%
I: module-alsa-sink.c: Starting playback.
D: module-suspend-on-idle.c: Source alsa_output.pci_10de_59_sound_card_0_alsa_playback_0.monitor becomes idle.
D: module-suspend-on-idle.c: Sink alsa_output.pci_10de_59_sound_card_0_alsa_playback_0 becomes idle.
I: module.c: Loaded "module-alsa-sink" (index: #4; argument: "device_id=0 sink_name=alsa_output.pci_10de_59_sound_card_0_alsa_playback_0 tsched=0").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 source_name=alsa_input.pci_10de_59_sound_card_0_alsa_capture_0 tsched=0'
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
W: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: module-device-restore.c: Restoring volume for source alsa_input.pci_10de_59_sound_card_0_alsa_capture_0.
I: module-device-restore.c: Restoring mute state for source alsa_input.pci_10de_59_sound_card_0_alsa_capture_0.
I: source.c: Created source 1 "alsa_input.pci_10de_59_sound_card_0_alsa_capture_0" with sample spec s16le 2ch 48000Hz and channel map front-left,front-right
I: module-alsa-source.c: Using 8 fragments of size 1920 bytes, buffer time is 80.00ms
D: module-alsa-source.c: hwbuf_unused=0
D: module-alsa-source.c: setting avail_min=1
I: module-alsa-source.c: Volume ranges from 0 to 15.
I: module-alsa-source.c: Volume ranges from 0.00 dB to 22.50 dB.
I: alsa-util.c: All 2 channels can be mapped to mixer channels.
I: module-alsa-source.c: Using hardware volume control. Hardware dB scale supported.
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Hardware PCM card 0 'NVidia CK804' device 0 subdevice 0
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : CAPTURE
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 48000
D: alsa-util.c:   exact rate   : 48000 (48000/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 3840
D: alsa-util.c:   period_size  : 480
D: alsa-util.c:   period_time  : 10000
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 480
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 2013265920
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 2013265920
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
D: module-alsa-source.c: Requested volume: 0:  62% 1:  62%
D: module-alsa-source.c: Got hardware volume: 0:  62% 1:  62%
D: module-alsa-source.c: Calculated software volume: 0: 100% 1: 100%
D: module-suspend-on-idle.c: Source alsa_input.pci_10de_59_sound_card_0_alsa_capture_0 becomes idle.
I: module.c: Loaded "module-alsa-source" (index: #5; argument: "device_id=0 source_name=alsa_input.pci_10de_59_sound_card_0_alsa_capture_0 tsched=0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10de_59_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 2 modules.
I: module.c: Loaded "module-hal-detect" (index: #6; argument: "tsched=0").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #7; argument: "").
I: module.c: Loaded "module-native-protocol-unix" (index: #8; argument: "").
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
I: module-suspend-on-idle.c: Sink alsa_output.pci_10de_59_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.pci_10de_59_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Source alsa_input.pci_10de_59_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...

```

---

