---
title: "On board Nvidia gfx + sound = broken in 8.04.3 &amp; 9.04; Sound incredibly garbled."
date: 2010-01-11
forum: Multimedia Software
---

### Post by Gilthanaz on 2010-01-11
Hi all!

I have an issue with a box that ran "okay" so far on Kubuntu 8.04 but due to a recent HDD failure, i decided to set it up fresh on 8.04.3

As i did so, i found that enabling the proprietary Nvidia-glx driver causes 2 things:
1. The sound is horribly garbled. As in, your ears get cancer
2. Graphics are "laggy", drawing of windows and so on is incredibly slow - actually so slow that you can watch them as they are drawn.

I've spent now 2 weeks daily on search engines and reading thread over thread in about 200 different forums. Right now iam a bit desperate to get this fixed, tried everything i could find on the net and wasted hours over hours of spare time. The bad thing is: If iam not able to fix this soon, the poor box will be infected with windows :(

Well, here some more facts (Iam not near the box so i cant post dmesg/lspci/etc. at the moment):

1. Audio sounds perfect if the default (vesa?) driver is loaded. I would be happy with that driver, but 1024x768 on a 24" screen really hurts and iam not sure if even the 2d acceleration would work, possibly causing simple things like flashmovies not to run at all. Also, as far as i know vesa does not support higher than that. 

2. After a clean install of 8.04.3, enabling the nvidia driver and restarting X, the sound is horribly garbled.

3. After a clean install of 9.04, same as above

4. After a clean reinstall of 8.04, enabling nvidia driver and restarting X, sound is not-so-bad-but-still-garbled

5. The problem also happens if i put soundcards in the PCI slots and disable the on-board soundcard, with the exact same results. Works until nvidia driver is enabled, then => broken (tested with SB Live 5.1, Ensoniq PCI Soundcard, SB 64)

Appearently this is a rather known issue of some on-board chipsets (by Nvidia?). At least that is what i could read of the countless posts of this problem on a bazillion of forums. Unfortunately, all the possible 20 solutions, none worked for me. I've tried using the intel instead the nvidia driver (snd_intel). I've tried alternative hardware, but only for the soundcard as i dont have any spare PCI-E GFX cards left. 

Has anyone here ever heard of this problem and can probably give me a pointer in the right direction? I also thought of an old-school "shared IRQ" issue, but unfortunately the cheap BIOS on this box does not allow manual ressource management :(

If you need any information to help me, please let me know what ... and i'll get you that as soon as iam home from work and back at the little bugger of a box :)

KR,
-G

Edit:
Also, i would like to stick to 8.04.3 and rather not use 9.04, as KDE4 was - imho - adopted way too early and is unfortunately not even close to the stability and speed of KDE3.

---

### Post by Gilthanaz on 2010-01-11
Doublepost and *bump* :)

Iam home from work now and wired the box up again. So if anyone is up to help me, tell me what info you need and i'll issue the commands and post them as fast as i can.

And as long as no one helps me here, back to destroying the fresh installation again with random changes that might or might not fix something ;)

- G

Edit:

Here is 'sudo lspci -v', the audio part:
<source>
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
        Subsystem: Elitegroup Computer Systems Unknown device 2609
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
        Memory at fdff8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
        Capabilities: [6c] HyperTransport: MSI Mapping
 </source>


[B]Edit:
Something very interested happened. I noticed that when i lower the screen resolution from 1600x1200 to 1280x1024, the sound is way better. So i tried lower resolutions. Well, the lower the resolution, the less artifacts i have on sound playback.
[/B]
Does that make sense to anyone?

---

### Post by Gilthanaz on 2010-01-12
*bump* 

Anyone? :cry:

---

