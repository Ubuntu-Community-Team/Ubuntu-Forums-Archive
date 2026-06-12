---
title: "My internal microphone is not working in Ubunto in my lenovo g470"
date: 2012-10-20
forum: Multimedia Software
---

### Post by reinildes on 2012-10-20
Hi everybody!

I'm having this problem with my internal microphone. I look up in the internet and I didn't find anything so I'm here asking someone to help me. 

I have read something about being a bug but i couldn't understand

Please Help me

---

### Post by ajgreeny on 2012-10-20
If you use the command alsamixer in terminal you will get a screen like my screenshot.
Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture".
In capture page use spacebar to enable the different input devices (mic, line, CD, video).
Esc will save and exit.

You may find that the mic channel is too low or muted.

---

### Post by reinildes on 2012-10-20
Thanks for replying!

But it dosen't work! I send the image of my alsamixer:

[http://imageshack.us/a/img339/7463/myalsamixerscreenshot.png](http://imageshack.us/a/img339/7463/myalsamixerscreenshot.png)

Please help me! I don't know what more can I do!

Really, thank you so mutch and please try again! kkkk

---

### Post by ajgreeny on 2012-10-21
If you use the cursor keys to the right is there a "mic" channel?

Also if you use Tab to go to the capture options you may find that the wrong capture device is activated (see new screenshot).  If so move to the mic and use spacebar to activate.

---

