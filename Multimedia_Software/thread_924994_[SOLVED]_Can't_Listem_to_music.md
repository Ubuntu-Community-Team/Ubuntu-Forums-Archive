---
title: "[SOLVED] Can't Listem to music"
date: 2008-09-20
forum: Multimedia Software
---

### Post by parnmatt on 2008-09-20
Ok, the low-down.
I'm fairly new at linux, so don't know how to fix stuff as well as the next linux user.

I am using Ubuntu/Ubuntu Studio (after Ubuntu studio didn't let me use the internet, i re-installed my Ubuntu and upgraded/installed everything to make it into Ubuntu studio, inc. themes, logins, 'the look' etc.)
And I can listen to the start-up music, but nothing else.
Since re-installation i haven't been able to listen to any form of music.
I use Rhythmbox Music Player usually, and when that didn't work i used Amarok (now unistalled) -- even Totem couldn't read my music.
I run a dual boot between XP and Ubuntu --only use xp for iTunes and one other program -- so all my music is in *.m4a format, as normal it said it wanted the codecs and then it downloaded them so i could .... as was the first couple of times i installed it. But it can't read them.

Totem comes up with an error (the others don't physically show the error, they just have a fit) and it says:

**An error occurred**
Failed to connect stream: Invalid argument.

what's wrong and how can I fix it???

---

### Post by BattousaiX on 2008-09-20
Your error doesn't give much details.

How long have you worked with that error?  Most issues unless already frustrated I've looked over myself for a few hours and seem to wind up learning more.

In addition, there are many guides like this to look at.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by markbuntu on 2008-09-20
If you are using UbuntuStudio, you are probably also using jack. To get applications like rythmbox and firefox flash to play through jack, you should read my guide:


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by parnmatt on 2008-09-22
i have apps that require JACK, but i don't have the jack server installed - and i can't figure out how.
Ok a but of an update. I can here all sound from the internet and music the OS itself plays on login..etc, but I still can't listem to my personal music files.


> **markbuntu said:**
> If you are using UbuntuStudio, you are probably also using jack. To get applications like rythmbox and firefox flash to play through jack, you should read my guide:


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by parnmatt on 2008-09-22
Another update

> **markbuntu said:**
> 
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

I used the link to see if anything changed ... and as soon as I followed the first step of turning everything to ALSA -- i had it on auto-detect and i clicked:

**Sound Events**
Sound playback: *Autodetect* Test

and i get this error:
*audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument*


**Music and Movies**
Sound playback: *Autodetect* Test

*audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Failed to connect stream: Invalid argument*


**Audio Conferencing**
Sound playback: *Autodetect* Test

*audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Failed to connect stream: Invalid argument*

Sound capture: *ALSA - Advanced Linux Sound Architecture* Test

*gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Failed to connect stream: Invalid argument*

---

### Post by markbuntu on 2008-09-22
Did you try the other steps before you did that?


Since yours sound it sort of working, you can skip down to the Multiple Application Sound Sharing section to straighten out that problem.

---

### Post by SuperSonic4 on 2008-09-22
What does ```
sudo apt-get install faac faad faad2
``` give? (faac and faad/faad2 are AAC encode/decode respectively)

---

### Post by parnmatt on 2008-09-23
There was no steps really before that, but i made a couple of changes suggested, and It works fine now.

Cheers

> **markbuntu said:**
> Did you try the other steps before you did that?


Since yours sound it sort of working, you can skip down to the Multiple Application Sound Sharing section to straighten out that problem.

---

### Post by driven1 on 2008-09-24
> **parnmatt said:**
> There was no steps really before that, but i made a couple of changes suggested, and It works fine now.

Cheers

So what did you do to fix it? I have sound working, but none of my music will play. I installed the medibuntu codecs, but still no joy.

---

### Post by parnmatt on 2008-09-25
> **driven1 said:**
> So what did you do to fix it? I have sound working, but none of my music will play. I installed the medibuntu codecs, but still no joy.

Go to System/Preferences/Sound and switch everything to ALSA from auto-detect.
that's pretty much all i did.

---

### Post by driven1 on 2008-09-25
That did the trick, suddenly everything is on :)

---

### Post by soumyajit pramanick on 2008-10-09
i am facing similar prolem on my laptop. and parnmatt's solution didn't fix it. can anyone help?

---

### Post by minky311 on 2008-10-09
What seems to be the problem and are you getting any errors?

---

### Post by soumyajit pramanick on 2008-10-10
here's my problem in detail

1. suddenly alsa has stopped working. and as a result rhythmbox, amarok and lastfm are not working.

2. i went to system>preferences>sound and tried all the tests.
getting some strange errors like
'audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not get/set settings from/on resource.'

3. swithiching the default sound playback from 'autodetect' to 'OSS' makes Rhythmbox work,but amarok and lastfm are still mute.
and also i cand hear any sound while watching flash videos in firefox(youtube etc.)

please help!

---

### Post by Philo1 on 2008-11-15
> **parnmatt said:**
> Go to System/Preferences/Sound and switch everything to ALSA from auto-detect.
that's pretty much all i did.
Thanks for this info. I reverted back to 8.04 and have had this problem for two days with Firefox and a couple of audio apps, issue fixed.

---

