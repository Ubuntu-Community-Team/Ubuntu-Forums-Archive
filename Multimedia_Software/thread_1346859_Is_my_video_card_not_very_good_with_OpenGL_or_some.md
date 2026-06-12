---
title: "Is my video card not very good with OpenGL or something?"
date: 2009-12-05
forum: Multimedia Software
---

### Post by MetroidJunkie2008 on 2009-12-05
With the exception of Sauerbraten, it seems like every Linux native 3D game has framerate problems, from OpenArena to DarkPlaces Quake. Changing the graphical settings affects how much it lags so I'm sure it's the video card having trouble. I have a GeForce 8800GT 512MB and I have the latest Nvidia driver, desktop effects are also completely disabled. What could be causing my video card to become so crippled? I know it can do more than this, I managed to practically max out games like Bioshock and Modern Warfare when I had Windows.

Edit: Before I forget, I have Ubuntu version 9.10

---

### Post by xc3RnbFO8P on 2009-12-05
Did you check the frame rate
> glxgears

---

### Post by MetroidJunkie2008 on 2009-12-05
That test, of 10 entries, yielded an average of 9666.3 every 5 seconds or 1933.26 a second.

---

### Post by JBAlaska on 2009-12-05
This is what I get with my integrated GeForce 8200:
```
10390 frames in 5.0 seconds
11175 frames in 5.0 seconds
10974 frames in 5.0 seconds
11097 frames in 5.0 seconds
11081 frames in 5.0 seconds
11171 frames in 5.0 seconds
11138 frames in 5.0 seconds
11144 frames in 5.0 seconds
11084 frames in 5.0 seconds
```

Just so you have something to compare.

---

### Post by MetroidJunkie2008 on 2009-12-05
Looks like my 8800GT is performing worse than your 8200.

Update: Ironically, I just downloaded the Bioshock demo to see how well it would work on Wine, no framerate problems, even at maxed out settings. Yet, most Linux native 3D games that should use far less graphical power give me more problems.

[Bioshock Pic]("http://i48.tinypic.com/1zptx6q.png")

---

### Post by MetroidJunkie2008 on 2009-12-06
Anyone got any ideas? It's weird that Bioshock gives me better performance than what is essentially Quake 3.

---

### Post by Yellow Pasque on 2009-12-06
WHat version of nvidia driver are you using? (Oh, and please use thumbnails).

---

### Post by MetroidJunkie2008 on 2009-12-06
As I said, I 'm using the newest one, version 185. It was also recommended.

---

### Post by Yellow Pasque on 2009-12-06
The newest driver is 195.something (from nvidia's site).

---

### Post by MetroidJunkie2008 on 2009-12-06
I updated to the new 195.22 and I think it helped. Quake Dark World still lags if I turn shadows on and Quake 3 has some kind of sound lag but it seems better than before.

---

