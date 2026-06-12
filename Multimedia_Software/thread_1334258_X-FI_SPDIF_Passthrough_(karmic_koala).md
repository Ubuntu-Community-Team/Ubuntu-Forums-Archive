---
title: "X-FI SPDIF Passthrough (karmic koala)"
date: 2009-11-22
forum: Multimedia Software
---

### Post by makaveli789 on 2009-11-22
Hi everyone, I just finished installing Karmic Koala last night and today I fiddled around with my alsamixer settings to get my SoundBlaster X-FI working - just had to switch on the digital out. From Sound Preferences, I left the profile to 'Analog Stereo Duplex' and it seemed to be working ok.

However, when I try to play a file with an AC3/DTS track the soundcard is not outputting a digital signal to my receiver i.e. I still get stereo sound. I am using VLC and normally in Windows under Audio > Audio Device I can select the AC3 to pass straight through to my receiver. But in Ubuntu that section is completely greyed out.

As a side note, I can see from my receiver that any signal coming through is at the frequency 96khz. I believe a digital bitstream should output at 48khz...

I have kept my home desktop Ubuntu free for a long time because X-FI support was a little dodgey but thought I'd jump in and try again now that X-FI is supported. Therefor, I am not too familiar with audio configuration under Ubuntu/Linux. I love my music and movies (in 5.1) so I really need my soundcard to work properly otherwise it is a deal breaker for me and I am going to have to revert to Windows for my home pc. Please help!

---

### Post by makaveli789 on 2009-11-23
Comeon guys, so many views - can I get anyone's thoughts?

---

### Post by makaveli789 on 2009-11-26
> **makaveli789 said:**
> Comeon guys, so many views - can I get anyone's thoughts?
It must be to do with the frequency of the sound being sent from the soundcard.

---

### Post by kamienn on 2009-11-28
Hi,
I have exactly the same situation like you!
Unfortunately I don't know how to force ubuntu to play 5.1 movies correctly (like windows does) :-(. I'm keep searching in google. Maybe I will find something and let you know.

---

### Post by makaveli789 on 2009-11-29
> **kamienn said:**
> Hi,
I have exactly the same situation like you!
Unfortunately I don't know how to force ubuntu to play 5.1 movies correctly (like windows does) :-(. I'm keep searching in google. Maybe I will find something and let you know.

Sure ok, I will do the same. Just wondering, what are you using to play the file - VLC also?

---

### Post by makaveli789 on 2009-12-01
[Just found this post on another forum by ]("http://www.silicondust.com/forum/viewtopic.php?t=7876&sid=093a13bb3ad8260a49d82aa19f5fc401")**[WattoDaToydarian]("http://www.silicondust.com/forum/viewtopic.php?t=7876&sid=093a13bb3ad8260a49d82aa19f5fc401")**. I will try this whenI get a bit of time to play around with Ubuntu at home.

[quote=WattoDaToydarian]
I recently installed Ubuntu 9.10 on my PC and found that the included PulseAudio version blocks SPDIF passthrough for media players including VLC. 
However it includes a program called pasuspender which you can use to run media players to bypass PulseAudio for direct access to the SPDIF port. 
 
I had some time today and decided to see if I could hack the source to the hdhomerun gui to include pasuspender when launching VLC. An hour or so later I finally got it to work so I decided to share it with everyone. 
 
First you need to download and extract both source code tarballs from [here]("http://www.silicondust.com/downloads/linux") (do "tar xzf *" in the download location.) Next open "hdhomerun_config_gui/src/Viewer.cpp" in a text editor. Then scroll to line #161 and replace it with this: 
 ```
execlp("/usr/bin/pasuspender", ExeName.c_str(), ExeName.c_str(), "udp://@127.0.0.1:5000", (char *) NULL);
```Finally save it, compile, and install as you normally do. 
 
When you go to open your TV channel it will stop all other sound playback in favor of VLC. 
I hope this helps at least one person and maybe the devs can incorporate a PulseAudio auto-detection mechanism to add this when needed in the future.
[/quote]

---

### Post by golovan on 2010-02-13
Oops posted in wrong thread...

Sorry

---

