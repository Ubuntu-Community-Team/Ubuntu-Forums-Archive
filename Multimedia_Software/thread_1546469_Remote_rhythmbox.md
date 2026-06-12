---
title: "Remote rhythmbox?"
date: 2010-08-05
forum: Multimedia Software
---

### Post by malcmail on 2010-08-05
This is probably a long shot but since switching most of my stuff to Ubuntu I've been surprised every day so I thought it was worth asking.
 
I have a server over there ------> 
 
Over here is where my lardy backside resides all day working away <--------
 
My stereo is over there --------> plugged into the server (OK I concede its only kind of a server). The server runs a full desktop version of 10.04. Witha chunk of server stuff on it too.
 
At the moment I use rhythmbox to pick up my podcasts and music on the server and play it out through the stereo. That bit is all good. What isnt so good is the control of it. At the moment I'm using remote desktop from over here <--------- but the mouse movement on screen is a little jerky, a bit laggy and frustrates me a little sometimes.  So...the million dollar question, seeing as I can SSH over to the server can I use any command lines or similar to control rhythmbox (or something similar) so the sound still comes out over there ----->.
 
A long shot - probably but as I said I'm learning whats capable every day and never ceases to surprise me. I've done more with this set up in 3 weeks than I have in Windows pretty much all my days (maybe except visual basic). Who says Ubuntu isn't easy to swap to ;)

---

### Post by perrti-y02 on 2010-08-09
Once Rhythmbox is running over there ----> you first need to ssh over the you need to type in here <----

export DISPLAY=:0.0

I am not 100% sure what this does, but I think it stops the machine here <--- trying to do things locally.

You can then control it with rhythmbox-client and commands such as --play, --next, --previous i,e,

rhythmbox-client --next

As far as I am aware there is no GUI to do it but there is demand for it on the Ubuntu website. [https://wiki.ubuntu.com/rhythmboxWebRemoteControl](https://wiki.ubuntu.com/rhythmboxWebRemoteControl)

Hope that helps.

---

### Post by malcmail on 2010-08-09
Brilliant - thanks for that. I had seen something about mpd as well but couldnt quite fathom out what I had to do where - it looks pretty much like what I was looking for overall. Any good on that? ;)

---

### Post by perrti-y02 on 2010-08-10
Where did you see this about Rhythmbox and MPD? I have looking for anything relating to that for some time now but hadn't seen anything. If you send me a link I might be able to work it out, or at least try...

---

### Post by malcmail on 2010-08-26
Sorry its taken a while. Sadly it wasnt mpd with rhythmbox but with a number of other players. Kind of got it working from my iphone but not 2nd box.

As my server type box is seeing more use now I actually moved to a KVM switch instead.  But before that I tried Subsonic as a jukebox but couldnt get the sound to come out. You may have more joy.

Or see a couple of apps on this page although I havent tried them. [http://live.gnome.org/RhythmboxPlugins/ThirdParty](http://live.gnome.org/RhythmboxPlugins/ThirdParty)

---

