---
title: "no sound in kubuntu"
date: 2008-09-17
forum: Multimedia Software
---

### Post by mistaboins on 2008-09-17
i just reinstalled kubutu (hardy) and now have no sound, even though it appears sound is playing on amarok (i can see the eq graphs moving). no system sound, it is not muted and everything is plugged in correctly. i am using ess 1938 solo sound card. i have searched many threads on sound issues but so far nothing has worked.

---

### Post by miscreant on 2008-09-27
> **mistaboins said:**
> i just reinstalled kubutu (hardy) and now have no sound, even though it appears sound is playing on amarok (i can see the eq graphs moving). no system sound, it is not muted and everything is plugged in correctly. i am using ess 1938 solo sound card. i have searched many threads on sound issues but so far nothing has worked.

Did you find a solution for this? I'm having the same issue. Looks like Amarok is playing, but no sound is coming through the speakers. Nothing is muted. Was working before I did a reinstall.

---

### Post by markbuntu on 2008-09-27
Since you are using kubuntu, you may need to set Amarok to use alsa plugin in Settings/Configure Amarok/Engine. You also need to make sure you have the packages:

libxine-misc-plugins
amarok-xine

if xine is the engine.

---

