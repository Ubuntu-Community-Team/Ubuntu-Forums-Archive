---
title: "sound gone after login"
date: 2011-09-18
forum: Multimedia Software
---

### Post by Dubanubiel on 2011-09-18
Last night I was once again trying to get Skype working without sounding terrible. Skype crashed (as usual) and it took my sound with it (as usual). Problem is, when I rebooted my sound was still gone. When I open up sound preferences, there are no devices shown. I've read the comprehensive guide and just about everything else I could find and nothing has fixed it. every asla check I do gives me errors. The weird thing is, when I first start linux, I can get sound on the login screen but not when I log in. I (begrudgingly) dual-boot and sound still works in Windows. I'm running 11.04 with an integrated Realtek soundcard. A quick warning: I'm not the most proficient Linux user.

---

### Post by lidex on 2011-09-18
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

After that run these commands and post the output using code tags (#)
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```
```
pkill pulseaudio; sleep 2; pulseaudio -vv
```

And finally your alsa-info. ```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by Dubanubiel on 2011-09-19
Thank you so much lidex! You are a total ear saver. I did the first step and I was nearly knocked out of my chair by tribal drums and crickets as I logged in (I had my speakers CRANKED). I didn't know if you still wanted that code so I'll post it below.

The first one:
```
Specified filename /dev/dsp* does not exist.
Specified filename /dev/seq* does not exist.
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  dan        1444 F.... pulseaudio
/dev/snd/controlC1:  dan        1444 F.... pulseaudio

```second:
```
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: core-rtclock.c: Timer slack is set to 50 us.
D: core-util.c: RealtimeKit worked.
I: core-util.c: Successfully gained nice level -11.
I: main.c: This is PulseAudio 0.9.22-24-g67d18
D: main.c: Compilation host: i686-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -O2 -Wall -W -Wextra -pipe -Wno-long-long -Winline -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing=2 -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: main.c: Running on host: Linux i686 2.6.38-11-generic-pae #48-Ubuntu SMP Fri Jul 29 20:51:21 UTC 2011
D: main.c: Found 2 CPUs.
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in Valgrind mode: no
D: main.c: Running in VM: no
D: main.c: Optimized build: yes
D: main.c: All asserts enabled.
I: main.c: Machine ID is 7bb222b94ea449cbf9b9de9d4cbc71b9.
I: main.c: Session ID is 7bb222b94ea449cbf9b9de9d4cbc71b9-1316444917.880310-994022178.
I: main.c: Using runtime directory /home/dan/.pulse/7bb222b94ea449cbf9b9de9d4cbc71b9-runtime.
I: main.c: Using state directory /home/dan/.pulse.
I: main.c: Using modules directory /usr/lib/pulse-0.9.22/modules.
I: main.c: Running in system mode: no
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.
```and the third is [here]("http://www.alsa-project.org/db/?f=dc5510286620cd1c69117c803e18a8543174b1ea").

Again, thanks a ton.

---

### Post by lidex on 2011-09-19
You're welcome. Let me know if any more issues arise.

---

