---
title: "Solfege won't start!!"
date: 2009-09-30
forum: Multimedia Software
---

### Post by pluckypigeon on 2009-09-30
I'm trying to get Solfege to start but I'm not sure what is wrong. Does anyone have any ideas?

Thanks in advance!

```


Traceback (most recent call last):
  File "/usr/bin/solfege", line 83, in <module>
    solfege.mainwin.start_app(os.path.join(prefix, "share", "solfege"))
  File "/usr/share/solfege/solfege/mainwin.py", line 1134, in start_app
    solfege.win = w = MainWin(options, datadir, lessonfile_manager)
  File "/usr/share/solfege/solfege/mainwin.py", line 529, in __init__
    self.on_learning_tree_changed()
  File "/usr/share/solfege/solfege/mainwin.py", line 597, in on_learning_tree_changed
    self.display_frontpage()
  File "/usr/share/solfege/solfege/mainwin.py", line 1041, in display_frontpage
    self.get_view().display_data(data)
  File "/usr/share/solfege/solfege/mainwin.py", line 434, in display_data
    self._display_data(data, display_only_tests)
  File "/usr/share/solfege/solfege/mainwin.py", line 334, in _display_data
    label = gu.ClickableLabel(_no_xgettext(link.m_name))
  File "/usr/share/solfege/solfege/gu.py", line 829, in __init__
    self.get_children()[0].set_alignment(0.0, 0.5)
IndexError: list index out of range





```

---

### Post by pluckypigeon on 2009-10-30
anyone??

---

