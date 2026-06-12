---
title: "proprietary ati driver, help with memory allocation"
date: 2008-12-30
forum: Multimedia Software
---

### Post by fyra on 2008-12-30
> [INDENT][I]"Computer Freezes while using fglrx (UMA and SIDEPORT)

If after choosing fglrx as your driver in either xorg.conf or xfree86.conf files, the computer freezes and becomes unresponsive while trying to start X this may be the solution.

Some ATI cards have the ability to run in three modes: UMA, SIDEPORT, or a combination of both. UMA mode is that one in which the video card does not use its dedicated memory, but rather uses and shares the system memory. On the other hand, SIDEPORT mode is the one in which the card uses its own dedicated memory. And finally, the third mode is a combination of the previous modes in which the card uses both the system memory and its dedicated memory.

If your computer hangs, this settings may be where the solution lies. If your computer hangs, try using either UMA by itself or a combination of both. However, if you choose the combination, make sure that the UMA one is at least 128MB. In my case, I have SIDEPORT 128MB and 128MB UMA. If I choose any less for UMA, it does not work. This is definetly not an attractive solution since it compromises your systems performance. Hopefully, this will be solved very soon.

**On some systems, the BIOS screen may not offer a choice of UMA or SIDEPORT. In this case, you can try turning the amount of RAM dedicated to the video card down, from 128Mb to 64Mb for example."**[/I][/INDENT]

I am experiencing this problem, and read about the above solution at [http://wiki.cchtml.com/index.php/Troubleshooting#Computer_Freezes_while_using_fglrx_.28UMA_and_SIDEPORT.29]("http://wiki.cchtml.com/index.php/Troubleshooting#Computer_Freezes_while_using_fglrx_.28UMA_and_SIDEPORT.29")

I am using an Acer TravelMate 6592 notebook, with Radeon HD 2300 card. I have the proprietary ati driver installed as I cannot watch video files at all with the standard driver (totem, vlc and mplayer all close a second into playback.) I fixed this by enabling the proprietary driver, and fixed the subsequent screen flickering by disbling compiz.

Now, I get the occasional system freeze (always seems to happen while I'm typing a forum post, ha) and want to try the above solution to fix this. Unfortunately, my bios does not let me change any of the above that I bolded. THe card appears to be running in sideport mode, and I have no idea if I am able to change this another way or not.

Or if perhaps someone has another suggestion for the cause of the fault, and a solution?

---

### Post by fyra on 2009-01-02
Solved.. I think. So far it seems that turning off compiz has fixed the random freezing as well. Woo!

---

