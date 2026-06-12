---
title: "Soundblaster Live! 24-bit (Audigy LS) Output Issue"
date: 2006-07-16
forum: Multimedia &amp; Video
---

### Post by foofightrs777 on 2006-07-16
I am having an issue where my sound card only outputs sound over the "Analog F" channel.  All other channels are silence and thus I'm unable to hear anything from my speakers besides left and right.

Steps I've already taken:
1.  Attempted to adjust levels using alsamixer.  This has resulted in me seeing that only the Analog F channel has any output.
2.  Removed (purged) alsa and reinstalled.  This seemed to have no effect besides getting a default configuration back.
3.  Compiled alsa from source using module-assistant.  This seems to kill my sound for some reason.  I'm unsure why this does not work.
4.  Attempted to use an asound.rc.  This seemed a little above my head so I decided to leave it be.  I was reading that new alsa doesn't always play nice with this method anyway.
5.  I've read about loading alsa with certain settings for surround sound.  How would one go about doing this?  Would this even be applicable in my situation?

So, I'm at a loss now.  I have scoured the forum and googled for a solution and have found individuals with the same problem; but no solution.  I really like Ubuntu and would like to use my (modest) setup to its full capabilities.  Does anyone have ANY ideas?  Thanks in advance.

---

### Post by foofightrs777 on 2006-07-17
I'm going to bump this back up.  Surely someone has some info....

What about duplicating the sound (for 2 channel audio) to the to the other speakers through alsa conf?  Would anyone know how to do that?

---

### Post by foofightrs777 on 2006-07-17
Just an update in case someone more knowledgable than I happens across this thread....

Using xmms I've found that

hw0,0 is the output for my L&R speakers.
hw0,1 outputs for the rear speakers.
hw0,2 oupputs the center speaker.

Is there anyway I could use all these channels at once?  They work individually but I see no way to combine them.  :(

---

### Post by foofightrs777 on 2006-07-17
If nobody has any ideas could someone at least recommend where I can get some general support with alsa.  Such as other message boards, etc?  

I think the solution to my problem isn't all that dificult..just a bit beyond me :(

---

### Post by thoffland on 2006-10-12
I'm having the same problem.  I had a USB soundcard for my 5.1 system and just happened to have a spare card (same as yours) in my box so I eliminated the USB card and now I only have sound out of the front speakers and base. If I turn it up... it's all tinny. 

I've been searching and only found this so far from another link: 
[http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml](http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml)

I got started on it, but gave up... there has to be a better way. If I dont find anything else soon, I'll go through with this.

---

