---
title: "fullscreen frontend in unity 14.04"
date: 2014-05-07
forum: Mythbuntu
---

### Post by zzztownsend2 on 2014-05-07
Hi folks - previous issue has come back in 14.04

Mythfrontend won't go to full screen in 14.04 (ubuntu-unity), however previous workaround of 'enable legacy fullscreen' in compizconfig-settings-manager is not possible available any more as this option has been removed.

Any thoughts on how to get mythfrontend to fullscreen?

Many thanks for your suggestions!

Matt

---

### Post by blm-ubunet on 2014-05-08
Do you mean "not completely full screen" or windowed ?
Windowed is caused by FE settings or frontend cmd line options..

[http://www.gossamer-threads.com/lists/mythtv/users/567567#567567](http://www.gossamer-threads.com/lists/mythtv/users/567567#567567)
[https://bugs.launchpad.net/mythbuntu/+bug/1282868](https://bugs.launchpad.net/mythbuntu/+bug/1282868)

---

### Post by khPWXxF on 2014-05-08
Do you mean the application bar across the top?

I did find that compiz legacy setting in 14.04 but it did nothing.
See this
[http://ubuntuforums.org/showthread.php?t=2222438&](http://ubuntuforums.org/showthread.php?t=2222438&)
but if there is a more elegant solution which goes straight to the heart of the problem that would be preferable.
Phil

---

### Post by Al_Vampyre on 2014-05-08
I found the same after a reboot but on mine if you exit the frontend and then open it again from the menu it properly fills the screen

---

### Post by zzztownsend2 on 2014-05-14
thanks for your thoughts folks. autohiding the unity launcher means  that at least that is out of the way, however the wmctrl command  suggested in your posts and in the bug reports has no effect on the  mythfrontend window, leaving the top panel still visibl. However, I can  live with this for now and will keep tinkering

cheers

mat

---

### Post by dannyboy79 on 2014-05-14
would devilspie help at all I wonder?

---

### Post by zzztownsend2 on 2014-05-14
OK so I found "enable legacy fullscreen" buried in the latest compizconfig-settings-manager.
Its in 'advanced search' then Plugin: workarounds, then second on the list below

This has done the job

cheers 
matt

---

