---
title: "Intel sound cards"
date: 2007-05-11
forum: Multimedia &amp; Video
---

### Post by Arry on 2007-05-11
What's the deal with the lack of sound support for intel sound chips? I tried every guide, hack and 'fix' I could come accross, and still so sound.

I'm new to linux so I don't really know how it works, but is there likely to be some sort of official fix or kernel patch or something in the near future? It's very unfortunate, I only installed a few days ago, and I like it so much I've been feverishly tring to get sound sorted almost non-stop, and the fact that I can't do it or get solid support for doing it is a bit of a deal-breaker as far as I'm concerned; I need sound. I'd be alot happier if I could see an anouncment or something saying that the development team is aware of this problem (affecting thousands of potential ubuntu converts), and that a fix is in the works. Someone told me that there is a bug report or something like that regarding the issue, but I don't know what that is or what gets done about it - something should be stickied on the forums, it'd save alot of stress for people trying to make the transistion like me.

---

### Post by tampagault on 2007-05-11
I'm having the same problem, and I've even followed some of the better guides.

I'm completely new to Ubuntu. The funny thing is that when I ran this off the live CD (don't have it anymore) the sound worked perfectly. Now I can't even get a system beep.

Incredibly frustrating. :mad:

---

### Post by tampagault on 2007-05-11
I have found a solution to my problem

[LIST=1]
[*]Open Volume Control (Ctrl +0 or right click volume icon and hit Open Volume Control)
[*]Click: Edit --> Preferences
[*]Under "Select Tracks to Make Visible" click -EVERYTHING- so you can take a look at every track.
[*]Once done, go to the "Switches" Tab which is in the main window of the Volume Control window.
[*]Under Switches you'll see a lot of checked boxes. Check to see if one of the checked boxes is "External Amplifier" and UNCHECK
[*]For good measure, uncheck anything that isn't obviously playback related (like Line-In Capture, or Microphon Capture, you can reactivate if needed later)

[/LIST]

This worked for me. Now I can play sound.

I'm a little shocked that I figured this out. Let me know if that fixes the problem.

---

