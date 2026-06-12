---
title: "Sound streaming to ethernet wired and|or wireless speakers"
date: 2013-08-07
forum: Multimedia Software
---

### Post by KmCsDFL on 2013-08-07
Hi,
I was trying for last couple of hours to stream to : Pioneer XW-SMA4-K wired netwok speakers from Ubuntu using
pulse ausio 3.0 From x86_64 x86, Ubuntu raring (13.04). I ran into several posts and I uninistalled/ reinstalled
combinations of pulseaudio/alsa, configs and I have no succes of hearing any bit on the remote speaker.
The device  claims that it accepts:


[LIST]
[*][SIZE=1][FONT=courier new]AirPlay 
[/FONT][/SIZE] 
[*][SIZE=1][FONT=courier new]DLNA Digital Media Rendering
[/FONT][/SIZE] 
[/LIST]

I can see in pulse configuration UI the 


[LIST]
[*][FONT=courier new][SIZE=1]Speaker Build in audio
[/SIZE][/FONT] 
[*][FONT=courier new][SIZE=1]filips [/SIZE][/FONT]                                  [COLOR=#006400][SIZE=1]*<- the remote speaker, detected by pulseaudio*[/SIZE][/COLOR] 
[/LIST]


 and it appears with correct IP in pacmd. Still there is no sound when I am selecting the device, nomater I load unload 
the modules specified after the pacmd output.

[COLOR=#0000cd][SIZE=1][FONT=courier new]pacmd list | grep filips
    argument: <server=[192.168.1.113]:1026 sink_name=raop.filips.local sink_properties='device.description="filips"'>
    name: <raop.filips.local>
        device.description = "filips"
    name: <raop.filips.local.monitor>
        device.description = "Monitor of filips"
marius@ofis:~$ pacmd list | grep filips
    argument: <server=[192.168.1.113]:1026 sink_name=raop.filips.local sink_properties='device.description="filips"'>
    name: <raop.filips.local>
        device.description = "filips"
    name: <raop.filips.local.monitor>
        device.description = "Monitor of filips"
marius@ofis:~$ pacmd list | grep filips
    argument: <server=[192.168.1.113]:1026 sink_name=raop.filips.local sink_properties='device.description="filips"'>
    name: <raop.filips.local>
        device.description = "filips"
    name: <raop.filips.local.monitor>
        device.description = "Monitor of filips"

[/FONT][/SIZE][/COLOR]
 - pulseaudio 3.0 with config, (listed at the end)
 - with modules loaded/unloaded (from shell), in different combinations.

[SIZE=1][FONT=courier new]pacmd load-module module-native-protocol-tcp
pacmd load-module load-module module-rtp-send
pacmd load-module module-cli-protocol-unix
pacmd load-module module-rtp-send
pacmd load-module module-http-protocol-tcp[/FONT][/SIZE]


Any troubleshooting would be appreciated. I really need to be able to stream from Linux to
the speakers.

Thank you.


























[FONT=courier new][SIZE=1]load-module module-device-restore
load-module module-stream-restore
load-module module-card-restore
.ifexists module-udev-detect.so
    load-module module-udev-detect use_ucm=0
.else
    load-module module-detect
.endif

.ifexists module-jackdbus-detect.so
.nofail
    load-module module-jackdbus-detect channels=2
.fail
.endif

.ifexists module-bluetooth-policy.so
    load-module module-bluetooth-policy
.endif

.ifexists module-bluetooth-discover.so
    load-module module-bluetooth-discover
.endif

.ifexists module-esound-protocol-unix.so
    load-module module-esound-protocol-unix
.endif
    load-module module-native-protocol-unix

load-module module-rtp-send

load-module module-default-device-restore
load-module module-rescue-streams
load-module module-always-sink
load-module module-intended-roles
load-module module-suspend-on-idle

.ifexists module-console-kit.so
    load-module module-console-kit
.endif
.ifexists module-systemd-login.so
    load-module module-systemd-login
.endif
load-module module-position-event-sounds
load-module module-switch-on-port-available
[/SIZE][/FONT]

---

### Post by Nicolas_Andrade on 2014-01-19
Hello !
I wanted to buy this speaker to use with Pulse and I've found your post while searching for the compatibility of this device with Pulse.
I had a iHome iw1 that did not work with Pulse. But while working with this one, I've learned how to turn on the debugging mode.

Essentially you'll need to:
1-Avoid pulseaudio to respawn automatically when you kill it.
2-Kill pulseaudio
3-Start pulseaudio in Debug mode
4-Monitor the debug output
5-Try to connect the speaker
6-Try to play sound
7-Get the debug output, understand what it says, and paste it in the forums!

So, step by step:
1-Avoid pulseaudio to respawn automatically when you kill it.
[COLOR=#333333][FONT=UbuntuRegular][COLOR=#222222][FONT=Verdana]
Create a ~/.pulse/ directory (I guess it exists already) and create a file named "client.conf" inside. This file should have this line

```
autospawn=no
```

2-Kill pulseaudio
Open a terminal and issue the command:

```
killall pulseaudio
```

[/FONT][/COLOR][COLOR=#222222][FONT=Verdana]3-Start pulseaudio in Debug mode
[/FONT][/COLOR][COLOR=#222222][FONT=Verdana]On the same terminal, call pulseaudio in verbose mode, and sending log messages to the System log:

[/FONT][/COLOR][/FONT][/COLOR]```
pulseaudio -v --log-target=syslog
```
[COLOR=#333333][FONT=UbuntuRegular][COLOR=#222222][FONT=Verdana]
To have more info, you can increase the level of verbosity:

[/FONT][/COLOR][/FONT][/COLOR]```
pulseaudio -vv --log-target=syslog
```
[COLOR=#333333][FONT=UbuntuRegular][COLOR=#222222][FONT=Verdana]
```
tail -f /var/log/syslog | grep pulse
```

4-Monitor the log:
In a new terminal, type:

[/FONT][/COLOR][/FONT][/COLOR]```
[FONT=Verdana]tail -f /var/log/syslog | grep pulse[/FONT]
```
[COLOR=#333333][FONT=UbuntuRegular][COLOR=#222222][FONT=Verdana]
5-Try to connect the speaker
[/FONT][/COLOR][COLOR=#222222][FONT=Verdana]6-Make some noise!!
[/FONT][/COLOR][COLOR=#222222][FONT=Verdana]
7-Get the debug output, understand what it says, and paste it in the forums!

```
grep "pulse" /var/log/syslog > /tmp/pulse.log
```

Your log will be stored in /tmp/pulse.log


To revert your system to it's default, remove the "autospawn" line from ~/.pulse/client.conf; or set it back to
```
autospawn = yes
```


Then let us know what comes out from these steps! I'm interested on the results as I might buy the same Pioneer speaker.

Best!



[/FONT][/COLOR][/FONT][/COLOR]

---

