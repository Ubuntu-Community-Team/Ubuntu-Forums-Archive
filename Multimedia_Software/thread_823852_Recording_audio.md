---
title: "Recording audio"
date: 2008-06-09
forum: Multimedia Software
---

### Post by Gina on 2008-06-09
I have searched the forums but not found an answer...

I am trying to record (copy) music from my old LPs (vinyl) to HD but not having any success.  I can play the audio from my record deck via the Line Input, through my PC speakers but neither Audacity nor Sound Recorder will record anything.  Audacity plays back audio files OK but the recording only sees a faint background noise.

Does anyone have any suggestions please?

---

### Post by xc3RnbFO8P on 2008-06-09
If you own these LPs, I cant see no reason why you cant download
it from the internet, I do (saves time).
You can record it through mic jack with Sound Recorder.

---

### Post by cariboo on 2008-06-09
If you have tape monitor jacks on your stereo use a Y-cable, ususally 2 rca to 1 mini headphone connector and then try the line input on your sound card. I picked up an old Harmon Kardon receiver at the local Salvation Army for $20.00 as none of the other receivers I own have turntable inputs. I replaced a few burnt out light bulbs and it's still in use out in my shop.

I used a program called gramofile that is available in the repositories. It encodes the files as .wav, and if you set it up properly it will create a separate wav for each track. The web page is here:

[http://www.hitsquad.com/smm/programs/gramofile/](http://www.hitsquad.com/smm/programs/gramofile/)

Jim

---

### Post by mehtdosa11 on 2008-06-09
are using just a normal record deck or a usb deck made for converting vinyl to digital?

---

### Post by markbuntu on 2008-06-09
What are your devices set to in System/Prefences/Sound?
And is capture on in your mixer?

---

### Post by Gina on 2008-06-09
Thank you everyone for your replies :)> **cariboo907 said:**
> If you have tape monitor jacks on your stereo use a Y-cable, ususally 2 rca to 1 mini headphone connector and then try the line input on your sound card. I picked up an old Harmon Kardon receiver at the local Salvation Army for $20.00 as none of the other receivers I own have turntable inputs. I replaced a few burnt out light bulbs and it's still in use out in my shop.

I used a program called gramofile that is available in the repositories. It encodes the files as .wav, and if you set it up properly it will create a separate wav for each track. The web page is here:

[http://www.hitsquad.com/smm/programs/gramofile/](http://www.hitsquad.com/smm/programs/gramofile/)

JimThanks Jim - I'll try gramofile :)

My record deck has a preamp with line level output (I used to connect it to a power amplifier to feed the speakers).  This works fine with the Line In port on the mobo.  I can play through the sound card to the speakers (Line Out).  Capture is turned on and devices set to the sound system.  Capture input is set to Line In.  

It works with Audacity in Windows but I prefer not to use that OS.  (OK - so it's one option :lol: )

Yes, I do own the records - many of them are very old and rare (though in good condition) and I cannot find copies either in CD form in the shops or online.  I have replaced much of my collection with CDs but some favourites remain without modern equivalents.

---

### Post by Gina on 2008-06-10
Hmm... gramofile won't compile (make) on this system (64 bit AMD Athlon) - I'll try it on a 32 bit system - I see it's dated 2000 (rather old).

I've done some more experimenting - looking at PulseAudio.  I think this is the problem - it only uses the front audio connections it would seem from it's settings.  However, something (ALSA?) is working with the rear connections because I can play records through the Line In socket and have my speakers connected to Line Out.  Now I just need Audacity to use the rear Line In for capture - there must be a setting somewhere.

---

### Post by Gina on 2008-06-10
Won't compile in Hardy 32 bit either :(  Same errors.

---

