---
title: "[SOLVED] Sound suddenly stopped working"
date: 2008-11-24
forum: Mythbuntu
---

### Post by Fonikar on 2008-11-24
I've just had the problem that my sound stopped working. I eventually got there myself, but I'll add the situation and fix here, just in case someone else has the same problem.

SYMPTOMS:
Sound working normally (Mythbuntu 8.04 upgraded to 8.10) using motherboard sound out of spdif. Everything working well. At some point, and I didn't notice when as I was doing a few bits with the system with my amplifier off, the sound stopped working. Nothing, wouldn't play through Mythtv or mythvideo (mplayer). Tried externally to mythtv by playing an audio track in vlcplayer, still nothing. 

Originally I thought it might be a hardware issue, so I booted up using my windows drive to test the hardware and it all checked out fine. So, back to Ubuntu. I found a few people had the problem that Ubuntu would suddenly stop with sound, but often rectified with a reboot. No such joy for me.

SOLUTION:
I went to Applications>Settings>Main Menu and selected Sound&Video in the left window and then enabled Volume Control in the right.
Then accessed Accessories>Multimedia>Volume Control and found that the master control was muted (red cross). One click on that and everything came back to life...perfect

I'm not sure why this happened, could well have been some shortcut key I was unaware of, but all solved now.

Hope it helps someone else save a bit of time :)

---

