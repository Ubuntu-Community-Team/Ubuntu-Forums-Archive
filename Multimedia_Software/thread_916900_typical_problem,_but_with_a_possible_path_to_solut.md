---
title: "typical problem, but with a possible path to solution: spdif digital sound"
date: 2008-09-11
forum: Multimedia Software
---

### Post by pivot@pivpoint.no on 2008-09-11
Hey guys!
I know this is a subject that has been discussed for endless times here at ubuntuforums. It really sux that the alsa project still hasnt figured this one out, and that some of us still suffer from this.

I have a problem getting spdif digtal sound from my htpc to my reciever. The passthrough analog works fine. No worries about that. But other than that it's a mess.

I use mythtv for dvb-c, and as a media center. I've tested all kinds of options in mythtv, vlc and other progs but never really got it working. However. I did find one command to use to make mplayer use digital sound. I feel this is a breakthrough, and I see a light in the tunnel!

I got this sample. An ac3 file (download [here]("http://www.diatonis.com/downloads/diatonis_ac3_48k_soal.zip")). If I use the terminal and type the command 

mplayer diatonis_soal_48k.ac3 -ao alsa:device=hw=0.0 -ac hwac3

i get beautiful digital surround in my speakers. The reciever recognizes the signal and everything seems ok. I used this command in mythtv to make the external player in "watch videos" (which is also mplayer) use the correct device too. So now I have surround for all videos that uses mplayer and not the internal player.

I would however get the internal mythtv player to use the correct device too, because I cannot make digital sound at my dvb-c broadcasts work. Also I cannot make VideoLan use the correct device.

In vlc I've tried to set the alsa output module to use the device "Nvidia ck804: Nvidia ck804 (hw:0,0) but this only resulted in sound stutter when playing digital sound media.

In mythtv all I can get is sound or no sound, no matter what I try...

Any suggestions?

---

