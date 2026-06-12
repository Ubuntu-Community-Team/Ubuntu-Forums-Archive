---
title: "Sound issues + Lexicon Lambda"
date: 2008-12-11
forum: Multimedia Software
---

### Post by Trinitrogen Oxide on 2008-12-11
Fresh install of Ubuntu yesterday to get rid of the failed experiment that was my week with Vista. After install, I wasn't getting any sound through my Lexicon Lambda. I went to System->Preferences->Sound and they are all set to Auto Detect. Whats strange is that in the drop down list I've got TONS of devices. 

Nvidia CK804 with ALC655 Nvidia CK804 - IEC958 (ALSA)
Nvidia CK804 with ALC655 Nvidia CK804 (ALSA)
Lexicon Lambda USB Audio (ALSA)
Nvidia CK804 with ALC655 Nvidia CK804 (OSS)
Nvidia CK804 with ALC655 Nvidia CK804 (OSS)
Nvidia CK804 with ALC655 Nvidia CK804 (OSS)
Lexicon Lambda USB Audio (OSS)
Lexicon Lambda USB Audio (OSS)
ALSA Advanced Linux Sound Architecture
OSS Open Sound System
Pulse Audio Sound Server

In each of the drop down lists. I tried the Lambda Alsa drivers, and I get the error 

audiotestsrc wave=sine freq=512 ! audioconvert ! audiosample ! gconfaudiosink:Could not open audio device for playback

The only one that works is Lexicon Lambda USB Audio (OSS), both of them. My question is strange, because my sound is working just fine, but it doesn't seem like I should have so many versions of the same device in the dropdown list...

---

### Post by gasto on 2009-06-13
Me too.

The main problem is that system sounds are playing but flash music and sound (using JW player) is not working. Neither are flv files' sound working using VLC.

Any suggestions_?

---

### Post by gasto on 2009-06-13
I tried with Totem Movie Player 2.26.1 , Movie Player using GStreamer 0.10.22 , and the same flv file tested and the sound works! Also an mp3 played on gstreamer on Mozilla Firefox also worked.

So I tried to figure out what settings did Totem movie player have for sound, but no luck, nothing really showing on the GUI besides the stereo/mono  option and other stuff, not mentioning the actual device.

---

### Post by gasto on 2009-07-06
Anyone?

---

### Post by Mucus on 2009-10-25
No, I have no clue as to what is causing this. Having the same (very annoying problem) and it's even more mysterious as some applications (Caffeine, VLC etc.) have no problems using the ALSA drivers through the Lexicon Lambda (so it at least works...?) but on most of the other applications it fails. JACK is also incapable of running ALSA with the soundcard, and this is the main problem as I cannot do ANY recording, editing or real audio work (with the Lambda as the interface) without JACK running as most programs refer to it as a standard.

However, I did get JACK up by using OSS4, but then again programs like Audacity do not seem to be able to connect to JACK if it's running OSS... I am at a wall here and after some months of (randomly) wrestling with the problem I am trying to decide whether I should get a gun and shoot the sound card or put the money on a new soundcard. But then the problem is that if it's NOT a soundcard issue, I end up buying a new piece of equipment that is going to be useless to me and I don't even have the gun so I cannot go on a mad murderous rampage, running naked on the street and shouting "drop database Dresses;" to all possible bypassers...


Um. So anyone got a clue on how I could get it to work?

---

### Post by Mucus on 2010-03-17
Looking back at my n00bness...


The issue has to do with realtime processing permissions. You will find the solution in the forums here.

OR!

Install realtime kernel.

---

### Post by tchekyfelb7 on 2011-01-08
> **gasto said:**
> Me too.The main problem is that system sounds are playing but flash music and [[COLOR=#000000]sound[/COLOR]](http://www.**********************/xvid-avi-conversion-guide/xvid-avi-to-ipod-touch-guide.html) (using JW player) is not working. Neither are flv files' sound working using VLC.Any suggestions_?Could you give more explanation on it?

---

