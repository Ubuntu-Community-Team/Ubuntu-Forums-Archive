---
title: "Skype + playing other sound = sound stops -- pulsaudio crashing?"
date: 2009-05-03
forum: Multimedia Software
---

### Post by raym0nd on 2009-05-03
[FONT="Lucida Console"][/FONT]
Package: skype 
Version: 2.0.0.72-0medibuntu4

Sound playback disappears completely if I play any sound file when Skype is running concurrently. My system is Kubuntu 9.04 jaunty on a Dell E521 AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ with HDA Nvidia integrated sound device (running on host: Linux x86_64 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009).

I have found a temporary solution which may be useful for others with a similar problem: 

1. Log out of KDE and log into a console.
2. Move the .pulse* files from your home directory into a temporary directory:
	$ mkdir ~/pulse_BAK
	$ mv -i ~/.pulse* ~/pulse_BAK
3. Restart the computer.
4. Delete `pulse_BAK` if sound comes back:
	$ rm ~/pulse_BAK

Source of suggestion to delete .pulse* files: [Bug #334319: Stale ~/.pulse/* entries causes inaudible sound after dist-upgrade from 8.10 to 9.04]:([https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/334319](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/334319))

---

### Post by lineinthesand on 2012-09-28
Moving the ~/.pulse directory solved the problem of other sound sources being stopped for me (skype 4.0.0.8, opensuse 12.2)

---

