---
title: "no sound in MythTV"
date: 2008-10-05
forum: Mythbuntu
---

### Post by AndrewStout on 2008-10-05
Hi folks--

I'm sure I'm not the first person to have this problem, but a few minutes of searching didn't get me anything.

I've got an Ubuntu 8.04 desktop box.  I recently installed a Hauppauge WinTV PVR-350 and a Hauppauge WinTV PVR-150, and then installed Mythbuntu following the instructions [here]("https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop").  I've got analog cable plugged into those cards (just the 350 at the moment, but...).  

When I select Watch TV in MythTV Frontend I get video, but no sound.

I can get video and sound out of the card in Windows, but the Windows WinTV software is terrible, and I want to use MythTV in linux.

I imagine this is a relatively elementary configuration problem, but I've always been a little puzzled by sound in linux.  Here's what I know:
- MythTV configuration has the sound output set to "default: ALSA" (although that's not verbatim, I don't have it in front of me at the moment).
- Sound generally works for me in other applications, e.g. Amarok.  Amarok uses the xine backend.  The amarok settings give "autodetect" as the sound driver, which isn't very helpful.
- System > Preferences > Sound is similarly unhelpful: most things are listed "autodetect"; test sounds work; the default mixer tracks device was lissted as Realtek ALC850 rev 0 (OSS Mixer), but changing it to the other option, NVidia CK804 (Alsa mixer) didn't seem to make any difference.
- sometimes when I play sound through flash in firefox (youtube, streaming audio), amarok can't get sound out until I quit firefox.  I assume this is unrelated to my MythTV problem, but I thought I'd mention it just in case.

Any help would be appreciated!
--Andrew

---

### Post by AndrewStout on 2008-10-05
I now have reason to believe the problem might not be in the front end.  If I do the following:

# /usr/bin/ivtv-tune -c [channel]
# cat /dev/video0 > /tmp/test_capture.mpg
(ctrl-c to stop capture)
# mplayer -vo xv /tmp/test_capture.mpg 

...the resulting file doesn't seem to have any audio (I also tried it with VLC, just to be sure).

Please advise.

---

### Post by Ronno6 on 2008-10-07
I had the same problem, fixed by going to Backend Setup > Capture Card Setup and choosing "none" for the Audio device for the card you're setting up. 

Give that a shot and see if it helps.

---

### Post by AndrewStout on 2008-10-09
Backend Setup > Capture Cards > [one of my capture cards] doesn't have a place to configure audio device.  It just sets the kind of card (Hauppauge x50), the default source (Tuner 1), etc.

---

### Post by Caps18 on 2008-10-09
I had to select /dev/dsp2 for some reason.  I can't remember what happened.  I also would recommend restarting after changing from /dev/dsp1, /dev/dsp, /dev/dsp2, default,...  I'm not sure it will help solve your problem, but it's something to try.

---

