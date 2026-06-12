---
title: "Samba Config doesn't want to open"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by Zyferian on 2008-12-06
Hey, all... I went through and installed all the components of Samba that people seem to think are important, including the system-samba-config one. Then, when I went to open it on the menu, it promptly gave me a massive error and crashed. It doesn't even get open all the way... I'm not sure what's going on. 

Does anyone have any leads?

---

### Post by stinger30au on 2008-12-06
try un installing the lot via synaptic and reinstall and see what happens

---

### Post by Zyferian on 2008-12-06
> **stinger30au said:**
> try un installing the lot via synaptic and reinstall and see what happens
After doing this... the same problem occurs. The Samba config program crashes before it even gets a chance to really run first.

Here's the output... 
```
~$ sudo system-config-samba
[sudo] password for akcin: 
Traceback (most recent call last):
  File "/usr/sbin/system-config-samba", line 41, in <module>
    mainWindow.MainWindow(debug_flag)
  File "/usr/share/system-config-samba/mainWindow.py", line 118, in __init__
    self.basic_preferences_win = basicPreferencesWin.BasicPreferencesWin(self, self.xml, self.samba_data, self.samba_backend, self.main_window)
  File "/usr/share/system-config-samba/basicPreferencesWin.py", line 93, in __init__
    self.admin = libuser.admin()
SystemError: could not open configuration file `/etc/libuser.conf': No such file or directory

```

---

