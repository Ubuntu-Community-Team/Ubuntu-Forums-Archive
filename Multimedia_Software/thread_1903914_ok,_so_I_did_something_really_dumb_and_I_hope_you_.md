---
title: "ok, so I did something really dumb and I hope you can help me fix it..."
date: 2012-01-03
forum: Multimedia Software
---

### Post by Silverflyer on 2012-01-03
in my efforts to get rid of Pulse Audio and use ALSA only, I found this website which had directions purporting to allow the disabling of pulse audio on a per session basis needing only a reboot to re-enable...

well, it turns out that is not the case, PulseAudio refuses to re-enable upon a reboot.

the website is here, [http://howto.blbosti.com/2010/04/ubuntu-make-alsa-default-instead-of-pulseaudio/](http://howto.blbosti.com/2010/04/ubuntu-make-alsa-default-instead-of-pulseaudio/)

and I did this command

```
echo autospawn = no|tee -a ~/.pulse/client.conf && killall pulseaudio
```

How do I undo this, and get pulseaudio to restart?

thanks.

---

### Post by mocha on 2012-01-04
Just open the file ~/.pulse/client.conf in a text editor and delete the line autospawn = no.

---

### Post by Silverflyer on 2012-01-04
Thats what I did yesterday.  It worked just fine.  Thanks for the reply, I appreciate it.

---

