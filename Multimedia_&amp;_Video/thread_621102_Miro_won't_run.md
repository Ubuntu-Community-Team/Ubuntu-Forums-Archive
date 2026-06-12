---
title: "Miro won't run"
date: 2007-11-23
forum: Multimedia &amp; Video
---

### Post by Kreuger on 2007-11-23
I just installed Miro to try it out and when I try to run it, I get this:
> 
kreuger@kreuger-desktop:~$ /usr/bin/miro
/usr/lib/firefox
DTV: Warning: could not import GTK (is DISPLAY set?)
Traceback (most recent call last):
  File "/usr/bin/miro.real", line 106, in <module>
    startapp()
  File "/usr/bin/miro.real", line 80, in startapp
    app.main()
  File "/var/lib/python-support/python2.5/miro/app.py", line 94, in main
    Controller().Run()
  File "/var/lib/python-support/python2.5/miro/app.py", line 620, in __init__
    frontend.Application.__init__(self)
AttributeError: class Application has no attribute '__init__'
kreuger@kreuger-desktop:~$ 
 Google didn't help.

---

