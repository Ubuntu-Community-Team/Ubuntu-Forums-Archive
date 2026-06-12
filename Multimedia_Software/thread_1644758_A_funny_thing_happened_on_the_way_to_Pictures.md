---
title: "A funny thing happened on the way to Pictures"
date: 2010-12-13
forum: Multimedia Software
---

### Post by Graham C Williams on 2010-12-13
Ubuntu 10.10.
All things have been working well and as expected until tonight.
I was updating some flac files using easyTAG (AAC), adding pictures and changing things a little, then dropping them into a Sansa Fuze+. All things I've done with this setup before and with no problems.
I close easyTAG and try to open: Places/ Pictures. Instead of the normal brouser up pops easytag at the pictures directory.
I test all other Places.
For each Place selected easyTAG opens instead of the usual brouser.
I go to synaptic and remove easyTAG and then restart the system.
All is now normal again (except that easyTAG is missing).
I reload easyTAG and once again it has put itself as the preferred tool to view directories.
How do I restore things to normal and what have I done?

Thanks in advance
Graham

Happy Christmas.

---

### Post by adam22 on 2011-01-07
I have this same exact issue with my computer and my sansa fuze...did you get it solved?

---

### Post by Graham C Williams on 2011-01-11
Hi.
No, I have not solved the problem, only worked around it!
I don't think it has anything to do with the Sansa Fuze (I have both a Fuze and a Fuze+; using the Fuze for nearly 2 years now). On this Ubuntu machine 'easyTAG' will take over the duties of 'Nautilus' wether I have a Sansa Fuze plugged in or not. On the other side the whole business started when I transfered files.
Do you know, is there a preferred file manager list or switch or selector within Ubuntu? I'm guessing that 'easyTAG' has installed itself as the number 1 file manager ahead of 'Nautilus'. It's the only way I can explain the action - install 'easyTAG' and that becomes the default file browser - remove 'easyTAG' and 'Nautilus is restored as the default browser.

I'll let you know if I have any Joy!

Graham.

---

### Post by Graham C Williams on 2011-02-02
Hi Adam22.

Finally found a solution.

Goto posting #44 here:
[http://ubuntuforums.org/showthread.php?t=1151325&highlight=easytag+nautilus](http://ubuntuforums.org/showthread.php?t=1151325&highlight=easytag+nautilus)

copy and enter:
gksudo gedit ~/.local/share/applications/mimeapps.list

Delete the easytag line and save.

):P

Graham.

---

### Post by adam22 on 2011-08-29
Didn't see this til now...thanks!

---

