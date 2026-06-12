---
title: "Error: Exception in capturestate of plugin MYSQL"
date: 2010-05-29
forum: Mythbuntu
---

### Post by geekyhawkes on 2010-05-29
I have just upgraded from 9.10 to 10.04 mythbuntu and was pretty pleased with how the process went (all in all).  The only noticeable problem i have is the following error window when i run MCC;

ERROR:

Exception in capturestate of plugin MYSQL

Disabling plugin.

Now clearly this is not good, but how do i go about fixing the issue?  

I am running 10.04 64bit mythbuntu with mediatomb and squeezeserver on the same machine.

Thanks

---

### Post by geekyhawkes on 2010-05-31
Anyone have any thoughts on this?  The above error doesnt really give me much in the way of clues what is happening and for the most part the machine seems to be working fine (although mythstream isnt playing ball)

---

### Post by geekyhawkes on 2010-06-19
So plot thickens with this.  After a bit of digging around i have noticed that my squeezebox no longer has my m3 library built in it as well, i am pretty sure that the squeezbox uses mysql so i opted to remove the squeezebox server from my myth machine and restart mythcontrolcenter.  

This time the error i get is ;

Exception in captureState of plugin Mirobridgeconfig

Slightly more revealing than the previous, if i go to the miro page in mcc then any tick selections of install/unistall with an apply do nothing (does see any changes to apply).  

Any ideas whats going on?  Could i just add miro to my software sources and install that way?

---

### Post by geekyhawkes on 2010-06-19
For what it is worth, i also tried a 

mysqlcheck --auto-repair -A -u mythtv -pmysqlpass

when the capture state error was for mysql, but all of the tables came back as "ok"


EDIT:
[https://bugs.launchpad.net/mythbuntu/+bug/558912](https://bugs.launchpad.net/mythbuntu/+bug/558912)

Seems like it might be linked to storage groups some how. (Although that doesnt explain why my squeezeboxserver wont add music, which happened at the same time).  

However, strangely if i sudo mythbuntu-control-center from terminal then it runs fine, without the dialogue warning and allows me to install miro.  Really confused now!


EDIT (again):

So now i am very confused, i have installed miro under sudo mythbuntu-control-center which hasnt really helped as if i open mythbuntu-control-center as my normal user login then i get the same error message.  Likewise, i cannot get miro to run as a normal user as terminal tells me i dont have permission to access the directory.

If i run mcc as a normal user from terminal then i get this back;

Traceback (most recent call last):
  File "/usr/bin/mythbuntu-control-centre", line 375, in refreshState
    plugin.captureState()
  File "/usr/share/mythbuntu/plugins/python/mirobridgeconfig.py", line 99, in captureState
    self.mbfunctions.isInstalled()
  File "/usr/share/mythbuntu/plugins/python/mirobridgeconfig.py", line 571, in isInstalled
    self.getMythtvDirectories()
  File "/usr/share/mythbuntu/plugins/python/mirobridgeconfig.py", line 729, in getMythtvDirectories
    raise MirobridgeconfigPlugin_error(errormsg)
MirobridgeconfigPlugin_error: The MythTV video and/or image directories do not have the proper read/write permission, correct and retry installation, errors are displayed in the log.

/usr/bin/mythbuntu-control-centre:126: GtkWarning: gtk_window_realize_icon: assertion `info->icon_pixmap == NULL' failed
  self.main_window.show()


How do i fix the permissions that are quoted as wrong above, and which log would the errors be in ?

---

### Post by ian dobson on 2010-06-19
Hi,

It looks as if your python is broken. Maybe try reinstalling/repairing python.

Regards
Ian Dobson

---

### Post by tgm4883 on 2010-06-19
start mythbuntu-control-centre from the command line, post the output here. That will tell us more info.

---

### Post by geekyhawkes on 2010-06-19
tgm, the output above is from mcc running as my normal user login. 


Traceback (most recent call last):
File "/usr/bin/mythbuntu-control-centre", line 375, in refreshState
plugin.captureState()
File "/usr/share/mythbuntu/plugins/python/mirobridgeconfig.py", line 99, in captureState
self.mbfunctions.isInstalled()
File "/usr/share/mythbuntu/plugins/python/mirobridgeconfig.py", line 571, in isInstalled
self.getMythtvDirectories()
File "/usr/share/mythbuntu/plugins/python/mirobridgeconfig.py", line 729, in getMythtvDirectories
raise MirobridgeconfigPlugin_error(errormsg)
MirobridgeconfigPlugin_error: The MythTV video and/or image directories do not have the proper read/write permission, correct and retry installation, errors are displayed in the log.

/usr/bin/mythbuntu-control-centre:126: GtkWarning: gtk_window_realize_icon: assertion `info->icon_pixmap == NULL' failed
self.main_window.show()

To re-install python is that as simple as a apt-get remove python / apt-get install python

---

### Post by tgm4883 on 2010-06-19
I don't think you need reinstall python. Try checking the permissions on the directories first per the error message.

```
MirobridgeconfigPlugin_error: The MythTV video and/or image directories do not have the proper read/write permission, correct and retry installation, errors are displayed in the log.
```

---

### Post by geekyhawkes on 2010-06-20
Just to check i understand, you mean the directories i use for fanart, coverart etc?

Im guessing chmod 755 (folders for fanart, screenshots,trailers,etc) should cover it?

---

### Post by geekyhawkes on 2010-06-20
Solved thanks, it was down to permissions.  I am not sure if this is the best way to fix permissions or not but i do have the machine working correctly now;

sudo chmod -R o=rxw (folder name here)

Clearly pretty broad approach to give all other users rxw but i dont think its too big an issue.

Thanks for all of the help

---

