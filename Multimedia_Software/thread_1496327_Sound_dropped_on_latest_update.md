---
title: "Sound dropped on latest update"
date: 2010-05-29
forum: Multimedia Software
---

### Post by MartinHansell on 2010-05-29
Hi,

My sound was working just fine after installing Ubuntu 10.04 as a clean install, but over the last few days "just dropped out".  I'm not sure if it's related to the latest update earlier this week, or the heavy electrical storm we had recently in sunny KL.

I've checked the basics (see below), and to all intents... it should be working - but it isn't.  And I haven't yet found any post with a conclusive guide I can use...  Anyone got any ideas?

Thanks.
Martin

**CHECKS I RAN**
[LIST=1]
[*]Sound Groups - OK
```
fgrep -ie 'audio' /etc/group
```[FONT=Courier New]audio:x:29:pulse,martin,root,hannah[/FONT]
Where the smilies are you should read x & p - but I can't figure out how to escape them.
:KS
[*]Sound card recognized
```
sudo aplay -l
```[FONT=Courier New]**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/FONT]
:KS
[*]Sound modules installed - seem to be...
```
find /lib/modules/`uname -r` | grep snd
```
A list of modules appeared.
:KS
[*]Sound card installed ok
```
lspci -v | less
```00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High
 Definition Audio Controller (rev 03)
        Subsystem: Intel Corporation Device e201
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f6bfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
:KS
[/LIST]

I was using [this post]("https://help.ubuntu.com/community/SoundTroubleshooting") to guide me but gave up at that stage because it looked like trying to fix things that couldn't possibly be broken as my system had been working just fine until a couple of days ago.

There are [other]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1481792") [posts]("http://ubuntuforums.org/showthread.php?t=789578") regarding sound but I cannot see conclusive answers here so don't want to play with my system without clear "guidance".  Hence this post.

---

### Post by MartinHansell on 2010-05-29
...looks like the new Creative speaker I bought today is the source of the fault!

---

