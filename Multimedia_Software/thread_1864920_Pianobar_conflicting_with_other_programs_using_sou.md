---
title: "Pianobar conflicting with other programs using sound"
date: 2011-10-19
forum: Multimedia Software
---

### Post by TheOneEyedMan on 2011-10-19
I recently upgraded to Ubuntu 11.10. 

Now when I run pianiobar it plays audio if nothing else is using audio. Otherwise it won't play sound but otherwise runs without indicating a problem. On the other hand, if pianobar is playing audio, the rest of the system (examples youtube on Chrome or Firefox and VLC of an MP3) won't play audio. 

When Pianobar is running, the Gnome Preferences Sound tool (tab applications) doesn't indicate that anything is running, which makes me wonder if the problem is happening a low level where whatever library it is using is short circuiting whatever Gnome is using. 

Anyone have any ideas on how to resolve this problem?

---

### Post by meierbac on 2011-11-09
I also experienced this problem numerous times, although I have not had any problems after updating to the new (2011.11.09) version.

---

### Post by TheOneEyedMan on 2011-11-10
Did you compile that from source? I don't see that available as a deb file anywhere.

Also, are you getting the " Login... Error: Protocol incompatible. Please upgrade libpiano." error? I just started getting that today.  I am also using the most up to date version of libpiano0 I could find, 2011.09.22-1.

---

### Post by meierbac on 2011-11-15
Yes, I compiled from source (2011.11.11).  No, I am not getting the login error.  I updated my libpiano version to 2011.09.22-1 as well.  Restarting with the newest version seems to work just fine.

---

