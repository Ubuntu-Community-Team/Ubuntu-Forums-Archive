---
title: "Login ok, desktop corrupted"
date: 2009-03-28
forum: Multimedia Software
---

### Post by LutherCymru on 2009-03-28
Hi,
  I've just upgraded the missus' PC to the latest version of Ubuntu, ignoring her pleas not to fix unbroken things. This was partly motivated by my desire to finally get the ATI drivers working correctly. Predictably, this has all come back to bite me on the ****.
  The installation is very confused regarding the graphics. I get numerous errors on start up, including:
(EE) module ABI major version(0) doesn't match the servers version
and 
(EE) failed to load module 'dri'.

The login screen comes up fine, albeit in what appears to be 565 16bit colour mode (banding is visible) and I can get into console fail safe mode, which is a console in graphics mode but with no window manager.
  Trying to get to the desktop however causes grief. The display blanks, presumably indicating a mode switch and then I get a bunch of corrupted graphics which looks like the driver thinks the stride of the screen in pixels isn't what it actually is as the display is sheered and wrapped around the screen a few times. Totally unusable, obviously.

I've edited, reset and done everything I can think of to 'xorg.conf'. Right now, I really don't care if its using some ancient fall-back vesa driver, as long as it works. My better (and wiser) half was using it in this manner for over a year and whilst I found the update rate and video playback painfully slow, she was happy enough with it.

None of my edits to 'xorg.conf' seem to have had any effect what so ever. I've uninstalled the ati drivers, also to no discernible effect.

On a possibly unrelated note, my installation also fails to resolve its own host name. Any ideas?

My graphics card is an ATI all-in-one wonder (ha) 9800

Cheers,

Tim Lewis.

---

