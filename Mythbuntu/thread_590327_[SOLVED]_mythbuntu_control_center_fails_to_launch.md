---
title: "[SOLVED] mythbuntu control center fails to launch"
date: 2007-10-24
forum: Mythbuntu
---

### Post by the Goat on 2007-10-24
I installed the mythbuntu control center program on my Ubuntu 7.10 amd64 desktop install.  I want to install mythfrontend.  But when I try to run the mythbuntu control center in the System:Administration menu nothing happens.  I tried running it from a terminal.  Here is the error message:
```

$ gksu -k -D /usr/share/applications/mythbuntu-control-centre.desktop /usr/bin/mythbuntu-control-centre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
  File "/usr/share/mythbuntu-control-centre/bin/mythbuntu-control-centre", line 46, in <module>
    script = ControlCentre()
  File "/usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py", line 173, in __init__
    self.revert_gui()
  File "/usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py", line 1075, in revert_gui
    self.query_system_state()
  File "/usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py", line 758, in query_system_state
    result = self.query_installed(item)
  File "/usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py", line 585, in query_installed
    return self.cache[package].CurrentVer
KeyError: 'w64codecs'
$ 


```

---

### Post by tgm4883 on 2007-10-24
[http://ubuntuforums.org/showthread.php?t=590475](http://ubuntuforums.org/showthread.php?t=590475)

---

### Post by the Goat on 2007-10-24
That fixed the problem.  Thanks.

---

