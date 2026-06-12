---
title: "MCC 8.04 crashes"
date: 2008-03-12
forum: Mythbuntu
---

### Post by tomansbro on 2008-03-12
When I enable remote ( hauppauge tv) lirc works fine to control mythtv If I enable Ir transmitter ( hauppauge pvr 150 dish receiver)
 Mcc crashes???  is this a bug or am I missing something?
 using alfa 4

---

### Post by laga on 2008-03-12
Please open a terminal, type

```

sudo /usr/share/mythbuntu-control-centre/bin/mythbuntu-control-centre
```

and do whatever you did to make it crash. Once it crashed, you should see some output in the terminal window. Please post it here so we can fix it. Thanks!

---

### Post by tomansbro on 2008-03-12
tom@tom-desktop:~$ sudo /usr/share/mythbuntu-control-centre/bin/mythbuntu-control-centre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py", line 1525, in toggle_role
    old_u_active=self.config.get("mythbuntu","ubuntu-desktop")
  File "/usr/lib/python2.5/ConfigParser.py", line 520, in get
    raise NoOptionError(option, section)
ConfigParser.NoOptionError: No option 'ubuntu-desktop' in section: 'mythbuntu'
Traceback (most recent call last):
  File "/usr/share/mythbuntu-control-centre/bin/mythbuntu-control-centre", line 46, in <module>
    script = ControlCentre()
  File "/usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py", line 190, in __init__
    self.revert_gui()
  File "/usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py", line 1298, in revert_gui
    self.query_system_state()
  File "/usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py", line 1092, in query_system_state
    if self.communicator.run("get","mythweb/enable") == "true":
  File "/var/lib/python-support/python2.5/mythbuntu_common/debconftalk.py", line 43, in run
    response = debconf_read.readlines()[0].partition(' ')
IndexError: list index out of range

---

### Post by tomansbro on 2008-03-12
this is after I enable transmitter

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py", line 1525, in toggle_role
    old_u_active=self.config.get("mythbuntu","ubuntu-desktop")
  File "/usr/lib/python2.5/ConfigParser.py", line 520, in get
    raise NoOptionError(option, section)
ConfigParser.NoOptionError: No option 'ubuntu-desktop' in section: 'mythbuntu'
/usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py:206: GtkWarning: gtk_file_folder_unix_get_info: assertion `strcmp (dirname, folder_unix->filename) == 0' failed
  gtk.main()
 * Reloading kernel event manager...                                     [ OK ] 
 * Loading LIRC modules                                                  [ OK ] 
 * Starting remote control daemon(s) : LIRC                              [fail] 
 * Stopping remote control daemon(s): LIRC                               [ OK ] 

Reading package lists... Done
Building dependency tree       
Reading state information... Done

---

### Post by laga on 2008-03-13
Hi,

please file a bug report for each of those backtraces at [https://bugs.launchpad.net/ubuntu/+source/mythbuntu-control-centre/+filebug](https://bugs.launchpad.net/ubuntu/+source/mythbuntu-control-centre/+filebug)

Also mention what you did to provoke those crashes. Thanks!

---

