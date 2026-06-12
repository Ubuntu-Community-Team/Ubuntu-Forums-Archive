---
title: "Timidity works great - no sound in Rosegarden - SOLUTION"
date: 2014-08-08
forum: Multimedia Software
---

### Post by halfvulcan on 2014-08-08
Hi all. I wanted to nip this problem for whoever else is having it. I would repeatedly have this problem of no sound in Rosegarden, despite my having installed and properly configured timidity, Rosegarden, etc.  For me, just running timidity -iA didn't solve the problem. And I noticed it wasn't solving it for a number of others either in a somewhat old, though, I'm sure, still applicable thread (midi is not the fastest moving in development). I wanted to tell you how I solved it without resorting to bizarre means I've seen others resort to that they just shouldn't have to. What I mean is, you shouldn't have to install qsynth, sound systems other than alsa, jack, none of that ****.  Because this solves it. For me it did anyway. And no one in the other thread that was closed (why do people insist on closing threads?) gave this solution.

Rather than timidity -iA, do this in a terminal:
timidity -iA -B2,8 -Os1l -s 44100

Then, with the terminal still open, restart rosegarden. Try playing something. It plays? Problem solved. It doesn't? Maybe try making sure your midi devices preferences in Rosegarden are configured for the timidity server. 
Why this works, I haven't figured out completely yet. I think I did figure it out years ago, but can't remember. It isn't in my files.

I generally refer to this guide 
[https://help.ubuntu.com/community/Midi/SoftwareSynthesisHowTo](https://help.ubuntu.com/community/Midi/SoftwareSynthesisHowTo)
when setting up timidity. This solution was from that.

I should mention, the problem and solution above are possibly only applicable if you, like me, don't have pulseaudio or jack or other sound servers installed. I don't know much about all that, except that I tend to smell bloat and maybe a bit of latency in a lot of those things so I tend to steer clear of them.

---

