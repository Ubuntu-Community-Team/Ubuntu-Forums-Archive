---
title: "Can't play DVDs in Totem"
date: 2007-06-12
forum: Multimedia &amp; Video
---

### Post by Smeerkat on 2007-06-12
Hi,

I'm new to Ubuntu and have been setting up my feisty (7.04) system over the last weeks.
So far I'm very impressed with it and have had mostly success with installation of various
applications.

I followed a recent sticky thread on how to install DVD playback capability and Win32 codecs.
This install seemed to go fine until I tried to play a DVD using Totem. I get the message that Totem
can't play this media format unless I install the correct plugins.

What plugins do I need? I have installed the Medibuntu stuff, libdvdcss2 and w32codecs as per
the recent thread.

I'd be very grateful for any helpful suggestions to get Totem to play DVDs!

TIA,

David :(

---

### Post by yabbadabbadont on 2007-06-12
From the Ubuntu wiki: > Note : While Totem-gstreamer can play a DVD automatically when it is inserted into the DVD drive, it cannot navigate the DVD nor play it by selecting Movie &#8594; Play Disc 'DVD Name'.
However, it does contain information on getting the ability to play DVDs.

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Read through that and see if there are any steps in it that weren't listed in the stickied thread that you followed.

---

### Post by Smeerkat on 2007-06-12
HI,

Thanks for this link - that has solved the problem.

I installed the version of Totem with the xine back-end and also the 
libxine1-ffmpeg package, which was missing.

Now works perfectly!

I hope that not having the gstreamer version won't effect anything else, but I'll
cross that bridge when I come to it. 

Thanks again for the tip.

David :D

---

