---
title: "Apps won't open in TV-OUT X Screen"
date: 2009-11-25
forum: Multimedia Software
---

### Post by Cuco3 on 2009-11-25
Hello.

I'm pretty sure I've got TV-Out configured properly using the option "Seperate X Screen." My goal is to be able to use my TV to watch videos while using my computer. The problem is, every time I open the movie player (or any program) in the TV-Out X Screen, the program always opens on my main monitor rather than TV out.

I also can't seem to drag the program window on to the TV-Out X Screen. I wonder if using Compiz with Expo and 4 workspaces has something to do with it (although I can move my mouse to the right of the screen to get into the TV-Out X Screen, so it should work)

I've tried google for an answer but I'm not sure I was using the proper words to get the answer I'm looking for.

Can anyone be so kind as to offer me advice? Thank you.

***edit***  I just used "TwinView" with the "Clone" setting then disabled the main monitor. Now I can watch my movies through my computer.

---

### Post by yauhen on 2010-01-03
I had the same problem. What I did was the following.

1)Type in the terminal:
gksudo nvidia-settings

2)Then go to X Server Display Configuration and 

3)check box "enable xinerama"

4) save changes to xfile

---

