---
title: "Elisa Media Center opening, returning multiple errors"
date: 2007-05-26
forum: Multimedia &amp; Video
---

### Post by zheepeez on 2007-05-26
I just installed Elisa Media Center (using repositories and apt-get, as normal), and upon opening through the Applications menu, nothing happens.

Running the command "elisa" through the terminal gives the following:

```
ross@ross:~$ elisa
26/05/2007 19:12:20.371  INFO     Config format error in /home/ross/.elisa/./elisa.conf: Parse error in value at line 73.
Traceback (most recent call last):
  File "/usr/bin/elisa", line 7, in ?
    sys.exit(
  File "/usr/lib/python2.4/site-packages/elisa/core/application.py", line 497, in start
    app = Application(options['config_file'])
  File "/usr/lib/python2.4/site-packages/elisa/core/application.py", line 104, in __init__
    self.set_config(config_filename)
  File "/usr/lib/python2.4/site-packages/elisa/core/application.py", line 309, in set_config
    self.close()
  File "/usr/lib/python2.4/site-packages/elisa/core/application.py", line 448, in close
    skin_unloaded(None)
  File "/usr/lib/python2.4/site-packages/elisa/core/application.py", line 408, in skin_unloaded
    thumbnail_manager = self.get_thumbnail_manager()
  File "/usr/lib/python2.4/site-packages/elisa/core/application.py", line 285, in get_thumbnail_manager
    return self._thumbnail_manager
AttributeError: Application instance has no attribute '_thumbnail_manager'

```

Any ideas? If it's at all relevant, I'm running Enlightenment 17, although I've tried running a Gnome session and I get the same result.

Thanks

---

### Post by amoore on 2007-06-06
your ~/.elisa/elisa.conf file has some typos. Check the sorces and check your spelling.

---

### Post by MetalMusicAddict on 2007-06-06
I would also recommend chatting with those guys on IRC (#elisa on freenode) reporting bugs if any. It's really early in Elisa's development and they need any help they can get. They are friendly guys as well.

---

