---
title: "HELP: ive messed amarok up"
date: 2007-02-06
forum: Multimedia &amp; Video
---

### Post by ffxr on 2007-02-06
Amarok 1.4.4 was working fine from a standard install on xubuntu.

last night i decided to have a nosy & i compiled the 1.4.5 amarok from source and had it working fine.. but i hated having 100mb of dependent packages installed.. so i decided to make uninstall & remove it..

I had tracked all my installed packages in a notepad & removed them.. all.

I think i went an sudo apt-get autoremove too far tho.. and now after a standard install of amarok from the repos, it wont start at all..

```
sudo amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...

```

then it just dies and does nothing.. i have kdelibs installed & lib-xine.. but m sure i must be missing another required package.. i have tried installing kde-base & all dependent package as a test, but i still get the same error.. 

ve tried uninstalling and installing amarok & amarok-engines but nothing...

can anyone offer any ideas or clues as to what may be up? I cant live without Amarok... 


thanks.

---

### Post by ffxr on 2007-02-06
ahhhhh i killed amarok... :confused:

---

### Post by ffxr on 2007-02-06
panic over.. picked up the 1.4.5 debs from [http://forum.ubuntuusers.de/topic/5406/75/#565526](http://forum.ubuntuusers.de/topic/5406/75/#565526)
& managed work out i was missing  "libvisual-0.4-plugins libqt0-ruby1.8"


*breathes a sigh of releif*


thats the last time ll be throw around sudo apt-get autoremove commands willie nille..

---

