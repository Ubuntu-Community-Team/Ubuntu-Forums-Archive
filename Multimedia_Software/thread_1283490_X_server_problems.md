---
title: "X server problems"
date: 2009-10-05
forum: Multimedia Software
---

### Post by flakas on 2009-10-05
Hello,
I am running HP Pavilion dv9000. It's VGA (8400M GS) has fried a bit, but still works, although video and text is not very good.
I have installed a fresh version of ubuntu 9.04
Then i tried updating. After newest updates were installed, i rebooted my laptop. Then evil things started. I get a blue screen with this:

Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?
Y/n

I select yes. Output:

Warning: Failsafe mode was already attempted within 30 seconds.
Warning: Falling back to gdm to report the issue.

I tried reconfiguring xserver (dpkg-reconfigure -phigh xserver-xorg), installing nvidia drivers (i don't know why, probably wouldn't help).

I am planning to use it as a web server, but at least minimal 800x600 graphical display is necessary for me.

Could you help me out?



By the way,
Another problem. Even when i am booting LiveCD it starts in low-graphics mode(DDC tables not found; screens found, but none have usable configuration). Installing nvidia drivers does not help(more errors. cannot load nvidia glx module). I would be grateful if you would help me with this too.

---

### Post by flakas on 2009-10-06
Help, please?


Xserver works again. It must be my faulty VGA's fault - when it gets hotter, it does not work normally after PC is restarted. Few external fans should help it cooler.

---

