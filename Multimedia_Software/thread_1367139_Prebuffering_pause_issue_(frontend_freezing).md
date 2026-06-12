---
title: "Prebuffering pause issue (frontend freezing)"
date: 2009-12-29
forum: Multimedia Software
---

### Post by Mrazek on 2009-12-29
Hello, I want to be more exact when solving my frontend freezing problem described here:
[http://ubuntuforums.org/showthread.php?t=1360030](http://ubuntuforums.org/showthread.php?t=1360030)

My hardware is:
- AMD Athlon II X2 @ 2.8 (mainboard Gigabyte MA770T-UD3P 770)
- 1 GB DDR3
- nVidia 7300 GS
- on-board sound card used (Realtek ALC 888 )
- TV card Pinnacle 310i (hybrid analog+DVB-T, SAA713x, TDA1004x)

Software: fresh installation of Mythbuntu 9.04 for AMD 64 with all updates installed.
There is no problem for me to set all settings in backend for both analog and digital parts of my TV card. After running LiveTV without no changes in frontend settings, analog TV runs about two seconds quicker than normal (including quicker "chipmunks" sound) and then waits about one second.
I read very carefully this troubleshooting site:
[Troubleshooting:Prebuffering pause - MythTV]("http://www.mythtv.org/wiki/Prebuffering_pause")
My symptoms are the same as described here (including error messages in mythfrontend.log - I can post it) so I try to react to advices there:
- CPU starvation? I think it's not my case (Athlon II X2 @ 2.8 is powerful enough for Mythtv)
- I/O wait? I have "Delete files slowly" checked all the time.
- Invalid/corrupt seek table? **I didn't test this issue, should I?**
- Audio issues? I thought this is my case and so I tried almost all settings in Fix part. **I don't know how to set Slim playback profile **but I tried to change a sound card (SB Live! 5.1) - without no impact to video and sound in LiveTV :-(
- Network I/O related issues: I don't use network storage(s)
- Network configuration? I think not.
- Kernel scheduler misconfiguration? I think in fresh installation is all OK?
- Failing hard drive? I think not. I'm using Seagate Barracuda 7200.10 (several months "old") and previously I tested Transcend SSD hard drive with the same results.

---

### Post by Mrazek on 2010-01-04
So I tried new hardware:
- MOBO Intel Little Fall 945GC (with Atom 230 single core @ 1,6)
- 512 MB DDR2
- the same Seagate Barracuda
- the same TV card Pinnacle 310i
 
There are some buffering errors in logs but it doesn't freeze at all(!). Tried both analog and DVB-T live TV.
Very strange. I'm going to try other TV card (Hauppauge 1110) with Gigabyte MOBO and also Intel Mount Olive N10 with Atom D510.

---

### Post by Mrazek on 2010-01-12
SOLVED: I used original HW (Gigabyte with AMD + 7300) plus 9.10 + 0.22.
I had to enter analog channels by hand (Channel search button in backend settings/inputs is disabled) and had to significantly increase signal timeout and tuning timeout for DVB-T before channel search in DVB-T part.
 
The only one problem is that switching from digital source to analog leads to black screen, have to kill frontend and start it again. But I didn't see logs nor discussions yet.

---

