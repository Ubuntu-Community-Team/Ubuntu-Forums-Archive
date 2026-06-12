---
title: "New monitor, weird problem"
date: 2006-06-07
forum: Multimedia &amp; Video
---

### Post by Ian Maxwell on 2006-06-07
I just bought a new LCD monitor recently: a Princeton VL1918. Overall it works okay, but when I tried to up my screen res to 1280x1024 I got a weird result: the usable space for windows was the full 1280x1024, but the desktop icons and toolbars were stuck in the old 1152x864 box (even though I could see them if I pulled them outside, they bounced right back when I let go).

I managed to solve this by changing the res to something else and back, and saving it as the new default in the process. This causes a totally different problem: going back to the GDM login screen from my session makes the monitor go black, and from there it stays black even if I switch to, say, a text TTY. This is not a problem if I go to the GDM logon screen from anywhere else (say, on bootup).

Right now I can avert this by simply never logging out (I'm the only user on this computer), but it's a really stupid thing and I'd like to solve it. Any clues what's up?

---

### Post by mlind on 2006-06-07
It's could be that your monitor is using wrong/old settings.
Have you tried to reconfigure X-Server ?

```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by Ian Maxwell on 2006-06-07
I did, and that's exactly when  problems started showing up, even though it correctly detected the model and everything.

---

### Post by mlind on 2006-06-07
If the monitor stays blank even if you're switching to text tty, then there's something
definely wrong. Have you tried if this happens with generic 'vesa' driver too?

Are you forcing any special VESA framebuffer modes on grub.conf ?
Does /var/log/Xorg.0.log contain any warnings or errors regarding to the problem ?

---

### Post by joshchernoff on 2006-07-28
I installed the desktop from ssh on to my server and ran in to this same problem. I had to do a reconfigure on the box it's self for it to see my hardware.

---

