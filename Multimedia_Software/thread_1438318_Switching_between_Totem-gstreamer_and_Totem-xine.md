---
title: "Switching between Totem-gstreamer and Totem-xine"
date: 2010-03-24
forum: Multimedia Software
---

### Post by cksarvis on 2010-03-24
I've noticed that we can now install both xine and gstreamer backends. The problem is I'm not sure how to switch between the two backends within the same gnome session. The way it's set up now is I can watch my .avi movies (which is why I first installed xine) after I login, but then it'll stop supporting sound and playback. I'm not sure why it stops, but it does.

I've never posted in the forums before, so I'm sorry if my technical terms aren't technical enough.

Any ideas?

---

### Post by cksarvis on 2010-03-24
I think I figured out the problem as far as why it's not staying .avi capable. Between using totem to watch files from my computer, I'm using my browser to watch movies on the embedded movie player. The problem is I don't have a totem-xine player. So it must be defaulting to gstreamer when I open videos in my firefox browser.

This means that I also have to figure out how to figure out how to use a totem-xine plugin. Anyone know how?

---

### Post by Yellow Pasque on 2010-03-25
totem-xine is no longer installable from the repo, because development on it stopped a little while ago in favor of just using gstreamer. totem-xine is just a metapackage that points to totem-gstreamer.

If you want xine, you'll have to find another player, like gxine or xine-ui.

---

### Post by cksarvis on 2010-03-25
Totem-xine is still found in my package manager.

If that's true than that brings up a whole new question why my .avi files started working.

---

