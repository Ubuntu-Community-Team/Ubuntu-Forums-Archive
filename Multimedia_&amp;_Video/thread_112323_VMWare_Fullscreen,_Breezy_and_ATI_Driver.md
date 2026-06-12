---
title: "VMWare Fullscreen, Breezy and ATI Driver"
date: 2006-01-04
forum: Multimedia &amp; Video
---

### Post by jonspinks on 2006-01-04
Hi,
I was wondering if someone may be able to help me.  I've looked through the VMWare forums and have been able to get a little bit further.  Basically since I upgraded to Breezy my VMWare session has been able to enter fullscreen mode but it is really distorted.  This worked fine in Hoary.  I played around with the guest settings but got nowhere.  After reading some info on the VMWare site I tried changing the driver from ati in the xorg conf file to vesa.  VMWare now works in fullscreen mode.  It sounds as though it is a bug in the ATI driver in Breezy.  Does anyone know of a work around or a way to get this raised and looked at?

Thanks for any help
Jon

---

### Post by santo on 2006-03-23
I'm interested in a solution for this problem as well.

---

### Post by santo on 2006-03-23
I just found a (really simple) solution for it.

Make sure your preferences are set correctly:
Edit > Preferences > Display > Full Screen > Resize Guest

This should do the trick

---

### Post by MTZeon on 2006-11-17
You can fix this by:

[http://www.ubuntuforums.org/showthread.php?t=300968&highlight=vmware](http://www.ubuntuforums.org/showthread.php?t=300968&highlight=vmware)

---

