---
title: "Firefox Java Console not working."
date: 2008-06-24
forum: Multimedia Software
---

### Post by miko777 on 2008-06-24
My Firefox Java Console isn't working at all. It's completely blank. Applets, however, are working.

Anyone with similar experiences or useful info?

Thanks.

---

### Post by jamesstansell on 2008-06-25
Yep - in Ubuntu 8.04 the default Java plugin doesn't have a console.  If you absolutely need the Sun Java console then remove the icedtea-gcjwebplugin package and install the sun-java6-plugin package.

If you need to debug or troubleshoot an applet then you might have some other options, but the programming forum might be more appropriate.

---

