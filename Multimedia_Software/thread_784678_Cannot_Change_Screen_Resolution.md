---
title: "Cannot Change Screen Resolution"
date: 2008-05-06
forum: Multimedia Software
---

### Post by Cornova on 2008-05-06
After updating to 8.04 my screen resolution is way too high. Trying to change it via system>preferences>screen resolution results in an error message:

"The X Server does not support the XRandR extension. Runtime resolution changes to the display size are not available."

---

### Post by Cornova on 2008-05-06
I should mention that I am using the ATI driver for my videocard since the default one was extremely sluggish when scrolling/opening and closing windows. Using the ATI driver is still a little sluggish when scrolling but I suspect it is because the resolution is so obnoxiously high.

---

### Post by Cornova on 2008-05-06
I was able to change the screen resolution down to 1280x1024 using sudo displayconfig-gtk in the terminal and selecting the monitor I have. However windows are still laggy/delayed when I scroll down or open programs which did not happen on 7.04.

---

