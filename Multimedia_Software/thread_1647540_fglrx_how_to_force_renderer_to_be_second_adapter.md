---
title: "fglrx: how to force renderer to be second adapter?"
date: 2010-12-17
forum: Multimedia Software
---

### Post by dsjstc on 2010-12-17
I'm using two Radeons for a multihead setup, an onboard HD 4290, and a PCI-E 5850.

fglrxinfo tells me that the renderer is the onboard 4290.  Obviously, I'd prefer if it were using the 5850.

Is there a way to specify it?


> $ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4290
OpenGL version string: 3.3.10317 Compatibility Profile Context


---

### Post by dsjstc on 2011-01-06
Update: I reassigned screen 0 as one of the displays attached to the 5850.  Now the 5850 is the render device.

Not really "solved", but at least worked around.

---

