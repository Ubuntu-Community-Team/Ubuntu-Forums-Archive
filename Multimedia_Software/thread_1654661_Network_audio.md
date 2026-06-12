---
title: "Network audio"
date: 2010-12-28
forum: Multimedia Software
---

### Post by vortmax on 2010-12-28
When I ride my indoor bike trainer, I play videos on my laptop set in front of me.  However, the audio gets drowned out, and the computer is too far to run headphones.  So what I'm attempting to do is configure something like jackd to grab all systems sounds (or just the audio portion of the video I'm watching) and broadcast it over my lan to my android phone.  I've looked around and don't see any android apps that can connect to a jackd server, BUT there are plenty that can receive streaming audio (I can stream audio to the phone via VLC).

I'm sure there is a simple solution lost somewhere in the intricacies of VLC and jackd, but I have yet to find it.  Any ideas?

---

### Post by gordintoronto on 2010-12-28
How about an extension cable for your earphones?

---

### Post by vortmax on 2010-12-29
What fun is that?  Seriously though, I don't want to be connected to the computer.  When you ride rollers, the bike isn't fixed in one place.  I'm envisioning very bad things happening if the long cable got caught in the front wheel, or if I happened to go down and pull the computer with me.  Ideally I could just buy a bluetooth headset and be done with it, but I'm cheap at the moment.

Anyway, I did make it work.  I set up an icecast2 server, setup alsamixer to clone the soundcard output to an input channel, then used darkice to connect the two.  Then I just installed a shoutcast player on my phone and connected to my laptop.  Unfortunately every attempt resulted in 5 to 10 seconds of latency, which makes it useless for my purpose.

My workaround was to just strip the audio out of the video with ffmpeg and load it on my phone.  Then I just manually synced the two players.  It wound up working out just fine.

---

