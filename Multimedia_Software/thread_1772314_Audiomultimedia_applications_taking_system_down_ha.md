---
title: "Audio/multimedia applications taking system down hard"
date: 2011-05-31
forum: Multimedia Software
---

### Post by RansomOttawa on 2011-05-31
Hi all.  For the past several weeks, I've encountered problems with nearly every media player I've used: a few minutes after starting the application, the entire system freezes, requiring a power cycle to get it going again.

I first experienced this problem with Rhythmbox, then Banshee and gtkpod.  On the guess that this was a problem with GTK-based players, I switched over to Amarok, which remained stable. Unfortunately, Amarok's support for my iPod Nano 3G is tenuous, to say the least, so I then tried out Clementine.

Unfortunately, now Clementine has also started crashing on startup.  This has sort of blown my hypothesis that GTK audio apps were at fault, but KDE-based ones were immune. It may be related to checking/updating my music library, but it wasn't happening before yesterday - and I had *none* of these problems before about March or April.

I've tried searching the forums and the Net at large, but haven't found any description of the same symptoms elsewhere, so I finally decided to bite the bullet and ask.  I've also attempted to diagnose what processes might be causing the problem by running top in a terminal window and waiting for a crash, but either I couldn't see any pattern, or couldn't replicate the crashes on purpose (you know what they say about a watched pot . . .)

This isn't happening with Totem, so at least I can play media, as long as I can find it on the filesystem.

My system is a 1.8 GHz AMD Athlon XP with 1 GB RAM, running Lucid with the 2.6.32-32 kernel and GNOME.  My music library is fairly large - several thousand tracks, mostly MP3, with parts residing on two different hard drives.

I'm an Ubuntu user of a few years (started in 2007/08 with Gutsy), but a newbie to the forums as well as the more technical aspects of managing a Linux install, so have patience!  I'll be glad to try and supply any further details that might be helpful. I'm at work and the afflicted PC is at home, so any further tinkering will have to wait until tonight.

---

### Post by RansomOttawa on 2011-06-07
Pardon the bump, but is there anyone who can provide some input on this issue?  Even a helping hand in the right direction, if not a full solution?

Judging from my system monitor, the crash is preceded by CPU activity ramping up for a few seconds before the whole system locks up.  However, it doesn't appear that the system load is particularly high - at times, this machine has had a system load average of 25+ and, although it was unusable, eventually it settled down again.

Unfortunately, running Clementine or Rhythmbox from the command line provided no helpful information either.

Any hints?
Some other information I could offer, via some command-line tool or utility I haven't considered?
Known bugs in some library shared by media apps, that cause some sort of runaway process?
Another forum (or section on this forum) better suited to inquiries of this type?

This problem is getting really aggravating, and I'd like to resolve it, if possible, in some way other than reinstalling my OS or reverting to Windows . . .

Many thanks!

---

### Post by BicyclerBoy on 2011-06-08
Can you monitor the system RAM & swap space ?
Are you running out of space on your system drive ?

Have you compiled/installed non-std versions of ffmpeg/libav etc ?

But your problem does seem linked to the startup/collection database/rescan..
Possibly one of the system folders is full (log files or some other junk?).

You could check some of the system log files for clues../var/log/example_logfile

---

### Post by RansomOttawa on 2011-06-08
> **BicyclerBoy said:**
> Can you monitor the system RAM & swap space ?

By adding those graphs to the System Monitor applet, or did you have something a little more informative in mind (that I might not be aware of)?

> Are you running out of space on your system drive ?

Not the system drive - it's a 40-gig partition that's only about half full.  My home partition is constantly giving me warnings about only having 2 GB free, however (it tends to hold at 2-3 GB of free space).

> Have you compiled/installed non-std versions of ffmpeg/libav etc ?

No, nothing that wasn't just installed from the repos via Synaptic.

> But your problem does seem linked to the startup/collection database/rescan..
Possibly one of the system folders is full (log files or some other junk?).

You could check some of the system log files for clues../var/log/example_logfile

Since I generally don't pay any attention to the logs or clean them out (I'm more an end-user than a power user), I suppose this is a possibility.  I'll see what comes up next time it crashes.

Thanks!

---

### Post by BicyclerBoy on 2011-06-09
Long shot..
You could try Clementine using the alsa audio device (not pulse).
Clementine is like Amarok where you can configure the audio playback device & override system wide settings.

You could keep a terminal open & keep re-running 
dmesg

Check contents of 
/var/log/Xorg.0.log     (this session)

kern.log syslog  (has history)

I find that totem utilises lots of CPU when browsing into a folder with a lot of video recordings (700GB) & tries to make thumbnails..just un-installed in the end.

---

### Post by lidex on 2011-06-09
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

No joy, try this:
```
pkill pulseaudio; sleep 2; pulseaudio -vv
```
Then post output here.

---

### Post by Yellow Pasque on 2011-06-10
Note: all of the players you list use gstreamer for audio output (even clementine). You could try a newer version of gstreamer: [https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

---

### Post by RansomOttawa on 2011-06-12
Hi, and thanks for the replies. Sorry I'm not responding as frequently - but with the system apparently crashing on a moment's notice, you'll probably understand if I leave it alone and find another one to do something productive on. :)
> **Temüjin said:**
> Note: all of the players you list use gstreamer for audio output (even clementine). You could try a newer version of gstreamer: [https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

I'm glad you spotted this commonality -  I wouldn't, as the workings of Linux's sound architecture is a complete mystery to me.  I'm going to start with this suggestion, and update gstreamer.  Failing that, I'll work with pulse - though, since the crash happens before I even play any media, I suspect that is the less likely suspect.

Here's the most recent entries in syslog (which occured about 5 minutes before the crash, so it's possibly not helpful - I've redacted the MAC address but left everything else as-is):

```

Jun 12 15:02:39 deepthought wpa_supplicant[1086]: WPA: Group rekeying completed with xx:xx:xx:xx:xx:xx [GTK=TKIP]
Jun 12 15:02:39 deepthought NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> group handshake
Jun 12 15:02:39 deepthought NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed

```

And here's what clementine sent to stdout/stderr before it hung the system: 

```

Couldn't load icon "clementine-panel" 
Couldn't load icon "clementine-panel-grey" 
virtual bool GnomeGlobalShortcutBackend::DoRegister()

```

I'll try upgrading gstreamer and see what happens. It looks like adding the PPA to my repos will upgrade me from 0.10-28 to 0.10-34.

---

### Post by RansomOttawa on 2011-06-12
OK, it doesn't appear that gstreamer is directly to blame: the upgrade didn't change clementine's behaviour.  Neither did plan B:

> **lidex said:**
> Try resetting your pulse configuration.

. . .

No joy, try this:
```
pkill pulseaudio; sleep 2; pulseaudio -vv
```
Then post output here.

No joy.  Here's the output from pulseaudio -vv:

```


I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: core-rtclock.c: Timer slack is set to 50 us.
D: core-util.c: RealtimeKit worked.
I: core-util.c: Successfully gained nice level -11.
I: main.c: This is PulseAudio 0.9.21-63-gd3efa-dirty
D: main.c: Compilation host: i486-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pipe -Wno-long-long -Winline -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing=2 -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: main.c: Running on host: Linux i686 2.6.32-32-generic #62-Ubuntu SMP Wed Apr 20 21:54:21 UTC 2011
D: main.c: Found 1 CPUs.
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Running in VM: no
D: main.c: Optimized build: yes
D: main.c: All asserts enabled.
I: main.c: Machine ID is dd04440455c048df0c39f4c24bdc76b9.
I: main.c: Session ID is dd04440455c048df0c39f4c24bdc76b9-1307910304.558631-133216115.
I: main.c: Using runtime directory /home/ransom/.pulse/dd04440455c048df0c39f4c24bdc76b9-runtime.
I: main.c: Using state directory /home/ransom/.pulse.
I: main.c: Using modules directory /usr/lib/pulse-0.9.21/modules.
I: main.c: Running in system mode: no
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.

```

Clementine is still rescanning my music on startup: it gets about 25% into the scan, then hangs the system.  I think this is part of the problem - only thing is, I can't keep clementine running long enough to turn library scanning off at startup . . . *sigh* (Or switching over to ALSA, for the same reason.)

---

### Post by lidex on 2011-06-13
Media is on two hard drives? Are they both mounted when loading your database?

---

### Post by RansomOttawa on 2011-06-13
> **lidex said:**
> Media is on two hard drives? Are they both mounted when loading your database?

Oh, man. I am *really* glad you asked me that question.

The drive (/dev/sdb2) is always mounted to /media/Temp via fstab, and symlinked to ~/user/Music/Temp, since it contains only audio files. (As the name suggests, it's a temporary solution to a storage space problem, albeit one that I've been slow to fix.)

However, that may very well be completely irrelevant.  I just tried to open a Nautilus window to look at that drive's contents, and that *too* caused a system crash.

I think my problem is with hardware, not software: possibly sdb2 is on the verge of failure.  I've seen no error messages threatening me of an imminent drive crash. And since it contains nothing but audio files, maybe trouble only happens when an audio application tries to access it.

To test this hypothesis, I unmounted sdb2 from /media/Temp immediately after reboot, and fired up Clementine.  To my utter surprise, it scanned the remaining music library without a hitch.  Rhythmbox also seems to be working OK, updating the removed songs in its database (albeit in its usual slowpoke fashion).

So I think there's a good chance I've got not a problem with multimedia apps, but with hardware that only the multimedia apps need to access, which is why I didn't clue in sooner.  I'll pull the drive, then keep an eye on it for a couple of days and see what happens.

Many thanks for the suggestions!

Newbie question: Is it good form to mark the thread "Solved" even if the solution is unrelated to the forum topic?

---

### Post by Yellow Pasque on 2011-06-13
> **RansomOttawa said:**
> Newbie question: Is it good form to mark the thread "Solved" even if the solution is unrelated to the forum topic?
Yes. This saves people time and they can skip your thread to troubleshoot other issues.

---

### Post by RansomOttawa on 2011-06-13
Thanks.  If I'm satisfied that my woes are indeed caused by the imminent demise of my older hard drive, I'll do so.

---

### Post by RansomOttawa on 2011-06-17
After 3 days without the offending HDD, the system is still running smooth as glass.  So I'm chalking this one up to an undetected equipment failure.  Bit of a wild goose chase, but at least the mystery's solved.

Thanks everyone!

---

