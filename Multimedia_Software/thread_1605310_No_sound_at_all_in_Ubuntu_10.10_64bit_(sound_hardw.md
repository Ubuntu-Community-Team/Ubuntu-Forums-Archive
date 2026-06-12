---
title: "No sound at all in Ubuntu 10.10 64bit (sound hardware not loaded)"
date: 2010-10-25
forum: Multimedia Software
---

### Post by Meatknight on 2010-10-25
Hi everyone,

I am a bit at a loss here and could need some help. After several years of having flawlessly running Ubuntu installations, I purchased a new pc and installed  10.10 on it.

Everything works fine with the exception of sound - no sound cards get loaded. They do get recognized though. I have onboard sound as well as hdmi sound on my ATI graphics card. Problem occurs on my installation as well as when I boot from a live cd.

I am posting this because I already posted a bug report to launchpad a few weeks ago but with no results up to this day: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/660488](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/660488) I have attached all requested information there (alsa script reports, dmesg outputs) for everyone to check out who is willing to help me here.

On a curious sidenote, there is no sound problem at all when booting from a fresh Fedora 13 live cd and sound works fine as well in Windows7. So I dont think that my hardware is damaged or malfunctioning.

Not sure if this is the correct subforum as my launchpad bug was retagged as kernel related. If this post does not belong here, feel free to move it somewhere more fitting.

Kind regards,
Meatknight.

---

### Post by johnmay on 2010-10-25
same o same o

Sound card shows up in lspci: 

[FONT=monospace]0a:00.0 PCI bridge: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG PCI to PCIe Bridge
0b:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG


However occasionally it won't register at all. No sound, and when I attempt to watch videos, my screen blacks out.

As above, 64 bit 10.10 release, and working hardware.

Any suggestions would be great!


[/FONT]

---

### Post by lidex on 2010-10-25
*Meatknight:*
What is the make/model of this PC?
Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by hxcjonnysniper on 2010-11-19
symptom script /usr/share/apport/symptoms/audio.py crashed:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport/ui.py", line 54, in thread_collect_info
    package = symb['run'](report, ui)
  File "/usr/share/apport/symptoms/audio.py", line 28, in run
    package, card = soundcard_query(report, ui)
  File "/usr/share/apport/symptoms/audio.py", line 206, in soundcard_query
    for card in open('/proc/asound/cards'):
IOError: [Errno 2] No such file or directory: '/proc/asound/cards'

what do i do now?

---

