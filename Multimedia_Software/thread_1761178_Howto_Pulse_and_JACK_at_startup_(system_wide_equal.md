---
title: "Howto: Pulse and JACK at startup (system wide equalization and etc)"
date: 2011-05-17
forum: Multimedia Software
---

### Post by MBouffard on 2011-05-17
1) Install JACK, JACK Rack and related stuff:

```
sudo apt-get install jackd1 pulseaudio-module-jack jack-rack libnotify-bin ladspa-sdk plugins-swh
```

More packages might be needed here, I'm not sure. You can also browse Synaptic for more LADSPA plugins. "Patchage" is also a useful program to verify that everything is connected properly.

2) Make configuration files:

Stop pulseaudio from starting automatically:

Make ~/.pulse/client.conf and paste

```
autospawn=no
```

Create .asoundrc in your home directory and paste:

```
#  ALSA configuration file, .asoundrc

pcm.!default {
    type pulse
    hint.description "Default Audio Device"
}
ctl.!default {
    type pulse
}
```

Create jackd.pa, paste:

```
#!/usr/bin/pulseaudio -nF
#	Pulse config file
#---------------------------------#

###
# these modules will connect to JACK
load-module module-jack-sink
load-module module-jack-source

###
#add-autoload-sink output module-jack-sink channels=2
#add-autoload-source input module-jack-source channels=2
#load-module module-esound-protocol-unix
load-module module-native-protocol-unix
load-module module-stream-restore
load-module module-rescue-streams
.nofail

###
load-module module-x11-publish
load-module module-gconf

###
# Load LIRC for Pulse, uncomment if needed
#load-module module-lirc sink=jack_out config=/home/###username###/.lircrc
```

3) Open JACK Rack, add some plugins and save a configuration to "array.rack" in your home directory.

4) Now for the startup script:

Create sound.sh in your home directory

```
#!/bin/sh
#
# JACK/Pulse/DSP startup loader
#-----------------------------------------#

# Variables
#-----------------------------------------#
PULSECONF=/home/`whoami`/jackd.pa
RACKFILE=/home/`whoami`/array.rack
LOGDIR=/home/`whoami`/logs/jack
JACKLOG=/home/`whoami`/logs/jack/jack.log
TRANS=/home/`whoami`/logs/jack/transport
STATS=/home/`whoami`/logs/jack/stats

# Clean up old log files/logging stuff
#-----------------------------------------#
rm -rf $LOGDIR/*
sleep 1

# Check for configuration files, alert user
# to make them if they dont exist and exit
#------------------------------------------#
if [ -s $PULSECONF ]; then
	echo "JACKLoader: jackd.pa exists." > $JACKLOG
else
	echo "JACKLOADER: jackd.pa not found. Exiting." >> $JACKLOG
	notify-send "JACK" \
		"Error: No configuration file for pulse (jackd.pa)"
	exit 1
fi

# Ping clienf.conf, if it does not exist,
# make one. Kill pulse and continue
#----------------------------------------#
if [ -s /home/`whoami`/.pulse/client.conf ]; then
	echo "JACKLOADER: client.conf exists in ~/.pulse/" >> $JACKLOG
else
	echo "autospawn=no" > /home/`whoami`/.pulse/client.conf
	echo "JACKLOADER: Created client.conf. Killing pulseaudio..." >> $JACKLOG
	pulseaudio --kill >> $JACKLOG 2>&1 &
	sleep 1
fi

echo "JACKLOADER: Ready. Starting..." >> $JACKLOG

# Start JACK
#-----------------------------------------#

# To edit JACK settings, view JACK documentation or use
# Qjackctl to generate a .jackdrc and paste it here.
jackd -r -dalsa -dhw:0 -r96000 -p512 -n4 -P -o2 >> $JACKLOG 2>&1 &
sleep 2 &&

# Start Pulse
#-----------------------------------------#
pulseaudio -n -F $PULSECONF >> $JACKLOG 2>&1 &
sleep 2 &&

# Start JACK transport
#-----------------------------------------#
echo "play" | jack_transport > /dev/null 2>&1 &
sleep 1 &&
jack-info > $TRANS &&

# Verify transport and continue
#-----------------------------------------#
if [ -s $TRANS ]; then
	# jack-info creates an empty file if JACK is not running or not transporting
	# so we just ping for a non-empty transport file. If it doesn't exist then there
	# was an error.
	echo "JACKLOADER: transport file exists and is not empty which indicates success, moving on..." >> $JACKLOG
else
	notify-send "JACK" \
		"There was an error starting the sound servers.\nPlease see the log files."
	echo "JACKLOADER: Failure, existing with status 1." >> $JACKLOG
	exit 1
fi

# Launch DSP
#-----------------------------------------#
jack-rack -n $RACKFILE > /dev/null 2>&1 &
sleep 4 &&
# To make sure that jack-rack is registered before connecting...
sleep 2 &&

# Connect the components together
#-----------------------------------------#

# First disconnect the sink from the sound card
jack_disconnect "system:playback_1" "PulseAudio JACK Sink:front-left" >> $JACKLOG 2>&1
jack_disconnect "system:playback_2" "PulseAudio JACK Sink:front-right" >> $JACKLOG 2>&1
# Connect the sink to jack rack
jack_connect "PulseAudio JACK Sink:front-left" "jack_rack:in_1" >> $JACKLOG 2>&1
jack_connect "PulseAudio JACK Sink:front-right" "jack_rack:in_2" >> $JACKLOG 2>&1
# Connect jack rack to the sound card
jack_connect "jack_rack:out_1" "system:playback_1" >> $JACKLOG 2>&1
jack_connect "jack_rack:out_2" "system:playback_2" >> $JACKLOG 2>&1

# All done, notify & exit
#------------------------------------------#
notify-send "JACK" \
	"The DSP is enabled and JACK is connected.\nChannels: Stereo playback"
echo "JACKLOADER: DSP loaded and components connected. Exiting with status 0." >> $JACKLOG
exit 0
```

Make sure that the script can be executed and point Startup Applications to it (/home/username/sound.sh)

You might have to fiddle with the startup script because this is a rather peculiar setup. ;)

To troubleshoot, check ~/logs/jack/jack.log. A possible problem could be that it's not using the correct names to connect, so edit accordingly.

To restart without rebooting, close jack rack if opened, open a terminal:
```
killall jackd
pulseaudio --kill
./sound.sh
```

But now, all programs *should* be directed to use PulseAudio, which should be connected to jack-rack, which should be connected to JACK output. I don't use capture devices in this manner, so figuring that out would be up to you.

---

