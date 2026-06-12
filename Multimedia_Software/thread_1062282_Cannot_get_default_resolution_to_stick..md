---
title: "Cannot get default resolution to stick."
date: 2009-02-06
forum: Multimedia Software
---

### Post by Ouoertheo on 2009-02-06
Hello, I've been trying to set my default resolution to 1152x864, but everytime I restart, it is back at 1024x768. I'm using nvidia-settings (under sudo) to set it and have it save the settings to my xorg.config.

I know it's not *that* much of a problem, but it's kinda annoying.

I'm running UbuntuStudio 8.10 with nvidia 177 drivers.

Any help on this issue would be gratly appreciated.
Thanks.

---

### Post by redroad55 on 2009-02-06
one way I've seen this done is to eliminate the other choices leaving only the one you want..forcing it to be the only choice..Post back..best to you

---

### Post by Ouoertheo on 2009-02-07
Hmmmm, no offense, but don't really agree with doing that one there. I'd rather figure out the issue than just jury rig it like that. Thanks for the reply.

---

### Post by redroad55 on 2009-02-07
No offense taken :

> man xorg.conf

or read this: [https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution")

or you could simply use the search engine at the top of the page and see this very issue has been addressed many times in just this last week...Best to you

---

### Post by xc3RnbFO8P on 2009-02-07
> **Ouoertheo said:**
> Hello, I've been trying to set my default resolution to 1152x864, but everytime I restart, it is back at 1024x768. I'm using nvidia-settings (under sudo) to set it and have it save the settings to my xorg.config.

I know it's not *that* much of a problem, but it's kinda annoying.

I'm running UbuntuStudio 8.10 with nvidia 177 drivers.

Any help on this issue would be gratly appreciated.
Thanks.

What resolution do you have in **System> Preferences> Screen Resolution**
You have to have same resolution in **Nvida-settings** and **Screen Resolution**

---

### Post by Ouoertheo on 2009-02-07
Thank you very much for your replies :) All I had to do was open up Screen Resolution and make sure it was set the same like Ringi mentions.

Case closed :popcorn:

---

