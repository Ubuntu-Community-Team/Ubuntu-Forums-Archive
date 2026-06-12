---
title: "[SOLVED] Intrepid nVidia driver problems"
date: 2008-11-06
forum: Multimedia Software
---

### Post by jacmoe on 2008-11-06
I upgraded to Ubuntu 8.10 - and everything was right.:

Or, so I thought it was.

Until I tried to compile OGRE, a 3D graphics programming library.

Seems like my OpenGL, GLU in particular, vanished during the upgrade.:confused:

Tried to install libglu-dev, but Ubuntu would only install the mesa version, which I don't want.

Looking closer, I notice that the new NVIDIA drivers doesn't come with sources.

Tried to uninstall libglu1-mesa, but I couldn't do that. It would uninstall my entire system.

How on Earth do I get rid of Mesa?
And get hold of the real OpenGL headers?

I read the upgrade notes, about the new nvidia-glx-177 drivers.

How come they are not providing any OpenGL ?

My system is insisting on using Mesa when I tell it to install lib glu and friends, but is running the NVIDIA proprietary driver.

I am confused. :)

Do I need to roll back to Hardy, or is there a work around?

Thanks.:wink:

---

### Post by jacmoe on 2008-11-07
That one was easy enough - once I figured it out:

Install **nvidia-glx-177-dev**:)


Woo-Hoo! Intrepid, here I come! :D

---

