---
title: "Video Card Struggles in Ubuntu"
date: 2011-05-11
forum: Multimedia Software
---

### Post by wheelern on 2011-05-11
Hey all,

So I recently bought a new computer and added a new video card. A GeForce GTS 440, to be exact. Not top of the line, but gets the job done. I play a few games on my Windows partition. Everything on Windows works great; I am able to play at the highest quality with up to ~60 fps. I love it. However, in Ubuntu 11.04, the video card can't even handle high quality videos, like of Youtube or something. Anything flash, basically, it struggles with, extremely choppy, pretty much unwatchable. I have the latest Flash player, as well as all of my drivers installed. It's def not a driver issue, because everything in Unity works. But this video problem is getting frustrating. Any suggestions on what I should try?

---

### Post by lovinglinux on 2011-05-11
The main problem is that flash sucks on Linux and uses too much CPU, because of it's inability to use xv output.

Get [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/") and run it. It will detect installed flash plugins, remove them and install the best option according to your system architecture and version. Additionally, it will apply some tweaks that should improve performance. If you still get that issue after running Flash-Aid, then go to the extension Help tab, click the "Generate Report" button and send me the results so I can analyze your situation.

---

