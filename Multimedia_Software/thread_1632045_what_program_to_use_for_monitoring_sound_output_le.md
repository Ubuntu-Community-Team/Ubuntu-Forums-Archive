---
title: "what program to use for monitoring sound output level / vu meter"
date: 2010-11-27
forum: Multimedia Software
---

### Post by pgagy on 2010-11-27
Can someone recommend a good app to monitor the OUTPUT of my soundcard?  I don't just want to look at the VU meter of my music player - i actually want to see what the soundcard is outputting.  Windows drivers for my soundcard (Audiophile 192) had this ability, but I'm not sure what software to use in Linux.

---

### Post by cchhrriiss121212 on 2010-11-28
That card uses the ice1724 chip so you can use envy24control, which is in a package called alsa-tools.

---

### Post by pgagy on 2010-11-28
> **cchhrriiss121212 said:**
> That card uses the ice1724 chip so you can use envy24control, which is in a package called alsa-tools.

I had no idea that was part of the driver - or that there even was something to control it with.  Any idea how to actually access this utility?  I do have alsa-tools installed.

---

### Post by cchhrriiss121212 on 2010-11-28
Sorry, I was mistaken the envy24control program only works for ice17**12** chips. I only know of other vu meters that work with jackd, something like this is used mostly for audio work.
Are you running audio manipulation or are you just curious about your output level?

---

### Post by pgagy on 2010-11-28
Just want to know if my levels are clipping or not.  It sounds like there is some clipping in some of my music, so I want to see if it's going too far.  I have output levels set to 80% in alsamixer, but I'm curious if I need to go lower.  Best is to go as high as possible without getting clipping.

> **cchhrriiss121212 said:**
> Sorry, I was mistaken the envy24control program only works for ice17**12** chips. I only know of other vu meters that work with jackd, something like this is used mostly for audio work.
Are you running audio manipulation or are you just curious about your output level?

---

### Post by ThatBum on 2010-11-28
I know an **input** VU meter, probably isn't going to help you.

arecord -D pulse -f dat -c 2 -vv /dev/null

Assuming you have a microphone.

---

### Post by cchhrriiss121212 on 2010-11-28
In alsamixer select one of your output channels and look at the "Item" line at the top, on my card it tells me the dB level, as opposed to the percentage level at the bottom.
For example if my first ADC is set to 80% it will be at 2.5dB, at 90% it is 10dB. It could be that 80% is over the 0dB level for your card (and therefore adding distortion to the audio).

I would test the alsamixer levels out any way, try listening at 50% and amplify it externally to test the difference.

---

