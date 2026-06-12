---
title: "I'm having some of the weirdest problems with my sound..."
date: 2013-08-03
forum: Multimedia Software
---

### Post by impinball on 2013-08-03
I have sound output perfectly fine in all the testing for if the sound drivers, etc. are working, but I still am having issues adjusting sound volume. I'll try to explain it as best as I can.

[LIST]
[*]My volume icon is showing as being muted (three dashes). On the other hand, I can play sound through Rhythmbox and the command [FONT=courier new]speaker-test[/FONT], which indicates that it isn't a problem with the sound driver being completely dysfunctional.
[*]I tried to troubleshoot PulseAudio to see what was wrong with it, and here is basically what happened:
[/LIST]
[INDENT=2]I run the following commands (denoted by Command here) and get the following output (denoted by Output).

Command: [FONT=courier new]pulseaudio --check[/FONT]
Ouput: (nothing)

Command: [FONT=courier new]killall pulseaudio[/FONT]
Output: [FONT=courier new]pulseaudio: no process found[/FONT]

Command: [FONT=courier new]sudo rm -rf /tmp/.pulse*[/FONT]
Output: [FONT=courier new][sudo] password for <user>:[/FONT]
(no further output--success)

Command: [FONT=courier new]rm -rf ~/.pulse*[/FONT]
Output: (nothing--success)

Command: [FONT=courier new]pulseaudio -D[/FONT]
Output: [FONT=courier new]E: [pulseaudio] main.c: [COLOR=#ff0000]Daemon startup failed.[/COLOR][/FONT]

Command: [FONT=courier new]pulseaudio -vvvv[/FONT]
Output: (This is a bit long...)
[FONT=courier new]I: [pulseaudio] main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: [pulseaudio] main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: [pulseaudio] core-rtclock.c: Timer slack is set to 50 us.
D: [pulseaudio] core-util.c: RealtimeKit worked.
I: [pulseaudio] core-util.c: Successfully gained nice level -11.
I: [pulseaudio] main.c: This is PulseAudio 3.0
D: [pulseaudio] main.c: Compilation host: x86_64-pc-linux-gnu
D: [pulseaudio] main.c: Compilation CFLAGS: -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security -Wall -W -Wextra -pipe -Wno-long-long -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: [pulseaudio] main.c: Running on host: Linux x86_64 3.8.0-26-generic #38-Ubuntu SMP Mon Jun 17 21:43:33 UTC 2013
D: [pulseaudio] main.c: Found 2 CPUs.
I: [pulseaudio] main.c: Page size is 4096 bytes
D: [pulseaudio] main.c: Compiled with Valgrind support: no
D: [pulseaudio] main.c: Running in valgrind mode: no
D: [pulseaudio] main.c: Running in VM: no
D: [pulseaudio] main.c: Optimized build: yes
D: [pulseaudio] main.c: FASTPATH defined, only fast path asserts disabled.
I: [pulseaudio] main.c: Machine ID is [128-bit ID].
I: [pulseaudio] main.c: Using runtime directory /run/user/<user>/pulse.
E: [pulseaudio] core-util.c: [COLOR=#ff0000]Home directory not accessible: Permission denied[/COLOR][/FONT][/INDENT]
[INDENT=2]
I, then, following some troubleshooting steps online (URL: [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)), download pavucontrol, and run it ([FONT=courier new]pavucontrol[/FONT]), finding this message after entering the command:
> [I]Connection to PulseAudio failed. Auto Retry in 5s
[/I][I]
In this case this is likely because PULSE_SERVER in the Environment/X11 Root Window Properties or default-server is misconfigured.
[/I][I]This situation can also arrise when PulseAudio crashed and left stale details in the X11 Root Window.
[/I]*If this is the case, then PulseAudio should autospawn again, or if htis is not configured you should run start-pulseaudio-x11 manually.*

I read this message and try the following command: [FONT=courier new]start-pulseaudio-x11[/FONT], with the following output:
[FONT=courier new]Connection failure: Connection refused
pa_context_connect() failed: Connection refused[/FONT]
[/INDENT]



[LIST]
[*]The real issue I have right now (as far as I've seen) is that the PulseAudio daemon isn't wanting to start. I can get my speakers to play things through Rhythmbox and that terminal test ([FONT=courier new]speaker-test[/FONT]), but I have no control over volume whatsoever. Also, in Settings>Sound, the sections "Output Volume", "Input Volume" (in Settings>Sound>Input), and "Alert Volume" (in Settings>Sound>Sound Effects) are grayed out (slider bar and on/off switch both on all of them) and the button "Test sound" is non-functional. The boxes labeled "Play sound through" and "Record sound through" are blank.
[/LIST]

I have done a ton of Google searches, searched these forums quite a bit, among other things, and found nothing to help me in this massive dilemma.

---

### Post by tgalati4 on 2013-08-03
Is your username in group audio?

```
grep audio /etc/group

```

tgalati4@tpad-Gloria7 ~ $ grep audio /etc/group
audio:    x    :29     :    pulse,herb3538,tgalati4

---

### Post by Yellow Pasque on 2013-08-04
No, don't put your user in the audio group (pulseaudio accesses the device directly, not the user). The problem is the permissions on your home directory.
```
ls -la /home
```

---

### Post by impinball on 2013-08-12
Do I only need to change the user folder, or do I need to change anything else?
Here is the output of that command:
```

<user>@<computer>:~$ ls -la /home
total 21
drwxrwxrwx  1 root root 4096 Aug  9 19:10 .
drwxr-xr-x 24 root root 4096 Aug  3 21:21 ..
drwxrwxrwx  1 root root 8192 Aug 12 16:11 <user>
drwxrwxrwx  1 root root    0 Jul 31 12:57 $RECYCLE.BIN
brwxrwxrwx  1 root root 8, 6 Jul 27 14:23 sda6
drwxrwxrwx  1 root root 4096 Aug  8 19:52 System Volume Information

```
There are two things to note:
[LIST=1]
[*]I am running a dual boot of Windows 7 and Ubuntu 13.04 (that should explain the $RECYCLE.BIN and System Volume Information folders). A side note is that I am looking for a way to make a temporary admin for Windows to be able to mount the NTFS partition (mounted as /home here) to C:\Users instead of F:, but that is slightly off topic here.
[*]I have already run [FONT=courier new]chown -cR <user> /home/<user>[/FONT] successfully to take ownership of my /home/<user> directory. My remaining question is if I need to chown anything else.
[/LIST]

---

### Post by impinball on 2013-08-13
Also, I still have the problem.

---

### Post by impinball on 2013-08-13
> **tgalati4 said:**
> Is your username in group audio?

```
grep audio /etc/group

```

tgalati4@tpad-Gloria7 ~ $ grep audio /etc/group
audio:    x    :29     :    pulse,herb3538,tgalati4
No.

---

### Post by Yellow Pasque on 2013-08-13
```
drwxrwxrwx  1 root root 8192 Aug 12 16:11 <user>
```

Is this still the output? Your home directory is still owned by root.

---

### Post by impinball on 2013-08-20
Yes, and that is even after the initial run of [FONT=courier new]chown -cR <user> /home/<user>[/FONT] and a later reboot.

**EDIT:** This still persisted after another run of that command. After running the same command as sudo, here's the result of [FONT=courier new]ls -la /home[/FONT]:
```
total 21drwxrwxrwx  1 root root 4096 Aug 17 13:11 .
drwxr-xr-x 24 root root 4096 Aug  3 21:21 ..
drwxrwxrwx  1 root root 8192 Aug 20 16:04 <user>
drwxrwxrwx  1 root root    0 Jul 31 12:57 $RECYCLE.BIN
brwxrwxrwx  1 root root 8, 6 Jul 27 14:23 sda6
drwxrwxrwx  1 root root 4096 Aug  8 19:52 System Volume Information
```
Note the lack of effect had by chown, regardless of privileges. Keep in mind, this is on an NTFS partition (actively used by Windows).

---

### Post by digitalattorney on 2013-12-01
Any luck on resolving the PulseAudio issue? I'm having the same problem... Xubuntu 13.04,  3.8.0-33-generic, i686

BUT

I don't believe I have the Home directory issue that "impinball" is having:

jonpaulr@Neoi5:~$ ls -la /home
total 16
drwxr-xr-x  4 root          root          4096 Nov 30 16:45 .
drwxr-xr-x 24 root          root          4096 Nov  9 08:49 ..
drwxr-xr-x 19 administrator administrator 4096 Nov 30 16:57 administrator
drwxr-xr-x 57 jonpaulr      jonpaulr      4096 Dec  2 08:53 jonpaulr


This seems to be an extremely rare issue, with extremely little support on it anywhere on the net. Any suggestions?

---

