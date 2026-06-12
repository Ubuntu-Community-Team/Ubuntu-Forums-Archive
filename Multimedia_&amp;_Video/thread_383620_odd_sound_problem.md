---
title: "odd sound problem"
date: 2007-03-13
forum: Multimedia &amp; Video
---

### Post by click4851 on 2007-03-13
never did get sound working as well as I would have liked, I have no sound when using Firefox for Soundclick or Youtube or Yahoo Video or MySpace but Streamtuner works okay. When I call for Alsamixer it says no mixer elems found? Alsa was installed by Synaptic and the codec plugins for Firefox by Automatix.

---

### Post by ssavelan on 2007-03-14
AMD64 or i386?

---

### Post by click4851 on 2007-03-14
AMD64, and I tried reloading alsa using the purge option from the HowTo at the top of this section. I use Firefox as my browser so i reloaded the mplayer plugins from automatix, and just to make sure its not a browser problem, I also loaded Opera from automatix as well. Same problem, embedded audio only is a no go. I don't believe its a browser issue or a codec issue, I think somehow alsa is either confused or broken. I am using a Creative Labs Sound blaster 16.bit  Gamer 5.1 with the on board sound disabled in BIOS. Alsa should be using the  emuk10k1 driver for the module.

---

### Post by ssavelan on 2007-03-14
> **click4851 said:**
> AMD64, and I tried reloading alsa using the purge option from the HowTo at the top of this section. I use Firefox as my browser so i reloaded the mplayer plugins from automatix, and just to make sure its not a browser problem, I also loaded Opera from automatix as well. Same problem, embedded audio only is a no go. I don't believe its a browser issue or a codec issue, I think somehow alsa is either confused or broken. I am using a Creative Labs Sound blaster 16.bit  Gamer 5.1 with the on board sound disabled in BIOS. Alsa should be using the  emuk10k1 driver for the module.

I think that the problem is due to 64-bit firefox; I am not sure.  Can you play like... a google video or other flash media with sound; or, absolutely no embedded sound whatsoever?

---

### Post by click4851 on 2007-03-14
whoops, back up, reverse it, i386 version of Ubuntu (firefox), my bad. Also made sure I had flash 9 plugin.

---

### Post by click4851 on 2007-03-14
firefox was using an mplayer plugin for this, so just to eliminate that I uninstalled it, and let VLC do the heavy lifting. Just doesn't seem to make a difference. I still think somehow ALSA has a hand in whats not right.

---

### Post by click4851 on 2007-03-15
I noticed that I can't pull up alsamixer or alsaconf, alsactl seems to be there. I'm going to check for modules that are loaded and see if any conflict. Should be emuk10k1 related and nothing else I believe. My fear is hotpug is going out and loading modules whatever it finds.

---

### Post by ssavelan on 2007-03-16
> **click4851 said:**
> I noticed that I can't pull up alsamixer or alsaconf, alsactl seems to be there. I'm going to check for modules that are loaded and see if any conflict. Should be emuk10k1 related and nothing else I believe. My fear is hotpug is going out and loading modules whatever it finds.

Are you working with the ALSA that ubuntu comes with or source from the ALSA-project?

---

### Post by click4851 on 2007-03-16
that would be Ubuntu ALSA.  This is weird, this morning I saw that synaptic had a gnome alsa mixer package ala gui style vs the ncurses alsamixer utiltity that doesn't work for me. Heres the weird part, the mixer shows a device "SigmaTel STAC9708.11" and has at least 20 sliders and 14 switches. Now I don't know if my Creative Sound Blaster 16 bit 5.1 uses this, I due know that the driver should be "emuk10k1" which is also the chipset dsp of the board. When I google sigmatel STAC9708.11,  I did find an email from the ALSA Sourceforge maling list:

Sigmatel STAC9708/011
From: <fmoraes74@ne...> - 2004-06-17 19:44
On ALSA 1.0.4, there was a control called Sigmatel on the mixer for the emu10k1x STAC9708/011 mixer.

Now, on ALSA 1.0.5a, the control is gone even though I could use it to control the volume of one of the hardware buffers.

Any reason for the removal? If the removal is needed, should I add it back?

Francisco


This at least confirms that this Sigmatel STAC9708.11 that the gnome gui mixer is showing me could or does represent the correct device. I have played with most of the sliders and some or all of the switches and still can't hear any embedded audio from videos or standalone songs through my browser. Very strange, I'm really hoping the powers that be would focus on a sound server and eliminate/simplify the whole thing, it should "just work". To me this is more important than Compiz or Beryl.

---

### Post by ssavelan on 2007-03-16
> **click4851 said:**
> I'm really hoping the powers that be would focus on a sound server and eliminate/simplify the whole thing, it should "just work". To me this is more important than Compiz or Beryl.

Sound is my top priority as well.  Fortunately or not, we may be the powers that be to a certain extent.

I would set-up another mint partition of Ubuntu and try to install the latest ALSA drivers from source.  Is this the only soundcard that you are using?

---

### Post by click4851 on 2007-03-16
it is, and I could do that. I was hoping to upgrade to feisty first, in vain hope that it would all just work. Have you heard of PulseAudio?

---

### Post by ssavelan on 2007-03-16
> **click4851 said:**
> it is, and I could do that. I was hoping to upgrade to feisty first, in vain hope that it would all just work. Have you heard of PulseAudio?

You can go ahead and get a copy of feisty... a few weeks ago it was still not friendly enough for me.  You could make another partition and try Feisty or Xubuntu and try a few strategies out without tangling your only install.

I haven't heard of PulseAudio............searching.........loading..............

[http://en.wikipedia.org/wiki/PulseAudio]("http://en.wikipedia.org/wiki/PulseAudio")

oh yeah!  That's what Feisty is set to use instead of ESD?

---

### Post by click4851 on 2007-03-18
I might not sure what Feisty will use, I just wish they would pick one and be done with it, can you say too many API's. Certainly sounds interesting, I think if they would just focus on one, any of them could be good. PulseAudio sure has the potential.

---

### Post by ssavelan on 2007-03-18
Well, OSS is like a legacy, right?  And ALSA is the device drivers.  ESD is like the newer OSS.  I think everything is getting progressively better.  (like oss does not allow for audio multitasking much- like you are on windows kinda, "device is in use")

---

### Post by click4851 on 2007-03-19
I would generally agree, but after OSS was recognized as needing replacement, it was like everyone reinvented the wheel and we got ESD, ALSA, JACK and ArtS, oh and keep some OSS like features while your at it. Frustrating.

---

### Post by click4851 on 2007-03-19
Spent some time seeing what the common thread was with my sound problem and all the places I missing the audio, either from video or audio alone, involve Flash Player 9. Thats as far as I am, great waiting all this time with FP 7, no FP 8, and now FP 9 appears to be fubar.

---

### Post by click4851 on 2007-03-19
Ok fixed....first see here:

[http://www.ubuntuforums.org/showthread.php?t=343025&highlight=flash+player+no+sound](http://www.ubuntuforums.org/showthread.php?t=343025&highlight=flash+player+no+sound)

now the first part went ok, but I had no /etc/environment file to edit so I kept reading:


1) Create the file .asoundrc in your home directory: sudo vi .asoundrc
2) Paste this into it and save:

Quote:
pcm.!default {
type plug
slave.pcm "dmix"
}
3) Edit the environment file: sudo vi /etc/environment
4) Paste this into it and save:

Quote:
FIREFOX_DSP=aoss


and here is the bit that applies to me apparently, from a later post, the part about editing /etc/firefox/firefoxrc for aoss:

Open terminal, and enter:
Code:

sudo aptitude install alsa-oss

Wait for the install to complete, before typing:
Code:

gksudo gedit /etc/firefox/firefoxrc

A file will open, and in the file you will see:
Quote:
FIREFOX_DSP=&#8221;none&#8221;
Change this to:
Quote:
FIREFOX_DSP=&#8221;aoss&#8221;

Good luck !

and that appears to have resolved that, just wish I knew what did that, probably some firefox update. Oh well theres the end, for now, of that sad story, hope it helps someone. Thanks ssavelan for your help.

---

