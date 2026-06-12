---
title: "Miro problems in 9.04"
date: 2010-04-15
forum: Multimedia Software
---

### Post by BonRouge on 2010-04-15
[edit]I have a bad feeling that this is the wrong forum for this question, but...[/edit]
It was a fresh install of 9.04 (because 9.10 frustrated the hell out of me by not connecting to the internet).

Now here's my problem when I (try to) run Miro:

```

failed 1
Traceback (most recent call last):
  File "/usr/bin/miro.real", line 269, in <module>
    startapp()
  File "/usr/bin/miro.real", line 226, in startapp
    startup(props_to_set)
  File "/usr/bin/miro.real", line 166, in startup
    application = load_frontend(globals(), locals(), att)
  File "/usr/bin/miro.real", line 142, in load_frontend
    _temp = __import__(frontend, globals_, locals_, ['application'], -1)
  File "/var/lib/python-support/python2.6/miro/plat/frontends/widgets/application.py", line 47, in <module>
    from miro.frontends.widgets.application import Application
  File "/var/lib/python-support/python2.6/miro/frontends/widgets/application.py", line 57, in <module>
    from miro.frontends.widgets import dialogs
  File "/var/lib/python-support/python2.6/miro/frontends/widgets/dialogs.py", line 42, in <module>
    from miro.frontends.widgets import style
  File "/var/lib/python-support/python2.6/miro/frontends/widgets/style.py", line 40, in <module>
    from miro.frontends.widgets import imagepool
  File "/var/lib/python-support/python2.6/miro/frontends/widgets/imagepool.py", line 42, in <module>
    from miro.plat.frontends.widgets import widgetset
  File "/var/lib/python-support/python2.6/miro/plat/frontends/widgets/widgetset.py", line 29, in <module>
    import gtkmozembed
SystemError: dynamic module not initialized properly

```

Any help?

Thanks in advance.

---

