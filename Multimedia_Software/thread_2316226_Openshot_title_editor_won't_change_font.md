---
title: "Openshot title editor won't change font"
date: 2016-03-06
forum: Multimedia Software
---

### Post by Nyap on 2016-03-06
I'm trying to make a tutorial but for some reason the title editor won't change the font. When I press "ok" nothing happens.

Here's whats the terminal has to say:
> KeyError: 'style'
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.7/openshot/windows/fontselector.py", line 116, in on_btnOK_clicked
    self.calling_form.set_font_style()
  File "/usr/lib/pymodules/python2.7/openshot/windows/Titles.py", line 437, in set_font_style
    s = tspan_child.attributes["style"].value
  File "/usr/lib/python2.7/xml/dom/minidom.py", line 522, in __getitem__
    return self._attrs[attname_or_tuple]
KeyError: 'style'

plz help

---

