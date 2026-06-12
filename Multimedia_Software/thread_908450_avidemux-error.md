---
title: "avidemux-error"
date: 2008-09-02
forum: Multimedia Software
---

### Post by sourlemonhead on 2008-09-02
when i try to play a video, it says audio device not found, anyone have any ideas on how to fix this??:confused:

---

### Post by Keith Hedger on 2008-09-02
I've had this message a few times it usually means another app has grabbed the sound device (when I'm playing music etc) try making sure no other app is trying to use the audio device

---

### Post by sourlemonhead on 2008-09-02
> I've had this message a few times it usually means another app has grabbed the sound device (when I'm playing music etc) try making sure no other app is trying to use the audio device
no other media app is up,could the browser be doing it?(I'm not playing any videos or sound from the browser as of this moment)

---

### Post by Avoozl on 2008-09-02
Sometimes flash grabs the sound from my system and I have to close the browser.  If that doesn't work you can try "killall esd" and then alt+F2 and type "esd &" to start esd again when you are done.

---

### Post by sourlemonhead on 2008-09-02
> **Avoozl said:**
> Sometimes flash grabs the sound from my system and I have to close the browser.  If that doesn't work you can try "killall esd" and then alt+F2 and type "esd &" to start esd again when you are done.
still doesnt work:(

---

### Post by sourlemonhead on 2008-09-02
on above i noticed i put audio device not found, it actually says Trouble initializing audio device.

---

### Post by Avoozl on 2008-09-02
There's an apparent fix in the thread here.

[http://ubuntuforums.org/showthread.php?t=513901](http://ubuntuforums.org/showthread.php?t=513901)

---

