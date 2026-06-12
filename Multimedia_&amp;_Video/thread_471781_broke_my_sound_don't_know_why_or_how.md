---
title: "broke my sound? don't know why or how?"
date: 2007-06-12
forum: Multimedia &amp; Video
---

### Post by shane2peru on 2007-06-12
Help, I broke my sound.  I don't know what I did, or how I did it, but it is very annoying.  What can I do to fix it?  Something must have reconfigured my sound.  I can hear it but it is very faint.  Volume is turned up on panel, and on Rythmbox.  My system sound is very soft too.  I have to have the volume on my speakers all the way up to be able to hear anything.  HELP!  Thanks.

Shane

---

### Post by shane2peru on 2007-06-12
Ok, this is weird.  I opened up realplayer and noticed the volume was turned way down.  I turned it up, and it was as if my whole system sound was tied to realplayer volume control.  ???  I don't understand that at all.  At any rate my problem is solved.  

Shane

---

### Post by osxdude on 2007-06-12
It also could have been your speakers.

---

### Post by shane2peru on 2007-06-12
> **osxdude said:**
> It also could have been your speakers.

Actually my speakers were turned all the way up, and when I opened a real audio file and turned the sound on the program 'realplayer' up they were really loud.  Sorry if I didn't clarify that.  It was some sort of setting in the computer somewhere, and some how tied to RealPlayer, or seemingly so.

Shane

---

### Post by HotShotDJ on 2007-06-12
PCM must have been turned down -- the realplayer volume probably uses the system's PCM control rather than the master volume.

---

### Post by shane2peru on 2007-06-12
> **HotShotDJ said:**
> PCM must have been turned down -- the realplayer volume probably uses the system's PCM control rather than the master volume.

what is PCM and how would I access it outside of realplayer?  For next time.

Shane

---

### Post by HotShotDJ on 2007-06-13
OOPS... Sorry it took so long to get back to you on this... I'm not sure of the Gnome specific application -- in KDE, it is KMixer.  However, on all systems, you can use the command "alsamixer" from the command line (without the quotes, of course) and you'll find PCM there.  Use the L/R arrow buttons to switch between the controls and U/D arrows to raise or lower the controls.

---

### Post by shane2peru on 2007-06-13
> **HotShotDJ said:**
> OOPS... Sorry it took so long to get back to you on this... I'm not sure of the Gnome specific application -- in KDE, it is KMixer.  However, on all systems, you can use the command "alsamixer" from the command line (without the quotes, of course) and you'll find PCM there.  Use the L/R arrow buttons to switch between the controls and U/D arrows to raise or lower the controls.

Thanks!  That was really cool.  

Shane

---

### Post by cookiefreak on 2007-06-14
alsamixer help me a lot! thanks! HotShotDJ!

---

### Post by shane2peru on 2007-06-14
if someone knows the trick to opening that without command line in Gnome, I would love to hear it.  I don't mind using the command line, but GUI, usually looks a little nicer.  Thanks!

Shane

---

### Post by crane on 2007-06-14
You should be able to double click your sound icon and open the sound control panel. Then if you look through you menus, you should be able to select preferences where you can add and remove controls. You should be able to add the PCM volume there.

---

### Post by shane2peru on 2007-06-14
> **crane said:**
> You should be able to double click your sound icon and open the sound control panel. Then if you look through you menus, you should be able to select preferences where you can add and remove controls. You should be able to add the PCM volume there.

Hey now that is cool.  Thanks a bundle!

Shane

---

