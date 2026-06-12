---
title: "No sound Intel 8201DB-ICH4"
date: 2010-09-14
forum: Multimedia Software
---

### Post by james.euless on 2010-09-14
I am running Ubuntu 9.10.  I just noticed I am getting no sound at all from any source.  I have run through a lot of fixes and nothing has worked.  I know the hardware is ok since it works in Windows XP and Linux Mint.  Here is the sound card info:


ntel 8201DB-ICH4

   description: Multimedia audio controller
       product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=Intel ICH latency=0
       resources: irq:17 ioport:2000(size=256) ioport:2400(size=64) memory:f8400400-f84005ff memory:f8400600-f84006ff

Tried these already:
[How To Fix Sound Issues in Ubuntu 9.10 - How-To Geek]("http://www.howtogeek.com/howto/10964/how-to-fix-sound-issues-in-ubuntu-9.10/")

and

[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

Nothing.  I have worked with the alsamixer and config, but nothing comes out.  Any ideas?

If all else fails, I might pull a microsoft and do a fresh install.  Who do you back up just files and some setting without pulling in audio?

Update: I upgraded to 10.04 and whatever was causing the trouble came along.  Still no sound.  Is there anyway to detect software conflicts?

Update: Did a complete reinstall of 9.10 (I rather like that one).  The sound works fine.  The only thing I can think of is an update or software added caused the problem.  What I would like to see is a good way of back up your profile and installed software for cases where a reinstall become necessary.  Also, some sort of restore point would be nice.

---

