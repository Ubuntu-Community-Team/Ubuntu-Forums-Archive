---
title: "No Sound"
date: 2007-05-29
forum: Multimedia &amp; Video
---

### Post by abbasali31 on 2007-05-29
I just successfully installed Ubuntu, and am loving it.  I got almost everything to work except the sound.  There is a red mark on my volume control button, and when I click on it, it states that I need Gstreamer Plugin.  Being a new Linux users, I don't know which plugin to download.

Please help.

Thanks,

---

### Post by frozinfire on 2007-05-29
ALSA would be my first choice, but you could probably just download several (/all) of them and let the computer do the work for you.

BTW, have you updated ALSA since you installed?

---

### Post by abbasali31 on 2007-05-29
No I haven't, but I certainly can.

The question is how to install the plugin in Linux.  I a long time Windows users.

---

### Post by frozinfire on 2007-05-29
Go to System -> Administration -> Synaptic Package Manager, and do a search for gstreamer. It should give you a list of options. To the left of the plugin's name, you should see an empty white box. Click on it, select "mark for installation," and click the "Apply" toolbar button.

---

### Post by abbasali31 on 2007-05-29
I installed the Plugin the way you told me, and it went fine.  But, I still have a red icon on my volume control, and when I click on it it states:

No Volume Control Gstreamer Plugin and/or device found.

Thanks,

---

### Post by frozinfire on 2007-05-29
Try updating your alsa drivers. There's a great guide [here]("http://ubuntuforums.org/showthread.php?t=205449").

Also, go to Applications -> Add/Remove, do a search for "gstreamer," and make sure you've installed those plugins.

---

