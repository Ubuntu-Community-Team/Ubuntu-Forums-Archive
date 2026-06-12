---
title: "PulseAudio has suddenly broken. I have tried uninstalling and reinstalling it all."
date: 2018-02-07
forum: Multimedia Software
---

### Post by dscottboggs on 2018-02-07
First, to preface, I don't run a standard distro. I'm on Ubuntu 17.10, but I use i3 window manager with XFCE bar and all the standard stuff handpicked rather than bundled. So, if you think that's a stupid thing to do and I should just go install Gnome or Plasma, I get that, you don't have to help. I was just hoping someone could help me with this pulse audio issue I'm having.

I use pulseaudio with pavucontrol to manage my sound. However, about a week ago, I was poking around in *htop* and noticed that gnome-shell was taking up 5% of my memory, but I wasn't in gnome, I was in i3. So I killed it, not realizing that it was also the bit that does the login and all that. This prompted me to immediately remove all the gnome stuff from my system left over from the base Ubuntu install, and replace it with lightdm.

However, I still can't control my volume. The audio works, as it's set now, but I can't adjust the volume or which output is being piped to. When I open pavucontrol, I get the following error, on a blank, white screen:

[IMG]http://i.imgur.com/dIW5uul.png[/IMG]

If I run *start-pulseaudio-x11* like it recommends, I get this error:

```

scott@living-room-tower ~ » start-pulseaudio-x11 
Connection failure: Connection refused
pa_context_connect() failed: Connection refused

```

I also got the same error when I ran the command outside of the X11 environment.

---

### Post by #&amp;thj^% on 2018-02-07
that's not good.:(
Just a quick check here, will you try this:
```
pulseaudio -k
```
Now this:
```
pulseaudio --start
```
Post any errors from the last command back here.

---

### Post by dscottboggs on 2018-02-07
pulseaudio -k gives me:

```
E: [pulseaudio] main.c: Failed to kill daemon: No such file or directory
```

And pulseaudio --start -vv gives me:

```

D: [pulseaudio] conf-parser.c: Parsing configuration file '/etc/pulse/client.conf'
D: [pulseaudio] conf-parser.c: /etc/pulse/client.conf.d does not exist, ignoring.
E: [pulseaudio] main.c: Daemon startup failed.

```

---

### Post by #&amp;thj^% on 2018-02-08
Thanks for the good information you provided. ;)
How do you log in, how do you start your X session, outputs of:
```
pulseaudio -vvv

```
Mine shows:
```
pulseaudio -vvv
I: [pulseaudio] main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
D: [pulseaudio] core-rtclock.c: Timer slack is set to 50 us.
D: [pulseaudio] core-util.c: RealtimeKit worked.
I: [pulseaudio] core-util.c: Successfully gained nice level -11.
I: [pulseaudio] main.c: This is PulseAudio 11.1
D: [pulseaudio] main.c: Compilation host: x86_64-pc-linux-gnu
D: [pulseaudio] main.c: Compilation CFLAGS: -march=x86-64 -mtune=generic -O2 -pipe -fstack-protector-strong -fno-plt -Wall -W -Wextra -Wno-long-long -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing -Wwrite-strings -Wno-unused-parameter -ffast-math -fno-common -fdiagnostics-show-option -fdiagnostics-color=auto
D: [pulseaudio] main.c: Running on host: Linux x86_64 4.15.1-2-ARCH #1 SMP Sun Feb 4 22:27:45 UTC 2018
D: [pulseaudio] main.c: Found 4 CPUs.
I: [pulseaudio] main.c: Page size is 4096 bytes
D: [pulseaudio] main.c: Compiled with Valgrind support: no
D: [pulseaudio] main.c: Running in valgrind mode: no
D: [pulseaudio] main.c: Running in VM: no
D: [pulseaudio] main.c: Optimized build: yes
D: [pulseaudio] main.c: FASTPATH defined, only fast path asserts disabled.
I: [pulseaudio] main.c: Machine ID is Sniped by me..
I: [pulseaudio] main.c: Session ID is c2.
I: [pulseaudio] main.c: Using runtime directory /run/user/1001/pulse.
I: [pulseaudio] main.c: Using state directory /home/me/.config/pulse.
I: [pulseaudio] main.c: Using modules directory /usr/lib/pulse-11.1/modules.
I: [pulseaudio] main.c: Running in system mode: no
E: [pulseaudio] pid.c: Daemon already running.
E: [pulseaudio] main.c: pa_pid_file_create() failed.

```
The last 2 errors on mine are expected due to pulse already running.
And if you would be kind enough to show the output of:
```
ls -l ~/.config/pulse

```

---

### Post by dscottboggs on 2018-02-13
My apologies for not replying sooner, I was on vacation.

I believe we have found a clue, thanks to your suggestion to run "pulseaudio -vvv". There are some bright red errors towards the end, which point to an issue with inotify:

```

E: [pulseaudio] module-udev-detect.c: You apparently ran out of inotify watches, probably because Tracker/Beagle took them all away. I wished people would do their homework first and fix inotify before using it for watching whole directory trees which is something the current inotify is certainly not useful for. Please make sure to drop the Tracker/Beagle guys a line complaining about their broken use of inotify.

```

I don't have Tracker or Beagle, and I don't know what those are, but the bit about "watching whole directory trees" gave me the tip-off I needed. I recently installed [uLauncher]("https://github.com/Ulauncher/Ulauncher"), which depends on pyinotify. I'm guessing that uLauncher is hogging inotify in an ineffective attempt to watch for newly installed programs in the various folders which would contain the appropriate .desktop files. I'll have to look into implementing a different directory watch system for uLauncher or drop back to i3's default launcher.

Marking this as solved.

---

### Post by #&amp;thj^% on 2018-02-13
Great detective work. :)
Good Job!;)
Kind Regards

---

### Post by rabiyajamal45 on 2018-02-15
Thanks every one for your useful support





[Multi Recharge Software]("http://etop.red-apple.in")

---

### Post by Yellow Pasque on 2018-02-16
[https://github.com/Ulauncher/Ulauncher/issues/51](https://github.com/Ulauncher/Ulauncher/issues/51)

---

