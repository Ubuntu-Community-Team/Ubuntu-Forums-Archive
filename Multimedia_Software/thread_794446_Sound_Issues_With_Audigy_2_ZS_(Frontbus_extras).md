---
title: "Sound Issues With Audigy 2 ZS (Frontbus extras)"
date: 2008-05-14
forum: Multimedia Software
---

### Post by Kelpie on 2008-05-14
OKay, I have an Audigy 2 ZS, it has a front side bus extras, which looks like this:
[IMG]http://kelpie.fragvault.com/images/newcompcase.jpg[/IMG]

My problem existed after I had upgraded all the way from 6.06 to 7.10, because I wasn't going to wait for CDs, and I am frankly, too poor for buying CDs myself.

I could play music with the 6.06 install, but sound no longer works. And it seems the test in the sound thingy only works for OSS, but I have no idea how that works, and I know I was using ALSA before.

Along with this, I am getting an error when playing MP3s in XMMS (other players do not play MP3s until I make them support it):
Please check: your soundcard is configured properly, you have the correct output plugin selected, No other program is blocking the soundcard.

When I go to the sound in preference, testing anything except OSS makes similiar errors, but for ALSA it says:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open resource for writing.

When I select OSS to test, it only works in the back of my computer, but I do not use the back of my computer for sound, as you can see on the image.

I also have Kubuntu and Ubuntu installed, as well as Compiz-fusion, but the problem existed after I upgraded.

Can someone help me sort this out?

---

### Post by retro_killa on 2008-05-14
I would try 8.04 that might be your best bet. :guitar:

I was running 8.04 for a while & all my laptop drivers installed easy even the built in webcam ;) but with windows vista it took me 5-6 months to get that built in webcam to work 

good luck 


:KS:KS:KS:KS:KS:

---

