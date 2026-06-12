---
title: "Can't install Noise Music Player on 14.04"
date: 2014-04-24
forum: Multimedia Software
---

### Post by solomonhodge on 2014-04-24
Trying to get Noise on 14.04, but it won't allow it. Here's the errors I get:

Depends: libgtk-3-0 (>=3.11.6) but 3.10.8 is to be installed
Depends: libnoise-core0 but it is not going to be installed

I'm assuming that first one is where the issue lies. Do you think there's any workaround?

Thanks!

---

### Post by blacksnow67 on 2014-04-30
The very same issue here, any help would be greatly appreciated!

---

### Post by gross-jonas on 2014-05-25
Same here -> Bump

---

### Post by mc4man on 2014-05-25
Where are you getting Noise from?

---

### Post by Yellow Pasque on 2014-05-25
Are you getting the package from elementary daily ppa?
If so, the packager is requiring a version of libgtk-3-0 greater than what's available in Trusty (which is probably not what s/he intended). You should contact him/her and ask about it.

---

