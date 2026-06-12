---
title: "How to enable Vsync in aticonfig"
date: 2006-08-31
forum: Multimedia &amp; Video
---

### Post by WalmartSniperLX on 2006-08-31
Hi. Ive been trying to enable vsync with my ati graphics card using the standard aticonfig command. Does anyone know the exact command or way to enable this setting? I tried using : *aticonfig --sync-vsync=on * but it says:


[I] Warning: Option 'Capabilities' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-1
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.[/I]

Am I doing a wrong command or something? Please help

---

### Post by theearp on 2006-09-08
sudo aticonfig --sync-vsync=on

---

