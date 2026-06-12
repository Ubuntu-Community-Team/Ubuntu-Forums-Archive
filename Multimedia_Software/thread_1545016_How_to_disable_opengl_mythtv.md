---
title: "How to disable opengl mythtv?"
date: 2010-08-03
forum: Multimedia Software
---

### Post by agentsmith23 on 2010-08-03
I was configuring mythtv and when I was in the video settings I set it up to use OpenGL. Now I can no longer see video and I can't get back to the settings screen to disable OpenGL. Is there a config file that I can edit to disable OpenGL or someway to revert everything back to default. I tried completely removing the frontend and reinstalling it but that didn't do anything helpful. 

Thanks for any possible help!

---

### Post by heimo on 2010-08-03
Perpaps:  mythfrontend -O ThemePainter=qt
Or: mythfrontend -r (resets appearance settings and language)

---

### Post by agentsmith23 on 2010-08-05
Thanks for the help!
mythfrontend -r worked great, I didn't try the other option

---

