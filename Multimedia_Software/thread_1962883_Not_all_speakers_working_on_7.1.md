---
title: "Not all speakers working on 7.1"
date: 2012-04-21
forum: Multimedia Software
---

### Post by Another Monkey on 2012-04-21
I have a bit of an odd issue with surround sound.
Running 10.10 (yes I know I need to upgrade) with a SB X-FI XtremeMusic card (emu20k1) and Creative Inspire T7900 speakers. ALSA version 1.0.23.

I've configured the system correctly (I think) to use 7.1, but neither side-right nor side-left function.

I've swapped the speakers around and their cables to check they are OK (they are).
I've swapped the cables around from the sub-woofer (which acts as the hub) around to check the cabling to the PC is OK (it is).
I've fiddled around in alsamixer and all the outputs/volumes look good.
I set the "default-sample-channels" in pulse/daemon.conf to 8; that had no effect.
No matter what, the speakers plugged into side-right/left do not work.  The other 5 speakers and the woofer work well.

Anyone got any trouble shooting tips?

Alsa [dump here]("http://www.alsa-project.org/db/?f=53d6e38123dee70f5ac41733b36815bf2fa7f304")

---

### Post by Another Monkey on 2012-04-22
OK, a few things need added to the troubleshooting list I think.

Items required:
1) Torch
2) Magnifying glass
3) Brain

Switch item 1 on, and in conjunction with item 2 carefully inspect the ports on the back of your card.  Some Creative Labs cards (like the X-Fi XtremeMusic) are colour coded (orange, black, green and gray).  The ports on the back of the sub-woofer are similarly colour coded.

Or so you would think.

By applying item 3 to the mix, you will discover that the gray port on the back of the card is not a speaker out port and does not correspond to side-speaker in of the sub-woofer, even though they are the same colour.  It is in fact a microphone input port.  A further clue is that the sub-woofer cable has 3 jacks on one end and 4 on the other (it's the extension cable that is 4-4).

Further more, on the sub-woofer itself the right speaker ports are on the left, and the left speaker ports are on the right.  Nice!

Once all this is sorted, the product works as advertised.

Your brain, never geek without it!

---

