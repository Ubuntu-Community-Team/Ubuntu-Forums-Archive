---
title: "3D Acceleration Broken - How do I fix it ???"
date: 2006-02-21
forum: Multimedia &amp; Video
---

### Post by kudu on 2006-02-21
Attempting to run a game in Cedega locked up necessitating a ctl-alt-backspace to get out but it killed my 3D acceleration...AGAIN!

I have an Nvidia 6800 GT card which runs at 12000+ FPS normally, but is now running at 60 FPS. I tried re-enabling nvidia-glx-config but no dice.

How do I fix this without having to re-install my OS ?? ...AGAIN!

Please HELP!

---

### Post by Perfect Storm on 2006-02-21
How's your xorg.conf looks like?

---

### Post by kudu on 2006-02-21
That's the funny thing. It looks perfect. Anyway, I figured out how to fix it. I uninstalled nvidia-glx, rebooted, got a damaged xserver terminal, used nano to edit the xorg.conf to use stock default nv X driver, rebooted into X, reinstalled nvidia-glx etc., happiness.

I also managed to fix my problem trying to install the i686 kernel. Cool! Everything always comes out for the best.

\\:D/

---

### Post by kudu on 2006-02-22
It's broken again! I tried Cedega 5.1 again and it definitely kills my 3D Acceleration. I have no idea how, but it does. Now I can't get it back. I've tried everything. How the hell do you enable Acceleration other than xorg.conf ? Something somewhere is choking my card. I really really don't want to do another reinstall.

[SIZE="6"]Help![/SIZE]

---

### Post by kudu on 2006-02-22
HA! I figured it out...God what an imbecile I am.

I had Sync to VBlank in OpenGL Performance checked in Nvidia-Settings, effectvely throttling down my FPS to 60 FPS. I need Sync to VBlank checked for Xserver Xvideo adapter otherwise OpenGL programs twirl around a million cycles per second. Had the wrong box checked is all. Ahhh! Now I can rest...

---

### Post by Perfect Storm on 2006-02-22
What I know is that there some problem with the newest cedega, you might try a previous version to see if that might be the problem.

---

### Post by kudu on 2006-02-22
[QUOTE=Artificial Intelligence]What I know is that there some problem with the newest cedega, you might try a previous version to see if that might be the problem.[/QUOTE]

Actually, I have no problems with 5.1 now that I figured out I was the idiot in charge. It works fine, at least for the stuff I use it for.

Nope...was operator error. Nvidia-Settings adjusted, all works. Thanks for helping me sort it out though, very much appreciated.

regards,
kudu

---

