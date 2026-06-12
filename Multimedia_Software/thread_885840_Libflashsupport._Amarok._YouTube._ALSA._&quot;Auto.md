---
title: "Libflashsupport. Amarok. YouTube. ALSA. &quot;Auto Detect.&quot;"
date: 2008-08-10
forum: Multimedia Software
---

### Post by Roasted on 2008-08-10
I'm trying to sort out this ball of confusion.

I tried going to this web site. It's a news web site that has a video to it about a kid from a baseball game that I wanted to see.

[http://www.wgal.com/video/17122708/index.html](http://www.wgal.com/video/17122708/index.html) (warning: if you have libflashsupport installed, it may crash firefox. I'll explain more later)

Going back a bit, I had a system crash last week. I was listening to Amarok and I had 4 tabs open in Firefox. Two were YouTube (nothing playing) and one was UbuntuForums. I was typing a response here on the forums and suddenly my audio locked up and my entire system just stopped responding. I had to do a cold shutdown and restart it. I posted here asking what was up, and someone suggested I install libflashsupport.

Once I installed libflashsupport, I went to that news site I posted above. Sure enough, firefox crashes. I was confused, cause I was under the impression that libflashsupport takes away from the instability of flash in firefox. 

I uninstalled libflashsupport. Bam. Worked perfect then. So then, I started doing some research behind the purpose of libflashsupport... Because after all, why is it needed if, in my case, it only crashed things? I kept reading that it enables you to play music on your music player (Amarok, Audacious, etc) AND watch/listen to youtube at the same time. But, wtf, I can do that WITHOUT libflashsupport. How am I any different from anybody else?

So then, I figured this out...

I'm using Ubuntu Hardy Heron 32 bit 8.04 with Flash 9, Firefox 3, and Amarok. Under system-preferences-sound, all sound preferences are using ALSA. I am using a Turtle Beach Montego 7.1 PCI Sound Card, although I doubt the sound card would yield any different results than say, my onboard Realtek sound card.

I found:

With libflashsupport = YouTube and Amarok will work together (Audio/Video from YouTube + Audio from Amarok) if Amarok's engine is set to "Auto Detect." Amarok being set to "ALSA" does not work.

Without libflashsupport = YouTube and Amarok will work together (Audio/Video from YouTube + Audio from Amarok) if Amarok's engine is set to "ALSA." Amarok being set to "Auto Detect" does not work. 

So in essence, the presence of libflashsupport requires the engine in Amarok to be switched. However, if the engine is set to ALSA, and my preferences are set to ALSA, everything seems to be happy. 

Why? 
Why is this? 
What's the purpose of libflashsupport if my settings without libflashsupport work perfectly fine?

Also - just for kicks, I tested this same theory with Audacious. Audacious does not have "auto detect", but I was able to test it with the engine being set to ALSA. Sure enough, without libflashsupport, Audacious and YouTube were happy. Yet, with libflashsupport, Audacious did not work.

---

### Post by t0p on 2008-08-10
So your system works okay without libflashsupport.  Congratulations.

Unfortunately, not all systems will work like yours.  Some have an issue with pulseaudio - ie, pulseaudio won't work when playing flash vids.  As part of a fix for that problem, it is necessary to install libflashaudio (and some other stuff).

---

### Post by eye208 on 2008-08-10
> **Roasted said:**
> I am using a Turtle Beach Montego 7.1 PCI Sound Card, although I doubt the sound card would yield any different results than say, my onboard Realtek sound card.
Some sound cards support mixing multiple streams in hardware, some don't. Sometimes this can make all the difference.

---

### Post by Roasted on 2008-08-10
I understand that, but what about other systems would make pulseaudio become such a problematic thing? 

The common concensus seems to be that pulseaudio often offers problems with pretty much everybody, and your choices are to either work through it or uninstall it.

I chose neither, and everything works. I understand some systems may differ in terms of results, but what I don't understand is what about each system that'll dictate system A resulting in catastrophic problems whereas system B runs off yippy skippy all well and good.

Know what I mean? I'm just trying to understand how everything inter-mingles together... 

But, in essence, you're saying that it's possible that somebody else after a fresh format of Ubuntu Hardy could set up their system settings and sound settings the exact same as I did and get completely off the wall problems and responses?

---

### Post by Roasted on 2008-08-10
> **eye208 said:**
> Some sound cards support mixing multiple streams in hardware, some don't. Sometimes this can make all the difference.

Hmm... I see. I wonder... if I were to take my PCI sound card out, re-enable my onboard card, and try the same settings that I had set up for my Montego sound card, if I would get the same results... hmm...

I didn't think about this. Is mixing multiple streams often a feature that you would read under a specification list on say newegg.com or something? Or is it just assumed that all newer sound cards support it?

---

