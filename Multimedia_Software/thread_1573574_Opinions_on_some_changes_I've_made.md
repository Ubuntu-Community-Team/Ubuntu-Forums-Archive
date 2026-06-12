---
title: "Opinions on some changes I've made"
date: 2010-09-12
forum: Multimedia Software
---

### Post by Xranger60 on 2010-09-12
Hello all, love the Ubuntu! I've recently noticed that in youtube, running under compiz, there is a problem with video "tearing" on my set-up. Having searched for a while, I've come across some common solutions. These usually involve tweaking some options in the compiz-settings manager and the nvidia x server settings. I've changed the following:

Under the compiz settings manager:
"General compiz options":

"General" tab:
checked the "unredirect fullscreen windows" option

"Display settings" tab
unchecked "Detect refresh rate" option
set "refresh rate" to 60
enabled "sync to vblank"

Under the Nvidia X Server Settings:
"Open GL Settings"
Enabled "sync to vblank"

It seems as though "X serverXvideo settings" has sync to vblank enabled by default, so left that alone.

Although it really hasn't fixed the video tearing problem, I haven't changed these options back to their previous settings. 

I wanted to know what you guys think: Does having Vblank sync in Nvidia settings in addition to the compiz settings manager have any effect on performance? Are any of these changes actually counter-productive? Redundant? Only because I don't have an advanced technical knowledge of what these changes do.

And one more question for you guys... when running games or videos, do you disable compiz? Thanks for any opinions on this in advance!

---

