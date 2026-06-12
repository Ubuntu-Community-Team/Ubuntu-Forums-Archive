---
title: "what is &quot;generate frontend restart mapping followed by clear&quot;"
date: 2011-10-17
forum: Mythbuntu
---

### Post by jeremycobert on 2011-10-17
in the mythbuntu install and on the remote control setup there is an option for "generate frontend restart mapping followed by clear"
can someone explain what that does ? is it a way to start the frontend with a remote control button ?

---

### Post by sikk on 2012-06-28
Hello,

Old thread I know, but since I have found the answer I thought I would reply for others.

This option enables a function which automatically restarts the mythfrontend if it crashes. See this thread for more details.

[http://ubuntuforums.org/showthread.php?t=1785156](http://ubuntuforums.org/showthread.php?t=1785156)

---

### Post by tgm4883 on 2012-06-28
> **sikk said:**
> Hello,

Old thread I know, but since I have found the answer I thought I would reply for others.

This option enables a function which automatically restarts the mythfrontend if it crashes. See this thread for more details.

[http://ubuntuforums.org/showthread.php?t=1785156](http://ubuntuforums.org/showthread.php?t=1785156)

No, that is incorrect. The autorestart functionality is built into the frontend startup script by default, it is not something you can add/remove though MCC.

What the OP is talking about is the "Generate frontend restart mapping (Power followed by Clear)" checkbox. What this does is creates a button mapping in LIRC that if you press Power then press Clear it will kill mythfrontend and start a new one. This would be used if for some reason the frontend locked up and needed to be restarted. (mythfrontend, not the OS itself)


Locking old thread

---

