---
title: "Change ALSA default input"
date: 2008-05-30
forum: Multimedia Software
---

### Post by forezt on 2008-05-30
I just installed a sound blaster audigy SE, and after some tinkering got everything working great, even the microphone.

However, the default microphone input is not correct. I have to manually choose "CA0106 (hw:CA0106,1)" for "sound in" to get it to work.

How do I set this device as the default, so it works when I choose "Default device (default)"?

---

### Post by forezt on 2008-06-01
Bump?

Let me clarify my problem. I recently installed a new sound card (Audigy SE) and everything works, except the default mic in is not correct. My workaround is currently to go into each application and manually tell it what device to use. 

How do I set a default input device for ALSA, so that I can tell it to use the correct device?

I imagine it would involve doing something to /etc/asound.conf, but I can't get the right settings. If you need any more information please tell me. Thank you.

---

### Post by markbuntu on 2008-06-01
I think you can change the default mic in the gnome alsa mixer if you have it. I know there is a selection box for that in there but I only have one mic input so it does not do anything for me.

---

