---
title: "snd_emu10k1 restart GDM"
date: 2012-10-06
forum: Multimedia Software
---

### Post by mr.suchy on 2012-10-06
Hi everyone!

I have problem with my sound blaster 5.1. Like u probably know I use ALSA and Pulsaudio in my desktop. Now I try describe the problem. When I listen radio or music in Rythmbox I have the same error. Error occurs randomly. My syslog:
```

Oct  6 10:17:13  gdm-simple-greeter[7451]: last message repeated 4 times
Oct  6 10:17:13 ubuntu-desktop gdm-simple-greeter[7451]: Gtk-WARNING: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkwidget.c:7117: widget not within a GtkWindow
Oct  6 10:17:13 ubuntu-desktop gdm-simple-greeter[7451]: Gtk-CRITICAL: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed
Oct  6 10:17:13 ubuntu-desktop gdm-simple-greeter[7451]: Gtk-CRITICAL: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed
Oct  6 10:17:13 ubuntu-desktop gdm-simple-greeter[7451]: Gtk-WARNING: gtk_widget_size_allocate(): attempt to allocate widget with width -47 and height -47
Oct  6 10:17:13 ubuntu-desktop gdm-simple-greeter[7451]: Gtk-CRITICAL: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed
Oct  6 10:17:13 ubuntu-desktop gdm-simple-greeter[7451]: Gtk-CRITICAL: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed
Oct  6 10:17:13 ubuntu-desktop gdm-simple-greeter[7451]: Gtk-WARNING: gtk_widget_size_allocate(): attempt to allocate widget with width -47 and height -47
Oct  6 10:17:13 ubuntu-desktop gdm-simple-greeter[7451]: CRITICAL: get_column_number: assertion `i < gtk_tree_view_get_n_columns (treeview)' failed
Oct  6 10:17:13 ubuntu-desktop gdm-simple-greeter[7451]: CRITICAL: get_column_number: assertion `i < gtk_tree_view_get_n_columns (treeview)' failed
Oct  6 10:17:19 ubuntu-desktop rtkit-daemon[1356]: Successfully made thread 7585 of process 7585 (n/a) owned by '1000' high priority at nice level -11.
Oct  6 10:17:19 ubuntu-desktop rtkit-daemon[1356]: Supervising 4 threads of 2 processes of 2 users.
Oct  6 10:17:19 ubuntu-desktop pulseaudio[7585]: [pulseaudio] pid.c: Stale PID file, overwriting.
Oct  6 10:17:19 ubuntu-desktop pulseaudio[7585]: [pulseaudio] sink.c: Default and alternate sample rates are the same.
Oct  6 10:17:19 ubuntu-desktop rtkit-daemon[1356]: Successfully made thread 7591 of process 7585 (n/a) owned by '1000' RT at priority 5.
Oct  6 10:17:19 ubuntu-desktop rtkit-daemon[1356]: Supervising 5 threads of 2 processes of 2 users.
Oct  6 10:17:19 ubuntu-desktop pulseaudio[7585]: [alsa-sink] alsa-sink.c: Us&#322;uga ALSA zosta&#322;a wybudzona, aby zapisa&#263; nowe dane do urz&#261;dzenia, ale nie by&#322;o nic do zapisania.
Oct  6 10:17:19 ubuntu-desktop pulseaudio[7585]: [alsa-sink] alsa-sink.c: Prawdopodobnie jest to b&#322;&#261;d w sterowniku ALSA "snd_emu10k1". Prosz&#281; zg&#322;osi&#263; ten problem programistom us&#322;ugi ALSA.
Oct  6 10:17:19 ubuntu-desktop pulseaudio[7585]: [alsa-sink] alsa-sink.c: Wybudzono za pomoc&#261; ustawienia POLLOUT - ale jednoczesne wywo&#322;anie snd_pcm_avail() zwróci&#322;o zero lub inn&#261; warto&#347;&#263; < min_avail.
Oct  6 10:17:19 ubuntu-desktop rtkit-daemon[1356]: Successfully made thread 7592 of process 7585 (n/a) owned by '1000' RT at priority 5.
Oct  6 10:17:19 ubuntu-desktop rtkit-daemon[1356]: Supervising 6 threads of 2 processes of 2 users.
Oct  6 10:17:25 ubuntu-desktop kernel: [ 5736.394226] do_general_protection: 36 callbacks suppressed
Oct  6 10:17:25 ubuntu-desktop kernel: [ 5736.394232] dropbox[7600] general protection ip:81080a8 sp:bfe49210 error:0 in python2.7[8048000+256000]
Oct  6 10:18:23 ubuntu-desktop dbus[600]: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper)
Oct  6 10:18:23 ubuntu-desktop AptDaemon: INFO: Initializing daemon
Oct  6 10:18:23 ubuntu-desktop AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
Oct  6 10:18:23 ubuntu-desktop dbus[600]: [system] Successfully activated service 'org.freedesktop.PackageKit'
Oct  6 10:18:23 ubuntu-desktop AptDaemon.PackageKit: INFO: Initializing PackageKit transaction
Oct  6 10:18:23 ubuntu-desktop AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/173df5648d054361a958fae53cbe18d5
Oct  6 10:18:23 ubuntu-desktop AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/173df5648d054361a958fae53cbe18d5
Oct  6 10:18:24 ubuntu-desktop AptDaemon.PackageKit: INFO: Get updates()

```

and the my gdm, gui restart automatic. I will help and translate this: "This is probably a bug in the ALSA driver 'snd_emu10k1 ". Please report the issue to the ALSA developers services." What can I do ? Sorry for my language.

Best regards!

---

