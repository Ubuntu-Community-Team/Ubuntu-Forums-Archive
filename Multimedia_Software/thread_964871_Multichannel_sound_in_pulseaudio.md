---
title: "Multichannel sound in pulseaudio"
date: 2008-10-31
forum: Multimedia Software
---

### Post by Longinus00 on 2008-10-31
I've been trying to get 5.1 sound to work in 8.10 as per these instructions. [http://ubuntuforums.org/showthread.php?t=795525](http://ubuntuforums.org/showthread.php?t=795525) ```
default-sample-channels = 6
```  Using speaker-test I can make out that there are indeed 6 discreet channels. Everything was going well until very recently. I started noticing something was amiss when pulseaudio was taking up 50% cpu whenever I watched a video.
```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 8196 dl        20   0 31340 6304 4920 S 53.3  0.3   3:20.19 pulseaudio         
 8080 root      20   0  412m  39m  10m S  9.3  2.0   0:43.24 Xorg               
 8772 dl        20   0 73336  24m 8416 S  7.3  1.2   0:05.08 mplayer
```Normally this should look like this. (The higher mplayer cpu usage is because my A64 is able to clock down more due to pulseaudio not requiring so much processing power. Both of these results are from playing the same video file.)
```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 9264 dl        20   0 74360  24m 8372 S 14.8  1.2   0:04.15 mplayer            
 8080 root      20   0  404m  40m  11m R 13.7  2.0   2:21.33 Xorg               
 9256 dl        20   0 31160 5148 3980 S  5.7  0.2   0:01.53 pulseaudio 
```
This causes horrible slowdowns in certain cases and makes flash video all but unwatchable. Sometimes pulseaudio will crash in the middle of playback. The error that floods the stdout when pulseaudio dies is this.
```
AO: [pulse] Connection died: Connection terminated22 ??% ??% ??,?% 0 0 
AO: [pulse] Connection died: Connection terminated
AO: [pulse] Connection died: Connection terminated
AO: [pulse] Connection died: Connection terminated
```
This floods stdout until I ctrl-c mplayer. There are a few variations on the question marks that appear but I have no idea what they mean.
```

AO: [pulse] Connection died: Connection terminated  4%  0%  2.3% 8 0 
```
```
AO: [pulse] Connection died: Connection terminated  4%  0%  1.8% 11 0
```
Setting ```
default-sample-channels = 2
``` in daemon.conf fixes the pulseaudio cpu usage but leaves me without 5.1 audio. 


I went poking around in /var/log to see if there were any clues and I find this message in my syslog.

```
pulseaudio[8161]: ltdl-bind-now.c: Failed to find original dlopen loader.
pulseaudio[8163]: pid.c: Stale PID file, overwriting.
pulseaudio[8163]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
pulseaudio[8163]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
**pulseaudio[8163]: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.**
pulseaudio[8163]: module-x11-xsmp.c: X11 session manager not running.
pulseaudio[8163]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
```

I have no idea why pulseaudio says this but perhaps it's referring to the card's input capabilities rather than output? 

The card I am using is a Sound Blaster Audigy 2 ZS
```
$ dmesg | grep Audigy
[   15.614619] EMU10K1_Audigy 0000:00:08.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   15.617048] Installing spdif_bug patch: Audigy 2 ZS [SB0350]
```
```
$ lspci | grep audio
00:08.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
```

I don't know when this started because and I'm fairly certain that when I set up 5.1 a few days ago there was no outrageous cpu usage. I remember getting a kernel update from the update manager recently but I have no idea if that's the culprit.

Any help or suggestions would be appreciated.

---

### Post by Brebs on 2008-10-31
With an Audigy 2 ZS (which is one of the very few cards performing **hardware mixing**), pulseaudio is 99% likely to be useless for you. In fact, more than useless - it will add latency, for zero benefit.

I (on a different distro) recompile ALSA with pulseaudio removed. E.g. with alsa-plugins:  ./configure **--without-pulse**

And in alsa-lib, remove any patches making pulseaudio the default.

---

