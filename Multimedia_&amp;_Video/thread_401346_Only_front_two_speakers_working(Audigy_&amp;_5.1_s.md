---
title: "Only front two speakers working(Audigy &amp; 5.1 speakers)"
date: 2007-04-04
forum: Multimedia &amp; Video
---

### Post by binilbenjamin on 2007-04-04
I'm having 5.1 creative inspire speakers with Sound blaster Audigy sound card. While i play mp3s using xmms or other players, only front two speakers and woofer are working.  The front center and the back two speakers are idle. 
When I used the following command, all speakers worked!
[INDENT]speaker-test -Dplug:surround51 -c6[/INDENT]

I tried everything in alsamixer. Nothing is solving my problem. I tried playing dvd using totem movie player and media player.Still only 2 speakers are working. Please help me!

---

### Post by crispy_420 on 2007-04-06
Does totem support 5.1 output? Try xine or vlc instead. As far as mp3 and surround, it is only 2 channels so I believe it doesn't even try the rear channels as they are not needed. In the case of the same card in WIndows, it tries to emulate but it is just filler.

---

### Post by binilbenjamin on 2007-04-06
I got the solution from this link: [http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml](http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml) 
The .asoundrc file did the job!. No I could hear from all speakers while playing in xmms. Thanks for your reply

---

