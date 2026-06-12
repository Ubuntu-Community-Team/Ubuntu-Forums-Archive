---
title: "cronjob"
date: 2015-05-04
forum: Mythbuntu
---

### Post by deanie44 on 2015-05-04
Hi everyone.  The crontab jobs are not running.  **I get an error message: (gedit:4801): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files**
What does the error mean?  The jobs use to run as scheduled.  For example I would schedule my PC to shutdown at 2300 daily. --
00 23 * * * root power off. Now it does not execute.  Can someone give my some insight on this subject?  Thanks sister5091

---

### Post by ian-weisser on 2015-05-04
ALL cron jobs are not running?
Or just that one cron job is not running?
Does /var/log/syslog have cron error messages?


I don't have a command 'power'. Where did you get it from? Is it perhaps an alias? Or a typo of the one-word 'poweroff'?


Do you get that error frequently throughout the day?
Or only for certain cronjobs?
Or only for the shutdown cronjob that doesn't work? 


The specific answer to your question isn't helpful: DBus is a way for processes to communicate. One process (we don't know what triggered it) is trying, in turn, to trigger another process. The error is because the second process doesn't exist. Might be a typo. Might be renamed. May or may not be relevant to your problem - insufficient data so far.

---

### Post by SeijiSensei on 2015-05-04
The command is "poweroff" with no spaces.  Just fix the entry in crontab.

---

