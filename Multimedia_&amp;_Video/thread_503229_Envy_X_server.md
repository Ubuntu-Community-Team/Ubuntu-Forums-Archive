---
title: "Envy X server"
date: 2007-07-17
forum: Multimedia &amp; Video
---

### Post by catch2two on 2007-07-17
I am an absolute noob, but that said i did manage to get my dual screens running. The problem i am having is that each time i restart i loose my settings and one screen is default disabled.

I assume by clicking the option in the nvidia setting to save updates to the x server would fix this problem???

However, when i click that it is unable to save it says something about unable to copy over the back up file.

Is there a simple fix for this problem?

Any help[ would be great

---

### Post by dabl on 2007-07-17
Yes, you have to be in "Super User" mode to save any system file including /etc/xorg.conf.

So, open a console window and enter ```
sudo nvidia-settings
```

then set your screens and refresh rates and all that, THEN click the "Save to X Config File" button and it should work correctly.

:guitar:

---

