---
title: "Help! Jaunty LOUD beep shutdown..."
date: 2009-07-18
forum: Multimedia Software
---

### Post by gm_w on 2009-07-18
I am getting this very loud beep at shutdown... I have no idea how to turn it off. I tried several methods I found everywhere:

1. add "blacklist pcspkr" to /etc/modprobe.d/blacklist.conf 
This does not work. I don't believe the beep is coming from the pc speaker.

2. sudo modprobe -r pcspkr
I get the following two warnings and does not remove the beep at shutdown
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.

3. sudo rmmod pcspkr
I get this error: ERROR: Module pcspkr does not exist in /proc/modules

4. gconftool-2 --type bool --set /apps/metacity/general/audible_bell False
No effect here.

5. Disabled all sound alerts -- beep is still there at shutdown.

I havev Dell vostro 1500. Can anyone help me remove this annoying beep at shutdown?

---

### Post by miniyak on 2009-07-18
i have this issue on one of my older machines (dell demention 2350)

pretty sure it is a system beep though in my case, interested in seeing solution/suggestions regardless

---

### Post by budajeff on 2009-07-20
I have a related problem. I get a loud beep on resume from hibernate and sometimes when I boot and jaunty detects that one of my USB ports is bad.

---

