---
title: "Jack + Pulseaudio: no sound through headphones"
date: 2012-03-13
forum: Multimedia Software
---

### Post by virgult on 2012-03-13
I don't like bothering the community with this kind of very specific requests, since they're the most cumbersome to solve and yet they don't provide real useful information to the user base, but I'm really getting annoyed with this one, thus I have to pass it on to you.

On my brand new Asus X54C, when I start Jack (through Jackd or Qjackctl), I hear no sound from the headphones when I plug them in, but everything works just fine from the internal speakers. Every other audio subsystem (ALSA, Puleaudio) works well.

I can guess that in some way Jack connects only to the speaker output in ALSA, bypassing the headphone control, or when PulseAudio mutes the speaker output and routes everything to the phones output, jack is "left behind". I have no experience with Pulse and Jack configuration files, I have googled and tried to edit some details in /etc/pulse/default.pa, to no avail.

Please get me out of this mess. :)
Info about the notebook: Asus X54C with Core i3 Sandy Bridge 2350M, internal graphics, internal HD Audio soundcard, HM65 chipset, 2 gigs of ram (going to upgrade soon ;) ), and a "vanilla" Kubuntu 11.10 as the only OS.

/etc/pulse/default.pa:

```
.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/gtk-events/activate.wav
#load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-coldplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-access /usr/share/sounds/generic.wav

.fail

### Automatically restore the volume of streams and devices
load-module module-device-restore
load-module module-stream-restore
load-module module-card-restore

### Automatically augment property information from .desktop files
### stored in /usr/share/application
load-module module-augment-properties

### Load audio drivers statically
### (it's probably better to not load these drivers manually, but instead
### use module-udev-detect -- see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
load-module module-udev-detect
.else
### Use the static hardware detection module (for systems that lack udev/hal support)
load-module module-detect
.endif

### Automatically connect sink and source if JACK server is present
.ifexists module-jackdbus-detect.so
load-module module-jackdbus-detect
.endif

### Automatically load driver modules for Bluetooth hardware
.ifexists module-bluetooth-discover.so
load-module module-bluetooth-discover
.endif

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish

### If the zeroconf/RAOP package is installed, load the module automatically.
### TODO: Upstream thinks this should be done using gconf/paprefs instead.
.ifexists module-zeroconf-discover.so
.nofail
load-module module-zeroconf-discover
.fail
.endif
.ifexists module-raop-discover.so
.nofail
load-module module-raop-discover
.fail
.endif


### Load the RTP receiver module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 sink_properties="device.description='RTP Multicast Sink'"
#load-module module-rtp-send source=rtp.monitor

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

### Automatically restore the default sink/source when changed by the user
### during runtime
### NOTE: This should be loaded as early as possible so that subsequent modules
### that look up the default sink/source get the right value
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Make sure we always have a sink around, even if it is a null sink.
load-module module-always-sink

### Honour intended role device property
load-module module-intended-roles

### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### If autoexit on idle is enabled we want to make sure we only quit
### when no local session needs us anymore.
.ifexists module-console-kit.so
load-module module-console-kit
.endif

### Enable positioned event sounds
load-module module-position-event-sounds

### Cork music streams when a phone stream is active
#load-module module-cork-music-on-phone
### Modules to allow autoloading of filters (such as echo cancellation)
### on demand. module-filter-heuristics tries to determine what filters
### make sense, and module-filter-apply does the heavy-lifting of
### loading modules and rerouting streams.
load-module module-filter-heuristics
load-module module-filter-apply

### Load DBus protocol
.ifexists module-dbus-protocol.so
load-module module-dbus-protocol
.endif

# X11 modules should not be started from default.pa so that one daemon
# can be shared by multiple sessions.

### Load X11 bell module
#load-module module-x11-bell sample=bell-windowing-system

### Register ourselves in the X11 session manager
#load-module module-x11-xsmp

### Publish connection data in the X11 root window
#.ifexists module-x11-publish.so
#.nofail
#load-module module-x11-publish
#.fail
#.endif

load-module module-switch-on-port-available

### Make some devices default
#set-default-sink output
#set-default-source input


```

Jackd output:

```
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2011 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 10
control device hw:0
control device hw:0
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback

```

---

### Post by virgult on 2012-03-13
P.S: I tried removing Pulseaudio, but this prevents Jack from running at all. I suppose that is because Phonon keeps the interface permanently busy through ALSA. When I fire up Jackd, the main error is "the playback device "hw:0" is already in use. please stop the application using it and run jack again".

---

### Post by MAM3166 on 2012-05-21
bump :p
Got the same problem, it's frustrating, after all the trouble I've been throught working to fix every glitch (including wine)..

I beleive it's wineasio, since I've got test sound in winecfg with pulseaudio, headphones in, but nothing with FL studio 10

AND no audio at all from other apps (sound forge 9.0c, traktor 1.01 demo) ......help :)

---

