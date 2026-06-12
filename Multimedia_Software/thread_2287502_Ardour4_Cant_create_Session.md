---
title: "Ardour4 Cant create Session"
date: 2015-07-20
forum: Multimedia Software
---

### Post by Prem_Reginald on 2015-07-20
[COLOR=#333333][FONT=Open Sans]Hi,[/FONT][/COLOR]
[COLOR=#333333][FONT=Open Sans]I just installed ardour4 (4.0.111+r12804 ) and am facing problem creating a session.[/FONT][/COLOR]
[COLOR=#333333][FONT=Open Sans]the message box states "Could not create a session in /home/user/a"[/FONT][/COLOR]
[COLOR=#333333][FONT=Open Sans]This is the output from terminal.
```

prem-dell:~$ ardour4
WARNING: Your system has a limit for maximum amount of locked memory!
This might cause Ardour to run out of memory before your system runs
out of memory. You can view the memory limit with 'ulimit -l', and it
is normally controlled by /etc/security/limits.conf
bind txt domain [gtk2_ardour4] to /usr/share/ardour4/locale
Ardour4.0.111+r12804 (built using 4.0.111+r12804.21 and GCC version 4.8.4)
ardour: [INFO]: Your system is configured to limit Ardour to only 4096 open files
ardour: [WARNING]: Illegal value loaded for N6ARDOUR16AutoReturnTargetE (15) - LastLocate used instead
ardour: [INFO]: Loading system configuration file /etc/ardour4/system_config
Loading user configuration file /home/prem/.config/ardour4/config
Using SSE optimized routines
ardour: [INFO]: Loading default ui configuration file /etc/ardour4/default_ui_config
ardour: [INFO]: Loading user ui configuration file /home/prem/.config/ardour4/ui_config
ardour: [INFO]: Loading color file /etc/ardour4/dark.colors
ardour: [INFO]: Loading ui configuration file /etc/ardour4/clearlooks.rc
ardour: [INFO]: Loading ui configuration file /etc/ardour4/clearlooks.rc
Cannot lock down 82274202 byte memory area (Cannot allocate memory)
Cannot lock down 82274202 byte memory area (Cannot allocate memory)
Found nothing along /home/prem/.config/ardour4/
run dialog
```[/FONT][/COLOR]

---

