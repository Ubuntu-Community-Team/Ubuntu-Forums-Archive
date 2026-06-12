---
title: "[SOLVED] Help Please: VLC Plays Nothing"
date: 2008-07-09
forum: Multimedia Software
---

### Post by 71CH on 2008-07-09
I tried to completely remove VLC so that I could reinstall it.  I followed the instructions of kmf31 in this post [http://forum.videolan.org/viewtopic.php?f=13&t=39638#p123376](http://forum.videolan.org/viewtopic.php?f=13&t=39638#p123376) and I think that screwed me up.  After reinstalling vlc whenever I try to play any video I get these errors:

main error: no interface module matched "hotkeys,none"
main error: no suitable interface module
main error: interface "hotkeys,none" initialization failed
main error: no interface module matched "screensaver,none"
main error: no suitable interface module
main error: interface "screensaver,none" initialization failed
main error: no access2 module matched "file"
main error: no access2 module matched "file"
main error: no suitable access module for 

Can somebody please help me.

---

### Post by 71CH on 2008-07-09
bump

---

### Post by Odrodzona-Sarmacja on 2008-07-09
My guess you didn't do
"sudo dpkg --purge vlc" alternatively "sudo dpkg --force-all --purge vlc"
before going berserk at these directories and I hope you did use
"sudo rm -rf (these directories)"
and not just
"rm -rf ..."
:)

Good luck!

---

### Post by 71CH on 2008-07-09
thanks for the reply but it didn't help
any other ideas?

---

### Post by 71CH on 2008-07-10
bump

---

### Post by gandaran on 2008-07-10
> **71CH said:**
> I tried to completely remove VLC so that I could reinstall it.  I followed the instructions of kmf31 in this post [http://forum.videolan.org/viewtopic.php?f=13&t=39638#p123376](http://forum.videolan.org/viewtopic.php?f=13&t=39638#p123376) and I think that screwed me up.  After reinstalling vlc whenever I try to play any video I get these errors:

main error: no interface module matched "hotkeys,none"
main error: no suitable interface module
main error: interface "hotkeys,none" initialization failed
main error: no interface module matched "screensaver,none"
main error: no suitable interface module
main error: interface "screensaver,none" initialization failed
main error: no access2 module matched "file"
main error: no access2 module matched "file"
main error: no suitable access module for 

Can somebody please help me.

I'm not sure, but from reading your post I believe you compiled vlc, if that is correct, these errors could be due to a missing dependency, and if you want to remove vlc you'll have to delete all the vlc files.
it's best to always use the synaptic package manager to install and remove completely any application or in this case **vlc**, installing an application using synaptic will also install all the necessary dependencies and the same is true when you remove the application using synaptic.

---

### Post by 71CH on 2008-07-10
reinstalled it and installed all plugins
works fine now
I think the problem before was the missing plugins

---

