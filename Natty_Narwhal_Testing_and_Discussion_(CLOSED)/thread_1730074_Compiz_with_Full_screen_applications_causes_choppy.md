---
title: "Compiz with Full screen applications causes choppy video"
date: 2011-04-15
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by defconoii on 2011-04-15
When running FPS games like openarena or quakelive with compositing enabled, you get choppy video playback because of the compositing overlay, previously  metacity --replace then compiz --replace remedied the issue but since unity relies on compiz to run, it seems its impossible to temporarily disable compiz.  Anyone know of a good way to temporarily disable compiz on start of a game then re-enable it after?  alt shift F12 used to toggle compositing in the past, it seems as if its disabled now since compiz is required for unity to run.

If anyone knows a bug that I can subscribe to on launchpad please let me know, been searching for a while now

---

### Post by RomeReactor on 2011-04-15
Hi. Choose "Ubuntu Classic (No effects)" at the login screen and see if your framerate improves.

---

### Post by defconoii on 2011-04-15
framerate is fine but the compiz compositing overlay has video stuttering, ubuntu classic of course has no stuttering, compiz is the problem but its a pain having to logout and log back in to play a game

---

### Post by defconoii on 2011-04-15
unity 2d works fine since there is no compiz compositing but unity 2d does not look as good as unity 3d

---

### Post by VMC on 2011-04-15
> **defconoii said:**
> unity 2d works fine since there is no compiz compositing but unity 2d does not look as good as unity 3d
Its the trade off. I notice unity 3d also has shuddering playing chess full screen.

Its good to know that when 11.10 rolls around and we no longer have Gnome2(as well know it) as an option, we can use Unity 2d when playing games, until someone comes up with a brilliant fix.

---

### Post by Stubbs3 on 2011-04-27
I don't play games, but i notice a choppy (lines) during HQ video playback with full screen. I just disable compiz using the Compiz Fusion Icon. Right click on the icon and choose Metacity as a windows manager. Playback is immediately improved. 
Im just a noob and im not sure if this will help you out in your situation, or if it can be applied towards natty. Im currently using this setup in lucid. 
Sorry if im waisting your time.

---

