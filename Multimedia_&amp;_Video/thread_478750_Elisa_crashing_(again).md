---
title: "Elisa crashing (again)"
date: 2007-06-19
forum: Multimedia &amp; Video
---

### Post by zheepeez on 2007-06-19
After having numerous problems last time I tried it, I did a complete remove of Elisa Media Center through Synaptic and then reinstalled. Typing "elisa" into terminal gives the output:

```
  File "/usr/bin/elisa", line 7, in ?
    sys.exit(
  File "/usr/lib/python2.4/site-packages/elisa/core/application.py", line 498, in start
    app.setup()
  File "/usr/lib/python2.4/site-packages/elisa/core/application.py", line 181, in setup
    plugin_manager = PluginManager(config)
  File "/usr/lib/python2.4/site-packages/elisa/core/plugin_manager.py", line 74, in __init__
    console_log_output = int(log_output)
TypeError: int() argument must be a string or a number

```

and no Media Center :(

I've tried deciphering it but it doesn't mean much to me - is there anyone who knows what the issue is? My noob eyes see Python scripting.

---

### Post by jpeddicord on 2007-06-20
It appears to be a bug in the program. If you are familiar with filing bugs, you can write one up at [https://bugs.launchpad.net/elisa](https://bugs.launchpad.net/elisa)

It appears the project was recently registered in Launchpad, so you might not get a response right away.

Jacob

---

