---
title: "Failed to start Portal service"
date: 2024-01-12
forum: MINT
---

### Post by krolaper on 2024-01-12
Operating System: Ubuntu 22.04
XDG Desktop Portal version: 1.14.4-1ubuntu2~22.04.1
Desktop Environment: Xfce
Expected Behavior: Not the occurrence of these errors, but the successful launch of services

Current Behavior:

System:
  Desktop: Xfce 4.16.0 Distro: Linux Mint 21 Vanessa base: Ubuntu 22.04 jammy

Magazines:
Failed to start Portal service.
Failed to start XFCE notifications service.

systemctl --user status xdg-desktop-portal :
   Loaded: loaded (/usr/lib/systemd/user/xdg-desktop-portal.service; static)
   Active: failed (Result: timeout) since Fri 2024-01-12 07:57:16 EET; 2min 6>
  Process: 7088 ExecStart=/usr/libexec/xdg-desktop-portal (code=killed, signa>
 Main PID: 7088 (code=killed, signal=TERM)
      CPU: 45ms
systemd[1867]: Starting Portal service...
xdg-desktop-por[7088]: Failed to create settings prox>
xdg-desktop-por[7088]: No skeleton to export
xdg-desktop-por[7088]: Failed to create file chooser >
xdg-desktop-por[7088]: No skeleton to export
systemd[1867]: xdg-desktop-portal.service: start oper>
systemd[1867]: xdg-desktop-portal.service: Failed wit>
systemd[1867]: Failed to start Portal service.

systemctl --user status xdg-desktop-portal-gtk :
   Loaded: loaded (/usr/lib/systemd/user/xdg-desktop-portal-gtk.service; stat>
   Active: failed (Result: exit-code) since Fri 2024-01-12 07:55:46 EET; 18mi>
  Process: 7092 ExecStart=/usr/libexec/xdg-desktop-portal-gtk (code=exited, s>
 Main PID: 7092 (code=exited, status=1/FAILURE)
      CPU: 15ms
systemd[1867]: Starting Portal service (GTK/GNOME imp>
systemd[1867]: xdg-desktop-portal-gtk.service: Main p>
systemd[1867]: xdg-desktop-portal-gtk.service: Failed>
systemd[1867]: Failed to start Portal service (GTK/GN

Synaptic installed:
xdg-desktop-portal version: 1.14.4-1ubuntu2~22.04.1 - last

Answer flatpak https://github.com/flatpak/xdg-desktop-portal/issues/1264

Will there be support for newer versions?

---

### Post by QIII on 2024-01-12
Moved to MINT

---

