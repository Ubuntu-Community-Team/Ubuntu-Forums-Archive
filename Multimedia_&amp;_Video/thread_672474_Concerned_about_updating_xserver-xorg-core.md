---
title: "Concerned about updating xserver-xorg-core"
date: 2008-01-19
forum: Multimedia &amp; Video
---

### Post by rainwalker on 2008-01-19
It says it's the core X.Org X server, so I'm a little cautious. I'm running Gutsy with the open ATI driver and Compiz Fusion. The only problem I've had with graphics was using the proprietary driver, I haven't had to tweak resolution or refresh rates, etc.
 
Should I be wary of updating?

---

### Post by yetanothersteve on 2008-01-19
Yes, you should. Nothing quite like being forced to the CLI to wake you up in a bad way.
You could wait a week to see if the patch had been pulled and replaced.

I did do the update, but first I downloaded the latest drivers for my card and put them in the same folder with the previous drivers.
I did the update from the console after going to run level 3.
```
sudo apt-get update
sudo apt-get upgrade
```
Then I installed the latest drivers for my video card because I was one version behind.

If something had gone wrong I could have rolled back to the previous version of Xorg and the video card drivers as well if necessary.

---

