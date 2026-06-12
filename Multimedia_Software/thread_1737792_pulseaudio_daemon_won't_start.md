---
title: "pulseaudio daemon won't start"
date: 2011-04-23
forum: Multimedia Software
---

### Post by pwabrahams on 2011-04-23
After my latest reboot, pulseaudio broke.  When I call **pavucontrol** I get an error window with the message "Connection failed: connection refused".  If I call pulseaudio from the command line, I get this:

Daemon startup without any loaded modules, refusing to work

During my last bootup I had a USB turntable plugged in.  At one point I got a message asking if I wanted the system to forget about certain input devices.  I don't remember what I did with that, but I would hope that any problems there (none were observable at that time) would clear up after a reboot.

How can I get my sound to come alive again?

---

### Post by lidex on 2011-04-23
Try removing your ~/.pulse folder.

---

### Post by pwabrahams on 2011-04-24
I tried removing ~/.pulse.  It made no visible difference.  I guess I have to provide some loaded modules -- but how?

---

### Post by lidex on 2011-04-24
Post these outputs:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```
```
pkill pulseaudio; sleep 2; pulseaudio -vv
```

Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by pwabrahams on 2011-04-25
Here's the result of executing the commands as requested:```
wa@pwa-K60IJ:~$ sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
[sudo] password for pwa: 
Specified filename /dev/dsp* does not exist.
Specified filename /dev/seq* does not exist.
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  pwa        1668 F.... kded4
                     pwa        1914 F.... kmix
                     pwa       10469 F.... alsamixer
                     pwa       16586 F.... audacity
/dev/snd/controlC1:  pwa        1668 F.... kded4
                     pwa        1914 F.... kmix
                     pwa       16586 F.... audacity
/dev/snd/pcmC0D0p:   pwa        1749 F...m knotify4
/dev/snd/pcmC1D0c:   pwa       16586 F...m audacity
/dev/snd/timer:      pwa        1749 f.... knotify4
pwa@pwa-K60IJ:~$ sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
[sudo] password for pwa: 
Specified filename /dev/dsp* does not exist.
Specified filename /dev/seq* does not exist.
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  pwa        1668 F.... kded4
                     pwa        1914 F.... kmix
                     pwa       10469 F.... alsamixer
/dev/snd/controlC1:  pwa        1668 F.... kded4
                     pwa        1914 F.... kmix
/dev/snd/pcmC0D0p:   pwa        1749 F...m knotify4
/dev/snd/timer:      pwa        1749 f.... knotify4
pwa@pwa-K60IJ:~$ pkill pulseaudio; sleep 2; pulseaudio -vv
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: core-rtclock.c: Timer slack is set to 50 us.
D: core-util.c: RealtimeKit worked.
I: core-util.c: Successfully gained nice level -11.
I: main.c: This is PulseAudio 0.9.22
D: main.c: Compilation host: x86_64-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pipe -Wno-long-long -Winline -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing=2 -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: main.c: Running on host: Linux x86_64 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 18:42:20 UTC 2011
D: main.c: Found 2 CPUs.
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Running in VM: no
D: main.c: Optimized build: yes
D: main.c: All asserts enabled.
I: main.c: Machine ID is d0cccc58e087a2964ecd082800000006.
I: main.c: Session ID is d0cccc58e087a2964ecd082800000006-1303621144.228647-440631156.
I: main.c: Using runtime directory /home/pwa/.pulse/d0cccc58e087a2964ecd082800000006-runtime.
I: main.c: Using state directory /home/pwa/.pulse.
I: main.c: Using modules directory /usr/lib/pulse-0.9.22/modules.
I: main.c: Running in system mode: no
I: main.c: Fresh high-resolution timers available! Bon appetit!
I: cpu-x86.c: CPU flags: CMOV MMX SSE SSE2 SSE3 SSSE3 
I: svolume_mmx.c: Initialising MMX optimized functions.
I: remap_mmx.c: Initialising MMX optimized remappers.
I: svolume_sse.c: Initialising SSE2 optimized functions.
I: remap_sse.c: Initialising SSE2 optimized remappers.
I: sconv_sse.c: Initialising SSE2 optimized conversions.
D: memblock.c: Using shared memory pool with 1024 slots of size 64.0 KiB each, total size is 64.0 MiB, maximum usable slot size is 65472
E: main.c: Daemon startup without any loaded modules, refusing to work.
I: main.c: Daemon terminated.
pwa@pwa-K60IJ:~$ wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
--2011-04-25 08:28:07--  http://www.alsa-project.org/alsa-info.sh
Resolving www.alsa-project.org... 77.48.224.243
Connecting to www.alsa-project.org|77.48.224.243|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh [following]
--2011-04-25 08:28:13--  http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh
Resolving git.alsa-project.org... 77.48.224.243
Reusing existing connection to www.alsa-project.org:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `alsa-info.sh'

    [  <=>                                                                                                             ] 27,247      72.1K/s   in 0.4s    

2011-04-25 08:28:16 (72.1 KB/s) - `alsa-info.sh' saved [27247]

ALSA Information Script v 0.4.60
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

Automatically upload ALSA information to www.alsa-project.org? [y/N] : y
Uploading information to www.alsa-project.org ...  Done!

Your ALSA information is located at 
Please inform the person helping you.


```
As you can see, no location was provided.  Please let me know if I've misunderstood your instructions and what I should do to correct that.

---

### Post by pwabrahams on 2011-04-25
On a second try, I got this URL: [http://www.alsa-project.org/db/?f=ffa75846f6f7a31253de3f3b628871b6e9f4e3ce]("http://www.alsa-project.org/db/?f=ffa75846f6f7a31253de3f3b628871b6e9f4e3ce")

Hope that helps!!

---

### Post by Yellow Pasque on 2011-04-25
Try resetting your pulseaudio configuration like this:
```
dpkg --purge --force-depends pulseaudio
sudo apt-get install pulseaudio

```

Also, I have a suspicion that Phonon is grabbing the alsa /devices for KDE system sounds, but I'm not sure.

---

### Post by KegHead on 2011-04-25
Hi!

Have you tried;

system...preferences..start up apps?

KegHead

---

### Post by pwabrahams on 2011-04-25
I tried purging and reinstalling pulseaudio as suggested.  Now I have no sound at all.  Phonon indicates that pulseaudio is now the only choice for output, and KDE asks me if I want it to forget about the USB audio devices because it thinks they can be removed.

---

### Post by Yellow Pasque on 2011-04-25
Call pulseaudio from the command line. It might not be set to autostart.

---

### Post by pwabrahams on 2011-04-25
Pulseaudio is definitely running:```
pwa@pwa-K60IJ:~$ pulseaudio
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.

``` Now audacity is able to see my USB turntable, but I still have utter silence, even when I run the phonon test.

---

### Post by Yellow Pasque on 2011-04-25
When you run pavucontrol, what happens?

---

### Post by pwabrahams on 2011-04-25
Pavucontrol, of course, has 5 tabs.  I assume the ones of interest are Output Devices and Configuration.  

For Output Devices, the first device is Internal Audio Analog Stereo, with port Analog Output.  The second device is PCM 2900 Audio Codec Analog Stereo.  Both levels are set at about 80% and are not muted.

For Configuration, the profile for both devices is Analog Stereo Duplex.

**Update:** I removed pulseaudio and my sound came back.  I wish I was able to use it, but I don't know how to get it to work.

---

### Post by SeijiSensei on 2011-04-25
You didn't tell us which version of Kubuntu you're running.  For me, pulseaudio didn't work reliably before 10.10 (Maverick).

---

### Post by pwabrahams on 2011-04-26
I'm running KUbuntu 10.10 Maverick, so it's the right version.

The trouble with sound problems is that there are so many interacting players that it's hard to know where the responsibility lies.  There's alsa, pulseaudio, phonon, and the applications such as amarok.  Plus the drivers.  And even, sometimes, the hardware.

Thanks for the help.

---

