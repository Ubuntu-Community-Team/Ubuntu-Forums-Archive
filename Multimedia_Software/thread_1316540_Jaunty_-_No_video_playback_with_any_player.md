---
title: "Jaunty - No video playback with any player"
date: 2009-11-06
forum: Multimedia Software
---

### Post by stisoulreaper on 2009-11-06
I apologize if this is posted elsewhere, but I haven't found any solutions on the forum which can help me. First off, I'm a bit of a newb, so I'm not familiar with any advanced operations. That being said, I do know how to enter code in the terminal, navigate nautilis and check the synaptic package manager.

Now on to the problem:

I am completely unable to run any videos in any of the video playback programs I have installed (VLC, Mplayer and Movie Player). When I try to open a video, the player opens up for a moment, then closes automatically. I don't get any error messages, and audio works fine with mplayer and vlc (but not movie player). I have tried purging vlc and reinstalling it, to no avail. I even deleted the VLC files in /.config but there was no effect.

As far as I know, my system is fully updated. Does anyone know of a solution to my problem that I could try?

---

### Post by 4Orbs on 2009-11-06
There is a sticky thread at the top of this forum "Comprehensive Multimedia and Video How-To". Follow the instructions step-by-step for your version of Ubuntu, and when you finish the how-to... your media should play.

---

### Post by andrew.46 on 2009-11-06
Hi stisoulreaper,

> **stisoulreaper said:**
> Does anyone know of a solution to my problem that I could try?

Often this means that the video-out device selected by your program will not work on your system. This can be tested in vlc for example by going to:

Tools --> Preferences --> Video --> Output

and selecting an alernative like 'x11 video output'.

Andrew

---

### Post by stisoulreaper on 2009-11-07
> **andrew.46 said:**
> Hi stisoulreaper,



Often this means that the video-out device selected by your program will not work on your system. This can be tested in vlc for example by going to:

Tools --> Preferences --> Video --> Output

and selecting an alernative like 'x11 video output'.

Andrew


Thanks a lot - This fixed the problem for VLC, as well as for mplayer (when i followed the same steps in mplayer's preferences.

----

> **4Orbs said:**
> There is a sticky thread at the top of this forum "Comprehensive Multimedia and Video How-To". Follow the instructions step-by-step for your version of Ubuntu, and when you finish the how-to... your media should play.

I haven't read through this yet (no time yet), but I will, as the problem has yet to be resolved in movie player.

Thanks for the help!!

---

