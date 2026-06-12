---
title: "Annoying SOUND problems in KDE4"
date: 2010-09-09
forum: Multimedia Software
---

### Post by Rytis on 2010-09-09
Hello,
I am getting mad about 10.10. Nothing is working as it should work!

Sound... Ok, system sounds is working. Amarok is working. But it doesn't work in VLC, flash, etc. GNOME: works, but only starts working, when sound is changed.

(No idea, but KCMInit always crashes at start (segm fault)).

What I supposed to do?

---

### Post by Rytis on 2010-09-10
Oh, now I dont have sound at all! What I supposed to do?

[IMG]http://img823.imageshack.us/img823/5863/snapshot3c.png[/IMG]

Edit: sound works through headphones from amarok, but not from any other software.
Edit v2: after restart sound is not working at all again. At system start I get this message:
[IMG]http://img96.imageshack.us/img96/1690/snapshot3kp.png[/IMG]

---

### Post by Yellow Pasque on 2010-09-10
Did you uninstall pulseaudio, or is it just not showing up in Phonon settings? It sounds like Phonon is grabbing the sound device and locking out pulseaudio (which all your other apps are probably using). This is why Phonon apps (KDE sounds and Amarok) work and nothing else does.

---

### Post by matyasfalvi on 2010-09-29
Hi Everybody!

I have a very similar problem I have described in this thread:
[http://ubuntuforums.org/showthread.php?t=1537940]("http://ubuntuforums.org/showthread.php?t=1537940")

I have been struggling with this for a while now and I couldn't find any reasonable solution. 

Bottom line is: 
My system uninstalled pulseaudio and I can't reinstall it proper. There is no way somehow. I can reinstall pulseaudio but my sound is barely working after that. I'm also not able to prefer pulseaudio as the default sound server in System settings -> Multimedia. No matter what so ever. :-(

Any help is much appreciated. I have been really suffering from this now for a while.

Thank you.

Take care.

---

