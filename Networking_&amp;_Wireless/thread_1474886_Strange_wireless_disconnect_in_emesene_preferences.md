---
title: "Strange wireless disconnect in emesene preferences."
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by user 123 on 2010-05-06
When I try togo into the preferences in Emesene, I get the following error message:

```
Exception
You are using emesene 1.6.1 "mate" so you're free to complain here:
http://forum.emesene.org/index.php/board,19.0.html
Check already existing tickets for duplicates first, please.
Traceback (most recent call last):

  File "/usr/share/emesene/MainMenu.py", line 465, in on_preferences_activate
    self.config, self.controller.mainWindow).show()

  File "/usr/share/emesene/PreferenceWindow.py", line 183, in __init__
    self.webcam_page = WebcamPage(self.config, self.controller)

  File "/usr/share/emesene/PreferenceWindow.py", line 1626, in __init__
    self.get_device_list()

  File "/usr/share/emesene/PreferenceWindow.py", line 1694, in get_device_list
    self.combobox.append_text(name)

TypeError: Gtk.ComboBox.append_text() argument 1 must be string, not None
```


and my wireless immediately disconnects and will not function at all.


However after the wireless crash, preferences opens correctly. 

I'm using 10.04.

Very confused by this, if anyone has any suggestions I'd be very grateful.

Thanks.

---

### Post by user 123 on 2010-05-06
Please, anybody got any ideas? This is a really frustrating problem.

---

### Post by user 123 on 2010-05-07
Bump

---

### Post by user 123 on 2010-05-08
Bump

---

