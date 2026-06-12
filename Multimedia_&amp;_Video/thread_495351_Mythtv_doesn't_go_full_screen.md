---
title: "Mythtv doesn't go full screen"
date: 2007-07-07
forum: Multimedia &amp; Video
---

### Post by obryant on 2007-07-07
I've installed Mythtv on a fresh Feisty install.

Problem is, when Mythtv starts, it doesn't start full screen (I can still see the upper and lower Ubuntu tool bars). When mplayer launches --- from within mythvideo --- mplayer goes full screen, but the internal mythtv player still shows the Ubuntu toolbars.

I didn't have this problem with Edgy, and I only have it with mythtv --- other apps such as mplayer, totem, firefox go full screen as expected.

Any suggestions?

---

### Post by NT4usB on 2007-07-08
In the frontend setup>setup>appearance
Is 'Use GUI size for TV playback' checked?
Is 'Run frontend in a window' unchecked?

---

### Post by tgm4883 on 2007-07-08
> **obryant said:**
> I've installed Mythtv on a fresh Feisty install.

Problem is, when Mythtv starts, it doesn't start full screen (I can still see the upper and lower Ubuntu tool bars). When mplayer launches --- from within mythvideo --- mplayer goes full screen, but the internal mythtv player still shows the Ubuntu toolbars.

I didn't have this problem with Edgy, and I only have it with mythtv --- other apps such as mplayer, totem, firefox go full screen as expected.

Any suggestions?

Are you using compiz fusion or beryl?

---

### Post by obryant on 2007-07-09
I just tried all four possibilities for those two options (exiting and restarting the frontend each time), and there is no change in behavior at all.

The two options I'm referring to are 'Use GUI size for TV playback' and 'Run frontend in a window'.

---

### Post by obryant on 2007-07-09
I had to Google to even understand the question. After Google, I realized that you were suggesting that having "desktop effects" enabled might be causing the problem.

And then, disabling desktop effects fixed it.

Thanks!

---

