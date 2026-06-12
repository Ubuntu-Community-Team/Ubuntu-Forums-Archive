---
title: "Sound stopped working suddenly"
date: 2009-02-26
forum: Multimedia Software
---

### Post by airjaw on 2009-02-26
Hi all, wondering if I can get help with troubleshooting this.
My sound was working fine (well relatively; pulseaudio always give me random troubles but worked if I restarted)
but all of a sudden my sound stopped working. mp3s would play but no sound comes out. Instead I get this static-y noise.
the pulse audio process was in futex_wait and I tried killing it. Got an error though.

So I restart my computer, and the sound still isn't working! At this point I think maybe my sound card died. I boot into Windows and the sound is working perfectly. Reboot into Ubuntu and here I am.

Some details:
Ubuntu 8.10
Dell Inspiron 1520 
> snd-hda-intel
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
        Subsystem: Dell Device 01f1                                                      
        Flags: bus master, fast devsel, latency 0, IRQ 21                                
        Memory at febfc000 (64-bit, non-prefetchable) [size=16K]                         
        Capabilities: <access denied>                                                    
        Kernel driver in use: HDA Intel                                                  
        Kernel modules: snd-hda-intel    

If there is any other info I can provide that would be of help, please let me know.
Thanks.


edit::output from a few shell commands
> $ pulseaudio
W: ltdl-bind-now.c: Failed to find original dlopen loader.
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.


> $ killall -9 pulseaudio && pulseaudio
W: ltdl-bind-now.c: Failed to find original dlopen loader.
W: pid.c: Stale PID file, overwriting.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0


Oh, and when Pulseaudio is running, I hear that staticky sound when I try to play music. When I kill pulseaudio, the sound goes away.

---

### Post by markbuntu on 2009-02-26
You can try reloading ALSA or reinstalling it. There are directions for that in here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by airjaw on 2009-02-26
For some reason, my PCM output was MUTED.
alsamixer -Dhw
 and increased the PCM. It was set at 0.
weird thing is, in my desktop volume settings, the PCM was set just fine.  Are thee volume settings not linked or something?


edit:: how do I make this thread [SOLVED}

---

