---
title: "System sounds not playing - other sound ok"
date: 2009-02-10
forum: Multimedia Software
---

### Post by Berduchwal on 2009-02-10
Hi
System sounds do not work properly. You can hear short noise but it quickly ends.

I have ESD as my default device for both multimedia and other sounds.

VLC, Amarok, Skype work correctly.

When I go to System>Preferences>Sound and play manually the same happens.

This is only recent issue it was ok before in 8.10

Following web page describes similar issue:
[http://forum.eeeuser.com/viewtopic.php?id=53864]("http://forum.eeeuser.com/viewtopic.php?id=53864")

but this is all I was able to find of the subject.

Can you please suggest what other test can I run to get to the bottom of the issue?

---

### Post by Berduchwal on 2009-02-13
I have located variety of web pages about sound issues but still no solution:
[https://wiki.ubuntu.com/DebuggingSoundProblems]("https://wiki.ubuntu.com/DebuggingSoundProblems")

[http://ubuntuforums.org/showthread.php?t=324113]("http://ubuntuforums.org/showthread.php?t=324113")

```

maleccy@maleccy-laptop:~$ aplay -l
**** Lista PLAYBACK urz&#261;dze&#324; ****
karta 0: Intel [HDA Intel], urz&#261;dzenie 0: ALC268 Analog [ALC268 Analog]
  Urz&#261;dzenia podrz&#281;dne: 1/1
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0

```

```
lspci -v | less

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Acer Incorporated [ALI] Device 011f
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at fc300000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

```

Where else can I check?

---

### Post by Berduchwal on 2009-02-28
I have noticed that the problem only appears after login as the initial sound that is played when login screen comes up works fine.

---

