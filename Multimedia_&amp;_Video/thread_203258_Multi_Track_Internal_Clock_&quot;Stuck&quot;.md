---
title: "Multi Track Internal Clock &quot;Stuck&quot;"
date: 2006-06-24
forum: Multimedia &amp; Video
---

### Post by souled on 2006-06-24
Alright... So I was playing around with the Volume Control menu when all of a sudden, something happened. I'm not exactly sure what happened, but here are the results. My sound no longer works. I think this is because the Multi Track Internal Clock is "stuck" at IEC958 Input (it's usually at 48000). I have no idea why this is. In alsamixer, I can't change it back to 48000; it doesn't move from IEC958I. In the Volume Control menu, I can change it from the dropdown menu, but when I exit, it just sets back to IEC958 Input. Is there a way for me to reset the control menu to default settings or something? I tried alsactrl restore, but that doesn't help. I'm pretty sure this is why my sound doesn't work... What can I do to fix this?

Also, when I try to play something from amaroK,  the bars start to move (but no sound), and then amaroK locks up.

---

### Post by GrumpySmurf on 2007-02-19
I am having this problem as well. I reported a bug on launchpad:

[https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/86325](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/86325)

---

### Post by blanko on 2007-12-23
i too had this problem. I fixed it by simply uninstalling and reinstalling alsa-base and alsa-utils in synaptic.

---

