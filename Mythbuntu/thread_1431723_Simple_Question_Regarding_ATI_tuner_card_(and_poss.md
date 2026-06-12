---
title: "Simple Question Regarding ATI tuner card (and possible future card)"
date: 2010-03-16
forum: Mythbuntu
---

### Post by JesterPoet on 2010-03-16
I just got mythbuntu up and running and can record programs.  I have a couple of questions, though, that I was hoping someone could help with.

Before the questions, I'm using an ATI TV-Wonder Pro (it was free).

First, the picture when I "Watch TV" or watch recorded shows is pretty jittery.  Not unwatchable, but the quality is poor.  Is there something I can do to fix this at all, or is it just a limitation of the crappy card?  Does transcoding after the recording help this at all?  Are there quality settings I can change?  I don't really care that much about watching the TV live (though it would be nice), but it would be nice to be able to have the recorded shows look decent.  The box is a 2Ghz processor with 768MB RAM.  It's not great, but all it does is run Myth.

Second, when I decide to splurge on a new card, I'm not entirely sure what to buy.  (Here's where the really dumb question is)...  Is my signal analog or digital?  I'm using comcast cable, but it's the most basic cable package, and doesn't use a cable box or anything.  I just run the coax directly from where the cable comes into the house straight into the TV (or in this case, the mythbuntu box).  Until I know if it is digital or analog, I don't really know what kind of card to buy.

Any help that anyone can offer would be greatly appreciated!  

Thanks!
-JP

---

### Post by matt06 on 2010-03-17
Hi JesterPoet, sounds like you are on the right track so far.

> **JesterPoet said:**
> Before the questions, I'm using an ATI TV-Wonder Pro (it was free).

First, the picture when I "Watch TV" or watch recorded shows is pretty jittery.  Not unwatchable, but the quality is poor.  Is there something I can do to fix this at all, or is it just a limitation of the crappy card?  Does transcoding after the recording help this at all?  Are there quality settings I can change?

Since you said "jittery" I'm assuming we are talking about video playback and not signal quality.  Transcoding may or may not help, I don't use it myself, but I would check your playback profiles in Myth first thing.  Try different ones (CPU--, CPU+, Normal, etc.) and see if any work better.  Some may not work at all so be prepared to switch back to your original settings.  Also, it would help to know what video card and drivers you are using as that is most likely to reveal the issue at hand.

> **JesterPoet said:**
> Is my signal analog or digital?  I'm using comcast cable, but it's the most basic cable package, and doesn't use a cable box or anything.  I just run the coax directly from where the cable comes into the house straight into the TV (or in this case, the mythbuntu box).

Almost 100% positive you have an analog signal (I was sure your old ATI card is analog/NTSC so this confirms it).  If you were to buy a new card today, you would need one that takes analog/NTSC signals such as your ATI does.  I believe these cards will be hard to find soon as there are no more analog signals being broadcast in countries like the U.S. and cable companies are moving to "digital-only" platforms.  That being said, there are still plenty of options right now for analog capture cards.  In the future you may need a digital card (ATSC) if and when Comcast forces you over to digital or to receive locally broadcast digital signals (over-the-air, standard antenna).  There are also "hybrid" or "dual" cards that can capture both types of signals.

---

### Post by JesterPoet on 2010-03-17
Actually, I seem to have gotten around the picture quality issue with transcoding.  That's been working great.  I have a new issue, though, that I can't seem to figure out.  First, though, for the record, I'm still using the ATI TV Wonder Pro.

So my current problem is with sound.  If I use the "Watch TV" feature in Myth, the sound is fine (though, admittedly, a little behind).  If I go back to the menu, however, the sound from the channel I was watching continues to play.  It's really weird.

Worse, though, when I set a recording, the sound for whatever I'm recording comes on, even if Myth is on the menu screen (and it continues to play unless I reboot).  Then, even worse than that, when I go to play back the recording, the recorded show has no sound at all.

It seems like I must have the sound connected correctly if it comes through on "Watch TV."  Yet the fact that sound doesn't seem to be RECORDED is weird.  I can't seem to figure out why this is happening.  Any ideas?

---

### Post by matt06 on 2010-03-17
Myth General Options, look for Audio stuff.  The settings might be very specific to your system or the default options may work.  It's just a matter of finding out.  IIRC, I had to use some alsa utilities (or Pulseaudio if you are using that??) to make some adjustments.  It sounds like you need to mute your recording or line using alsa-mixer to keep it from coming through via the ATI card when you are recording though.

I don't know a whole lot about linux audio, but here's Myth's page on sound setup (google cache, i guess mythtv.org is down?)

[http://74.125.93.132/search?q=cache:tIs_TGYIdXEJ:www.mythtv.org/docs/mythtv-HOWTO-7.html+mythtv+audio&cd=1&hl=en&ct=clnk&gl=us](http://74.125.93.132/search?q=cache:tIs_TGYIdXEJ:www.mythtv.org/docs/mythtv-HOWTO-7.html+mythtv+audio&cd=1&hl=en&ct=clnk&gl=us)

[http://www.mythtv.org/docs/mythtv-HOWTO-7.html](http://www.mythtv.org/docs/mythtv-HOWTO-7.html)

---

### Post by JesterPoet on 2010-03-17
Muting "line-in" and unmuting "line capture" fixed it.  Everything is working now!  I'm in business!

Thanks everyone!

---

