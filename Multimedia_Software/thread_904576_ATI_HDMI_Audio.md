---
title: "ATI HDMI Audio"
date: 2008-08-29
forum: Multimedia Software
---

### Post by bml137 on 2008-08-29
I am having two problems.  The first one has a far higher priority and might solve the second one anyway.

I have a 780G mobo and am running Hardy mythbuntu.  I am also using the ATI fglrx driver.

Here is the issue:

About a 3rd of the time, the audio works.  The other two-thirds of the time, it does not.  I play a recording and if there is no audio, I back out of the recording and go back in.  I repeat the process until I get the audio.  I have recently found out that I can simply pause/unpause the recording instead of backing out.  If the audio is working and I pause the recording, the audio may not (most of the time) come back.

Maybe something isn't releasing the device or could there be a race condition between the video and audio?  I have absolutely no idea.  This is the case with SDTV and HDTV.  I have HDMI cables from Mythbuntu to the TV and the DVD player to the TV.  I also have a digital audio cable from the TV to the receiver.  There are no DVD issues.


The second and lower priority issue is with ESPN-HD (and possibly other channels).  It seems as though the audio is not going to the correct speakers or something and the volume is MUCH lower than any other station.  Again, DVD audio (5.1) works perfectly.  My thought is ESPN-HD is delivering real 5.1.

Thanks,
Brian

---

### Post by bml137 on 2008-09-04
I want to follow up on my original post.

I read somewhere that both of the issues I am experiencing may be a problem with the linux kernel/alsa version.  Someone stated that they had issues with 2.6.24 and that 2.6.26 solved it for them.

I upgraded from hardy to intrepid, which I was already running on my desktop.  This allowed me to go to 2.6.26 or 2.6.27.  I installed both, but the ATI drivers (fglrx) would not work on 2.6.27.  I upgraded everything but xorg (fglrx only works with xorg <= 7.3).  This included MythTV fixes.

The problem was not solved.  It actually got slightly worse.  Now I lose/gain sound when I skip 30 seconds while watching a recording.  Before, I only gained/lost sound when I paused/unpaused.  I wouldn't even lose it when I changed channels while watching LiveTV.

I was only able to get 2.6.26.5 though, and maybe a later 26 release fixes it, but is unavailable in intrepid.

---

### Post by bml137 on 2008-09-05
I have now confirmed that I cannot get fglrx working with linux 2.6.27 or xorg 7.4.  I am running linux 2.6.26 and xorg 7.3.

Also, yesterday's MythTV updates fixed the "it's even worse" problem I experienced.

I am still unable to consistently get sound and unable to hear even remotely decent sound on ESPNHD.

Does anyone have any clue was to why?  Thanks...

Brian

---

