---
title: "Global hotkeys (Exaile &amp; AmaroK)"
date: 2007-06-10
forum: Multimedia &amp; Video
---

### Post by clk99 on 2007-06-10
I recently uninstalled Exaile because I started using AmaroK as my main media player.  I set my global hotkeys in AmaroK and everything, but when I use any of them (the same as I had in Exaile) I get an error saying:

"There was an error running 'exail -*': Failed to execute child process 'exaile' (No such file or directory)."

So something of the global hotkeys setting from Exaile is still somewhere in my system and it's overriding the ones for AmaroK.  How can I fix this? 
Thanks.

---

### Post by clk99 on 2007-06-17
bump

---

### Post by El Jamo on 2007-07-11
Same problem here.  I wish I knew where Exaile's global hotkeys were running from.  They aren't part of the "Keyboard Shortcuts" in System -> Preferences.  Uninstalled Exaile (sudo apt-get --purge autoremove exaile), but still get "There was an error running "exaile": Failed to execute child process "exaile" (No such file or directory)." when I use the old shortcut keys.  It'd be nice to figure this out, b/c that would also show me how I could add some useful shortcuts to Ubuntu.

---

### Post by ryl on 2007-08-17
I've got the same problem. Used System Tools -> Configuration Editor to remove every Exaile reference, now just comes up "No command XX has been defined". Tried "sudo dpkg-reconfigure amarok" and "amarok --wizard" for first-time wizard, no joy. I'm on Feisty.

In different threads, people have been talking about 'resetting' the global bindings through amarok, all I can see is reset to defaults which is greyed out anyway, there doesn't seem to be anything going on.

Has anyone else tried the above? I can't think of anything else apart from doing it manually, which isn't a great chore but it'd be handy for it to be done automatically.

---

