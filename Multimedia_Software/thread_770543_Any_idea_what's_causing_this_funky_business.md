---
title: "Any idea what's causing this funky business?"
date: 2008-04-27
forum: Multimedia Software
---

### Post by Jimmy9pints on 2008-04-27
Please see the attached screenshot. 

It happens when playing back video and even with visuals while listening to music. It often happens randomly but I can cause it by skipping forwards and backwards in a vid. 

If I close the video player and reopen it doesn't solve it. If I use another video player (e.g. mplayer instead of movie player) it doesn't solve it. 

It's only solved by logging out and back in. 

Any help appreciated. 

J

---

### Post by Jimmy9pints on 2008-04-28
Anyone?

---

### Post by Jammin80503 on 2008-04-28
You might want to make sure your video card is working correctly, and that your video cable is connected properly. 

To see if your video card is working, enter```
 glxgears 
```into the terminal. every 5 seconds, it will output a frames per second. If its over 1000 fps, it is probably working correctly.

---

### Post by Jimmy9pints on 2008-04-29
Thanks for your reply~

glxgears led to the gears window coming up and my system totally freezing!

Actually, my whole system freezes quite often (something which I have reported in other posts). Perhaps the whole thing is related. Seems to me, a high percentage of problems that people post about are related to graphics cards and drivers.

---

### Post by Jimmy9pints on 2008-04-29
OK, I typed glxgears again, the cogs turned and the system froze again. I stopped the programme and this output came up in the terminal:

james@james-desktop:~$ glxgears
346 frames in 12.3 seconds = 28.123 FPS
X connection to :0.0 broken (explicit kill or server shutdown).
james@james-desktop:~$ 

You said > If its over 1000 fps, it is probably working correctly. So... I guess mine isn't working correctly at all. 

FYI my graphic card is:
Nvidia GeForce 7300 LE

---

### Post by Jammin80503 on 2008-04-29
I've seen this freezing problem before, it happened to my friend's computer when he didnt have enough RAM. what are your system specs?

also, there is a program called envy ([http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)) that will configure your card for you. I recommend it.

---

### Post by Jimmy9pints on 2008-04-30
Hi,

My system specs are:

AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
L2 Cache 512 KB
1004 MiB DDRII RAM

---

### Post by cor2y on 2008-04-30
Is compiz-fusion enabled?

whats the output of the movie player when launched from the terminal?
Try disabling compiz (System->Preferences, visual effects tab set to none)
Then try playback again.
If its good then you may have to not use compiz-fusion or enable the video playback plugin in compiz-fusion.

---

### Post by Jammin80503 on 2008-05-01
your computer looks great, I dont see anything that would cause a problem. I'm pretty sure its the graphics card, or, as the post above me says, compiz.

---

### Post by Jimmy9pints on 2008-05-02
Thank you both cory and Jammin

I have had the Nvidia driver (and hence compiz) disabled since I last posted. My computer's running as sweet as a nut (no freeze ups, no funky business on the video playback) but it looks pretty old school. :(

J

---

### Post by Jammin80503 on 2008-05-02
Try Envy - Thats the easiest way I've found to configure graphics cards. I mentioned it in a previous post, with the URL.

---

### Post by dasunst3r on 2008-05-02
And remember: Even when you have no effects running, you can still enjoy a lean, mean, reliable machine!

---

### Post by Jimmy9pints on 2008-05-04
Thanks guys

---

