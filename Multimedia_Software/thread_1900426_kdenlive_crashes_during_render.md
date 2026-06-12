---
title: "kdenlive crashes during render"
date: 2011-12-26
forum: Multimedia Software
---

### Post by mattgeb84 on 2011-12-26
i have the latest version of kdenlive, and mlt, i just finished making a cool looking progect but when i go to render kdenlive stops rendering at 50% every time. when it gets to 50% the progress bar and the remaining time stays the same no matter how long you leave it alone. strangly enough i was able to successfully render some other progects that were a bit shorter in time, but this almost 5 minute progect won't render no matter what. i've tried changing the render settings, used different profiles, restarting the computer, unistalling and then reinstalling kdenlive, but nothing works, i'd hate to have to go back to cinelerra because kdenlive is ten times easier to learn but if i cant even output my file then i might.
please help

p.s. kdenlive will not let me update my render profiles, when i click the update button it looks like it updates fine, but then when i close and reopen the render profile window the update button for the one i just updated or installed is still available as if it hadn't updated or installed

---

### Post by mattgeb84 on 2011-12-26
it appears it may have been the effects, i just took out all the effects which included some composites, scaling, and bluring effects, now it rendered fine, why would the effects cause it not to render ?

---

### Post by Hunkadoodledoo on 2012-04-01
I too would like to know which specific effects cause the render to crash. I am using version .8.2.1, and I have an effects stack including gamma correction, the denoiser, curves and the speed effect. Doing a two pass MP4 render, it would always crash when calculating the first pass on frame 410. Removing all of the effects seems to allow me to render. I am now going to try to remove all but each to test to see which one is causing the error. Were you using any of these effects? I don't know if it matters, but the curves effect I'm using is a custom effect I saved to reuse on multiple clips in my project.

---

