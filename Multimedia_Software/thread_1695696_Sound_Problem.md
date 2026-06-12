---
title: "Sound Problem"
date: 2011-02-26
forum: Multimedia Software
---

### Post by amir786_z on 2011-02-26
Hi there guys iam new to ubuntu.. i just love this o.s. i left windows. but i have this sound issue that i cant figure out how to solve it:confused:, making me really disappointed in ubuntu:(.. after about 1 hour or so sound stops working and when i restart the system the sound comes back on. cant figure out whats wrong. this sound problem making me mad:mad:. can somebody tell me whats the solution of this problem.. 

thanks in advance guys:)..

---

### Post by amir786_z on 2011-02-27
hey guys, its been a while could someone help me out please, with the sound issue? 
Thanks

---

### Post by amir786_z on 2011-02-28
i think nobody cares to help me :(.. still stuck on the same problem..

---

### Post by amir786_z on 2011-03-01
and my sound card is

Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 3603
    Flags: bus master, fast devsel, latency 0, IRQ 49
    Memory at df300000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

can somebody help me now please..

---

### Post by amir786_z on 2011-03-01
so many views but no one suggested any solution :(..

---

### Post by lidex on 2011-03-01
Try resetting your pulse configuration. 
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Logout/in.**
No joy? Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by amir786_z on 2011-03-02
thanks man :) ... i will check when the sound stops this time..:D..

---

### Post by amir786_z on 2011-03-03
i think sound issue is resolved somehow maybe by an update.. now it does not stop. :) iam so happy :D:D

---

### Post by amir786_z on 2011-03-04
**Damn sound stops again :(:(.. i tried this following commands**

> **lidex said:**
> Try resetting your pulse configuration. 
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```**Logout/in.**

**the result is this:-**
rm: cannot remove `/home/amir/.asound*': No such file or directory
amir@amir-HP-Pavilion-dv5-Notebook-PC:~$ sudo rm /etc/asound.conf

**Now for this following set of code **

No joy? Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

**i uploaded all the info..and in the end this link appeared**
[http://www.alsa-project.org/db/?f=acf61414f2ca782058d1b2f1daf50a63e6581af3](http://www.alsa-project.org/db/?f=acf61414f2ca782058d1b2f1daf50a63e6581af3)

---

### Post by lidex on 2011-03-04
Let's see what pulse is up to:
```
pkill pulseaudio; sleep 2; pulseaudio -vv
```
Next time it cuts out, run this and post results:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

In the interim - as a workaround - try this to get your sound back:
```
sudo alsa force-reload
```

BTW, do all of your audio devices work?

---

### Post by amir786_z on 2011-03-07
thanks man i will try all the commands that u said, when sound stops this time.;)

---

### Post by amir786_z on 2011-03-08
> **lidex said:**
> Let's see what pulse is up to:
```
pkill pulseaudio; sleep 2; pulseaudio -vv
```
The above command result
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: core-rtclock.c: Timer slack is set to 50 us.
D: core-util.c: RealtimeKit worked.
I: core-util.c: Successfully gained nice level -11.
I: main.c: This is PulseAudio 0.9.21-63-gd3efa-dirty
D: main.c: Compilation host: i686-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pipe -Wno-long-long -Winline -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing=2 -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: main.c: Running on host: Linux i686 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:29 UTC 2011
D: main.c: Found 2 CPUs.
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Running in VM: no
D: main.c: Optimized build: yes
D: main.c: All asserts enabled.
I: main.c: Machine ID is 62c64d2bc2d87990217ca6990000000e.
I: main.c: Session ID is 62c64d2bc2d87990217ca6990000000e-1299599679.825498-1962468931.
I: main.c: Using runtime directory /home/amir/.pulse/62c64d2bc2d87990217ca6990000000e-runtime.
I: main.c: Using state directory /home/amir/.pulse.
I: main.c: Using modules directory /usr/lib/pulse-0.9.21/modules.
I: main.c: Running in system mode: no
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.


Next time it cuts out, run this and post results:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

the result is

Specified filename /dev/dsp* does not exist.
Specified filename /dev/seq* does not exist.
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  amir      15579 F.... pulseaudio




In the interim - as a workaround - try this to get your sound back:
```
sudo alsa force-reload
```

the result is

lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/amir/.gvfs
      Output information may be incomplete.
Terminating processes: 15579lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/amir/.gvfs
      Output information may be incomplete.
 16312lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/amir/.gvfs
      Output information may be incomplete.
 16332lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/amir/.gvfs
      Output information may be incomplete.
 16347lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/amir/.gvfs
      Output information may be incomplete.
 (with SIGKILL:) 16363lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/amir/.gvfs
      Output information may be incomplete.
 (failed: processes still using sound devices: 16383(pulseaudio)).
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/amir/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 16383(pulseaudio).
Unloading ALSA sound driver modules: snd-hda-codec-nvhdmi snd-hda-codec-idt snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-codec-nvhdmi snd-hda-codec-idt snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-hda-codec-nvhdmi snd-hda-codec-idt snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.

BTW, do all of your audio devices work?

and all my sound devices work i checked in windows..

---

### Post by lidex on 2011-03-08
What I was asking is do all your devices work in ubuntu with your configuration? Line, mic, headphones, etc? Did the reload bring back audio?

---

### Post by amir786_z on 2011-03-08
yes all my devices work with my configuration...but sometimes sound stops...no reload did not bring back sound..

---

### Post by amir786_z on 2011-03-12
hmm so no solution for this problem? :(:(

---

### Post by amir786_z on 2011-03-14
hello guys can anybody help me with the soln of this problem:( ?

---

### Post by amir786_z on 2011-04-03
Thank GOD problem is solved.. i think mozilla is corrupt or bugged in ubuntu. it causes sound problem and as well as flash problem. so i quit using mozilla and started using chrome. now the things are going well.

thanks guys who helped me.. i appreciate ur help :)

---

