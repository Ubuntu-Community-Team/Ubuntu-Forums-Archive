---
title: "MPD not working"
date: 2009-03-27
forum: Multimedia Software
---

### Post by starNIX on 2009-03-27
Ok, here's the deal.  I have mpd installed on my Intrepid box but I cannot get it to play.  I followed the steps here [http://ubuntuforums.org/showthread.php?t=789578&highlight=mpd+play](http://ubuntuforums.org/showthread.php?t=789578&highlight=mpd+play) to try to fix pulse but I don't know if that's the problem.  

MPD starts up fine and I can see all my music in ario but when I try to play something there is no sound.  What I mean is it doesn't start playing.  It isn't as if it's playing and the volume is muted,  it doesn't start playing at all.

I have the following in mpd.conf:

user                                 "<my username>"
bind_to_address                 "10.0.21.250"
port                                 "6600"

audio_output {
        type "pulse"
        name "My MPD PulseAudio"
        server "10.0.21.250" # optional
        sink "alsa_output" # optional
}

This is what comes up over and over in the log when I start ario:

Mar 27 00:36 : interface 0: process command "status"
Mar 27 00:36 : interface 0: command returned 0
Mar 27 00:36 : interface 0: closed

Any ideas what could be wrong or how I could hack it to work?

---

