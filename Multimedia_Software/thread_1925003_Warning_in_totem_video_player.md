---
title: "Warning in totem video player"
date: 2012-02-13
forum: Multimedia Software
---

### Post by aocferreira on 2012-02-13
Hello,

Whenever i try to start totem to run in background mode (totem &)  everything works fine. But when I open any video, I always get an  error/warning on my terminal:

***Problem inhibiting the screensaver: GDBus.Error[IMG]http://static.linuxquestions.org/questions/images/smilies/redface.gif[/IMG]rg.freedesktop.DBus.Error.NameHasNoOwner: Name "org.gnome.SessionManager" does not exist***

Can anyone tell me what's the problem and how can I fix this annoying situation? Thanks in advance.

BR,
André

---

### Post by Yellow Pasque on 2012-02-13
What version of Ubuntu are you using? If you're using Unity, the warning is probably because totem is expecting gnome to be running.

---

### Post by pixel :-) on 2012-03-12
try deactivating visual effects. I think all the lib* options make it crash.

edit>preferences>display>Visual effects

If it works you can try reactivating it, but by choosing GOOM.

---

