---
title: "Envy not working after upgrade"
date: 2008-02-09
forum: Multimedia &amp; Video
---

### Post by Mazehero55 on 2008-02-09
Hey I originally installed my driver through envy in fiesty, I have since upgraded to gutsy. I reinstalled envy to reinstall a new driver and now when I open it this is what it says exactly.

tieden@infinite:~$ envy -g
gksudo: /opt/mono-1.2.6/lib/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
  File "/usr/share/envy/gtkenvy.py", line 7, in <module>
    from Envy import objects
ImportError: No module named Envy


any ideas? I've run sudo apt-get install -f 
and that doesn't help at all.
:confused:

---

### Post by brikenobi7r on 2008-02-10
Hi, I'm not an expert at this but try to uninstall and re-install. Then, maybe try to save it in a different document, such as downloads or files. If this doesnt work, sorry. at least try it might work. OR, take off the upgrade and re upgrade. :guitar:

---

