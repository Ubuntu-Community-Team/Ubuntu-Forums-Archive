---
title: "Howto: Route all sound to Jack via Pulse Audio in Feisty (finally EQ in all audio!)"
date: 2007-09-11
forum: Multimedia &amp; Video
---

### Post by hotspoons on 2007-09-11
I have always wanted to run all of my audio apps through Jack to take advantage of the ability to process audio using LADSPA plugins, and the fact that my favorite audio application (Banshee) doesn't have equalization or sound dynamics as part of the package left me looking. And looking. And this is what I figured out. The first thing you need to do is get some dependencies taken care of. You will need pulseaudio-module-jack (not in Feisty reps, but the same version as the rest of pulse is in Debian etch. Download here: [pulseaudio-module-jack]("http://packages.debian.org/etch/pulseaudio-module-jack")).

You will also need jack_transport. You can either build this from source (for what ever reason, even though I had the readline dependency met for development files, it would never compile), or grab it from an old version of Jack (this does not come with jack for Ubuntu). I got an old RPM containing it here: [jack examples]("http://fr2.rpmfind.net//linux/RPM/PLD/dists/ac/ready/i586/jack-audio-connection-kit-example-clients-0.99.0-3.i586.html"). Those are the two files you need not included with Ubuntu, but don't do anything with them just yet.

First, install pulse audio and jack, and other dependencies:

```

sudo apt-get install jackd jack-rack jack-tools pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-lirc pulseaudio-module-x11 pulseaudio-module-zeroconf pulseaudio-utils padevchooser paman paprefs pavucontrol pavumeter libreadline5

```

Don't worry about ESD being removed. Pulse is a dropin replacement for it. Now you can get some plugins. The easiest way (and it gets you the most) is to install ubuntu Studio Plugins:

```

sudo apt-get install ubuntustudio-audio-plugins

```

Now install the pulseaudio-module-jack file:
```

cd /to/where/you/downloaded/it
sudo dpkg -i pulseaudio-module-jack_0.9.5-5_i386.deb

```

Now extract the RPM file (somewhere in your home directory! Do not alien it, or install it. You just need one file). You should be able to right click and extract it, or use another tool. 

Cd to the usr/bin folder from the extracted RPM, and copy jack_transport to /usr/bin:
```

cd /path/to/where/you/extracted/it
sudo cp jack_transport /usr/bin

```

You also have to link a library that SUSE adds a .0 to the end of, so do this:
```

sudo ln -s /usr/lib/libjack.so  /usr/lib/libjack.so.0

```

Now all of the ground work is in place, begin configuration.
```

sudo nano /etc/security/limits.conf

```

Add these lines at the bottom of the file (these take care of conflicts between Jack and Pulse)
```

###
@audio - rtprio 100
@audio - nice -20
@audio - memlock 452192
###

```

Save, log out, and log back in.

Remove the SUID bit from pulse audio:
```

sudo chmod -s /usr/bin/pulseaudio

```

Copy the default pulse audio config to your home directory:
```

cp /etc/pulse/default.pa ~/jackd.pa

```

And edit ~/jackd.pa to look something like this (this is mine, and it works perfectly, though I probably don't need all of the modules installed). The main thing is to  remove any module-hal-detect, module-detect, module-alsa-* and module-oss-* lines as these will not be used (Jack is handling ins and outs).

```

#!/usr/bin/pulseaudio -nF 

###
load-module module-jack-sink
load-module module-jack-source
###
#add-autoload-sink output module-jack-sink channels=2
#add-autoload-source input module-jack-source channels=2
#load-module module-esound-protocol-unix
load-module module-native-protocol-unix
load-module module-volume-restore
load-module module-rescue-streams
.nofail

load-module module-x11-publish
load-module module-gconf

```

Save that. Now to handle Jack. Here's a script I found, adjusted, and added to. You will have to adjust for any paths or file names that are different, and be sure to save your jack-rack configuration file to where you say it is in the script. But this script as a startup item in Gnome (as well as disabling ESD software mixing in sound preferences...this is important) will automate this whole thing. You can even use alltray on jack-rack if you don't want it popping up every time. And here it is:

```

#!/bin/sh

jackd -R -d alsa &
sleep 2
echo "play" | jack_transport &
pulseaudio -n -F /home/rich/jackd.pa &
# specify your default plugin setup here
RACKFILE=/home/rich/rich.rack

# start JACK Rack
jack-rack -n $RACKFILE &

# wait for JACK Rack to register with JACK
sleep 3 

# connect
jack_connect PulseAudio:front-left jack_rack:in_1
jack_connect PulseAudio:front-right jack_rack:in_2
for ch in 1 2; do
    # rack -> speakers
    jack_connect jack_rack:out_$ch alsa_pcm:playback_$ch
done

```

Save that, 'chmod +x' the file, and that should do it for you! Now you just need to perform a bit of configuration to Gnome. Open sound preferences (system->preferences->sound), change everything you can on the devices page to "PulseAudio Sound Server", uncheck "enable software sound mixing (ESD)" on the sounds tab, and close. Kill any running instance of Pulse Audio ('killall pulseaudio' from a terminal), run the script, and hope it works!. And of course you can do much more complicated set ups (like passing 10 channels to Jack if your card supports it, and processing them all), but that should get you started.

CJ van den Berg graciously pointed me to a tutorial he wrote on the subject found [here ]("https://tango.0pointer.de/pipermail/pulseaudio-discuss/2007-March/000330.html"), but it was missing some detail (mainly where to find jack_transport or how to get it to compile) so I built on it.

---

### Post by hotspoons on 2007-09-11
Whoops. That broke firefox and flash sound. Well, here's a fix. Edit firefoxrc:

```
 
sudo nano /etc/firefox/firefoxrc 

```

Change the only uncommented line to read as follows:
```

FIREFOX_DSP="padsp"

```

To fix flash, you need lib flash support. Instructions are here: [http://pulseaudio.revolutionlinux.com/PulseAudio]("http://pulseaudio.revolutionlinux.com/PulseAudio"), but here is the quick and dirty.

```

sudo apt-get install subversion libpulse-dev

svn co https://svn.revolutionlinux.com/MILLE/XTERM/trunk/libflashsupport/src/
cd src
make
sudo make install

```

Restart firefox and you should be good to go!

---

### Post by hotspoons on 2007-09-11
I found out that the latest pulse audio 0.9.6-2 (not in Feisty or Gutsy yet, but in debian unstable) doesn't require the jack_transport step as it automatically starts the transport upon connecting to Jack, so that saves a lot of hassle.

---

### Post by triptoe on 2007-09-14
will this benefit gaming at all? or is it only for musical stuff?

---

### Post by hotspoons on 2007-09-20
> **triptoe said:**
> will this benefit gaming at all? or is it only for musical stuff?

It is mostly for music, but any game that uses GStreamer for sound and is Gnome-aware should work. There are other ways to do this (OSS2JACK) that will work with any sound, but they are much more involved and require custom kernel modules. I found the jackaudiosink plugin for GStreamer is a more direct solution, not requiring pulse audio, and having everything you need to make it work available in official Feisty repositories.

---

### Post by k-o-x on 2007-12-16
Hello and thanks for this how-to.

This mostly works but still I have a little problem. In gnome sound preferences, there's no entry for PulseAudio in the device selection menus. I cannot figure out how to solve that, anybody has an idea ?

The good news is, thanks to this howto I managed to do the main thing I have wanted for months, which is routing audio from flash (i.e. youtube etc) to Jack :)

---

### Post by motin on 2008-01-02
Wow this is very exciting, as it could be the start to be able to use JACK ona fulltime basis! Probably soon can start JACK on startup and never again have to work through many hassles just to get my keyboard to produce some sound, while at the same time being able to watch videos on the net etc!

I have two questions however - before I accidentally ruin my sound output overall:

1. Has anyone tried this on Gutsy yet and confirmed it works there as well? Does all steps need to be done?
2. Any good tips for howto make this process run on startup - maybe even before the gnome login screen shows up? That would be the ultimate JACK sound experience - probably even something for Ubuntu Studio 8.04 to want to include by default...

---

### Post by k-o-x on 2008-01-12
> **k-o-x said:**
> This mostly works but still I have a little problem. In gnome sound preferences, there's no entry for PulseAudio in the device selection menus. I cannot figure out how to solve that, anybody has an idea ?
Oh, I found what was missing: the libgstreamer-plugins-pulse0.10-0 package :)

---

### Post by k-o-x on 2008-01-12
> **motin said:**
> 1. Has anyone tried this on Gutsy yet and confirmed it works there as well? Does all steps need to be done?
2. Any good tips for howto make this process run on startup - maybe even before the gnome login screen shows up? That would be the ultimate JACK sound experience - probably even something for Ubuntu Studio 8.04 to want to include by default...
1. Yes ! I did it. All steps must be performed (you have to read the whole topic however), except for me the jack_connect script lines (pulseaudio seems to connect automatically to system in/outputs).
2. That's not very difficult, I did it based on a little init script and some pam configuration (to have realtime priority before gdm starts), I don't have quite the time right now but I'll explain it eventually (don't hesitate to PM me if I forget !)

---

### Post by rgeddes on 2008-01-17
I tried to extract the rpm file from my file manager(right click -> extract here) and it didn't recognize the format.    I dug around the internet and found a script rpm2cpio.sh... at [http://www.rpm.org/tools/scripts/]("http://www.rpm.org/tools/scripts/")
 that didn't work... complained about a piped stdin not in gzip format.

Is there an easy tool that is in one of  the std repositories for extracting rpms?

Thanks

---

### Post by rgeddes on 2008-01-17
After going over the instructions, I read that I may not need  jack_transport... the pulseaudio I'm using is 0.9.6-1ubuntu2... anyway I proceeded as if I didn't need jack_transport.... commented out the script lines that refer to jack_transport.

there is a section that references the jack-rack config file... I assume it can be any name.. does it contain something in particular (I've never used jack-rack)

When I got to the step to change the settings under System-> Preferences->Sound under the device tab, the drop downs didn't list Pulse Audio Server... I thought maybe I have to run the final script, so I ran it...

got a message dialog from jack-rack ... Could not create JACK client  Is the server running?

Also got he following terminal output:

jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: use 2 periods for playback
E: module.c: Failed to open module "module-jack-sink": libpulsecore.so.2: cannot open shared object file: No such file or directory
E: main.c: Module load failed.
E: main.c: failed to initialize daemon.
JACK tmpdir identified as [/dev/shm]
process_info_connect_jack: could not create jack client; exiting
JACK tmpdir identified as [/dev/shm]
jack server not running?
JACK tmpdir identified as [/dev/shm]
jack server not running?
JACK tmpdir identified as [/dev/shm]
jack server not running?
JACK tmpdir identified as [/dev/shm]
jack server not running?


BTW, jackd is running...

$0> ps aux | grep jackd | grep -v grep
root      7270  0.3  2.9  22556 22748 ?        SLsl 13:09   0:01 jackd -R -d alsa

Out of curiosity, I started jacd through the qtjackctl manually, and Jack Rack gives the same message....  Could not create JACK client  Is the server running?

Any help is appreciated

---

### Post by motin on 2008-01-18
> **rgeddes said:**
> I tried to extract the rpm file from my file manager(right click -> extract here) and it didn't recognize the format.    I dug around the internet and found a script rpm2cpio.sh... at [http://www.rpm.org/tools/scripts/]("http://www.rpm.org/tools/scripts/")
 that didn't work... complained about a piped stdin not in gzip format.

Is there an easy tool that is in one of  the std repositories for extracting rpms?

Thanks

That shouldn't be any problem - I just did the same maneuver over here (Gutsy). The message seems to hint that the rpm is faulty - maybe not completely downloaded? Try downloading it again.

---

### Post by motin on 2008-01-18
> **rgeddes said:**
> 
E: module.c: Failed to open module "module-jack-sink": libpulsecore.so.2: cannot open shared object file: No such file or directory
E: main.c: Module load failed.
E: main.c: failed to initialize daemon.


I got the same error in Gutsy. Tried this:

```
sudo ln -s /usr/lib/libpulsecore.so.3.0.0 /usr/lib/libpulsecore.so.2
```

And now the file is found but I get this instead:

With jackd running (through qjackctl running as normal user):

```
motin@laptop:~$ pulseaudio -n -F /home/motin/.jackd.pa &
[2] 10790
motin@laptop:~$ JACK tmpdir identified as [/dev/shm]
W: module-jack-sink.c: JACK error >cannot lock down memory for RT thread (Operation not permitted)<
JACK tmpdir identified as [/dev/shm]
W: module-jack-source.c: JACK error >cannot lock down memory for RT thread (Operation not permitted)<
E: module-jack-source.c: jack_client_open() failed.
E: module.c: Failed to load  module "module-jack-source" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: failed to initialize daemon.

```

Without:

```
$ pulseaudio -n -F /home/motin/.jackd.pa &
[1] 10707
JACK tmpdir identified as [/dev/shm]
exec of JACK server (command = "jackd") failed: No such file or directory
E: module-jack-sink.c: jack_client_open() failed.
E: module.c: Failed to load  module "module-jack-sink" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: failed to initialize daemon.

```

With jackd and sudo'd:

```
$ sudo pulseaudio -n -F /home/motin/.jackd.pa &
[3] 10820
motin@laptop:~$ W: main.c: This program is not intended to be run as root (unless --system is specified).
JACK tmpdir identified as [/dev/shm]
exec of JACK server (command = "jackd") failed: No such file or directory
E: module-jack-sink.c: jack_client_open() failed.
E: module.c: Failed to load  module "module-jack-sink" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: failed to initialize daemon.
```

So, I am trying the Debian lenny-version of PulseAudio by using prevu:

```
sudo apt-get install prevu
sudo prevu-init # <-- only needed to be run before the first time prevu is used
prevu http://ftp.de.debian.org/debian/pool/main/p/pulseaudio/pulseaudio_0.9.8-2.dsc
sudo apt-get install pulseaudio-module-jack -V
sudo adduser `whoami` pulse-rt
# log out and back in

```

Gotta log out and back in ... ibb.

---

### Post by motin on 2008-01-18
Ok - with the 0.9.8 version that problem seem to be fixed so almost there... 

Sound works in:
xine
amarok

But not in:
firefox
flash

Also, vlc doesn't start any longer (may or may not be related).

More about these problems later. First:

Here is the difference between the Pulsa Audio config file /etc/pulse/default.pa and my own breed ~/.jackd.pa :

```
$ diff .jackd.pa  /etc/pulse/default.pa 
19,22d18
< # Jack sinks
< load-module module-jack-sink
< load-module module-jack-source
< 
27c23
< #jack# load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
---
> load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
45c41
< #jack# load-module module-hal-detect
---
> load-module module-hal-detect
49c45
< #jack# load-module module-detect
---
> load-module module-detect
54c50
< #jack# load-module module-esound-protocol-unix socket="/tmp/.esd/socket"
---
> load-module module-esound-protocol-unix socket="/tmp/.esd/socket"
56c52
< #jack# load-module module-native-protocol-unix
---
> load-module module-native-protocol-unix
91c87
< # disabled because of error message "PulseAudio information vanished from X11" # load-module module-x11-publish
---
> load-module module-x11-publish

```

The shell-script:

```
#!/bin/sh

#jackd -R -d alsa &
# I'm loading the control center instead - I have set it to automatically start the JACK server upon startup (+ enabled the taskbar icon btw)
qjackctl &

sleep 5

# 
pulseaudio -n -F $HOME/.jackd.pa &

# specify your default plugin setup for JACK Rack here
RACKFILE=$HOME/.default.rack

# start JACK Rack
jack-rack -n $RACKFILE &

# wait for JACK Rack to register with JACK
sleep 3 

# connect
jack_connect "PulseAudio JACK Sink:front-left" jack_rack:in_1
jack_connect "PulseAudio JACK Sink:front-right" jack_rack:in_2
for ch in 1 2; do
    # rack -> speakers
    jack_connect jack_rack:out_$ch alsa_pcm:playback_$ch
done

```

The VLC error message:

```
$ vlc
VLC media player 0.8.6c Janus
The program '.' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 474 error_code 11 request_code 145 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

Now, flash in firefox doesn't work. Firefox doesn't even show up as a JACK output port (should it?). 

I changed to the padsp and installed the debian package of libflashsupport from [http://pulseaudio.vdbonline.net/libflashsupport/](http://pulseaudio.vdbonline.net/libflashsupport/) 

Any ides of how to proceed in order to get Flash in Firefox sound working?

Thanks a million for the guide and help so far!

---

### Post by motin on 2008-01-18
Also, even though it is possible to process all applications' sound through JACK Rack - I have to disconnect the relevant output port from alsa_pcm and connect it to jack_rack in order to run it though JACK Rack. Can this be done automatically?

---

### Post by hotspoons on 2008-01-21
Wow...I never check my hotmail account, and I logged in today and noticed a bunch of replies to this. Crazy! For my particular application (car audio) I found it more reliable to use the jack sink for gstreamer and change my gstreamer properties to route all gstreamer output to jack. Here's a walk through I wrote up for that: [http://ubuntuforums.org/showthread.php?t=554457&highlight=jack](http://ubuntuforums.org/showthread.php?t=554457&highlight=jack) . This (pulse) solution, in combination with the gstreamer solution, would take care of almost all of your audio. I'll read through this later and see if I can remember any tips for you guys who were stuck.

-Rich

---

### Post by motin on 2008-04-25
Unfortunately, Kubuntu's Amarok doesn't support gstreamer atm, and sure, I could go with the Amarok jack output plugin and probably live adequately, but now with Hardy installed it would be a shame not to be able to plug in jack between Pulse and the soundcard...

So, after having installed [pulseaudio-module-jack from debian lenny]("http://packages.debian.org/lenny/pulseaudio-module-jack"), I can now start jack using qjackctl or:
```
/usr/bin/jackd -R -t2000 -dalsa -dhw:0 -r44100 -p128 -n2
```

... followed by PulseAudio in jack-mode:
```
pulseaudio -vnF /home/motin/.jackd.pa
```

Using the following .jackd.pa:
```
#!/usr/bin/pulseaudio -nF

# Jack sinks
load-module module-jack-sink
load-module module-jack-source

### Automatically restore the volume of playback streams
load-module module-volume-restore

### Automatically restore the default sink/source when changed by the user during runtime
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists /usr/lib/pulse-0.9/modules//module-gconf.so
load-module module-gconf
.endif

.fail

```

Now PulseAudio starts fine with the following log messages:
```
motin@laptop:~$ pulseaudio -vnF /home/motin/.jackd.pa
I: main.c: We're in the group 'pulse-rt', allowing real-time and high-priority scheduling.
I: core-util.c: Successfully gained nice level -11.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operationen inte tillåten
I: main.c: This is PulseAudio 0.9.10
I: main.c: Page size is 4096 bytes
I: main.c: Fresh high-resolution timers available! Bon appetit!
I: module-jack-sink.c: Successfully connected as 'PulseAudio JACK Sink'
I: sink.c: Created sink 0 "jack_out" with sample spec "float32le 2ch 44100Hz"
I: source.c: Created source 0 "jack_out.monitor" with sample spec "float32le 2ch 44100Hz"
I: module-jack-sink.c: JACK thread starting up.
I: module-jack-sink.c: Connecting PulseAudio JACK Sink:front-left to system:playback_1
I: module-jack-sink.c: Connecting PulseAudio JACK Sink:front-right to system:playback_2
I: module.c: Loaded "module-jack-sink" (index: #0; argument: "").
I: module-jack-source.c: Successfully connected as 'PulseAudio JACK Source'
I: source.c: Created source 1 "jack_in" with sample spec "float32le 2ch 44100Hz"
I: module-jack-source.c: JACK thread starting up.
I: module-jack-source.c: connecting PulseAudio JACK Source:front-left to system:capture_1
I: module-jack-source.c: connecting PulseAudio JACK Source:front-right to system:capture_2
I: module.c: Loaded "module-jack-source" (index: #1; argument: "").
I: module.c: Loaded "module-volume-restore" (index: #2; argument: "").
I: module.c: Loaded "module-default-device-restore" (index: #3; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #4; argument: "").
I: module.c: Loaded "module-gconf" (index: #5; argument: "").
I: main.c: Daemon startup complete.

```

...and seems to connect itself to JACK (looks fine in qjackctl's Connect-overview), but everytime I try to play a sample, no sound is heard and jackd starts spitting out hundreds of messages about xruns...:
```
**** alsa_pcm: xrun of at least 1.387 msecs



**** alsa_pcm: xrun of at least 2.377 msecs



**** alsa_pcm: xrun of at least 1.099 msecs



...

```

I can but guess that this has something to do with the realtime mode of either PulseAudio or JACK but know no more. Can anybody figure out what's the issue here?

Soooo close now to finally be able to run all application sounds through JACK...

---

### Post by noisesmith on 2008-05-04
> **motin said:**
> Unfortunately, Kubuntu's Amarok doesn't support gstreamer atm, and sure, I could go with the Amarok jack output plugin and probably live adequately, but now with Hardy installed it would be a shame not to be able to plug in jack between Pulse and the soundcard...

So, after having installed [pulseaudio-module-jack from debian lenny]("http://packages.debian.org/lenny/pulseaudio-module-jack"), I can now start jack using qjackctl or:
```
/usr/bin/jackd -R -t2000 -dalsa -dhw:0 -r44100 -p128 -n2
```

... followed by PulseAudio in jack-mode:
```
pulseaudio -vnF /home/motin/.jackd.pa
```

Using the following .jackd.pa:
```
#!/usr/bin/pulseaudio -nF

# Jack sinks
load-module module-jack-sink
load-module module-jack-source

### Automatically restore the volume of playback streams
load-module module-volume-restore

### Automatically restore the default sink/source when changed by the user during runtime
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists /usr/lib/pulse-0.9/modules//module-gconf.so
load-module module-gconf
.endif

.fail

```

Now PulseAudio starts fine with the following log messages:
```
motin@laptop:~$ pulseaudio -vnF /home/motin/.jackd.pa
I: main.c: We're in the group 'pulse-rt', allowing real-time and high-priority scheduling.
I: core-util.c: Successfully gained nice level -11.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operationen inte tillåten
I: main.c: This is PulseAudio 0.9.10
I: main.c: Page size is 4096 bytes
I: main.c: Fresh high-resolution timers available! Bon appetit!
I: module-jack-sink.c: Successfully connected as 'PulseAudio JACK Sink'
I: sink.c: Created sink 0 "jack_out" with sample spec "float32le 2ch 44100Hz"
I: source.c: Created source 0 "jack_out.monitor" with sample spec "float32le 2ch 44100Hz"
I: module-jack-sink.c: JACK thread starting up.
I: module-jack-sink.c: Connecting PulseAudio JACK Sink:front-left to system:playback_1
I: module-jack-sink.c: Connecting PulseAudio JACK Sink:front-right to system:playback_2
I: module.c: Loaded "module-jack-sink" (index: #0; argument: "").
I: module-jack-source.c: Successfully connected as 'PulseAudio JACK Source'
I: source.c: Created source 1 "jack_in" with sample spec "float32le 2ch 44100Hz"
I: module-jack-source.c: JACK thread starting up.
I: module-jack-source.c: connecting PulseAudio JACK Source:front-left to system:capture_1
I: module-jack-source.c: connecting PulseAudio JACK Source:front-right to system:capture_2
I: module.c: Loaded "module-jack-source" (index: #1; argument: "").
I: module.c: Loaded "module-volume-restore" (index: #2; argument: "").
I: module.c: Loaded "module-default-device-restore" (index: #3; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #4; argument: "").
I: module.c: Loaded "module-gconf" (index: #5; argument: "").
I: main.c: Daemon startup complete.

```

...and seems to connect itself to JACK (looks fine in qjackctl's Connect-overview), but everytime I try to play a sample, no sound is heard and jackd starts spitting out hundreds of messages about xruns...:
```
**** alsa_pcm: xrun of at least 1.387 msecs



**** alsa_pcm: xrun of at least 2.377 msecs



**** alsa_pcm: xrun of at least 1.099 msecs



...

```

I can but guess that this has something to do with the realtime mode of either PulseAudio or JACK but know no more. Can anybody figure out what's the issue here?

Soooo close now to finally be able to run all application sounds through JACK...

The xruns are caused by too small a frames/period setting or periods/buffer setting in qjackctl. Try different values, and pick the smallest value of (frames/period)*(periods/buffer) that does not make xruns happen regularly.

---

### Post by motin on 2008-06-25
Having bought a new computer, I just tried to reaccomplish this. This time I do not get any errors at start-up of neither jack nor pulseaudio but on the other hand other clients cannot connect to the pulseaudio server...

Has anyone tried this since last time we posted and have any success stories to share?

---

### Post by motin on 2008-07-03
> **neltnerb said:**
> I agree that pulseaudio outputting to jack is ideal, but this seems to be much further from functional than your HOWTO here as far as amarok is concerned =) I feel like a reasonable workaround should be to have ALSA recognize jack as an output device, but even though I was able to do this, it didn't integrate at all into the rest of the system.

In particular, jackd has to be running before you try to connect ALSA to it -- since ALSA starts far before you can open qjackctl or run jackd from the command line as a human, this has to be addressed by some sort of script. I'm not sure as to the timing, so that's something that would have to be addressed. Further, the System->Sound configuration tool didn't list the jack devices even when I started the jack server and then restarted ALSA. I could *try* to figure out how to configure gnome to output to my chosen device, but it's a lot of hassle.

I'd personally rather just use this workaround for my music along with 'mplayer -ao jack' for movies until the Ubuntu developers consider jack to be stable enough to include in universe. The only other thing I'd like to be able to do is get firefox to output to jack as well, but I don't see anything reasonable matching 'sound' or 'audio' in about:config.

Never thought about the Jack before Alsa requirement... Maybe that's the whole deal here. Have you tried following the steps in this guide? It worked on Feisty for the OP, but I haven't had any luck... Would be interesting to see if one of us could make it work...

---

### Post by motin on 2008-07-21
Shameless Bump - has anyone managed to set this up on Hardy?

If someone could help here it would be greatly appreciated!

JACK through PulseAudio for me is the ability to easily jam using a midi keyboard between ordinary laptop work - if there is 20ms latency I really don't care - as long as I can jam to Youtube-videos etc...

Cheers!

---

