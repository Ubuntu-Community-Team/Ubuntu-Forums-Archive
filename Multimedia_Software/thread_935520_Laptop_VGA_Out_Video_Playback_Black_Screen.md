---
title: "Laptop VGA Out Video Playback Black Screen"
date: 2008-10-01
forum: Multimedia Software
---

### Post by solarwind on 2008-10-01
Hey all, I have a Dell Inspiron 6000 laptop with ATI x300 mobile graphics. I have Ubuntu 8.10 Hardy Heron.

I have a projector which can connect to the laptop via VGA out. When I plug in my laptop, everything seems to work fine. I see my desktop as I should. If I try to play a video with VLC or the default video player in Ubuntu, there is a black screen where the video *should* be. I see no video, just a black area where I should be seeing video. On the laptop screen it works fine, but on the tv screen, there's just that black screen. Why is this happening? Could I somehow change the output mode of VLC or something maybe?

All help will be much appreciated. I have to use my laptop and projector for presentations and not being able to play video on the projector means big trouble for me.

---

### Post by solarwind on 2008-10-02
Bump.

---

### Post by solarwind on 2008-10-02
Another bump. This is immensely annoying.

---

### Post by solarwind on 2008-10-04
Bump.

---

### Post by ee19921 on 2008-11-18
> **solarwind said:**
> Hey all, I have a Dell Inspiron 6000 laptop with ATI x300 mobile graphics. I have Ubuntu 8.10 Hardy Heron.

I have a projector which can connect to the laptop via VGA out. When I plug in my laptop, everything seems to work fine. 

All help will be much appreciated. I have to use my laptop and projector for presentations and not being able to play video on the projector means big trouble for me.
Hey, how did you setup the projector to work? When I connect my laptop to my school projector and Fn+F8, no response at all in the projector? Is there a HOW-TO thread for setting it up?

TIA!

---

### Post by solarwind on 2008-11-18
> **ee19921 said:**
> Hey, how did you setup the projector to work? When I connect my laptop to my school projector and Fn+F8, no response at all in the projector? Is there a HOW-TO thread for setting it up?

TIA!

Nope. It's as simple as plugging in the cable. You need to use the special Fn keys on your laptop to redirect the video output though. Nothing special needs to be done.

---

### Post by ee19921 on 2008-11-19
> **solarwind said:**
> Nope. It's as simple as plugging in the cable. You need to use the special Fn keys on your laptop to redirect the video output though. Nothing special needs to be done.

I don't know. It doesn't work on my laptop. I see the graphics cards are different, wonder if that is the reason?

---

### Post by solarwind on 2008-11-19
> **ee19921 said:**
> I don't know. It doesn't work on my laptop. I see the graphics cards are different, wonder if that is the reason?

Highly doubt that's the reason. Try connecting to an external monitor first and use the FN keys to redirect video output. On my dell 6000, it's the **Fn + F8** keys. Cycle through video output modes.

---

### Post by ee19921 on 2008-11-20
> **solarwind said:**
> Highly doubt that's the reason. Try connecting to an external monitor first and use the FN keys to redirect video output. On my dell 6000, it's the **Fn + F8** keys. Cycle through video output modes.

Thanks, I will try that and post the results.

---

### Post by newbyoob on 2008-11-20
I'm running into the exact same problem. Sony Laptop with an ATI chipset hooked up to an external screen. Everything works fine except video, I can hear audio and it seems to play smoothly but no video will display.

---

### Post by solarwind on 2008-11-20
> **newbyoob said:**
> I'm running into the exact same problem. Sony Laptop with an ATI chipset hooked up to an external screen. Everything works fine except video, I can hear audio and it seems to play smoothly but no video will display.

What do you mean no video? You mean you see absolutely nothing on your external monitor or just when watching movies you see a black area where the movie is supposed to be?

My problem is that I see a black area where the movie is supposed to be, but everything else is working fine.

---

### Post by newbyoob on 2008-11-20
Just black where the video is supposed to be, everything else is fine. I can see the player, the audio works and the video time scroller moves forward, but where the video should be there is just black.

---

### Post by cabinetman on 2008-11-25
I have solved this problem by changing the video driver in your dvd player to Opengl. I hope this will help you.:)

---

### Post by hayim on 2008-12-01
> **cabinetman said:**
> I have solved this problem by changing the video driver in your dvd player to Opengl. I hope this will help you.:)

Hey Cabinetman! thanks that totally worked!!

i was having the same problem with outputting my video (VGA) to a 22inch ViewSonic lcd!

HOWEVER, the problem only occurred at highest res (1680x1050) - so maybe its a video card / xorg / set up issue?

But it works with opengl driver - ill try some of the others too.

---

### Post by solarwind on 2008-12-01
> **cabinetman said:**
> I have solved this problem by changing the video driver in your dvd player to Opengl. I hope this will help you.:)

How do you change that?

---

### Post by ee19921 on 2008-12-01
> **solarwind said:**
> How do you change that?

In VLC, check in preferences, video, output.

---

### Post by cabinetman on 2008-12-04
In Mplayer right click on screen and then preferences/video. I didn't find a way to do it in movie player.

---

