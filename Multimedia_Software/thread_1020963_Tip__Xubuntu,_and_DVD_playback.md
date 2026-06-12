---
title: "Tip:  Xubuntu, and DVD playback"
date: 2008-12-24
forum: Multimedia Software
---

### Post by flyingcadet on 2008-12-24
If you want to watch DVDs, you have to use the instructions found on the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") page.  Once you are done, Totem should play DVDs without a problem.  If DVD playback still doesn't work, then reinstalling Totem is a likely next step.  Totem out of the box is from totem-gstreamer package, which doesn't seem to like DVDs very much.  Reinstalling totem was the only way for me to get ride of the following erorr message: ```
"Totem could not play this media (DVD) although a plugin is present to handle it."
```.

To get around this particular problem, one must use the totem-xine package when reinstalling totem.

1) To remove the Totem-gstreamer, use the follwoing code in the terminal: ```
sudo apt-get remove totem-gstreamer totem-plugins totem-common
```

2)  Reinstalling with totem-xine is doen with the following in the terminal: ```
sudo apt-get install totem-xine totem-plugins totem-common
```

YMMV, but good luck.

flyingcadet

---

