---
title: "Amarok needs decoder in 8.10"
date: 2008-10-30
forum: Multimedia Software
---

### Post by geovino on 2008-10-30
setting up 8.10 

When trying to play streaming radio in Amarok I get this error:

Error Loading Media
There is no available decoder.
[http://scfire-nyk-aa01.stream.aol.com:80/stream/1035](http://scfire-nyk-aa01.stream.aol.com:80/stream/1035)

I have installed the Mediubuntu command and key. What else is needed?

---

### Post by Dastez on 2008-11-03
Hi geovino,

Try "sudo apt-get install libxine1-ffmpeg" in a console.
This solve all for me.

Regards.

---

### Post by geovino on 2008-11-04
Thank you! That got it working :)

[Solved]

---

