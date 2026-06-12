---
title: "Problems with LiveTV with v4l cards"
date: 2012-01-10
forum: Mythbuntu
---

### Post by cara1968 on 2012-01-10
I've used Myth 0.23 for a long time now, having 3 v4l cards on the backend. Everything worked but the image quality wasn't great.
So I got a new set of v4l cards and upgraded to 0.24.1 (v0.24.1-120-g294968b). Well, crap, LiveTV starts but changing channel throws the frontend into a fit of errors. The bulk of them are :

> 2012-01-10 06:09:30.361 AFD Error: Unknown audio decoding error
2012-01-10 06:09:30.361 [mp1 @ 0x2020b00]Header missing
2012-01-10 06:09:30.361 AFD Error: Unknown audio decoding error
2012-01-10 06:09:30.361 [mp1 @ 0x2020b00]Header missing
2012-01-10 06:09:30.361 AFD Error: Unknown audio decoding error
2012-01-10 06:09:30.361 [mp1 @ 0x2020b00]Header missing
2012-01-10 06:09:30.361 AFD Error: Unknown audio decoding error
2012-01-10 06:09:30.361 [mp1 @ 0x2020b00]Header missing
2012-01-10 06:09:30.361 AFD Error: Unknown audio decoding error

Others, accompanied by noises I haven't heard since learning to program a AY-3-8910 chip on a ZX-81, are :

> [mp3 @ 0xad66b470] incorrect frame size
[mp3 @ 0xad66b470] Header missing                                               
    Last message repeated 71 times                                              
[mp3 @ 0xad66b470] incorrect frame size
[mp3 @ 0xad66b470] Header missing                                               
    Last message repeated 71 times                                              
[mp3 @ 0xad66b470] incorrect frame size
[mp3 @ 0xad66b470] Header missing                                               
    Last message repeated 71 times                                              
[mp3 @ 0xad66b470] incorrect frame size
[mp3 @ 0xad66b470] Header missing       

I thought that this problem was already solved as I had read some post about problems with channel changes, but apparently not.
And 0.25 is even worse; it won't even do more than a couple of frames of LiveTV.

Apparently v4l card support is getting dumped from Myth as it keeps getting worse and worse. Is this so or is there hope ?

P.S. I'm posting this here as the packages I'm using are from the Mythbuntu repositories.

---

### Post by jlp_engineer on 2012-01-13
I too am having issues with LiveTV and analog capture cards.  I have a few PVR-150 cards in a backend running Mythbuntu 8.10, and with that software load, everything works just fine.  I advance to 9.10, 10.10, and finally 11.10, and things begin to go wrong.  With the later versions, I seem to be able to pick up the first PVR-150 at whatever default station it is on, and even changing channels on the first card seems to go OK 90 percent of the time.  My trouble comes when I switch to the second PVR-150.  With v9.10 I get distorted video, that stutters, and breaks up.  With Mythbuntu 10.10 I get the same on the second card, with occasional blank screens that seem to lock up the frontend, and I have to re-start the backend.  With Mythbuntu 11.10 I get similar behavior to version 9.10, but without the blank screen lockups (one step forward, two steps back) :-).

I have read thousands of posts and as much other information as I could get my hands on, but nothing has helped identify this issue.  Seems like the causes for this are many, and everything from PCI latency to DMA buffering can cause it.  I just cannot believe that I have to go back to 8.10 for my analog tuners to work.  I agree with you...it seems as if support for IVTV and V4L analog tuners is just breaking down and no one notices or cares.  Support for the digital tuners seems to have taken over all development attention, even though I believe that the bulk of MythTV users are still watching standard definition channels along side of the few digital channels that are transmitted in clear QAM (local broadcasters).  I live in a rural part of South Dakota, and the cable providers here transmit the bulk of their digital channels encrypted, and have "basic" standard definition channels transmitted on analog cable frequencies, with no plans to change that lineup any time soon.

My troubles started with not being able to do analog channel scans with my PVR-150's when I loaded up 11.04, but I have now ended up back where I started some 3 to 4 years ago, running version 8.10.  I may end up just running version 8.10 for a period of time, while I continue to research all the issues I have encountered.  BTW, analog channel scans are only partially functional in Mythbuntu 9.10, and completely broken in 10.10 and 11.10.  More evidence that the analog side of things continues to atrophy from lack of attention. 

I am a hardware engineer, and not so much of a programmer.  But I have considered using my feeble programming skills to see what I could do, if I even knew where to look for the cause of the issues I am seeing.  I can't help but consider the possibility that the issues we are seeing are related.

Good luck to you in your quest.

---

