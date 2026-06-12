---
title: "Any way to dim background\desktop while watching videos??"
date: 2009-08-18
forum: Multimedia Software
---

### Post by Ubersci on 2009-08-18
I'm looking for media player that when watching videos the background\desktop dims down when i don't watch videos in full screen mode a bit like Divx Player or some online video sites.

I use VLC player and find it a extremely good program and if anyone knows how to do it through this or even Ubuntu 9.04 its self.

---

### Post by dlmarti on 2009-08-18
I don't know of a video viewer that does this (would be a great idea).

Here is a way to do it from the command line, maybe setup a little script that resides on your desktop to switch to a subdued version of your wallpaper.

```
**gconftool-2 -t string -s /desktop/gnome/background/picture_filename full_path_to_filename**
```

---

### Post by Ubersci on 2009-08-19
Thank you for your help will give it go

---

