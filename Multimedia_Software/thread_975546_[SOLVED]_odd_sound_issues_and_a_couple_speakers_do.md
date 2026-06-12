---
title: "[SOLVED] odd sound issues and a couple speakers dont work"
date: 2008-11-08
forum: Multimedia Software
---

### Post by gummygod on 2008-11-08
i recently fresh installed to 8.10 so i could get somethings how i wanted and hopefully finally fix all my sound issues.  but im having sound issues again. i always have with my lovely Creative Live Sound Blaster Audigy.  this time, since pulseaudio is default im using that. 
first, i have 5.1 speaker set up. i edited /etc/pulse/daemon.conf to get more speakers working.  but my back two speakers do nothing. the front left, right, AND center and LFE all work.  the connections are fine, and all of the speakers work in windows.  pulseaudio volume meter shows bouncing bars indicating theres sound going to the channels.  amarok, vlc, and 'speaker-test -Dplug:surround51 -c6 -l1 -twav' all play sound through 4 speakers instead of the 6 i would like.  any ideas what to do to get the other speakers working?

secondly, some .mp3s, and some .m4as i play have abysmal quality. they speed up and slow down slightly but its noticeable. and they have static where there was no static before. im not sure if this is from amarok, pulseaudio, xine, or because i copied them all to an external hdd when i fresh installed and copied them back.  again, any ideas on this one?

thanks for any help. im just gettin frustrated fixing my system again and dont have the time to crawl forums and search google all day long

---

### Post by gummygod on 2008-11-11
so turns out in the volume control gui i needed to change the volume of the speakers. i figured i needed to mess with pulseaudio, but guess not.

and the other issue im not sure what happened, but it might just have been a fluke.

---

