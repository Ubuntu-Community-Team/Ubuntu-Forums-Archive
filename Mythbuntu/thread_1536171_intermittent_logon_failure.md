---
title: "intermittent logon failure"
date: 2010-07-21
forum: Mythbuntu
---

### Post by jonnybignote on 2010-07-21
Hi
So I have an intermittent boot (login) failure that I can't figure out.  Mythbuntu 9.10 64bit.

Mythbuntu loads, screen blanks and load screen returns followed by regular [Gnome?] user login window - in other words autologin fails and my regular mythtv user will not login.  I setup another regular user and I can login with that, so its obviously a user profile specific problem.

This is what I think to be the pertinent entries from my syslog file
[HTML]
Jul 21 17:46:33 MediaPC gnome-session[2603]: devkit-power-gobject-WARNING: Couldn't enumerate devices: The name org.freedesktop.DeviceKit.Power was not provided by any .service files
Jul 21 17:46:33 MediaPC gnome-session[2603]: WARNING: Could not launch application 'metacity.desktop': Unable to start application: Failed to execute child process "metacity" (No such file or directory)
Jul 21 17:46:33 MediaPC gnome-session[2603]: WARNING: Could not launch application 'gnome-power-manager.desktop': Unable to start application: Failed to execute child process "gnome-power-manager" (No such file or directory)
Jul 21 17:46:33 MediaPC gdm-simple-greeter[2615]: devkit-power-gobject-WARNING: Couldn't enumerate devices: The name org.freedesktop.DeviceKit.Power was not provided by any .service files
Jul 21 17:46:33 MediaPC gdm-simple-greeter[2615]: devkit-power-gobject-WARNING: Error invoking GetAll() to get properties: The name org.freedesktop.DeviceKit.Power was not provided by any .service files
Jul 21 17:46:33 MediaPC gdm-simple-greeter[2615]: devkit-power-gobject-WARNING: Error invoking GetAll() to get properties: The name org.freedesktop.DeviceKit.Power was not provided by any .service files
Jul 21 17:46:34 MediaPC pulseaudio[2486]: main.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-snoazn53YE: Connection refused
Jul 21 17:46:35 MediaPC gdm-simple-greeter[2615]: devkit-power-gobject-WARNING: Error invoking GetAll() to get properties: The name org.freedesktop.DeviceKit.Power was not provided by any .service files
Jul 21 17:46:35 MediaPC gdm-simple-greeter[2615]: devkit-power-gobject-WARNING: Error invoking GetAll() to get properties: The name org.freedesktop.DeviceKit.Power was not provided by any .service files
Jul 21 17:47:33 MediaPC kernel: [  102.870025] Clocksource tsc unstable (delta = -258823289 ns)[/HTML]I have so far followed various clues and done things like reinstall gdm, deleting .ICEauthority and often the machine reboots accordingly.  Then the following reboot fails again.  

My machine is instant on with suspend to ram so I run some houskeeping crons in the early hours and end with a reboot to keep things running smoothly - thats when I wake to find the thing stuck.  

After a few tries and maybe a hard reset with fsck on reboot I can get my mythbox up and running.  I'll not be rebooting much until I can fix this obviously.

Any genius's out there with some advice would be most welcome

Thanks all

---

### Post by jonnybignote on 2010-07-21
Forgot to mention that I've just updated the machine after resisting for a great while.

---

