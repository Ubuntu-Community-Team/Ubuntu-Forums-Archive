---
title: "How do I get rid of Video Tearing?"
date: 2009-01-19
forum: Multimedia Software
---

### Post by Roasted on 2009-01-19
Note:

I tried X11 video output setting on VLC.
I turned off Compiz Fusion.

I have no idea what I can do. I hate watching movies in Ubuntu and seeing a rippling line horizontally across the screen during action scenes.

I have a 9600GT 512mb 256bit PCIEx16 2.0 graphics card. I'm running a 24" Dell 1080p widescreen monitor as my main + a 19" eMachines monitor as my secondary.

My system is a fresh install of Ubuntu Intrepid 64 bit. I did a fresh install yesterday. I installed libdvdcss2 as well as medibuntu repository. I don't know what else I can do.

I already use Vista exclusively for gaming. I don't want to use Vista exclusively for multimedia use as well. That'd pretty much render Linux useless for my needs.

---

### Post by Anthony T. on 2009-01-19
Try setting desktop effects to None. It removed all video tearing for me in World of Warcraft but then again I'm new to Linux aswell so it might not work.

---

### Post by Melcar on 2009-01-19
Can't really fix it.  Try using opengl instead of Xv and force vsync. on the video driver; that seems to work for most people.

---

### Post by Roasted on 2009-01-19
Can't fix it?

Then why does Intrepid have tearing, but Hardy didn't? 

Certainly there's a fix. Somehow.

---

### Post by Roasted on 2009-01-19
> **Anthony T. said:**
> Try setting desktop effects to None. It removed all video tearing for me in World of Warcraft but then again I'm new to Linux aswell so it might not work.

As I said, I already turned off compiz fusion. With it on or off, it makes no difference.

---

### Post by metallicamike on 2009-01-19
the same things happen to me in intrepid but not in hardy....must just be a bug

---

### Post by Roasted on 2009-01-19
Stupid question, but if I put Hardy on my computer, would it be likely that Hardy would be running the same kernel that Intrepid uses for the sake of hardware support?

---

### Post by Roasted on 2009-01-28
Is there an active bug report for this? Can we expect that in the next release of Ubuntu, or (hopefully) it be fixed during Intrepid's life cycle???

---

### Post by browndog on 2009-01-28
> **Roasted said:**
> Note:

I tried X11 video output setting on VLC.
I turned off Compiz Fusion.

I have no idea what I can do. I hate watching movies in Ubuntu and seeing a rippling line horizontally across the screen during action scenes.

I have a 9600GT 512mb 256bit PCIEx16 2.0 graphics card. I'm running a 24" Dell 1080p widescreen monitor as my main + a 19" eMachines monitor as my secondary.

My system is a fresh install of Ubuntu Intrepid 64 bit. I did a fresh install yesterday. I installed libdvdcss2 as well as medibuntu repository. I don't know what else I can do.

I already use Vista exclusively for gaming. I don't want to use Vista exclusively for multimedia use as well. That'd pretty much render Linux useless for my needs.

When you're watching a movie in VLC click on the Video (or Playback menu...can't remember which one) and set the Deinterlace option to Discard.  I found it works great for getting rid of those lines.

---

### Post by Roasted on 2009-01-28
> **browndog said:**
> When you're watching a movie in VLC click on the Video (or Playback menu...can't remember which one) and set the Deinterlace option to Discard.  I found it works great for getting rid of those lines.

No dice. In fact, it made no difference.

It's upsetting... using Vista for movie usage... :(

---

### Post by browndog on 2009-01-28
> **Roasted said:**
> No dice. In fact, it made no difference.

It's upsetting... using Vista for movie usage... :(

Of course...do what you must.  I hope you keep an eye out for such a time that Ubuntu DOES suit your needs.  Take care.

---

### Post by Roasted on 2009-01-28
> **browndog said:**
> Of course...do what you must.  I hope you keep an eye out for such a time that Ubuntu DOES suit your needs.  Take care.

It does everything I need it to, and then some. With the exception of being able to play decent games and... in this case... play movies that are worth half a shat to watch.

---

