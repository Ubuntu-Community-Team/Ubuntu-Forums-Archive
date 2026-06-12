---
title: "Sound stuttering with si7018"
date: 2006-07-27
forum: Multimedia &amp; Video
---

### Post by fragmental on 2006-07-27
I have a serious sound stuttering problem.  The sound is an integrated sis 7018 chipset.  I have tried changing to asoundrc file to change the dmix settings. I have tried switching the output source from oss to alsa to esd.  I have tried killing esd.  I have tried a number of things.  It seems like the stuttering is the pcm sound but it might be midi too. I'm not completely sure.

I have no idea what to do besides going out and buying a new sound card, and that's not really an option right now.

This probably started with breezy and continues with dapper.

Anyone have any suggestions?  I may try setting up polyp audio or setting up also to use ESD's software mixer.  I'm not sure it will really help though, s I'm pretty sure I can already play multiple sound files, they just stutter.

---

### Post by fragmental on 2006-07-27
Seems to stutter even more now that I have been trying to fix it, as if in defiance.

---

### Post by fragmental on 2006-07-27
and I think midi skips the same way pcm does.

---

### Post by fragmental on 2006-08-03
I fixed it!!!

I tested the audio some more and realised it only does it with some programs.  Those programs were using sdl.

I ran "export SDL_AUDIO=esd" before running the programs (scummvm and ppracer) and the stuttering was gone.

After that I added that line to the "/etc/environment" folder.  I have no rebooted yet to see if that works.  I could probably have also ran "putenv("SDL_AUDIODRIVER=esd")".

This would probably work for other crappy sound chipsets too.

Edit:  Oh yeah, I forgot to mention that I added some sound libraries too.  Specifically, and possibly most important, I added the libsdl1.2debian-all.  However, I also added alsa-oss and I might have added libesd-also0 as well as some other gstreamer/alsa/oss/sdl packages.  I really don't remember now.

---

### Post by Hyuuga on 2006-08-03
Wow, i had a problem with sound stuttering and that fixed it :D

---

### Post by fragmental on 2006-08-18
midi doesn't seem to work in scummvm.  I'm not sure if it ever did, I just know it doesn't now.  I have tried solutions from here [http://www.ubuntuforums.org/showthread.php?t=58859&highlight=midi+snd-seq](http://www.ubuntuforums.org/showthread.php?t=58859&highlight=midi+snd-seq) and here [http://www.ubuntuforums.org/showthread.php?t=205449&highlight=midi](http://www.ubuntuforums.org/showthread.php?t=205449&highlight=midi) with no luck so far.

---

### Post by fragmental on 2006-08-21
Well, after a little experimentation I found out that I could get midi to work if I switch back to alsa but it was really bad.  A lot of the instruments wouldn't play and the ones that did didn't sound right.  That and the same stuttering problem I was having before also seemed to affect to the midi.

So after some searching I set scummvm up to play fluid synth and I set up fluid synth with the instructions here [http://ubuntuforums.org/archive/index.php/t-8736.html](http://ubuntuforums.org/archive/index.php/t-8736.html).  I also used the same soundfont I had already set up.

Hope anyone else having problems with scummvm might find this useful

---

### Post by ringmaster on 2006-11-16
Thank you!!! I am having the same problem with the same sound chipset (integrated on a SiS630).
I will tell SDL for this possible bug (this could be a widely used chipset on low-budget PCs and a lot of users could be affected).

---

### Post by Koloth57 on 2007-12-08
I would be happy with stuttering. <grin>

I've just installed Ubuntu and it seems to see the SI7018, but I may not have a driver.  What driver package are you using?

---

### Post by fragmental on 2007-12-09
I really don't remember what driver. I'm pretty sure it's just whichever one automatically loads from the kernel.  I might have had to load a driver myself, but I really doubt it. I think, in ubuntu, I've only had to do that for an old isa sb16 on one of the first ubuntu releases.

You may have to mess with the sound settings.  There may be a couple different drivers you can choose from in the sound volume settings.  If you have no sound you might want to try unmuting things and switching between them.  There's also some alsa command that unmutes everything.

I haven't booted the particular computer with the chipset into ubuntu in a long time, because of games.  It's my girlfriend's computer now.  

If you are not 100 percent sure that sound is turned on in the bios, that could be a good thing to check also.

---

### Post by Koloth57 on 2007-12-15
If you do boot it up again, please do a 

     sudo lshw -C sound

where the last line, configuration, should list the driver.  Here's what I get for my non-working driver:

sudo lshw -C sound
  *-multimedia            
       description: Multimedia audio controller
       product: SiS PCI Audio Accelerator
       vendor: Silicon Integrated Systems [SiS]
       physical id: 1.4
       bus info: pci@0000:00:01.4
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Trident4DWaveAudio latency=64 maxlatency=24 mingnt=2 module=snd_trident


Thanks in advance for your help.

Take Care,
Koloth

---

### Post by fragmental on 2007-12-16
I realised that the reason I hadn't booted back into ubuntu in such a long time is because I installed windows after ubuntu and didn't bother to reinstall grub.  So, I did that and booted in to Ubuntu, ran lshw- C sound, and ran the upgrade.  Afterwards the computer started acting strange and now it won't even get past "checking nvram" in the bios.  So, I'll have to wait until I can figure out what the problem is before continuing.

I don't have the exact output from lshw to copy and paste, but I did check it against what you have.

Everything was exactly the same except the *-multimedia had a number, because I have two devices(one is a video capture card), and mine did not have the "module=snd_trident" bit at the end.

I was running 7.04 when I ran lshw.  I've run a couple different releases though and always had sound.

The output could mean that you're running a module where I'm not, but I don't know.  It could just be a version difference or something.  The motherboard is a pcchips model.  The model number is something like m810lr.

If running a sound program doesn't just output errors, then I would check whether it's trying to play with alsa or oss emulation and try switching and checking levels.

I hope that helps.  If not, then it could be a while before I could be of any more help.  This computer is somewhat dead for the moment.

---

