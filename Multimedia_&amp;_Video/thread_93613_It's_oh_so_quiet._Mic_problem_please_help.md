---
title: "It's oh so quiet. Mic problem please help"
date: 2005-11-22
forum: Multimedia &amp; Video
---

### Post by DiscoKiller on 2005-11-22
Calling all friendly linux people. I`m new to this game and have been beating my head against a wall for some time now yet slowly but surely i`m coming to terms with my new best friend Mr. Linux (much quicker and less patronising that windows it would seem). Anyway, as someone used to just pointing and clicking i`ve been trying my best to come to terms with this wonderful piece of operating system yet there is one problem i just cant seem to solve. the first time i really noticed it was when running Skype. once upon a time i was able to use skpy hassle free but all of a sudden i cant use my microphone in it, the sound comes out of the speakers but when calling the likes of echo123 i cant seem to send any audio myself. this is getting right on my tits as i want to be able to talk to my girlfriend who is currently in spain. i thought at first it was something to do with skype itself but then i tried to use audacity, again to no avail. it doesnt seem to want to use my microphone as an input device, thinking maybe i wasnt using audacity correctly as i am pretty hopeless with most things i tried the little generic sound recorder that came with ubuntu, alas no luck. i`ve tried several things like editing the eds.conf file and whatever else i was told to do by a previous post but nothing appears to be working. Please can somebody shed some light on this little problem of mine so i can talk to my lovely gily while she is all alone in mean old spain. Thank you DK

---

### Post by jeffjanzen on 2005-11-22
what exactly have you tried?
if playback and playthrough (hearing real-time microphone input through the speakers) are working, it seems to me like capture should work, if you've enabled sound capture from your mic jack.  all the settings are in the volume control app (sound & video > volume control) under the tab labeled "capture".  buttons under the sliders control muting and capturing.  make sure capture is enabled for the slider labeled "microphone" and you should be in business.
i apologize if you've tried this already.

---

### Post by DiscoKiller on 2005-11-22
no appology necessary, unfortunately i have been arsing around with the mixer for weeks now and i`ve not got a peep out of it. the bit that perplexes me the most is that i have had it working before. it just seems to not want to capture any kind of audio for me, about a week ago a was dicking around with audacity and i got some form of audio capture but the bitrate must have been slowly rodgered from behind coz everything was excruciatingly slowed down on playback and choppy as hell. i`m looking to use some for of recording software (multitrack) in the near future but things arent looking good for that. as it stands. everything soundwise i.e. playback through XMMS, Mplayer, Xine and realplayer all work fine and dandy, it just seems that i`m unable to record any audio from my microphone. is there another mixer application i can try that is less vague than the one that sits in the bottom of my screen?

---

### Post by drkemp on 2005-11-22
I had a similar problem and learned that you MUST use alsamixer NOT the gnome mixer app. 
How I fixed it: Launch a terminal and run alsamixer. Use the tab key to select inputs and arrow across to each input and ensure that the mic and capture are selected.

---

### Post by drkemp on 2005-11-22
Oops. That would only apply if you are using Alsa sound (as opposed to esd or oss).

---

### Post by avliet on 2005-11-22
I am having a very very similar issue - Using Skype, about 2 weeks ago, I updated Ubuntu, had to restart, and noticed...  *poof* - no microphone...  very frustrating... my girlfriend is in Brazil so I know what you're going through...  very annoying.   I am suspecting that it's a driver / ALSA issue but I'm not sure how to go about testing / fixing this.  Anyone have any ideas?

---

### Post by gpfreitas on 2005-11-23
Here's what worked for me:

1. Fire a terminal and type 

$alsamixer

You will see a text-mode mixer.

2. Press the "arrow-left" key nine times (I'll call this entry number 9). You should be in the item "Mic-In Mode [Center / LFE Output]". Press the "arrow-down" key once.

3. Check if the "Mic" item levels are high enough. "Mic" is entry 7.

Test you mic... It worked for me.

---

### Post by gpfreitas on 2005-11-23
By the way, at step 2, when you press "arrow-down" key, the item name should change from "Mic-In Mode [Center / LFE Output]" to "Mic-In Mode [Mic-In]".

---

### Post by dave.goodfellow on 2006-06-03
[QUOTE=gpfreitas]Here's what worked for me:

1. Fire a terminal and type 

$alsamixer

You will see a text-mode mixer.

2. Press the "arrow-left" key nine times (I'll call this entry number 9). You should be in the item "Mic-In Mode [Center / LFE Output]". Press the "arrow-down" key once.

3. Check if the "Mic" item levels are high enough. "Mic" is entry 7.

Test you mic... It worked for me.[/QUOTE]

using alsamixergui is easier

---

