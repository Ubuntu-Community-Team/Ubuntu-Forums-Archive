---
title: "Samsung SH-S222A optical drive locks up system"
date: 2010-10-27
forum: Multimedia Software
---

### Post by Objekt on 2010-10-27
The culprit is a Toshiba Samsung Storage Technology 222A CD/DVD RW drive, aka SH-S222A, sold under the Samsung brand.  It occasionally locks up my entire system when I'm ripping an audio CD to a *.toc/*bin image with Brasero.

I've had this happen with several different audio CDs, while ripping discs using both Imgburn under Windows XP and Brasero under Ubuntu 10.04.  The display freezes completely, the mouse cursor doesn't move, and I can't get any response to keyboard input.  Any sounds playing loop endlessly, repeating the last 0.5 sec or so before the cursor freeze.

Meanwhile, the hard drive activity light stays on, but the optical drive light does not.  I've let the system sit this way for several minutes, with no sign of change.  To recover, I must press the system reset button.

I ripped the same discs without incident, using my other optical drive.  It is a different brand, Lite-On, but otherwise similar to the Samsung drive: PATA interface, CD/DVD RW, etc.

Anyone else have the Samsung SH-S222A?  I'm wondering whether there is a bug in the drive's firmware, or I just have a defective drive.  It works for other things.  I can play audio CDs, access CD-ROMs, and rip audio CDs to individual tracks (rather than a disc image).  I can also rip DVDs.

Is there some way to recover my system when it locks up from drive misbehavior?  I haven't found a way so far.  I'm surprised that Ubuntu can be incapacitated so easily.

The SH-S222A has the most recent firmware revision, SB01.  [s]I tried to install the newer ID01 firmware from Samsung's website, but got a message that the installer couldn't find a "suitable" drive.  I take that to mean that the ID01 firmware is meant for a slightly different variant of the -S222A, perhaps one only sold overseas.[/s]

Yep, that's pretty much it.  My drive's customer code is BEBE.  Firmware ID01 is for drives with a different customer code.

Still don't understand why the drive locks up my system sometimes.

---

### Post by burpen on 2010-12-05
My CD/DVD drive is an NEC DVD-RW ND-3550A, but I experience a similar problem, and I'm thinking it could be related.

Any time I insert a non-blank disc into my CD/DVD-RW drive, the drive spins up as expected, but the disc never shows up in Nautilus, and maybe 30 seconds later, the system completely freezes and becomes unresponsive to any input. I can't bring it back with a control-alt-backspace or control-alt-f1, I just have to hit the reset button. This seems to be consistent with your issue.

It doesn't seem to matter what kind of media I put in the drive... everything I have tried (data and video DVDs mostly, IIRC) seems to lock it up. I mean, there could be something that *doesn't* freeze it, but I don't feel like sitting around having to repeatedly hard-reboot my computer to find out.

I have checked on several occasions, but nothing relevant can be found in my syslog after the hang occurs.

Note that this only happens with a non-blank CD/DVD. Strangely enough, if I insert a blank, I can burn it just fine, but I have to immediately eject it after the burn, because of course if K3B tries to verify the write, the system hangs.

I tried to find any bug reports/other forum threads about this issue but I only found a few, none of which had a solution (or at least a solution that worked):
[http://ubuntuforums.org/showthread.php?t=700804](http://ubuntuforums.org/showthread.php?t=700804)
[http://ubuntuforums.org/showthread.php?t=828390](http://ubuntuforums.org/showthread.php?t=828390)

FYI, my system specs are as follows:
Ubuntu 10.04 x86_64
2.6.32-25-generic

---

### Post by Objekt on 2010-12-06
Yikes, that's pretty bad.  Maybe we're experiencing a bug in the way Ubuntu handles optical drives?  Or possibly there is something specially broken about our particular drive models.  It's impossible to say, since no one else seems to have this problem.

Audio CDs seem to be a special case.  I've had my system lock up when trying to image them in Windows XP as well, using a different program (ImgBurn I think).

---

