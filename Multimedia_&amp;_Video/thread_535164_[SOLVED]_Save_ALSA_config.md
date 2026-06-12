---
title: "[SOLVED] Save ALSA config"
date: 2007-08-26
forum: Multimedia &amp; Video
---

### Post by Calle on 2007-08-26
Hey!
I'm enjoying the new 7.04 release, but got this one problem:
Each time I reboot, the volume control tracks are reset. And as I have surround speakers, I have to drag and adjust about 5 of these controllers after every reboot. Where can I save my config?

Thanks in advance!

---

### Post by K.Mandla on 2007-08-26
I don't know if this will work for you or not, but it's worth a try. 

Boot normally, then set your volume levels how you want them. Then, from a terminal, try this command.

```
sudo alsactl store
```
Hopefully that will write a little file at /etc/asound.state that has your current sound settings in it. You can check and see if the file is there, and what's in it, with this command.

```
cat /etc/asound.state
```

Reboot and see how it goes. Cross your fingers. ... ;)

---

### Post by Calle on 2007-08-26
Thanks K.Mandla!
The file didn't save to /etc/asound.state, but /var/lib/alsa/asound.state.
I'll see what happens after reboot.

---

### Post by K.Mandla on 2007-08-26
Good to know. I'm using Arch right now, so they must move that file to /etc. ;)

---

### Post by Calle on 2007-08-26
Alrighty, it sure did work, thanks alot!

---

### Post by K.Mandla on 2007-08-26
Great, I'll mark this thread as solved. ;)

---

