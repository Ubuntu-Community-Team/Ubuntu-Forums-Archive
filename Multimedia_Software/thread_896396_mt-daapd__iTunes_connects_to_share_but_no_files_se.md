---
title: "mt-daapd:  iTunes connects to share but no files served"
date: 2008-08-21
forum: Multimedia Software
---

### Post by Bllz on 2008-08-21
Hello:

I successfully managed to get mt-daapd to set up a shared library to which my windows itunes client could connect.  Unfortunately, mt-daapd is not serving any files even after multiple full scans and my chmod 777 of the host directory.

What gives?  I'd be glad to post any relevant info that could be needed.

Bllz

---

### Post by Bllz on 2008-08-21
Bump


I just noticed that the WebUI is giving me a "Service: Bonjour Stopped"  message even though i have avahi-daemon running.

Could this be part of the problem?

---

### Post by kronepils on 2008-08-25
Hi,

I think, that if Avahi/Bonjour isn't running/working, iTunes can't even see your share.
Also, remember, that iTunes is doing the actual playing of your media files. Rememeber, that they have to be in a format that iTunes can read. It won't play ogg files without a patch for instance.

---

### Post by jcbwalsh on 2008-09-02
I think iTunes does something to make this not work with anything other than another copy of iTunes. I've just found a great alternative called SimplifyMedia - [http://www.simplifymedia.com/](http://www.simplifymedia.com/) . It works with iTunes on Windows and Mac and Rhythmbox in Ubuntu 8.04. Works like a charm for me.

---

