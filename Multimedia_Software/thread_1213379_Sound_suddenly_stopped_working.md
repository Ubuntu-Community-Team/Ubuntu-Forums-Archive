---
title: "Sound suddenly stopped working"
date: 2009-07-14
forum: Multimedia Software
---

### Post by ebineesey on 2009-07-14
Hi-
I'm a novice ubuntu user so please bear with me as I don't know all the lingo or how to cary out any of the terminal commands.

Sound suddenly stopped working in ubuntu. I have a dual OS, and sound in windows works perfectly fine. So it's not the speakers or the soundcard or anything else as far as hardware is concerned (i don't think...)

Not sure when it happened or why...
any ideas?
Volume is turned up as far as I know (on the speaker, as well as the sound controls in ubuntu). Can't play mp3s, mpegs, etc-- or at least can't hear the sound anyway. System sounds dont play either (the login music, etc). 

Thanks for any help--

---

### Post by igorzwx on 2009-07-14
I may try to help, if you would tell which Ubuntu you have (9.04 or else).
And more info about your box

---

### Post by ebineesey on 2009-07-14
> **igorzwx said:**
> I may try to help, if you would tell which Ubuntu you have (9.04 or else).
And more info about your box
Jauntry 9.04, yes. 

My computer is an AMD 7750 dual-core, 4gb ram, and i'm using an old sound-blaster soundcard because my speakers are digital and don't work with the onboard sound on my mobo. 

But sound has worked in the past, since 8.10-- i think. 

I did notice something a while back, but this had always been the case:
When I'm listening to an mp3/video/etc and want to turn the sound down, the main sound control has no effect (the speaker icon at the top by the clock). Instead I had to control the sound in the application (be it something in the browser, or a different program). I thought this was strange because if I muted the speaker icon at the top, I still had sound at whatever volume in other applications. Not sure if it muted system sounds or not but that's besides the point.

I don't know how to troubleshoot this issue of having no sound now. Again, everything works fine in windows (usually it's the other way around).

---

### Post by igorzwx on 2009-07-14
Your box may work with Pulse, perhaps.

Step 1: System -> Preferences -> Sound
change everything to pulse

actually, solution is very simple.
you have already pulse-audio installed, I presume.
Open Synaptic, install all the Pulse tools.
There should be something like pulse control, or pavucontol, or else.
with this thing you can move audio stream where you want with one
click of the mouse.
There should be howto. I tried it, it works.
I cannot help more, because I have already removed both Pulse and ALSA,
and installed an alternative sound system.

google -> ubuntu pulseaudio
google -> markbuntu pulseaudio

Tell how it works.

You can also ask markbuntu, he knows everything about pulse

---

### Post by ebineesey on 2009-07-14
Pulse didn't do anything.
I changed everything to "pulse audio sound server". No change.

I downloaded pavucontrol from synaptic-- opening up the pulse audio device chooser, as well as the volume control, doesn't do anything. Everything shows as audible percentages but I don't hear anything. 

Also, the pulse dropdown menu (near the clock) says "Default Server, Sink, Source" None of these show anything-- each says "no network devices found".

I went through the "configure local sound server" dialog and no changes resulted from checking/unchecking the variou boxes. 

The volume-meter playback shows sound in the bars which may or may not move in accordance to the beat of an mp3 I tried to play, but I don't hear anything.

---

### Post by igorzwx on 2009-07-14
Ask markbuntu, he knows everything

---

