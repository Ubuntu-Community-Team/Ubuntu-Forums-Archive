---
title: "laptop based remote control for MythTV"
date: 2010-03-17
forum: Multimedia Software
---

### Post by bjdekruif on 2010-03-17
Hello all, 

I am running mythbuntu on a computer that is connected to my television and stereo. 
Most of the time, I use this system to play my music, and not for watching television. As a result, the TV is often off.

I would like to control my music with my laptop. Several solutions are possible, but they don't do what I think is best:
- VNC:    too slow, fonts not optimised for laptop
- telnet: no visual feedback
- x2x:    love the idea, but still needs my tv turned on. 

I just installed MythWeb, and I really like that interface. It is easy to make playlist, scroll through your music, and select what you want to  hear. However, when I push 'play' it starts streaming... It is not playing over my stereo.

Is there a laptop based remote control, on which the visual feedback is optimised for working behind a laptop. E.g. the MythWeb interface, but play means play on the frontend, not streaming to the laptop.

Hope somebody knows how this can be done...

Any help is welcome
Bas

---

### Post by Chris Musampa on 2010-03-17
I don't know if you've tried X forwarding, I use it for precisely what your asking.  Media server (with amarok installed) behind the TV and speaker system attached.

On my laptop I can type in a terminal:
```
ssh -X username@serveripaddress
amarok &
```
I then have Amarok's interface on the laptop but sound produced on the server.

I actually have key authentication setup so I don't need a password to login to the server, so instead of using the above terminal commands I click a couple of desktop shortcuts containing:
ssh -X username@serveripaddress amarok &
and
ssh -X username@serveripaddress kmix &

---

### Post by bjdekruif on 2010-03-17
Hey Chris, 

Thanks for your reply. I will try your solution to see how I like it. This certainly will be working. 

I was hoping to keep it all centralised: keep mythtv as the system that will take care of all my music and if I want to watch TV, that I can use it. I try to minimise the number of programs that I need. That's why I began with loving the MythWeb interface, until I found out that it only worked for streaming. 

Thanks

Bas

---

### Post by Chris Musampa on 2010-03-17
My server is also a mythbuntu box and mythweb is superb for sheduling/managing recordings etc, much faster and easier than using the onscreen tv guide/menus IMO. I just hate the music interface in myth, I find a proper music player much easier to use with drag and drop for making playlists.

---

