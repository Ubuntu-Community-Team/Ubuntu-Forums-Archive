---
title: "jumpy lines through video"
date: 2007-04-11
forum: Multimedia &amp; Video
---

### Post by herorev on 2007-04-11
When I play a video larger than original size, there is sometimes some horizontal jumpy lines. Even when paused, there are horizontal lines flashing and moving side-to-side.

The problem becomes much worse when in fullscreen, and the severity differs from video to video. The color of the lines matches pixels to the right or left. It's like random sections of random lines are copied and pasted to the left or right or their original location.

It happens with Kaffeine using Xine, VLC, and KMPlayer.

I'm running Kubuntu 6.10 on a Dell 8300 with a GeForce FX 5200.

---

### Post by RomeReactor on 2007-04-11
Hi. I had similar problems when i had a nVidia TNT Riva 32MB RAM, before enabling acceleration; did you install the drivers through Synaptic, and if so, did you enable 3d acceleration afterwards (running **sudo nvidia-glx-config enable** in the terminal)?

---

### Post by jkwarras on 2007-04-11
I think I have the same problem. mine is with an ATI fglrx.

---

### Post by herorev on 2007-04-11
I tried to install nVidia drivers several times through several different means. After every try, Kubuntu would only boot up into a command line, so each time I replaced xorg.conf with a backup. Adept currently shows that I have nvidia-glx 1.0.9755 installed.

---

### Post by ahaslam on 2007-04-11
Do you have composite enabled in your xorg.conf? It caused a similar, though less severe problem for me.

---

### Post by herorev on 2007-04-11
> **Anthony Haslam said:**
> Do you have composite enabled in your xorg.conf? It caused a similar, though less severe problem for me.
I don't know, but Kate didn't find any instances of "comp" or "cmp".

---

### Post by herorev on 2007-04-15
Any ideas?

---

### Post by RomeReactor on 2007-04-15
Please post your xorg.conf file, so we can take a look at it.

---

