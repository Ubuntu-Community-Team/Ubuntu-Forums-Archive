---
title: "Sound only with Rhythmbox"
date: 2007-04-13
forum: Multimedia &amp; Video
---

### Post by anthonyesau on 2007-04-13
I am running Ubuntu Edgy Eft on a Dell Dimension 8400 ([**click here for specs**]("http://reviews.cnet.com/Dell_Dimension_8400_Pentium_4_3_6_GHz_512_MB_RAM_80_GB_HDD/4507-3118_7-30919189.html")).  My problem is that I cannot get sound to work except for that Rhythmbox plays music just fine.  No videos play sound with VLC, Totem, or anything else.  There is no sound from Firefox when I watch videos on YouTube, play Flash games, or even open an mp3 with it.  The only other things that any sound work with are the game N, under Wine; and the System > Preferences > Sound tests with the options p16v, Multichannel Playback, a few others, but not with ALSA, ESD, or OSS.  

For a while I could get sound to work with everything if I switched libsdl1.2debian-all to libsdl1.2debian-oss or vice versa and then restarted the computer.  Usually the next or the time after next when I restarted the computer and used it, the sound would not work again and I would have to switch libsdl1.2debian-all to libsdl1.2debian-oss or vice versa again and restart.  

Now none of these procedures work!  I have tried the **[Comprehensive Sound Problems Solutions Guide]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide")**, and it does not help even with using libsdl1.2debian-alsa.  I have not compiled ALSA from source yet.  Would that help?  I get a good list of soundcards installed on my system with 
'aplay -l' in terminal.  I do not know what to do.  If you have some input, I would really appreciate your time and be thankful for a solution!

---

### Post by anthonyesau on 2007-04-15
I now found out that Totem Movie Player does work with sound output.  Most of the time, though, it can't play the correct video files, and even if it does, it doesn't even show the video.  So what is it that both Rhythmbox and Totem do that everything else does not?

---

