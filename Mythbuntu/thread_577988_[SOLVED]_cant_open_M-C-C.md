---
title: "[SOLVED] cant open M-C-C"
date: 2007-10-16
forum: Mythbuntu
---

### Post by govee on 2007-10-16
I cant use launcher in menu and this is what I get from the Terminal. I dont know what I did????


andy@andy-dvr:~$ mythbuntu-control-centr
bash: mythbuntu-control-centr: command not found
andy@andy-dvr:~$ mythbuntu-control-centre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
  File "/usr/share/mythbuntu-control-centre/bin/mythbuntu-control-centre", line 46, in <module>
    script = ControlCentre()
  File "/usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py", line 166, in __init__
    self.revert_gui()
  File "/usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py", line 942, in revert_gui
    self.query_system_state()
  File "/usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py", line 610, in query_system_state
    if self.query_installed("ubuntu-desktop"):
  File "/usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py", line 544, in query_installed
    return self.cache[package].CurrentVer
KeyError: 'ubuntu-desktop'

---

### Post by superm1 on 2007-10-16
Can you try to apt-get update and run it again?

---

### Post by karlec on 2007-10-18
I am having the same problem with RC.

---

### Post by superm1 on 2007-10-18
The solution for govee as mentioned in another thread, was the apt-get update.

---

### Post by karlec on 2007-10-18
I have done that but it still does not work.  I have rebooted several times but still no luck.

---

### Post by superm1 on 2007-10-18
...sigh... well that's not a good sign.  

Give this a shot:
[http://ppa.launchpad.net/mythbuntu/ubuntu/pool/main/m/mythbuntu-control-centre/mythbuntu-control-centre_0.11-0ubuntu1~ppa1_all.deb](http://ppa.launchpad.net/mythbuntu/ubuntu/pool/main/m/mythbuntu-control-centre/mythbuntu-control-centre_0.11-0ubuntu1~ppa1_all.deb)

It works around that error that you were getting.  Unfortunately the archives are closed, so it won't be in the ubuntu archives for release.  It will however be on the final mythbuntu disk.  Will try to shoot for gutsy-updates too.

---

### Post by karlec on 2007-10-18
Ok, thanks!  That worked.

---

