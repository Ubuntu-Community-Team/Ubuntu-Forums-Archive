---
title: "NVidia Settings Won't Save - NO text editing"
date: 2008-11-04
forum: Multimedia Software
---

### Post by AEngineer on 2008-11-04
I see from scanning other posts that others have had difficulties getting the NVidia control panel to save the settings.  I'm looking for a way to save them without going in to edit a text file.  It must be possible - I hope.

I have a machine with an NVidia card, two Dell monitors, and a clean install of Ubuntu 8.10.  All went splendidly, including installing the restricted NVidia driver.  I can even, with some flakiness, get the display to spread over two screens using the "Twin" setting.  What I cannot do is get Ubuntu to remember that setting.  When I restart I come back to the single screen.

I know from past sad experience that there's probably a way to edit a text file, but I've screwed up Ubuntu too many times to want to take that route.

Is there a way to get Ubuntu to remember the settings?  I've tried the following without any success:
- "Apply" the settings - that gives a message that cannot do everything.
- "Save" the settings - It appears to do so, but the problem persists on restart.
- "Quit" - which says the settings will be saved, but no luck.

Thanks

---

### Post by Jeffa on 2008-11-04
Try running:

```
sudo nvidia-settings
```

in the terminal. That should allow you to save your settings.

---

