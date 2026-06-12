---
title: "GIMP GAP errors."
date: 2010-02-15
forum: Multimedia Software
---

### Post by HBSC on 2010-02-15
I installed the gimp-gap package from the repositories. When I attempt to use the "filter all layers" function I get multiple errors, and the plugins are not available to me.

Errors:

```
GIMP Message
Calling error for procedure 'gimp-procedural-db-proc-info':
Procedure 'plug-in-diffraction-Iterator' not found

GIMP Message
Calling error for procedure 'gimp-procedural-db-proc-info':
Procedure 'plug-in-solid-noise-Iterator' not found

GIMP Message
Calling error for procedure 'gimp-procedural-db-proc-info':
Procedure 'python-fu-slice-Iterator' not found

Too many error messages!

Messages are redirected to stderr.

```

The stderr file (in /lib/udev/devices) is flooded with similar messages. Any ideas how to go about finding these plugins that gimp can't find? Was installing gimp-gap not sufficient?
I am running Ubuntu 9.10 32bit and my gimp version is 2.6.7
Thanks!

P.S. I hope it's ok to post questions about the gimp here on ubuntuforums.

---

### Post by HBSC on 2010-02-15
I have verified that all the dependencies are satisfied one by one, did some more googling and read some gimp forums -- there has to be something obvious that I'm missing here!

---

### Post by HBSC on 2010-02-15
bump

---

### Post by HBSC on 2010-02-17
bump

---

### Post by Captain_Rage on 2010-03-07
It's exactly the same thing here. I also run Ubuntu 9.10, 32 bit. After installing the package gimp-gap and selecting "Filter all Layers" I get the same errors. Don't know what might be wrong..

---

