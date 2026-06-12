---
title: "Sound worked before upgrades yesterday"
date: 2018-07-11
forum: Multimedia Software
---

### Post by SimpsonTruckDriver on 2018-07-11
Yesterday, sound worked fine (always works fine on Windows10), today nothing. No sound. In lspci, this is the audio info:

00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Kabini HDMI/DP Audio
        Subsystem: Hewlett-Packard Company Kabini HDMI/DP Audio
        Flags: bus master, fast devsel, latency 0, IRQ 45
        Memory at feb64000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [48] Vendor Specific Information: Len=08 <?>
        Capabilities: [50] Power Management version 3
        Capabilities: [58] Express Root Complex Integrated Endpoint, MSI 00
        Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd_hda_intel

0:09.2 Audio device: Advanced Micro Devices, Inc. [AMD] Device 157a
        Subsystem: Hewlett-Packard Company Device 8353
        Flags: bus master, fast devsel, latency 0, IRQ 46
        Memory at feb60000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [60] Power Management version 3
        Capabilities: [a4] PCI Advanced Features
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd_hda_intel

I tried using the steps on this [site from ItsFoss]("https://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/") and nothing worked. In Phonon Audio and Video Device Preference, it lists "Built In Analog Stereo" and "Built In Audio Digital Stereo (HDMI)", but clicking on either does nothing (no sound). In the Audio Hardware Setup, hitting many of the settings (mix and match) does nothing either. Like ItsFoss says, this is one of the biggest complaints about Kubuntu/Ubuntu, multimedia can be shut off with little warning and it takes a lot to get it to work again.

Any other ideas not listed in ItsFoss?

TS

---

### Post by SimpsonTruckDriver on 2018-07-13
*UPDATE*
I found a temporary "cure"... installed PulseAudio. That fixed it for a day. Now, it does not work, it says PulseAudio is installed but I have no way of restarting it. I can't kill it since it's not running, nor can I get it running with "pulseaudio -- start". I went into sound settings, every option I tried NO SOUND.

Again, if I go into Windows 10, sound works fine.

---

### Post by SimpsonTruckDriver on 2018-07-15
I am definitely getting frustrated at the lack of sound, while Windows 10 sound works fine. If I deleted KUbuntu (again) and instead installed Linux Mint, would that solve it once and for all? Since Alsa and Pulseinfo are troublesome, here is my [Alsa-Info]("http://www.alsa-project.org/db/?f=ebb6bbb16b54c1f4f2aba3ad40943898c28b0543"). And yes, I have done the "kill" and "force-reload" on both to no avail.

And here is the Pulseaudio -vv
> [FONT=monospace][COLOR=#000000]I: [pulseaudio] main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted[/COLOR]
I: [pulseaudio] main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: [pulseaudio] core-rtclock.c: Timer slack is set to 50 us.
D: [pulseaudio] core-util.c: RealtimeKit worked.
I: [pulseaudio] core-util.c: Successfully gained nice level -11.
I: [pulseaudio] main.c: This is PulseAudio 11.1
D: [pulseaudio] main.c: Compilation host: x86_64-pc-linux-gnu
D: [pulseaudio] main.c: Compilation CFLAGS: -g -O2 -fdebug-prefix-map=/build/pulseaudio-E
OwPuF/pulseaudio-11.1=. -fstack-protector-strong -Wformat -Werror=format-security -Wall -
W -Wextra -pipe -Wno-long-long -Wno-overlength-strings -Wunsafe-loop-optimizations -Wunde
f -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wforma
t-nonliteral -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmi
ssing-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -We
ndif-labels -Wcast-align -Wstrict-aliasing -Wwrite-strings -Wno-unused-parameter -ffast-m
ath -fno-common -fdiagnostics-show-option -fdiagnostics-color=auto
D: [pulseaudio] main.c: Running on host: Linux x86_64 4.15.0-23-generic #25-Ubuntu SMP We
d May 23 18:02:16 UTC 2018
D: [pulseaudio] main.c: Found 4 CPUs.
I: [pulseaudio] main.c: Page size is 4096 bytes
D: [pulseaudio] main.c: Compiled with Valgrind support: no
D: [pulseaudio] main.c: Running in valgrind mode: no
D: [pulseaudio] main.c: Running in VM: no
D: [pulseaudio] main.c: Optimized build: yes
D: [pulseaudio] main.c: FASTPATH defined, only fast path asserts disabled.
I: [pulseaudio] main.c: Machine ID is 68a1a28d73d54fc6a894eb12c4527309.
I: [pulseaudio] main.c: Session ID is 3.
I: [pulseaudio] main.c: Using runtime directory /run/user/1000/pulse.
I: [pulseaudio] main.c: Using state directory /home/toddsimpson/.config/pulse.
I: [pulseaudio] main.c: Using modules directory /usr/lib/pulse-11.1/modules.
I: [pulseaudio] main.c: Running in system mode: no
E: [pulseaudio] pid.c: [COLOR=#FF5454]**Daemon already running.**[/COLOR][COLOR=#000000][/COLOR]
E: [pulseaudio] main.c: [COLOR=#FF5454]**pa_pid_file_create() failed.**[/COLOR]
[/FONT]

TS

---

### Post by kazakore on 2018-07-17
Why was pulse audio not installed? You must have removed it as it is the default sound sever in Ubuntu (and most of Linux distros.) What are you trying to achieve wit having a non-standard audio setup? What do you mean by "Since Alsa and Pulseinfo are troublesome"?? You really need to explain what are actually trying to do, what steps you have done and what you want the final outcome to be!

---

### Post by sangamswadik on 2018-07-19
> **SimpsonTruckDriver said:**
> I am definitely getting frustrated at the lack of sound, while Windows 10 sound works fine. If I deleted KUbuntu (again) and instead installed Linux Mint, would that solve it once and for all? Since Alsa and Pulseinfo are troublesome, here is my [Alsa-Info]("http://www.alsa-project.org/db/?f=ebb6bbb16b54c1f4f2aba3ad40943898c28b0543"). And yes, I have done the "kill" and "force-reload" on both to no avail.

And here is the Pulseaudio -vv


TS
Hi,I seem to have the same problem would it be possible for you to post the solution( If you found one) ?

---

### Post by SimpsonTruckDriver on 2018-07-22
I wish I had a solution. But it just started working again. I guess Sound is a fickle beast, kinda like a cat. One day it works fine, another day it doesn't, another day it works.

TS

---

