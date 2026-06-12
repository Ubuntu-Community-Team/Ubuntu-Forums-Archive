---
title: "update to 9.04 caused many strange things"
date: 2009-05-10
forum: Mythbuntu
---

### Post by jeffspen on 2009-05-10
Since upgrading from 8.10 to 9.04 recently I've had a set of problems I can't get to the bottom of. They seem to have user privileges as the common factor.

- Every time I boot the resolution is wrong. I change it in the display settings and all looks good. However, this is never preserved.

- i am unable to run the update-manager from the system menu. sudo apt-get update seems to work fine in terminal.

- I am unable to edit my software sources list through the gui. As with the update manager, something flickers then disappears. If I try manually as described to me elsewhere, /etc/apt/sources.list doesn't seem to exist.

- Mythbuntu Control Centre does not work. I select it from system menu and am asked for my password once, then nothing happens. If i run from terminal, I am told that module pygtk does not exist. I can't install this manually as it is not in any repository I have up and i can't edit my software sources...!

When I upgraded, I was asked for my root password. I just pressed enter and left it blank. I think this happened a few times. 

Any ideas???

---

