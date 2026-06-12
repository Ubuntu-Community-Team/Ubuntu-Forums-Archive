---
title: "Sound Recorder, Audacity...I cant record anything"
date: 2007-06-01
forum: Multimedia &amp; Video
---

### Post by residualbit on 2007-06-01
ok if someone could tell me where to find it, i will post my sound card info...anyway. sound recorder won't work at all, if i plug a mic into my laptop i can hear it through the speakers just fine, but sound recorder will pick nothing up....even weirder...in audacity when i just try to record my voice it records, but then playsback with a high pitch squeal in the background and my voice is nearly indistinguishable, it kind ok sounds like a robot....help!

---

### Post by tgalati4 on 2007-06-01
Double click on the speaker volume control on the upper dock bar.  This will bring up the volume mixer control.  Edit preferences and turn on every thing.  I mean every thing.  Now you should see extra volume sliders and sometimes extra options (like 20 dB microphone boost).  Unmute everything and lift every slider to 70%.

Go back into Audacity and hit record.  You should see/hear something.

---

### Post by residualbit on 2007-06-01
i can see and hear things in audacity, i can see the level indicator, but when it records and i play it back there is a terrible squeal, and my voice sounds like a robot(this is in audacity) in regular sound recorder i get nothing at all

---

### Post by tgalati4 on 2007-06-01
You are experiencing feedback.  Your best bet is to put a piece of tape over the microphone hole or use an external microphone.  This is a common problem on laptops.  You will have to play with the volume/gain control settings in the mixer panel and in the microphone gain slider in audacity to get it under control.

I use a headset mic and it works fine.  The output from the laptop speakers will often feed into the built-in microphone causing feedback.  Poor design usually.  Playing with the sliders will help, but the recording quality is generally poor.  A headset mic will produce a cleaner sound.

---

### Post by residualbit on 2007-06-01
i am using an external mic, and i get the same "feedback" with any input i connect including guitar and synth.....also, any ideas as to why i cant get "sound recorder" to work at all?

---

### Post by tgalati4 on 2007-06-01
Turn off the "Play while recording" in audacity preferences.  Also, in the volume mixer, there is normally a channel that controls the monitor--the amount of signal that gets sent internally in the card for monitor purposes.  Mute or turn this channel down.

Some sound chips are better than others for isolating the recording channel.

---

### Post by OneSeventeen on 2007-06-02
For some reason this problem creeps up on me every once in a while.  While a high-pitch squeal usually does mean feedback, this is not caused by microphone/speaker placement, but by audio processing.

According to [this thread](http://ubuntuforums.org/showthread.php?t=368904) the solution is to install alsa-aoss from synaptic, then launch audacity with "aoss audacity".

I had the exact same problem today, and it did not exist before installing updates.  (I haven't updated my laptop in a little over a month, so I had tons of updates to go through.)

Also, I went to System>Preferences>Main Menu 
then chose "Sound and Video" on the left, 
right-clicked on audacity and clicked "properties"
Then I changed the command to "aoss audacity" (without the quotes)

It worked for me, hope it helps you too.

Also, here is [an uncompressed wav of audacity not working](http://bin.woventhorns.com/bad_audacity.wav).  It has the high pitched squeal and I sound weird.

Here is my [an uncompressed wav of audacity working](http://bin.woventhorns.com/good_audacity.wav).  This does not have the hight pitched squeal, but I still sound weird (but that's just my normal voice this time!)

Please post back if this helped, otherwise we'll keep on troubleshooting.

---

### Post by Dan Lyke on 2007-10-04
Fantastic! This worked on my HP Pavilion dv6000 aka dv6452se, fixing the squeal that also made TeamSpeak unusable.

Thank you!

---

### Post by dinub1 on 2007-10-04
> **nkirk1 said:**
> ok if someone could tell me where to find it, i will post my sound card info...anyway. sound recorder won't work at all, if i plug a mic into my laptop i can hear it through the speakers just fine, but sound recorder will pick nothing up....even weirder...in audacity when i just try to record my voice it records, but then playsback with a high pitch squeal in the background and my voice is nearly indistinguishable, it kind ok sounds like a robot....help!

The high pitc squeal is a feedback from your speakers. When mic is too close to speakers or gain too high you get that effect called feedback. You need to lower either your mic recording level or the volume of your speakers. This way you can avoid the so called "microphony" or feedback, which is a well known fact in mike recording. If you want to hear your sound source with Audacity while recording, enable "monitor input" on your upper right of Audacity menu.

---

### Post by feverfresh on 2007-10-14
> **tgalati4 said:**
> Double click on the speaker volume control on the upper dock bar.  This will bring up the volume mixer control.  Edit preferences and turn on every thing.  I mean every thing.  Now you should see extra volume sliders and sometimes extra options (like 20 dB microphone boost).  Unmute everything and lift every slider to 70%.

Go back into Audacity and hit record.  You should see/hear something.

Hallelujah! I had the same problem and this worked for me. 

I knew the solution to the problem had to be simple. I upgraded my laptop to Gutsy beta last week. I could not get audacity (1.3.3) to record, but I WAS able to record the last episode of Stereo Radiation on Sound Recorder, with disappointing results. Everything is cool now. 

*SIGH* of relief.

---

### Post by feverfresh on 2007-10-15
> **tgalati4 said:**
> Double click on the speaker volume control on the upper dock bar.  This will bring up the volume mixer control.  Edit preferences and turn on every thing.  I mean every thing.  Now you should see extra volume sliders and sometimes extra options (like 20 dB microphone boost).  Unmute everything and lift every slider to 70%.

Go back into Audacity and hit record.  You should see/hear something.

I followed this and was pleased that I can now record. I have now discovered, however, that the speakers in the laptop are not working. The headphone jack does work, so I would not classify this as "urgent," but what would I have to undo to get the speakers working again?

THANKS.

---

