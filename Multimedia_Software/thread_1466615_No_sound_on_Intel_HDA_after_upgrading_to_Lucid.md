---
title: "No sound on Intel HDA after upgrading to Lucid"
date: 2010-04-30
forum: Multimedia Software
---

### Post by coolfrood on 2010-04-30
Hi,

I have no sound on my machine after upgrading to Lucid.  Looking at other discussion threads, it seems to be an ALSA problem.  If I boot back into an older kernel (2.6.31 from Jaunty), the sound works, but the NVidia driver doesn't, so I have to boot into 2.6.32-21.  As per other threads, I have upgraded to 1.0.22.1 of ALSA.

I suspect it might have something to do with this change in the kernel:

```
http://kerneltrap.org/mailarchive/git-commits-head/2010/1/26/22623
```

Because if I look at the contents of /proc/asound/card0/codec#0 for the two kernels, I see this in 2.6.31:


```
Node 0x21 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x0221402f: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x2, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=04, enabled=1
  Connection: 2
     0x0c* 0x0d

```

whereas in 2.6.32, I see this:
```
Node 0x21 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x0221402f: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x2, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=04, enabled=1
  Connection: 2
     0x0c 0x0d*

```

Note the choice of connection (0x0c vs. 0x0d)

Any ideas as to how to fix this?

Thanks.

---

### Post by jacksonpollack on 2010-04-30
I also have an Intel HDA card. I upgraded to Lucid from Karmic, where the sound worked just fine. Now there is no sound at all.
The sound control applet disappeared too. I can get it back... but that changes nothing, still no sound.

---

### Post by rldsoftware on 2010-04-30
What worked for me, i installed the pulseaudio volume control tool. When i started it i saw that my volume meter was moving, so it produced sound but didn't output it.

When i opened the configuration tab, it showed the 'internal audio settings' where set to 'Analog stero output' which was correct.

I changed it to 'off', and then to 'Analog Stereo Output' again, and suddenly my audio was working.

Hopes that does it for you... 

Is this something to file a bug report for, and if so where do i do that?

---

### Post by doktorOblivion on 2010-04-30
Had the same issue, this worked for me.

This is BS.  It worked out-of-box in Jaunty, now it doesn't.  Lack of QA!!!  Or, it should be in the release NOTES.  TY.

---

### Post by dino99 on 2010-04-30
open /etc/modprobe.d/alsa.conf  

and add this line to end:

options snd-hda-intel model=auto

depend on the real model model=auto can be replaced with better alsa definition.

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

dont forget to install paprefs and gnome-alsamixer to thweak settings (apps sound)

---

### Post by jacksonpollack on 2010-05-01
Neither method worked for me.

With the pulseaudio volume control I can see the volume meter moving, but there's no output. The gnome volume contorl applet is gone too, not sure if that's a related problem. 

My sound has worked fine in Hardy, Intrepid, Jaunty and Karmic... 

Thanks ahead for any help anyone can provide.

---

### Post by kepreon on 2010-05-01
Same thing is happening to me.  I did an upgrade from Karmic to Lucid and my sound broke!  I was searching around and found one thing that did fix it:

```
alsactl init
```

I get the following output:

```
kevin@alpha:~$ alsactl init
Unknown hardware: "HDA-Intel" "SigmaTel STAC9205" "HDA:838476a0,102801f9,00100204" "0x1028" "0x01f9"
Hardware is initialized using a guess method

```

But then my sound works again.  I'm still missing the sound icon in the taskbar, though...

---

### Post by sammydee on 2010-05-01
What is the output of pulseaudio -vv?

---

### Post by kepreon on 2010-05-01
Because it's already running, it doesn't do all that much.

```
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: core-rtclock.c: Timer slack is set to 50 us.
D: core-util.c: RealtimeKit worked.
I: core-util.c: Successfully gained nice level -11.
I: main.c: This is PulseAudio 0.9.21-63-gd3efa-dirty
D: main.c: Compilation host: x86_64-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pipe -Wno-long-long -Winline -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing=2 -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: main.c: Running on host: Linux x86_64 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010
D: main.c: Found 2 CPUs.
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Running in VM: no
D: main.c: Optimized build: yes
D: main.c: All asserts enabled.
I: main.c: Machine ID is 6c433160ff0d9046e39a73f14aecf5a8.
I: main.c: Session ID is 6c433160ff0d9046e39a73f14aecf5a8-1272741525.232461-713244013.
I: main.c: Using runtime directory /home/kevin/.pulse/6c433160ff0d9046e39a73f14aecf5a8-runtime.
I: main.c: Using state directory /home/kevin/.pulse.
I: main.c: Using modules directory /usr/lib/pulse-0.9.21/modules.
I: main.c: Running in system mode: no
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.

```

I can kill pulseaudio and start it manually, but there's a lot of output, and then my sound breaks again until I reinit alsa.  Does alsactl init tell the system to use ALSA over PulseAudio?  Am I looking for anything in particular?  The only error I see is:

```
E: module-udev-detect.c: You apparently ran out of inotify watches, probably because Tracker/Beagle took them all away. I wished people would do their homework first and fix inotify before using it for watching whole directory trees which is something the current inotify is certainly not useful for. Please make sure to drop the Tracker/Beagle guys a line complaining about their broken use of inotify.
```

Thanks!

---

### Post by jacksonpollack on 2010-05-01
Ah, I have sound again!

I'm not sure why this worked, but I just went to sound preferences in gnome-volume-control (the regular notification area applet) and changed the settings under the "Input" and "Output" tabs, and then the sound managed to work. Nothing was selected for input, but I doubt that made a difference. For the output, I switched it from "Simultaneous output to Internal Audio Analog Stereo" to "Internal Audio Analog Stereo". What I don't understand is that when I change the setting back it still works just fine. Sounds like I had a similar problem to rldsoftware above, though a slightly different way of solving it.

I suppose this might be some bug related to the gnome-volume-control not being around by default. In Lucid the volume control only appears "indicator applet" area (which I hate since the icons are spaced out quite far from one another). In any case, you can run gnome-volume-control-applet to make it appear. Make a new entry in Startup applications with the command "gnome-volume-control-applet &" to make that appear permanently.

---

### Post by mpennell on 2010-05-01
alsactl init

This seems to have worked for me, at least for youtube (trying now...). Also still no "sound" option on menu list.

---

### Post by garvinrick4 on 2010-05-01
Seems like good idea to get back to fresh install.
Works for me most times.

sudo apt-get remove --purge alsa-base

sudo apt-get remove --purge pulseaudio

sudo get clean && sudo apt-get autoremove  

 sudo apt-get install alsa-base 

sudo apt-get install pulseaudio

---

### Post by ivotron on 2010-05-02
> **garvinrick4 said:**
> Seems like good idea to get back to fresh install.
Works for me most times.

sudo apt-get remove --purge alsa-base

sudo apt-get remove --purge pulseaudio

sudo get clean && sudo apt-get autoremove  

 sudo apt-get install alsa-base 

sudo apt-get install pulseaudio
thanks a lot man. This solved the problem on my Xubuntu 10.04

---

### Post by Sputnik82 on 2010-05-02
Reinstalling also worked for me but i lost the volume indicator in the toolbar

---

### Post by ajmfulcher on 2010-05-02
> **garvinrick4 said:**
> Seems like good idea to get back to fresh install.
Works for me most times.

sudo apt-get remove --purge alsa-base

sudo apt-get remove --purge pulseaudio

sudo get clean && sudo apt-get autoremove  

 sudo apt-get install alsa-base 

sudo apt-get install pulseaudio

This worked well for me too.

> **Sputnik82 said:**
> Reinstalling also worked for me but i lost the volume indicator in the toolbar

To get the volume indicator back, you'll need to do:
**sudo apt-get install indicator-applet**


In addition I re-added the ubuntu meta-packages, so (on UNR):
**sudo apt-get install ubuntu-desktop ubuntu-netbook ubuntu-netbook-remix**

For a standard ubuntu desktop, you'll only need to re-add the ubuntu desktop meta-package:
**sudo apt-get install ubuntu-desktop**

---

### Post by Manslen on 2010-05-03
I ran ```
pavucontrol
``` and under "output devices" there is a cryptic-looking button that is in fact mute. For some reason, it was pressed by default after the Lucid installation..

---

### Post by coolfrood on 2010-05-04
None of the options worked for me.  I can see the meters moving in pavucontrol, but I get no sound with any of the options discussed earlier.  My only guess is that the ALSA driver in the kernel has a bug.

```
$ alsactl init
Unknown hardware: "HDA-Intel" "Realtek ALC259" "HDA:10ec0269,102802da,00100100" "0x1028" "0x02da"
```

---

### Post by coolfrood on 2010-05-05
It turns out that my first suspicion was correct.  There is indeed a bug in the ALSA drivers for the ALC259 codec.  I was able to fix it by patching the linux-backports-modules-alsa-lucid-generic package and recompiling it.  I have filed a bug against it, so hopefully it'll get fixed upstream too.

[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/575793](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/575793)

---

### Post by lidex on 2010-05-05
> **coolfrood said:**
> It turns out that my first suspicion was correct.  There is indeed a bug in the ALSA drivers for the ALC259 codec.  I was able to fix it by patching the linux-backports-modules-alsa-lucid-generic package and recompiling it.  I have filed a bug against it, so hopefully it'll get fixed upstream too.

[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/575793](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/575793)

Did you try upgrading alsa to 1.0.23?

---

### Post by coolfrood on 2010-05-10
> **lidex said:**
> Did you try upgrading alsa to 1.0.23?

No.  Alsa 1.0.23 isn't available through lucid-backports and for now I don't want to go off of Ubuntu packages.

---

### Post by alexpercont on 2010-05-27
My case is the same.. the output of alsactl init is:

```

Unknown hardware: "HDA-Intel" "IDT 92HD75B2X5" "HDA:111d7608,103c308c,00100202 HDA:11c11040,103c1378,00100200" "0x103c" "0x308c"
Hardware is initialized using a guess method

```

Any suggestion about what to do to get sound back?

> **coolfrood said:**
> None of the options worked for me.  I can see the meters moving in pavucontrol, but I get no sound with any of the options discussed earlier.  My only guess is that the ALSA driver in the kernel has a bug.

```
$ alsactl init
Unknown hardware: "HDA-Intel" "Realtek ALC259" "HDA:10ec0269,102802da,00100100" "0x1028" "0x02da"
```

---

### Post by pjeeanah on 2010-06-06
Nothing of the above worked for me.

But I found a clue from the Fedora forums.

Add yourself to the "pulse" and "pulse-access" groups and reboot.

That worked for me.

NB You might have to unmute  sound

---

