---
title: "M-audio delta 44 alsa question"
date: 2008-01-16
forum: Multimedia Production
---

### Post by AzraelSlain on 2008-01-16
Ok, i finally went out and got a delta 44 to use with Ubuntu. I got it to work with Ardour, only problem is the outs are unbalanced, so out 1 i get everything in just the left channel. I'm sure i'm just missing where to go to turn all 4 outs on my card stereo, where in the alsa mixer do i turn to? outside of that, I'm friggin excited as hell that i finally got this far, i went rounds with my tascam us 122 till i gave up and got the delta 44. Help on this would rock so much,

---

### Post by Stochastic on 2008-01-16
is this the case all the time (sound events to sign in, movie player, etc...) or merely inside ardour?

You card only has mono outputs, four of them, so you'll only ever be able to play two stereo channels.  If my memory serves correct.

---

### Post by tgalati4 on 2008-01-17
>sudo apt-get install envy24control

>envy24control

---

### Post by AzraelSlain on 2008-01-17
this is the case with anything ran though the delta. What i did was connect a Y cable to both out 1 and 2 and then my headphones to the in on the end of the Y cable, but still all i get is everything though just the left channel. I messed with envy24 a bit, but still just left channel, id just get more of it. Muted one channel, still left. So how does everyone get balance here? Anyone else got a M-Audio Delta 44?

---

### Post by tgalati4 on 2008-01-18
I have a Delta 66 (which is a Delta 44 with stereo digitial in and out--making 6 inputs and 6 outputs).  I have the Omni I/O headend which contains two mic preamps and two headphone monitors.  I've never experienced this problem.

I use it with Dynebolic Live CD.  It's a real-time kernel that's optimized for music recording.  Give it a spin and see if the behavior changes.

As I don't have the standard head end, I can't say how the jacks are arranged.  Do you get a mono signal out of each individual output?  If so, then it's working.  Also, the Delta series card uses "balanced" audio connections.  Shield, hot, cold or 3-pin connection--TRS.  They are not stereo connections.  You need a proper Y connector--TRS mono and TRS mono on one end and stereo 1/4" on the other.

---

### Post by Stochastic on 2008-01-18
I have a Delta 44 in my old computer and upon many re-installations of many different linux distros I've never(or at least rarely ever) experienced any difficulties with the card.  If it was to work, it would work in fully duplex quad audio.

I'm guessing it's something with your 'y' cable setup or possibly levels inside alsamixer.  Can you double check that the 'y' cable is a dual-mono to single-stereo 'y' cable and not a dual-stereo to single-stereo splitter?  This would take both signals and mix them together onto the same channel of the stereo mix (giving the scenario you're describing).

---

### Post by AzraelSlain on 2008-01-30
Ok, Ive figured out how to make everything stereo finally with the help of my behringer mixer. Now the problem i have is being able to audition while playing back. For example, with my Tascam us 122 and Acid pro i could load drum samples up and then listen to them play back and hear my guitar and jam out while the samples are playing. But now what happens is as soon as i hit play in Ardour, the guitar cuts out till i hit stop, then it returns. So how do i route the audio so i can hear playback in ardour and hear the incoming signal of my guitar at the same time?

---

### Post by AzraelSlain on 2008-01-30
Great, now i can't get any input now, i can get output but no input now

---

