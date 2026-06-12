---
title: "MythTV Login screen on startup - doesn't recognise any users/passwords"
date: 2014-09-22
forum: Mythbuntu
---

### Post by johalareewi on 2014-09-22
Mythbuntu 12.10, MythTV 0.27.

When I start Mythbuntu, instead of the desktop,  I now get a grey popup login window (see image).
No matter what I do, I can only login as Guest Account and am unable to do much.

[ATTACH=CONFIG]256609[/ATTACH]

I have searched and found lots of suggestions but nothing that seems to work in this situation.

---

### Post by johalareewi on 2014-09-22
Found this thread and was able to login after using CTL ALT F1 and a finding an account that works.

[http://ubuntuforums.org/showthread.php?t=2167759&p=12757266#post12757266](http://ubuntuforums.org/showthread.php?t=2167759&p=12757266#post12757266)

then discovered that there was a .Xauthority file with root root permission similar to those in this thread

[http://ubuntuforums.org/showthread.php?t=2167760](http://ubuntuforums.org/showthread.php?t=2167760)

did sudo chmod 666 .Xauthority
then sudo reboot
and Mythbuntu desktop is back.

---

