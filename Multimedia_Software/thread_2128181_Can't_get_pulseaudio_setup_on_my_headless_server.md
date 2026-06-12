---
title: "Can't get pulseaudio setup on my headless server"
date: 2013-03-22
forum: Multimedia Software
---

### Post by homer52 on 2013-03-22
[COLOR=#000000][FONT=verdana]So I have been trying to setup pulseaudio for hours.

[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]I have MPD and a pulseaudio server installed on a headless ubuntu server on my network. The pulseaudio server is setup to stream the audio using RTP. 

On my laptop I can setup pulseauido using 'paprefs' and I can hear the audio through my laptop speakers.

I have another headless server with speakers plugged into it.  I can't seem to get pulseaudio to stream to this system to play through the speakers using the RTP stream.  Sound is able to play out of the speakers using mplayer though.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]
So far I have set it up in system mode and have included the line "load-module module-rtp-recv" in my system.pa file. When I reboot the server the pulseaudio service is running with command:[/FONT][/COLOR]
[FONT=verdana, arial, helvetica, sans-serif][SIZE=2][COLOR=#000000]"/usr/bin/pulseaudio --system --disallow-exit --disallow-module-loading=1 --daemonize --log-target=syslog --high-priority" under the user 'pulse'.[/COLOR][/SIZE][/FONT]
[COLOR=#000000][FONT=verdana]
Any help will be appreciated.[/FONT][/COLOR]

---

