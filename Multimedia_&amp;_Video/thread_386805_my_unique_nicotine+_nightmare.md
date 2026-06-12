---
title: "my unique nicotine+ nightmare"
date: 2007-03-17
forum: Multimedia &amp; Video
---

### Post by bradford72 on 2007-03-17
I'm having trouble with nicotine+ and can't seem to find any other errors posted with the same errors I'm getting...here's what I do/get
> bradford@bradford-desktop:~$ nicotine
Nicotine supports "psyco", an inline optimizer for python
code, you can get it at [http://sourceforge.net/projects/psyco/](http://sourceforge.net/projects/psyco/)
Nicotine supports a country code blocker but that
requires a (GPL'ed) library called GeoIP. You can find it here:
C library:       [http://www.maxmind.com/app/c](http://www.maxmind.com/app/c)
Python bindings: [http://www.maxmind.com/app/python](http://www.maxmind.com/app/python)
(the python bindings require the C library)

Traceback (most recent call last):
  File "/usr/bin/nicotine", line 155, in <module>
    app = frame.MainApp(config, trayicon)
  File "/var/lib/python-support/python2.5/pynicotine/gtkgui/frame.py", line 1666, in __init__
    self.frame = testwin(config, trayicon)
  File "/var/lib/python-support/python2.5/pynicotine/gtkgui/frame.py", line 65, in __init__
    config2.readConfig()
  File "/var/lib/python-support/python2.5/pynicotine/config.py", line 244, in readConfig
    if self.sections["server"]["server"][0] in [ "mail.slsknet.org", "mail.slsk.org" ]:
TypeError: 'NoneType' object is unsubscriptable

I'm not so worried about psycho, or blocking addresses right now...I just can't seem to get the thing to work...any help here?

---

