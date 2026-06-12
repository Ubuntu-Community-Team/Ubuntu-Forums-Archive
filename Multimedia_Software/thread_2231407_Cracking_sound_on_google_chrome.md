---
title: "Cracking sound on google chrome"
date: 2014-06-25
forum: Multimedia Software
---

### Post by Vormeph on 2014-06-25
I think this problem is specific to chrome/chromium; the sound cracks occasionally. I looked it up and found it might have something to do with the audio buffer size. If I want to change the audio buffer size, how can I make the change when launching google chrome? Where would I place 

```
--audio-buffer-size=2048
``` in the settings of google chrome?

---

### Post by lidex on 2014-07-01
Don't think you can do that from within chrome. Run it from a terminal or <Alt>+<F2>:
```
chrome --audio-buffer-size=2048
```

What version do you have? 27 should have fixed that issue:
[https://code.google.com/p/chromium/issues/detail?id=178626]("https://code.google.com/p/chromium/issues/detail?id=178626")

---

