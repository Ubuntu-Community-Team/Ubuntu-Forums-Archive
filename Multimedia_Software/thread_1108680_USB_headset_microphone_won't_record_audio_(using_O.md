---
title: "USB headset microphone won't record audio (using OSS)."
date: 2009-03-28
forum: Multimedia Software
---

### Post by AntiNeko on 2009-03-28
Heyya all!

ALSA didn't work out for me, at all, so I replaced it with OSS. I found a comfortable solution, using OSS, in changing the default sound source between my SB-Live card and my USB headset, so I stuck with OSS. I've looked like crazy for a solution to my problem, but the only information I've actually managed to come across has been about ALSA, so I'm hoping for some OSS-feedback.

I've been happy with the change to OSS and it's been working nicely 'til I tried out the built-in mic of my A4 Tech HD 800 headset. The only recording I manage to do is the output of the SB-Live sound.

In my Sound Preferences, there's OSSv4 options for my USB headset, SB-Live card and RealTek motherboard-based sound. I've tried all possible combinations here and nothing works the way I want it to. For my USB audio, I set all the options to "OSSv4 USB Sound Device Play" and then the output works fine.

Now, starting out, I just had the option called "USB sound device rec" under Sound Capture. If I choose that and run the test, it gives me the following error:

> gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Error recording from audio device.

So, I tried installing a package called "gstreamer-oss", which gave me another device called "USB Sound Device rec (custom)", which gives me a different friggin' error:

> gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open audio device for recording.

---

### Post by JoshTodd on 2009-03-30
I am having the exact same problem. Any help appreciated!

---

