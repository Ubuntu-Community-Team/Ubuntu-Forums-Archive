---
title: "microphone weak in Skype"
date: 2010-04-07
forum: Multimedia Software
---

### Post by gnostlos on 2010-04-07
Two different plugin front microphones worked, but the sound is weak and I cannot adjust it.   On the Ubuntu menu under Edit>Preferences>.... there was a slider for the microphone, but that did not help. This is Ubuntu 9.10.  I saw that in this forum, "Configuring webcam and microphone", ajgreeny said:

As regards the microphone, I suggest you run alsamixer in terminal and check that the mic level is set right, it is not muted, and also perhaps that mic boost 20db is on, if needed. You may even have more that one mic listed so make sure you try both, if two are shown in "mic select".

I ran alsamixer and for the only microphone item  "Front Mi" I got:

At the top: Item: Front Mic Jack Mode [Mic In]

Below: No bargraph, just says "Mic In".

This is Greek to me, but it appears there is no adjustment. 

Any suggestions would be appreciated.

---

### Post by gordintoronto on 2010-04-07
You might need to make your command window bigger, just drag the bottom-right corner.

To learn about Alsamixer, use the command:
man alsamixer
(Note: to exit from the manual, tap the "q" key.)

In particular, look at the section headed "keyboard commands," and you will find that the Tab key will cycle among the different view modes. When you're looking at "capture" mode, "mic boost" should be one of the items.

You might even find it handy to have two terminal windows open, so you can read the manual and play with alsamixer at the same time. Mostly, you use the left-right and up-down keys to change volume levels.

---

### Post by alanwalterthomas on 2010-04-07
this is a problem for me too. If I yell into my laptop's microphone during skype's test call my voice comes back just barely audible with my ear right against the speaker with the volume cranked up.
In Sounds - Input I can sometime just barely make the mic indicator move 1 space.
Sound recorder works fine, record/playback at a reasonable volume, so it's not a hardware problem.
I unchecked (& checked just to see) the let skype adjust your sound settings box, but that made no difference.
I opened alsamixer, tab'd to capture & both mic boost & capture volume are maxed out.

Any help getting skype to work again would be wonderful. (lucid beta)

---

### Post by Yingy on 2010-04-07
I couldn't get my mic to work at all in anything.  So when I installed Skype I started to look for a way to enable it.  The post I read said something about Karmic using PulseAudio and that you should use the Pulse Audio Control Volume, **pavucontrol** in repositories.  I set it up for my sound card and I had my mic up and running sounding crisp and clear.  Make sure you have the right profile selected for your card.

---

### Post by lidex on 2010-04-08
For help configuring skype with pulseaudio scroll to the "Skype" section on this page:
[http://pulseaudio.org/wiki/PerfectSetup]("http://pulseaudio.org/wiki/PerfectSetup")

Remember if you set the option in skype to allow it to control sound settings it can affect system audio. So if you find volume issues go to alsamixer/gnome-alsamixer to reset.

---

### Post by gnostlos on 2010-04-08
Gnostlos here again.  I am unfortunately understanding nothing of what my responders have so nicely offered.

Alsamixer did not have a volume bar for the microphone, so I could not turn it up.

One of the most baffling remarks was Ying's, which left me feeling somewhat inferior as I understood not a word of it:

The post I read said something about Karmic using PulseAudio and that you should use the Pulse Audio Control Volume, **pavucontrol** in repositories.  I set it up for my sound card and I had my mic up and running sounding crisp and clear.

Similarly, the reference [http://pulseaudio.org/wiki/PerfectSetup](http://pulseaudio.org/wiki/PerfectSetup) went on at some length, offering so many casually mentioned possibilities that I could not follow it.

My speaker works fine.  The microphone does work, but it is very faint.  If anyone still has simple suggestions, I'd appreciate it.

---

### Post by gnostlos on 2010-04-08
(This is gnostlos:)  I found pulseaudio's web site and downloaded pulseaudio and pavucontrol.  Pavucontrol said the microphone volume was 100%, but it is still very weak.

---

### Post by kleskjr on 2010-04-08
sometimes skype plays tricks and decreases the mic input. from skype options you can disable the automatic microphone adjustment. Although this solved my problem I am not sure if you have the same issue.

---

### Post by alanwalterthomas on 2010-04-08
I'm finding some weird behaviour, but no good results.
I tried pavucontrol but it didn't help. Under input devices there are two items for my computer (acer aspire one netbook) if I choose to show all input devices - Monitor of Internal Audio Analog Stereo & Internal Audio Analog Stereo. I'm not sure what the monitor's for, but muting it did nothing even while recording using sound recorder so I doubt it's the problem. What's weird is the Internal Audio Analog Stereo volume control. I affected sound recorder, meaning I was able to shift sound right, left, & off. Therefore there is some connection between sound recorder and what I did in pavucontrol. What's weird: If the left & right input controls were at the same level, the input meter below the volume controls wouldn't pick up anything, or it might twitch; if they were different (right maxed, left silence) it would strongly indicate that it was picking up my voice. The bigger the difference between them, the more the computer said it heard me. Nevertheless, sound recorder picked me up as it should have given the volume level to be recorded for each of the stereo tracks regardless of what the computer indicated it was hearing.
So I've describe this with as much detail as I can. If anyone is or knows an ubuntu sound expert, please help me figure out how to solve this. (or wait, seated, for the open-source skype client)

---

### Post by gnostlos on 2010-04-10
Alanwalterthomas: as you seem to be having as much trouble as I do, I'll mention that the preceding suggestion by kleskjr may have helped me.  (I cannot be sure from the test call, and the friend who is helping me has wireless trouble at the moment.)  I'll give the details, as I think this is what kleskjr meant.  In the lower left corner of the little Skype box (the connection box, not the web site) there is a tiny black triangle which gives the Main Menu.  Go to Options>Sound Devices.  There is a little box that says "Allow Skype to automatically adjust my mixer levels".  Remove the click from that box.  It may help.

---

### Post by alanwalterthomas on 2010-04-11
tried that long ago. didn't help. thanks anyway.

---

### Post by lidex on 2010-04-11
Can you post a screenshot of alsamixer?

---

### Post by alanwalterthomas on 2010-04-16
No need to post alsamixer, it's quite normal. No need also because

I FIXED IT!!!

To recap - 
the problem - skype couldn't hear my voice
other symptoms - sound recorder recorded my voice without problems; in pavucontrol my voice would not register if under input devices both front left & front right were at the same level - but would register if either side were set to base or silence. This way my voice would also appear to register in input in the regular volume control.

Solution:

Make a test call using skype, then work fast because you only have about 20 seconds to make the change.
Open pavucontrol & go to Recording. While skype's test call is active skype should appear as another item in the list. To the right side is an option to select the source. My source had been set to Montior of Internal Audio Analog Stereo; when I changed that to just Internal Audio Analog Stereo, skype suddenly sprang to life & I got to hear the last numbers of the 10,11,12... sequence I was saying in time to the call time meter. Afterwards, skype worked perfectly, loud & clear.

I don't know why skype was automatically configured to use that useless source, but if your audio mostly works & the problem is that skype doesn't hear you, try the above.

---

