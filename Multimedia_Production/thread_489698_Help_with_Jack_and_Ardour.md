---
title: "Help with Jack and Ardour ?"
date: 2007-07-01
forum: Multimedia Production
---

### Post by Drakkor on 2007-07-01
Ok, I have the repos ubuntu studio, not the OS ubuntu studio, so it's not Ardour 2.0, the exact version number should not be the problem, I have managed to record several tracks from my midi keyboard to Ardour, and could play them back before,but after recording, I got a terrible whining sound, so anyway, long story short,
what do I have to do to make the Ardour tracks so I can hear the playback, seems to be a Jack problem, but 
I have everything connected !  :(

---

### Post by fredj on 2007-07-05
How is your jack server setup? How many frames and periods are you using ? What is the latency?
Are you running Jack in Realtime?

What sound card are you using? Run the jack server through qjackctl, open the status window and start
jack so that you can see if there are any problems. Are there any Xruns? Can you record and playback
audio using audacity without jack?

Can you record and play back audio through Audacity when jack is running. Don't forget to go to the
EDIT -> Preferences in Audacity and set it up to use jack when you are doing this last test. 
How many tracks are you trying to play back at once. What CPU does you computer have?
We need much more information before we can help you.

---

### Post by fredj on 2007-07-05
Just noticed that it is midi playback that is not working. Do you have Qsynth loaded with a soundfont. How were
you playing back midi when it worked?

---

### Post by Drakkor on 2007-07-05
Ya, fredj, been awhile, but I could hear the tracks in the "Audition' mode.
I have a Soundblaster Live 5.1 soundcard, and in Fiesty, it doesn't  even give me
any input sources in Audacity. i'm using ZynAddSubFX and Ardour

---

### Post by paulg on 2007-07-06
> **Drakkor said:**
> Ok, I have the repos ubuntu studio, not the OS ubuntu studio, so it's not Ardour 2.0, 

Adding the repositories is basically the same thing as installing (or rather _can_ be with some additional tweaks). The core of Studio is still Feisty. Very few packages  I very briefly experimented with Ardour 1.x prior to installing the Studio repositories and there is a drastic difference between the two. 

If you're not using 2.0 I highly, highly recommend you upgrade to it. Purge Ardour first (to remove all the 1.0 components), then move the Studio repository to the top of your sources.list file, run an apt update and reinstall Ardour and it will select the studio repository copy from the top of the list. It will probably update any other audio programs that you have installed that are in the Feisty and Studio as the Studio repository has more current versions (or the same) for many of the applications. 

I had this problem when I first added the Studio repositories. Ardour 1.0 had been installed previously and I could only get 2.0 after purging 1.0. Everything else that had an equivalent package in Studio was replaced fine.

---

