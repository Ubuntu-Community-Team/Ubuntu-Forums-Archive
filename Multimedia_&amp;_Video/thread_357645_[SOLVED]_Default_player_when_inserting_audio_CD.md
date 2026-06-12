---
title: "[SOLVED] Default player when inserting audio CD"
date: 2007-02-09
forum: Multimedia &amp; Video
---

### Post by jdackle on 2007-02-09
Hi everyone!

I have both gnome-cd and soundjuicer installed on my system. When I insert an audio CD in the drive, sound juicer pops up.

I'd prefer gnome-cd for that task, but I do not want to uninstall sound juicer.
So I used gconf2 editor to make this change:
```
/desktop/gnome/url-handlers/cdda = gnome-cd %s
```
(This key was previously set to soundjuicer)

Restarted session, rebooted the machine and still no changes. Whenever I insert an audio CD, soundjuicer comes up.

Is there a way to change this without uninstalling sound-juicer?

Thanks in advance

---

### Post by jpeddicord on 2007-02-09
The "official" way to change the setting is from System > Preferences > Removable Drives and Media. On the Multimedia tab, you can change the setting for different types of CDs. This might change the setting correctly and save it, since sometimes GConf settings are overwritten at the end of the session.

---

### Post by bucky100771 on 2007-02-10
Odd...when I go to change this setting by following the above instructions, I do not have a "multimedia" tab.  I only have "INTERNET" & "SYSTEM".  Am I missing an installed library file?

Help...

---

### Post by jdackle on 2007-02-10
Thanks for the tip, jacobmp92. Worked perfect! :cool:
Looks like I'd taken the long road nowhere on this one... :lol: 


Sorry, bucky, I have no idea on how you got that missing tab...


Thanks again jacob! :)

---

