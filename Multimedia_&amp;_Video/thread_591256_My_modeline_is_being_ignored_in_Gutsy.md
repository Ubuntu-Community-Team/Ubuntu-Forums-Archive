---
title: "My modeline is being ignored in Gutsy"
date: 2007-10-25
forum: Multimedia &amp; Video
---

### Post by dmsa31 on 2007-10-25
I have a laptop with a Radeon 9200 hooked up to a Dell 2005fpw via VGA. I found a custom modeline somewhere and used that. Everything worked fine. The modeline was a bit incorrect, since about 5 or so pixels in the top were cut off, but everything else looked perfect.

Now that I installed Gutsy, though, it seems like the Screens and Graphics tool has taken over everything. It correctly detected my monitor as a 2005fpw and seems to have used its own mode. To its credit, it no longer cuts the top of the screen off, but everything looks kinda blurry and I have to use my monitor's auto-adjust a couple of times before it's OK. Even then, though, it's not quite right. I'd like to be able to just use the modeline I have already, but it seems to be completely ignored. Does anyone know if there's a way to have it use a custom mode?

Actually, is it possible to somehow uninstall the Screens and Graphics thing and make the screen handling be exactly like it was in Feisty? It's causing me more trouble than it's worth. Back in Feisty, it blanked my laptop's LCD when X started up with the monitor plugged in, but now, I have to do that manually via xrandr every time I start X.

edit: By the way, I'm using the open-source ati driver.

edit2: Oh, and I'm also experiencing random lockups of X. Thankfully, ctrl-alt-backspace works, but what's up with that? It never happened to me in Feisty. I'm honestly thinking about just switching to Gentoo at this point.

---

