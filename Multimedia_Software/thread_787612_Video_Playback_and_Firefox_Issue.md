---
title: "Video Playback and Firefox Issue"
date: 2008-05-09
forum: Multimedia Software
---

### Post by fahimdadream on 2008-05-09
Hello everyone, 

I am currently running Ubuntu 8.04 on my Dell Inspiron 8200. I installed the NVIDIA Legacy drivers and managed to get Compiz to work. The issue, however is that I get lots of lag in FireFox, and choppy video playback in VLC. If I dont use fullscreen its watchable, but nowhere near as good as XP, and Fullscreen is unwatchable. Totem player (GStreamer) crashes if I try to play video fullscreen, and the XINE version doesn't play it at all. 

Also, turning compiz off helps my firefox, but doesnt solve the choppy fullscreen video in VLC.

Thanks in advance.

---

### Post by hermes0710 on 2008-05-09
What kind of media are you trying to playback?
Have you installed w32codecs/libdvdcss2 (add medibuntu repositories in order  to have them appeared in synaptic)?
Did you install the drivers through System>Administration>Hardware Drivers?
If yes, going there again does the driver show up as enabled and in use?

---

### Post by fahimdadream on 2008-05-10
Hey, thanks for the quick reply, and sorry about the late reply. To answer your questions:
> What kind of media are you trying to playback?
I'm trying to watch an XVID MPEG-4, 512 x 384 video. (Daily Show)

> Did you install the drivers through System>Administration>Hardware Drivers? If yes, going there again does the driver show up as enabled and in use? 

Yes.

> Have you installed w32codecs/libdvdcss2 (add medibuntu repositories in order to have them appeared in synaptic)?


Didn't have w32 or libdvdcss2 before you mentioned it but gave it a shot. 

Without any compiz effects enabled, in VLC, when the video output is default, its perfect, fullscreen too. When the output is X11, fullscreen video is alot better but slightly choppy (yes its nitpicking, but I imagine playing a dvd with a higher res would be an issue.)

With compiz, in VLC, when the video output is default, it crashes, and openGL and X11 work better at fullscreen, but still very choppy

Side Note: W/O Compiz Firefox is pretty damn good, With Compiz its, "slower than molasses in an igloo" 

Thanks in advance

---

### Post by fahimdadream on 2008-05-12
B-U-M-P, you ain't got no alibi

---

### Post by hermes0710 on 2008-05-12
Try enabling sync2vblank through nvidia-settings (sudo). Is the video playback still choppy?

---

### Post by fahimdadream on 2008-05-12
Video playback is only choppy when I use Compiz.. otherwise its fine, I'm going to try this sync2vblank right now. Will update soon.

---

### Post by Zorael on 2008-05-12
Compiz can be a pain when it comes to vsync. You'll want to go into General Options in ccsm and then Display Settings. Try enabling vsync there and see if it improves.

I'll update this post in a bit, but I actually think I didn't check it, and instead disabled detect refresh rate and manually set the wanted frame rate to my monitor's refresh rate. (rate rate rate)

---

### Post by Zorael on 2008-05-12
My mistake, I did check it.

---

### Post by fahimdadream on 2008-05-12
Alright gave those two things a shot, the enable VSync in NVidia-Settings, and in the CCSM. In VLC, with Compiz ON, and output to X11, fullscreen is definately much better, but still jerky at times. I could live with it, but im only watching this small XVID MPEG-4, 512 x 384 video. If I can't get this to run smooth with compiz, I dont like the idea of having to turn it off anytime I wanna watch a movie much less a DVD. Not to mention, FireFox is un-usable with Compiz on. 

Also, when I use VLC with the output as OpenGl.., its like watching a slide show. (incase anyone was wondering).

Thanks so far to the both of you.

---

### Post by hermes0710 on 2008-05-12
What is your nvidia model?

---

### Post by fahimdadream on 2008-05-12
Its the v.card on my Dell Inspiron 8200 its the GeForce4 440 Go 32mb

Edit: I noticed that on NVidia settings it says my refresh rate is 60 Hz, but on screen resolution under System>Preference, it says 50Hz... dunno if that has to do with anything

---

### Post by Zorael on 2008-05-12
That's a bug with the Nvidia driver, not to worry. But that's precisely why you don't want to let Compiz autodetect refresh rate; if you check vsync along with that, it'll limit framerates to those 50hz, and you get le choppiness™.

---

### Post by fahimdadream on 2008-05-12
So, you suggest that in Compiz I should, Turn off Sync to VBlank, Turn off detect refresh rate and drop it to 50(which is what Ubuntu says I should have)?

Update: Well whether or not you were suggesting that, gave it a shot and no go, oddly enough my sound seems choppy too at time with Compiz on... Im beginning to think Compiz + Video playback/Firefox = :(. Atleast thats the case with the graphic card on my computer, it IS very old after all. Oh well thanks to everyone who tried really do appreciate it.

---

