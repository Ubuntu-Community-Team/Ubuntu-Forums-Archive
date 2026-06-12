---
title: "k3bmonkeyaudioplugin-3.1 compile error"
date: 2007-11-28
forum: Multimedia &amp; Video
---

### Post by logos34 on 2007-11-28
Same plugin installed fine on my x86 ubuntu gutsy partition, but I can't get past the configure stage on my 64-bit ubuntu studio setup.  Here's the error:
> ...
[COLOR="Red"]checking crt_externs.h usability... no
checking crt_externs.h presence... no
checking for crt_externs.h... no
checking for _NSGetEnviron... no[/COLOR]
checking for vsnprintf... yes
checking for snprintf... yes
[COLOR="Red"]checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths![/COLOR]

Anyone have an idea?

---

### Post by logos34 on 2007-11-28
I should add I looked for x-window-system-dev. xlibs-dev, and xlibs-static-dev packages [per these instructions]("https://help.ubuntu.com/community/CompilingSoftware#head-69bd6c392f766fa1598f09efdc69d26c8afcaad8") (only found and installed the last).

EDIT: kdebase-dev may do the trick, but I'd rather not have to install it--it's 96 packages and ~200 MB! (i only have a few kde apps)

---

