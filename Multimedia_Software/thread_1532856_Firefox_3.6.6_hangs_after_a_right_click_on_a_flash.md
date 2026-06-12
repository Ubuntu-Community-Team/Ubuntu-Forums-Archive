---
title: "Firefox 3.6.6 hangs after a right click on a flash video."
date: 2010-07-17
forum: Multimedia Software
---

### Post by prodigy_ on 2010-07-17
Ubuntu 10.04 64-bit. Firefox 3.6.6. Flash 10.1.53.64. When I right-click on any flash video, FF hangs completely and has to be killed/restarted.

Any ideas how to resolve this?

---

### Post by lovinglinux on 2010-07-17
Try this:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

Then add the following line before the last line of that file:

```
export GDK_NATIVE_WINDOWS=1
```

The file content should look like this:

```
#!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386
export GDK_NATIVE_WINDOWS=1
. /usr/lib/nspluginwrapper/noarch/npviewer
```

Save the file and restart the browser.

---

### Post by prodigy_ on 2010-07-17
Tried this. Didn't help.

In the meantime I found out that this bug doesn't affect YouTube and some other sites. It does affect [About - Flash Player](http://www.adobe.com/software/flash/about/) page on Adobe official site however.

---

