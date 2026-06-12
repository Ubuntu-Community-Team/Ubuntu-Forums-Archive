---
title: "No sound on HP Pavilion dv6-1030us running 9.04"
date: 2009-06-19
forum: Multimedia Software
---

### Post by ertayone on 2009-06-19
Hello,

I'm a complete Linux noob. I've gotten everything on my laptop (HP Pavilion dv6-1030us) working so far aside from the sound.

I've consulted the [Ubuntu documentation Sound Troubleshooting page]("https://help.ubuntu.com/community/SoundTroubleshooting") and here's what I've found out:


[LIST]
[*]I checked Volume Control and the volume is turned up and the speaker isn't muted
[*]The system appears to recognize my sound card. **aplay -l** outputs this information:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
[*]My sound modules appear to be installed. **find /lib/modules/`uname -r` | grep snd** outputs a long list of .ko files in the /lib/modules/2.6.28-13-generic/kernel/sound/ directory.
[*]My sound card appears to be physically installed and recognized by my hardware. **lspci -v | less** lists this "Audio device:"
```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company Device 3627
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at da500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
```
[*]Here's [the ALSA project's reference page for my sound setup]("http://www.alsa-project.org/db/?f=15b8b4bae1ec5946f8d67257aec592ab2eabb5c0") and (I believe) [the corresponding git repository page]("http://git.alsa-project.org/?p=alsa-kmirror.git;a=blob;f=Documentation/ALSA-Configuration.txt;h=5c08d96f407cb2afc95836ae987963afd371bc7e;hb=d511cb39d1cc52cbaa86b0ad7df5d462508e80d9") for my driver version, 1.0.18rc3. (I'm not sure why the driver version is a release candidate rather than plain old 1.0.18, the same as in the documentation. I downloaded my Ubuntu release from the official website yesterday.)

My reference page lists my ALSA module as snd_hda_intel and my soundcard codec as IDT 92HD75B3X5. The author of the documentation has found a section to match up with his codec in the git repository page, but I have not.
[/LIST]
Where should I go from here?

Thanks in advance

---

### Post by ertayone on 2009-06-19
EDIT: Nevermind, I uninstalled and reinstalled Ubuntu so now we are back at Square A, which is to say, ignore this reply :-)

---

### Post by ertayone on 2009-06-20
The problem seems to be with the Intel Corporation 82801I (ICH9 Family) audio device, which is incompatible with ALSA. I followed [this guide]("http://ubuntuforums.org/showthread.php?t=1043568"), but it ended up fouling up everything. When I restarted alsa:
```
killall pulseaudio
```Here's what happens when I use **sudo alsa force-reload**:
```
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/chris/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/chris/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).
```And here's what happens when I use **pulseaudio -D**:
```
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
E: main.c: Daemon startup failed.
```Now when I use **aplay -l** it outputs this:
```
aplay: device_list:217: no soundcards found...
```I'm totally clueless. Is my ALPA shut off forever now?

---

### Post by ertayone on 2009-06-20
Good news, everyone!

[IMG]http://img35.imageshack.us/img35/8559/goodnewsfarnsworththumb.jpg[/IMG]

Nallen00's instructions in [this thread](http://ubuntuforums.org/showpost.php?p=7299632&postcount=60) got my sound working at long last. Seems to be the key for everyone with a dvX.

---

### Post by josevm on 2009-06-28
I've a HP HP dv4-1204TU whose sound card specifications match with yours. There is no sound in Ubuntu 9.04.I tried the steps in your last thread and configured latest ALSA  snapshot. But when i give, \

 	 	sudo gedit /etc/modprobe.d/alsa-base 
the output file is a blank page.
Can you help me out of this

---

### Post by XmaskX on 2009-06-30
since 9.04 the file is called /etc/modprobe.d/alsa-base.conf

---

### Post by schnack on 2009-07-02
Same problem (no sound at all) with HP Pavilion dv6 1014el running 9.04 (same sound card, Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)... I tried almost every solution I found in the web, also editing /etc/modprobe.d/alsa-base.conf with different options... is there somebody in the world that have a solution...?

---

### Post by aadx on 2009-07-02
Schnack,
Maybe it takes away some pain knowing that you are not alone with the kind of problem you have.
I have a HP Pavillion T3260 DX17 desktop.
Last week I installed Ubuntu 9.04 as single OS on my computer.
First I could not print with my Canon MP600. At last, problem "solved" by telling Ubuntu it is a different printer.
Secondly I could not hear sound. Then I noticed that with the volume turned up to max I could hear sound, though very soft and somewhat distorted. The volume control works. Therefore I think the endstage amplifier works fine too and the volume control receives a to small input signal from the (digital) pre-amplifier or pre-soundprocessor. 
Anyway, I tried everything, amongst which every piece of advise I found in these Ubuntu fora, but the problem remained. 
Untill installation of Ubuntu, under Windows, my computer created perfect sound. Therefore I think the hardware is OK. Someone on these fora suggested that there might be a mis-connected pin. I rather think that the sound control (volume/amplitude) software is inproper or is supplied with a to weak (digital) signal.

I hope a programmer can have a look at the audio control software.

Aad van der Arend

---

### Post by schnack on 2009-07-02
Thank you Aad,
maybe the problem is really the compatibility between the sound card and ALSA. Somebody in the italian forum said me that in the bug's list of Ubuntu (??) there is also our problem... so, maybe some programmer will solve it (I hope!)... (but another guy told me that the same sound card works in his pc, even if I don't know if he has a hp).
So, let's wait... meanwhile I must keep also windows.
With all my attempts I got the only result that my system now doesn't see my sound card any more; but in any case I've never heard any kind of feeble sound.
Thank you again...! Bye!

---

### Post by bruno.vitorino on 2009-09-29
I was almost pulling my hair out because of this issue!! But finally someone sharing my pain found the solution to this problem.

I have a HP dv6 1220sp, and now the sound is working great, both speakers and headphones!

Thanks!

---

