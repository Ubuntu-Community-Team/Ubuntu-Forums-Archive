---
title: "Breezy: No sound on a Via 8237 sound chip."
date: 2005-10-24
forum: Multimedia &amp; Video
---

### Post by Choco on 2005-10-24
**EDIT** - This is no longer a problem. Don't read unless you're just absolutely bored.

The title of this thread is a bit of a lie. 

It's true that I have no sound... unless my PCM and Master volumes are all the way up. When they are, system sounds, XMMS, and other things crackle and pop, but never produce any real understandable sound. Anything less than max volume causes no sound to be output.

In Multimedia Systems Selector, testing the default sink (on all modes-ALSA, ESD, OSS) produces several rhythmic clicks, then a steady beep noise. Testing the default source causes the program to crash and force quit.

Here's another funny kink in all this. When my volume is all the way up, and I log in (after rebooting or after a simple log out), I hear the Ubuntu startup sound with the synths and the nature sounds for a maximum of two seconds. After that, nothing but pops and clicks until I log in once again.

--

Now, I have gone through countless steps to get this working with no changes in my situation. Trying to use the viaudiocombo driver, downloading the ALSA driver packages and installing them from the terminal, etc. Synaptic shows my alsa packages are up-to-date, as well (1.0.9b-4) with libsdl1.2debian-alsa installed as well.

I've fiddled with the Ubuntu mixer and alsamixer with no changes.  The machine is correctly detecting my setup as a VIA 8237 with a VIA1617A chip. The chip is on a Micro-ATX board MSI P4MAM2-V

My head hurts from all I've tried so far, and I'm not yet willing to break down and install the only Sound Blaster Live card I own just for Linux sound.

Oh, one more thing: I have another harddrive set up in this box that has Windows XP Pro installed on it. The MB's sound chip has no problems in Windows at all.

Any ideas? If you need more specifics, tell me the commands to run and what text to paste.

---

### Post by camj on 2005-10-24
Out of curiosity whats your dmesg output

---

### Post by Choco on 2005-10-25
Well, I was going to post it, but... there appears to be no need. I didn't change anything, but sound seems to be working just fine, now O.o Very, VERY strange.

In fact, the moment I found out it was working fine, I loaded up the main theme for The Elder Scrolls: Oblivion ;P

[http://www.elderscrolls.com/downloads/downloads_music.htm](http://www.elderscrolls.com/downloads/downloads_music.htm) <~ Oh noes, shameless plug!

Thanks for reading this crazy tale.

---

