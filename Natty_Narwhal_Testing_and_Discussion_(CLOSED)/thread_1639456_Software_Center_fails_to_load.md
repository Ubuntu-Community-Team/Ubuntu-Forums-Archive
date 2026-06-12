---
title: "Software Center fails to load"
date: 2010-12-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by kyleabaker on 2010-12-06
I just installed Natty with the release of Alpha 1 and have run all updates. I've also not modified anything regarding the Software Center, but I noticed that it wouldn't load.

Trying to open it from a terminal I see the following:
```
2010-12-06 19:01:41,276 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/db/database.py', 96, 'open')'
2010-12-06 19:01:41,276 - root - WARNING - failed to add sca db Couldn't stat '/home/kyleabaker/.cache/software-center/software-center-agent.db' (No such file or directory)
Traceback (most recent call last):
  File "/usr/bin/software-center", line 109, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path, options, args)
  File "/usr/share/software-center/softwarecenter/app.py", line 209, in __init__
    self.navhistory_forward_action)
  File "/usr/share/software-center/softwarecenter/view/availablepane.py", line 100, in __init__
    self._build_ui()
  File "/usr/share/software-center/softwarecenter/view/availablepane.py", line 111, in _build_ui
    self.apps_filter)
  File "/usr/share/software-center/softwarecenter/view/catview_gtk.py", line 256, in __init__
    self.build(desktopdir)
  File "/usr/share/software-center/softwarecenter/view/catview_gtk.py", line 497, in build
    self._build_homepage_view()
  File "/usr/share/software-center/softwarecenter/view/catview_gtk.py", line 327, in _build_homepage_view
    self._append_featured_and_new()
  File "/usr/share/software-center/softwarecenter/view/catview_gtk.py", line 412, in _append_featured_and_new
    nonapps_visible=AppStore.NONAPPS_ALWAYS_VISIBLE)
  File "/usr/share/software-center/softwarecenter/view/appview.py", line 180, in __init__
    q.get_description() for q in search_query])):
AttributeError: 'Query' object has no attribute 'get_description'
```

I did a quick search and found the [bug report]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/684887") for this, but if its affecting anyone else and you're anxiously waiting for the update to fix it, you can do the following as a quick fix (the update will likely be the same change anyway, but you can do this to make it work sooner :D )..

[LIST=1]
[*]sudo gedit /usr/share/software-center/softwarecenter/view/appview.py
[*]replace 'q.get_description()' in line 180 with 'str(q)'
[*]save and close
[/LIST]

[QUOTE=Kiwinote]launch software-center, and it *should* hopefully work[/QUOTE]

Worked for me. :D

---

### Post by Amroozy on 2010-12-07
you the man .. thanks alot
you know i had ubuntu  10.10 and updated it to 11.4 and when i found out software center and other apps not working so i decided to make fresh 11.4 install.. after 4 days failing to set it up finally i managed to make it works.. then i found out that software center not working :D 
sadly you didn't post this earlier but any way thanks again it works so fine atm 
wish you all the best in your life..

---

### Post by OlyPerson on 2010-12-07
Mine still won't start even though the update already changed this line.  Starting it from the terminal I get:
```
2010-12-07 08:56:41,666 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/db/database.py', 99, 'open')'
2010-12-07 08:56:41,666 - root - WARNING - failed to add sca db Couldn't stat '/home/paul/.cache/software-center/software-center-agent.db' (No such file or directory)
Traceback (most recent call last):
  File "/usr/bin/software-center", line 109, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path, options, args)
  File "/usr/share/software-center/softwarecenter/app.py", line 209, in __init__
    self.navhistory_forward_action)
  File "/usr/share/software-center/softwarecenter/view/availablepane.py", line 97, in __init__
    self._build_ui()
  File "/usr/share/software-center/softwarecenter/view/availablepane.py", line 108, in _build_ui
    self.apps_filter)
  File "/usr/share/software-center/softwarecenter/view/catview_gtk.py", line 244, in __init__
    self.build(desktopdir)
  File "/usr/share/software-center/softwarecenter/view/catview_gtk.py", line 489, in build
    self._build_homepage_view()
  File "/usr/share/software-center/softwarecenter/view/catview_gtk.py", line 315, in _build_homepage_view
    self._append_featured_and_new()
  File "/usr/share/software-center/softwarecenter/view/catview_gtk.py", line 404, in _append_featured_and_new
    nonapps_visible=AppStore.NONAPPS_ALWAYS_VISIBLE)
  File "/usr/share/software-center/softwarecenter/view/appview.py", line 182, in __init__
    self._perform_search()
  File "/usr/share/software-center/softwarecenter/view/appview.py", line 249, in _perform_search
    enquire.set_sort_by_key(LocaleSorter(self.db), reverse=False)
  File "/usr/share/software-center/softwarecenter/view/appview.py", line 594, in __init__
    xapian.Sorter.__init__(self)
  File "/usr/lib/python2.6/dist-packages/xapian/__init__.py", line 5620, in __init__
    def __init__(self, *args, **kwargs): raise AttributeError("No constructor defined")
AttributeError: No constructor defined

```

I'm not that proficient with python, any ideas what's wrong?

---

### Post by Penguin360 on 2010-12-17
You are the man. It worked like a charm.

Thanks a lot.

---

