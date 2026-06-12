---
title: "Differences between &quot;ati&quot; and &quot;radeon&quot; drivers"
date: 2007-11-15
forum: Multimedia &amp; Video
---

### Post by infinito on 2007-11-15
Hello,

Can anyone explain me the differences between the drivers "ati" and "radeon" for xorg?
I'm asking this 'cause my ATI Mobility X600 works with both, but I'm not sure which is the right option.

Thanks in advance!

---

### Post by Yellow Pasque on 2007-11-15
Use the ati driver, as the radeon driver has been around for a while and is meant more for the R100/200 cards.

You can either use the open-source "ati" driver or the proprietary "fglrx" driver, which generally performs better in OpenGL apps and Desktop Effects at the expense of stability.

If you don't play 3d games and can do without eye candy, stick with the ati driver.

---

