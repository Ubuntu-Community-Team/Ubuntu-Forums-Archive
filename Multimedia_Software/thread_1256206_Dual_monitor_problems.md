---
title: "Dual monitor problems"
date: 2009-09-02
forum: Multimedia Software
---

### Post by Lucky75 on 2009-09-02
Hey all,

I am running into an annoying problem with dual monitors.

One is a 19"(left), and the other is a 22" (right, primary). I have them set up using twinview with my NVIDIA cards. Using the nvidia drivers.

Whenever I try to fullscreen a flash video in firefox, it does three things:

1) It always moves to the left monitor, regardless of where firefox is running from.
2) It either shrinks the image and distorts it, or tries to stretch it across both monitors
3) It restores back to being embedded into the web page when I click on anything on the other monitor.

Any ideas how to fix these issues? 

I also can't seem to get the absolute positioning to work properly. It likes to make programs think there is extra space off screen (at t the top?) for my smaller monitor, so that when I maximize windows, the bars are always off screen and I can't see them. Switching to automatic positioning fixes the problem, but it's a bit annoying since one monitor is slightly higher than the other.

Thanks for the help!!


Running Gnome on Jaunty.

---

### Post by Lucky75 on 2009-09-02
bump, help please :)

---

### Post by bear24rw on 2009-09-02
Is each monitors native resolution being correctly identified by nvidia-settings?

---

### Post by Lucky75 on 2009-09-02
Yeah,that all seems to be fine. It doesn't like flash though.

Actually, I think the absolute positioning works now, it's just the flash.

Youtube likes to stretch across one screen and a bit of the other (or seems like that would be the width if it did span the 2nd screen), while others just screw up the resolution and make the fullscreen picture play in a subset of the total screen size (from the top left corner) on the lower resolution, left, secondary monitor.

---

### Post by Lucky75 on 2009-09-02
Hmm, now that I switched to absolute, youtube also just shrinks the video to a portion of the screen.

I took a picture of the monitor (couldn't screenshot without the fullscreen closing down lol)

---

### Post by Lucky75 on 2009-09-03
bump

---

### Post by Lucky75 on 2009-09-03
bump

---

### Post by Lucky75 on 2009-09-03
bump

---

### Post by overdrank on 2009-09-03
Hi and please do not bump your thread so quickly, once a day is polite to the community. :)
Which nvidia driver version and have you tried any others?

---

### Post by Lucky75 on 2009-09-03
Hey, yea, sorry, I usually try not to bump so often, but it was a few pages down, so I figured that it wouldn't be that big of a deal.

Anyways, I'm using 180.44 at the moment. Not too sure what the latest is?

---

### Post by Lucky75 on 2009-09-06
bump

---

### Post by Lucky75 on 2009-09-07
Does anyone have any suggestions?

---

### Post by markbuntu on 2009-09-07
Full screen flash will be positioned at 0,0 which is the top left of your left most monitor. There seems to be no way to change this default behavior. Bugs have been filed with the flash devs but it does not seem to be a priority for them.

---

### Post by Lucky75 on 2009-09-07
Sure, that's fine, but I still have a **problem with the size of the video**, as can be seen in the picture I attached earlier. I guess because one of my monitors is larger and of a higher resolution than the other? That's the truly annoying part. Any way to fix that? 

Also, how would I make it so that it doesn't go back to regular size from full screen if I click on the other monitor? I know there's a hack one can do in windows with modifying the DLL in a hex editor, but obviously that won't work for linux.

---

### Post by Lucky75 on 2009-09-08
bump

---

### Post by Lucky75 on 2009-09-09
bump

---

### Post by Lucky75 on 2009-09-10
up

---

### Post by Lucky75 on 2009-09-12
up

---

### Post by nohammer on 2009-09-12
> **Lucky75 said:**
> Sure, that's fine, but I still have a **problem with the size of the video**, as can be seen in the picture I attached earlier. I guess because one of my monitors is larger and of a higher resolution than the other? That's the truly annoying part. Any way to fix that? 

Also, how would I make it so that it doesn't go back to regular size from full screen if I click on the other monitor? I know there's a hack one can do in windows with modifying the DLL in a hex editor, but obviously that won't work for linux.

I have the same problems - and as said with the 2nd problem that is a glitch with Flash - a really awful hack is to switch the video address from

[http://www.youtube.com/watch?v=EiWLOTv9tKE](http://www.youtube.com/watch?v=EiWLOTv9tKE)

to [http://www.youtube.com/watch/v/EiWLOTv9tKE](http://www.youtube.com/watch/v/EiWLOTv9tKE)

which puts it in a separate full screen window that can easily be dragged to your other desktop. I'm assuming similar things would work for playlists et al. But its a very inelegant hack.

As for the first problem with the full screen button not 'filling' the screen I have no solutions other than that /v/ solution and then F11 to fill Firefox on the screen. 


(aha! found another link here describing the problem as I was typing it up [http://www.webhostingtalk.com/showthread.php?t=686904](http://www.webhostingtalk.com/showthread.php?t=686904))

---

### Post by Lucky75 on 2009-09-13
Interesting "hack", thanks! Unfortunately, it doesn't help with any other flash sites.

Actually, I recently installed boxee, and had the same "fullscreen" problem there, where it stretches past the width of monitor and messes up the resolution.

---

### Post by Lucky75 on 2009-09-15
bump

---

### Post by Lucky75 on 2009-09-17
up

---

### Post by Lucky75 on 2009-09-19
up

---

### Post by Lucky75 on 2009-10-17
Up

---

### Post by Lucky75 on 2009-10-19
Anyone have any suggestions? Thanks!

---

### Post by Lucky75 on 2009-10-20
up

---

### Post by dmb on 2009-12-04
Same issue. For me it tries to extend, but doesn't actually extend, and makes the video unviewable.

---

### Post by Lucky75 on 2009-12-20
up, same on karmic

---

### Post by Lucky75 on 2009-12-28
up

---

### Post by 66Ton99 on 2010-06-07
up

---

